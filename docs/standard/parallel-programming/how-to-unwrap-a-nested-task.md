---
title: HOW TO：解除包裝巢狀工作
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to unwrap nested tasks
ms.assetid: a0769dd2-0f6d-48ca-8418-a9d39de7f450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cc468da70d3c62c139a98a6637e7a3c7990c378
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602048"
---
# <a name="how-to-unwrap-a-nested-task"></a><span data-ttu-id="e1f15-102">HOW TO：解除包裝巢狀工作</span><span class="sxs-lookup"><span data-stu-id="e1f15-102">How to: Unwrap a Nested Task</span></span>
<span data-ttu-id="e1f15-103">您可以從方法傳回工作，接著等待或繼續該工作，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e1f15-103">You can return a task from a method, and then wait on or continue from that task, as shown in the following example:</span></span>  
  
 [!code-csharp[TPL_Unwrap#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#01)]
 [!code-vb[TPL_Unwrap#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#01)]  
  
 <span data-ttu-id="e1f15-104">在上述範例中，<xref:System.Threading.Tasks.Task%601.Result%2A> 屬性是 `string` 類型 (Visual Basic 中為 `String`)。</span><span class="sxs-lookup"><span data-stu-id="e1f15-104">In the previous example, the <xref:System.Threading.Tasks.Task%601.Result%2A> property is of type `string` (`String` in Visual Basic).</span></span>  
  
 <span data-ttu-id="e1f15-105">不過，在某些情況下，您可能想要在另一個工作內建立工作，然後傳回巢狀的工作。</span><span class="sxs-lookup"><span data-stu-id="e1f15-105">However, in some scenarios, you might want to create a task within another task, and then return the nested task.</span></span> <span data-ttu-id="e1f15-106">在此情況下，封閉式工作的 `TResult` 本身就是工作。</span><span class="sxs-lookup"><span data-stu-id="e1f15-106">In this case, the `TResult` of the enclosing task is itself a task.</span></span> <span data-ttu-id="e1f15-107">在下列範例中，Result 屬性在 C# 中為 `Task<Task<string>>`，在 Visual Basic 中則為 `Task(Of Task(Of String))`。</span><span class="sxs-lookup"><span data-stu-id="e1f15-107">In the following example, the Result property is a `Task<Task<string>>` in C# or `Task(Of Task(Of String))` in Visual Basic.</span></span>  
  
 [!code-csharp[TPL_Unwrap#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#02)]
 [!code-vb[TPL_Unwrap#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#02)]  
  
 <span data-ttu-id="e1f15-108">雖然可以撰寫程式碼來解除包裝外部工作並擷取原始工作及其 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性，但這類程式碼不容易編寫，因為您必須處理例外狀況及取消要求。</span><span class="sxs-lookup"><span data-stu-id="e1f15-108">Although it is possible to write code to unwrap the outer task and retrieve the original task and its <xref:System.Threading.Tasks.Task%601.Result%2A> property, such code is not easy to write because you must handle exceptions and also cancellation requests.</span></span> <span data-ttu-id="e1f15-109">在此情況下，建議您使用其中一個 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 擴充方法，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="e1f15-109">In this situation, we recommend that you use one of the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods, as shown in the following example.</span></span>  
  
 [!code-csharp[TPL_UnWrap#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#03)]
 [!code-vb[TPL_UnWrap#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippets1-3.vb#03)]  
  
 <span data-ttu-id="e1f15-110">使用 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 方法可以將任何 `Task<Task>` 或 `Task<Task<TResult>>` (Visual Basic 中為 `Task(Of Task)` 或 `Task(Of Task(Of TResult))`) 轉換為 `Task` 或 `Task<TResult>` (Visual Basic 中為 `Task(Of TResult)`)。</span><span class="sxs-lookup"><span data-stu-id="e1f15-110">The <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> methods can be used to transform any `Task<Task>` or `Task<Task<TResult>>` (`Task(Of Task)` or `Task(Of Task(Of TResult))` in Visual Basic) to a `Task` or `Task<TResult>` (`Task(Of TResult)` in Visual Basic).</span></span> <span data-ttu-id="e1f15-111">新的工作完全代表內部巢狀工作，並包含取消狀態及所有例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e1f15-111">The new task fully represents the inner nested task, and includes cancellation state and all exceptions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1f15-112">範例</span><span class="sxs-lookup"><span data-stu-id="e1f15-112">Example</span></span>  
 <span data-ttu-id="e1f15-113">下列範例示範如何使用 <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> 擴充方法。</span><span class="sxs-lookup"><span data-stu-id="e1f15-113">The following example demonstrates how to use the <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> extension methods.</span></span>  
  
 [!code-csharp[TPL_UnWrap#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_unwrap/cs/unwrapprogram.cs#04)]
 [!code-vb[TPL_UnWrap#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_unwrap/vb/snippet04.vb#04)]  
  
## <a name="see-also"></a><span data-ttu-id="e1f15-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1f15-114">See also</span></span>

- <xref:System.Threading.Tasks.TaskExtensions?displayProperty=nameWithType>
- [<span data-ttu-id="e1f15-115">以工作為基礎的非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="e1f15-115">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
