---
title: "如何：接聽具有等候控制代碼的取消要求"
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
- cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a0998703ef5b27b4de725a2c2adcfc3d9a2135b9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a><span data-ttu-id="011b4-102">如何：接聽具有等候控制代碼的取消要求</span><span class="sxs-lookup"><span data-stu-id="011b4-102">How to: Listen for Cancellation Requests That Have Wait Handles</span></span>
<span data-ttu-id="011b4-103">如果方法正在等待要接收訊號的事件時遭到封鎖，則它無法檢查取消語彙基元的值並及時回應。</span><span class="sxs-lookup"><span data-stu-id="011b4-103">If a method is blocked while it is waiting for an event to be signaled, it cannot check the value of the cancellation token and respond in a timely manner.</span></span> <span data-ttu-id="011b4-104">第一個範例示範如何在您使用 <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> 之類的事件 (不以原生方式支援統一取消架構) 時，解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="011b4-104">The first example shows how to solve this problem when you are working with events such as <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> that do not natively support the unified cancellation framework.</span></span> <span data-ttu-id="011b4-105">第二個範例示範使用 <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> 以支援統一取消的更簡化方法。</span><span class="sxs-lookup"><span data-stu-id="011b4-105">The second example shows a more streamlined approach that uses <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, which does support unified cancellation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="011b4-106">啟用 [Just My Code] 時，Visual Studio 在某些情況下會在擲回例外狀況的字行上中斷，並顯示錯誤訊息，指出「使用者程式碼未處理例外狀況」。</span><span class="sxs-lookup"><span data-stu-id="011b4-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="011b4-107">這個錯誤是良性的。</span><span class="sxs-lookup"><span data-stu-id="011b4-107">This error is benign.</span></span> <span data-ttu-id="011b4-108">您可以按 F5 鍵繼續，並查看下面範例中示範的例外狀況處理行為。</span><span class="sxs-lookup"><span data-stu-id="011b4-108">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="011b4-109">若要防止 Visual Studio 在遇到第一個錯誤時就中斷，只要取消核取 [工具]、[選項]、[偵錯]、[一般] 下的 [Just My Code] 核取方塊即可。</span><span class="sxs-lookup"><span data-stu-id="011b4-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="011b4-110">範例</span><span class="sxs-lookup"><span data-stu-id="011b4-110">Example</span></span>  
 <span data-ttu-id="011b4-111">下列範例使用 <xref:System.Threading.ManualResetEvent>，來示範如何解除封鎖不支援統一取消的等候控制代碼。</span><span class="sxs-lookup"><span data-stu-id="011b4-111">The following example uses a <xref:System.Threading.ManualResetEvent> to demonstrate how to unblock wait handles that do not support unified cancellation.</span></span>  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="011b4-112">範例</span><span class="sxs-lookup"><span data-stu-id="011b4-112">Example</span></span>  
 <span data-ttu-id="011b4-113">下列範例使用 <xref:System.Threading.ManualResetEventSlim>，來示範如何解除封鎖不支援統一取消的協調基本類型。</span><span class="sxs-lookup"><span data-stu-id="011b4-113">The following example uses a <xref:System.Threading.ManualResetEventSlim> to demonstrate how to unblock coordination primitives that do support unified cancellation.</span></span> <span data-ttu-id="011b4-114">相同的方法可以與其他輕量型協調基本類型搭配使用，例如 <xref:System.Threading.Semaphore>`Slim` 和 <xref:System.Threading.CountdownEvent>。</span><span class="sxs-lookup"><span data-stu-id="011b4-114">The same approach can be used with other lightweight coordination primitives, such as <xref:System.Threading.Semaphore>`Slim` and <xref:System.Threading.CountdownEvent>.</span></span>  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="011b4-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="011b4-115">See Also</span></span>  
 [<span data-ttu-id="011b4-116">Managed 執行緒中的取消作業</span><span class="sxs-lookup"><span data-stu-id="011b4-116">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
