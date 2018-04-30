---
title: WCF 分析追蹤
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 57e3ee18848031bce8ffbb54d26353fe36ee1def
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="wcf-analytic-tracing"></a><span data-ttu-id="d9794-102">WCF 分析追蹤</span><span class="sxs-lookup"><span data-stu-id="d9794-102">WCF Analytic Tracing</span></span>
<span data-ttu-id="d9794-103">此範例示範如何將您自己的追蹤事件加入至 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 寫入到 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 之 ETW 的分析追蹤資料流。</span><span class="sxs-lookup"><span data-stu-id="d9794-103">This sample demonstrates how to add your own tracing events into the stream of analytic traces that [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] writes to ETW in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="d9794-104">分析追蹤的用意在於輕鬆取得服務的可視性，而不必付出高效能的代價。</span><span class="sxs-lookup"><span data-stu-id="d9794-104">Analytic traces are meant to make it easy to get visibility into your services without paying a high performance penalty.</span></span> <span data-ttu-id="d9794-105">此範例示範如何使用 <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> API 撰寫與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務整合的事件。</span><span class="sxs-lookup"><span data-stu-id="d9794-105">This sample shows how to use the <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> APIs to write events that integrate with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span>  
  
 <span data-ttu-id="d9794-106">如需有關<xref:System.Diagnostics.Eventing?displayProperty=nameWithType>Api，請參閱<xref:System.Diagnostics.Eventing?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="d9794-106">For more information about the <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> APIs, see <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="d9794-107">若要了解有關在 Windows 事件追蹤的詳細資訊，請參閱[改善偵錯和效能微調與 ETW](http://go.microsoft.com/fwlink/?LinkId=166488)。</span><span class="sxs-lookup"><span data-stu-id="d9794-107">To learn more about event tracing in Windows, see [Improve Debugging and Performance Tuning with ETW](http://go.microsoft.com/fwlink/?LinkId=166488).</span></span>  
  
## <a name="disposing-eventprovider"></a><span data-ttu-id="d9794-108">處置 EventProvider</span><span class="sxs-lookup"><span data-stu-id="d9794-108">Disposing EventProvider</span></span>  
 <span data-ttu-id="d9794-109">此範例使用實作 <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> 的 <xref:System.IDisposable?displayProperty=nameWithType> 類別。</span><span class="sxs-lookup"><span data-stu-id="d9794-109">This sample uses the <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> class, which implements <xref:System.IDisposable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d9794-110">實作 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的追蹤時，您可能會在服務的存留時間中使用 <xref:System.Diagnostics.Eventing.EventProvider> 的資源。</span><span class="sxs-lookup"><span data-stu-id="d9794-110">When implementing tracing for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, it is likely that you may use the <xref:System.Diagnostics.Eventing.EventProvider>’s resources for the lifetime of the service.</span></span> <span data-ttu-id="d9794-111">因此，為了便於讀取，此範例絕不會處置已包裝的 <xref:System.Diagnostics.Eventing.EventProvider>。</span><span class="sxs-lookup"><span data-stu-id="d9794-111">For this reason, and for readability, this sample never disposes of the wrapped <xref:System.Diagnostics.Eventing.EventProvider>.</span></span> <span data-ttu-id="d9794-112">如果您的服務因為任何原因而有不同的追蹤需求，而且您必須處置這個資源，則應根據處置 Unmanaged 資源的最佳作法修改此範例。</span><span class="sxs-lookup"><span data-stu-id="d9794-112">If for some reason your service has different requirements for tracing and you must dispose of this resource, then you should modify this sample in accordance with the best practices for disposing of unmanaged resources.</span></span> <span data-ttu-id="d9794-113">如需處置 unmanaged 的資源的詳細資訊，請參閱[實作 Dispose 方法](http://go.microsoft.com/fwlink/?LinkId=166436)。</span><span class="sxs-lookup"><span data-stu-id="d9794-113">For more information about disposing unmanaged resources, see [Implementing a Dispose Method](http://go.microsoft.com/fwlink/?LinkId=166436).</span></span>  
  
## <a name="self-hosting-vs-web-hosting"></a><span data-ttu-id="d9794-114">自我裝載與Web 裝載</span><span class="sxs-lookup"><span data-stu-id="d9794-114">Self-Hosting vs. Web Hosting</span></span>  
 <span data-ttu-id="d9794-115">為 Web 託管服務，WCF 的分析追蹤會提供名為"HostReference"，這用來識別發出追蹤服務的欄位。</span><span class="sxs-lookup"><span data-stu-id="d9794-115">For Web-hosted services, WCF’s analytic traces provide a field, called "HostReference", which is used to identify the service that is emitting the traces.</span></span> <span data-ttu-id="d9794-116">可延伸的使用者追蹤可以參與這個模型，而且此範例會示範其最佳作法。</span><span class="sxs-lookup"><span data-stu-id="d9794-116">The extensible user traces can participate in this model and this sample demonstrates best practices for doing so.</span></span> <span data-ttu-id="d9794-117">Web 主控件的格式會參考當管道 '&#124;' 字元實際出現在所產生的字串可以是下列任何一個：</span><span class="sxs-lookup"><span data-stu-id="d9794-117">The format of a Web host reference when the pipe ‘&#124;’ character actually appears in the resulting string can be any one of the following:</span></span>  
  
-   <span data-ttu-id="d9794-118">如果應用程式不在根目錄：</span><span class="sxs-lookup"><span data-stu-id="d9794-118">If the application is not at the root.</span></span>  
  
     <span data-ttu-id="d9794-119">\<站台名稱 >\<ApplicationVirtualPath >&#124;\<ServiceVirtualPath >&#124;\<ServiceName ></span><span class="sxs-lookup"><span data-stu-id="d9794-119">\<SiteName>\<ApplicationVirtualPath>&#124;\<ServiceVirtualPath>&#124;\<ServiceName></span></span>  
  
-   <span data-ttu-id="d9794-120">如果應用程式在根目錄：</span><span class="sxs-lookup"><span data-stu-id="d9794-120">If the application is at the root.</span></span>  
  
     <span data-ttu-id="d9794-121">\<站台名稱 >&#124;\<ServiceVirtualPath >&#124;\<ServiceName ></span><span class="sxs-lookup"><span data-stu-id="d9794-121">\<SiteName>&#124;\<ServiceVirtualPath>&#124;\<ServiceName></span></span>  
  
 <span data-ttu-id="d9794-122">對於自我裝載服務，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]的分析追蹤不會填入"HostReference"欄位。</span><span class="sxs-lookup"><span data-stu-id="d9794-122">For self-hosted services, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]’s analytic traces do not populate the "HostReference" field.</span></span> <span data-ttu-id="d9794-123">此範例中的 `WCFUserEventProvider` 類別與自我裝載之服務所使用的類別行為一致。</span><span class="sxs-lookup"><span data-stu-id="d9794-123">The `WCFUserEventProvider` class in this sample behaves consistently when used by a self-hosted service.</span></span>  
  
## <a name="custom-event-details"></a><span data-ttu-id="d9794-124">自訂事件詳細資料</span><span class="sxs-lookup"><span data-stu-id="d9794-124">Custom Event Details</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="d9794-125"> 的 ETW 事件提供者資訊清單會定義設計為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務作者從服務程式碼中所發出的三個事件。</span><span class="sxs-lookup"><span data-stu-id="d9794-125">’s ETW Event Provider manifest defines three events that are designed to be emitted by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service authors from within service code.</span></span> <span data-ttu-id="d9794-126">下表為顯示這三個事件的分解。</span><span class="sxs-lookup"><span data-stu-id="d9794-126">The following table shows a breakdown of the three events.</span></span>  
  
|<span data-ttu-id="d9794-127">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="d9794-127">Event</span></span>|<span data-ttu-id="d9794-128">描述</span><span class="sxs-lookup"><span data-stu-id="d9794-128">Description</span></span>|<span data-ttu-id="d9794-129">事件 ID</span><span class="sxs-lookup"><span data-stu-id="d9794-129">Event ID</span></span>|  
|-----------|-----------------|--------------|  
|<span data-ttu-id="d9794-130">UserDefinedInformationEventOccurred</span><span class="sxs-lookup"><span data-stu-id="d9794-130">UserDefinedInformationEventOccurred</span></span>|<span data-ttu-id="d9794-131">在服務中發生需要注意但不是問題的事件，發出此事件。</span><span class="sxs-lookup"><span data-stu-id="d9794-131">Emit this event when something of note happens in your service that is not a problem.</span></span> <span data-ttu-id="d9794-132">例如，您可能會在成功呼叫資料庫之後發出事件。</span><span class="sxs-lookup"><span data-stu-id="d9794-132">For example, you might emit an event after successfully making a call to a database.</span></span>|<span data-ttu-id="d9794-133">301</span><span class="sxs-lookup"><span data-stu-id="d9794-133">301</span></span>|  
|<span data-ttu-id="d9794-134">UserDefinedWarningOccurred</span><span class="sxs-lookup"><span data-stu-id="d9794-134">UserDefinedWarningOccurred</span></span>|<span data-ttu-id="d9794-135">發生未來可能導致失敗的問題時，發出此事件。</span><span class="sxs-lookup"><span data-stu-id="d9794-135">Emit this event when a problem occurs that may result in a failure in the future.</span></span> <span data-ttu-id="d9794-136">例如，當資料庫的呼叫失敗，但您能夠透過恢復成多餘的資料存放區來復原時，您可能會發出警告事件。</span><span class="sxs-lookup"><span data-stu-id="d9794-136">For example, you may emit a warning event when a call to a database fails but you were able to recover by falling back to a redundant data store.</span></span>|<span data-ttu-id="d9794-137">302</span><span class="sxs-lookup"><span data-stu-id="d9794-137">302</span></span>|  
|<span data-ttu-id="d9794-138">UserDefinedErrorOccurred</span><span class="sxs-lookup"><span data-stu-id="d9794-138">UserDefinedErrorOccurred</span></span>|<span data-ttu-id="d9794-139">當您的服務無法如預期運作時，發出此事件。</span><span class="sxs-lookup"><span data-stu-id="d9794-139">Emit this event when your service fails to behave as expected.</span></span> <span data-ttu-id="d9794-140">例如，如果資料庫的呼叫失敗，而且您無法從其他地方擷取資料，您可能會發出事件。</span><span class="sxs-lookup"><span data-stu-id="d9794-140">For example, you might emit an event if a call to a database fails and you could not retrieve the data from elsewhere.</span></span>|<span data-ttu-id="d9794-141">303</span><span class="sxs-lookup"><span data-stu-id="d9794-141">303</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="d9794-142">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="d9794-142">To use this sample</span></span>  
  
1.  <span data-ttu-id="d9794-143">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 WCFAnalyticTracingExtensibility.sln 方案檔案。</span><span class="sxs-lookup"><span data-stu-id="d9794-143">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the WCFAnalyticTracingExtensibility.sln solution file.</span></span>  
  
2.  <span data-ttu-id="d9794-144">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="d9794-144">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="d9794-145">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="d9794-145">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="d9794-146">在 Web 瀏覽器中，按一下**Calculator.svc**。</span><span class="sxs-lookup"><span data-stu-id="d9794-146">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="d9794-147">服務的 WSDL 文件 URI 應該會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="d9794-147">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="d9794-148">請複製該 URI。</span><span class="sxs-lookup"><span data-stu-id="d9794-148">Copy that URI.</span></span>  
  
4.  <span data-ttu-id="d9794-149">執行 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 測試用戶端 (WcfTestClient.exe)。</span><span class="sxs-lookup"><span data-stu-id="d9794-149">Run the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client (WcfTestClient.exe).</span></span>  
  
     <span data-ttu-id="d9794-150">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]測試用戶端 (WcfTestClient.exe) 位於\< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir> > \Common7\IDE\ WcfTestClient.exe (預設[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]安裝目錄是 C:\Program Files\Microsoft Visual Studio 10.0)。</span><span class="sxs-lookup"><span data-stu-id="d9794-150">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client (WcfTestClient.exe) is located in the \<[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] Install Dir>\Common7\IDE\ WcfTestClient.exe (default [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] install dir is C:\Program Files\Microsoft Visual Studio 10.0).</span></span>  
  
5.  <span data-ttu-id="d9794-151">內[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]測試用戶端中，選取 加入服務**檔案**，然後**加入服務**。</span><span class="sxs-lookup"><span data-stu-id="d9794-151">Within the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client, add the service by selecting **File**, and then **Add Service**.</span></span>  
  
     <span data-ttu-id="d9794-152">在輸入方塊中加入端點位址。</span><span class="sxs-lookup"><span data-stu-id="d9794-152">Add the endpoint address in the input box.</span></span>  
  
6.  <span data-ttu-id="d9794-153">按一下**確定**以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="d9794-153">Click **OK** to close the dialog.</span></span>  
  
     <span data-ttu-id="d9794-154">ICalculator 服務會在左窗格中加入**我的服務專案**。</span><span class="sxs-lookup"><span data-stu-id="d9794-154">The ICalculator service is added in the left pane under **My Service Projects**.</span></span>  
  
7.  <span data-ttu-id="d9794-155">開啟 [事件檢視器] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d9794-155">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="d9794-156">叫用服務之前，啟動 [事件檢視器] 並確認事件記錄正在接聽從 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務發出的追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="d9794-156">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
8.  <span data-ttu-id="d9794-157">從**啟動**功能表上，選取**系統管理工具**，然後**事件檢視器**。</span><span class="sxs-lookup"><span data-stu-id="d9794-157">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span> <span data-ttu-id="d9794-158">啟用**分析**和**偵錯**記錄檔。</span><span class="sxs-lookup"><span data-stu-id="d9794-158">Enable the **Analytic** and **Debug** logs.</span></span>  
  
9. <span data-ttu-id="d9794-159">在樹狀檢視中事件檢視器中，瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後按一下**應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="d9794-159">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="d9794-160">以滑鼠右鍵按一下**應用程式伺服器-應用程式**，選取**檢視**，然後**顯示分析與偵錯記錄檔**。</span><span class="sxs-lookup"><span data-stu-id="d9794-160">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="d9794-161">請確認**顯示分析與偵錯記錄檔**核取選項。</span><span class="sxs-lookup"><span data-stu-id="d9794-161">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span> <span data-ttu-id="d9794-162">啟用**分析**記錄檔。</span><span class="sxs-lookup"><span data-stu-id="d9794-162">Enable the **Analytic** log.</span></span>  
  
     <span data-ttu-id="d9794-163">在樹狀檢視中事件檢視器中，瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**， **應用程式伺服器-應用程式**，然後**分析**。</span><span class="sxs-lookup"><span data-stu-id="d9794-163">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**, and then **Analytic**.</span></span> <span data-ttu-id="d9794-164">以滑鼠右鍵按一下**分析**選取**啟用記錄**。</span><span class="sxs-lookup"><span data-stu-id="d9794-164">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
10. <span data-ttu-id="d9794-165">使用 WCF 測試用戶端測試此服務。</span><span class="sxs-lookup"><span data-stu-id="d9794-165">Test the service using the WCF Test Client.</span></span>  
  
    1.  <span data-ttu-id="d9794-166">在 WCF 測試用戶端中，按兩下**add （)** ICalculator 服務節點下。</span><span class="sxs-lookup"><span data-stu-id="d9794-166">In the WCF Test Client, double-click **Add()** under the ICalculator service node.</span></span>  
  
         <span data-ttu-id="d9794-167">**Add （)** 方法會出現在右窗格具有兩個參數。</span><span class="sxs-lookup"><span data-stu-id="d9794-167">The **Add()** method appears in the right pane with two parameters.</span></span>  
  
    2.  <span data-ttu-id="d9794-168">輸入 2 供第一個參數使用，並輸入 3 供第二個參數使用。</span><span class="sxs-lookup"><span data-stu-id="d9794-168">Type in 2 for the first parameter and 3 for the second parameter.</span></span>  
  
    3.  <span data-ttu-id="d9794-169">按一下**Invoke**叫用方法。</span><span class="sxs-lookup"><span data-stu-id="d9794-169">Click **Invoke** to invoke the method.</span></span>  
  
11. <span data-ttu-id="d9794-170">移至**事件檢視器**已經開啟的視窗。</span><span class="sxs-lookup"><span data-stu-id="d9794-170">Go to the **Event Viewer** window that you have already opened.</span></span> <span data-ttu-id="d9794-171">瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，**應用程式伺服器應用程式**。</span><span class="sxs-lookup"><span data-stu-id="d9794-171">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span>  
  
12. <span data-ttu-id="d9794-172">以滑鼠右鍵按一下**分析**節點，然後選取**重新整理**。</span><span class="sxs-lookup"><span data-stu-id="d9794-172">Right-click the **Analytic** node and select **Refresh**.</span></span>  
  
     <span data-ttu-id="d9794-173">這些事件會出現在右窗格中。</span><span class="sxs-lookup"><span data-stu-id="d9794-173">The events appear in the right pane.</span></span>  
  
13. <span data-ttu-id="d9794-174">找出識別碼為 303 的事件，然後按兩下它即可開啟並檢查其內容。</span><span class="sxs-lookup"><span data-stu-id="d9794-174">Locate the event with the ID of 303 and double-click it to open it up and inspect its contents.</span></span>  
  
     <span data-ttu-id="d9794-175">此事件由發出`Add()`ICalculator 服務的方法，且其裝載等於"2 + 3 = 5"。</span><span class="sxs-lookup"><span data-stu-id="d9794-175">This event was emitted by the `Add()` method of the ICalculator service and has a payload equal to "2+3=5".</span></span>  
  
#### <a name="to-clean-up-optional"></a><span data-ttu-id="d9794-176">若要清除 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="d9794-176">To clean up (Optional)</span></span>  
  
1.  <span data-ttu-id="d9794-177">開啟**事件檢視器**。</span><span class="sxs-lookup"><span data-stu-id="d9794-177">Open **Event Viewer**.</span></span>  
  
2.  <span data-ttu-id="d9794-178">瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**，然後**應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="d9794-178">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="d9794-179">以滑鼠右鍵按一下**分析**選取**停用記錄**。</span><span class="sxs-lookup"><span data-stu-id="d9794-179">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3.  <span data-ttu-id="d9794-180">瀏覽至**事件檢視器**， **Applications and Services Logs**， **Microsoft**， **Windows**， **應用程式伺服器-應用程式**，然後**分析**。</span><span class="sxs-lookup"><span data-stu-id="d9794-180">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application-Server-Applications**, and then **Analytic**.</span></span> <span data-ttu-id="d9794-181">以滑鼠右鍵按一下**分析**選取**清除記錄檔**。</span><span class="sxs-lookup"><span data-stu-id="d9794-181">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4.  <span data-ttu-id="d9794-182">按一下**清除**可清除事件。</span><span class="sxs-lookup"><span data-stu-id="d9794-182">Click **Clear** to clear the events.</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="d9794-183">已知問題</span><span class="sxs-lookup"><span data-stu-id="d9794-183">Known Issue</span></span>  
 <span data-ttu-id="d9794-184">中的已知問題**事件檢視器**位置可能無法為 ETW 事件解碼。</span><span class="sxs-lookup"><span data-stu-id="d9794-184">There is a known issue in the **Event Viewer** where it may fail to decode ETW events.</span></span> <span data-ttu-id="d9794-185">您可能會看到錯誤訊息，指出: 「 事件識別碼的描述\<識別碼 > 來源 Microsoft Windows 應用程式伺服器-應用程式找不到。</span><span class="sxs-lookup"><span data-stu-id="d9794-185">You may see an error message that says: "The description for Event ID \<id> from source Microsoft-Windows-Application Server-Applications cannot be found.</span></span> <span data-ttu-id="d9794-186">本機電腦可能並未安裝引發此事件的元件，或安裝已損毀。</span><span class="sxs-lookup"><span data-stu-id="d9794-186">Either the component that raises this event is not installed on your local computer or the installation is corrupted.</span></span> <span data-ttu-id="d9794-187">您可以安裝或修復本機電腦上的元件。 」</span><span class="sxs-lookup"><span data-stu-id="d9794-187">You can install or repair the component on the local computer."</span></span> <span data-ttu-id="d9794-188">如果您遇到這個錯誤，請選取**重新整理**從**動作**功能表。</span><span class="sxs-lookup"><span data-stu-id="d9794-188">If you encounter this error, select **Refresh** from the **Actions** menu.</span></span> <span data-ttu-id="d9794-189">接著，事件應該就會正確解碼。</span><span class="sxs-lookup"><span data-stu-id="d9794-189">The event should then decode properly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d9794-190">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="d9794-190">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d9794-191">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="d9794-191">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d9794-192">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="d9794-192">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d9794-193">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="d9794-193">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a><span data-ttu-id="d9794-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9794-194">See Also</span></span>  
 [<span data-ttu-id="d9794-195">AppFabric 監控範例</span><span class="sxs-lookup"><span data-stu-id="d9794-195">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
