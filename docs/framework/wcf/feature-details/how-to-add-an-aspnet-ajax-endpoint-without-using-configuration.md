---
title: HOW TO：不使用組態新增 ASP.NET AJAX 端點
ms.date: 03/30/2017
ms.assetid: b05c1742-8d0a-4673-9d71-725b18a3008e
ms.openlocfilehash: 9935e2a7738796fff9a037b09237a6acbf7bf988
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185126"
---
# <a name="how-to-add-an-aspnet-ajax-endpoint-without-using-configuration"></a>HOW TO：不使用組態新增 ASP.NET AJAX 端點
Windows 通信基礎 （WCF） 允許您創建一個服務，該服務公開ASP.NET啟用 AJAX 的終結點，可以從用戶端網站上的 JavaScript 調用。 若要建立此類端點，您可以使用組態檔 (與建立其他所有 WCF 端點一樣)，或是使用不需要任何組態項目的方法。 本主題示範第二種方法。  
  
 若要以不包含組態的 ASP.NET AJAX 端點來建立服務，服務必須由網際網路資訊服務 (IIS) 加以裝載。 要使用此方法啟動ASP.NET AJAX 終結點，請在<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>.svc 檔中的[\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指令中指定 作為出廠參數。 這項自訂的處理站元件會自動設定 ASP.NET AJAX 端點，以便用戶端網站上的 JavaScript 能夠對它呼叫。  
  
 有關工作示例，請參閱[無配置的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)。  
  
 有關如何使用配置元素配置ASP.NET AJAX 終結點的概述，請參閱[：使用配置添加ASP.NET AJAX 終結點](../../../../docs/framework/wcf/feature-details/how-to-use-configuration-to-add-an-aspnet-ajax-endpoint.md)。  
  
### <a name="to-create-a-basic-wcf-service"></a>若要建立基本 WCF 服務  
  
1. 定義具有帶有<xref:System.ServiceModel.ServiceContractAttribute>屬性標記的介面的基本 WCF 服務協定。 以 <xref:System.ServiceModel.OperationContractAttribute> 標記每項作業。 請務必設定 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 屬性。  
  
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
  
1. 在應用程式中建立名為 service 且包含 .svc 副檔名的新檔案。 通過添加服務的相應[\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指令資訊來編輯此檔。 指定<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>將在[\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指令中使用，以自動設定ASP.NET AJAX 終結點。  
  
    ```text
    <%@ServiceHost
        language=c#
        Debug="true"
        Service="Microsoft.Ajax.Samples.CalculatorService"  
        Factory=System.ServiceModel.Activation.WebScriptServiceHostFactory  
    %>  
    ```  
  
2. 建置服務並從用戶端呼叫。 網際網路資訊服務 (IIS) 會在收到呼叫時啟用服務。 有關在 IIS 中託管的詳細資訊，請參閱[如何：在 IIS 中託管 WCF 服務](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)。  
  
### <a name="to-call-the-service"></a>若要呼叫服務  
  
1. 終結點在相對於 .svc 檔的空位址進行配置，因此服務現在可用，可以通過向 service.svc/\<操作> - 例如，用於`Add`操作的服務.svc/Add 來調用。 您可以將服務 URL 輸入 ASP.NET AJAX 指令碼管理員控制項的指令碼集合來加以使用。 例如，請參閱[無配置的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-without-configuration.md)。  
  
## <a name="example"></a>範例  
  
 自動設定的端點會在相對於基底 URL 的空白位址建立。 您也可以新增組態檔並搭配這個方法使用。 如果組態檔包含端點定義，則這些端點就會新增到自動設定的端點中。  
  
 例如，service.svc 會使用 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 而服務目錄則包含了 Web.config 檔案，以便透過 "soap" 相對位址上的 <xref:System.ServiceModel.BasicHttpBinding> 來定義相同服務的端點。 在此情況中，服務包含了兩個端點：一個位於 service.svc (回應 ASP.NET AJAX 的要求) 而另一個則位於 service.svc/soap (回應 SOAP 的要求)。  
  
 如果組態檔在空白的相對位址上定義了端點，並且使用了 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>，則會擲回例外狀況，而且服務也將無法啟動。  
  
 您無法在自動設定的端點上使用組態來修改設定。 如果必須修改任何設定 (例如，讀取器配額)，您不可以藉由移除 .svc 檔案中的 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 並為端點建立組態項目的方式來使用無組態檔的方式。  
  
 如果您的服務要求使用 ASP.NET 相容性模式 (例如，如果它使用 <xref:System.Web.HttpContext> 類別或 ASP.NET 授權機制) 則您還是需要組態檔來開啟此模式。 所需的配置元素是[\<服務託管環境>](../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)元素，必須按如下方式添加。  
  
 `<system.serviceModel>`  
  
 `<serviceHostingEnvironment aspNetCompatibilityEnabled="true" /> </system.serviceModel>`  
  
 有關詳細資訊，請參閱[WCF 服務和ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)主題。  
  
 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 類別是 <xref:System.ServiceModel.Activation.ServiceHostFactory> 的衍生類別。 有關服務主機工廠機制的詳細說明，請參閱[使用服務HostFactory擴展主機](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)主題。  
  
## <a name="see-also"></a>另請參閱

- [建立 ASP.NET AJAX 的 WCF 服務](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [HOW TO：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
