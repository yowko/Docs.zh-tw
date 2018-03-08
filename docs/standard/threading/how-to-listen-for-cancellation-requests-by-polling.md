---
title: "如何：透過輪詢接聽取消要求"
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
- cancellation, how to poll for requests
ms.assetid: c7f2f022-d08e-4e00-b4eb-ae84844cb1bc
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 56a927e10cb026814302728a72acb2f32223b29b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-listen-for-cancellation-requests-by-polling"></a><span data-ttu-id="3cb23-102">如何：透過輪詢接聽取消要求</span><span class="sxs-lookup"><span data-stu-id="3cb23-102">How to: Listen for Cancellation Requests by Polling</span></span>
<span data-ttu-id="3cb23-103">下列範例將示範一種方式：使用者程式碼可定期輪詢取消語彙基元，以查看呼叫執行緒是否已要求取消。</span><span class="sxs-lookup"><span data-stu-id="3cb23-103">The following example shows one way that user code can poll a cancellation token at regular intervals to see whether cancellation has been requested from the calling thread.</span></span> <span data-ttu-id="3cb23-104">這個範例會使用 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 類型，但相同的模式適用於 <xref:System.Threading.ThreadPool?displayProperty=nameWithType> 類型或 <xref:System.Threading.Thread?displayProperty=nameWithType> 類型直接建立的非同步作業。</span><span class="sxs-lookup"><span data-stu-id="3cb23-104">This example uses the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type, but the same pattern applies to asynchronous operations created directly by the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> type or the <xref:System.Threading.Thread?displayProperty=nameWithType> type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cb23-105">範例</span><span class="sxs-lookup"><span data-stu-id="3cb23-105">Example</span></span>  
 <span data-ttu-id="3cb23-106">輪詢需要某種可定期讀取布林值 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 屬性值的迴圈或遞迴程式碼。</span><span class="sxs-lookup"><span data-stu-id="3cb23-106">Polling requires some kind of loop or recursive code that can periodically read the value of the Boolean <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property.</span></span> <span data-ttu-id="3cb23-107">如果您使用 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 類型且正在等候呼叫執行緒上的工作完成，您可以使用 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> 方法來檢查屬性，並擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3cb23-107">If you are using the <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> type and you are waiting for the task to complete on the calling thread, you can use the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method to check the property and throw the exception.</span></span> <span data-ttu-id="3cb23-108">使用此方法，您可以確保會擲回正確的例外狀況來回應要求。</span><span class="sxs-lookup"><span data-stu-id="3cb23-108">By using this method, you ensure that the correct exception is thrown in response to a request.</span></span> <span data-ttu-id="3cb23-109">如果您使用 <xref:System.Threading.Tasks.Task>，則呼叫此方法優於手動擲回 <xref:System.OperationCanceledException>。</span><span class="sxs-lookup"><span data-stu-id="3cb23-109">If you are using a <xref:System.Threading.Tasks.Task>, then calling this method is better than manually throwing an <xref:System.OperationCanceledException>.</span></span> <span data-ttu-id="3cb23-110">如果您不需擲回例外狀況，則只需檢查屬性，如果屬性為 `true`，即從方法返回。</span><span class="sxs-lookup"><span data-stu-id="3cb23-110">If you do not have to throw the exception, then you can just check the property and return from the method if the property is `true`.</span></span>  
  
 [!code-csharp[Cancellation#11](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex11.cs#11)]
 [!code-vb[Cancellation#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex11.vb#11)]  
  
 <span data-ttu-id="3cb23-111">呼叫 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> 相當快速，不會在迴圈中引進大量額外負荷。</span><span class="sxs-lookup"><span data-stu-id="3cb23-111">Calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> is extremely fast and does not introduce significant overhead in loops.</span></span>  
  
 <span data-ttu-id="3cb23-112">如果您正在呼叫 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>，當您要進行其他工作來回應取消 (擲回例外狀況除外) 時，只需明確檢查 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="3cb23-112">If you are calling <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A>, you only have to explicitly check the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property if you have other work to do in response to the cancellation besides throwing the exception.</span></span> <span data-ttu-id="3cb23-113">在此範例中，您可以看到程式碼會實際存取屬性兩次：一次是明確的存取，另一次則是在 <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> 方法中。</span><span class="sxs-lookup"><span data-stu-id="3cb23-113">In this example, you can see that the code actually accesses the property twice: once in the explicit access and again in the <xref:System.Threading.CancellationToken.ThrowIfCancellationRequested%2A> method.</span></span> <span data-ttu-id="3cb23-114">但由於讀取 <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> 屬性的動作牽涉到每次存取只能有一個暫時性讀取指令，因此，從效能觀點來看，兩次存取並不重要。</span><span class="sxs-lookup"><span data-stu-id="3cb23-114">But because the act of reading the <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> property involves only one volatile read instruction per access, the double access is not significant from a performance perspective.</span></span> <span data-ttu-id="3cb23-115">最好還是呼叫方法，而非手動擲回 <xref:System.OperationCanceledException>。</span><span class="sxs-lookup"><span data-stu-id="3cb23-115">It is still preferable to call the method rather than manually throw the <xref:System.OperationCanceledException>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cb23-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="3cb23-116">See Also</span></span>  
 [<span data-ttu-id="3cb23-117">Managed 執行緒中的取消作業</span><span class="sxs-lookup"><span data-stu-id="3cb23-117">Cancellation in Managed Threads</span></span>](../../../docs/standard/threading/cancellation-in-managed-threads.md)
