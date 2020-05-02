---
title: 自訂服務裝載
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: 70d527599c310cba694624839f14a313f6000337
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728436"
---
# <a name="custom-service-host"></a>自訂服務裝載
這個範例會示範如何使用 <xref:System.ServiceModel.ServiceHost> 類別的自訂衍生，以變更服務的執行階段行為。 這個方法會提供可重複使用替代方案，以便透過常用方法來設定大量服務。 此範例也會示範如何使用 <xref:System.ServiceModel.Activation.ServiceHostFactory> 類別，以便在網際網路資訊服務 (IIS) 或 Windows Process Activation Service (WAS) 裝載環境中使用自訂 ServiceHost。  
  
> [!IMPORTANT]
> 這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> 如果此目錄不存在，請移至[.NET Framework 4 的 Windows Communication Foundation （wcf）和 Windows Workflow Foundation （WF）範例](https://www.microsoft.com/download/details.aspx?id=21459)，以下載所有 WINDOWS COMMUNICATION FOUNDATION （wcf） [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a>關於案例
 為避免不慎洩漏可能的敏感性服務中繼資料，Windows Communication Foundation （WCF）服務的預設設定會停用中繼資料發行。 此行為預設是安全的，但也表示您無法使用中繼資料匯入工具（例如 Svcutil）來產生呼叫服務所需的用戶端程式代碼，除非在設定中明確啟用服務的中繼資料發行行為。  
  
 啟用大量服務的中繼資料發行，需要將相同的組態項目加入至每個個別服務，而這會產生大量組態資訊，這些資訊基本上都是相同的。 除了個別設定每個服務，也撰寫命令式程式碼，讓中繼資料一次發行，然後在數個不同的服務中重複使用該程式碼。 這是藉由建立衍生自 <xref:System.ServiceModel.ServiceHost> 並覆寫 `ApplyConfiguration`() 方法，以命令方式新增中繼資料發行行為的新類別來達成。  
  
> [!IMPORTANT]
> 為了清楚說明，這個範例示範如何建立不安全的中繼資料發行端點。 這類端點可能會提供給匿名未驗證的取用者使用，而且必須在部署這類端點之前小心處理，以確保公開服務的中繼資料是適當的。  
  
## <a name="implementing-a-custom-servicehost"></a>實作自訂 ServiceHost
 <xref:System.ServiceModel.ServiceHost> 類別會公開數個繼承者可覆寫以變更服務之執行階段行為的有用虛擬方法。 例如，`ApplyConfiguration`() 方法會從組態存放區讀取服務組態資訊，並因此變更主機的 <xref:System.ServiceModel.Description.ServiceDescription>。 預設的執行會從應用程式的設定檔讀取設定。 自訂實作可以覆寫 `ApplyConfiguration`()，以進一步使用命令式程式碼變更 <xref:System.ServiceModel.Description.ServiceDescription>，或甚至完全取代預設組態存放區。 例如，從資料庫讀取服務的端點設定，而不是從應用程式的設定檔。  
  
 在此範例中，我們想要建立自訂的 ServiceHost 來新增 ServiceMetadataBehavior （這會啟用中繼資料發行），即使此行為未明確新增至服務的設定檔也一樣。 若要完成此動作，請建立繼承自<xref:System.ServiceModel.ServiceHost>的新類別`ApplyConfiguration`，並覆寫（）。  
  
```csharp
class SelfDescribingServiceHost : ServiceHost  
{  
    public SelfDescribingServiceHost(Type serviceType, params Uri[] baseAddresses)  
        : base(serviceType, baseAddresses) { }  
  
    //Overriding ApplyConfiguration() allows us to
    //alter the ServiceDescription prior to opening  
    //the service host.
    protected override void ApplyConfiguration()  
    {  
        //First, we call base.ApplyConfiguration()  
        //to read any configuration that was provided for  
        //the service we're hosting. After this call,  
        //this.Description describes the service  
        //as it was configured.  
        base.ApplyConfiguration();
  
        //(rest of implementation elided for clarity)  
    }  
}  
```  
  
 因為我們不想要忽略應用程式佈建檔案中所提供的任何設定，所以覆寫`ApplyConfiguration`（）的第一件事就是呼叫基底執行。 完成此方法時，就可以使用下列命令式程式碼，以命令方式將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 新增至描述。  
  
```csharp
ServiceMetadataBehavior mexBehavior = this.Description.Behaviors.Find<ServiceMetadataBehavior>();  
if (mexBehavior == null)  
{  
    mexBehavior = new ServiceMetadataBehavior();  
    this.Description.Behaviors.Add(mexBehavior);  
}  
else  
{  
    //Metadata behavior has already been configured,
    //so we do not have any work to do.  
    return;  
}  
```  
  
 覆寫 `ApplyConfiguration`() 必須執行的最後一個動作為新增預設中繼資料端點。 依照慣例，會為服務主機的 BaseAddresses 集合中的每個 URI 建立一個中繼資料端點。  
  
```csharp
//Add a metadata endpoint at each base address  
//using the "/mex" addressing convention  
foreach (Uri baseAddress in this.BaseAddresses)  
{  
    if (baseAddress.Scheme == Uri.UriSchemeHttp)  
    {  
        mexBehavior.HttpGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeHttps)  
    {  
        mexBehavior.HttpsGetEnabled = true;  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexHttpsBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetPipe)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexNamedPipeBinding(),  
                                "mex");  
    }  
    else if (baseAddress.Scheme == Uri.UriSchemeNetTcp)  
    {  
        this.AddServiceEndpoint(ServiceMetadataBehavior.MexContractName,  
                                MetadataExchangeBindings.CreateMexTcpBinding(),  
                                "mex");  
    }  
}  
```  
  
## <a name="using-a-custom-servicehost-in-self-host"></a>在自我裝載案例中使用自訂 ServiceHost  
 現在您已完成自訂 ServiceHost 實作，可以透過在 `SelfDescribingServiceHost` 的執行個體內裝載服務，即可使用此實作將中繼資料發行行為新增至該服務。 下列程式碼會顯示如何在自我裝載案例中使用該服務。  
  
```csharp
SelfDescribingServiceHost host =
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 我們的自訂主機仍會從應用程式的設定檔讀取服務的端點設定，如同我們已使用預設<xref:System.ServiceModel.ServiceHost>類別來裝載服務。 不過，由於新增邏輯以在自訂主機內啟用中繼資料發行，就不再需要於組態中明確啟用中繼資料發行行為。 當您建置其中包含多個服務的應用程式，而且想要在每個服務上啟用中繼資料發行，但不想要重複撰寫相同的組態項目時，這個方法特別有用。  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a>在 IIS 或 WAS 中使用自訂 ServiceHost  
 在自我裝載案例中使用自訂服務主機很簡單，因為這是您的應用程式程式碼，而且主要負責建立及開啟服務主機執行個體。 不過，在 IIS 或 WAS 裝載環境中，WCF 基礎結構會動態具現化服務的主機，以回應傳入的訊息。 自訂服務主機也可以在此裝載環境中使用，但形式上在 ServiceHostFactory 中需要額外的程式碼。 下列程式碼會顯示 <xref:System.ServiceModel.Activation.ServiceHostFactory> 衍生，而這個衍生會傳回自訂 `SelfDescribingServiceHost` 的執行個體。  
  
```csharp
public class SelfDescribingServiceHostFactory : ServiceHostFactory  
{  
    protected override ServiceHost CreateServiceHost(Type serviceType,
     Uri[] baseAddresses)  
    {  
        //All the custom factory does is return a new instance  
        //of our custom host class. The bulk of the custom logic should  
        //live in the custom host (as opposed to the factory)
        //for maximum  
        //reuse value outside of the IIS/WAS hosting environment.  
        return new SelfDescribingServiceHost(serviceType,
                                             baseAddresses);  
    }  
}  
```  
  
 如您所見，執行自訂 ServiceHostFactory 相當簡單。 所有自訂邏輯都在 ServiceHost 實作內部，而處理站會傳回衍生類別的執行個體。  
  
 若要搭配服務執行使用自訂處理站，我們必須將一些額外的中繼資料新增至服務的 .svc 檔案。  
  
```xml
<% @ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"
               language=c# Debug="true" %>
```
  
 在這裡，我們已將`Factory`額外的屬性`@ServiceHost`新增至指示詞，並將自訂 factory 的 CLR 型別名稱傳遞為屬性的值。 當 IIS 或 WAS 收到此服務的訊息時，WCF 裝載基礎結構會先建立 ServiceHostFactory 的實例，然後藉由呼叫`ServiceHostFactory.CreateServiceHost()`來具現化服務主機本身。  
  
## <a name="running-the-sample"></a>執行範例  
 雖然此範例提供功能完整的用戶端和服務執行，但此範例的重點在於說明如何透過自訂主機來改變服務的執行時間行為。請執行下列步驟：  
  
### <a name="observe-the-effect-of-the-custom-host"></a>觀察自訂主機的效果
  
1. 開啟服務的 Web.config 檔案，並觀察沒有設定明確啟用服務的中繼資料。  
  
2. 開啟服務的 .svc 檔案，並觀察其@ServiceHost指示詞是否包含指定自訂 ServiceHostFactory 名稱的 Factory 屬性。  
  
### <a name="set-up-build-and-run-the-sample"></a>設定、建立和執行範例
  
1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](one-time-setup-procedure-for-the-wcf-samples.md)。

2. 若要建立方案，請依照[建立 Windows Communication Foundation 範例](building-the-samples.md)中的指示進行。

3. 建立解決方案之後，請執行 Setup .bat 來設定 IIS 7.0 中的 ServiceModelSamples 應用程式。 ServiceModelSamples 目錄現在應該會顯示為 IIS 7.0 應用程式。

4. 若要在單一或跨電腦設定中執行範例，請遵循執行[Windows Communication Foundation 範例](running-the-samples.md)中的指示。

5. 若要移除 IIS 7.0 應用程式，請執行*清除 .bat*。

## <a name="see-also"></a>另請參閱

- [How to: Host a WCF Service in IIS](../feature-details/how-to-host-a-wcf-service-in-iis.md)
