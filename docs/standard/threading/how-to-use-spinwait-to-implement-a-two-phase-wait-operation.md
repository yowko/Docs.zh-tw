---
title: "如何：使用 SpinWait 實作兩階段等候作業"
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
helpviewer_keywords: SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2717ba2d63e4ecf40638c369b66f2c696e396a5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a><span data-ttu-id="0ae6a-102">如何：使用 SpinWait 實作兩階段等候作業</span><span class="sxs-lookup"><span data-stu-id="0ae6a-102">How to: Use SpinWait to Implement a Two-Phase Wait Operation</span></span>
<span data-ttu-id="0ae6a-103">下列範例示範如何使用<xref:System.Threading.SpinWait?displayProperty=nameWithType>來實作兩階段等候作業的物件。</span><span class="sxs-lookup"><span data-stu-id="0ae6a-103">The following example shows how to use a <xref:System.Threading.SpinWait?displayProperty=nameWithType> object to implement a two-phase wait operation.</span></span> <span data-ttu-id="0ae6a-104">在第一個階段中，同步處理物件， `Latch`，它會檢查是否鎖定已變成可用時少數週期旋轉。</span><span class="sxs-lookup"><span data-stu-id="0ae6a-104">In the first phase, the synchronization object, a `Latch`, spins for a few cycles while it checks whether the lock has become available.</span></span> <span data-ttu-id="0ae6a-105">在第二個階段中，如果鎖定可用，然後在`Wait`方法傳回時不使用<xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>執行等待; 否則`Wait`執行等候。</span><span class="sxs-lookup"><span data-stu-id="0ae6a-105">In the second phase, if the lock becomes available, then the `Wait` method returns without using the <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> to perform its wait; otherwise, `Wait` performs the wait.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ae6a-106">範例</span><span class="sxs-lookup"><span data-stu-id="0ae6a-106">Example</span></span>  
 <span data-ttu-id="0ae6a-107">此範例示範基本的閂鎖同步處理的基本實作。</span><span class="sxs-lookup"><span data-stu-id="0ae6a-107">This example shows a very basic implementation of a Latch synchronization primitive.</span></span> <span data-ttu-id="0ae6a-108">預期的等候時間很短時，您可以使用這個資料結構。</span><span class="sxs-lookup"><span data-stu-id="0ae6a-108">You can use this data structure when wait times are expected to be very short.</span></span> <span data-ttu-id="0ae6a-109">這個範例是僅針對示範目的。</span><span class="sxs-lookup"><span data-stu-id="0ae6a-109">This example is for demonstration purposes only.</span></span> <span data-ttu-id="0ae6a-110">如果您在程式中需要閂鎖類型功能，請考慮使用<xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="0ae6a-110">If you require latch-type functionality in your program, consider using <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.</span></span>  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 <span data-ttu-id="0ae6a-111">使用閂鎖<xref:System.Threading.SpinWait>就地啟動只到下一個呼叫的物件`SpinOnce`導致<xref:System.Threading.SpinWait>產生執行緒的時間配量。</span><span class="sxs-lookup"><span data-stu-id="0ae6a-111">The latch uses the <xref:System.Threading.SpinWait> object to spin in place only until the next call to `SpinOnce` causes the <xref:System.Threading.SpinWait> to yield the time slice of the thread.</span></span> <span data-ttu-id="0ae6a-112">此時，閂鎖會使它自己的內容切換藉由呼叫<xref:System.Threading.WaitHandle.WaitOne%2A>上<xref:System.Threading.ManualResetEvent>並傳入逾時值的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="0ae6a-112">At that point, the latch causes its own context switch by calling <xref:System.Threading.WaitHandle.WaitOne%2A> on the <xref:System.Threading.ManualResetEvent> and passing in the remainder of the time-out value.</span></span>  
  
 <span data-ttu-id="0ae6a-113">記錄輸出會顯示頻率閂鎖來提升效能所取得的鎖定，而不使用<xref:System.Threading.ManualResetEvent>。</span><span class="sxs-lookup"><span data-stu-id="0ae6a-113">The logging output shows how often the Latch was able to increase performance by acquiring the lock without using the <xref:System.Threading.ManualResetEvent>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ae6a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ae6a-114">See Also</span></span>  
 [<span data-ttu-id="0ae6a-115">SpinWait</span><span class="sxs-lookup"><span data-stu-id="0ae6a-115">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 [<span data-ttu-id="0ae6a-116">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="0ae6a-116">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
