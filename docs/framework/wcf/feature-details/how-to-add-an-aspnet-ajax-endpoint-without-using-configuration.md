---
title: HOW TO：不使用組態新增 ASP.NET AJAX 端點
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 078580b96ab911f65790e58338951532cd7ad704
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344685"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>HOW TO：不使用組態新增 ASP.NET AJAX 端點
Windows Communication Foundation (WCF) 可讓您建立公開啟用 ASP.NET AJAX 的端點，可從 JavaScript 呼叫用戶端網站上的服務。 若要建立此類端點，您可以使用組態檔 (與建立其他所有 WCF 端點一樣)，或是使用不需要任何組態項目的方法。 本主題示範第二種方法。  
  
 若要以不包含組態的 ASP.NET AJAX 端點來建立服務，服務必須由網際網路資訊服務 (IIS) 加以裝載。 若要啟用 ASP.NET AJAX 端點使用這種方法，指定<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>中的處理站參數[ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) .svc 檔案中的指示詞。 這項自訂的處理站元件會自動設定 ASP.NET AJAX 端點，以便用戶端網站上的 JavaScript 能夠對它呼叫。  
  
 如需實用範例，請參閱 < [AJAX 服務而不需要組態](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)。  
  
 概述如何設定 ASP.NET AJAX 端點使用組態項目，請參閱[How to:使用組態新增 ASP.NET AJAX 端點](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)。  
  
### <a name="to-create-a-basic-wcf-service"></a>若要建立基本 WCF 服務  
  
1. 定義基本的 WCF 服務合約介面標記為<xref:System.ServiceModel.ServiceContractAttribute>屬性。 以 <xref:System.ServiceModel.OperationContractAttribute> 標記每項作業。 請務必設定 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 屬性。  
  
    ```csharp  
    [ServiceContract(Namespace = "MyService")]]  
    public interface ICalculator  
    {  
        [OperationContract]  
        // This operation returns the sum of d1 and d2.  
        double Add(double n1, double n2);  
  
        //Other operations omitted…  
  
    }  
    ```  
  
2. 使用 `ICalculator` 來實作 `CalculatorService` 服務合約。  
  
    ```csharp  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3. 定義 `ICalculator` 和 `CalculatorService` 實作的命名空間，方法是將它們包裝在命名空間區塊中。  
  
    ```csharp  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-host-the-service-in-internet-information-services-without-configuration"></a>若要將服務裝載到不含組態的網際網路資訊服務中  
  
1. 在應用程式中建立名為 service 且包含 .svc 副檔名的新檔案。 編輯此檔案加上適當[ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)服務的指示詞資訊。 指定<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>是要用於[ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指示詞，以自動設定 ASP.NET AJAX 端點。  
  
    ```  
    <%@ServiceHost   
        language=c#   
        Debug="true"   
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. 建置服務並從用戶端呼叫。 網際網路資訊服務 (IIS) 會在收到呼叫時啟用服務。 如需有關如何在 IIS 中裝載的詳細資訊，請參閱[How to:將 WCF 服務裝載於 IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)。  
  
### <a name="to-call-the-service"></a>若要呼叫服務  
  
1. 此端點設定在相對於.svc 檔案中，空白位址上，因此服務現已推出，並可以將要求傳送至 service.svc / 叫用\<作業 >-例如，service.svc/add`Add`作業。 您可以將服務 URL 輸入 ASP.NET AJAX 指令碼管理員控制項的指令碼集合來加以使用。 如需範例，請參閱[AJAX 服務而不需要組態](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)。  
  
## <a name="example"></a>範例  
  
 自動設定的端點會在相對於基底 URL 的空白位址建立。 您也可以新增組態檔並搭配這個方法使用。 如果組態檔包含端點定義，則這些端點就會新增到自動設定的端點中。  
  
 例如，service.svc 會使用 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 而服務目錄則包含了 Web.config 檔案，以便透過 "soap" 相對位址上的 <xref:System.ServiceModel.BasicHttpBinding> 來定義相同服務的端點。 在此情況中，服務包含了兩個端點：一個位於 service.svc (回應 ASP.NET AJAX 的要求) 而另一個則位於 service.svc/soap (回應 SOAP 的要求)。  
  
 如果組態檔在空白的相對位址上定義了端點，並且使用了 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>，則會擲回例外狀況，而且服務也將無法啟動。  
  
 您無法在自動設定的端點上使用組態來修改設定。 如果必須修改任何設定 (例如，讀取器配額)，您不可以藉由移除 .svc 檔案中的 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 並為端點建立組態項目的方式來使用無組態檔的方式。  
  
 如果您的服務要求使用 ASP.NET 相容性模式 (例如，如果它使用 <xref:System.Web.HttpContext> 類別或 ASP.NET 授權機制) 則您還是需要組態檔來開啟此模式。 所需的組態項目是[ \<serviceHostingEnvironment >](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)項目，必須加入，如下所示。  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 如需詳細資訊，請參閱 < [WCF 服務與 ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)主題。  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 類別是 <xref:System.ServiceModel.Activation.ServiceHostFactory> 的衍生類別。 服務主機處理站機制的詳細說明，請參閱 <<c0> [ 擴充裝載使用 ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)主題。  
  
## <a name="see-also"></a>另請參閱

- [建立 ASP.NET AJAX 的 WCF 服務](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [HOW TO：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
