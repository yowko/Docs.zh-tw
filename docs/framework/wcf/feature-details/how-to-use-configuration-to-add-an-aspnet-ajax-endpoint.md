---
title: "HOW TO：使用組態新增 ASP.NET AJAX 端點 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# HOW TO：使用組態新增 ASP.NET AJAX 端點
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 可讓您建立服務以提供啟用 ASP.NET AJAX 的端點，進而透過用戶端網站上的 JavaScript 來進行呼叫。若要建立此類端點，您可以使用組態檔 \(如同建立所有其他 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 端點一般\)，或是使用不需要任何組態項目的方法。本主題示範組態方法。  
  
 讓服務端點成為啟用了 ASP.NET AJAX 的程序部分包含設定端點使用 <xref:System.ServiceModel.WebHttpBinding> 並新增 [\<enableWebScript\>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) 端點行為。設定好端點之後，實作與裝載服務的步驟與其他 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務所採用的步驟很類似。如需實用範例，請參閱[使用 HTTP POST 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)。  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]不使用組態來設定 ASP.NET AJAX 端點的詳細資訊，請參閱 [HOW TO：不使用組態新增 ASP.NET AJAX 端點](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)。  
  
### 若要建立基本 WCF 服務  
  
1.  使用以 <xref:System.ServiceModel.ServiceContractAttribute> 屬性標記的介面來定義基本的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務合約。以 <xref:System.ServiceModel.OperationContractAttribute> 標記每項作業。請務必設定 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 屬性。  
  
    ```  
    [ServiceContract(Namespace = "MyService")]  
    public interface ICalculator  
    {  
        [OperationContract]  
         // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2.  使用 `CalculatorService` 來實作 `ICalculator` 服務合約。  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  定義 `ICalculator` 和 `CalculatorService` 實作的命名空間，方法是將它們包裝在命名空間區塊中。  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### 若要建立服務的 ASP.NET AJAX 端點  
  
1.  針對服務中啟用了 ASP.NET AJAX 的端點，建立行為組態並指定 [\<enableWebScript\>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) 行為。  
  
    ```  
    <system.serviceModel>  
        <behaviors>  
            <endpointBehaviors>  
                <behavior name="AspNetAjaxBehavior">  
                    <enableWebScript />  
                </behavior>  
            </endpointBehaviors>  
        </behaviors>  
    </system.serviceModel>  
    ```  
  
2.  針對使用 <xref:System.ServiceModel.WebHttpBinding> 和 ASP.NET AJAX 行為 \(上一個步驟中所定義\) 的服務，建立其端點。  
  
    ```  
    <system.serviceModel>  
        <services>  
            <service name="Microsoft.Ajax.Samples.CalculatorService">  
                <endpoint address=""  
                    behaviorConfiguration="AspNetAjaxBehavior"   
                    binding="webHttpBinding"  
                    contract="Microsoft.Ajax.Samples.ICalculator" />  
            </service>  
        </services>  
    </system.serviceModel>   
    ```  
  
### 若要在 IIS 中裝載服務  
  
1.  若要在 IIS 中裝載服務，請在應用程式中建立一個名為 service 且副檔名為 .svc 的新檔案。您可以為服務新增適當的 [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) 指示資訊，編輯這個檔案。例如，`CalculatorService` 範例中的服務檔案內容包含下列資訊。  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]在 IIS 中裝載的詳細資訊，請參閱 [HOW TO：在 IIS 中裝載 WCF 服務](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)。  
  
### 若要呼叫服務  
  
1.  端點會在相對於 .svc 檔案的空白位址上設定，因此服務現在可以使用而且可藉由將要求傳送至 service.svc\/\<operation\> 來叫用。例如，`Add` 作業的 service.svc\/Add。您可以將端點 URL 輸入 ASP.NET AJAX 指令碼管理員控制項的指令碼集合來加以使用。如需範例，請參閱[使用 HTTP POST 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)。  
  
## 請參閱  
 [建立 ASP.NET AJAX 的 WCF 服務](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)   
 [HOW TO：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)