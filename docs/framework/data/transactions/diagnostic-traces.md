---
title: 診斷追蹤
description: 瞭解 .NET 中的診斷追蹤。 追蹤就是在應用程式執行期間，所產生的特定訊息之發行動作。
ms.date: 03/30/2017
ms.assetid: 28e77a63-d20d-4b6a-9caf-ddad86550427
ms.openlocfilehash: 1999cd922b9e7299cbf3c10a702eb4d2dc6c3fbb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177237"
---
# <a name="diagnostic-traces"></a><span data-ttu-id="ace15-104">診斷追蹤</span><span class="sxs-lookup"><span data-stu-id="ace15-104">Diagnostic Traces</span></span>

<span data-ttu-id="ace15-105">追蹤就是在應用程式執行期間，所產生的特定訊息之發行動作。</span><span class="sxs-lookup"><span data-stu-id="ace15-105">Traces are the publishing of specific messages that are generated during application execution.</span></span> <span data-ttu-id="ace15-106">使用追蹤功能時，您必須具有收集和記錄所傳送訊息的機制。</span><span class="sxs-lookup"><span data-stu-id="ace15-106">When using tracing, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="ace15-107">追蹤訊息由「接聽項」負責接收。</span><span class="sxs-lookup"><span data-stu-id="ace15-107">Trace messages are received by listeners.</span></span> <span data-ttu-id="ace15-108">接聽項的用途是收集、儲存和傳送追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="ace15-108">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="ace15-109">接聽項會將追蹤輸出導向至適當的目標，例如記錄檔、視窗或文字檔。</span><span class="sxs-lookup"><span data-stu-id="ace15-109">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="ace15-110">這類的接聽項，例如 <xref:System.Diagnostics.DefaultTraceListener>，會在啟用追蹤時自訂建立與初始。</span><span class="sxs-lookup"><span data-stu-id="ace15-110">One such listener, the <xref:System.Diagnostics.DefaultTraceListener>, is automatically created and initialized when tracing is enabled.</span></span> <span data-ttu-id="ace15-111">如果您要將追蹤輸出傳送至任何其他來源，您必須建立和初始化其他的追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="ace15-111">If you want trace output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span> <span data-ttu-id="ace15-112">您建立的接聽項應反映出您個人的需求。</span><span class="sxs-lookup"><span data-stu-id="ace15-112">The listeners you create should reflect your individual needs.</span></span> <span data-ttu-id="ace15-113">例如，您可能想要所有追蹤輸出的文字記錄。</span><span class="sxs-lookup"><span data-stu-id="ace15-113">For example, you might want a text record of all trace output.</span></span> <span data-ttu-id="ace15-114">在這種情況中，您建立的接聽項要在啟用時，將所有的輸出寫入新的文字檔。</span><span class="sxs-lookup"><span data-stu-id="ace15-114">In this case, you would create a listener that wrote all output to a new text file when enabled.</span></span> <span data-ttu-id="ace15-115">另一方面，您可能只想在應用程式執行期間檢視輸出。</span><span class="sxs-lookup"><span data-stu-id="ace15-115">On the other hand, you might only want to view output during application execution.</span></span> <span data-ttu-id="ace15-116">在這種情況中，您可建立導向所有輸出至主控台視窗的接聽項。</span><span class="sxs-lookup"><span data-stu-id="ace15-116">In that case, you might create a listener that directed all output to a console window.</span></span> <span data-ttu-id="ace15-117"><xref:System.Diagnostics.EventLogTraceListener> 可以導向追蹤輸出至事件記錄檔，而 <xref:System.Diagnostics.TextWriterTraceListener> 可將追蹤輸出寫入資料流。</span><span class="sxs-lookup"><span data-stu-id="ace15-117">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log, and the <xref:System.Diagnostics.TextWriterTraceListener> can write trace output to a stream.</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="ace15-118">啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="ace15-118">Enabling Tracing</span></span>  

 <span data-ttu-id="ace15-119">若要在交易處理期間啟用追蹤，您應該編輯應用程式的組態檔。</span><span class="sxs-lookup"><span data-stu-id="ace15-119">To enable traces during transaction processing, you should edit your application’s configuration file.</span></span> <span data-ttu-id="ace15-120">以下是一個範例。</span><span class="sxs-lookup"><span data-stu-id="ace15-120">The following is an example.</span></span>  
  
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
  
 <span data-ttu-id="ace15-121"><xref:System.Transactions> 追蹤會寫入名為 "System.Transactions" 的來源中。</span><span class="sxs-lookup"><span data-stu-id="ace15-121"><xref:System.Transactions> traces are written to the source named "System.Transactions".</span></span> <span data-ttu-id="ace15-122">您可以使用 `add` 來指定要使用的追蹤接聽項名稱與型別。</span><span class="sxs-lookup"><span data-stu-id="ace15-122">You can use `add` to specify the name and type of the trace listener you want to use.</span></span> <span data-ttu-id="ace15-123">在我們的組態範例中，我們將接聽項命名為 "tx" 並將標準 .NET Framework 追蹤接聽項 (<xref:System.Diagnostics.XmlWriterTraceListener>) 當成要使用的型別加入。</span><span class="sxs-lookup"><span data-stu-id="ace15-123">In our example configuration, we named the Listener "tx" and added the standard .NET Framework trace listener (<xref:System.Diagnostics.XmlWriterTraceListener>) as the type we want to use.</span></span> <span data-ttu-id="ace15-124">請使用 `initializeData` 來設定該接聽項的記錄檔名稱。</span><span class="sxs-lookup"><span data-stu-id="ace15-124">Use `initializeData` to set the name of the log file for that listener.</span></span> <span data-ttu-id="ace15-125">此外，您可以使用完整路徑來取代簡單檔名。</span><span class="sxs-lookup"><span data-stu-id="ace15-125">In addition, you can substitute a fully qualified path for a simple file name.</span></span>  
  
 <span data-ttu-id="ace15-126">每個追蹤訊息類型都會指派一個層級來代表自己的重要程度。</span><span class="sxs-lookup"><span data-stu-id="ace15-126">Each trace message type is assigned a level to indicate its degree of importance.</span></span> <span data-ttu-id="ace15-127">如果應用程式定義域的追蹤層級等於或小於事件型別的層級，則會產生該訊息。</span><span class="sxs-lookup"><span data-stu-id="ace15-127">If the app-domain’s trace level is equal or lower than the level of an event type, then that message is generated.</span></span> <span data-ttu-id="ace15-128">追蹤層級可由組態檔中的 `switchValue` 設定來控制。</span><span class="sxs-lookup"><span data-stu-id="ace15-128">The tracing level is controlled by the `switchValue` setting in the configuration file.</span></span> <span data-ttu-id="ace15-129">下表定義了與診斷追蹤訊息相關聯的層級。</span><span class="sxs-lookup"><span data-stu-id="ace15-129">The levels that are associated with diagnostic trace messages are defined in the following table.</span></span>  
  
|<span data-ttu-id="ace15-130">追蹤層級</span><span class="sxs-lookup"><span data-stu-id="ace15-130">Trace Level</span></span>|<span data-ttu-id="ace15-131">描述</span><span class="sxs-lookup"><span data-stu-id="ace15-131">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="ace15-132">重大</span><span class="sxs-lookup"><span data-stu-id="ace15-132">Critical</span></span>|<span data-ttu-id="ace15-133">已發生如下列所述的嚴重失敗情況：</span><span class="sxs-lookup"><span data-stu-id="ace15-133">Serious failures, such as the following, have occurred:</span></span><br /><br /> <span data-ttu-id="ace15-134">-可能會導致使用者功能立即遺失的錯誤。</span><span class="sxs-lookup"><span data-stu-id="ace15-134">-   An error that can cause an immediate loss in user functionality.</span></span><br /><span data-ttu-id="ace15-135">-需要系統管理員採取動作以避免功能遺失的事件。</span><span class="sxs-lookup"><span data-stu-id="ace15-135">-   An event that requires an administrator to take action to avoid loss of functionality.</span></span><br /><span data-ttu-id="ace15-136">-程式碼停止回應。</span><span class="sxs-lookup"><span data-stu-id="ace15-136">-   Code hangs.</span></span><br /><span data-ttu-id="ace15-137">-此追蹤層級也可以提供足夠的內容來解讀其他重要的追蹤。</span><span class="sxs-lookup"><span data-stu-id="ace15-137">-   This tracing level can also provide sufficient context for interpreting other critical traces.</span></span> <span data-ttu-id="ace15-138">如此便可協助找出導致嚴重失敗的作業序列。</span><span class="sxs-lookup"><span data-stu-id="ace15-138">This can help to identify the sequence of operations leading to a serious failure.</span></span>|  
|<span data-ttu-id="ace15-139">錯誤</span><span class="sxs-lookup"><span data-stu-id="ace15-139">Error</span></span>|<span data-ttu-id="ace15-140">已經發生可導致使用者功能喪失的錯誤 (例如，無效的組態或網路行為)。</span><span class="sxs-lookup"><span data-stu-id="ace15-140">An error (for example, invalid configuration or network behavior) has occurred that can result in a loss of user functionality.</span></span>|  
|<span data-ttu-id="ace15-141">警告</span><span class="sxs-lookup"><span data-stu-id="ace15-141">Warning</span></span>|<span data-ttu-id="ace15-142">存在一個可間接導致錯誤或嚴重失敗的狀況 (例如，配置失敗或到達上限)。</span><span class="sxs-lookup"><span data-stu-id="ace15-142">A condition exists that can subsequently result in an error or critical failure (for example, allocation failing or approaching a limit).</span></span> <span data-ttu-id="ace15-143">對使用者程式碼錯誤的正常處理 (例如，交易中止、逾時、驗證失敗) 也可能產生警告。</span><span class="sxs-lookup"><span data-stu-id="ace15-143">Normal processing of errors from user code (for example, transaction aborted, timeouts, authentication failed) can also generate a warning.</span></span>|  
|<span data-ttu-id="ace15-144">資訊</span><span class="sxs-lookup"><span data-stu-id="ace15-144">Information</span></span>|<span data-ttu-id="ace15-145">會產生對監控與診斷系統狀態、衡量效能，或描述分析有幫助的訊息。</span><span class="sxs-lookup"><span data-stu-id="ace15-145">Messages helpful for monitoring and diagnosing system status, measuring performance, or profiling are generated.</span></span> <span data-ttu-id="ace15-146">這些訊息包含交易與登記存留期事件，例如正在建立或認可的交易、重要界限的跨越，或是重要資源的配置。</span><span class="sxs-lookup"><span data-stu-id="ace15-146">These can include transaction and enlistment lifetime events, such as a transaction being created or committed, the crossing of a significant boundary, or the allocation of significant resources.</span></span> <span data-ttu-id="ace15-147">這時開發人員可以使用此類資訊來進行容量規劃與效能管理。</span><span class="sxs-lookup"><span data-stu-id="ace15-147">A developer can then utilize such information for capacity planning and performance management.</span></span>|  
  
## <a name="trace-codes"></a><span data-ttu-id="ace15-148">追蹤程式碼</span><span class="sxs-lookup"><span data-stu-id="ace15-148">Trace Codes</span></span>  

 <span data-ttu-id="ace15-149">下表列出由 <xref:System.Transactions> 基礎結構所產生的追蹤程式碼。</span><span class="sxs-lookup"><span data-stu-id="ace15-149">The following table lists the trace codes that are generated by the <xref:System.Transactions> infrastructure.</span></span> <span data-ttu-id="ace15-150">資料表中包含追蹤程式碼識別碼、 <xref:System.Diagnostics.EventTypeFilter.EventType%2A> 追蹤的列舉層級，以及追蹤 **TraceRecord** 中包含的額外資料。</span><span class="sxs-lookup"><span data-stu-id="ace15-150">Included in the table are the trace code identifier, the <xref:System.Diagnostics.EventTypeFilter.EventType%2A> enumeration level for the trace, and the extra data contained in the **TraceRecord** for the trace.</span></span> <span data-ttu-id="ace15-151">此外，追蹤的對應追蹤層級也會儲存在 **TraceRecord**中。</span><span class="sxs-lookup"><span data-stu-id="ace15-151">In addition, the corresponding trace level of the trace is also stored in the **TraceRecord**.</span></span>  
  
|<span data-ttu-id="ace15-152">TraceCode</span><span class="sxs-lookup"><span data-stu-id="ace15-152">TraceCode</span></span>|<span data-ttu-id="ace15-153">EventType</span><span class="sxs-lookup"><span data-stu-id="ace15-153">EventType</span></span>|<span data-ttu-id="ace15-154">TraceRecord 中的額外資料</span><span class="sxs-lookup"><span data-stu-id="ace15-154">Extra data in TraceRecord</span></span>|  
|---------------|---------------|-------------------------------|  
|<span data-ttu-id="ace15-155">TransactionCreated</span><span class="sxs-lookup"><span data-stu-id="ace15-155">TransactionCreated</span></span>|<span data-ttu-id="ace15-156">資訊</span><span class="sxs-lookup"><span data-stu-id="ace15-156">Info</span></span>|<span data-ttu-id="ace15-157">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="ace15-157">TransactionTraceId</span></span>|  
|<span data-ttu-id="ace15-158">TransactionPromoted</span><span class="sxs-lookup"><span data-stu-id="ace15-158">TransactionPromoted</span></span>|<span data-ttu-id="ace15-159">資訊</span><span class="sxs-lookup"><span data-stu-id="ace15-159">Info</span></span>|<span data-ttu-id="ace15-160">本機 TransactionTraceId、Distributed TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="ace15-160">Local TransactionTraceId, Distributed TransactionTraceId</span></span>|  
|<span data-ttu-id="ace15-161">EnlistmentCreated</span><span class="sxs-lookup"><span data-stu-id="ace15-161">EnlistmentCreated</span></span>|<span data-ttu-id="ace15-162">資訊</span><span class="sxs-lookup"><span data-stu-id="ace15-162">Info</span></span>|<span data-ttu-id="ace15-163">TransactionTraceId、EnlistmentTraceId、EnlistmentType (永久性/變動性)、EnlistmentOptions</span><span class="sxs-lookup"><span data-stu-id="ace15-163">TransactionTraceId, EnlistmentTraceId, EnlistmentType (durable/volatile), EnlistmentOptions</span></span>|  
|<span data-ttu-id="ace15-164">EnlistmentCallbackNegative</span><span class="sxs-lookup"><span data-stu-id="ace15-164">EnlistmentCallbackNegative</span></span>|<span data-ttu-id="ace15-165">警告</span><span class="sxs-lookup"><span data-stu-id="ace15-165">Warning</span></span>|<span data-ttu-id="ace15-166">TransactionTraceId、EnlistmentTraceId、</span><span class="sxs-lookup"><span data-stu-id="ace15-166">TransactionTraceId, EnlistmentTraceId,</span></span><br /><br /> <span data-ttu-id="ace15-167">回呼 (forcerollback/中止/indoubt)</span><span class="sxs-lookup"><span data-stu-id="ace15-167">Callback (forcerollback/aborted/indoubt)</span></span>|  
|<span data-ttu-id="ace15-168">TransactionRollbackCalled</span><span class="sxs-lookup"><span data-stu-id="ace15-168">TransactionRollbackCalled</span></span>|<span data-ttu-id="ace15-169">警告</span><span class="sxs-lookup"><span data-stu-id="ace15-169">Warning</span></span>|<span data-ttu-id="ace15-170">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="ace15-170">TransactionTraceId</span></span>|  
|<span data-ttu-id="ace15-171">TransactionAborted</span><span class="sxs-lookup"><span data-stu-id="ace15-171">TransactionAborted</span></span>|<span data-ttu-id="ace15-172">警告</span><span class="sxs-lookup"><span data-stu-id="ace15-172">Warning</span></span>|<span data-ttu-id="ace15-173">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="ace15-173">TransactionTraceId</span></span>|  
|<span data-ttu-id="ace15-174">TransactionInDoubt</span><span class="sxs-lookup"><span data-stu-id="ace15-174">TransactionInDoubt</span></span>|<span data-ttu-id="ace15-175">警告</span><span class="sxs-lookup"><span data-stu-id="ace15-175">Warning</span></span>|<span data-ttu-id="ace15-176">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="ace15-176">TransactionTraceId</span></span>|  
|<span data-ttu-id="ace15-177">TransactionScopeCreated</span><span class="sxs-lookup"><span data-stu-id="ace15-177">TransactionScopeCreated</span></span>|<span data-ttu-id="ace15-178">資訊</span><span class="sxs-lookup"><span data-stu-id="ace15-178">Info</span></span>|<span data-ttu-id="ace15-179">TransactionScopeResult，可能為下列各項：</span><span class="sxs-lookup"><span data-stu-id="ace15-179">TransactionScopeResult, which can be the following:</span></span><br /><br /> <span data-ttu-id="ace15-180">-新增交易。</span><span class="sxs-lookup"><span data-stu-id="ace15-180">-   New transaction.</span></span><br /><span data-ttu-id="ace15-181">-傳遞交易。</span><span class="sxs-lookup"><span data-stu-id="ace15-181">-   Transaction passed.</span></span><br /><span data-ttu-id="ace15-182">相依交易已通過。</span><span class="sxs-lookup"><span data-stu-id="ace15-182">-   Dependent transaction passed.</span></span><br /><span data-ttu-id="ace15-183">-使用目前的交易。</span><span class="sxs-lookup"><span data-stu-id="ace15-183">-   Using current transaction.</span></span><br /><span data-ttu-id="ace15-184">-無交易。</span><span class="sxs-lookup"><span data-stu-id="ace15-184">-   No transaction.</span></span><br /><br /> <span data-ttu-id="ace15-185">目前新 TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="ace15-185">new current TransactionTraceId</span></span>|  
|<span data-ttu-id="ace15-186">TransactionScopeDisposed</span><span class="sxs-lookup"><span data-stu-id="ace15-186">TransactionScopeDisposed</span></span>|<span data-ttu-id="ace15-187">資訊</span><span class="sxs-lookup"><span data-stu-id="ace15-187">Info</span></span>|<span data-ttu-id="ace15-188">範圍「預期」目前交易的 TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="ace15-188">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="ace15-189">TransactionScopeIncomplete</span><span class="sxs-lookup"><span data-stu-id="ace15-189">TransactionScopeIncomplete</span></span>|<span data-ttu-id="ace15-190">警告</span><span class="sxs-lookup"><span data-stu-id="ace15-190">Warning</span></span>|<span data-ttu-id="ace15-191">範圍「預期」目前交易的 TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="ace15-191">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="ace15-192">TransactionScopeNestedIncorrectly</span><span class="sxs-lookup"><span data-stu-id="ace15-192">TransactionScopeNestedIncorrectly</span></span>|<span data-ttu-id="ace15-193">警告</span><span class="sxs-lookup"><span data-stu-id="ace15-193">Warning</span></span>|<span data-ttu-id="ace15-194">範圍「預期」目前交易的 TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="ace15-194">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="ace15-195">TransactionScopeCurrentTransactionChanged</span><span class="sxs-lookup"><span data-stu-id="ace15-195">TransactionScopeCurrentTransactionChanged</span></span>|<span data-ttu-id="ace15-196">警告</span><span class="sxs-lookup"><span data-stu-id="ace15-196">Warning</span></span>|<span data-ttu-id="ace15-197">目前舊有 TransactionTraceId、其他 TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="ace15-197">Old current TransactionTraceId, other TransactionTraceId</span></span>|  
|<span data-ttu-id="ace15-198">TransactionScopeTimeout</span><span class="sxs-lookup"><span data-stu-id="ace15-198">TransactionScopeTimeout</span></span>|<span data-ttu-id="ace15-199">警告</span><span class="sxs-lookup"><span data-stu-id="ace15-199">Warning</span></span>|<span data-ttu-id="ace15-200">範圍「預期」目前交易的 TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="ace15-200">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="ace15-201">DependentCloneCreated</span><span class="sxs-lookup"><span data-stu-id="ace15-201">DependentCloneCreated</span></span>|<span data-ttu-id="ace15-202">資訊</span><span class="sxs-lookup"><span data-stu-id="ace15-202">Info</span></span>|<span data-ttu-id="ace15-203">TransactionTraceId、所建立的相依交易型別 (RollbackIfNotComplete/BlockCommitUntilComplete)</span><span class="sxs-lookup"><span data-stu-id="ace15-203">TransactionTraceId, type of dependent transaction created (RollbackIfNotComplete/BlockCommitUntilComplete)</span></span>|  
|<span data-ttu-id="ace15-204">DependentCloneComplete</span><span class="sxs-lookup"><span data-stu-id="ace15-204">DependentCloneComplete</span></span>|<span data-ttu-id="ace15-205">資訊</span><span class="sxs-lookup"><span data-stu-id="ace15-205">Info</span></span>|<span data-ttu-id="ace15-206">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="ace15-206">TransactionTraceId</span></span>|  
|<span data-ttu-id="ace15-207">RecoveryComplete</span><span class="sxs-lookup"><span data-stu-id="ace15-207">RecoveryComplete</span></span>|<span data-ttu-id="ace15-208">資訊</span><span class="sxs-lookup"><span data-stu-id="ace15-208">Info</span></span>|<span data-ttu-id="ace15-209">資源管理員 GUID (從基底)</span><span class="sxs-lookup"><span data-stu-id="ace15-209">Resource Manager GUID (from base)</span></span>|  
|<span data-ttu-id="ace15-210">Reenlist</span><span class="sxs-lookup"><span data-stu-id="ace15-210">Reenlist</span></span>|<span data-ttu-id="ace15-211">資訊</span><span class="sxs-lookup"><span data-stu-id="ace15-211">Info</span></span>|<span data-ttu-id="ace15-212">資源管理員 GUID (從基底)</span><span class="sxs-lookup"><span data-stu-id="ace15-212">Resource Manager GUID (from base)</span></span>|  
|<span data-ttu-id="ace15-213">TransactionSerialized</span><span class="sxs-lookup"><span data-stu-id="ace15-213">TransactionSerialized</span></span>|<span data-ttu-id="ace15-214">資訊</span><span class="sxs-lookup"><span data-stu-id="ace15-214">Info</span></span>|<span data-ttu-id="ace15-215">TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="ace15-215">TransactionTraceId.</span></span>|  
|<span data-ttu-id="ace15-216">TransactionException</span><span class="sxs-lookup"><span data-stu-id="ace15-216">TransactionException</span></span>|<span data-ttu-id="ace15-217">錯誤</span><span class="sxs-lookup"><span data-stu-id="ace15-217">Error</span></span>|<span data-ttu-id="ace15-218">例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="ace15-218">Exception message</span></span>|  
|<span data-ttu-id="ace15-219">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="ace15-219">InvalidOperationException</span></span>|<span data-ttu-id="ace15-220">錯誤</span><span class="sxs-lookup"><span data-stu-id="ace15-220">Error</span></span>|<span data-ttu-id="ace15-221">例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="ace15-221">Exception message</span></span>|  
|<span data-ttu-id="ace15-222">InternalError</span><span class="sxs-lookup"><span data-stu-id="ace15-222">InternalError</span></span>|<span data-ttu-id="ace15-223">重大</span><span class="sxs-lookup"><span data-stu-id="ace15-223">Critical</span></span>|<span data-ttu-id="ace15-224">例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="ace15-224">Exception message</span></span>|  
|<span data-ttu-id="ace15-225">TransferEvent</span><span class="sxs-lookup"><span data-stu-id="ace15-225">TransferEvent</span></span>||<span data-ttu-id="ace15-226">當交易已還原序列化，或是由 <xref:System.Transactions> 交易提升為分散式交易，則會寫入來自 ExecutionContext 與分散式交易識別碼的目前 ActivityID。</span><span class="sxs-lookup"><span data-stu-id="ace15-226">When a transaction is deserialized, or promoted from a <xref:System.Transactions> transaction to a distributed one, the current ActivityID from the ExecutionContext and the distributed transaction ID are written.</span></span><br /><br /> <span data-ttu-id="ace15-227">當 DTC 回呼 Managed 程式碼，分散式交易識別碼就會針對回呼的持續時間設為 ExecutionContext 中的 ActivityID。</span><span class="sxs-lookup"><span data-stu-id="ace15-227">When the DTC calls back into managed code, the distributed transaction ID is set as the ActivityID in the ExecutionContext for the duration of the callback.</span></span>|  
|<span data-ttu-id="ace15-228">ConfiguredDefaultTimeoutAdjusted</span><span class="sxs-lookup"><span data-stu-id="ace15-228">ConfiguredDefaultTimeoutAdjusted</span></span>|<span data-ttu-id="ace15-229">警告</span><span class="sxs-lookup"><span data-stu-id="ace15-229">Warning</span></span>|<span data-ttu-id="ace15-230">無額外的資料</span><span class="sxs-lookup"><span data-stu-id="ace15-230">No extra data</span></span>|  
|<span data-ttu-id="ace15-231">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="ace15-231">TransactionTimeout</span></span>|<span data-ttu-id="ace15-232">警告</span><span class="sxs-lookup"><span data-stu-id="ace15-232">Warning</span></span>|<span data-ttu-id="ace15-233">目前逾時的交易 TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="ace15-233">The TransactionTraceId of the transaction being timed out.</span></span>|  
  
 <span data-ttu-id="ace15-234">每個前置額外資料項目的 XML 結構描述都具有下列格式。</span><span class="sxs-lookup"><span data-stu-id="ace15-234">The XML schema for each of the preceding extra data items has the following format.</span></span>  
  
### <a name="transactiontraceidentifier"></a><span data-ttu-id="ace15-235">TransactionTraceIdentifier</span><span class="sxs-lookup"><span data-stu-id="ace15-235">TransactionTraceIdentifier</span></span>  

 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `< CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `</TransactionTraceIdentifier>`  
  
### <a name="enlistmenttraceidentifier"></a><span data-ttu-id="ace15-236">EnlistmentTraceIdentifier</span><span class="sxs-lookup"><span data-stu-id="ace15-236">EnlistmentTraceIdentifier</span></span>  

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
  
### <a name="resource-manager-identifier"></a><span data-ttu-id="ace15-237">資源管理員識別項</span><span class="sxs-lookup"><span data-stu-id="ace15-237">Resource Manager Identifier</span></span>  

 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
## <a name="security-issues-for-tracing"></a><span data-ttu-id="ace15-238">追蹤安全性問題</span><span class="sxs-lookup"><span data-stu-id="ace15-238">Security Issues For Tracing</span></span>  

 <span data-ttu-id="ace15-239">當您以管理員身分開啟追蹤功能時，敏感性資訊可能會寫入預設可公開檢視的追蹤記錄中。</span><span class="sxs-lookup"><span data-stu-id="ace15-239">When you as an administrator turn on tracing, sensitive information might be written to a trace log that is publicly viewable by default.</span></span> <span data-ttu-id="ace15-240">為了緩和任何可能發生的安全性威脅，您應該考慮將追蹤記錄存放在由共用與檔案系統存取權限所控制的安全地點。</span><span class="sxs-lookup"><span data-stu-id="ace15-240">To mitigate any possible security threat, you should consider storing the trace log in a secure location controlled by share and file system access permissions.</span></span>
