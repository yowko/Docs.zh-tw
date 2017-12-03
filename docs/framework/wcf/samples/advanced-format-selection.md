---
title: "進階格式選取"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e02d9082-4d55-41d8-9329-98f6d1c77f06
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b14aa97f1483b3c69bfecfa0b625e590c0c37836
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="advanced-format-selection"></a><span data-ttu-id="20dad-102">進階格式選取</span><span class="sxs-lookup"><span data-stu-id="20dad-102">Advanced Format Selection</span></span>
<span data-ttu-id="20dad-103">這個範例示範如何擴充 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] REST 程式設計模型，以支援新的傳出回應格式。</span><span class="sxs-lookup"><span data-stu-id="20dad-103">This sample demonstrates how to extend the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] REST programming model to support new outgoing response formats.</span></span> <span data-ttu-id="20dad-104">此外，這個範例使用 T4 範本將回應當做 XHTML 頁面傳回，示範如何實作檢視樣式程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="20dad-104">In addition, the sample uses a T4 Template to return the response as an XHTML page, demonstrating how a view-style programming model can be implemented.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="20dad-105">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="20dad-105">Sample Details</span></span>  
 <span data-ttu-id="20dad-106">這個範例包含一項簡單的服務，以及可對服務發出要求的用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="20dad-106">The sample consists of a simple service along with client code that makes requests to the service.</span></span>  <span data-ttu-id="20dad-107">服務支援單一 [WebGet] 作業，這項作業擁有下面這個方法簽章：`Message EchoListWithGet(string list);`</span><span class="sxs-lookup"><span data-stu-id="20dad-107">The service supports a single [WebGet] operation, which has the following method signature: `Message EchoListWithGet(string list);`</span></span>  
  
 <span data-ttu-id="20dad-108">當用戶端對服務發出要求時，它會從 `list` 查詢字串參數提供逗號分隔的項目清單，而服務會以下列其中一種格式傳回同一份清單：XML、JSON、Atom、XHTML 或 jpeg。</span><span class="sxs-lookup"><span data-stu-id="20dad-108">When the client makes a request to the service, it provides a comma-separated list of items from the `list` query-string parameter and the service returns that same list in one of the following formats: XML, JSON, Atom, XHTML, or jpeg.</span></span>  
  
 <span data-ttu-id="20dad-109">服務傳回的回應格式會先以 `format` 查詢字串參數決定，再以隨要求提供的 HTTP Accept 標頭決定。</span><span class="sxs-lookup"><span data-stu-id="20dad-109">The response format returned by the service is determined first by a `format` query-string parameter and second by an HTTP Accept header supplied with the request.</span></span> <span data-ttu-id="20dad-110">如果 `format` 查詢字串參數的值是上面其中一種格式，則回應會以該格式傳回。</span><span class="sxs-lookup"><span data-stu-id="20dad-110">If the value of `format` query-string parameter is one of the preceding formats, then the response is returned in that format.</span></span> <span data-ttu-id="20dad-111">如果 `format` 查詢字串不存在，則服務會從要求逐一查看 Accept 標頭項目，然後傳回服務支援的第一個 content-type 的格式。</span><span class="sxs-lookup"><span data-stu-id="20dad-111">If the `format` query-string is not present, then the service iterates through the Accept header elements from the request and returns the format of the first content-type that the service supports.</span></span>  
  
 <span data-ttu-id="20dad-112">值得注意的是作業的傳回類型。</span><span class="sxs-lookup"><span data-stu-id="20dad-112">The return type of the operation is worth noting.</span></span> <span data-ttu-id="20dad-113">當作業傳回的類型不是 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 時，<xref:System.ServiceModel.Channels.Message> REST 程式設計模型原本就僅支援 XML 和 JSON 回應格式。</span><span class="sxs-lookup"><span data-stu-id="20dad-113">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST programming model only natively supports XML and JSON response formats when an operation returns a type other than <xref:System.ServiceModel.Channels.Message>.</span></span> <span data-ttu-id="20dad-114">不過，使用 <xref:System.ServiceModel.Channels.Message> 做為傳回類型時，開發人員可以完全掌控應如何格式化訊息的內容。</span><span class="sxs-lookup"><span data-stu-id="20dad-114">However, when using <xref:System.ServiceModel.Channels.Message> as the return type, the developer has complete control over how the content of the message should be formatted.</span></span>  
  
 <span data-ttu-id="20dad-115">這個範例使用 <xref:System.ServiceModel.Web.WebOperationContext.CreateXmlResponse%2A>、<xref:System.ServiceModel.Web.WebOperationContext.CreateJsonResponse%2A> 和 <xref:System.ServiceModel.Web.WebOperationContext.CreateAtom10Response%2A> 方法分別將字串清單序列化為 XML、JSON 和 ATOM 訊息。</span><span class="sxs-lookup"><span data-stu-id="20dad-115">The sample uses the <xref:System.ServiceModel.Web.WebOperationContext.CreateXmlResponse%2A>, <xref:System.ServiceModel.Web.WebOperationContext.CreateJsonResponse%2A> and <xref:System.ServiceModel.Web.WebOperationContext.CreateAtom10Response%2A> methods to serialize the list of strings into XML, JSON, and ATOM messages respectively.</span></span> <span data-ttu-id="20dad-116">若為 jpeg 回應格式，則會使用 <xref:System.ServiceModel.Web.WebOperationContext.CreateStreamResponse%2A> 方法，且影像會儲存到資料流。</span><span class="sxs-lookup"><span data-stu-id="20dad-116">For the jpeg response format, the <xref:System.ServiceModel.Web.WebOperationContext.CreateStreamResponse%2A> method is used and the image is saved to the stream.</span></span> <span data-ttu-id="20dad-117">若為 XHTML 回應，則會使用 <xref:System.ServiceModel.Web.WebOperationContext.CreateTextResponse%2A> 搭配預先處理的 T4 範本，這個範本是由 .tt 檔和自動產生的 .cs 檔所組成。</span><span class="sxs-lookup"><span data-stu-id="20dad-117">For the XHTML response, the <xref:System.ServiceModel.Web.WebOperationContext.CreateTextResponse%2A> is used along with a preprocessed T4 template, which consists of a .tt file and an auto-generated .cs file.</span></span> <span data-ttu-id="20dad-118">.tt 檔可讓開發人員以包含變數和控制項結構的範本形式撰寫回應。</span><span class="sxs-lookup"><span data-stu-id="20dad-118">The .tt file allows a developer to write a response in a template form that contains variables and control structures.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="20dad-119">T4，請參閱[所使用文字範本產生成品](http://go.microsoft.com/fwlink/?LinkId=166023)。</span><span class="sxs-lookup"><span data-stu-id="20dad-119"> T4, see [Generating Artifacts By Using Text Templates](http://go.microsoft.com/fwlink/?LinkId=166023).</span></span>  
  
 <span data-ttu-id="20dad-120">此範例包含在主控台應用程式中執行的自我裝載服務和用戶端。</span><span class="sxs-lookup"><span data-stu-id="20dad-120">The sample consists of a self-hosted service and a client that runs within a console application.</span></span> <span data-ttu-id="20dad-121">當主控台應用程式執行時，用戶端會對服務發出要求，然後將相關的資訊從回應寫入至主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="20dad-121">As the console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="20dad-122">若要執行這個範例</span><span class="sxs-lookup"><span data-stu-id="20dad-122">To run this sample</span></span>  
  
1.  <span data-ttu-id="20dad-123">開啟「進階格式選取範例」的方案。</span><span class="sxs-lookup"><span data-stu-id="20dad-123">Open the solution for the Advanced Format Selection Sample.</span></span> <span data-ttu-id="20dad-124">啟動 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 時，您應該以系統管理員身分執行，才能讓範例成功執行。</span><span class="sxs-lookup"><span data-stu-id="20dad-124">When launching [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], you should run as an administrator for the sample to execute successfully.</span></span> <span data-ttu-id="20dad-125">執行這項操作，以滑鼠右鍵按一下[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]圖示，然後選擇**系統管理員身分執行**從內容功能表。</span><span class="sxs-lookup"><span data-stu-id="20dad-125">Do this by right-clicking the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] icon and choosing **Run as Administrator** from the context menu.</span></span>  
  
2.  <span data-ttu-id="20dad-126">按下 CTRL+SHIFT+B 建置方案，然後按下 Ctrl-F5，在不偵錯的情況下執行主控台應用程式 AdvancedFormatSelection 專案。</span><span class="sxs-lookup"><span data-stu-id="20dad-126">Press CTRL+SHIFT+B to build the solution and then press Ctrl-F5 to run the console application AdvancedFormatSelection project without debugging.</span></span> <span data-ttu-id="20dad-127">主控台視窗隨即出現，並提供執行中服務的 URI，以及執行中服務之 HTML 說明頁的 URI。</span><span class="sxs-lookup"><span data-stu-id="20dad-127">The console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span>  
  
3.  <span data-ttu-id="20dad-128">當範例執行時，用戶端會對服務傳送要求，然後將回應寫入至主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="20dad-128">As the sample runs, the client sends requests to the service and writes the responses to the console window.</span></span> <span data-ttu-id="20dad-129">請注意不同格式的回應：XML、JSON、Atom 和 XHTML。</span><span class="sxs-lookup"><span data-stu-id="20dad-129">Notice the different formats of the responses: XML, JSON, Atom, and XHTML.</span></span>  
  
4.  <span data-ttu-id="20dad-130">接著會提示您瀏覽至 URI，您可以在其中要求 .jpeg 格式的回應。</span><span class="sxs-lookup"><span data-stu-id="20dad-130">You are then prompted to browse to a URI in which you can request the response in a .jpeg format.</span></span> <span data-ttu-id="20dad-131">開啟瀏覽器並瀏覽至指定的 URI。</span><span class="sxs-lookup"><span data-stu-id="20dad-131">Open a browser and browse to the given URI.</span></span>  
  
5.  <span data-ttu-id="20dad-132">按下任何按鍵可終止此範例。</span><span class="sxs-lookup"><span data-stu-id="20dad-132">Press any key to terminate the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="20dad-133">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="20dad-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="20dad-134">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="20dad-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="20dad-135">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="20dad-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="20dad-136">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="20dad-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AdvancedFormatSelection`  
  
## <a name="see-also"></a><span data-ttu-id="20dad-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20dad-137">See Also</span></span>
