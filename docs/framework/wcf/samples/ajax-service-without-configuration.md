---
title: "無組態的 AJAX 服務"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 13f74a69e05c419cc76cc8df8f58d3e3385ab35f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="35c90-102">無組態的 AJAX 服務</span><span class="sxs-lookup"><span data-stu-id="35c90-102">AJAX Service Without Configuration</span></span>
<span data-ttu-id="35c90-103">這個範例會示範如何在不使用任何組態設定的情況下，使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 來建立基本 ASP.NET Asynchronous JavaScript 與 XML (AJAX) 服務 (指您可以從 Web 瀏覽器用戶端使用 JavaScript 程式碼存取的服務)。</span><span class="sxs-lookup"><span data-stu-id="35c90-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="35c90-104">此服務會在 .svc 檔中使用特殊語法以自動啟用 AJAX 端點。</span><span class="sxs-lookup"><span data-stu-id="35c90-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>  
  
 <span data-ttu-id="35c90-105">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的 AJAX 支援已針對透過 `ScriptManager` 控制項來搭配 ASP.NET AJAX 使用完成最佳化。</span><span class="sxs-lookup"><span data-stu-id="35c90-105">AJAX support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="35c90-106">如需使用[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]與 ASP.NET AJAX，請參閱[Ajax 範例](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)。</span><span class="sxs-lookup"><span data-stu-id="35c90-106">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see the [Ajax Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35c90-107">此範例的安裝程序與建置指示位於本主題的結尾。</span><span class="sxs-lookup"><span data-stu-id="35c90-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="35c90-108">這個範例是以使用 HTTP POST 的 AJAX 服務為基礎所建立。</span><span class="sxs-lookup"><span data-stu-id="35c90-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="35c90-109">中所述[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例中，<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>用來裝載服務。</span><span class="sxs-lookup"><span data-stu-id="35c90-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>  
  
```  
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```  
  
 <span data-ttu-id="35c90-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 會自動將 <xref:System.ServiceModel.Description.WebScriptEndpoint> 加入至服務。</span><span class="sxs-lookup"><span data-stu-id="35c90-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="35c90-111">如果在不變更設定需要對端點進行\<系統。ServiceModel > 區段可以完全移除 Web.config 檔案中的服務。</span><span class="sxs-lookup"><span data-stu-id="35c90-111">If no configuration changes need to be made to the endpoint, the \<system.ServiceModel> section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="35c90-112">Web.config 檔案會包含 ConfigFreeClientPage.aspx 所使用的一些 ASP.NET 設定。</span><span class="sxs-lookup"><span data-stu-id="35c90-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="35c90-113">如果沒有，就可以移除整個 Web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="35c90-113">If that were not the case, the entire Web.config file could be removed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="35c90-114">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="35c90-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="35c90-115">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="35c90-115">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="35c90-116">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="35c90-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="35c90-117">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="35c90-117">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="35c90-118">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="35c90-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="35c90-119">請確定您執行中的安裝指示[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="35c90-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="35c90-120">中所述，建置此方案 ConfigFreeAjaxService.sln[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="35c90-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="35c90-121">瀏覽到 http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (不要使用瀏覽器從專案目錄開啟 ConfigFreeClientPage.aspx)。</span><span class="sxs-lookup"><span data-stu-id="35c90-121">Navigate to http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35c90-122">執行這個範例時，請確定 IIS 中 ServiceModelSamples 資料夾的匿名驗證與 Windows 驗證並未同時啟用。</span><span class="sxs-lookup"><span data-stu-id="35c90-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="35c90-123">如果是這種情況，請停用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="35c90-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="35c90-124">在執行範例之後，請啟用 Windows 驗證並執行「iisreset」。</span><span class="sxs-lookup"><span data-stu-id="35c90-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35c90-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="35c90-125">See Also</span></span>  
 [<span data-ttu-id="35c90-126">基本 AJAX 服務</span><span class="sxs-lookup"><span data-stu-id="35c90-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
