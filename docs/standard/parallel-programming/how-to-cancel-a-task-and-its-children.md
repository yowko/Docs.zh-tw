---
title: 作法：取消工作及其子系
description: 請參閱如何在 .NET 中取消工作及其子系的範例。 這些範例涵蓋可取消的工作建立的步驟，以及工作已取消的通知。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, how to cancel
ms.assetid: 08574301-8331-4719-ad50-9cf7f6ff3048
ms.openlocfilehash: 82a71faf3a2390f5bb36dd896cf865f773f54bd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713219"
---
# <a name="how-to-cancel-a-task-and-its-children"></a><span data-ttu-id="4e9ef-104">作法：取消工作及其子系</span><span class="sxs-lookup"><span data-stu-id="4e9ef-104">How to: Cancel a Task and Its Children</span></span>

<span data-ttu-id="4e9ef-105">這些範例示範如何執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="4e9ef-105">These examples show how to perform the following tasks:</span></span>  
  
1. <span data-ttu-id="4e9ef-106">建立和啟動可取消的工作。</span><span class="sxs-lookup"><span data-stu-id="4e9ef-106">Create and start a cancelable task.</span></span>  
  
2. <span data-ttu-id="4e9ef-107">將取消權杖傳送至您的使用者委派或工作執行個體 (選擇性)。</span><span class="sxs-lookup"><span data-stu-id="4e9ef-107">Pass a cancellation token to your user delegate and optionally to the task instance.</span></span>  
  
3. <span data-ttu-id="4e9ef-108">注意並回應使用者委派中的取消要求。</span><span class="sxs-lookup"><span data-stu-id="4e9ef-108">Notice and respond to the cancellation request in your user delegate.</span></span>  
  
4. <span data-ttu-id="4e9ef-109">注意已取消工作的呼叫端執行緒 (選擇性)。</span><span class="sxs-lookup"><span data-stu-id="4e9ef-109">Optionally notice on the calling thread that the task was canceled.</span></span>  
  
 <span data-ttu-id="4e9ef-110">呼叫端執行緒不會強制結束工作；它只會通知已要求取消。</span><span class="sxs-lookup"><span data-stu-id="4e9ef-110">The calling thread does not forcibly end the task; it only signals that cancellation is requested.</span></span> <span data-ttu-id="4e9ef-111">如果工作已在執行，則是由使用者委派來通知要求並適當回應。</span><span class="sxs-lookup"><span data-stu-id="4e9ef-111">If the task is already running, it is up to the user delegate to notice the request and respond appropriately.</span></span> <span data-ttu-id="4e9ef-112">如果在工作執行前要求取消，則永遠不會執行使用者委派，且工作物件會轉換成 Canceled 狀態。</span><span class="sxs-lookup"><span data-stu-id="4e9ef-112">If cancellation is requested before the task runs, then the user delegate is never executed and the task object transitions into the Canceled state.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e9ef-113">範例</span><span class="sxs-lookup"><span data-stu-id="4e9ef-113">Example</span></span>  

 <span data-ttu-id="4e9ef-114">此範例示範如何終止 <xref:System.Threading.Tasks.Task> 及其子系，以回應取消要求。</span><span class="sxs-lookup"><span data-stu-id="4e9ef-114">This example shows how to terminate a <xref:System.Threading.Tasks.Task> and its children in response to a cancellation request.</span></span> <span data-ttu-id="4e9ef-115">這個範例也會說明在使用者委派藉由擲回 <xref:System.Threading.Tasks.TaskCanceledException> 結束時，呼叫端執行緒可以選擇性地使用 <xref:System.Threading.Tasks.Task.Wait%2A> 方法或 <xref:System.Threading.Tasks.Task.WaitAll%2A> 方法等候工作完成。</span><span class="sxs-lookup"><span data-stu-id="4e9ef-115">It also shows that when a user delegate terminates by throwing a <xref:System.Threading.Tasks.TaskCanceledException>, the calling thread can optionally use the <xref:System.Threading.Tasks.Task.Wait%2A> method or <xref:System.Threading.Tasks.Task.WaitAll%2A> method to wait for the tasks to finish.</span></span> <span data-ttu-id="4e9ef-116">在這種情況下，您必須使用 `try/catch` 區塊來處理呼叫端執行緒上的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4e9ef-116">In this case, you must use a `try/catch` block to handle the exceptions on the calling thread.</span></span>  
  
 [!code-csharp[TPL_Cancellation#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cancellation/cs/cancel1.cs#04)]
 [!code-vb[TPL_Cancellation#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cancellation/vb/cancel1.vb#04)]  
  
 <span data-ttu-id="4e9ef-117"><xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 類別已和基礎是 <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> 及 <xref:System.Threading.CancellationToken?displayProperty=nameWithType> 型別的取消模型完全整合。</span><span class="sxs-lookup"><span data-stu-id="4e9ef-117">The <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> class is fully integrated with the cancellation model that is based on the <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType> and <xref:System.Threading.CancellationToken?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="4e9ef-118">如需詳細資訊，請參閱[受控執行緒中的取消作業](../threading/cancellation-in-managed-threads.md)和[工作取消](task-cancellation.md)。</span><span class="sxs-lookup"><span data-stu-id="4e9ef-118">For more information, see [Cancellation in Managed Threads](../threading/cancellation-in-managed-threads.md) and [Task Cancellation](task-cancellation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e9ef-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e9ef-119">See also</span></span>

- <xref:System.Threading.CancellationTokenSource?displayProperty=nameWithType>
- <xref:System.Threading.CancellationToken?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>
- [<span data-ttu-id="4e9ef-120">以工作為基礎的非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="4e9ef-120">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
- [<span data-ttu-id="4e9ef-121">附加與中斷連結的子工作</span><span class="sxs-lookup"><span data-stu-id="4e9ef-121">Attached and Detached Child Tasks</span></span>](attached-and-detached-child-tasks.md)
- [<span data-ttu-id="4e9ef-122">PLINQ 和 TPL 中的 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="4e9ef-122">Lambda Expressions in PLINQ and TPL</span></span>](lambda-expressions-in-plinq-and-tpl.md)
