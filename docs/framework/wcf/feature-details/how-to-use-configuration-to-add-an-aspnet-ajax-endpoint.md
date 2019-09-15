---
title: HOW TO：使用組態新增 ASP.NET AJAX 端點
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 33f99161034db2aa142a422139406a1a68d42b2c
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972269"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>作法：使用組態新增 ASP.NET AJAX 端點
Windows Communication Foundation （WCF）可讓您建立服務，讓 ASP.NET AJAX 啟用的端點可在用戶端網站上從 JavaScript 呼叫。 若要建立此類端點，您可以使用設定檔，如同所有其他的 Windows Communication Foundation （WCF）端點，或使用不需要任何設定元素的方法。 本主題示範組態方法。  
  
 讓服務端點變成 ASP.NET AJAX 啟用的程式部分包含設定端點來使用<xref:System.ServiceModel.WebHttpBinding>和，以[ \<新增 enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)端點行為。 設定端點之後，執行和裝載服務的步驟類似于任何 WCF 服務所使用的。 如需實用的範例，請參閱[使用 HTTP POST 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)。  
  
 如需如何設定 ASP.NET AJAX 端點而不使用設定的詳細資訊，請[參閱如何：新增 ASP.NET AJAX 端點](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)，而不使用設定。  
  
## <a name="to-create-a-basic-wcf-service"></a>若要建立基本 WCF 服務  
  
1. 使用以<xref:System.ServiceModel.ServiceContractAttribute>屬性標記的介面來定義基本 WCF 服務合約。 以 <xref:System.ServiceModel.OperationContractAttribute> 標記每項作業。 請務必設定 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 屬性。  
  
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
  
    //Other operations omitted…  
    ```  
  
3. 定義 `ICalculator` 和 `CalculatorService` 實作的命名空間，方法是將它們包裝在命名空間區塊中。  
  
    ```csharp
    namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>若要建立服務的 ASP.NET AJAX 端點  
  
1. 建立行為設定，並指定[ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)行為，以 ASP.NET 服務的 AJAX 啟用端點。  
  
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
  
1. 若要在 IIS 中裝載服務，請在應用程式中建立一個名為 service 且副檔名為 .svc 的新檔案。 藉由為服務新增適當[ \@的 ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指示詞資訊來編輯此檔案。 例如，`CalculatorService` 範例中的服務檔案內容包含下列資訊。  
  
    ```
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. 如需在 IIS 中裝載的詳細資訊[，請參閱如何：在 IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)中裝載 WCF 服務。  
  
## <a name="to-call-the-service"></a>若要呼叫服務  
  
1. 端點是在與 .svc 檔案相對的空白位址上設定的，因此服務現在可供使用，而且可以藉由將要求傳送至服務來加以叫\<用。 svc/作業 >-例如，作業的服務 .svc `Add` /Add。 您可以將端點 URL 輸入 ASP.NET AJAX 指令碼管理員控制項的指令碼集合來加以使用。 如需範例，請參閱[使用 HTTP POST 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)。  
  
## <a name="see-also"></a>另請參閱

- [建立 ASP.NET AJAX 的 WCF 服務](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [如何：將具備 AJAX 功能的 ASP.NET Web 服務遷移至 WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
