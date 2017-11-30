---
title: "如何：使用 SpinLock 進行低階同步處理"
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
helpviewer_keywords: SpinLock, how to use
ms.assetid: a9ed3e4e-4f29-4207-b730-ed0a51ecbc19
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 30ddc7d340b210aaad4a04ea43e89555d2701f20
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-use-spinlock-for-low-level-synchronization"></a><span data-ttu-id="45817-102">如何：使用 SpinLock 進行低階同步處理</span><span class="sxs-lookup"><span data-stu-id="45817-102">How to: Use SpinLock for Low-Level Synchronization</span></span>
<span data-ttu-id="45817-103">下列範例示範如何使用<xref:System.Threading.SpinLock>。</span><span class="sxs-lookup"><span data-stu-id="45817-103">The following example demonstrates how to use a <xref:System.Threading.SpinLock>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45817-104">範例</span><span class="sxs-lookup"><span data-stu-id="45817-104">Example</span></span>  
 <span data-ttu-id="45817-105">在此範例中，關鍵區段執行少量工作，讓它的絕佳候選<xref:System.Threading.SpinLock>。</span><span class="sxs-lookup"><span data-stu-id="45817-105">In this example, the critical section performs a minimal amount of work, which makes it a good candidate for a <xref:System.Threading.SpinLock>.</span></span> <span data-ttu-id="45817-106">增加工作只需要編寫小量會增加的效能<xref:System.Threading.SpinLock>相較於標準的鎖定。</span><span class="sxs-lookup"><span data-stu-id="45817-106">Increasing the work a small amount increases the performance of the <xref:System.Threading.SpinLock> compared to a standard lock.</span></span> <span data-ttu-id="45817-107">不過，在增加到達某一程度後，SpinLock 的成本就會變成高於標準鎖定。</span><span class="sxs-lookup"><span data-stu-id="45817-107">However, there is a point at which a SpinLock becomes more expensive than a standard lock.</span></span> <span data-ttu-id="45817-108">您可以使用程式碼剖析工具中的並行分析功能，來查看哪一種鎖定型別可在您的程式中提供較佳的效能。</span><span class="sxs-lookup"><span data-stu-id="45817-108">You can use the concurrency profiling functionality in the profiling tools to see which type of lock provides better performance in your program.</span></span> <span data-ttu-id="45817-109">如需詳細資訊，請參閱[並行視覺化檢視](/visualstudio/profiling/concurrency-visualizer)。</span><span class="sxs-lookup"><span data-stu-id="45817-109">For more information, see [Concurrency Visualizer](/visualstudio/profiling/concurrency-visualizer).</span></span>  
  
 [!code-csharp[CDS_SpinLock#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#02)]
 [!code-vb[CDS_SpinLock#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_vb.vb#02)]  
  
 <span data-ttu-id="45817-110"><xref:System.Threading.SpinLock>可能會很有用，當共用資源上的鎖定並不會保留很長。</span><span class="sxs-lookup"><span data-stu-id="45817-110"><xref:System.Threading.SpinLock> might be useful when a lock on a shared resource is not going to be held for very long.</span></span> <span data-ttu-id="45817-111">在這類情況下，多核心電腦上的已封鎖執行緒可以有效率地微調幾個週期，直到鎖定釋放為止。</span><span class="sxs-lookup"><span data-stu-id="45817-111">In such cases, on multi-core computers it can be efficient for the blocked thread to spin for a few cycles until the lock is released.</span></span> <span data-ttu-id="45817-112">藉由微調，執行緒不會變成鎖定狀態 (這是需要大量 CPU 的程序)。</span><span class="sxs-lookup"><span data-stu-id="45817-112">By spinning, the thread does not become blocked, which is a CPU-intensive process.</span></span> <span data-ttu-id="45817-113"><xref:System.Threading.SpinLock>將會停止微調，以避免不足邏輯處理器或優先順序反轉具有超執行緒的系統上的某些條件下。</span><span class="sxs-lookup"><span data-stu-id="45817-113"><xref:System.Threading.SpinLock> will stop spinning under certain conditions to prevent starvation of logical processors or priority inversion on systems with Hyper-Threading.</span></span>  
  
 <span data-ttu-id="45817-114">這個範例會使用<xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>類別，需要進行多執行緒存取的使用者同步處理。</span><span class="sxs-lookup"><span data-stu-id="45817-114">This example uses the <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType> class, which requires user synchronization for multi-threaded access.</span></span> <span data-ttu-id="45817-115">在.NET Framework 第 4 版為目標的應用程式，另一個選項是使用<xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>，不需要任何使用者的鎖定。</span><span class="sxs-lookup"><span data-stu-id="45817-115">In applications that target the .NET Framework version 4, another option is to use the <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>, which does not require any user locks.</span></span>  
  
 <span data-ttu-id="45817-116">請注意使用`false`(`False`在 Visual Basic 中) 的呼叫中<xref:System.Threading.SpinLock.Exit%2A>。</span><span class="sxs-lookup"><span data-stu-id="45817-116">Note the use of `false` (`False` in Visual Basic) in the call to <xref:System.Threading.SpinLock.Exit%2A>.</span></span> <span data-ttu-id="45817-117">這可提供最佳效能。</span><span class="sxs-lookup"><span data-stu-id="45817-117">This provides the best performance.</span></span> <span data-ttu-id="45817-118">在 IA64 架構上指定 `true` (`True`) 以使用記憶體範圍，記憶體範圍可排清寫入緩衝區以確保鎖定現已可供其他執行緒來結束。</span><span class="sxs-lookup"><span data-stu-id="45817-118">Specify `true` (`True`)on IA64 architectures to use the memory fence, which flushes the write buffers to ensure that the lock is now available for other threads to exit.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45817-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45817-119">See Also</span></span>  
 [<span data-ttu-id="45817-120">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="45817-120">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
