---
title: SpinLock
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: synchronization primitives, SpinLock
ms.assetid: f9af93bb-7a0d-4ba5-afe8-74f48b6b6958
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: efe9b3126b3c952ab156f9ca40752ad8d3fddcd1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="spinlock"></a><span data-ttu-id="87729-102">SpinLock</span><span class="sxs-lookup"><span data-stu-id="87729-102">SpinLock</span></span>
<span data-ttu-id="87729-103"><xref:System.Threading.SpinLock>結構是低階、 互斥同步處理基本類型，在等候取得鎖定期間的旋轉。</span><span class="sxs-lookup"><span data-stu-id="87729-103">The <xref:System.Threading.SpinLock> structure is a low-level, mutual-exclusion synchronization primitive that spins while it waits to acquire a lock.</span></span> <span data-ttu-id="87729-104">在多核心電腦時應該等候時間很短且競爭時最少，<xref:System.Threading.SpinLock>可以優於其他類型的鎖定。</span><span class="sxs-lookup"><span data-stu-id="87729-104">On multicore computers, when wait times are expected to be short and when contention is minimal, <xref:System.Threading.SpinLock> can perform better than other kinds of locks.</span></span> <span data-ttu-id="87729-105">不過，我們建議您改用<xref:System.Threading.SpinLock>只有當您判斷程式碼剖析，<xref:System.Threading.Monitor?displayProperty=nameWithType>方法或<xref:System.Threading.Interlocked>方法會大幅減慢程式的效能。</span><span class="sxs-lookup"><span data-stu-id="87729-105">However, we recommend that you use <xref:System.Threading.SpinLock> only when you determine by profiling that the <xref:System.Threading.Monitor?displayProperty=nameWithType> method or the <xref:System.Threading.Interlocked> methods are significantly slowing the performance of your program.</span></span>  
  
 <span data-ttu-id="87729-106"><xref:System.Threading.SpinLock>可能會產生即使它不尚未取得鎖定之執行緒的時間配量。</span><span class="sxs-lookup"><span data-stu-id="87729-106"><xref:System.Threading.SpinLock> may yield the time slice of the thread even if it has not yet acquired the lock.</span></span> <span data-ttu-id="87729-107">它會以避免執行緒優先權反轉，並啟用進行記憶體回收行程。</span><span class="sxs-lookup"><span data-stu-id="87729-107">It does this to avoid thread-priority inversion, and to enable the garbage collector to make progress.</span></span> <span data-ttu-id="87729-108">當您使用<xref:System.Threading.SpinLock>，確保任何執行緒可以保留鎖定，非常短暫的時間範圍內，已超過和任何執行緒可以封鎖時，它會持有鎖定。</span><span class="sxs-lookup"><span data-stu-id="87729-108">When you use a <xref:System.Threading.SpinLock>, ensure that no thread can hold the lock for more than a very brief time span, and that no thread can block while it holds the lock.</span></span>  
  
 <span data-ttu-id="87729-109">由於單一執行緒存取鎖是實值類型，您必須明確地將傳遞它參考如果您想要參考相同的鎖定，兩個複本。</span><span class="sxs-lookup"><span data-stu-id="87729-109">Because SpinLock is a value type, you must explicitly pass it by reference if you intend the two copies to refer to the same lock.</span></span>  
  
 <span data-ttu-id="87729-110">如需如何使用這種類型的詳細資訊，請參閱<xref:System.Threading.SpinLock?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="87729-110">For more information about how to use this type, see <xref:System.Threading.SpinLock?displayProperty=nameWithType>.</span></span> <span data-ttu-id="87729-111">如需範例，請參閱[How to： 使用 SpinLock 進行低階同步處理](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="87729-111">For an example, see [How to: Use SpinLock for Low-Level Synchronization](../../../docs/standard/threading/how-to-use-spinlock-for-low-level-synchronization.md).</span></span>  
  
 <span data-ttu-id="87729-112"><xref:System.Threading.SpinLock>支援*執行緒*-*追蹤*模式可讓您在開發階段，協助追蹤在特定時間持有鎖定的執行緒。</span><span class="sxs-lookup"><span data-stu-id="87729-112"><xref:System.Threading.SpinLock> supports a *thread*-*tracking* mode that you can use during the development phase to help track the thread that is holding the lock at a specific time.</span></span> <span data-ttu-id="87729-113">執行緒追蹤模式是非常適用於偵錯，但我們建議您關閉該程式的發行版本中因為它可能會降低效能。</span><span class="sxs-lookup"><span data-stu-id="87729-113">Thread-tracking mode is very useful for debugging, but we recommend that you turn it off in the release version of your program because it may slow performance.</span></span> <span data-ttu-id="87729-114">如需詳細資訊，請參閱[How to： 啟用執行緒追蹤模式，在單一執行緒存取鎖](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md)。</span><span class="sxs-lookup"><span data-stu-id="87729-114">For more information, see [How to: Enable Thread-Tracking Mode in SpinLock](../../../docs/standard/threading/how-to-enable-thread-tracking-mode-in-spinlock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87729-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87729-115">See Also</span></span>  
 [<span data-ttu-id="87729-116">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="87729-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
