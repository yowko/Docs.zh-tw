---
title: 使用 HTTP POST 的 AJAX 服務
ms.date: 03/30/2017
ms.assetid: 1ac80f20-ac1c-4ed1-9850-7e49569ff44e
ms.openlocfilehash: c5e5de34573fbfc8a5c6e9607d10881941a9bed5
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972026"
---
# <a name="ajax-service-using-http-post"></a><span data-ttu-id="d1eb2-102">使用 HTTP POST 的 AJAX 服務</span><span class="sxs-lookup"><span data-stu-id="d1eb2-102">AJAX Service Using HTTP POST</span></span>

<span data-ttu-id="d1eb2-103">這個範例會示範如何使用 Windows Communication Foundation (WCF) 來建立使用 HTTP POST 的 ASP.NET 非同步 JavaScript 和 XML (AJAX) 服務。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that uses HTTP POST.</span></span> <span data-ttu-id="d1eb2-104">AJAX 是可從 Web 瀏覽器用戶端使用基本 JavaScript 程式碼存取的一種服務。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-104">An AJAX service is one that you can access by using basic JavaScript code from a Web browser client.</span></span> <span data-ttu-id="d1eb2-105">這個範例是以[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例為基礎。這兩個範例的唯一差別是使用 HTTP POST, 而不是 HTTP GET。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample; the only difference between the two samples is the use of HTTP POST instead of HTTP GET.</span></span>

<span data-ttu-id="d1eb2-106">Windows Communication Foundation (WCF) 中的 AJAX 支援已優化, 可透過`ScriptManager`控制項與 ASP.NET ajax 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-106">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="d1eb2-107">如需搭配使用 WCF 與 ASP.NET AJAX 的範例, 請參閱[AJAX 範例](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-107">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d1eb2-108">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="d1eb2-109">下列範例中的服務是不含 AJAX 特定程式碼的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span>

<span data-ttu-id="d1eb2-110">如果在<xref:System.ServiceModel.Web.WebInvokeAttribute>作業上套用屬性, <xref:System.ServiceModel.Web.WebGetAttribute>或未套用屬性, 則會使用預設 HTTP 動詞命令 ("POST")。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-110">If the <xref:System.ServiceModel.Web.WebInvokeAttribute> attribute is applied on an operation, or the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="d1eb2-111">POST 要求比 GET 要求更難建構，不過 POST 要求不會被快取。請在不適合快取的所有作業上使用 POST 要求。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-111">POST requests are harder to construct than GET requests, but they are not cached; use POST requests for all operations where caching is not appropriate.</span></span>

```csharp
[ServiceContract(Namespace = "PostAjaxService")]
public interface ICalculator
{
    [WebInvoke]
    double Add(double n1, double n2);
    //Other operations omitted…
}
```

<span data-ttu-id="d1eb2-112">您可以在服務上使用 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 來建立 AJAX 端點，如基本 AJAX 服務範例所示。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-112">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>

<span data-ttu-id="d1eb2-113">不同於 GET 要求，您無法從瀏覽器叫用 POST 服務。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-113">Unlike GET requests, you cannot invoke POST services from the browser.</span></span> <span data-ttu-id="d1eb2-114">例如, 流覽至`http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200`會導致錯誤, 因為 POST 服務`n1`預期和`n2`參數會以 JSON 格式在訊息本文中傳送, 而不是在 URL 中。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-114">For example, navigating to `http://localhost/ServiceModelSamples/service.svc/Add?n1=100&n2=200` results in an error, because the POST service expects the `n1` and `n2` parameters to be sent in the message body in the JSON format, and not in the URL.</span></span>

<span data-ttu-id="d1eb2-115">用戶端網頁 PostAjaxClientPage.aspx 包含 ASP.NET 程式碼，此程式碼會在使用者每次按下網頁上其中一個作業按鈕時叫用此服務。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-115">The client Web page PostAjaxClientPage.aspx contains ASP.NET code to invoke the service whenever the user clicks one of the operation buttons on the page.</span></span> <span data-ttu-id="d1eb2-116">服務的回應方式與[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例中的 GET 要求相同。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-116">The service responds in the same way as in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, with the GET request.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d1eb2-117">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-117">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d1eb2-118">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-118">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="d1eb2-119">如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-119">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d1eb2-120">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-120">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\PostAjaxService`

## <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d1eb2-121">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="d1eb2-121">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="d1eb2-122">請確定您已針對 Windows Communication Foundation 範例執行設定指示的[一次性設定程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-122">Ensure that you perform the setup instructions [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="d1eb2-123">如[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中所述, 建立方案 PostAjaxService。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-123">Build the solution PostAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="d1eb2-124">流覽至`http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (請勿在瀏覽器中從專案目錄開啟 postajaxclientpage.aspx)。</span><span class="sxs-lookup"><span data-stu-id="d1eb2-124">Navigate to `http://localhost/ServiceModelSamples/PostAjaxClientPage.aspx` (do not open PostAjaxClientPage.aspx in the browser from the project directory).</span></span>
