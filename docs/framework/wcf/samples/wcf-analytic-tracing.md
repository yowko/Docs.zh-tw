---
title: WCF 分析追蹤
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: ba4f1778059f7b960eebd42822048fa031e6961e
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044551"
---
# <a name="wcf-analytic-tracing"></a><span data-ttu-id="9dd2f-102">WCF 分析追蹤</span><span class="sxs-lookup"><span data-stu-id="9dd2f-102">WCF Analytic Tracing</span></span>
<span data-ttu-id="9dd2f-103">這個範例示範如何將您自己的追蹤事件加入至 Windows Communication Foundation (WCF) 寫入至中[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]ETW 的分析追蹤資料流程。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-103">This sample demonstrates how to add your own tracing events into the stream of analytic traces that Windows Communication Foundation (WCF) writes to ETW in [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].</span></span> <span data-ttu-id="9dd2f-104">分析追蹤的用意在於輕鬆取得服務的可視性，而不必付出高效能的代價。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-104">Analytic traces are meant to make it easy to get visibility into your services without paying a high performance penalty.</span></span> <span data-ttu-id="9dd2f-105">這個範例示範如何使用<xref:System.Diagnostics.Eventing?displayProperty=nameWithType> api 來撰寫與 WCF 服務整合的事件。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-105">This sample shows how to use the <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> APIs to write events that integrate with WCF services.</span></span>  
  
 <span data-ttu-id="9dd2f-106">如需有關 api 的<xref:System.Diagnostics.Eventing?displayProperty=nameWithType>詳細資訊, <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>請參閱。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-106">For more information about the <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> APIs, see <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="9dd2f-107">若要深入瞭解 Windows 中的事件追蹤, 請參閱[使用 ETW 改善調試和效能微調](https://go.microsoft.com/fwlink/?LinkId=166488)。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-107">To learn more about event tracing in Windows, see [Improve Debugging and Performance Tuning with ETW](https://go.microsoft.com/fwlink/?LinkId=166488).</span></span>  
  
## <a name="disposing-eventprovider"></a><span data-ttu-id="9dd2f-108">處置 EventProvider</span><span class="sxs-lookup"><span data-stu-id="9dd2f-108">Disposing EventProvider</span></span>  
 <span data-ttu-id="9dd2f-109">此範例使用實作 <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> 的 <xref:System.IDisposable?displayProperty=nameWithType> 類別。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-109">This sample uses the <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> class, which implements <xref:System.IDisposable?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9dd2f-110">在執行 WCF 服務的追蹤時, 您可能會在服務的存留期<xref:System.Diagnostics.Eventing.EventProvider>內使用的資源。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-110">When implementing tracing for a WCF service, it is likely that you may use the <xref:System.Diagnostics.Eventing.EventProvider>’s resources for the lifetime of the service.</span></span> <span data-ttu-id="9dd2f-111">因此，為了便於讀取，此範例絕不會處置已包裝的 <xref:System.Diagnostics.Eventing.EventProvider>。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-111">For this reason, and for readability, this sample never disposes of the wrapped <xref:System.Diagnostics.Eventing.EventProvider>.</span></span> <span data-ttu-id="9dd2f-112">如果您的服務因為任何原因而有不同的追蹤需求，而且您必須處置這個資源，則應根據處置 Unmanaged 資源的最佳作法修改此範例。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-112">If for some reason your service has different requirements for tracing and you must dispose of this resource, then you should modify this sample in accordance with the best practices for disposing of unmanaged resources.</span></span> <span data-ttu-id="9dd2f-113">如需處置非受控資源的詳細資訊, 請參閱[執行 Dispose 方法](https://go.microsoft.com/fwlink/?LinkId=166436)。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-113">For more information about disposing unmanaged resources, see [Implementing a Dispose Method](https://go.microsoft.com/fwlink/?LinkId=166436).</span></span>  
  
## <a name="self-hosting-vs-web-hosting"></a><span data-ttu-id="9dd2f-114">自我裝載與Web 裝載</span><span class="sxs-lookup"><span data-stu-id="9dd2f-114">Self-Hosting vs. Web Hosting</span></span>  
 <span data-ttu-id="9dd2f-115">若是 Web 裝載的服務, WCF 的分析追蹤會提供稱為 "HostReference" 的欄位, 用來識別發出追蹤的服務。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-115">For Web-hosted services, WCF’s analytic traces provide a field, called "HostReference", which is used to identify the service that is emitting the traces.</span></span> <span data-ttu-id="9dd2f-116">可延伸的使用者追蹤可以參與這個模型，而且此範例會示範其最佳作法。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-116">The extensible user traces can participate in this model and this sample demonstrates best practices for doing so.</span></span> <span data-ttu-id="9dd2f-117">當管道 '&#124;' 字元實際出現在產生的字串中時, Web 主機參考的格式可以是下列任何一項:</span><span class="sxs-lookup"><span data-stu-id="9dd2f-117">The format of a Web host reference when the pipe ‘&#124;’ character actually appears in the resulting string can be any one of the following:</span></span>  
  
- <span data-ttu-id="9dd2f-118">如果應用程式不在根目錄：</span><span class="sxs-lookup"><span data-stu-id="9dd2f-118">If the application is not at the root.</span></span>  
  
     <span data-ttu-id="9dd2f-119">\<SiteName>\<ApplicationVirtualPath>&#124;\<ServiceVirtualPath>&#124;\<ServiceName></span><span class="sxs-lookup"><span data-stu-id="9dd2f-119">\<SiteName>\<ApplicationVirtualPath>&#124;\<ServiceVirtualPath>&#124;\<ServiceName></span></span>  
  
- <span data-ttu-id="9dd2f-120">如果應用程式在根目錄：</span><span class="sxs-lookup"><span data-stu-id="9dd2f-120">If the application is at the root.</span></span>  
  
     <span data-ttu-id="9dd2f-121">\<SiteName>&#124;\<ServiceVirtualPath>&#124;\<ServiceName></span><span class="sxs-lookup"><span data-stu-id="9dd2f-121">\<SiteName>&#124;\<ServiceVirtualPath>&#124;\<ServiceName></span></span>  
  
 <span data-ttu-id="9dd2f-122">對於自我裝載的服務, WCF 的分析追蹤不會填入 "HostReference" 欄位。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-122">For self-hosted services, WCF’s analytic traces do not populate the "HostReference" field.</span></span> <span data-ttu-id="9dd2f-123">此範例中的 `WCFUserEventProvider` 類別與自我裝載之服務所使用的類別行為一致。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-123">The `WCFUserEventProvider` class in this sample behaves consistently when used by a self-hosted service.</span></span>  
  
## <a name="custom-event-details"></a><span data-ttu-id="9dd2f-124">自訂事件詳細資料</span><span class="sxs-lookup"><span data-stu-id="9dd2f-124">Custom Event Details</span></span>  
 <span data-ttu-id="9dd2f-125">WCF 的 ETW 事件提供者資訊清單會定義三個設計成由 WCF 服務作者從服務程式代碼中發出的事件。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-125">WCF’s ETW Event Provider manifest defines three events that are designed to be emitted by WCF service authors from within service code.</span></span> <span data-ttu-id="9dd2f-126">下表為顯示這三個事件的分解。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-126">The following table shows a breakdown of the three events.</span></span>  
  
|<span data-ttu-id="9dd2f-127">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="9dd2f-127">Event</span></span>|<span data-ttu-id="9dd2f-128">描述</span><span class="sxs-lookup"><span data-stu-id="9dd2f-128">Description</span></span>|<span data-ttu-id="9dd2f-129">事件 ID</span><span class="sxs-lookup"><span data-stu-id="9dd2f-129">Event ID</span></span>|  
|-----------|-----------------|--------------|  
|<span data-ttu-id="9dd2f-130">UserDefinedInformationEventOccurred</span><span class="sxs-lookup"><span data-stu-id="9dd2f-130">UserDefinedInformationEventOccurred</span></span>|<span data-ttu-id="9dd2f-131">在服務中發生需要注意但不是問題的事件，發出此事件。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-131">Emit this event when something of note happens in your service that is not a problem.</span></span> <span data-ttu-id="9dd2f-132">例如，您可能會在成功呼叫資料庫之後發出事件。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-132">For example, you might emit an event after successfully making a call to a database.</span></span>|<span data-ttu-id="9dd2f-133">301</span><span class="sxs-lookup"><span data-stu-id="9dd2f-133">301</span></span>|  
|<span data-ttu-id="9dd2f-134">UserDefinedWarningOccurred</span><span class="sxs-lookup"><span data-stu-id="9dd2f-134">UserDefinedWarningOccurred</span></span>|<span data-ttu-id="9dd2f-135">發生未來可能導致失敗的問題時，發出此事件。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-135">Emit this event when a problem occurs that may result in a failure in the future.</span></span> <span data-ttu-id="9dd2f-136">例如，當資料庫的呼叫失敗，但您能夠透過恢復成多餘的資料存放區來復原時，您可能會發出警告事件。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-136">For example, you may emit a warning event when a call to a database fails but you were able to recover by falling back to a redundant data store.</span></span>|<span data-ttu-id="9dd2f-137">302</span><span class="sxs-lookup"><span data-stu-id="9dd2f-137">302</span></span>|  
|<span data-ttu-id="9dd2f-138">UserDefinedErrorOccurred</span><span class="sxs-lookup"><span data-stu-id="9dd2f-138">UserDefinedErrorOccurred</span></span>|<span data-ttu-id="9dd2f-139">當您的服務無法如預期運作時，發出此事件。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-139">Emit this event when your service fails to behave as expected.</span></span> <span data-ttu-id="9dd2f-140">例如，如果資料庫的呼叫失敗，而且您無法從其他地方擷取資料，您可能會發出事件。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-140">For example, you might emit an event if a call to a database fails and you could not retrieve the data from elsewhere.</span></span>|<span data-ttu-id="9dd2f-141">303</span><span class="sxs-lookup"><span data-stu-id="9dd2f-141">303</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="9dd2f-142">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="9dd2f-142">To use this sample</span></span>  
  
1. <span data-ttu-id="9dd2f-143">使用 Visual Studio 2012, 開啟 [WCFAnalyticTracingExtensibility] 方案檔。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-143">Using Visual Studio 2012, open the WCFAnalyticTracingExtensibility.sln solution file.</span></span>  
  
2. <span data-ttu-id="9dd2f-144">若要建置此方案，請按 CTRL+SHIFT+B。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-144">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="9dd2f-145">若要執行此方案，請按下 CTRL+F5。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-145">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="9dd2f-146">在網頁瀏覽器中, 按一下 [**計算機 .svc**]。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-146">In the Web browser, click **Calculator.svc**.</span></span> <span data-ttu-id="9dd2f-147">服務的 WSDL 文件 URI 應該會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-147">The URI of the WSDL document for the service should appear in the browser.</span></span> <span data-ttu-id="9dd2f-148">請複製該 URI。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-148">Copy that URI.</span></span>  
  
4. <span data-ttu-id="9dd2f-149">執行 WCF 測試用戶端 (WcfTestClient .exe)。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-149">Run the WCF test client (WcfTestClient.exe).</span></span>  
  
     <span data-ttu-id="9dd2f-150">WCF 測試用戶端 (WcfTestClient) 位於`\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-150">The WCF test client (WcfTestClient.exe) is located at `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.</span></span> <span data-ttu-id="9dd2f-151">預設 Visual Studio 2012 安裝目錄是`C:\Program Files\Microsoft Visual Studio 10.0`。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-151">The default Visual Studio 2012 install dir is `C:\Program Files\Microsoft Visual Studio 10.0`.</span></span>  
  
5. <span data-ttu-id="9dd2f-152">在 WCF 測試用戶端中, 依序選取 [檔案] 和 [**新增服務**] 來新增服務。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-152">Within the WCF test client, add the service by selecting **File**, and then **Add Service**.</span></span>  
  
     <span data-ttu-id="9dd2f-153">在輸入方塊中加入端點位址。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-153">Add the endpoint address in the input box.</span></span>  
  
6. <span data-ttu-id="9dd2f-154">按一下 **[確定**] 以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-154">Click **OK** to close the dialog.</span></span>  
  
     <span data-ttu-id="9dd2f-155">ICalculator 服務會加入至 [**我的服務專案**] 底下的左窗格中。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-155">The ICalculator service is added in the left pane under **My Service Projects**.</span></span>  
  
7. <span data-ttu-id="9dd2f-156">開啟 [事件檢視器] 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-156">Open the Event Viewer application.</span></span>  
  
     <span data-ttu-id="9dd2f-157">叫用服務之前, 請先啟動事件檢視器, 並確定事件記錄檔正在接聽從 WCF 服務發出的追蹤事件。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-157">Before invoking the service, start Event Viewer and ensure that the event log is listening for tracking events emitted from the WCF service.</span></span>  
  
8. <span data-ttu-id="9dd2f-158">在 **開始** 功能表中, 選取 系統**管理工具**, 然後**事件檢視器**。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-158">From the **Start** menu, select **Administrative Tools**, and then **Event Viewer**.</span></span> <span data-ttu-id="9dd2f-159">啟用**分析**和**Debug**記錄。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-159">Enable the **Analytic** and **Debug** logs.</span></span>  
  
9. <span data-ttu-id="9dd2f-160">在事件檢視器的樹狀檢視中, 流覽至 [**事件檢視器**]、[**應用程式及服務記錄**檔]、[ **Microsoft**]、[ **Windows**] 和 [**應用程式伺服器應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-160">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application Server-Applications**.</span></span> <span data-ttu-id="9dd2f-161">以滑鼠右鍵按一下 [**應用程式伺服器-應用程式**], 選取 [ **View**], 然後**顯示 [分析與偵錯工具記錄**]。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-161">Right-click **Application Server-Applications**, select **View**, and then **Show Analytic and Debug Logs**.</span></span>  
  
     <span data-ttu-id="9dd2f-162">確定已核取 [**顯示分析和偵錯工具記錄**檔] 選項。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-162">Ensure that the **Show Analytic and Debug Logs** option is checked.</span></span> <span data-ttu-id="9dd2f-163">啟用**分析**記錄檔。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-163">Enable the **Analytic** log.</span></span>  
  
     <span data-ttu-id="9dd2f-164">在事件檢視器的樹狀檢視中, 流覽至 [**事件檢視器**]、[**應用程式及服務記錄**檔]、[ **Microsoft**]、[ **Windows**]、[**應用程式伺服器**] 和 [**分析**]。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-164">In the tree view in Event Viewer, navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**, and then **Analytic**.</span></span> <span data-ttu-id="9dd2f-165">以滑鼠右鍵按一下 [**分析**], 然後選取 [**啟用記錄**]。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-165">Right-click **Analytic** and select **Enable Log**.</span></span>  
  
10. <span data-ttu-id="9dd2f-166">使用 WCF 測試用戶端測試此服務。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-166">Test the service using the WCF Test Client.</span></span>  
  
    1. <span data-ttu-id="9dd2f-167">在 WCF 測試用戶端中, 按兩下 ICalculator 服務節點底下的 [**新增] ()** 。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-167">In the WCF Test Client, double-click **Add()** under the ICalculator service node.</span></span>  
  
         <span data-ttu-id="9dd2f-168">**Add ()** 方法會出現在右窗格中, 其中包含兩個參數。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-168">The **Add()** method appears in the right pane with two parameters.</span></span>  
  
    2. <span data-ttu-id="9dd2f-169">輸入 2 供第一個參數使用，並輸入 3 供第二個參數使用。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-169">Type in 2 for the first parameter and 3 for the second parameter.</span></span>  
  
    3. <span data-ttu-id="9dd2f-170">按一下 [叫用] 以叫用方法。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-170">Click **Invoke** to invoke the method.</span></span>  
  
11. <span data-ttu-id="9dd2f-171">移至您已開啟的 [**事件檢視器**] 視窗。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-171">Go to the **Event Viewer** window that you have already opened.</span></span> <span data-ttu-id="9dd2f-172">流覽至**事件檢視器**、**應用程式和服務記錄**檔、 **Microsoft**、 **Windows**、**應用程式伺服器-應用程式**。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-172">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span>  
  
12. <span data-ttu-id="9dd2f-173">以滑鼠右鍵按一下 [**分析**] 節點, 然後選取 [重新整理]。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-173">Right-click the **Analytic** node and select **Refresh**.</span></span>  
  
     <span data-ttu-id="9dd2f-174">這些事件會出現在右窗格中。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-174">The events appear in the right pane.</span></span>  
  
13. <span data-ttu-id="9dd2f-175">找出識別碼為 303 的事件，然後按兩下它即可開啟並檢查其內容。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-175">Locate the event with the ID of 303 and double-click it to open it up and inspect its contents.</span></span>  
  
     <span data-ttu-id="9dd2f-176">這個事件是由 ICalculator 服務`Add()`的方法發出, 並具有等於 "2 + 3 = 5" 的裝載。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-176">This event was emitted by the `Add()` method of the ICalculator service and has a payload equal to "2+3=5".</span></span>  
  
#### <a name="to-clean-up-optional"></a><span data-ttu-id="9dd2f-177">若要清除 (選擇性)</span><span class="sxs-lookup"><span data-stu-id="9dd2f-177">To clean up (Optional)</span></span>  
  
1. <span data-ttu-id="9dd2f-178">開啟**事件檢視器**。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-178">Open **Event Viewer**.</span></span>  
  
2. <span data-ttu-id="9dd2f-179">流覽至**事件檢視器**、**應用程式和服務記錄**檔、 **Microsoft**、 **Windows**和**應用程式伺服器應用程式**。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-179">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, and then **Application-Server-Applications**.</span></span> <span data-ttu-id="9dd2f-180">以滑鼠右鍵按一下 [**分析**], 然後選取 [**停用記錄**]。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-180">Right-click **Analytic** and select **Disable Log**.</span></span>  
  
3. <span data-ttu-id="9dd2f-181">流覽至**事件檢視器**、**應用程式和服務記錄**檔、 **Microsoft**、 **Windows**、**應用程式伺服器應用程式**, 然後進行**分析**。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-181">Navigate to **Event Viewer**, **Applications and Services Logs**, **Microsoft**, **Windows**, **Application-Server-Applications**, and then **Analytic**.</span></span> <span data-ttu-id="9dd2f-182">以滑鼠右鍵按一下 [**分析**], 然後選取 [**清除記錄**]。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-182">Right-click **Analytic** and select **Clear Log**.</span></span>  
  
4. <span data-ttu-id="9dd2f-183">按一下 [**清除**] 以清除事件。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-183">Click **Clear** to clear the events.</span></span>  
  
## <a name="known-issue"></a><span data-ttu-id="9dd2f-184">已知問題</span><span class="sxs-lookup"><span data-stu-id="9dd2f-184">Known Issue</span></span>  
 <span data-ttu-id="9dd2f-185">**事件檢視器**中有一個已知的問題, 可能無法將 ETW 事件解碼。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-185">There is a known issue in the **Event Viewer** where it may fail to decode ETW events.</span></span> <span data-ttu-id="9dd2f-186">您可能會看到一則錯誤訊息, 指出:「從來源 Microsoft-Windows \<-應用程式伺服器 > 事件識別碼識別碼的描述。找不到應用程式。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-186">You may see an error message that says: "The description for Event ID \<id> from source Microsoft-Windows-Application Server-Applications cannot be found.</span></span> <span data-ttu-id="9dd2f-187">本機電腦可能並未安裝引發此事件的元件，或安裝已損毀。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-187">Either the component that raises this event is not installed on your local computer or the installation is corrupted.</span></span> <span data-ttu-id="9dd2f-188">您可以在本機電腦上安裝或修復元件。」</span><span class="sxs-lookup"><span data-stu-id="9dd2f-188">You can install or repair the component on the local computer."</span></span> <span data-ttu-id="9dd2f-189">如果您遇到這個錯誤, 請從 [**動作**] 功能表中選取 [重新整理]。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-189">If you encounter this error, select **Refresh** from the **Actions** menu.</span></span> <span data-ttu-id="9dd2f-190">接著，事件應該就會正確解碼。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-190">The event should then decode properly.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="9dd2f-191">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-191">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9dd2f-192">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-192">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="9dd2f-193">如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-193">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9dd2f-194">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="9dd2f-194">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a><span data-ttu-id="9dd2f-195">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9dd2f-195">See also</span></span>

- [<span data-ttu-id="9dd2f-196">AppFabric 監視範例</span><span class="sxs-lookup"><span data-stu-id="9dd2f-196">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
