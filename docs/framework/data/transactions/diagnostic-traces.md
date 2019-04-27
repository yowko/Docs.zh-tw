---
title: 診斷追蹤
ms.date: 03/30/2017
ms.assetid: 28e77a63-d20d-4b6a-9caf-ddad86550427
ms.openlocfilehash: 56f79fb9140785188996cc413eca4dd530037ccd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934793"
---
# <a name="diagnostic-traces"></a><span data-ttu-id="2ea42-102">診斷追蹤</span><span class="sxs-lookup"><span data-stu-id="2ea42-102">Diagnostic Traces</span></span>
<span data-ttu-id="2ea42-103">追蹤就是在應用程式執行期間，所產生的特定訊息之發行動作。</span><span class="sxs-lookup"><span data-stu-id="2ea42-103">Traces are the publishing of specific messages that are generated during application execution.</span></span> <span data-ttu-id="2ea42-104">使用追蹤功能時，您必須具有收集和記錄所傳送訊息的機制。</span><span class="sxs-lookup"><span data-stu-id="2ea42-104">When using tracing, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="2ea42-105">追蹤訊息由「接聽項」負責接收。</span><span class="sxs-lookup"><span data-stu-id="2ea42-105">Trace messages are received by listeners.</span></span> <span data-ttu-id="2ea42-106">接聽項的用途是收集、儲存和傳送追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="2ea42-106">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="2ea42-107">接聽項會將追蹤輸出導向至適當的目標，例如記錄檔、視窗或文字檔。</span><span class="sxs-lookup"><span data-stu-id="2ea42-107">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="2ea42-108">這類的接聽項，例如 <xref:System.Diagnostics.DefaultTraceListener>，會在啟用追蹤時自訂建立與初始。</span><span class="sxs-lookup"><span data-stu-id="2ea42-108">One such listener, the <xref:System.Diagnostics.DefaultTraceListener>, is automatically created and initialized when tracing is enabled.</span></span> <span data-ttu-id="2ea42-109">如果您要將追蹤輸出傳送至任何其他來源，您必須建立和初始化其他的追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="2ea42-109">If you want trace output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span> <span data-ttu-id="2ea42-110">您建立的接聽項應反映出您個人的需求。</span><span class="sxs-lookup"><span data-stu-id="2ea42-110">The listeners you create should reflect your individual needs.</span></span> <span data-ttu-id="2ea42-111">例如，您可能想要所有追蹤輸出的文字記錄。</span><span class="sxs-lookup"><span data-stu-id="2ea42-111">For example, you might want a text record of all trace output.</span></span> <span data-ttu-id="2ea42-112">在這種情況中，您建立的接聽項要在啟用時，將所有的輸出寫入新的文字檔。</span><span class="sxs-lookup"><span data-stu-id="2ea42-112">In this case, you would create a listener that wrote all output to a new text file when enabled.</span></span> <span data-ttu-id="2ea42-113">另一方面，您可能只想在應用程式執行期間檢視輸出。</span><span class="sxs-lookup"><span data-stu-id="2ea42-113">On the other hand, you might only want to view output during application execution.</span></span> <span data-ttu-id="2ea42-114">在這種情況中，您可建立導向所有輸出至主控台視窗的接聽項。</span><span class="sxs-lookup"><span data-stu-id="2ea42-114">In that case, you might create a listener that directed all output to a console window.</span></span> <span data-ttu-id="2ea42-115"><xref:System.Diagnostics.EventLogTraceListener> 可以導向追蹤輸出至事件記錄檔，而 <xref:System.Diagnostics.TextWriterTraceListener> 可將追蹤輸出寫入資料流。</span><span class="sxs-lookup"><span data-stu-id="2ea42-115">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log, and the <xref:System.Diagnostics.TextWriterTraceListener> can write trace output to a stream.</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="2ea42-116">啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="2ea42-116">Enabling Tracing</span></span>  
 <span data-ttu-id="2ea42-117">若要在交易處理期間啟用追蹤，您應該編輯應用程式的組態檔。</span><span class="sxs-lookup"><span data-stu-id="2ea42-117">To enable traces during transaction processing, you should edit your application’s configuration file.</span></span> <span data-ttu-id="2ea42-118">下列為範例。</span><span class="sxs-lookup"><span data-stu-id="2ea42-118">The following is an example.</span></span>  
  
```xml  
<configuration>  
<system.diagnostics>  
     <sources>  
          <source name="System.Transactions" switchValue="Warning">  
               <listeners>  
                    <add name="tx"   
                     type="System.Diagnostics.XmlWriterTraceListener"   
                     initializeData= "tx.log" />  
               </listeners>  
          </source>  
     </sources>  
</system.diagnostics>  
</configuration>  
```  
  
 <span data-ttu-id="2ea42-119"><xref:System.Transactions> 追蹤會寫入名為 "System.Transactions" 的來源中。</span><span class="sxs-lookup"><span data-stu-id="2ea42-119"><xref:System.Transactions> traces are written to the source named "System.Transactions".</span></span> <span data-ttu-id="2ea42-120">您可以使用 `add` 來指定要使用的追蹤接聽項名稱與型別。</span><span class="sxs-lookup"><span data-stu-id="2ea42-120">You can use `add` to specify the name and type of the trace listener you want to use.</span></span> <span data-ttu-id="2ea42-121">在我們的組態範例中，我們將接聽項命名為 "tx" 並將標準 .NET Framework 追蹤接聽項 (<xref:System.Diagnostics.XmlWriterTraceListener>) 當成要使用的型別加入。</span><span class="sxs-lookup"><span data-stu-id="2ea42-121">In our example configuration, we named the Listener "tx" and added the standard .NET Framework trace listener (<xref:System.Diagnostics.XmlWriterTraceListener>) as the type we want to use.</span></span> <span data-ttu-id="2ea42-122">請使用 `initializeData` 來設定該接聽項的記錄檔名稱。</span><span class="sxs-lookup"><span data-stu-id="2ea42-122">Use `initializeData` to set the name of the log file for that listener.</span></span> <span data-ttu-id="2ea42-123">此外，您可以使用完整路徑來取代簡單檔名。</span><span class="sxs-lookup"><span data-stu-id="2ea42-123">In addition, you can substitute a fully qualified path for a simple file name.</span></span>  
  
 <span data-ttu-id="2ea42-124">每個追蹤訊息類型都會指派一個層級來代表自己的重要程度。</span><span class="sxs-lookup"><span data-stu-id="2ea42-124">Each trace message type is assigned a level to indicate its degree of importance.</span></span> <span data-ttu-id="2ea42-125">如果應用程式定義域的追蹤層級等於或小於事件型別的層級，則會產生該訊息。</span><span class="sxs-lookup"><span data-stu-id="2ea42-125">If the app-domain’s trace level is equal or lower than the level of an event type, then that message is generated.</span></span> <span data-ttu-id="2ea42-126">追蹤層級可由組態檔中的 `switchValue` 設定來控制。</span><span class="sxs-lookup"><span data-stu-id="2ea42-126">The tracing level is controlled by the `switchValue` setting in the configuration file.</span></span> <span data-ttu-id="2ea42-127">下表定義了與診斷追蹤訊息相關聯的層級。</span><span class="sxs-lookup"><span data-stu-id="2ea42-127">The levels that are associated with diagnostic trace messages are defined in the following table.</span></span>  
  
|<span data-ttu-id="2ea42-128">追蹤層級</span><span class="sxs-lookup"><span data-stu-id="2ea42-128">Trace Level</span></span>|<span data-ttu-id="2ea42-129">描述</span><span class="sxs-lookup"><span data-stu-id="2ea42-129">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="2ea42-130">Critical</span><span class="sxs-lookup"><span data-stu-id="2ea42-130">Critical</span></span>|<span data-ttu-id="2ea42-131">已發生如下列所述的嚴重失敗情況：</span><span class="sxs-lookup"><span data-stu-id="2ea42-131">Serious failures, such as the following, have occurred:</span></span><br /><br /> <span data-ttu-id="2ea42-132">-使用者功能可能會導致立即的遺失時發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2ea42-132">-   An error that can cause an immediate loss in user functionality.</span></span><br /><span data-ttu-id="2ea42-133">-需要採取行動來避免功能喪失的系統管理員的事件。</span><span class="sxs-lookup"><span data-stu-id="2ea42-133">-   An event that requires an administrator to take action to avoid loss of functionality.</span></span><br /><span data-ttu-id="2ea42-134">程式碼會停止回應。</span><span class="sxs-lookup"><span data-stu-id="2ea42-134">-   Code hangs.</span></span><br /><span data-ttu-id="2ea42-135">-此追蹤層級也可以提供足夠的內容解譯其他關鍵追蹤。</span><span class="sxs-lookup"><span data-stu-id="2ea42-135">-   This tracing level can also provide sufficient context for interpreting other critical traces.</span></span> <span data-ttu-id="2ea42-136">如此便可協助找出導致嚴重失敗的作業序列。</span><span class="sxs-lookup"><span data-stu-id="2ea42-136">This can help to identify the sequence of operations leading to a serious failure.</span></span>|  
|<span data-ttu-id="2ea42-137">錯誤</span><span class="sxs-lookup"><span data-stu-id="2ea42-137">Error</span></span>|<span data-ttu-id="2ea42-138">已經發生可導致使用者功能喪失的錯誤 (例如，無效的組態或網路行為)。</span><span class="sxs-lookup"><span data-stu-id="2ea42-138">An error (for example, invalid configuration or network behavior) has occurred that can result in a loss of user functionality.</span></span>|  
|<span data-ttu-id="2ea42-139">警告</span><span class="sxs-lookup"><span data-stu-id="2ea42-139">Warning</span></span>|<span data-ttu-id="2ea42-140">存在一個可間接導致錯誤或嚴重失敗的狀況 (例如，配置失敗或到達上限)。</span><span class="sxs-lookup"><span data-stu-id="2ea42-140">A condition exists that can subsequently result in an error or critical failure (for example, allocation failing or approaching a limit).</span></span> <span data-ttu-id="2ea42-141">對使用者程式碼錯誤的正常處理 (例如，交易中止、逾時、驗證失敗) 也可能產生警告。</span><span class="sxs-lookup"><span data-stu-id="2ea42-141">Normal processing of errors from user code (for example, transaction aborted, timeouts, authentication failed) can also generate a warning.</span></span>|  
|<span data-ttu-id="2ea42-142">資訊</span><span class="sxs-lookup"><span data-stu-id="2ea42-142">Information</span></span>|<span data-ttu-id="2ea42-143">會產生對監控與診斷系統狀態、衡量效能，或描述分析有幫助的訊息。</span><span class="sxs-lookup"><span data-stu-id="2ea42-143">Messages helpful for monitoring and diagnosing system status, measuring performance, or profiling are generated.</span></span> <span data-ttu-id="2ea42-144">這些訊息包含交易與登記存留期事件，例如正在建立或認可的交易、重要界限的跨越，或是重要資源的配置。</span><span class="sxs-lookup"><span data-stu-id="2ea42-144">These can include transaction and enlistment lifetime events, such as a transaction being created or committed, the crossing of a significant boundary, or the allocation of significant resources.</span></span> <span data-ttu-id="2ea42-145">這時開發人員可以使用此類資訊來進行容量規劃與效能管理。</span><span class="sxs-lookup"><span data-stu-id="2ea42-145">A developer can then utilize such information for capacity planning and performance management.</span></span>|  
  
## <a name="trace-codes"></a><span data-ttu-id="2ea42-146">追蹤程式碼</span><span class="sxs-lookup"><span data-stu-id="2ea42-146">Trace Codes</span></span>  
 <span data-ttu-id="2ea42-147">下表列出由 <xref:System.Transactions> 基礎結構所產生的追蹤程式碼。</span><span class="sxs-lookup"><span data-stu-id="2ea42-147">The following table lists the trace codes that are generated by the <xref:System.Transactions> infrastructure.</span></span> <span data-ttu-id="2ea42-148">包含資料表中的追蹤程式碼識別項，<xref:System.Diagnostics.EventTypeFilter.EventType%2A>列舉型別層級追蹤，以及額外的資料中包含**TraceRecord**追蹤。</span><span class="sxs-lookup"><span data-stu-id="2ea42-148">Included in the table are the trace code identifier, the <xref:System.Diagnostics.EventTypeFilter.EventType%2A> enumeration level for the trace, and the extra data contained in the **TraceRecord** for the trace.</span></span> <span data-ttu-id="2ea42-149">此外，對應的追蹤的追蹤層級也會儲存在**TraceRecord**。</span><span class="sxs-lookup"><span data-stu-id="2ea42-149">In addition, the corresponding trace level of the trace is also stored in the **TraceRecord**.</span></span>  
  
|<span data-ttu-id="2ea42-150">TraceCode</span><span class="sxs-lookup"><span data-stu-id="2ea42-150">TraceCode</span></span>|<span data-ttu-id="2ea42-151">EventType</span><span class="sxs-lookup"><span data-stu-id="2ea42-151">EventType</span></span>|<span data-ttu-id="2ea42-152">TraceRecord 中的額外資料</span><span class="sxs-lookup"><span data-stu-id="2ea42-152">Extra data in TraceRecord</span></span>|  
|---------------|---------------|-------------------------------|  
|<span data-ttu-id="2ea42-153">TransactionCreated</span><span class="sxs-lookup"><span data-stu-id="2ea42-153">TransactionCreated</span></span>|<span data-ttu-id="2ea42-154">資訊</span><span class="sxs-lookup"><span data-stu-id="2ea42-154">Info</span></span>|<span data-ttu-id="2ea42-155">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="2ea42-155">TransactionTraceId</span></span>|  
|<span data-ttu-id="2ea42-156">TransactionPromoted</span><span class="sxs-lookup"><span data-stu-id="2ea42-156">TransactionPromoted</span></span>|<span data-ttu-id="2ea42-157">資訊</span><span class="sxs-lookup"><span data-stu-id="2ea42-157">Info</span></span>|<span data-ttu-id="2ea42-158">本機 TransactionTraceId、Distributed TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="2ea42-158">Local TransactionTraceId, Distributed TransactionTraceId</span></span>|  
|<span data-ttu-id="2ea42-159">EnlistmentCreated</span><span class="sxs-lookup"><span data-stu-id="2ea42-159">EnlistmentCreated</span></span>|<span data-ttu-id="2ea42-160">資訊</span><span class="sxs-lookup"><span data-stu-id="2ea42-160">Info</span></span>|<span data-ttu-id="2ea42-161">TransactionTraceId、EnlistmentTraceId、EnlistmentType (永久性/變動性)、EnlistmentOptions</span><span class="sxs-lookup"><span data-stu-id="2ea42-161">TransactionTraceId, EnlistmentTraceId, EnlistmentType (durable/volatile), EnlistmentOptions</span></span>|  
|<span data-ttu-id="2ea42-162">EnlistmentCallbackNegative</span><span class="sxs-lookup"><span data-stu-id="2ea42-162">EnlistmentCallbackNegative</span></span>|<span data-ttu-id="2ea42-163">警告</span><span class="sxs-lookup"><span data-stu-id="2ea42-163">Warning</span></span>|<span data-ttu-id="2ea42-164">TransactionTraceId、EnlistmentTraceId、</span><span class="sxs-lookup"><span data-stu-id="2ea42-164">TransactionTraceId, EnlistmentTraceId,</span></span><br /><br /> <span data-ttu-id="2ea42-165">回呼 (forcerollback/中止/indoubt)</span><span class="sxs-lookup"><span data-stu-id="2ea42-165">Callback (forcerollback/aborted/indoubt)</span></span>|  
|<span data-ttu-id="2ea42-166">TransactionRollbackCalled</span><span class="sxs-lookup"><span data-stu-id="2ea42-166">TransactionRollbackCalled</span></span>|<span data-ttu-id="2ea42-167">警告</span><span class="sxs-lookup"><span data-stu-id="2ea42-167">Warning</span></span>|<span data-ttu-id="2ea42-168">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="2ea42-168">TransactionTraceId</span></span>|  
|<span data-ttu-id="2ea42-169">TransactionAborted</span><span class="sxs-lookup"><span data-stu-id="2ea42-169">TransactionAborted</span></span>|<span data-ttu-id="2ea42-170">警告</span><span class="sxs-lookup"><span data-stu-id="2ea42-170">Warning</span></span>|<span data-ttu-id="2ea42-171">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="2ea42-171">TransactionTraceId</span></span>|  
|<span data-ttu-id="2ea42-172">TransactionInDoubt</span><span class="sxs-lookup"><span data-stu-id="2ea42-172">TransactionInDoubt</span></span>|<span data-ttu-id="2ea42-173">警告</span><span class="sxs-lookup"><span data-stu-id="2ea42-173">Warning</span></span>|<span data-ttu-id="2ea42-174">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="2ea42-174">TransactionTraceId</span></span>|  
|<span data-ttu-id="2ea42-175">TransactionScopeCreated</span><span class="sxs-lookup"><span data-stu-id="2ea42-175">TransactionScopeCreated</span></span>|<span data-ttu-id="2ea42-176">資訊</span><span class="sxs-lookup"><span data-stu-id="2ea42-176">Info</span></span>|<span data-ttu-id="2ea42-177">TransactionScopeResult，可能為下列各項：</span><span class="sxs-lookup"><span data-stu-id="2ea42-177">TransactionScopeResult, which can be the following:</span></span><br /><br /> <span data-ttu-id="2ea42-178">-新的交易。</span><span class="sxs-lookup"><span data-stu-id="2ea42-178">-   New transaction.</span></span><br /><span data-ttu-id="2ea42-179">傳遞的交易。</span><span class="sxs-lookup"><span data-stu-id="2ea42-179">-   Transaction passed.</span></span><br /><span data-ttu-id="2ea42-180">-相依交易已通過。</span><span class="sxs-lookup"><span data-stu-id="2ea42-180">-   Dependent transaction passed.</span></span><br /><span data-ttu-id="2ea42-181">-使用目前的交易。</span><span class="sxs-lookup"><span data-stu-id="2ea42-181">-   Using current transaction.</span></span><br /><span data-ttu-id="2ea42-182">-無交易。</span><span class="sxs-lookup"><span data-stu-id="2ea42-182">-   No transaction.</span></span><br /><br /> <span data-ttu-id="2ea42-183">目前新 TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="2ea42-183">new current TransactionTraceId</span></span>|  
|<span data-ttu-id="2ea42-184">TransactionScopeDisposed</span><span class="sxs-lookup"><span data-stu-id="2ea42-184">TransactionScopeDisposed</span></span>|<span data-ttu-id="2ea42-185">資訊</span><span class="sxs-lookup"><span data-stu-id="2ea42-185">Info</span></span>|<span data-ttu-id="2ea42-186">TransactionTraceId 範圍的 「 預期 」 目前的交易。</span><span class="sxs-lookup"><span data-stu-id="2ea42-186">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="2ea42-187">TransactionScopeIncomplete</span><span class="sxs-lookup"><span data-stu-id="2ea42-187">TransactionScopeIncomplete</span></span>|<span data-ttu-id="2ea42-188">警告</span><span class="sxs-lookup"><span data-stu-id="2ea42-188">Warning</span></span>|<span data-ttu-id="2ea42-189">TransactionTraceId 範圍的 「 預期 」 目前的交易。</span><span class="sxs-lookup"><span data-stu-id="2ea42-189">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="2ea42-190">TransactionScopeNestedIncorrectly</span><span class="sxs-lookup"><span data-stu-id="2ea42-190">TransactionScopeNestedIncorrectly</span></span>|<span data-ttu-id="2ea42-191">警告</span><span class="sxs-lookup"><span data-stu-id="2ea42-191">Warning</span></span>|<span data-ttu-id="2ea42-192">TransactionTraceId 範圍的 「 預期 」 目前的交易。</span><span class="sxs-lookup"><span data-stu-id="2ea42-192">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="2ea42-193">TransactionScopeCurrentTransactionChanged</span><span class="sxs-lookup"><span data-stu-id="2ea42-193">TransactionScopeCurrentTransactionChanged</span></span>|<span data-ttu-id="2ea42-194">警告</span><span class="sxs-lookup"><span data-stu-id="2ea42-194">Warning</span></span>|<span data-ttu-id="2ea42-195">目前舊有 TransactionTraceId、其他 TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="2ea42-195">Old current TransactionTraceId, other TransactionTraceId</span></span>|  
|<span data-ttu-id="2ea42-196">TransactionScopeTimeout</span><span class="sxs-lookup"><span data-stu-id="2ea42-196">TransactionScopeTimeout</span></span>|<span data-ttu-id="2ea42-197">警告</span><span class="sxs-lookup"><span data-stu-id="2ea42-197">Warning</span></span>|<span data-ttu-id="2ea42-198">TransactionTraceId 範圍的 「 預期 」 目前的交易。</span><span class="sxs-lookup"><span data-stu-id="2ea42-198">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="2ea42-199">DependentCloneCreated</span><span class="sxs-lookup"><span data-stu-id="2ea42-199">DependentCloneCreated</span></span>|<span data-ttu-id="2ea42-200">資訊</span><span class="sxs-lookup"><span data-stu-id="2ea42-200">Info</span></span>|<span data-ttu-id="2ea42-201">TransactionTraceId、所建立的相依交易型別 (RollbackIfNotComplete/BlockCommitUntilComplete)</span><span class="sxs-lookup"><span data-stu-id="2ea42-201">TransactionTraceId, type of dependent transaction created (RollbackIfNotComplete/BlockCommitUntilComplete)</span></span>|  
|<span data-ttu-id="2ea42-202">DependentCloneComplete</span><span class="sxs-lookup"><span data-stu-id="2ea42-202">DependentCloneComplete</span></span>|<span data-ttu-id="2ea42-203">資訊</span><span class="sxs-lookup"><span data-stu-id="2ea42-203">Info</span></span>|<span data-ttu-id="2ea42-204">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="2ea42-204">TransactionTraceId</span></span>|  
|<span data-ttu-id="2ea42-205">RecoveryComplete</span><span class="sxs-lookup"><span data-stu-id="2ea42-205">RecoveryComplete</span></span>|<span data-ttu-id="2ea42-206">資訊</span><span class="sxs-lookup"><span data-stu-id="2ea42-206">Info</span></span>|<span data-ttu-id="2ea42-207">資源管理員 GUID (從基底)</span><span class="sxs-lookup"><span data-stu-id="2ea42-207">Resource Manager GUID (from base)</span></span>|  
|<span data-ttu-id="2ea42-208">Reenlist</span><span class="sxs-lookup"><span data-stu-id="2ea42-208">Reenlist</span></span>|<span data-ttu-id="2ea42-209">資訊</span><span class="sxs-lookup"><span data-stu-id="2ea42-209">Info</span></span>|<span data-ttu-id="2ea42-210">資源管理員 GUID (從基底)</span><span class="sxs-lookup"><span data-stu-id="2ea42-210">Resource Manager GUID (from base)</span></span>|  
|<span data-ttu-id="2ea42-211">TransactionSerialized</span><span class="sxs-lookup"><span data-stu-id="2ea42-211">TransactionSerialized</span></span>|<span data-ttu-id="2ea42-212">資訊</span><span class="sxs-lookup"><span data-stu-id="2ea42-212">Info</span></span>|<span data-ttu-id="2ea42-213">TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="2ea42-213">TransactionTraceId.</span></span>|  
|<span data-ttu-id="2ea42-214">TransactionException</span><span class="sxs-lookup"><span data-stu-id="2ea42-214">TransactionException</span></span>|<span data-ttu-id="2ea42-215">錯誤</span><span class="sxs-lookup"><span data-stu-id="2ea42-215">Error</span></span>|<span data-ttu-id="2ea42-216">例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="2ea42-216">Exception message</span></span>|  
|<span data-ttu-id="2ea42-217">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="2ea42-217">InvalidOperationException</span></span>|<span data-ttu-id="2ea42-218">錯誤</span><span class="sxs-lookup"><span data-stu-id="2ea42-218">Error</span></span>|<span data-ttu-id="2ea42-219">例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="2ea42-219">Exception message</span></span>|  
|<span data-ttu-id="2ea42-220">InternalError</span><span class="sxs-lookup"><span data-stu-id="2ea42-220">InternalError</span></span>|<span data-ttu-id="2ea42-221">Critical</span><span class="sxs-lookup"><span data-stu-id="2ea42-221">Critical</span></span>|<span data-ttu-id="2ea42-222">例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="2ea42-222">Exception message</span></span>|  
|<span data-ttu-id="2ea42-223">TransferEvent</span><span class="sxs-lookup"><span data-stu-id="2ea42-223">TransferEvent</span></span>||<span data-ttu-id="2ea42-224">當交易已還原序列化，或是由 <xref:System.Transactions> 交易提升為分散式交易，則會寫入來自 ExecutionContext 與分散式交易識別碼的目前 ActivityID。</span><span class="sxs-lookup"><span data-stu-id="2ea42-224">When a transaction is deserialized, or promoted from a <xref:System.Transactions> transaction to a distributed one, the current ActivityID from the ExecutionContext and the distributed transaction ID are written.</span></span><br /><br /> <span data-ttu-id="2ea42-225">當 DTC 回呼 Managed 程式碼，分散式交易識別碼就會針對回呼的持續時間設為 ExecutionContext 中的 ActivityID。</span><span class="sxs-lookup"><span data-stu-id="2ea42-225">When the DTC calls back into managed code, the distributed transaction ID is set as the ActivityID in the ExecutionContext for the duration of the callback.</span></span>|  
|<span data-ttu-id="2ea42-226">ConfiguredDefaultTimeoutAdjusted</span><span class="sxs-lookup"><span data-stu-id="2ea42-226">ConfiguredDefaultTimeoutAdjusted</span></span>|<span data-ttu-id="2ea42-227">警告</span><span class="sxs-lookup"><span data-stu-id="2ea42-227">Warning</span></span>|<span data-ttu-id="2ea42-228">無額外的資料</span><span class="sxs-lookup"><span data-stu-id="2ea42-228">No extra data</span></span>|  
|<span data-ttu-id="2ea42-229">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="2ea42-229">TransactionTimeout</span></span>|<span data-ttu-id="2ea42-230">警告</span><span class="sxs-lookup"><span data-stu-id="2ea42-230">Warning</span></span>|<span data-ttu-id="2ea42-231">目前逾時的交易 TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="2ea42-231">The TransactionTraceId of the transaction being timed out.</span></span>|  
  
 <span data-ttu-id="2ea42-232">每個前置額外資料項目的 XML 結構描述都具有下列格式。</span><span class="sxs-lookup"><span data-stu-id="2ea42-232">The XML schema for each of the preceding extra data items has the following format.</span></span>  
  
### <a name="transactiontraceidentifier"></a><span data-ttu-id="2ea42-233">TransactionTraceIdentifier</span><span class="sxs-lookup"><span data-stu-id="2ea42-233">TransactionTraceIdentifier</span></span>  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `< CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `</TransactionTraceIdentifier>`  
  
### <a name="enlistmenttraceidentifier"></a><span data-ttu-id="2ea42-234">EnlistmentTraceIdentifier</span><span class="sxs-lookup"><span data-stu-id="2ea42-234">EnlistmentTraceIdentifier</span></span>  
 `<EnlistmentTraceIdentifier>`  
  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `<CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<EnlistmentIdentifier>`  
  
 `the enlistment id number`  
  
 `</EnlistmentIdentifier>`  
  
 `</EnlistmentTraceIdentifier>`  
  
### <a name="resource-manager-identifier"></a><span data-ttu-id="2ea42-235">資源管理員識別項</span><span class="sxs-lookup"><span data-stu-id="2ea42-235">Resource Manager Identifier</span></span>  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
## <a name="security-issues-for-tracing"></a><span data-ttu-id="2ea42-236">追蹤安全性問題</span><span class="sxs-lookup"><span data-stu-id="2ea42-236">Security Issues For Tracing</span></span>  
 <span data-ttu-id="2ea42-237">當您以系統管理員身分開啟追蹤時，機密資訊可能會寫入追蹤記錄檔可公開檢視預設。</span><span class="sxs-lookup"><span data-stu-id="2ea42-237">When you as an administrator turn on tracing, sensitive information might be written to a trace log that is publicly viewable by default.</span></span> <span data-ttu-id="2ea42-238">若要解決任何可能的安全性威脅，您應該考慮將追蹤記錄檔儲存在安全的位置共用和檔案系統存取權限所控制。</span><span class="sxs-lookup"><span data-stu-id="2ea42-238">To mitigate any possible security threat, you should consider storing the trace log in a secure location controlled by share and file system access permissions.</span></span>
