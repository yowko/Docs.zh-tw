---
title: HOW TO：使用組態新增 ASP.NET AJAX 端點
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 188e88d40536b1d31c72f404957ef2de4ff87b1d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573786"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="921f4-102">HOW TO：使用組態新增 ASP.NET AJAX 端點</span><span class="sxs-lookup"><span data-stu-id="921f4-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="921f4-103">Windows Communication Foundation (WCF) 可讓您建立的服務，ASP.NET ajax 的端點可供使用，可以從 JavaScript 呼叫用戶端網站上。</span><span class="sxs-lookup"><span data-stu-id="921f4-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="921f4-104">若要建立此類端點，您可以使用組態檔，如同所有其他的 Windows Communication Foundation (WCF) 端點，或使用不需要任何組態項目的的方法。</span><span class="sxs-lookup"><span data-stu-id="921f4-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="921f4-105">本主題示範組態方法。</span><span class="sxs-lookup"><span data-stu-id="921f4-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="921f4-106">設定要使用的端點所組成，可讓服務端點成為啟用 ASP.NET AJAX 的程序的一部分<xref:System.ServiceModel.WebHttpBinding>，並加入[ \<Enablewebscript&gt >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)端點行為。</span><span class="sxs-lookup"><span data-stu-id="921f4-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="921f4-107">設定端點之後, 的步驟，實作與裝載服務是類似於任何 WCF 服務所使用。</span><span class="sxs-lookup"><span data-stu-id="921f4-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="921f4-108">如需實用範例，請參閱 <<c0> [ 使用 HTTP POST 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)。</span><span class="sxs-lookup"><span data-stu-id="921f4-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="921f4-109">如需如何設定 ASP.NET AJAX 端點，而不使用組態的詳細資訊，請參閱[How to:不使用組態新增 ASP.NET AJAX 端點](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="921f4-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
### <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="921f4-110">若要建立基本 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="921f4-110">To create a basic WCF service</span></span>  
  
1.  <span data-ttu-id="921f4-111">定義基本的 WCF 服務合約介面標記為<xref:System.ServiceModel.ServiceContractAttribute>屬性。</span><span class="sxs-lookup"><span data-stu-id="921f4-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="921f4-112">以 <xref:System.ServiceModel.OperationContractAttribute> 標記每項作業。</span><span class="sxs-lookup"><span data-stu-id="921f4-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="921f4-113">請務必設定 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="921f4-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2.  <span data-ttu-id="921f4-114">使用 `ICalculator` 來實作 `CalculatorService` 服務合約。</span><span class="sxs-lookup"><span data-stu-id="921f4-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
    ```  
    public class CalculatorService : ICalculator  
    {  
        public double Add(double n1, double n2)  
        {  
            return n1 + n2;  
        }  
  
    //Other operations omitted…  
    ```  
  
3.  <span data-ttu-id="921f4-115">定義 `ICalculator` 和 `CalculatorService` 實作的命名空間，方法是將它們包裝在命名空間區塊中。</span><span class="sxs-lookup"><span data-stu-id="921f4-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```  
    Namespace Microsoft.Ajax.Samples  
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
### <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="921f4-116">若要建立服務的 ASP.NET AJAX 端點</span><span class="sxs-lookup"><span data-stu-id="921f4-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1.  <span data-ttu-id="921f4-117">建立行為組態，並指定[ \<Enablewebscript&gt >](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)服務啟用 ASP.NET AJAX 的端點行為。</span><span class="sxs-lookup"><span data-stu-id="921f4-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2.  <span data-ttu-id="921f4-118">針對使用 <xref:System.ServiceModel.WebHttpBinding> 和 ASP.NET AJAX 行為 (上一個步驟中所定義) 的服務，建立其端點。</span><span class="sxs-lookup"><span data-stu-id="921f4-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
### <a name="to-host-the-service-in-iis"></a><span data-ttu-id="921f4-119">若要在 IIS 中裝載服務</span><span class="sxs-lookup"><span data-stu-id="921f4-119">To host the service in IIS</span></span>  
  
1.  <span data-ttu-id="921f4-120">若要在 IIS 中裝載服務，請在應用程式中建立一個名為 service 且副檔名為 .svc 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="921f4-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="921f4-121">編輯此檔案加上適當[ \@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)服務的指示詞資訊。</span><span class="sxs-lookup"><span data-stu-id="921f4-121">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="921f4-122">例如，`CalculatorService` 範例中的服務檔案內容包含下列資訊。</span><span class="sxs-lookup"><span data-stu-id="921f4-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```  
    <%@ServiceHost   
    language=c#   
    Debug="true"   
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2.  <span data-ttu-id="921f4-123">如需有關如何在 IIS 中裝載的詳細資訊，請參閱[How to:將 WCF 服務裝載於 IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)。</span><span class="sxs-lookup"><span data-stu-id="921f4-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
### <a name="to-call-the-service"></a><span data-ttu-id="921f4-124">若要呼叫服務</span><span class="sxs-lookup"><span data-stu-id="921f4-124">To call the service</span></span>  
  
1.  <span data-ttu-id="921f4-125">此端點設定在相對於.svc 檔案中，空白位址上，因此服務現已推出，並可以將要求傳送至 service.svc / 叫用\<作業 >-例如，service.svc/add`Add`作業。</span><span class="sxs-lookup"><span data-stu-id="921f4-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="921f4-126">您可以將端點 URL 輸入 ASP.NET AJAX 指令碼管理員控制項的指令碼集合來加以使用。</span><span class="sxs-lookup"><span data-stu-id="921f4-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="921f4-127">如需範例，請參閱[使用 HTTP POST 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)。</span><span class="sxs-lookup"><span data-stu-id="921f4-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="921f4-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="921f4-128">See also</span></span>
- [<span data-ttu-id="921f4-129">建立 ASP.NET AJAX 的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="921f4-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="921f4-130">如何：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF</span><span class="sxs-lookup"><span data-stu-id="921f4-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
