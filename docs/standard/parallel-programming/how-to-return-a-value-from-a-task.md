---
title: 作法：從工作傳回值
description: 請參閱如何使用 [工作] <TResult> 類型，從 .net 中的 Result 屬性傳回值。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to return a value
ms.assetid: c4bc0f44-eba2-4e96-9e03-1cc787461e61
ms.openlocfilehash: c7a4a683545c9ef0448d9cdce769aae79215aecf
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825607"
---
# <a name="how-to-return-a-value-from-a-task"></a><span data-ttu-id="aecea-103">作法：從工作傳回值</span><span class="sxs-lookup"><span data-stu-id="aecea-103">How to: Return a Value from a Task</span></span>
<span data-ttu-id="aecea-104">這個範例示範如何使用 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> 類型從 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性傳回值。</span><span class="sxs-lookup"><span data-stu-id="aecea-104">This example shows how to use the <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> type to return a value from the <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="aecea-105">它需要有 C:\Users\Public\Pictures\Sample Pictures\ 目錄存在，且其中包含檔案。</span><span class="sxs-lookup"><span data-stu-id="aecea-105">It requires that the C:\Users\Public\Pictures\Sample Pictures\ directory exists, and that it contains files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aecea-106">範例</span><span class="sxs-lookup"><span data-stu-id="aecea-106">Example</span></span>  
 [!code-csharp[TPL#10](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl/cs/returnavalue10.cs#10)]
 [!code-vb[TPL#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl/vb/10_returnavalue.vb#10)]  
  
 <span data-ttu-id="aecea-107"><xref:System.Threading.Tasks.Task%601.Result%2A> 屬性會封鎖呼叫執行緒，直到工作完成。</span><span class="sxs-lookup"><span data-stu-id="aecea-107">The <xref:System.Threading.Tasks.Task%601.Result%2A> property blocks the calling thread until the task finishes.</span></span>  
  
 <span data-ttu-id="aecea-108">若要查看如何傳遞一個 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> 的結果到接續工作，請參閱[使用接續工作鏈結工作](chaining-tasks-by-using-continuation-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="aecea-108">To see how to pass the result of one <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> to a continuation task, see [Chaining Tasks by Using Continuation Tasks](chaining-tasks-by-using-continuation-tasks.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aecea-109">請參閱</span><span class="sxs-lookup"><span data-stu-id="aecea-109">See also</span></span>

- [<span data-ttu-id="aecea-110">以工作為基礎的非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="aecea-110">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
- [<span data-ttu-id="aecea-111">PLINQ 和 TPL 中的 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="aecea-111">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
