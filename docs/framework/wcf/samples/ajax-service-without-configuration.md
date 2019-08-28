---
title: 無組態的 AJAX 服務
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: b3c12801d14c7f6850a985c521c0e3fff92ba8e4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045801"
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="e6651-102">無組態的 AJAX 服務</span><span class="sxs-lookup"><span data-stu-id="e6651-102">AJAX Service Without Configuration</span></span>

<span data-ttu-id="e6651-103">這個範例示範如何使用 Windows Communication Foundation (WCF) 來建立基本的 ASP.NET 非同步 JavaScript 和 XML (AJAX) 服務 (您可以從網頁瀏覽器用戶端使用 JavaScript 程式碼存取的服務), 而不需使用任何設定設置。</span><span class="sxs-lookup"><span data-stu-id="e6651-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="e6651-104">此服務會在 .svc 檔中使用特殊語法以自動啟用 AJAX 端點。</span><span class="sxs-lookup"><span data-stu-id="e6651-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>

<span data-ttu-id="e6651-105">WCF 中的 AJAX 支援已優化, 可透過`ScriptManager`控制項與 ASP.NET ajax 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="e6651-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="e6651-106">如需搭配使用 WCF 與 ASP.NET AJAX 的範例, 請參閱[AJAX 範例](ajax.md)。</span><span class="sxs-lookup"><span data-stu-id="e6651-106">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](ajax.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e6651-107">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="e6651-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

 <span data-ttu-id="e6651-108">這個範例是以使用 HTTP POST 的 AJAX 服務為基礎所建立。</span><span class="sxs-lookup"><span data-stu-id="e6651-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="e6651-109">如[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例中所述, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>是用來裝載服務。</span><span class="sxs-lookup"><span data-stu-id="e6651-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>

```svc
<%ServiceHost
    language=c#
    Debug="true"
    Service="Microsoft.Ajax.Samples.CalculatorService
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"
%>
```

<span data-ttu-id="e6651-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 會自動將 <xref:System.ServiceModel.Description.WebScriptEndpoint> 加入至服務。</span><span class="sxs-lookup"><span data-stu-id="e6651-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="e6651-111">如果不需要對端點進行任何組態變更，您就可以從服務的 Web.config 檔案中完全移除 `<system.ServiceModel>` 區段。</span><span class="sxs-lookup"><span data-stu-id="e6651-111">If no configuration changes need to be made to the endpoint, the `<system.ServiceModel>` section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="e6651-112">Web.config 檔案會包含 ConfigFreeClientPage.aspx 所使用的一些 ASP.NET 設定。</span><span class="sxs-lookup"><span data-stu-id="e6651-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="e6651-113">如果沒有，就可以移除整個 Web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="e6651-113">If that were not the case, the entire Web.config file could be removed.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6651-114">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="e6651-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="e6651-115">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="e6651-115">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="e6651-116">如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。</span><span class="sxs-lookup"><span data-stu-id="e6651-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e6651-117">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="e6651-117">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e6651-118">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="e6651-118">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="e6651-119">請確定您在[Windows Communication Foundation 範例的一次性設定程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)中執行設定指示。</span><span class="sxs-lookup"><span data-stu-id="e6651-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="e6651-120">如[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中所述, 建立方案 ConfigFreeAjaxService。</span><span class="sxs-lookup"><span data-stu-id="e6651-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="e6651-121">流覽至`http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (不要在瀏覽器中從專案目錄開啟 configfreeclientpage.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e6651-121">Navigate to `http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx` (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>

> [!NOTE]
> <span data-ttu-id="e6651-122">執行這個範例時，請確定 IIS 中 ServiceModelSamples 資料夾的匿名驗證與 Windows 驗證並未同時啟用。</span><span class="sxs-lookup"><span data-stu-id="e6651-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="e6651-123">如果是這種情況，請停用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="e6651-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="e6651-124">在執行範例之後，請啟用 Windows 驗證並執行「iisreset」。</span><span class="sxs-lookup"><span data-stu-id="e6651-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>

## <a name="see-also"></a><span data-ttu-id="e6651-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6651-125">See also</span></span>

- [<span data-ttu-id="e6651-126">基本 AJAX 服務</span><span class="sxs-lookup"><span data-stu-id="e6651-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
