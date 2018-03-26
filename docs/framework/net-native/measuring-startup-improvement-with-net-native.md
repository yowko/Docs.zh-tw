---
title: 評估使用 .NET Native 的啟動改善
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4d25b24-9c1a-4b3e-9705-97ba0d6c0289
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 03324850fbcb0264816b71cf8a8c6ad6a9688058
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="measuring-startup-improvement-with-net-native"></a><span data-ttu-id="4cecf-102">評估使用 .NET Native 的啟動改善</span><span class="sxs-lookup"><span data-stu-id="4cecf-102">Measuring Startup Improvement with .NET Native</span></span>
[!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="4cecf-103"> 可大幅改善應用程式的啟動時間。</span><span class="sxs-lookup"><span data-stu-id="4cecf-103"> significantly improves the launch time of apps.</span></span> <span data-ttu-id="4cecf-104">在可攜式、低電源的裝置上，以及用於複雜的應用程式時，這項改良功能尤其明顯。</span><span class="sxs-lookup"><span data-stu-id="4cecf-104">This improvement is particularly noticeable on portable, low-powered devices and with complex apps.</span></span> <span data-ttu-id="4cecf-105">本主題將協助您著手進行測量這項啟動改良功能所需的基本檢測。</span><span class="sxs-lookup"><span data-stu-id="4cecf-105">This topic helps you get started with the basic instrumentation needed to measure this startup improvement.</span></span>  
  
 <span data-ttu-id="4cecf-106">為加速效能調查，.NET Framework 和 Windows 使用一個名為 Windows 事件追蹤 (ETW) 的事件架構，可讓您的應用程式在事件發生時通知工具。</span><span class="sxs-lookup"><span data-stu-id="4cecf-106">To facilitate performance investigations, the .NET Framework and Windows use an event framework called Event Tracing for Windows (ETW) that allows your app to notify tooling when events happen.</span></span> <span data-ttu-id="4cecf-107">然後您可以使用名為 PerfView 的工具，輕鬆檢視及分析 ETW 事件。</span><span class="sxs-lookup"><span data-stu-id="4cecf-107">You can then use a tool called PerfView to easily view and analyze of ETW events.</span></span> <span data-ttu-id="4cecf-108">本主題將說明如何：</span><span class="sxs-lookup"><span data-stu-id="4cecf-108">This topic explains how to:</span></span>  
  
-   <span data-ttu-id="4cecf-109">使用 <xref:System.Diagnostics.Tracing.EventSource> 類別來發出事件。</span><span class="sxs-lookup"><span data-stu-id="4cecf-109">Use the <xref:System.Diagnostics.Tracing.EventSource> class to emit events.</span></span>  
  
-   <span data-ttu-id="4cecf-110">使用 PerfView 來收集這些事件。</span><span class="sxs-lookup"><span data-stu-id="4cecf-110">Use PerfView to gather those events.</span></span>  
  
-   <span data-ttu-id="4cecf-111">使用 PerfView 來顯示這些事件。</span><span class="sxs-lookup"><span data-stu-id="4cecf-111">Use PerfView to display those events.</span></span>  
  
## <a name="using-eventsource-to-emit-events"></a><span data-ttu-id="4cecf-112">使用 EventSource 來發出事件</span><span class="sxs-lookup"><span data-stu-id="4cecf-112">Using EventSource to emit events</span></span>  
 <span data-ttu-id="4cecf-113"><xref:System.Diagnostics.Tracing.EventSource> 提供可用來建立自訂事件提供者的基底類別。</span><span class="sxs-lookup"><span data-stu-id="4cecf-113"><xref:System.Diagnostics.Tracing.EventSource> provides a base class from which to create a custom event provider.</span></span> <span data-ttu-id="4cecf-114">一般而言，您會建立 <xref:System.Diagnostics.Tracing.EventSource> 的子類別，並以您自己的事件方法來包裝 `Write*` 方法。</span><span class="sxs-lookup"><span data-stu-id="4cecf-114">Generally, you create a subclass of <xref:System.Diagnostics.Tracing.EventSource> and wrap the `Write*` methods with your own event methods.</span></span> <span data-ttu-id="4cecf-115">通常會為每個 <xref:System.Diagnostics.Tracing.EventSource> 使用單一子句模式。</span><span class="sxs-lookup"><span data-stu-id="4cecf-115">A singleton pattern is generally used for each <xref:System.Diagnostics.Tracing.EventSource>.</span></span>  
  
 <span data-ttu-id="4cecf-116">例如，下列範例中的類別可以用來測量兩項效能特性：</span><span class="sxs-lookup"><span data-stu-id="4cecf-116">For example, the class in the following example can be used to measure two performance characteristics:</span></span>  
  
-   <span data-ttu-id="4cecf-117">到呼叫 `App` 類別建構函式之前的時間。</span><span class="sxs-lookup"><span data-stu-id="4cecf-117">The time until the `App` class constructor was called.</span></span>  
  
-   <span data-ttu-id="4cecf-118">到呼叫 `MainPage` 建構函式之前的時間。</span><span class="sxs-lookup"><span data-stu-id="4cecf-118">The time until the `MainPage` constructor was called.</span></span>  
  
 [!code-csharp[ProjectN_ETW#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw1.cs#1)]  
  
 <span data-ttu-id="4cecf-119">這裡有幾件事要特別注意。</span><span class="sxs-lookup"><span data-stu-id="4cecf-119">There are a few things to notice here.</span></span> <span data-ttu-id="4cecf-120">首先，單一子句會建立在 `AppEventSource.Log` 中。</span><span class="sxs-lookup"><span data-stu-id="4cecf-120">First, a singleton is created in `AppEventSource.Log`.</span></span> <span data-ttu-id="4cecf-121">該執行個體將會用於所有記錄。</span><span class="sxs-lookup"><span data-stu-id="4cecf-121">That instance will be used for all logging.</span></span> <span data-ttu-id="4cecf-122">第二，每個事件方法都有 <xref:System.Diagnostics.Tracing.EventAttribute>。</span><span class="sxs-lookup"><span data-stu-id="4cecf-122">Second, each event method has an <xref:System.Diagnostics.Tracing.EventAttribute>.</span></span> <span data-ttu-id="4cecf-123">這樣有助於工具將 <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> 方法的索引與在 `AppEventSource` 上呼叫的方法建立關聯。</span><span class="sxs-lookup"><span data-stu-id="4cecf-123">This helps tooling associate the index of the <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A> method with the method that was called on `AppEventSource`.</span></span>  
  
 <span data-ttu-id="4cecf-124">請注意，這些事件僅為範例。</span><span class="sxs-lookup"><span data-stu-id="4cecf-124">Note that these events are purely illustrative.</span></span> <span data-ttu-id="4cecf-125">大部分應用程式程式碼會在這些事件之後執行。</span><span class="sxs-lookup"><span data-stu-id="4cecf-125">Most app code will run after these events.</span></span> <span data-ttu-id="4cecf-126">您應該了解程式碼中的哪些事件對應至使用者互動、評量並改善這些基準測試。</span><span class="sxs-lookup"><span data-stu-id="4cecf-126">You should understand which events in code correspond to user interactions, measure those, and improve those benchmarks.</span></span> <span data-ttu-id="4cecf-127">此外，事件本身只會及時記錄單一執行個體。</span><span class="sxs-lookup"><span data-stu-id="4cecf-127">Also, the events themselves log only a single instance in time.</span></span> <span data-ttu-id="4cecf-128">如果每項作業都有成對的開始和停止事件，通常會很有用。</span><span class="sxs-lookup"><span data-stu-id="4cecf-128">It’s often useful to have paired start and stop events for every operation.</span></span> <span data-ttu-id="4cecf-129">檢查應用程式啟動時，開始事件通常是作業系統發出的「處理/開始」事件。</span><span class="sxs-lookup"><span data-stu-id="4cecf-129">When examining app startup, the start event is generally the "Process/Start" event that the operating system emits.</span></span>  
  
 <span data-ttu-id="4cecf-130">例如，假設您正在建立 RSS 閱讀程式。</span><span class="sxs-lookup"><span data-stu-id="4cecf-130">For example, suppose you are creating an RSS reader.</span></span> <span data-ttu-id="4cecf-131">幾個記錄事件的有趣位置是：</span><span class="sxs-lookup"><span data-stu-id="4cecf-131">A few interesting locations to log an event are:</span></span>  
  
-   <span data-ttu-id="4cecf-132">第一次呈現主頁面時。</span><span class="sxs-lookup"><span data-stu-id="4cecf-132">When the main page is first rendered.</span></span>  
  
-   <span data-ttu-id="4cecf-133">從本機儲存體將舊的 RSS 報導還原序列化時。</span><span class="sxs-lookup"><span data-stu-id="4cecf-133">When old RSS stories are deserialized from local storage.</span></span>  
  
-   <span data-ttu-id="4cecf-134">您的應用程式開始同步處理新的報導時。</span><span class="sxs-lookup"><span data-stu-id="4cecf-134">When your app begins syncing new stories.</span></span>  
  
-   <span data-ttu-id="4cecf-135">您的應用程式已經完成同步處理新的報導時。</span><span class="sxs-lookup"><span data-stu-id="4cecf-135">When your app has finished syncing new stories.</span></span>  
  
 <span data-ttu-id="4cecf-136">檢測應用程式很簡單：只要在衍生的類別上呼叫適當的方法即可。</span><span class="sxs-lookup"><span data-stu-id="4cecf-136">Instrumenting an app is straightforward: Just call the appropriate method on the derived class.</span></span> <span data-ttu-id="4cecf-137">使用先前範例中的 `AppEventSource`，您可以檢測應用程式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="4cecf-137">Using `AppEventSource` from the previous example, you can instrument an app as follows:</span></span>  
  
 [!code-csharp[ProjectN_ETW#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_etw/cs/etw2.cs#2)]  
  
 <span data-ttu-id="4cecf-138">檢測應用程式之後，您即可準備收集事件。</span><span class="sxs-lookup"><span data-stu-id="4cecf-138">When the app is instrumented, you’re ready to gather events.</span></span>  
  
## <a name="gathering-events-with-perfview"></a><span data-ttu-id="4cecf-139">使用 PerfView 收集事件</span><span class="sxs-lookup"><span data-stu-id="4cecf-139">Gathering events with PerfView</span></span>  
 <span data-ttu-id="4cecf-140">PerfView 會使用 ETW 事件來協助您在應用程式上進行各種效能調查。</span><span class="sxs-lookup"><span data-stu-id="4cecf-140">PerfView uses ETW events to help you do all sorts of performance investigations on your app.</span></span> <span data-ttu-id="4cecf-141">它也有包含組態 GUI，可讓您針對不同類型的事件開啟或關閉記錄功能。</span><span class="sxs-lookup"><span data-stu-id="4cecf-141">It also includes a configuration GUI that lets you turn logging for different types of events on or off.</span></span> <span data-ttu-id="4cecf-142">PerfView 是一種免費工具，可以從 [Microsoft 下載中心](http://www.microsoft.com/download/details.aspx?id=28567)下載。</span><span class="sxs-lookup"><span data-stu-id="4cecf-142">PerfView is a free tool and can be downloaded from the [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=28567).</span></span> <span data-ttu-id="4cecf-143">如需詳細資訊，請觀看 [PerfView 教學課程影片](http://channel9.msdn.com/Series/PerfView-Tutorial)。</span><span class="sxs-lookup"><span data-stu-id="4cecf-143">For more information, watch the [PerfView tutorial videos](http://channel9.msdn.com/Series/PerfView-Tutorial).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4cecf-144">PerfView 不能用來在 ARM 系統上收集事件。</span><span class="sxs-lookup"><span data-stu-id="4cecf-144">PerfView cannot be used to collect events on ARM systems.</span></span> <span data-ttu-id="4cecf-145">若要在 ARM 系統上收集事件，請使用 Windows 效能記錄程式 (WPR)。</span><span class="sxs-lookup"><span data-stu-id="4cecf-145">To collect events on ARM systems, use Windows Performance Recorder (WPR).</span></span> <span data-ttu-id="4cecf-146">如需詳細資訊，請參閱 [Vance Morrison 的部落格文章](http://blogs.msdn.com/b/vancem/archive/2012/12/19/collecting-etw-perfview-data-on-an-windows-rt-winrt-arm-surface-device.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4cecf-146">For more information, see [Vance Morrison's blog post](http://blogs.msdn.com/b/vancem/archive/2012/12/19/collecting-etw-perfview-data-on-an-windows-rt-winrt-arm-surface-device.aspx).</span></span>  
  
 <span data-ttu-id="4cecf-147">您也可以從命令列叫用 PerfView。</span><span class="sxs-lookup"><span data-stu-id="4cecf-147">You can also invoke PerfView from the command line.</span></span> <span data-ttu-id="4cecf-148">如果只要從您的提供者記錄事件，請開啟 [命令提示字元] 視窗，並輸入命令：</span><span class="sxs-lookup"><span data-stu-id="4cecf-148">To log only the events from your provider, open the Command Prompt window and enter the command:</span></span>  
  
```  
perfview -KernelEvents:Process -OnlyProviders:*MyCompany-MyApp collect outputFile   
```  
  
 <span data-ttu-id="4cecf-149">其中：</span><span class="sxs-lookup"><span data-stu-id="4cecf-149">where:</span></span>  
  
 `-KernelEvents:Process`  
 <span data-ttu-id="4cecf-150">指出您想要知道處理程序何時開始和停止。</span><span class="sxs-lookup"><span data-stu-id="4cecf-150">Indicates that you want to know when the process starts and stops.</span></span> <span data-ttu-id="4cecf-151">您需要應用程式的「處理/開始」事件，以將其從其他事件時間減去。</span><span class="sxs-lookup"><span data-stu-id="4cecf-151">You need the Process/Start event for your app so it can be subtracted from other event times.</span></span>  
  
 `-OnlyProviders:*MyCompany-MyApp`  
 <span data-ttu-id="4cecf-152">請關閉 PerfView 預設開啟的其他提供者，並開啟 MyCompany-MyApp 提供者。</span><span class="sxs-lookup"><span data-stu-id="4cecf-152">Turns off other providers that PerfView turns on by default, and turns on the MyCompany-MyApp provider.</span></span>  <span data-ttu-id="4cecf-153">(星號表示其為 <xref:System.Diagnostics.Tracing.EventSource>。)</span><span class="sxs-lookup"><span data-stu-id="4cecf-153">(The asterisk indicates that it is an <xref:System.Diagnostics.Tracing.EventSource>.)</span></span>  
  
 `collect outputFile`  
 <span data-ttu-id="4cecf-154">指出您想要開始收集資料，並將資料儲存至 outputFile.etl.zip。</span><span class="sxs-lookup"><span data-stu-id="4cecf-154">Indicates that you want to start collection and save the data to outputFile.etl.zip.</span></span>  
  
 <span data-ttu-id="4cecf-155">啟動 PerfView 之後，請執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4cecf-155">Run your app after starting PerfView.</span></span> <span data-ttu-id="4cecf-156">執行您的應用程式時，要記得幾件事：</span><span class="sxs-lookup"><span data-stu-id="4cecf-156">There are a few things to remember when running your app:</span></span>  
  
-   <span data-ttu-id="4cecf-157">使用發行組建，而不是偵錯組建。</span><span class="sxs-lookup"><span data-stu-id="4cecf-157">Use a release build, not a debug build.</span></span> <span data-ttu-id="4cecf-158">偵錯組建通常會包含額外的錯誤檢查和錯誤處理程式碼，可能會使您的應用程式執行速度比預期慢。</span><span class="sxs-lookup"><span data-stu-id="4cecf-158">Debug builds often contain extra error checking and error handling code that can cause your app to run slower than expected.</span></span>  
  
-   <span data-ttu-id="4cecf-159">附加偵錯工具來執行您的應用程式會影響應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="4cecf-159">Running your app with a debugger attached affects the performance of your app.</span></span>  
  
-   <span data-ttu-id="4cecf-160">Windows 會使用多個快取策略來加速應用程式啟動時間。</span><span class="sxs-lookup"><span data-stu-id="4cecf-160">Windows uses multiple caching strategies to speed up app launch times.</span></span> <span data-ttu-id="4cecf-161">如果您的應用程式目前快取在記憶體中，而且不必從磁碟載入，則啟動速度會較快。</span><span class="sxs-lookup"><span data-stu-id="4cecf-161">If your app is currently cached in memory and doesn't have to be loaded from disk, it will start faster.</span></span> <span data-ttu-id="4cecf-162">若要確保一致性，請在開始測量之前，將您的應用程式開始並關閉數次。</span><span class="sxs-lookup"><span data-stu-id="4cecf-162">To ensure consistency, start and close your app a few times before measuring it.</span></span>  
  
 <span data-ttu-id="4cecf-163">如果您已經執行您的應用程式，而 PerfView 可以收集發出的事件，請選擇 [停止收集] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4cecf-163">When you’ve run your app so that PerfView can collect emitted events, choose the **Stop Collection** button.</span></span> <span data-ttu-id="4cecf-164">一般而言，您應該先停止收集，再關閉應用程式，這樣才不會收集到無關的事件。</span><span class="sxs-lookup"><span data-stu-id="4cecf-164">Generally, you should stop collection before closing your app so you don’t get extraneous events.</span></span> <span data-ttu-id="4cecf-165">不過，如果您要測量關機或暫停效能，您就會想要繼續收集。</span><span class="sxs-lookup"><span data-stu-id="4cecf-165">However, if you’re measuring shutdown or suspension performance, you’ll want to continue collection.</span></span>  
  
## <a name="displaying-the-events"></a><span data-ttu-id="4cecf-166">顯示事件</span><span class="sxs-lookup"><span data-stu-id="4cecf-166">Displaying the events</span></span>  
 <span data-ttu-id="4cecf-167">若要檢視已收集的事件，請使用 PerfView 來開啟您建立的 .etl 或 .etl.zip 檔案，然後選擇 [事件]。</span><span class="sxs-lookup"><span data-stu-id="4cecf-167">To view the events that have already been collected, use PerfView to open the .etl or .etl.zip file you created and choose **Events**.</span></span> <span data-ttu-id="4cecf-168">ETW 將已經收集大量事件的相關資訊，包括來自其他處理序的事件。</span><span class="sxs-lookup"><span data-stu-id="4cecf-168">ETW will have collected information about a large number of events, including events from other processes.</span></span> <span data-ttu-id="4cecf-169">若要專注您的調查，請在 [事件] 檢視中填寫下列文字方塊：</span><span class="sxs-lookup"><span data-stu-id="4cecf-169">To focus your investigation, complete the following text boxes in the events view:</span></span>  
  
-   <span data-ttu-id="4cecf-170">在 [Process Filter] \(處理序篩選) 方塊中，指定您的應用程式名稱 (不含 ".exe")。</span><span class="sxs-lookup"><span data-stu-id="4cecf-170">In the **Process Filter** box, specify your app name (without ".exe").</span></span>  
  
-   <span data-ttu-id="4cecf-171">在 [Event Types Filter] \(事件類型篩選) 方塊中，指定 `Process/Start | MyCompany-MyApp`。</span><span class="sxs-lookup"><span data-stu-id="4cecf-171">In the **Event Types Filter** box, specify `Process/Start | MyCompany-MyApp`.</span></span> <span data-ttu-id="4cecf-172">這會從 MyCompany-MyApp 和 Windows 核心/處理/開始事件設定事件的篩選。</span><span class="sxs-lookup"><span data-stu-id="4cecf-172">This sets a filter for events from MyCompany-MyApp and the Windows Kernel/Process/Start event.</span></span>  
  
 <span data-ttu-id="4cecf-173">選取左窗格中列出的所有事件 (Ctrl-A)，然後選擇 **Enter** 鍵。</span><span class="sxs-lookup"><span data-stu-id="4cecf-173">Select all the events listed in the left pane (Ctrl-A) and choose the **Enter** key.</span></span> <span data-ttu-id="4cecf-174">現在，您應該可以看到每個事件的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="4cecf-174">Now, you should be able to see the timestamps from each event.</span></span> <span data-ttu-id="4cecf-175">這些時間戳記相對於追蹤的開始，所以您必須處理序的開始時間減去每個事件的時間，以識別自啟動後所耗用的時間。</span><span class="sxs-lookup"><span data-stu-id="4cecf-175">These timestamps are relative to the start of the trace, so you have to subtract the time of each event from the start time of the process to identify the elapsed time since startup.</span></span> <span data-ttu-id="4cecf-176">如果您使用 Ctrl+按一下的方式來選取兩個時間戳記，您會看到其之間的差異顯示在頁面底部的狀態列中。</span><span class="sxs-lookup"><span data-stu-id="4cecf-176">If you use Ctrl+Click to select two timestamps, you'll see the difference between them displayed in the status bar at the bottom of the page.</span></span> <span data-ttu-id="4cecf-177">這樣可以讓您很容易在顯示器中查看任何兩個事件之間的經歷時間 (包括處理開始)。</span><span class="sxs-lookup"><span data-stu-id="4cecf-177">This makes it easy to see the elapsed time between any two events in the display (including process start).</span></span> <span data-ttu-id="4cecf-178">您可以開啟檢視的快顯功能表，並從一些有用的選項中選取，像是匯出至 CSV 檔案，或是開啟 Microsoft Excel 來儲存或處理資料。</span><span class="sxs-lookup"><span data-stu-id="4cecf-178">You can open the shortcut menu for the view and select from a number of useful options, like exporting to CSV files or opening Microsoft Excel to save or process the data.</span></span>  
  
 <span data-ttu-id="4cecf-179">針對您原始的應用程式以及使用 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 工具鏈來建置的版本重複此程序，就可以比較出效能的差異。</span><span class="sxs-lookup"><span data-stu-id="4cecf-179">By repeating the procedure for both your original app and the version you built by using the [!INCLUDE[net_native](../../../includes/net-native-md.md)] tool chain, you can compare the difference in performance.</span></span>   [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="4cecf-180"> 應用程式的啟動速度通常會比非 [!INCLUDE[net_native](../../../includes/net-native-md.md)] 應用程式快。</span><span class="sxs-lookup"><span data-stu-id="4cecf-180"> apps generally start faster than non-[!INCLUDE[net_native](../../../includes/net-native-md.md)] apps.</span></span> <span data-ttu-id="4cecf-181">如果您有挖掘更深入的資料，PerfView 也可以識別出程式碼中最耗時間的部分。</span><span class="sxs-lookup"><span data-stu-id="4cecf-181">If you’re interested in digging deeper, PerfView can also identify the parts of your code that are taking the most time.</span></span> <span data-ttu-id="4cecf-182">如需詳細資訊，請觀看 [PerfView 教學課程](http://channel9.msdn.com/Series/PerfView-Tutorial)或閱讀 [Vance Morrison 的部落格文章](http://blogs.msdn.com/b/vancem/archive/2011/12/28/publication-of-the-perfview-performance-analysis-tool.aspx)。</span><span class="sxs-lookup"><span data-stu-id="4cecf-182">For more information, watch the [PerfView tutorials](http://channel9.msdn.com/Series/PerfView-Tutorial) or read [Vance Morrison’s blog entry](http://blogs.msdn.com/b/vancem/archive/2011/12/28/publication-of-the-perfview-performance-analysis-tool.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4cecf-183">請參閱</span><span class="sxs-lookup"><span data-stu-id="4cecf-183">See Also</span></span>  
 <xref:System.Diagnostics.Tracing.EventSource>
