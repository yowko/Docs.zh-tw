---
title: 自訂服務裝載
ms.date: 03/30/2017
ms.assetid: fe16ff50-7156-4499-9c32-13d8a79dc100
ms.openlocfilehash: d2eebd502fa02d01ac86cf88f336b72829a6116f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59340928"
---
# <a name="custom-service-host"></a>自訂服務裝載
這個範例會示範如何使用 <xref:System.ServiceModel.ServiceHost> 類別的自訂衍生，以變更服務的執行階段行為。 這個方法會提供可重複使用替代方案，以便透過常用方法來設定大量服務。 此範例也會示範如何使用 <xref:System.ServiceModel.Activation.ServiceHostFactory> 類別，以便在網際網路資訊服務 (IIS) 或 Windows Process Activation Service (WAS) 裝載環境中使用自訂 ServiceHost。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Hosting\CustomServiceHost`  
  
## <a name="about-the-scenario"></a>關於案例  
 若要避免不小心洩露可能含有機密的服務中繼資料，Windows Communication Foundation (WCF) 服務的預設組態會停用中繼資料發行。 這個行為依預設為安全行為，但也表示您無法使用中繼資料匯入工具 (例如 Svcutil.exe) 來產生呼叫服務所需的用戶端程式碼，除非組態中已明確啟用服務的中繼發行行為。  
  
 啟用大量服務的中繼資料發行，需要將相同的組態項目加入至每個個別服務，而這會產生大量組態資訊，這些資訊基本上都是相同的。 除了個別設定每個服務，也撰寫命令式程式碼，讓中繼資料一次發行，然後在數個不同的服務中重複使用該程式碼。 這是藉由建立衍生自 <xref:System.ServiceModel.ServiceHost> 並覆寫 `ApplyConfiguration`() 方法，以命令方式新增中繼資料發行行為的新類別來達成。  
  
> [!IMPORTANT]
>  為了清楚說明，這個範例示範如何建立不安全的中繼資料發行端點。 未經驗證的匿名使用者可能可以使用這類端點，所以部署前必須小心謹慎，才能確保公開服務中繼資料是否適切。  
  
## <a name="implementing-a-custom-servicehost"></a>實作自訂 ServiceHost  
 <xref:System.ServiceModel.ServiceHost> 類別會公開數個繼承者可覆寫以變更服務之執行階段行為的有用虛擬方法。 例如，`ApplyConfiguration`() 方法會從組態存放區讀取服務組態資訊，並因此變更主機的 <xref:System.ServiceModel.Description.ServiceDescription>。 預設實作會從應用程式的組態檔讀取組態。 自訂實作可以覆寫 `ApplyConfiguration`()，以進一步使用命令式程式碼變更 <xref:System.ServiceModel.Description.ServiceDescription>，或甚至完全取代預設組態存放區。 例如，從資料庫而不是從應用程式的組態檔讀取服務的端點組態。  
  
 在此範例中，會希望建置新增 ServiceMetadataBehavior 的自訂 ServiceHost (可啟用中繼資料發行)，即使此行為未明確新增在服務的組態檔中也一樣。 若要達到此目的，可建立繼承自 <xref:System.ServiceModel.ServiceHost> 的新類別，並覆寫 `ApplyConfiguration`()。  
  
```  
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
  
 由於不想要忽略應用程式組態檔中已提供的任何組態，覆寫 `ApplyConfiguration`() 時所執行的第一個動做為呼叫基底實作。 完成此方法時，就可以使用下列命令式程式碼，以命令方式將 <xref:System.ServiceModel.Description.ServiceMetadataBehavior> 新增至描述。  
  
```  
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
  
 覆寫 `ApplyConfiguration`() 必須執行的最後一個動作為新增預設中繼資料端點。 一般來說，會在服務主機的 BaseAddresses 集合中，對每個 URI 建立一個中繼資料端點。  
  
```  
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
  
```  
SelfDescribingServiceHost host =   
         new SelfDescribingServiceHost( typeof( Calculator ) );  
host.Open();  
```  
  
 自訂主機仍會從應用程式的組態檔中讀取服務的端點組態，就如使用預設 <xref:System.ServiceModel.ServiceHost> 類別裝載服務一樣。 不過，由於新增邏輯以在自訂主機內啟用中繼資料發行，就不再需要於組態中明確啟用中繼資料發行行為。 當您建置其中包含多個服務的應用程式，而且想要在每個服務上啟用中繼資料發行，但不想要重複撰寫相同的組態項目時，這個方法特別有用。  
  
## <a name="using-a-custom-servicehost-in-iis-or-was"></a>在 IIS 或 WAS 中使用自訂 ServiceHost  
 在自我裝載案例中使用自訂服務主機很簡單，因為這是您的應用程式程式碼，而且主要負責建立及開啟服務主機執行個體。 在 IIS 或 WAS 裝載環境中，不過，WCF 基礎結構以動態方式具現化您的服務主機，以回應傳入的訊息。 自訂服務主機也可以在此裝載環境中使用，但形式上在 ServiceHostFactory 中需要額外的程式碼。 下列程式碼會顯示 <xref:System.ServiceModel.Activation.ServiceHostFactory> 衍生，而這個衍生會傳回自訂 `SelfDescribingServiceHost` 的執行個體。  
  
```  
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
  
 如您所見，實作自訂 ServiceHostFactory 非常簡單。 所有自訂邏輯都在 ServiceHost 實作內部，而處理站會傳回衍生類別的執行個體。  
  
 若要搭配使用自訂處理站和服務實作，必須將一些額外的中繼資料新增至服務的 .svc 檔。  
  
```  
<%@ServiceHost Service="Microsoft.ServiceModel.Samples.CalculatorService"  
               Factory="Microsoft.ServiceModel.Samples.SelfDescribingServiceHostFactory"  
               language=c# Debug="true" %>  
```  
  
 在這裡會將額外的 `Factory` 屬性新增至 `@ServiceHost` 指示詞，並傳遞自訂處理站的 CLR 型別名稱做為屬性值。 當 IIS 或 WAS 接收此服務的訊息時，WCF 裝載基礎結構會先建立 ServiceHostFactory 的執行個體，然後具現化服務主機本身呼叫`ServiceHostFactory.CreateServiceHost()`。  
  
## <a name="running-the-sample"></a>執行範例  
 雖然此範例確實提供了完整功能的用戶端和服務實作，但此範例的目的為說明如何使用自訂主機，變更服務的執行個體行為。請執行下列步驟：  
  
#### <a name="to-observe-the-effect-of-the-custom-host"></a>若要觀察自訂主機的作用  
  
1. 開啟服務的 Web.config 檔，並觀察沒有組態已明確啟用服務的中繼資料。  
  
2. 開啟服務的.svc 檔，並觀察其@ServiceHost指示詞包含 Factory 屬性，指定自訂 ServiceHostFactory 名稱。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
3. 在建立方案後，執行 Setup.bat 以便在 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 中安裝 ServiceModelSamples 應用程式。 ServiceModelSamples 目錄現在應該會顯示為 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 應用程式。  
  
4. 若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
5. 若要移除 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] 應用程式，請執行 Cleanup.bat。  
  
## <a name="see-also"></a>另請參閱

- [如何：裝載在 IIS 中的 WCF 服務](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)
