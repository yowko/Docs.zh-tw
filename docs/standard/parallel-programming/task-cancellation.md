---
title: 工作取消
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, cancellation
- asynchronous task cancellation
ms.assetid: 3ecf1ea9-e399-4a6a-a0d6-8475f48dcb28
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7fefbfd33788ea84a8daf9dfbab452802ffd50d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650746"
---
# <a name="task-cancellation"></a>工作取消
<xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 和 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> 類別可使用 .NET Framework 中的取消語彙基元來支援取消作業。 如需詳細資訊，請參閱[受控執行緒中的取消作業](../../../docs/standard/threading/cancellation-in-managed-threads.md)。 在 Task 類別中，取消作業包括使用者委派之間的合作，這是指可取消的作業和要求取消的程式碼。  成功的取消包括要求呼叫 <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=nameWithType> 方法的程式碼，以及適時終止作業的使用者委派。 您可以使用下列選項之一來終止作業：  
  
- 藉由直接從委派傳回。 在許多情況下使用這個選項即已足夠，但以這種方式取消的工作執行個體將會轉換至 <xref:System.Threading.Tasks.TaskStatus.RanToCompletion?displayProperty=nameWithType> 狀態，而非 <xref:System.Threading.Tasks.TaskStatus.Canceled?displayProperty=nameWithType> 狀態。  
  
- 擲回 <xref:System.OperationCanceledException> ，並將其傳遞至據以要求取消的語彙基元。 執行此作業的常見方式是使用 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> 方法。 以此方式取消的工作會切換至 Canceled 狀態，可供呼叫端節點用以驗證工作已回應其取消要求。  
  
 下列範例說明會擲回例外狀況的工作取消基本模式。 請注意，語彙基元不但會傳遞至使用者委派，也會傳遞至工作執行個體本身。  
  
 [!code-csharp[TPL_Cancellation#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/snippet02.cs#02)]
 [!code-vb[TPL_Cancellation#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/module1.vb#02)]  
  
 如需更完整的範例，請參閱[如何：取消工作及其子系](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)。  
  
 工作執行個體在觀察到由使用者程式碼擲回的 <xref:System.OperationCanceledException> 時，會比較此例外狀況的語彙基元及與它自己相關聯的語彙基元 (即傳遞給建立工作之 API 的語彙基元)。 如果兩者相同，且此語彙基元的 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 屬性傳回 true，則工作會將此解譯成確認取消，並轉換至 Canceled 狀態。 如果未使用 <xref:System.Threading.Tasks.Task.Wait%2A> 或 <xref:System.Threading.Tasks.Task.WaitAll%2A> 方法等候工作，則工作只會將其狀態設為 <xref:System.Threading.Tasks.TaskStatus.Canceled>。  
  
 如果您正在等候轉換至 Canceled 狀態的工作，則會擲回 <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> 例外狀況 (包含在 <xref:System.AggregateException> 例外狀況中)。 請注意，此例外狀況表示取消成功，而非錯誤情況。 因此，工作的 <xref:System.Threading.Tasks.Task.Exception%2A> 屬性會傳回 `null`。  
  
 如果語彙基元的 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 屬性傳回 false，或例外狀況的語彙基元不符合工作的語彙基元，則 <xref:System.OperationCanceledException> 會被視為一般例外狀況，而使工作轉換至 Faulted 狀態。 同時也請注意，如有其他例外狀況存在，也會使工作轉換至 Faulted 狀態。 您可以在 <xref:System.Threading.Tasks.Task.Status%2A> 屬性中取得已完成工作的狀態。  
  
 不過，在要求取消之後，工作仍有可能會繼續處理某些項目。  
  
## <a name="see-also"></a>另請參閱

- [Managed 執行緒中的取消作業](../../../docs/standard/threading/cancellation-in-managed-threads.md)
- [如何：取消工作及其子系](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
