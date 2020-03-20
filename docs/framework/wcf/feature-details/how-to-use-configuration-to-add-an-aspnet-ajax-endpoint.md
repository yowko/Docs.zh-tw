---
title: HOW TO：使用組態新增 ASP.NET AJAX 端點
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 5314bb000371ee2d3eef2576e1edfa455aa65b90
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184828"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>HOW TO：使用組態新增 ASP.NET AJAX 端點
Windows 通信基礎 （WCF） 允許您創建一個服務，使啟用ASP.NET AJAX 的終結點可用，可以從用戶端網站上的 JavaScript 調用。 要創建此類終結點，可以使用設定檔（與所有其他 Windows 通信基礎 （WCF） 終結點一樣），也可以使用不需要任何配置元素的方法。 本主題示範組態方法。  
  
 使服務終結點ASP.NET啟用 AJAX 的過程包括將終結點配置為使用<xref:System.ServiceModel.WebHttpBinding>和 添加[\<啟用WebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)終結點行為。 配置終結點後，實現和託管服務的步驟與任何 WCF 服務使用的步驟類似。 有關工作示例，請參閱使用[HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)的 AJAX 服務。  
  
 有關如何在不使用配置的情況下配置ASP.NET AJAX 終結點的詳細資訊，請參閱[：添加ASP.NET AJAX 終結點而不使用配置](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)。  
  
## <a name="to-create-a-basic-wcf-service"></a>若要建立基本 WCF 服務  
  
1. 定義具有帶有<xref:System.ServiceModel.ServiceContractAttribute>屬性標記的介面的基本 WCF 服務協定。 以 <xref:System.ServiceModel.OperationContractAttribute> 標記每項作業。 請務必設定 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 屬性。  
  
    ```csharp
    [ServiceContract(Namespace = "MyService")]  
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
        // Other operations omitted…
    }
    ```  
  
3. 定義 `ICalculator` 和 `CalculatorService` 實作的命名空間，方法是將它們包裝在命名空間區塊中。  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>若要建立服務的 ASP.NET AJAX 端點  
  
1. 創建行為配置並指定[\<啟用WebScript>ASP.NET](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)啟用AJAX的服務終結點的行為。  
  
    ```xml  
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
  
2. 針對使用 <xref:System.ServiceModel.WebHttpBinding> 和 ASP.NET AJAX 行為 (上一個步驟中所定義) 的服務，建立其端點。  
  
    ```xml  
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
  
## <a name="to-host-the-service-in-iis"></a>若要在 IIS 中裝載服務  
  
1. 若要在 IIS 中裝載服務，請在應用程式中建立一個名為 service 且副檔名為 .svc 的新檔案。 通過添加服務的相應[\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指令資訊來編輯此檔。 例如，`CalculatorService` 範例中的服務檔案內容包含下列資訊。  
  
    ```
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. 有關在 IIS 中託管的詳細資訊，請參閱[如何：在 IIS 中託管 WCF 服務](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)。  
  
## <a name="to-call-the-service"></a>若要呼叫服務  
  
1. 終結點在相對於 .svc 檔的空位址進行配置，因此服務現在可用，可以通過向 service.svc/\<操作> - 例如，用於`Add`操作的服務.svc/Add 來調用。 您可以將端點 URL 輸入 ASP.NET AJAX 指令碼管理員控制項的指令碼集合來加以使用。 例如，請參閱[使用 HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)的 AJAX 服務。  
  
## <a name="see-also"></a>另請參閱

- [建立 ASP.NET AJAX 的 WCF 服務](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [HOW TO：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
