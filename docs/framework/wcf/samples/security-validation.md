---
title: 安全性驗證
ms.date: 03/30/2017
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
author: BrucePerlerMS
ms.openlocfilehash: 4b80457fb551c2ee99f910710c5f30fa59c53a01
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47203420"
---
# <a name="security-validation"></a>安全性驗證
這個範例示範如何使用自訂行為驗證電腦上的服務，以確定服務符合特定條件。 在這個範例中，服務會經過驗證，其方式是自訂行為掃描服務上的每個端點，並檢查這些端點是否包含安全繫結項目。 此樣本根據[開始使用](../../../../docs/framework/wcf/samples/getting-started-sample.md)。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
## <a name="endpoint-validation-custom-behavior"></a>端點驗證自訂行為  
 將使用者程式碼新增至包含在 `Validate` 介面中的 <xref:System.ServiceModel.Description.IServiceBehavior> 方法，可以提供自訂行為給服務或端點用來執行使用者定義的動作。 下列程式碼是用來對服務中包含的每個端點執行迴圈，以搜尋整個繫結集合中的安全繫結。  
  
```  
public void Validate(ServiceDescription serviceDescription,   
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually gathering their    
       binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =   
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any   
        // secure binding elements. Transport, Asymmetric, and Symmetric      
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 將下列程式碼新增至 Web.config 檔案，就可以為所要辨認的服務新增 `serviceValidate` 行為延伸。  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 一旦將行為延伸新增至服務，就會立即將 `endpointValidate` 行為新增至 Web.config 檔案中的行為清單，從而新增至服務。  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 新增至 Web.config 檔案的行為及其延伸會將行為套用至個別服務；然而，當新增至 Machine.config 檔案時，則會將行為套用至電腦上所有在作用中的服務。  
  
> [!NOTE]
>  將行為新增至所有服務時，建議您最好在進行任何變更前先備份 Machine.config 檔案。  
  
 現在，請執行本範例 client\bin 目錄中提供的用戶端。 例外狀況，並出現下列訊息，就會發生: 「 要求的服務，'http://localhost/servicemodelsamples/service.svc' 無法啟動。 」 這是預料中的事，因為端點驗證行為認為該端點不安全，所以不讓服務啟動。 這個行為還會擲回內部例外狀況，以描述哪個端點不安全，並且在系統「事件檢視器」中的 [System.ServiceModel 4.0.0.0] 來源與 [WebHost] 類別下方寫入訊息。 此外，您也可以在這個範例中的服務上開啟追蹤功能。 這將允許使用者使用「服務追蹤檢視器」工具開啟產生的服務追蹤，以檢視端點驗證行為擲回的例外狀況。  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a>在事件檢閱器中檢閱失敗的端點驗證例外狀況訊息  
  
1.  按一下 **開始**功能表，然後選取**執行...**.  
  
2.  型別`eventvwr`，按一下  **確定**。  
  
3.  在 [事件檢視器] 視窗中，按一下**應用程式**。  
  
4.  按兩下 [WebHost] 類別中的最近新增的 [System.ServiceModel 4.0.0.0] 事件**應用程式**視窗來檢視不安全端點訊息。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  若要建置方案的 C# 或 Visual Basic .NET 版本，請遵循 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)中的指示。  
  
3.  若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a>另請參閱  
 [AppFabric 監控範例](https://go.microsoft.com/fwlink/?LinkId=193959)
