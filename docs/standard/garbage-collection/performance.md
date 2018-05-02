---
title: 記憶體回收和效能
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- garbage collection, troubleshooting
- garbage collection, performance
ms.assetid: c203467b-e95c-4ccf-b30b-953eb3463134
caps.latest.revision: 35
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: daf70cdb7344f895059d0bc8b986edddbf7d53bc
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="garbage-collection-and-performance"></a>記憶體回收和效能
<a name="top"></a> 本主題描述記憶體回收和記憶體使用量的相關問題。 它解決關於 Managed 堆積的問題，並說明如何將記憶體回收對應用程式的影響降至最低。 每個問題已連結至程序，可讓您用來調查問題。  
  
 此主題包括下列章節：  
  
-   [效能分析工具](#performance_analysis_tools)  
  
-   [針對效能問題進行疑難排解](#troubleshooting_performance_issues)  
  
-   [疑難排解方針](#troubleshooting_guidelines)  
  
-   [效能檢查程序](#performance_check_procedures)  
  
<a name="performance_analysis_tools"></a>   
## <a name="performance-analysis-tools"></a>效能分析工具  
 下列各節說明可用來調查記憶體使用量和記憶體回收問題的工具。 本主題稍後提供的[程序](#performance_check_procedures)會參考這些工具。  
  
<a name="perf_counters"></a>   
### <a name="memory-performance-counters"></a>記憶體效能計數器  
 您可以使用效能計數器來收集效能資料。 如需相關指示，請參閱[執行階段分析](../../../docs/framework/debug-trace-profile/runtime-profiling.md)。 效能計數器的 .NET CLR 記憶體類別，如 [.NET Framework 中的效能計數器](../../../docs/framework/debug-trace-profile/performance-counters.md)中所述，會提供記憶體回收行程的相關資訊。  
  
<a name="sos"></a>   
### <a name="debugging-with-sos"></a>以 SOS 偵錯  
 您可以使用 [Windows 偵錯工具 (WinDbg)](/windows-hardware/drivers/debugger/index) 來檢查 Managed 堆積上的物件。
 
 若要安裝 WinDbg，請從[下載 Debugging Tools for Windows](/windows-hardware/drivers/debugger/debugger-download-tools) 頁面安裝 Debugging Tools for Windows。
  
<a name="etw"></a>   
### <a name="garbage-collection-etw-events"></a>記憶體回收 ETW 事件  
 Windows 事件追蹤 (ETW) 是補充 .NET Framework 所提供之程式碼剖析和偵錯支援的追蹤系統。 從 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 開始，[記憶體回收 ETW 事件](../../../docs/framework/performance/garbage-collection-etw-events.md)會擷取有用的資訊，以便從統計的觀點來分析 Managed 堆積。 例如，引發 `GCStart_V1` 事件時，會發生記憶體回收，這會提供下列資訊：  
  
-   所收集物件的層代。  
  
-   觸發記憶體回收的原因。  
  
-   記憶體回收 (並行或不同時) 的類型。  
  
 ETW 事件記錄很有效率，且不會遮蓋與記憶體回收相關聯的任何效能問題。 處理程序可以提供自己的事件來搭配 ETW 事件。 記錄時，應用程式的事件和記憶體回收事件都可以相互關聯，以判斷堆積問題發生的方式和時間。 例如，伺服器應用程式可以在用戶端要求開始和結束時提供事件。  
  
<a name="profiling_api"></a>   
### <a name="the-profiling-api"></a>程式碼剖析 API  
 Common Language Runtime (CLR) 程式碼剖析介面提供在記憶體回收期間受影響之物件的詳細相關資訊。 當記憶體回收開始和結束時，會通知程式碼剖析工具。 它可以提供 Managed 堆積上之物件的相關報告，包括每個層代中的物件識別碼。 如需詳細資訊，請參閱[分析概觀](../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)。  
  
 程式碼剖析工具可以提供完整的資訊。 不過，複雜的程式碼剖析工具可能會修改應用程式的行為。  
  
### <a name="application-domain-resource-monitoring"></a>應用程式定義域資源監視  
 從 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 開始，應用程式定義域資源監視 (ARM) 可讓主機監視應用程式定義域的 CPU 和記憶體使用量。 如需詳細資訊，請參閱[應用程式定義域資源監視](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)。  
  
 [回到頁首](#top)  
  
<a name="troubleshooting_performance_issues"></a>   
## <a name="troubleshooting-performance-issues"></a>效能問題疑難排解  
 第一個步驟是[判斷問題是否真的是記憶體回收](#IsGC)。 如果您判斷是，則請從下列清單選取以疑難排解問題。  
  
-   [擲回記憶體不足例外狀況](#Issue_OOM)  
  
-   [處理序使用太多記憶體](#Issue_TooMuchMemory)  
  
-   [記憶體回收行程回收物件速度不夠快](#Issue_NotFastEnough)  
  
-   [Managed 堆積太過分散](#Issue_Fragmentation)  
  
-   [記憶體回收暫停太長](#Issue_LongPauses)  
  
-   [層代 0 太大](#Issue_Gen0)  
  
-   [在記憶體回收期間的 CPU 使用量太高](#Issue_HighCPU)  
  
<a name="Issue_OOM"></a>   
### <a name="issue-an-out-of-memory-exception-is-thrown"></a>問題：擲回記憶體不足例外狀況  
 有兩種合理狀況會擲回 Managed <xref:System.OutOfMemoryException>：  
  
-   虛擬記憶體不足。  
  
     記憶體回收行程會以預先決定大小的區段，從系統配置記憶體。 如果配置需要額外的區段，但處理序的虛擬記憶體空間中沒有剩下連續的可用區塊，則 Managed 堆積配置將會失敗。  
  
-   沒有足夠的實體記憶體可配置。  
  
|效能檢查|  
|------------------------|  
|[判斷記憶體不足例外狀況是否為 Managed。](#OOMIsManaged)<br /><br /> [判斷可以保留多少虛擬記憶體。](#GetVM)<br /><br /> [判斷是否有足夠的實體記憶體。](#Physical)|  
  
 如果您判斷例外狀況不合法，請連絡 Microsoft 客戶服務及支援，並提供下列資訊：  
  
-   具有受管理的記憶體不足例外狀況的堆疊。  
  
-   完整記憶體傾印。  
  
-   證明它是不合法的記憶體不足例外狀況的資料，包括顯示虛擬或實體記憶體不是問題的資料。  
  
<a name="Issue_TooMuchMemory"></a>   
### <a name="issue-the-process-uses-too-much-memory"></a>問題：處理序使用太多記憶體  
 常見的假設是 Windows 工作管理員 [效能] 索引標籤上的記憶體使用量顯示可以指出使用太多記憶體的時刻。 不過，該顯示與工作集有關；它不提供虛擬記憶體使用量的相關資訊。  
  
 如果您判斷問題是 Managed 堆積所導致，您必須在一段時間內測量 Managed 堆積，以判斷任何模式。  
  
 如果您判斷問題不是 Managed 堆積所導致，則您必須使用原生偵錯。  
  
|效能檢查|  
|------------------------|  
|[判斷可以保留多少虛擬記憶體。](#GetVM)<br /><br /> [判斷 Managed 堆積正在認可的記憶體數量。](#ManagedHeapCommit)<br /><br /> [判斷 Managed 堆積保留的記憶體數量。](#ManagedHeapReserve)<br /><br /> [判斷層代 2 的大型物件。](#ExamineGen2)<br /><br /> [判斷物件的參考。](#ObjRef)|  
  
<a name="Issue_NotFastEnough"></a>   
### <a name="issue-the-garbage-collector-does-not-reclaim-objects-fast-enough"></a>問題：記憶體回收行程回收物件速度不夠快  
 當物件似乎未如預期般被回收以進行記憶體回收時，您必須判斷是否有對這些物件的任何強式參考。  
  
 如果包含無作用物件的層代已經沒有記憶體回收 (表示尚未執行無作用物件的完成項)，您也可能會遇到這個問題。 比方說，這可能發生在您執行單一執行緒 Apartment (STA) 應用程式和服務完成項佇列的執行緒無法呼叫到它時。  
  
|效能檢查|  
|------------------------|  
|[檢查物件的參考。](#ObjRef)<br /><br /> [判斷是否已執行完成項。](#Induce)<br /><br /> [判斷是否有等候完成的物件。](#Finalize)|  
  
<a name="Issue_Fragmentation"></a>   
### <a name="issue-the-managed-heap-is-too-fragmented"></a>問題：Managed 堆積太過分散  
 分散層級的計算方式是可用空間佔層代配置記憶體總數的比例。 針對層代 2，可接受的分散層級是不超過 20%。 層代 2 可能會非常大，因此分散比例比絕對值更重要。  
  
 層代 0 中有很多可用空間不成問題，因為這是配置新物件配置所在的層代。  
  
 分散一律發生在大型物件堆積中，因為它不會壓縮。 相鄰的可用物件自然而然會聚攏成為單一空間，以滿足大型物件配置要求。  
  
 分散可能會在層代 1 和層代 2 成為問題。 如果這些層代在記憶體回收之後有大量的可用空間，應用程式的物件使用方式可能需要修改，而且您應該考慮重新評估長期物件的存留期。  
  
 固定過多物件可能會增加分散。 如果分散很高，可能是已固定太多物件。  
  
 如果虛擬記憶體的分散導致記憶體回收行程無法加入區段，原因可能是下列其中一項：  
  
-   經常載入及卸載許多小型組件。  
  
-   與 Unmanaged 程式碼交互作用時，保留太多 COM 物件的參考。  
  
-   建立大型的暫時性物件，這會造成大型物件堆積頻繁地配置和釋放堆積區段。  
  
     裝載 CLR 時，應用程式可以要求記憶體回收行程保留其區段。 這會減少區段配置的頻率。 這可以藉由使用 [STARTUP_FLAGS 列舉](../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)中的 STARTUP_HOARD_GC_VM 旗標來達成。  
  
|效能檢查|  
|------------------------|  
|[判斷 Managed 堆積中的可用空間數量。](#Fragmented)<br /><br /> [判斷被固定的物件數目。](#Pinned)|  
  
 如果您認為是不合法的分散原因，請連絡 Microsoft 客戶服務及支援中心。  
  
<a name="Issue_LongPauses"></a>   
### <a name="issue-garbage-collection-pauses-are-too-long"></a>問題：記憶體回收暫停太長  
 記憶體回收以軟性即時方式運作，所以應用程式必須能夠容忍某些暫停。 軟性即時的準則是 95% 的作業必須準時完成。  
  
 在並行記憶體回收中，Managed 執行緒可以在回收期間執行，這表示很少暫停。  
  
 暫時記憶體回收 (層代 0 和 1) 只會持續幾毫秒，因此減少暫停通常並不可行。 不過，您可以變更應用程式的配置要求模式，來減少在層代 2 回收中的暫停。  
  
 另一個、更正確的方法是使用[記憶體回收 ETW 事件](../../../docs/framework/performance/garbage-collection-etw-events.md)。 您可以藉由加入一系列事件的時間戳記差異來尋找回收的時機。 整個回收順序包含擱置執行引擎、記憶體回收本身，以及繼續執行引擎。  
  
 您可以使用[記憶體回收通知](../../../docs/standard/garbage-collection/notifications.md)判斷伺服器是否即將有層代 2 回收，及將要求重設路徑到另一部伺服器是否可以緩解任何暫停問題。  
  
|效能檢查|  
|------------------------|  
|[判斷記憶體回收的時間長度。](#TimeInGC)<br /><br /> [判斷造成記憶體回收的原因。](#Triggered)|  
  
<a name="Issue_Gen0"></a>   
### <a name="issue-generation-0-is-too-big"></a>問題：層代 0 太大  
 層代 0 可能在 64 位元系統上，有較大量的物件，特別是當您使用伺服器記憶體回收，而不是工作站記憶體回收時。 這是因為在這些環境中觸發層代 0 記憶體回收的臨界值較高，層代 0 回收可能會變大許多。 當在觸發記憶體回收之前應用程式配置更多記憶體時，可提升效能。  
  
<a name="Issue_HighCPU"></a>   
### <a name="issue-cpu-usage-during-a-garbage-collection-is-too-high"></a>問題：在記憶體回收期間的 CPU 使用量太高  
 在記憶體回收期間的 CPU 使用量會很高。 如果大量的處理序時間花在記憶體回收，則表示回收次數過於頻繁或是回收的持續時間太長。 Managed 堆積上物件配置率增加，會導致更頻繁地進行記憶體回收。 減少配置率可降低記憶體回收的頻率。  
  
 您可以使用 `Allocated Bytes/second` 效能計數器，以監視配置率。 如需詳細資訊，請參閱 [.NET Framework 中的效能計數器](../../../docs/framework/debug-trace-profile/performance-counters.md)。  
  
 回收的持續時間主要是配置後存留之物件數目的因素。 如果要收集許多物件，記憶體回收行程必須通過大量的記憶體。 壓縮存留者的工作相當耗時。 若要判斷在回收期間處理的物件數目，請在指定層代的記憶體回收結尾處，在偵錯工具設定中斷點。  
  
|效能檢查|  
|------------------------|  
|[判斷高 CPU 使用量是否由於記憶體回收所造成。](#HighCPU)<br /><br /> [在記憶體回收結尾處設定中斷點。](#GenBreak)|  
  
 [回到頁首](#top)  
  
<a name="troubleshooting_guidelines"></a>   
## <a name="troubleshooting-guidelines"></a>疑難排解方針  
 本節描述當您開始調查時，應該考慮的方針。  
  
### <a name="workstation-or-server-garbage-collection"></a>工作站和伺服器記憶體回收  
 判斷您是否使用正確的記憶體回收類型。 如果您的應用程式使用多個執行緒和物件執行個體，請使用伺服器記憶體回收，而不要使用工作站記憶體回收。 伺服器記憶體回收會在多個執行緒上運作，而工作站記憶體回收則需要應用程式的多個執行個體執行自己的記憶體回收執行緒，且會競爭 CPU 時間。  
  
 具有低負載，且不常在背景中執行工作的應用程式，例如服務，可以使用工作站記憶體回收，並停用並行記憶體回收。  
  
### <a name="when-to-measure-the-managed-heap-size"></a>測量 Managed 堆積大小的時機  
 除非您使用程式碼剖析工具，否則您必須建立一致的測量模式，才能有效地診斷效能問題。 建立排程時請考慮下列各點：  
  
-   如果您在層代 2 記憶體回收之後測量，整個 Managed 堆積都將沒有廢棄項目 (無作用物件)。  
  
-   如果層代 0 記憶體回收之後立即測量，此時尚不會回收層代 1 和 2 中的物件。  
  
-   如果在記憶體回收之前立即測量，您會測量到記憶體回收開始之前最多的可能配置。  
  
-   在記憶體回收期間測量會有問題，因為記憶體回收行程資料結構不在周遊的有效狀態，而且可能無法提供完整的結果。 這是依設計的結果。  
  
-   當您使用工作站記憶體回收與並行記憶體回收時，回收的物件不會壓縮，因此堆積大小可能相同或更大 (分散可能讓它看起來似乎較大)。  
  
-   實體記憶體負載過高時，就會延遲層代 2 的並行記憶體回收。  
  
 下列程序描述如何設定中斷點，讓您可以測量 Managed 堆積。  
  
<a name="GenBreak"></a>   
##### <a name="to-set-a-breakpoint-at-the-end-of-garbage-collection"></a>在記憶體回收結尾處設定中斷點  
  
-   在載入 SOS 偵錯工具擴充功能的 WinDbg 中，輸入下列命令：  
  
     **bp mscorwks!WKS::GCHeap::RestartEE "j (dwo(mscorwks!WKS::GCHeap::GcCondemnedGeneration)==2) 'kb';'g'"**  
  
     其中 **GcCondemnedGeneration** 設為所需的層代。 此命令需要私用符號。  
  
     如果回收層代 2 物件，以進行記憶體回收之後，執行了 **RestartEE**，則此命令會強制中斷。  
  
     在伺服器記憶體回收中，只有一個執行緒呼叫 **RestartEE**，因此中斷點只會在層代 2 記憶體回收期間發生一次。  
  
 [回到頁首](#top)  
  
<a name="performance_check_procedures"></a>   
## <a name="performance-check-procedures"></a>效能檢查程序  
 本節描述下列程序，以找出效能問題的原因：  
  
-   [判斷問題是否由於記憶體回收所造成。](#IsGC)  
  
-   [判斷記憶體不足例外狀況是否為 Managed。](#OOMIsManaged)  
  
-   [判斷可以保留多少虛擬記憶體。](#GetVM)  
  
-   [判斷是否有足夠的實體記憶體。](#Physical)  
  
-   [判斷 Managed 堆積正在認可的記憶體數量。](#ManagedHeapCommit)  
  
-   [判斷 Managed 堆積保留的記憶體數量。](#ManagedHeapReserve)  
  
-   [判斷層代 2 的大型物件。](#ExamineGen2)  
  
-   [判斷物件的參考。](#ObjRef)  
  
-   [判斷是否已執行完成項。](#Induce)  
  
-   [判斷是否有等候完成的物件。](#Finalize)  
  
-   [判斷 Managed 堆積中的可用空間數量。](#Fragmented)  
  
-   [判斷被固定的物件數目。](#Pinned)  
  
-   [判斷記憶體回收的時間長度。](#TimeInGC)  
  
-   [判斷觸發記憶體回收的原因。](#Triggered)  
  
-   [判斷高 CPU 使用量是否由於記憶體回收所造成。](#HighCPU)  
  
<a name="IsGC"></a>   
##### <a name="to-determine-whether-the-problem-is-caused-by-garbage-collection"></a>判斷問題是否由於記憶體回收所造成  
  
-   檢查下列兩個記憶體效能計數器：  
  
    -   **在 GC 的時間 %**。 顯示自上次記憶體回收循環後所花費在執行記憶體回收的已耗用時間百分比。 使用此計數器來判斷是否記憶體回收行程花費太多時間才讓 Managed 堆積的空間可供使用。 如果花費在記憶體回收的時間很短，可能表示 Managed 堆積以外的資源問題。 與並行或背景記憶體回收相關時，這個計數器可能不正確。  
  
    -   **已認可的位元組總數**。 顯示記憶體回收行程目前已認可的虛擬記憶體數目。 使用此計數器來判斷記憶體回收行程所耗用的記憶體是否佔應用程式所使用記憶體的過多數量。  
  
     大部分的記憶體效能計數器會在每次記憶體回收結束時更新。 因此，它們可能無法反映您要取得相關資訊的目前狀況。  
  
<a name="OOMIsManaged"></a>   
##### <a name="to-determine-whether-the-out-of-memory-exception-is-managed"></a>判斷記憶體不足例外狀況是否為 Managed  
  
1.  在已載入 SOS 偵錯工具擴充功能的 WinDbg 或 Visual Studio 偵錯工具中，輸入列印例外狀況 (**pe**) 命令：  
  
     **!pe**  
  
     如果例外狀況為 Managed，<xref:System.OutOfMemoryException> 會顯示為例外狀況類型，如下列範例所示。  
  
    ```  
    Exception object: 39594518  
    Exception type: System.OutOfMemoryException  
    Message: <none>  
    InnerException: <none>  
    StackTrace (generated):  
    ```  
  
2.  如果輸出未指定例外狀況，您必須判斷記憶體不足例外狀況是來自哪一個執行緒。 在偵錯工具中輸入下列命令，顯示所有執行緒與其呼叫堆疊：  
  
     **~\*kb**  
  
     堆疊具有例外狀況呼叫的執行緒會以 `RaiseTheException` 引數表示。 這是 Managed 例外狀況物件。  
  
    ```  
    28adfb44 7923918f 5b61f2b4 00000000 5b61f2b4 mscorwks!RaiseTheException+0xa0   
    ```  
  
3.  您可以使用下列命令來傾印巢狀例外狀況。  
  
     **!pe -nested**  
  
     如果找不到任何例外狀況，表示記憶體不足例外狀況是源自於 Unmanaged 程式碼。  
  
<a name="GetVM"></a>   
##### <a name="to-determine-how-much-virtual-memory-can-be-reserved"></a>判斷可以保留多少虛擬記憶體  
  
-   在載入 SOS 偵錯工具擴充功能的 WinDbg 中，輸入下列命令，取得最大的可用區域：  
  
     **!address -summary**  
  
     最大可用區域會顯示在下列輸出中。  
  
    ```  
    Largest free region: Base 54000000 - Size 0003A980  
    ```  
  
     在此範例中，最大可用區域的大小大約為 24000 KB (十六進位為 3A980)。 此區域是遠小於記憶體回收行程針對區段所需。  
  
     -或-  
  
-   使用 **vmstat** 命令︰  
  
     **!vmstat**  
  
     最大可用區域是 MAXIMUM 資料行中的最大值，如下列輸出所示。  
  
    ```  
    TYPE        MINIMUM   MAXIMUM     AVERAGE   BLK COUNT   TOTAL  
    ~~~~        ~~~~~~~   ~~~~~~~     ~~~~~~~   ~~~~~~~~~~  ~~~~  
    Free:  
    Small       8K        64K         46K       36          1,671K  
    Medium      80K       864K        349K      3           1,047K  
    Large       1,384K    1,278,848K  151,834K  12          1,822,015K  
    Summary     8K        1,278,848K  35,779K   51          1,824,735K  
    ```  
  
<a name="Physical"></a>   
##### <a name="to-determine-whether-there-is-enough-physical-memory"></a>判斷是否有足夠的實體記憶體  
  
1.  啟動 Windows 工作管理員。  
  
2.  在 [效能] 索引標籤上，查看已認可的值。 (在 Windows 7 中，查看 [系統群組] 中的 [認可 (KB)]。)  
  
     如果 [總計] 很接近 [限制]，則您的實體記憶體不足。  
  
<a name="ManagedHeapCommit"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-is-committing"></a>判斷 Managed 堆積正在認可的記憶體數量  
  
-   使用 `# Total committed bytes` 記憶體效能計數器，以取得 Managed 堆積正在認可的位元組數目。 記憶體回收行程會視需要認可區段上的區塊 (chunk)，而不是同時全部認可。  
  
    > [!NOTE]
    >  請勿使用 `# Bytes in all Heaps` 效能計數器，因為它不代表 Managed 堆積的實際記憶體使用量。 層代的大小包含在此值中，且為其實際閾值大小，也就是層代裝滿物件時引發記憶體回收的大小。 因此，這個值通常是零。  
  
<a name="ManagedHeapReserve"></a>   
##### <a name="to-determine-how-much-memory-the-managed-heap-reserves"></a>判斷 Managed 堆積保留的記憶體數量  
  
-   使用 `# Total reserved bytes` 記憶體效能計數器。  
  
     記憶體回收行程會以區段來保留記憶體，您可以使用 **eeheap** 命令來判斷區段開始的位置。  
  
    > [!IMPORTANT]
    >  雖然您可以判斷記憶體回收行程配置給每個區段的記憶體數量，但區段大小會依實作而定，而且隨時可能變更，包括定期更新。 您的應用程式永遠都不應該對相關或根據特定區段的大小做出假設，也不應嘗試設定區段配置的可用記憶體數量。  
  
-   在已載入 SOS 偵錯工具擴充功能的 WinDbg 或 Visual Studio 偵錯工具中，輸入下列命令：  
  
     **!eeheap -gc**  
  
     結果如下所示。  
  
    ```  
    Number of GC Heaps: 2  
    ------------------------------  
    Heap 0 (002db550)  
    generation 0 starts at 0x02abe29c  
    generation 1 starts at 0x02abdd08  
    generation 2 starts at 0x02ab0038  
    ephemeral segment allocation context: none  
     segment    begin allocated     size  
    02ab0000 02ab0038  02aceff4 0x0001efbc(126908)  
    Large object heap starts at 0x0aab0038  
     segment    begin allocated     size  
    0aab0000 0aab0038  0aab2278 0x00002240(8768)  
    Heap Size   0x211fc(135676)  
    ------------------------------  
    Heap 1 (002dc958)  
    generation 0 starts at 0x06ab1bd8  
    generation 1 starts at 0x06ab1bcc  
    generation 2 starts at 0x06ab0038  
    ephemeral segment allocation context: none  
     segment    begin allocated     size  
    06ab0000 06ab0038  06ab3be4 0x00003bac(15276)  
    Large object heap starts at 0x0cab0038  
     segment    begin allocated     size  
    0cab0000 0cab0038  0cab0048 0x00000010(16)  
    Heap Size    0x3bbc(15292)  
    ------------------------------  
    GC Heap Size   0x24db8(150968)  
    ```  
  
     「區段」所指定的位址是區段的起始位址。  
  
<a name="ExamineGen2"></a>   
##### <a name="to-determine-large-objects-in-generation-2"></a>判斷層代 2 的大型物件  
  
-   在已載入 SOS 偵錯工具擴充功能的 WinDbg 或 Visual Studio 偵錯工具中，輸入下列命令：  
  
     **!dumpheap –stat**  
  
     如果 Managed 堆積很大，**dumpheap** 可能需要一些時間才能完成。  
  
     您可以從輸出的最後幾行開始分析，因為它們列出使用最多空間的物件。 例如:   
  
    ```  
    2c6108d4   173712     14591808 DevExpress.XtraGrid.Views.Grid.ViewInfo.GridCellInfo  
    00155f80      533     15216804      Free  
    7a747c78   791070     15821400 System.Collections.Specialized.ListDictionary+DictionaryNode  
    7a747bac   700930     19626040 System.Collections.Specialized.ListDictionary  
    2c64e36c    78644     20762016 DevExpress.XtraEditors.ViewInfo.TextEditViewInfo  
    79124228   121143     29064120 System.Object[]  
    035f0ee4    81626     35588936 Toolkit.TlkOrder  
    00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]  
    791242ec    40182     90664128 System.Collections.Hashtable+bucket[]  
    790fa3e0  3154024    137881448 System.String  
    Total 8454945 objects  
    ```  
  
     所列的最後一個物件是一個字串，而且會佔用最多的空間。 您可以檢查應用程式，了解如何最佳化您的字串物件。 若要查看介於 150 到 200 個位元組的字串，請輸入下列命令：  
  
     **!dumpheap -type System.String -min 150 -max 200**  
  
     結果的範例如下。  
  
    ```  
    Address  MT           Size  Gen  
    1875d2c0 790fa3e0      152    2 System.String HighlightNullStyle_Blotter_PendingOrder-11_Blotter_PendingOrder-11  
    …  
    ```  
  
     針對識別碼使用整數而不使用字串，可能會更有效率。 如果相同的字串重複數千次，請考慮字串拘留 (string interning)。 如需有關字串拘留的詳細資訊，請參閱 <xref:System.String.Intern%2A?displayProperty=nameWithType> 方法的參考主題。  
  
<a name="ObjRef"></a>   
##### <a name="to-determine-references-to-objects"></a>判斷物件的參考  
  
-   在載入 SOS 偵錯工具擴充功能的 WinDbg 中，輸入下列命令，列出物件的參考：  
  
     **!gcroot**  
  
     `-or-`  
  
-   若要判斷特定物件的參考，請包含位址：  
  
     **!gcroot 1c37b2ac**  
  
     在堆疊上找到的根可能是誤判。 如需詳細資訊，請參閱 `!help gcroot` 命令。  
  
    ```  
    ebx:Root:19011c5c(System.Windows.Forms.Application+ThreadContext)->  
    19010b78(DemoApp.FormDemoApp)->  
    19011158(System.Windows.Forms.PropertyStore)->  
    … [omitted]  
    1c3745ec(System.Data.DataTable)->  
    1c3747a8(System.Data.DataColumnCollection)->  
    1c3747f8(System.Collections.Hashtable)->  
    1c376590(System.Collections.Hashtable+bucket[])->  
    1c376c98(System.Data.DataColumn)->  
    1c37b270(System.Data.Common.DoubleStorage)->  
    1c37b2ac(System.Double[])  
    Scan Thread 0 OSTHread 99c  
    Scan Thread 6 OSTHread 484  
    ```  
  
     **gcroot** 命令可能會執行很長的時間才能完成。 不由記憶體回收所回收的任何物件便是實際物件。 這表示某些根是直接或間接緊守住物件，所以 **gcroot** 應該傳回物件的路徑資訊。 您應該檢查傳回的圖形，並查看為什麼仍然參考這些物件。  
  
<a name="Induce"></a>   
##### <a name="to-determine-whether-a-finalizer-has-been-run"></a>判斷是否已執行完成項  
  
-   執行測試程式，其中包含下列程式碼：  
  
    ```  
    GC.Collect();  
    GC.WaitForPendingFinalizers();  
    GC.Collect();  
    ```  
  
     如果測試可以解決此問題，這表示記憶體回收行程未回收物件，因為這些物件的完成項已暫止。 <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> 方法讓完成項能完成其工作，並修正問題。  
  
<a name="Finalize"></a>   
##### <a name="to-determine-whether-there-are-objects-waiting-to-be-finalized"></a>判斷是否有等候完成的物件  
  
1.  在已載入 SOS 偵錯工具擴充功能的 WinDbg 或 Visual Studio 偵錯工具中，輸入下列命令：  
  
     **!finalizequeue**  
  
     查看準備好進行最終處理的物件數目。 如果數量很高，您必須檢查為什麼這些完成項完全沒有進度，或進行的速度不夠快。  
  
2.  若要取得執行緒的輸出，請輸入下列命令：  
  
     **threads -special**  
  
     這個命令會提供如下所示的輸出。  
  
    ```  
       OSID     Special thread type  
    2    cd0    DbgHelper   
    3    c18    Finalizer   
    4    df0    GC SuspendEE   
    ```  
  
     完成項執行緒會指出目前正在執行哪一個完成項 (如果有的話)。 當完成項執行緒未在執行任何完成項時，它正在等候事件來告訴它要執行其工作。 大多數情況下會看見完成項執行緒處於此狀態，是因為它以 THREAD_HIGHEST_PRIORITY 執行，並且應該非常快速地完成執行完成項 (如果有的話)。  
  
<a name="Fragmented"></a>   
##### <a name="to-determine-the-amount-of-free-space-in-the-managed-heap"></a>判斷 Managed 堆積中的可用空間數量  
  
-   在已載入 SOS 偵錯工具擴充功能的 WinDbg 或 Visual Studio 偵錯工具中，輸入下列命令：  
  
     **!dumpheap -type Free -stat**  
  
     此命令會顯示 Managed 堆積中所有可用物件的大小總計，如下列範例所示。  
  
    ```  
    total 230 objects  
    Statistics:  
          MT    Count    TotalSize Class Name  
    00152b18      230     40958584      Free  
    Total 230 objects  
    ```  
  
-   若要判斷層代 0 中的可用空間，請輸入下列命令以取得依層代的記憶體耗用量資訊：  
  
     **!eeheap -gc**  
  
     這個命令會顯示與下列類似的輸出。 最後一行顯示暫時區段。  
  
    ```  
    Heap 0 (0015ad08)  
    generation 0 starts at 0x49521f8c  
    generation 1 starts at 0x494d7f64  
    generation 2 starts at 0x007f0038  
    ephemeral segment allocation context: none  
    segment  begin     allocated  size  
    00178250 7a80d84c  7a82f1cc   0x00021980(137600)  
    00161918 78c50e40  78c7056c   0x0001f72c(128812)  
    007f0000 007f0038  047eed28   0x03ffecf0(67103984)  
    3a120000 3a120038  3a3e84f8   0x002c84c0(2917568)  
    46120000 46120038  49e05d04   0x03ce5ccc(63855820)  
    ```  
  
-   計算層代 0 所使用的空間：  
  
     **?49e05d04-0x49521f8c**  
  
     結果如下所示。 層代 0 大約 9 MB。  
  
    ```  
    Evaluate expression: 9321848 = 008e3d78  
    ```  
  
-   下列命令會傾印在層代 0 範圍內的可用空間：  
  
     **!dumpheap -type Free -stat 0x49521f8c 49e05d04**  
  
     結果如下所示。  
  
    ```  
    ------------------------------  
    Heap 0  
    total 409 objects  
    ------------------------------  
    Heap 1  
    total 0 objects  
    ------------------------------  
    Heap 2  
    total 0 objects  
    ------------------------------  
    Heap 3  
    total 0 objects  
    ------------------------------  
    total 409 objects  
    Statistics:  
          MT    Count TotalSize Class Name  
    0015a498      409   7296540      Free  
    Total 409 objects  
    ```  
  
     此輸出顯示堆積的層代 0 部分使用 9 MB 的物件空間，並有 7 MB 可用。 這項分析顯示層代 0 對分散的影響程度。 在計算長期物件的分散原因時，此堆積使用量應該從總數量扣除。  
  
<a name="Pinned"></a>   
##### <a name="to-determine-the-number-of-pinned-objects"></a>判斷被固定的物件數目  
  
-   在已載入 SOS 偵錯工具擴充功能的 WinDbg 或 Visual Studio 偵錯工具中，輸入下列命令：  
  
     **!gchandles**  
  
     顯示的統計資料包括固定控制代碼數目，如下列範例所示。  
  
    ```  
    GC Handle Statistics:  
    Strong Handles:      29  
    Pinned Handles:      10  
    ```  
  
<a name="TimeInGC"></a>   
##### <a name="to-determine-the-length-of-time-in-a-garbage-collection"></a>判斷記憶體回收的時間長度  
  
-   檢查 `% Time in GC` 記憶體效能計數器。  
  
     值的計算是使用取樣間隔時間。 由於計數器會在每次記憶體回收結束時更新，如果在間隔期間未發生任何回收，則目前的取樣值將會與前一個取樣值相同。  
  
     回收時間是將取樣間隔時間乘上百分比值而取得。  
  
     下列資料顯示四個兩秒的取樣間隔，也就是 8 秒的研究。 `Gen0`、`Gen1` 和 `Gen2` 資料行會顯示在該層代的間隔期間發生的記憶體回收數目。  
  
    ```  
    Interval    Gen0    Gen1    Gen2    % Time in GC  
           1       9       3       1              10  
           2      10       3       1               1  
           3      11       3       1               3  
           4      11       3       1               3  
    ```  
  
     這項資訊不會顯示記憶體回收發生的時間，但您可以判斷在時間間隔中發生的記憶體回收數目。 假設在最壞的情況下，第十次層代 0 記憶體回收在第二個間隔開始時完成，而第十一次層代 0 記憶體回收在第五個間隔結束時完成。 第十次記憶體回收與第十一次記憶體回收結束之間的時間約 2 秒，而且效能計數器顯示 3%，因此第十一次層代 0 記憶體回收的持續時間為 (2 秒 * 3% = 60 毫秒)。  
  
     在此範例中，有 5 個週期。  
  
    ```  
    Interval    Gen0    Gen1    Gen2     % Time in GC  
           1       9       3       1                3  
           2      10       3       1                1  
           3      11       4       2                1  
           4      11       4       2                1  
           5      11       4       2               20  
    ```  
  
     第二次層代 2 記憶體回收在第三個間隔期間開始，並在第五個間隔完成。 假設在最壞的情況下，最後一次記憶體回收是針對層代 0 回收，其在第二個間隔開始時完成，且層代 2 記憶體回收在第五個間隔結束時完成。 因此，層代 0 記憶體回收結束與層代 2 記憶體回收結束之間的時間是 4 秒。 由於 `% Time in GC` 計數器為 20%，因此層代 2 記憶體回收可能花費的最長時間量是 (4 秒 * 20% = 800 毫秒)。  
  
-   或者，您可以使用[記憶體回收 ETW 事件](../../../docs/framework/performance/garbage-collection-etw-events.md)來判斷記憶體回收的長度，並分析資訊來判斷記憶體回收的持續時間。  
  
     例如，下列資料顯示在非並行記憶體回收期間發生的事件序列。  
  
    ```  
    Timestamp    Event name  
    513052        GCSuspendEEBegin_V1  
    513078        GCSuspendEEEnd  
    513090        GCStart_V1  
    517890        GCEnd_V1  
    517894        GCHeapStats  
    517897        GCRestartEEBegin  
    517918        GCRestartEEEnd  
    ```  
  
     暫止 Managed 執行緒花了 26 微秒 (`GCSuspendEEEnd` – `GCSuspendEEBegin_V1`)。  
  
     實際的記憶體回收花了 4.8 毫秒 (`GCEnd_V1` – `GCStart_V1`)。  
  
     繼續 Managed 執行緒花了 21 微秒 (`GCRestartEEEnd` – `GCRestartEEBegin`)。  
  
     下列輸出提供背景記憶體回收的範例，並包含處理序、執行緒和事件欄位。 (並非所有資料皆會顯示)。  
  
    ```  
    timestamp(us)    event name            process    thread    event field  
    42504385        GCSuspendEEBegin_V1    Test.exe    4372             1  
    42504648        GCSuspendEEEnd         Test.exe    4372          
    42504816        GCStart_V1             Test.exe    4372        102019  
    42504907        GCStart_V1             Test.exe    4372        102020  
    42514170        GCEnd_V1               Test.exe    4372          
    42514204        GCHeapStats            Test.exe    4372        102020  
    42832052        GCRestartEEBegin       Test.exe    4372          
    42832136        GCRestartEEEnd         Test.exe    4372          
    63685394        GCSuspendEEBegin_V1    Test.exe    4744             6  
    63686347        GCSuspendEEEnd         Test.exe    4744          
    63784294        GCRestartEEBegin       Test.exe    4744          
    63784407        GCRestartEEEnd         Test.exe    4744          
    89931423        GCEnd_V1               Test.exe    4372        102019  
    89931464        GCHeapStats            Test.exe    4372          
    ```  
  
     在 42504816 的 `GCStart_V1` 事件表示這是背景記憶體回收，因為最後一個欄位是 `1`。 這會變成記憶體回收第  102019 號。  
  
     因為需要先進行暫時記憶體回收，才能開始背景記憶體回收，因此發生 `GCStart` 事件。 這會變成記憶體回收第  102020 號。  
  
     在 42514170 處，記憶體回收第 102020 號完成。 Managed 執行緒會在此時重新啟動。 此步驟會在執行緒 4372，觸發此背景記憶體回收完成。  
  
     在執行緒 4744 上發生擱置。 這是背景記憶體回收唯一必須暫止 Managed 執行緒的時間。 這段期間是大約 99 毫秒 ((63784407-63685394)/1000)。  
  
     背景記憶體回收的 `GCEnd` 事件位於 89931423。 這表示背景記憶體回收持續大約 47 秒 ((89931423-42504816)/1000)。  
  
     在 Managed 執行緒執行時，您可能看到發生任意數目的暫時記憶體回收。  
  
<a name="Triggered"></a>   
##### <a name="to-determine-what-triggered-a-garbage-collection"></a>判斷觸發記憶體回收的原因  
  
-   在已載入 SOS 偵錯工具擴充功能的 WinDbg 或 Visual Studio 偵錯工具中，輸入下列命令以顯示所有執行緒及其呼叫堆疊：  
  
     **~\*kb**  
  
     這個命令會顯示與下列類似的輸出。  
  
    ```  
    0012f3b0 79ff0bf8 mscorwks!WKS::GCHeap::GarbageCollect   
    0012f454 30002894 mscorwks!GCInterface::CollectGeneration+0xa4  
    0012f490 79fa22bd fragment_ni!request.Main(System.String[])+0x48  
    ```  
  
     如果記憶體回收的起因是來自作業系統的記憶體不足通知，則呼叫堆疊會很類似，只除了執行緒是完成項執行緒。 完成項執行緒會收到非同步記憶體偏低通知，並引發記憶體回收。  
  
     如果記憶體回收的起因是記憶體配置，則堆疊會如下所示：  
  
    ```  
    0012f230 7a07c551 mscorwks!WKS::GCHeap::GarbageCollectGeneration  
    0012f2b8 7a07cba8 mscorwks!WKS::gc_heap::try_allocate_more_space+0x1a1  
    0012f2d4 7a07cefb mscorwks!WKS::gc_heap::allocate_more_space+0x18  
    0012f2f4 7a02a51b mscorwks!WKS::GCHeap::Alloc+0x4b  
    0012f310 7a02ae4c mscorwks!Alloc+0x60  
    0012f364 7a030e46 mscorwks!FastAllocatePrimitiveArray+0xbd  
    0012f424 300027f4 mscorwks!JIT_NewArr1+0x148  
    000af70f 3000299f fragment_ni!request..ctor(Int32, Single)+0x20c  
    0000002a 79fa22bd fragment_ni!request.Main(System.String[])+0x153  
    ```  
  
     Just-In-Time 協助程式 (`JIT_New*`) 實際上呼叫 `GCHeap::GarbageCollectGeneration`。 如果您判斷層代 2 記憶體回收起因是配置，則必須判斷層代 2 記憶體回收會回收哪些物件及如何加以避免。 也就是您想要判斷層代 2 記憶體回收開始和結束之間的差異，以及造成層代 2 記憶體回收的物件。  
  
     例如，在偵錯工具中輸入下列命令以顯示層代 2 記憶體回收的開始：  
  
     **!dumpheap –stat**  
  
     範例輸出 (經過刪減以顯示使用最大空間的物件)：  
  
    ```  
    79124228    31857      9862328 System.Object[]  
    035f0384    25668     11601936 Toolkit.TlkPosition  
    00155f80    21248     12256296      Free  
    79103b6c   297003     13068132 System.Threading.ReaderWriterLock  
    7a747ad4   708732     14174640 System.Collections.Specialized.HybridDictionary  
    7a747c78   786498     15729960 System.Collections.Specialized.ListDictionary+DictionaryNode  
    7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary  
    035f0ee4    89192     38887712 Toolkit.TlkOrder  
    00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]  
    7912c444    91616     71887080 System.Double[]  
    791242ec    32451     82462728 System.Collections.Hashtable+bucket[]  
    790fa3e0  2459154    112128436 System.String  
    Total 6471774 objects  
    ```  
  
     在層代 2 結束時重複執行命令：  
  
     **!dumpheap –stat**  
  
     範例輸出 (經過刪減以顯示使用最大空間的物件)：  
  
    ```  
    79124228    26648      9314256 System.Object[]  
    035f0384    25668     11601936 Toolkit.TlkPosition  
    79103b6c   296770     13057880 System.Threading.ReaderWriterLock  
    7a747ad4   708730     14174600 System.Collections.Specialized.HybridDictionary  
    7a747c78   786497     15729940 System.Collections.Specialized.ListDictionary+DictionaryNode  
    7a747bac   700298     19608344 System.Collections.Specialized.ListDictionary  
    00155f80    13806     34007212      Free  
    035f0ee4    89187     38885532 Toolkit.TlkOrder  
    00fcae40     6193     44911636 WaveBasedStrategy.Tick_Snap[]  
    791242ec    32370     82359768 System.Collections.Hashtable+bucket[]  
    790fa3e0  2440020    111341808 System.String  
    Total 6417525 objects  
    ```  
  
     `double[]` 物件從輸出結束消失，這表示它們已被回收。 這些物件大約 70 MB。 剩餘的物件變更不多。 因此，這些 `double[]` 物件便是這個層代 2 記憶體回收發生的原因。 您的下一個步驟是判斷 `double[]` 物件為何出現，以及其終止原因。 您可以要求程式碼開發人員這些物件的來源，或者您可以使用 **gcroot** 命令。  
  
<a name="HighCPU"></a>   
##### <a name="to-determine-whether-high-cpu-usage-is-caused-by-garbage-collection"></a>判斷高 CPU 使用量是否由於記憶體回收所造成  
  
-   相互關聯 `% Time in GC` 記憶體效能計數器值與處理序時間。  
  
     如果 `% Time in GC` 值與處理序時間同時升高，則記憶體回收便造成高 CPU 使用量。 否則，請針對應用程式進行程式碼剖析，尋找發生高使用量的地方。  
  
## <a name="see-also"></a>請參閱  
 [記憶體回收](../../../docs/standard/garbage-collection/index.md)
