---
title: 註冊取消要求的回呼
ms.date: 08/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
ms.openlocfilehash: f551055fc6e5e4565329201e9e0be6e4a83487a1
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826400"
---
# <a name="register-callbacks-for-cancellation-requests"></a><span data-ttu-id="7af27-102">註冊取消要求的回呼</span><span class="sxs-lookup"><span data-stu-id="7af27-102">Register callbacks for cancellation requests</span></span>

<span data-ttu-id="7af27-103">瞭解如何註冊將在屬性變成 true 時叫用的委派 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 。</span><span class="sxs-lookup"><span data-stu-id="7af27-103">Learn how to register a delegate that will be invoked when a <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property becomes true.</span></span> <span data-ttu-id="7af27-104">當對建立 <xref:System.Threading.CancellationTokenSource.Cancel%2A> 權杖的物件進行呼叫時，此值會從 false 變更為 true。</span><span class="sxs-lookup"><span data-stu-id="7af27-104">The value changes from false to true when a call to <xref:System.Threading.CancellationTokenSource.Cancel%2A> on the object that created the token is made.</span></span> <span data-ttu-id="7af27-105">使用這項技術來取消非原生支援整合取消架構的非同步作業，以及解除封鎖可能等候非同步作業完成的方法。</span><span class="sxs-lookup"><span data-stu-id="7af27-105">Use this technique for canceling asynchronous operations that do not natively support the unified cancellation framework, and for unblocking methods that might be waiting for an asynchronous operation to finish.</span></span>

> [!NOTE]
> <span data-ttu-id="7af27-106">啟用 [Just My Code] 時，Visual Studio 在某些情況下會在擲回例外狀況的字行上中斷，並顯示錯誤訊息，指出「使用者程式碼未處理例外狀況」。</span><span class="sxs-lookup"><span data-stu-id="7af27-106">When "Just My Code" is enabled, Visual Studio in some cases will break on the line that throws the exception and display an error message that says "exception not handled by user code."</span></span> <span data-ttu-id="7af27-107">這個錯誤是良性的。</span><span class="sxs-lookup"><span data-stu-id="7af27-107">This error is benign.</span></span> <span data-ttu-id="7af27-108">您可以按 <kbd>F5</kbd> 繼續執行，並查看下列範例中示範的例外狀況處理行為。</span><span class="sxs-lookup"><span data-stu-id="7af27-108">You can press <kbd>F5</kbd> to continue from it, and see the exception-handling behavior that is demonstrated in the examples below.</span></span> <span data-ttu-id="7af27-109">若要防止 Visual Studio 在遇到第一個錯誤時就中斷，只要取消核取 [工具]、[選項]、[偵錯]、[一般] 下的 [Just My Code] 核取方塊即可。</span><span class="sxs-lookup"><span data-stu-id="7af27-109">To prevent Visual Studio from breaking on the first error, just uncheck the "Just My Code" checkbox under **Tools, Options, Debugging, General**.</span></span>

## <a name="example"></a><span data-ttu-id="7af27-110">範例</span><span class="sxs-lookup"><span data-stu-id="7af27-110">Example</span></span>

<span data-ttu-id="7af27-111">在下列範例中，<xref:System.Net.WebClient.CancelAsync%2A> 方法註冊為透過取消語彙基元要求取消時，所要叫用的方法。</span><span class="sxs-lookup"><span data-stu-id="7af27-111">In the following example, the <xref:System.Net.WebClient.CancelAsync%2A> method is registered as the method to be invoked when cancellation is requested through the cancellation token.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs":::
:::code language="vb" source="../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb":::

<span data-ttu-id="7af27-112">如果註冊回呼時，已經要求過取消，仍然保證會呼叫回呼。</span><span class="sxs-lookup"><span data-stu-id="7af27-112">If cancellation has already been requested when the callback is registered, the callback is still guaranteed to be called.</span></span> <span data-ttu-id="7af27-113">在這個特殊案例中，如果沒有任何非同步作業正在進行中，<xref:System.Net.WebClient.CancelAsync%2A> 方法就不會做任何事，所以呼叫方法一定是安全的。</span><span class="sxs-lookup"><span data-stu-id="7af27-113">In this particular case, the <xref:System.Net.WebClient.CancelAsync%2A> method will do nothing if no asynchronous operation is in progress, so it is always safe to call the method.</span></span>

## <a name="see-also"></a><span data-ttu-id="7af27-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="7af27-114">See also</span></span>

- [<span data-ttu-id="7af27-115">受控執行緒中的取消作業</span><span class="sxs-lookup"><span data-stu-id="7af27-115">Cancellation in managed threads</span></span>](cancellation-in-managed-threads.md)
- <xref:System.Net.WebClient.DownloadStringTaskAsync(System.String)?displayProperty=nameWithType>
