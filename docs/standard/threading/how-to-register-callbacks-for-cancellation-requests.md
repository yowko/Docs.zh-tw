---
title: "如何：註冊取消要求的回呼"
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
helpviewer_keywords: cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 85b15ed610d80958ac9d7e3762ac8ea7b781b8d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a><span data-ttu-id="9d2df-102">如何：註冊取消要求的回呼</span><span class="sxs-lookup"><span data-stu-id="9d2df-102">How to: Register Callbacks for Cancellation Requests</span></span>
<span data-ttu-id="9d2df-103">下列範例示範如何註冊委派，會叫用時<xref:System.Threading.CancellationToken.IsCancellationRequested%2A>屬性變成 true 由於呼叫<xref:System.Threading.CancellationTokenSource.Cancel%2A>上建立權杖的物件。</span><span class="sxs-lookup"><span data-stu-id="9d2df-103">The following example shows how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true due to a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token.</span></span> <span data-ttu-id="9d2df-104">您可以使用這個技巧來取消原本不支援整合取消架構的非同步作業，以及解除封鎖可能會等候非同步作業完成的方法。</span><span class="sxs-lookup"><span data-stu-id="9d2df-104">Use this technique for cancelling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d2df-105">啟用 [Just My Code] 時，Visual Studio 在某些情況下會在擲回例外狀況的字行上中斷，並顯示錯誤訊息，指出「使用者程式碼未處理例外狀況」。</span><span class="sxs-lookup"><span data-stu-id="9d2df-105">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="9d2df-106">這個錯誤是良性的。</span><span class="sxs-lookup"><span data-stu-id="9d2df-106">This error is benign.</span></span> <span data-ttu-id="9d2df-107">您可以按 F5 鍵繼續，並查看下面範例中示範的例外狀況處理行為。</span><span class="sxs-lookup"><span data-stu-id="9d2df-107">You can press F5 to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="9d2df-108">若要防止 Visual Studio 的第一個錯誤的中斷，只要取消核取下的 [Just My Code] 核取方塊**工具、 選項、 偵錯、 一般**。</span><span class="sxs-lookup"><span data-stu-id="9d2df-108">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d2df-109">範例</span><span class="sxs-lookup"><span data-stu-id="9d2df-109">Example</span></span>  
 <span data-ttu-id="9d2df-110">在下列範例中，<xref:System.Net.WebClient.CancelAsync%2A> 方法註冊為透過取消語彙基元要求取消時，所要叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="9d2df-110">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 <span data-ttu-id="9d2df-111">如果註冊回呼時，已經要求過取消，仍然保證會呼叫回呼。</span><span class="sxs-lookup"><span data-stu-id="9d2df-111">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="9d2df-112">在這個特殊案例中，如果沒有任何非同步作業正在進行中，<xref:System.Net.WebClient.CancelAsync%2A> 方法就不會做任何事，所以呼叫方法一定是安全的。</span><span class="sxs-lookup"><span data-stu-id="9d2df-112">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d2df-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d2df-113">See Also</span></span>  
 [<span data-ttu-id="9d2df-114">Managed 執行緒中的取消作業</span><span class="sxs-lookup"><span data-stu-id="9d2df-114">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
