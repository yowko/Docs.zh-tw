---
title: HOW TO：使用組態新增 ASP.NET AJAX 端點
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 3a3474dc04ce2cda63157e68597d1184e9b2bf15
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43559947"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a>HOW TO：使用組態新增 ASP.NET AJAX 端點
Windows Communication Foundation (WCF) 可讓您建立的服務，ASP.NET ajax 的端點可供使用，可以從 JavaScript 呼叫用戶端網站上。 若要建立此類端點，您可以使用組態檔，如同所有其他的 Windows Communication Foundation (WCF) 端點，或使用不需要任何組態項目的的方法。 本主題示範組態方法。  
  
 設定要使用的端點所組成，可讓服務端點成為啟用 ASP.NET AJAX 的程序的一部分<xref:System.ServiceModel.WebHttpBinding>，並加入[ \<Enablewebscript&gt >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)端點行為。 設定端點之後, 的步驟，實作與裝載服務是類似於任何 WCF 服務所使用。 如需實用範例，請參閱 <<c0> [ 使用 HTTP POST 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)。  
  
 如需如何設定 ASP.NET AJAX 端點，而不使用組態的詳細資訊，請參閱[如何： 加入 ASP.NET AJAX 端點而不使用組態](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)。  
  
### <a name="to-create-a-basic-wcf-service"></a>若要建立基本 WCF 服務  
  
1.  定義基本的 WCF 服務合約介面標記為<xref:System.ServiceModel.ServiceContractAttribute>屬性。 以 <xref:System.ServiceModel.OperationContractAttribute> 標記每項作業。 請務必設定 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 屬性。  
  
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
  
2.  使用 `ICalculator` 來實作 `CalculatorService` 服務合約。  
  
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
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a>若要建立服務的 ASP.NET AJAX 端點  
  
1.  建立行為組態，並指定[ \<Enablewebscript&gt >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)服務啟用 ASP.NET AJAX 的端點行為。  
  
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
  
2.  針對使用 <xref:System.ServiceModel.WebHttpBinding> 和 ASP.NET AJAX 行為 (上一個步驟中所定義) 的服務，建立其端點。  
  
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
  
### <a name="to-host-the-service-in-iis"></a>若要在 IIS 中裝載服務  
  
1.  若要在 IIS 中裝載服務，請在應用程式中建立一個名為 service 且副檔名為 .svc 的新檔案。 編輯此檔案加上適當[ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)服務的指示詞資訊。 例如，`CalculatorService` 範例中的服務檔案內容包含下列資訊。  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  如需有關如何在 IIS 中裝載的詳細資訊，請參閱 <<c0> [ 如何： 將 WCF 服務裝載於 IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)。  
  
### <a name="to-call-the-service"></a>若要呼叫服務  
  
1.  此端點設定在相對於.svc 檔案中，空白位址上，因此服務現已推出，並可以將要求傳送至 service.svc / 叫用\<作業 >-例如，service.svc/add`Add`作業。 您可以將端點 URL 輸入 ASP.NET AJAX 指令碼管理員控制項的指令碼集合來加以使用。 如需範例，請參閱[使用 HTTP POST 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)。  
  
## <a name="see-also"></a>另請參閱  
 [建立 ASP.NET AJAX 的 WCF 服務](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [如何：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
