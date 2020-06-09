---
title: HOW TO：使用組態新增 ASP.NET AJAX 端點
ms.date: 03/30/2017
ms.assetid: 7cd0099e-dc3a-47e4-a38c-6e10f997f6ea
ms.openlocfilehash: 0aa59ce04e09d700d853f213c6fc9d3a25cdb43b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601149"
---
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="0ad24-102">HOW TO：使用組態新增 ASP.NET AJAX 端點</span><span class="sxs-lookup"><span data-stu-id="0ad24-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="0ad24-103">Windows Communication Foundation （WCF）可讓您建立服務，讓 ASP.NET AJAX 啟用的端點可在用戶端網站上從 JavaScript 呼叫。</span><span class="sxs-lookup"><span data-stu-id="0ad24-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="0ad24-104">若要建立此類端點，您可以使用設定檔，如同所有其他的 Windows Communication Foundation （WCF）端點，或使用不需要任何設定元素的方法。</span><span class="sxs-lookup"><span data-stu-id="0ad24-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="0ad24-105">本主題示範組態方法。</span><span class="sxs-lookup"><span data-stu-id="0ad24-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="0ad24-106">此程式的部分可讓服務端點變成 ASP.NET AJAX 啟用，其中包含設定端點以使用 <xref:System.ServiceModel.WebHttpBinding> 和來新增 [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) 端點行為。</span><span class="sxs-lookup"><span data-stu-id="0ad24-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="0ad24-107">設定端點之後，執行和裝載服務的步驟類似于任何 WCF 服務所使用的。</span><span class="sxs-lookup"><span data-stu-id="0ad24-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="0ad24-108">如需實用的範例，請參閱[使用 HTTP POST 的 AJAX 服務](../samples/ajax-service-using-http-post.md)。</span><span class="sxs-lookup"><span data-stu-id="0ad24-108">For a working example, see the [AJAX Service Using HTTP POST](../samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="0ad24-109">如需有關如何設定 ASP.NET AJAX 端點而不使用設定的詳細資訊，請參閱 how [to： Add a ASP.NET Ajax endpoint，而不](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)使用 configuration。</span><span class="sxs-lookup"><span data-stu-id="0ad24-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
## <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="0ad24-110">若要建立基本 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="0ad24-110">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="0ad24-111">使用以屬性標記的介面來定義基本 WCF 服務合約 <xref:System.ServiceModel.ServiceContractAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="0ad24-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="0ad24-112">以 <xref:System.ServiceModel.OperationContractAttribute> 標記每項作業。</span><span class="sxs-lookup"><span data-stu-id="0ad24-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="0ad24-113">請務必設定 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="0ad24-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2. <span data-ttu-id="0ad24-114">使用 `ICalculator` 來實作 `CalculatorService` 服務合約。</span><span class="sxs-lookup"><span data-stu-id="0ad24-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
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
  
3. <span data-ttu-id="0ad24-115">定義 `ICalculator` 和 `CalculatorService` 實作的命名空間，方法是將它們包裝在命名空間區塊中。</span><span class="sxs-lookup"><span data-stu-id="0ad24-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="0ad24-116">若要建立服務的 ASP.NET AJAX 端點</span><span class="sxs-lookup"><span data-stu-id="0ad24-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1. <span data-ttu-id="0ad24-117">建立行為設定，並指定 [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) ASP.NET 服務之 AJAX 啟用端點的行為。</span><span class="sxs-lookup"><span data-stu-id="0ad24-117">Create a behavior configuration and specify the [\<enableWebScript>](../../configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2. <span data-ttu-id="0ad24-118">針對使用 <xref:System.ServiceModel.WebHttpBinding> 和 ASP.NET AJAX 行為 (上一個步驟中所定義) 的服務，建立其端點。</span><span class="sxs-lookup"><span data-stu-id="0ad24-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
## <a name="to-host-the-service-in-iis"></a><span data-ttu-id="0ad24-119">若要在 IIS 中裝載服務</span><span class="sxs-lookup"><span data-stu-id="0ad24-119">To host the service in IIS</span></span>  
  
1. <span data-ttu-id="0ad24-120">若要在 IIS 中裝載服務，請在應用程式中建立一個名為 service 且副檔名為 .svc 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="0ad24-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="0ad24-121">藉由為服務新增適當的[ \@ ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md)指示詞資訊來編輯此檔案。</span><span class="sxs-lookup"><span data-stu-id="0ad24-121">Edit this file by adding the appropriate [\@ServiceHost](../../configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="0ad24-122">例如，`CalculatorService` 範例中的服務檔案內容包含下列資訊。</span><span class="sxs-lookup"><span data-stu-id="0ad24-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. <span data-ttu-id="0ad24-123">如需在 IIS 中裝載的詳細資訊，請參閱[如何：在 iis 中裝載 WCF 服務](how-to-host-a-wcf-service-in-iis.md)。</span><span class="sxs-lookup"><span data-stu-id="0ad24-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
## <a name="to-call-the-service"></a><span data-ttu-id="0ad24-124">若要呼叫服務</span><span class="sxs-lookup"><span data-stu-id="0ad24-124">To call the service</span></span>  
  
1. <span data-ttu-id="0ad24-125">端點是在與 .svc 檔案相對的空白位址上設定的，因此服務現在可供使用，並可透過將要求傳送至服務來叫用/ \<operation> -例如，針對作業的 .svc/Add。 `Add`</span><span class="sxs-lookup"><span data-stu-id="0ad24-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="0ad24-126">您可以將端點 URL 輸入 ASP.NET AJAX 指令碼管理員控制項的指令碼集合來加以使用。</span><span class="sxs-lookup"><span data-stu-id="0ad24-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="0ad24-127">如需範例，請參閱[使用 HTTP POST 的 AJAX 服務](../samples/ajax-service-using-http-post.md)。</span><span class="sxs-lookup"><span data-stu-id="0ad24-127">For an example, see the [AJAX Service Using HTTP POST](../samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ad24-128">請參閱</span><span class="sxs-lookup"><span data-stu-id="0ad24-128">See also</span></span>

- [<span data-ttu-id="0ad24-129">建立 ASP.NET AJAX 的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="0ad24-129">Creating WCF Services for ASP.NET AJAX</span></span>](creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="0ad24-130">HOW TO：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF</span><span class="sxs-lookup"><span data-stu-id="0ad24-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
