---
title: 診斷追蹤
ms.date: 03/30/2017
ms.assetid: 28e77a63-d20d-4b6a-9caf-ddad86550427
ms.openlocfilehash: 76712710bf42f498ba859c7b1cd18a261387078c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174416"
---
# <a name="diagnostic-traces"></a><span data-ttu-id="2b9b1-102">診斷追蹤</span><span class="sxs-lookup"><span data-stu-id="2b9b1-102">Diagnostic Traces</span></span>
<span data-ttu-id="2b9b1-103">追蹤就是在應用程式執行期間，所產生的特定訊息之發行動作。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-103">Traces are the publishing of specific messages that are generated during application execution.</span></span> <span data-ttu-id="2b9b1-104">使用追蹤功能時，您必須具有收集和記錄所傳送訊息的機制。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-104">When using tracing, you must have a mechanism for collecting and recording the messages that are sent.</span></span> <span data-ttu-id="2b9b1-105">追蹤訊息由「接聽項」負責接收。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-105">Trace messages are received by listeners.</span></span> <span data-ttu-id="2b9b1-106">接聽項的用途是收集、儲存和傳送追蹤訊息。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-106">The purpose of a listener is to collect, store, and route tracing messages.</span></span> <span data-ttu-id="2b9b1-107">接聽項會將追蹤輸出導向至適當的目標，例如記錄檔、視窗或文字檔。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-107">Listeners direct the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
 <span data-ttu-id="2b9b1-108">這類的接聽項，例如 <xref:System.Diagnostics.DefaultTraceListener>，會在啟用追蹤時自訂建立與初始。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-108">One such listener, the <xref:System.Diagnostics.DefaultTraceListener>, is automatically created and initialized when tracing is enabled.</span></span> <span data-ttu-id="2b9b1-109">如果您要將追蹤輸出傳送至任何其他來源，您必須建立和初始化其他的追蹤接聽項。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-109">If you want trace output to be directed to any additional sources, you must create and initialize additional trace listeners.</span></span> <span data-ttu-id="2b9b1-110">您建立的接聽項應反映出您個人的需求。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-110">The listeners you create should reflect your individual needs.</span></span> <span data-ttu-id="2b9b1-111">例如，您可能想要所有追蹤輸出的文字記錄。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-111">For example, you might want a text record of all trace output.</span></span> <span data-ttu-id="2b9b1-112">在這種情況中，您建立的接聽項要在啟用時，將所有的輸出寫入新的文字檔。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-112">In this case, you would create a listener that wrote all output to a new text file when enabled.</span></span> <span data-ttu-id="2b9b1-113">另一方面，您可能只想在應用程式執行期間檢視輸出。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-113">On the other hand, you might only want to view output during application execution.</span></span> <span data-ttu-id="2b9b1-114">在這種情況中，您可建立導向所有輸出至主控台視窗的接聽項。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-114">In that case, you might create a listener that directed all output to a console window.</span></span> <span data-ttu-id="2b9b1-115"><xref:System.Diagnostics.EventLogTraceListener> 可以導向追蹤輸出至事件記錄檔，而 <xref:System.Diagnostics.TextWriterTraceListener> 可將追蹤輸出寫入資料流。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-115">The <xref:System.Diagnostics.EventLogTraceListener> can direct trace output to an event log, and the <xref:System.Diagnostics.TextWriterTraceListener> can write trace output to a stream.</span></span>  
  
## <a name="enabling-tracing"></a><span data-ttu-id="2b9b1-116">啟用追蹤</span><span class="sxs-lookup"><span data-stu-id="2b9b1-116">Enabling Tracing</span></span>  
 <span data-ttu-id="2b9b1-117">若要在交易處理期間啟用追蹤，您應該編輯應用程式的組態檔。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-117">To enable traces during transaction processing, you should edit your application’s configuration file.</span></span> <span data-ttu-id="2b9b1-118">以下是一個範例。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-118">The following is an example.</span></span>  
  
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
  
 <span data-ttu-id="2b9b1-119"><xref:System.Transactions> 追蹤會寫入名為 "System.Transactions" 的來源中。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-119"><xref:System.Transactions> traces are written to the source named "System.Transactions".</span></span> <span data-ttu-id="2b9b1-120">您可以使用 `add` 來指定要使用的追蹤接聽項名稱與型別。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-120">You can use `add` to specify the name and type of the trace listener you want to use.</span></span> <span data-ttu-id="2b9b1-121">在我們的組態範例中，我們將接聽項命名為 "tx" 並將標準 .NET Framework 追蹤接聽項 (<xref:System.Diagnostics.XmlWriterTraceListener>) 當成要使用的型別加入。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-121">In our example configuration, we named the Listener "tx" and added the standard .NET Framework trace listener (<xref:System.Diagnostics.XmlWriterTraceListener>) as the type we want to use.</span></span> <span data-ttu-id="2b9b1-122">請使用 `initializeData` 來設定該接聽項的記錄檔名稱。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-122">Use `initializeData` to set the name of the log file for that listener.</span></span> <span data-ttu-id="2b9b1-123">此外，您可以使用完整路徑來取代簡單檔名。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-123">In addition, you can substitute a fully qualified path for a simple file name.</span></span>  
  
 <span data-ttu-id="2b9b1-124">每個追蹤訊息類型都會指派一個層級來代表自己的重要程度。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-124">Each trace message type is assigned a level to indicate its degree of importance.</span></span> <span data-ttu-id="2b9b1-125">如果應用程式定義域的追蹤層級等於或小於事件型別的層級，則會產生該訊息。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-125">If the app-domain’s trace level is equal or lower than the level of an event type, then that message is generated.</span></span> <span data-ttu-id="2b9b1-126">追蹤層級可由組態檔中的 `switchValue` 設定來控制。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-126">The tracing level is controlled by the `switchValue` setting in the configuration file.</span></span> <span data-ttu-id="2b9b1-127">下表定義了與診斷追蹤訊息相關聯的層級。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-127">The levels that are associated with diagnostic trace messages are defined in the following table.</span></span>  
  
|<span data-ttu-id="2b9b1-128">追蹤層級</span><span class="sxs-lookup"><span data-stu-id="2b9b1-128">Trace Level</span></span>|<span data-ttu-id="2b9b1-129">描述</span><span class="sxs-lookup"><span data-stu-id="2b9b1-129">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="2b9b1-130">重大</span><span class="sxs-lookup"><span data-stu-id="2b9b1-130">Critical</span></span>|<span data-ttu-id="2b9b1-131">已發生如下列所述的嚴重失敗情況：</span><span class="sxs-lookup"><span data-stu-id="2b9b1-131">Serious failures, such as the following, have occurred:</span></span><br /><br /> <span data-ttu-id="2b9b1-132">- 可能導致使用者功能立即丟失的錯誤。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-132">-   An error that can cause an immediate loss in user functionality.</span></span><br /><span data-ttu-id="2b9b1-133">- 需要管理員採取措施以避免功能遺失的事件。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-133">-   An event that requires an administrator to take action to avoid loss of functionality.</span></span><br /><span data-ttu-id="2b9b1-134">- 代碼掛起。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-134">-   Code hangs.</span></span><br /><span data-ttu-id="2b9b1-135">- 此跟蹤級別還可以為解釋其他關鍵跟蹤提供足夠的上下文。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-135">-   This tracing level can also provide sufficient context for interpreting other critical traces.</span></span> <span data-ttu-id="2b9b1-136">如此便可協助找出導致嚴重失敗的作業序列。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-136">This can help to identify the sequence of operations leading to a serious failure.</span></span>|  
|<span data-ttu-id="2b9b1-137">錯誤</span><span class="sxs-lookup"><span data-stu-id="2b9b1-137">Error</span></span>|<span data-ttu-id="2b9b1-138">已經發生可導致使用者功能喪失的錯誤 (例如，無效的組態或網路行為)。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-138">An error (for example, invalid configuration or network behavior) has occurred that can result in a loss of user functionality.</span></span>|  
|<span data-ttu-id="2b9b1-139">警告</span><span class="sxs-lookup"><span data-stu-id="2b9b1-139">Warning</span></span>|<span data-ttu-id="2b9b1-140">存在一個可間接導致錯誤或嚴重失敗的狀況 (例如，配置失敗或到達上限)。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-140">A condition exists that can subsequently result in an error or critical failure (for example, allocation failing or approaching a limit).</span></span> <span data-ttu-id="2b9b1-141">對使用者程式碼錯誤的正常處理 (例如，交易中止、逾時、驗證失敗) 也可能產生警告。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-141">Normal processing of errors from user code (for example, transaction aborted, timeouts, authentication failed) can also generate a warning.</span></span>|  
|<span data-ttu-id="2b9b1-142">資訊</span><span class="sxs-lookup"><span data-stu-id="2b9b1-142">Information</span></span>|<span data-ttu-id="2b9b1-143">會產生對監控與診斷系統狀態、衡量效能，或描述分析有幫助的訊息。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-143">Messages helpful for monitoring and diagnosing system status, measuring performance, or profiling are generated.</span></span> <span data-ttu-id="2b9b1-144">這些訊息包含交易與登記存留期事件，例如正在建立或認可的交易、重要界限的跨越，或是重要資源的配置。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-144">These can include transaction and enlistment lifetime events, such as a transaction being created or committed, the crossing of a significant boundary, or the allocation of significant resources.</span></span> <span data-ttu-id="2b9b1-145">這時開發人員可以使用此類資訊來進行容量規劃與效能管理。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-145">A developer can then utilize such information for capacity planning and performance management.</span></span>|  
  
## <a name="trace-codes"></a><span data-ttu-id="2b9b1-146">追蹤程式碼</span><span class="sxs-lookup"><span data-stu-id="2b9b1-146">Trace Codes</span></span>  
 <span data-ttu-id="2b9b1-147">下表列出由 <xref:System.Transactions> 基礎結構所產生的追蹤程式碼。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-147">The following table lists the trace codes that are generated by the <xref:System.Transactions> infrastructure.</span></span> <span data-ttu-id="2b9b1-148">表中包括跟蹤代碼識別碼、跟蹤的枚<xref:System.Diagnostics.EventTypeFilter.EventType%2A>舉級別以及跟蹤的**TraceRecord**中包含的額外資料。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-148">Included in the table are the trace code identifier, the <xref:System.Diagnostics.EventTypeFilter.EventType%2A> enumeration level for the trace, and the extra data contained in the **TraceRecord** for the trace.</span></span> <span data-ttu-id="2b9b1-149">此外，跟蹤的相應跟蹤級別也存儲在**追蹤記錄中**。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-149">In addition, the corresponding trace level of the trace is also stored in the **TraceRecord**.</span></span>  
  
|<span data-ttu-id="2b9b1-150">TraceCode</span><span class="sxs-lookup"><span data-stu-id="2b9b1-150">TraceCode</span></span>|<span data-ttu-id="2b9b1-151">EventType</span><span class="sxs-lookup"><span data-stu-id="2b9b1-151">EventType</span></span>|<span data-ttu-id="2b9b1-152">TraceRecord 中的額外資料</span><span class="sxs-lookup"><span data-stu-id="2b9b1-152">Extra data in TraceRecord</span></span>|  
|---------------|---------------|-------------------------------|  
|<span data-ttu-id="2b9b1-153">TransactionCreated</span><span class="sxs-lookup"><span data-stu-id="2b9b1-153">TransactionCreated</span></span>|<span data-ttu-id="2b9b1-154">資訊</span><span class="sxs-lookup"><span data-stu-id="2b9b1-154">Info</span></span>|<span data-ttu-id="2b9b1-155">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="2b9b1-155">TransactionTraceId</span></span>|  
|<span data-ttu-id="2b9b1-156">TransactionPromoted</span><span class="sxs-lookup"><span data-stu-id="2b9b1-156">TransactionPromoted</span></span>|<span data-ttu-id="2b9b1-157">資訊</span><span class="sxs-lookup"><span data-stu-id="2b9b1-157">Info</span></span>|<span data-ttu-id="2b9b1-158">本機 TransactionTraceId、Distributed TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="2b9b1-158">Local TransactionTraceId, Distributed TransactionTraceId</span></span>|  
|<span data-ttu-id="2b9b1-159">EnlistmentCreated</span><span class="sxs-lookup"><span data-stu-id="2b9b1-159">EnlistmentCreated</span></span>|<span data-ttu-id="2b9b1-160">資訊</span><span class="sxs-lookup"><span data-stu-id="2b9b1-160">Info</span></span>|<span data-ttu-id="2b9b1-161">TransactionTraceId、EnlistmentTraceId、EnlistmentType (永久性/變動性)、EnlistmentOptions</span><span class="sxs-lookup"><span data-stu-id="2b9b1-161">TransactionTraceId, EnlistmentTraceId, EnlistmentType (durable/volatile), EnlistmentOptions</span></span>|  
|<span data-ttu-id="2b9b1-162">EnlistmentCallbackNegative</span><span class="sxs-lookup"><span data-stu-id="2b9b1-162">EnlistmentCallbackNegative</span></span>|<span data-ttu-id="2b9b1-163">警告</span><span class="sxs-lookup"><span data-stu-id="2b9b1-163">Warning</span></span>|<span data-ttu-id="2b9b1-164">TransactionTraceId、EnlistmentTraceId、</span><span class="sxs-lookup"><span data-stu-id="2b9b1-164">TransactionTraceId, EnlistmentTraceId,</span></span><br /><br /> <span data-ttu-id="2b9b1-165">回呼 (forcerollback/中止/indoubt)</span><span class="sxs-lookup"><span data-stu-id="2b9b1-165">Callback (forcerollback/aborted/indoubt)</span></span>|  
|<span data-ttu-id="2b9b1-166">TransactionRollbackCalled</span><span class="sxs-lookup"><span data-stu-id="2b9b1-166">TransactionRollbackCalled</span></span>|<span data-ttu-id="2b9b1-167">警告</span><span class="sxs-lookup"><span data-stu-id="2b9b1-167">Warning</span></span>|<span data-ttu-id="2b9b1-168">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="2b9b1-168">TransactionTraceId</span></span>|  
|<span data-ttu-id="2b9b1-169">TransactionAborted</span><span class="sxs-lookup"><span data-stu-id="2b9b1-169">TransactionAborted</span></span>|<span data-ttu-id="2b9b1-170">警告</span><span class="sxs-lookup"><span data-stu-id="2b9b1-170">Warning</span></span>|<span data-ttu-id="2b9b1-171">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="2b9b1-171">TransactionTraceId</span></span>|  
|<span data-ttu-id="2b9b1-172">TransactionInDoubt</span><span class="sxs-lookup"><span data-stu-id="2b9b1-172">TransactionInDoubt</span></span>|<span data-ttu-id="2b9b1-173">警告</span><span class="sxs-lookup"><span data-stu-id="2b9b1-173">Warning</span></span>|<span data-ttu-id="2b9b1-174">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="2b9b1-174">TransactionTraceId</span></span>|  
|<span data-ttu-id="2b9b1-175">TransactionScopeCreated</span><span class="sxs-lookup"><span data-stu-id="2b9b1-175">TransactionScopeCreated</span></span>|<span data-ttu-id="2b9b1-176">資訊</span><span class="sxs-lookup"><span data-stu-id="2b9b1-176">Info</span></span>|<span data-ttu-id="2b9b1-177">TransactionScopeResult，可能為下列各項：</span><span class="sxs-lookup"><span data-stu-id="2b9b1-177">TransactionScopeResult, which can be the following:</span></span><br /><br /> <span data-ttu-id="2b9b1-178">- 新交易</span><span class="sxs-lookup"><span data-stu-id="2b9b1-178">-   New transaction.</span></span><br /><span data-ttu-id="2b9b1-179">- 交易通過。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-179">-   Transaction passed.</span></span><br /><span data-ttu-id="2b9b1-180">- 已傳遞從屬事務。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-180">-   Dependent transaction passed.</span></span><br /><span data-ttu-id="2b9b1-181">- 使用當前事務。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-181">-   Using current transaction.</span></span><br /><span data-ttu-id="2b9b1-182">-沒有交易</span><span class="sxs-lookup"><span data-stu-id="2b9b1-182">-   No transaction.</span></span><br /><br /> <span data-ttu-id="2b9b1-183">目前新 TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="2b9b1-183">new current TransactionTraceId</span></span>|  
|<span data-ttu-id="2b9b1-184">TransactionScopeDisposed</span><span class="sxs-lookup"><span data-stu-id="2b9b1-184">TransactionScopeDisposed</span></span>|<span data-ttu-id="2b9b1-185">資訊</span><span class="sxs-lookup"><span data-stu-id="2b9b1-185">Info</span></span>|<span data-ttu-id="2b9b1-186">作用域的"預期"當前事務的事務跟蹤Id。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-186">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="2b9b1-187">TransactionScopeIncomplete</span><span class="sxs-lookup"><span data-stu-id="2b9b1-187">TransactionScopeIncomplete</span></span>|<span data-ttu-id="2b9b1-188">警告</span><span class="sxs-lookup"><span data-stu-id="2b9b1-188">Warning</span></span>|<span data-ttu-id="2b9b1-189">作用域的"預期"當前事務的事務跟蹤Id。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-189">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="2b9b1-190">TransactionScopeNestedIncorrectly</span><span class="sxs-lookup"><span data-stu-id="2b9b1-190">TransactionScopeNestedIncorrectly</span></span>|<span data-ttu-id="2b9b1-191">警告</span><span class="sxs-lookup"><span data-stu-id="2b9b1-191">Warning</span></span>|<span data-ttu-id="2b9b1-192">作用域的"預期"當前事務的事務跟蹤Id。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-192">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="2b9b1-193">TransactionScopeCurrentTransactionChanged</span><span class="sxs-lookup"><span data-stu-id="2b9b1-193">TransactionScopeCurrentTransactionChanged</span></span>|<span data-ttu-id="2b9b1-194">警告</span><span class="sxs-lookup"><span data-stu-id="2b9b1-194">Warning</span></span>|<span data-ttu-id="2b9b1-195">目前舊有 TransactionTraceId、其他 TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="2b9b1-195">Old current TransactionTraceId, other TransactionTraceId</span></span>|  
|<span data-ttu-id="2b9b1-196">TransactionScopeTimeout</span><span class="sxs-lookup"><span data-stu-id="2b9b1-196">TransactionScopeTimeout</span></span>|<span data-ttu-id="2b9b1-197">警告</span><span class="sxs-lookup"><span data-stu-id="2b9b1-197">Warning</span></span>|<span data-ttu-id="2b9b1-198">作用域的"預期"當前事務的事務跟蹤Id。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-198">TransactionTraceId of the scope’s "expected" current transaction.</span></span>|  
|<span data-ttu-id="2b9b1-199">DependentCloneCreated</span><span class="sxs-lookup"><span data-stu-id="2b9b1-199">DependentCloneCreated</span></span>|<span data-ttu-id="2b9b1-200">資訊</span><span class="sxs-lookup"><span data-stu-id="2b9b1-200">Info</span></span>|<span data-ttu-id="2b9b1-201">TransactionTraceId、所建立的相依交易型別 (RollbackIfNotComplete/BlockCommitUntilComplete)</span><span class="sxs-lookup"><span data-stu-id="2b9b1-201">TransactionTraceId, type of dependent transaction created (RollbackIfNotComplete/BlockCommitUntilComplete)</span></span>|  
|<span data-ttu-id="2b9b1-202">DependentCloneComplete</span><span class="sxs-lookup"><span data-stu-id="2b9b1-202">DependentCloneComplete</span></span>|<span data-ttu-id="2b9b1-203">資訊</span><span class="sxs-lookup"><span data-stu-id="2b9b1-203">Info</span></span>|<span data-ttu-id="2b9b1-204">TransactionTraceId</span><span class="sxs-lookup"><span data-stu-id="2b9b1-204">TransactionTraceId</span></span>|  
|<span data-ttu-id="2b9b1-205">RecoveryComplete</span><span class="sxs-lookup"><span data-stu-id="2b9b1-205">RecoveryComplete</span></span>|<span data-ttu-id="2b9b1-206">資訊</span><span class="sxs-lookup"><span data-stu-id="2b9b1-206">Info</span></span>|<span data-ttu-id="2b9b1-207">資源管理員 GUID (從基底)</span><span class="sxs-lookup"><span data-stu-id="2b9b1-207">Resource Manager GUID (from base)</span></span>|  
|<span data-ttu-id="2b9b1-208">Reenlist</span><span class="sxs-lookup"><span data-stu-id="2b9b1-208">Reenlist</span></span>|<span data-ttu-id="2b9b1-209">資訊</span><span class="sxs-lookup"><span data-stu-id="2b9b1-209">Info</span></span>|<span data-ttu-id="2b9b1-210">資源管理員 GUID (從基底)</span><span class="sxs-lookup"><span data-stu-id="2b9b1-210">Resource Manager GUID (from base)</span></span>|  
|<span data-ttu-id="2b9b1-211">TransactionSerialized</span><span class="sxs-lookup"><span data-stu-id="2b9b1-211">TransactionSerialized</span></span>|<span data-ttu-id="2b9b1-212">資訊</span><span class="sxs-lookup"><span data-stu-id="2b9b1-212">Info</span></span>|<span data-ttu-id="2b9b1-213">TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-213">TransactionTraceId.</span></span>|  
|<span data-ttu-id="2b9b1-214">TransactionException</span><span class="sxs-lookup"><span data-stu-id="2b9b1-214">TransactionException</span></span>|<span data-ttu-id="2b9b1-215">錯誤</span><span class="sxs-lookup"><span data-stu-id="2b9b1-215">Error</span></span>|<span data-ttu-id="2b9b1-216">例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="2b9b1-216">Exception message</span></span>|  
|<span data-ttu-id="2b9b1-217">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="2b9b1-217">InvalidOperationException</span></span>|<span data-ttu-id="2b9b1-218">錯誤</span><span class="sxs-lookup"><span data-stu-id="2b9b1-218">Error</span></span>|<span data-ttu-id="2b9b1-219">例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="2b9b1-219">Exception message</span></span>|  
|<span data-ttu-id="2b9b1-220">InternalError</span><span class="sxs-lookup"><span data-stu-id="2b9b1-220">InternalError</span></span>|<span data-ttu-id="2b9b1-221">重大</span><span class="sxs-lookup"><span data-stu-id="2b9b1-221">Critical</span></span>|<span data-ttu-id="2b9b1-222">例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="2b9b1-222">Exception message</span></span>|  
|<span data-ttu-id="2b9b1-223">TransferEvent</span><span class="sxs-lookup"><span data-stu-id="2b9b1-223">TransferEvent</span></span>||<span data-ttu-id="2b9b1-224">當交易已還原序列化，或是由 <xref:System.Transactions> 交易提升為分散式交易，則會寫入來自 ExecutionContext 與分散式交易識別碼的目前 ActivityID。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-224">When a transaction is deserialized, or promoted from a <xref:System.Transactions> transaction to a distributed one, the current ActivityID from the ExecutionContext and the distributed transaction ID are written.</span></span><br /><br /> <span data-ttu-id="2b9b1-225">當 DTC 回呼 Managed 程式碼，分散式交易識別碼就會針對回呼的持續時間設為 ExecutionContext 中的 ActivityID。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-225">When the DTC calls back into managed code, the distributed transaction ID is set as the ActivityID in the ExecutionContext for the duration of the callback.</span></span>|  
|<span data-ttu-id="2b9b1-226">ConfiguredDefaultTimeoutAdjusted</span><span class="sxs-lookup"><span data-stu-id="2b9b1-226">ConfiguredDefaultTimeoutAdjusted</span></span>|<span data-ttu-id="2b9b1-227">警告</span><span class="sxs-lookup"><span data-stu-id="2b9b1-227">Warning</span></span>|<span data-ttu-id="2b9b1-228">無額外的資料</span><span class="sxs-lookup"><span data-stu-id="2b9b1-228">No extra data</span></span>|  
|<span data-ttu-id="2b9b1-229">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="2b9b1-229">TransactionTimeout</span></span>|<span data-ttu-id="2b9b1-230">警告</span><span class="sxs-lookup"><span data-stu-id="2b9b1-230">Warning</span></span>|<span data-ttu-id="2b9b1-231">目前逾時的交易 TransactionTraceId。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-231">The TransactionTraceId of the transaction being timed out.</span></span>|  
  
 <span data-ttu-id="2b9b1-232">每個前置額外資料項目的 XML 結構描述都具有下列格式。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-232">The XML schema for each of the preceding extra data items has the following format.</span></span>  
  
### <a name="transactiontraceidentifier"></a><span data-ttu-id="2b9b1-233">TransactionTraceIdentifier</span><span class="sxs-lookup"><span data-stu-id="2b9b1-233">TransactionTraceIdentifier</span></span>  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `< CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `</TransactionTraceIdentifier>`  
  
### <a name="enlistmenttraceidentifier"></a><span data-ttu-id="2b9b1-234">EnlistmentTraceIdentifier</span><span class="sxs-lookup"><span data-stu-id="2b9b1-234">EnlistmentTraceIdentifier</span></span>  
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
  
### <a name="resource-manager-identifier"></a><span data-ttu-id="2b9b1-235">資源管理員識別項</span><span class="sxs-lookup"><span data-stu-id="2b9b1-235">Resource Manager Identifier</span></span>  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
## <a name="security-issues-for-tracing"></a><span data-ttu-id="2b9b1-236">追蹤安全性問題</span><span class="sxs-lookup"><span data-stu-id="2b9b1-236">Security Issues For Tracing</span></span>  
 <span data-ttu-id="2b9b1-237">當您以管理員身分開啟追蹤功能時，敏感性資訊可能會寫入預設可公開檢視的追蹤記錄中。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-237">When you as an administrator turn on tracing, sensitive information might be written to a trace log that is publicly viewable by default.</span></span> <span data-ttu-id="2b9b1-238">為了緩和任何可能發生的安全性威脅，您應該考慮將追蹤記錄存放在由共用與檔案系統存取權限所控制的安全地點。</span><span class="sxs-lookup"><span data-stu-id="2b9b1-238">To mitigate any possible security threat, you should consider storing the trace log in a secure location controlled by share and file system access permissions.</span></span>
