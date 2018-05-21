---
title: SpinLock
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f7d1d95030d2bc9f9288ae134471c150a37291b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="spinlock"></a><span data-ttu-id="b47c7-102">SpinLock</span><span class="sxs-lookup"><span data-stu-id="b47c7-102">SpinLock</span></span>
<span data-ttu-id="b47c7-103"><xref:System.Threading.SpinLock> 結構是一個低階、互斥的同步處理基本類型，會在等候取得鎖定期間進行微調。</span><span class="sxs-lookup"><span data-stu-id="b47c7-103">The <xref:System.Threading.SpinLock> structure is a low-level, mutual-exclusion synchronization primitive that spins while it waits to acquire a lock.</span></span> <span data-ttu-id="b47c7-104">在多核心電腦上，預期等候時間很短且競爭最少時，<xref:System.Threading.SpinLock> 可以優於其他類型鎖定的方式執行。</span><span class="sxs-lookup"><span data-stu-id="b47c7-104">On multicore computers, when wait times are expected to be short and when contention is minimal, <xref:System.Threading.SpinLock> can perform better than other kinds of locks.</span></span> <span data-ttu-id="b47c7-105">不過，我們建議您只有在藉由分析 <xref:System.Threading.Monitor?displayProperty=nameWithType> 方法進行判斷時，或 <xref:System.Threading.Interlocked> 方法大幅減慢程式的效能，才使用 <xref:System.Threading.SpinLock>。</span><span class="sxs-lookup"><span data-stu-id="b47c7-105">However, we recommend that you use <xref:System.Threading.SpinLock> only when you determine by profiling that the <xref:System.Threading.Monitor?displayProperty=nameWithType> method or the <xref:System.Threading.Interlocked> methods are significantly slowing the performance of your program.</span></span>  
  
 <span data-ttu-id="b47c7-106">即使 <xref:System.Threading.SpinLock> 尚未取得鎖定，還是可能會讓出執行緒的時間配量。</span><span class="sxs-lookup"><span data-stu-id="b47c7-106"><xref:System.Threading.SpinLock> may yield the time slice of the thread even if it has not yet acquired the lock.</span></span> <span data-ttu-id="b47c7-107">它會執行此作業來避免執行緒優先順序反轉，並使記憶體回收行程繼續有進展。</span><span class="sxs-lookup"><span data-stu-id="b47c7-107">It does this to avoid thread-priority inversion, and to enable the garbage collector to make progress.</span></span> <span data-ttu-id="b47c7-108">當您使用 <xref:System.Threading.SpinLock> 時，確保沒有任何執行緒可以保留鎖定超過一個非常短暫的時間範圍，而且沒有執行緒可以在保留鎖定時加以封鎖。</span><span class="sxs-lookup"><span data-stu-id="b47c7-108">When you use a <xref:System.Threading.SpinLock>, ensure that no thread can hold the lock for more than a very brief time span, and that no thread can block while it holds the lock.</span></span>  
  
 <span data-ttu-id="b47c7-109">由於 SpinLock 是一個實值類型，因此，如果您想要讓兩個複本參考同一個鎖定，就必須明確地以傳址方式傳遞它。</span><span class="sxs-lookup"><span data-stu-id="b47c7-109">Because SpinLock is a value type, you must explicitly pass it by reference if you intend the two copies to refer to the same lock.</span></span>  
  
 <span data-ttu-id="b47c7-110">如需如何使用此類型的詳細資訊，請參閱 <xref:System.Threading.SpinLock?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="b47c7-110">For more information about how to use this type, see <xref:System.Threading.SpinLock?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b47c7-111">如需範例，請參閱[如何：使用 SpinLock 進行低階同步處理](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="b47c7-111">For an example, see [How to: Use SpinLock for Low-Level Synchronization](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).</span></span>  
  
 <span data-ttu-id="b47c7-112"><xref:System.Threading.SpinLock> 支援「執行緒-」模式，讓您可以在開發階段使用，以協助追蹤在特定時間保留鎖定的執行緒。</span><span class="sxs-lookup"><span data-stu-id="b47c7-112"><xref:System.Threading.SpinLock> supports a *thread*-*tracking* mode that you can use during the development phase to help track the thread that is holding the lock at a specific time.</span></span> <span data-ttu-id="b47c7-113">執行緒追蹤模式非常適用於偵錯，但我們建議您在程式的發行版本中關閉此模式，因為它可能會降低效能。</span><span class="sxs-lookup"><span data-stu-id="b47c7-113">Thread-tracking mode is very useful for debugging, but we recommend that you turn it off in the release version of your program because it may slow performance.</span></span> <span data-ttu-id="b47c7-114">如需詳細資訊，請參閱[如何：啟用 SpinLock 中的執行緒追蹤模式](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md)。</span><span class="sxs-lookup"><span data-stu-id="b47c7-114">For more information, see [How to: Enable Thread-Tracking Mode in SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b47c7-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="b47c7-115">See Also</span></span>  
 [<span data-ttu-id="b47c7-116">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="b47c7-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
