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
# <a name="how-to-use-configuration-to-add-an-aspnet-ajax-endpoint"></a><span data-ttu-id="92ef5-102">HOW TO：使用組態新增 ASP.NET AJAX 端點</span><span class="sxs-lookup"><span data-stu-id="92ef5-102">How to: Use Configuration to Add an ASP.NET AJAX Endpoint</span></span>
<span data-ttu-id="92ef5-103">Windows 通信基礎 （WCF） 允許您創建一個服務，使啟用ASP.NET AJAX 的終結點可用，可以從用戶端網站上的 JavaScript 調用。</span><span class="sxs-lookup"><span data-stu-id="92ef5-103">Windows Communication Foundation (WCF) allows you to create a service that makes an ASP.NET AJAX-enabled endpoint available that can be called from JavaScript on a client Web site.</span></span> <span data-ttu-id="92ef5-104">要創建此類終結點，可以使用設定檔（與所有其他 Windows 通信基礎 （WCF） 終結點一樣），也可以使用不需要任何配置元素的方法。</span><span class="sxs-lookup"><span data-stu-id="92ef5-104">To create such an endpoint, you can either use a configuration file, as with all other Windows Communication Foundation (WCF) endpoints, or use a method that does not require any configuration elements.</span></span> <span data-ttu-id="92ef5-105">本主題示範組態方法。</span><span class="sxs-lookup"><span data-stu-id="92ef5-105">This topic demonstrates the configuration approach.</span></span>  
  
 <span data-ttu-id="92ef5-106">使服務終結點ASP.NET啟用 AJAX 的過程包括將終結點配置為使用<xref:System.ServiceModel.WebHttpBinding>和 添加[\<啟用WebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)終結點行為。</span><span class="sxs-lookup"><span data-stu-id="92ef5-106">The part of the procedure that enables the service endpoint to become ASP.NET AJAX-enabled consists of configuring the endpoint to use the <xref:System.ServiceModel.WebHttpBinding> and to add the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) endpoint behavior.</span></span> <span data-ttu-id="92ef5-107">配置終結點後，實現和託管服務的步驟與任何 WCF 服務使用的步驟類似。</span><span class="sxs-lookup"><span data-stu-id="92ef5-107">After configuring the endpoint, the steps to implement and host the service are similar to those used by any WCF service.</span></span> <span data-ttu-id="92ef5-108">有關工作示例，請參閱使用[HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)的 AJAX 服務。</span><span class="sxs-lookup"><span data-stu-id="92ef5-108">For a working example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
 <span data-ttu-id="92ef5-109">有關如何在不使用配置的情況下配置ASP.NET AJAX 終結點的詳細資訊，請參閱[：添加ASP.NET AJAX 終結點而不使用配置](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md)。</span><span class="sxs-lookup"><span data-stu-id="92ef5-109">For more information about how to configure an ASP.NET AJAX endpoint without using configuration, see [How to: Add an ASP.NET AJAX Endpoint Without Using Configuration](../../../../docs/framework/wcf/feature-details/how-to-add-an-aspnet-ajax-endpoint-without-using-configuration.md).</span></span>  
  
## <a name="to-create-a-basic-wcf-service"></a><span data-ttu-id="92ef5-110">若要建立基本 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="92ef5-110">To create a basic WCF service</span></span>  
  
1. <span data-ttu-id="92ef5-111">定義具有帶有<xref:System.ServiceModel.ServiceContractAttribute>屬性標記的介面的基本 WCF 服務協定。</span><span class="sxs-lookup"><span data-stu-id="92ef5-111">Define a basic WCF service contract with an interface marked with the <xref:System.ServiceModel.ServiceContractAttribute> attribute.</span></span> <span data-ttu-id="92ef5-112">以 <xref:System.ServiceModel.OperationContractAttribute> 標記每項作業。</span><span class="sxs-lookup"><span data-stu-id="92ef5-112">Mark each operation with the <xref:System.ServiceModel.OperationContractAttribute>.</span></span> <span data-ttu-id="92ef5-113">請務必設定 <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="92ef5-113">Be sure to set the <xref:System.ServiceModel.ServiceContractAttribute.Namespace%2A> property.</span></span>  
  
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
  
2. <span data-ttu-id="92ef5-114">使用 `ICalculator` 來實作 `CalculatorService` 服務合約。</span><span class="sxs-lookup"><span data-stu-id="92ef5-114">Implement the `ICalculator` service contract with a `CalculatorService`.</span></span>  
  
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
  
3. <span data-ttu-id="92ef5-115">定義 `ICalculator` 和 `CalculatorService` 實作的命名空間，方法是將它們包裝在命名空間區塊中。</span><span class="sxs-lookup"><span data-stu-id="92ef5-115">Define a namespace for the `ICalculator` and `CalculatorService` implementations by wrapping them in a namespace block.</span></span>  
  
    ```csharp
    namespace Microsoft.Ajax.Samples
    {  
        //Include the code for ICalculator and Caculator here.  
    }  
    ```  
  
## <a name="to-create-an-aspnet-ajax-endpoint-for-the-service"></a><span data-ttu-id="92ef5-116">若要建立服務的 ASP.NET AJAX 端點</span><span class="sxs-lookup"><span data-stu-id="92ef5-116">To create an ASP.NET AJAX endpoint for the service</span></span>  
  
1. <span data-ttu-id="92ef5-117">創建行為配置並指定[\<啟用WebScript>ASP.NET](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md)啟用AJAX的服務終結點的行為。</span><span class="sxs-lookup"><span data-stu-id="92ef5-117">Create a behavior configuration and specify the [\<enableWebScript>](../../../../docs/framework/configure-apps/file-schema/wcf/enablewebscript.md) behavior for ASP.NET AJAX-enabled endpoints of the service.</span></span>  
  
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
  
2. <span data-ttu-id="92ef5-118">針對使用 <xref:System.ServiceModel.WebHttpBinding> 和 ASP.NET AJAX 行為 (上一個步驟中所定義) 的服務，建立其端點。</span><span class="sxs-lookup"><span data-stu-id="92ef5-118">Create an endpoint for the service that uses the <xref:System.ServiceModel.WebHttpBinding> and the ASP.NET AJAX behavior defined in the previous step.</span></span>  
  
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
  
## <a name="to-host-the-service-in-iis"></a><span data-ttu-id="92ef5-119">若要在 IIS 中裝載服務</span><span class="sxs-lookup"><span data-stu-id="92ef5-119">To host the service in IIS</span></span>  
  
1. <span data-ttu-id="92ef5-120">若要在 IIS 中裝載服務，請在應用程式中建立一個名為 service 且副檔名為 .svc 的新檔案。</span><span class="sxs-lookup"><span data-stu-id="92ef5-120">To host the service in IIS, create a new file named service with a .svc extension in the application.</span></span> <span data-ttu-id="92ef5-121">通過添加服務的相應[\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md)指令資訊來編輯此檔。</span><span class="sxs-lookup"><span data-stu-id="92ef5-121">Edit this file by adding the appropriate [\@ServiceHost](../../../../docs/framework/configure-apps/file-schema/wcf-directive/servicehost.md) directive information for the service.</span></span> <span data-ttu-id="92ef5-122">例如，`CalculatorService` 範例中的服務檔案內容包含下列資訊。</span><span class="sxs-lookup"><span data-stu-id="92ef5-122">For example, the content in the service file for the `CalculatorService` sample contains the following information.</span></span>  
  
    ```
    <%@ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService"  
    %>  
    ```  
  
2. <span data-ttu-id="92ef5-123">有關在 IIS 中託管的詳細資訊，請參閱[如何：在 IIS 中託管 WCF 服務](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)。</span><span class="sxs-lookup"><span data-stu-id="92ef5-123">For more information about hosting in IIS, see [How to: Host a WCF Service in IIS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md).</span></span>  
  
## <a name="to-call-the-service"></a><span data-ttu-id="92ef5-124">若要呼叫服務</span><span class="sxs-lookup"><span data-stu-id="92ef5-124">To call the service</span></span>  
  
1. <span data-ttu-id="92ef5-125">終結點在相對於 .svc 檔的空位址進行配置，因此服務現在可用，可以通過向 service.svc/\<操作> - 例如，用於`Add`操作的服務.svc/Add 來調用。</span><span class="sxs-lookup"><span data-stu-id="92ef5-125">The endpoint is configured at an empty address relative to the .svc file, so the service is now available and can be invoked by sending requests to service.svc/\<operation> - for example, service.svc/Add for the `Add` operation.</span></span> <span data-ttu-id="92ef5-126">您可以將端點 URL 輸入 ASP.NET AJAX 指令碼管理員控制項的指令碼集合來加以使用。</span><span class="sxs-lookup"><span data-stu-id="92ef5-126">You can use it by entering the endpoint URL into the Scripts collection of the ASP.NET AJAX Script Manager control.</span></span> <span data-ttu-id="92ef5-127">例如，請參閱[使用 HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)的 AJAX 服務。</span><span class="sxs-lookup"><span data-stu-id="92ef5-127">For an example, see the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92ef5-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92ef5-128">See also</span></span>

- [<span data-ttu-id="92ef5-129">建立 ASP.NET AJAX 的 WCF 服務</span><span class="sxs-lookup"><span data-stu-id="92ef5-129">Creating WCF Services for ASP.NET AJAX</span></span>](../../../../docs/framework/wcf/feature-details/creating-wcf-services-for-aspnet-ajax.md)
- [<span data-ttu-id="92ef5-130">HOW TO：將啟用 AJAX 的 ASP.NET Web 服務移轉至 WCF</span><span class="sxs-lookup"><span data-stu-id="92ef5-130">How to: Migrate AJAX-Enabled ASP.NET Web Services to WCF</span></span>](../../../../docs/framework/wcf/feature-details/how-to-migrate-ajax-enabled-aspnet-web-services-to-wcf.md)
