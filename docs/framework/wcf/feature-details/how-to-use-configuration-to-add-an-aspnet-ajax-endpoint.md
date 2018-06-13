---
title: HOW TO：使用組態新增 ASP.NET AJAX 端點
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: f14b441ead7c701aa4f794370fc5f54ad3b4a4e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494998"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="cbdf1-102">HOW TO：使用組態新增 ASP.NET AJAX 端點</span><span class="sxs-lookup"><span data-stu-id="cbdf1-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="cbdf1-103">Windows Communication Foundation (WCF) 可讓您建立可讓 ASP.NET ajax 端點使用，可透過 JavaScript 來呼叫用戶端網站上的服務。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="cbdf1-104">若要建立此類端點，您可以使用組態檔，如同所有其他 Windows Communication Foundation (WCF) 端點，或使用不需要任何組態項目的方法。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="cbdf1-105">本主題示範組態方法。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="cbdf1-106">可讓要變成 ASP.NET AJAX 能力的服務端點的程序的一部分包括設定端點以使用<xref:System.ServiceModel.WebHttpBinding>，並加入[ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)端點行為。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="cbdf1-107">後設定端點，將會類似於任何 WCF 服務所使用的實作與裝載服務的步驟。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="cbdf1-108">如需實用範例，請參閱[AJAX 服務使用 HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="cbdf1-109">如需如何設定 ASP.NET AJAX 端點，而不需要使用組態的詳細資訊，請參閱[如何： 加入 ASP.NET AJAX 端點而不使用組態](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="cbdf1-110">若要建立基本 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="cbdf1-110">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="cbdf1-111">定義基本的 WCF 服務合約介面標記為<xref:System.ServiceModel.ServiceContractAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="cbdf1-112">以 <xref:System.ServiceModel.OperationContractAttribute> 標記每項作業。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="cbdf1-113">請務必設定 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2.  <span data-ttu-id="cbdf1-114">使用 `ICalculator` 來實作 `CalculatorService` 服務合約。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="cbdf1-115">定義 `ICalculator` 和 `CalculatorService` 實作的命名空間，方法是將它們包裝在命名空間區塊中。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="cbdf1-116">若要建立服務的 ASP.NET AJAX 端點</span><span class="sxs-lookup"><span data-stu-id="cbdf1-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1.  <span data-ttu-id="cbdf1-117">建立行為設定，並指定[ \<enableWebScript >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) ASP.NET ajax 端點的服務行為。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2.  <span data-ttu-id="cbdf1-118">針對使用 <xref:System.ServiceModel.WebHttpBinding> 和 ASP.NET AJAX 行為 (上一個步驟中所定義) 的服務，建立其端點。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
### <a name="to-host-the-service-in-iis"></a><span data-ttu-id="cbdf1-119">若要在 IIS 中裝載服務</span><span class="sxs-lookup"><span data-stu-id="cbdf1-119">To host the service in IIS</span></span>  
  
1.  <span data-ttu-id="cbdf1-120">若要在 IIS 中裝載服務，請在應用程式中建立一個名為 service 且副檔名為 .svc 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="cbdf1-121">藉由新增適當的編輯此檔案[ @ServiceHost ](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指示詞服務的資訊。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-121">Edit this file by adding the appropriate [@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="cbdf1-122">例如，`CalculatorService` 範例中的服務檔案內容包含下列資訊。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  <span data-ttu-id="cbdf1-123">如需在 IIS 中裝載的詳細資訊，請參閱[How to： 將 WCF 服務裝載於 IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="cbdf1-124">若要呼叫服務</span><span class="sxs-lookup"><span data-stu-id="cbdf1-124">To call the service</span></span>  
  
1.  <span data-ttu-id="cbdf1-125">端點會設定在與.svc 檔，相對的空白位址，因此服務現在可以使用而且可以將要求傳送至 service.svc / 叫用\<作業 >-例如，service.svc/add`Add`作業。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="cbdf1-126">您可以將端點 URL 輸入 ASP.NET AJAX 指令碼管理員控制項的指令碼集合來加以使用。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="cbdf1-127">如需範例，請參閱[AJAX 服務使用 HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)。</span><span class="sxs-lookup"><span data-stu-id="cbdf1-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbdf1-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbdf1-128">See Also</span></span>  
 [<span data-ttu-id="cbdf1-129">建立 ASP.NET AJAX 的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="cbdf1-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)  
 [<span data-ttu-id="cbdf1-130">如何：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF</span><span class="sxs-lookup"><span data-stu-id="cbdf1-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
