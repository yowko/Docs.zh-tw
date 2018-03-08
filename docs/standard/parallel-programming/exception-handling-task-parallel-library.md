---
title: "例外狀況處理 (工作平行程式庫)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, exceptions
ms.assetid: beb51e50-9061-4d3d-908c-56a4f7c2e8c1
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 86b4d105b7d79abbd25b342774705866119ada68
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="exception-handling-task-parallel-library"></a>例外狀況處理 (工作平行程式庫)
由在工作中執行的使用者程式碼所擲回的未處理例外狀況，會傳播回到呼叫執行緒，本主題稍後所述的特定情況除外。 當您使用其中一個靜態或執行個體 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> 或 <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` 方法時會傳播例外狀況，您可以用 `try`/`catch` 陳述式包住呼叫來處理它們。 如果工作是已連結子工作的父代，或如果您在等候多個工作，就可能會擲回多個例外狀況。  
  
 若要將所有例外狀況傳播回呼叫執行緒，工作基礎結構會將它們包裝在 <xref:System.AggregateException> 執行個體中。 <xref:System.AggregateException> 例外狀況有 <xref:System.AggregateException.InnerExceptions%2A> 屬性，您可以列舉這個屬性來檢查所有擲回的原始例外狀況，並且個別處理 (或不處理) 每個例外狀況。 您也可以使用 <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> 方法處理原始的例外狀況。  
  
 即使只擲回一個例外狀況，它仍然會包裝在 <xref:System.AggregateException> 例外狀況裡，如下例所示。  
  
 [!code-csharp[TPL_Exceptions#21](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling21.cs#21)]
 [!code-vb[TPL_Exceptions#21](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling21.vb#21)]  
  
 只要攔截 <xref:System.AggregateException> 而且沒有觀察到任何內部的例外狀況，就可以避免未處理的例外狀況。 不過，建議您不要這麼做，因為它在非平行案例中類似於攔截基底 <xref:System.Exception> 類型。 攔截例外狀況卻不採取特定動作從它復原，可能會讓您的程式處於不確定狀態。  
  
 如果您不想要呼叫 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> 或 <!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait` 方法以等候工作完成，您也可以擷取來自工作之 <xref:System.AggregateException> 屬性的 <xref:System.Threading.Tasks.Task.Exception%2A> 例外狀況，如下例所示。 如需詳細資訊，請參閱本主題的 [使用 Task.Exception 屬性觀察例外狀況](#ExceptionProp) 一節。  
  
 [!code-csharp[TPL_Exceptions#29](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handling22.cs#29)]
 [!code-vb[TPL_Exceptions#29](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handling22.vb#29)]  
  
 如果您不需要等候工作傳播例外狀況，或存取其 <xref:System.Threading.Tasks.Task.Exception%2A> 屬性，當工作回收時就會根據 .NET 例外狀況原則提昇例外狀況。  
  
 當允許例外狀況反昇至聯結的執行緒時，工作可能就可以在引發例外狀況之後，繼續處理某些項目。  
  
> [!NOTE]
>  啟用 [Just My Code] 時，Visual Studio 在某些情況下會在擲回例外狀況的字行上中斷，並顯示錯誤訊息，指出「使用者程式碼未處理例外狀況」。 這個錯誤是良性的。 您可以按 F5 繼續，並查看下面範例中示範的例外狀況處理行為。 若要防止 Visual Studio 在遇到第一個錯誤時就中斷，只要取消核取 [工具]、[選項]、[偵錯]、[一般]  下的 [ **啟用 Just My Code**] 核取方塊即可。  
  
## <a name="attached-child-tasks-and-nested-aggregateexceptions"></a>已連結子工作和巢狀的 AggregateExceptions  
 如果工作有會擲回例外狀況的已連結子工作，該例外狀況就會先包裝在 <xref:System.AggregateException> 再傳播到父工作，這會先把此例外狀況包裝在它自己的 <xref:System.AggregateException> 再傳播回呼叫執行緒。 在這種情況下，在 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>、<!--zz <xref:System.Threading.Tasks.Task%601.Wait%2A?displayProperty=nameWithType>  --> `Wait`、<xref:System.Threading.Tasks.Task.WaitAny%2A> 或 <xref:System.Threading.Tasks.Task.WaitAll%2A> 方法攔截之 <xref:System.AggregateException> 例外狀況的 <xref:System.AggregateException.InnerExceptions%2A> 屬性會包含一個或多個 <xref:System.AggregateException> 執行個體，而不是包含造成錯誤的原始例外狀況。 為免逐一查看巢狀 <xref:System.AggregateException> 例外狀況，您可以使用 <xref:System.AggregateException.Flatten%2A> 方法移除所有的巢狀 <xref:System.AggregateException> 例外狀況，讓 <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> 屬性包含原始例外狀況。 下例中，巢狀 <xref:System.AggregateException> 執行個體被扁平化，並只在一個迴圈中處理。  
  
 [!code-csharp[TPL_Exceptions#22](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/flatten2.cs#22)]
 [!code-vb[TPL_Exceptions#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/flatten2.vb#22)]  
  
 您也可以使用 <xref:System.AggregateException.Flatten%2A?displayProperty=nameWithType> 方法，從被單一 <xref:System.AggregateException> 執行個體之多個工作擲回的多個 <xref:System.AggregateException> 執行個體中，重新擲回內部的例外狀況，如下例所示。  
  
 [!code-csharp[TPL_Exceptions#13](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions2.cs#13)]
 [!code-vb[TPL_Exceptions#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions2.vb#13)]  
  
## <a name="exceptions-from-detached-child-tasks"></a>來自中斷連結子工作的例外狀況  
 子工作預設的建立狀態為中斷連結。 從已中斷連結工作擲回的例外狀況，必須在緊鄰的父工作中處理或重新擲回；它們傳播回呼叫執行緒的方式，和已連結子工作傳播回的方式不一樣。 最上層的父代可以從中斷連結的子代手動重新擲回例外狀況，讓它包裝在 <xref:System.AggregateException> 中並傳播回呼叫執行緒。  
  
 [!code-csharp[TPL_Exceptions#23](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/detached21.cs#23)]
 [!code-vb[TPL_Exceptions#23](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/detached21.vb#23)]  
  
 即使您持續觀察子工作中的例外狀況，父工作也仍然必須觀察此例外狀況。  
  
## <a name="exceptions-that-indicate-cooperative-cancellation"></a>指出合作式取消的例外狀況  
 當工作中的使用者程式碼回應取消要求時，正確的程序會擲回 <xref:System.OperationCanceledException> 傳入已在其中通訊過要求的取消語彙基元。 在它嘗試傳播例外狀況之前，工作執行個體會比較例外狀況中的語彙基元和個體建立時傳來的語彙基元。 如果它們是相同的，工作會傳播包裝在 <xref:System.Threading.Tasks.TaskCanceledException> 中的 <xref:System.AggregateException>，而且在檢查內部例外狀況時可以看到它。 不過，如果呼叫執行緒並未等待工作，就不會傳播這個特定的例外狀況。 如需詳細資訊，請參閱 [Task Cancellation](../../../docs/standard/parallel-programming/task-cancellation.md)。  
  
 [!code-csharp[TPL_Exceptions#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#4)]
 [!code-vb[TPL_Exceptions#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/tpl_exceptions.vb#4)]  
  
## <a name="using-the-handle-method-to-filter-inner-exceptions"></a>使用控制方法篩選內部例外狀況  
 您可以使用 <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> 方法，不用任何進一步的邏輯，篩選出您可以視為「已處理」的例外狀況。 在提供給 <xref:System.AggregateException.Handle%28System.Func%7BSystem.Exception%2CSystem.Boolean%7D%29?displayProperty=nameWithType> 方法的使用者委派中，您可以檢查例外狀況類型、其 <xref:System.Exception.Message%2A> 屬性或任何其他相關資訊，讓您判斷其是否為良性。 在 <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> 方法傳回之後，任何讓委派傳回 `false` 的例外狀況都會立即在新的 <xref:System.AggregateException> 執行個體中重新擲回。  
  
 下例在功能上等同於本主題的第一個範例，這會檢查 <xref:System.AggregateException.InnerExceptions%2A?displayProperty=nameWithType> 集合中的每個例外狀況。  只不過，這個例外狀況處理常式會呼叫每個例外狀況的 <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> 方法物件，而且只重新擲回不是 `CustomException` 執行個體的例外狀況。  
  
 [!code-csharp[TPL_Exceptions#26](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/handlemethod21.cs#26)]
 [!code-vb[TPL_Exceptions#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/handlemethod21.vb#26)]  
  
 以下是更完整的範例，其使用 <xref:System.AggregateException.Handle%2A?displayProperty=nameWithType> 方法在列舉檔案時為 <xref:System.UnauthorizedAccessException> 例外狀況提供特殊處理。  
  
 [!code-csharp[TPL_Exceptions#12](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/taskexceptions.cs#12)]
 [!code-vb[TPL_Exceptions#12](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/taskexceptions.vb#12)]  
  
<a name="ExceptionProp"></a>   
## <a name="observing-exceptions-by-using-the-taskexception-property"></a>使用 Task.Exception 屬性觀察例外狀況  
 如果工作在 <xref:System.Threading.Tasks.TaskStatus.Faulted?displayProperty=nameWithType> 狀態中完成，可檢查其 <xref:System.Threading.Tasks.Task.Exception%2A> 屬性以探查哪些特定的例外狀況導致這個錯誤。 使用唯有在前項工作發生錯誤時才執行的接續，是觀察 <xref:System.Threading.Tasks.Task.Exception%2A> 屬性的好方法，如下例所示。  
  
 [!code-csharp[TPL_Exceptions#27](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptionprop21.cs#27)]
 [!code-vb[TPL_Exceptions#27](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionprop21.vb#27)]  
  
 在實際應用中，接續委派會記錄例外狀況的詳細資訊，並可能產生從例外狀況復原的新工作。  
  
## <a name="unobservedtaskexception-event"></a>UnobservedTaskException 事件  
 在某些情況下，例如裝載時不受信任的外掛程式，良性的例外狀況可能很常見，而要手動觀察全部太困難。 在這些情況下，您可以處理 <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=nameWithType> 事件。 傳遞至處理常式的 <xref:System.Threading.Tasks.UnobservedTaskExceptionEventArgs?displayProperty=nameWithType> 執行個體，可用來防止未觀察到的例外狀況傳播回聯結執行緒。  
  
## <a name="see-also"></a>請參閱  
 [工作平行程式庫 (TPL)](../../../docs/standard/parallel-programming/task-parallel-library-tpl.md)
