---
title: "如何：啟用 SpinLock 中的執行緒追蹤模式"
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
helpviewer_keywords: SpinLock, how to enable thread-tracking
ms.assetid: 62ee2e68-0bdd-4869-afc9-f0a57a11ae01
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca5f1b6eace7a24a6bbb7fd541858246828fa757
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-enable-thread-tracking-mode-in-spinlock"></a><span data-ttu-id="99166-102">如何：啟用 SpinLock 中的執行緒追蹤模式</span><span class="sxs-lookup"><span data-stu-id="99166-102">How to: Enable Thread-Tracking Mode in SpinLock</span></span>
<span data-ttu-id="99166-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType>是具有非常短的等候時間的情況下，您可以使用低層級的互斥鎖定。</span><span class="sxs-lookup"><span data-stu-id="99166-103"><xref:System.Threading.SpinLock?displayProperty=nameWithType> is a low-level mutual exclusion lock that you can use for scenarios that have very short wait times.</span></span> <span data-ttu-id="99166-104"><xref:System.Threading.SpinLock>不重複執行。</span><span class="sxs-lookup"><span data-stu-id="99166-104"><xref:System.Threading.SpinLock> is not re-entrant.</span></span> <span data-ttu-id="99166-105">在執行緒進入鎖定之後，它必須結束鎖定正確後，才可以一次進入。</span><span class="sxs-lookup"><span data-stu-id="99166-105">After a thread enters the lock, it must exit the lock correctly before it can enter again.</span></span> <span data-ttu-id="99166-106">一般而言，重新進入鎖定狀態的任何嘗試會導致死結，死結 （deadlock） 可以是很難偵錯。</span><span class="sxs-lookup"><span data-stu-id="99166-106">Typically, any attempt to re-enter the lock would cause deadlock, and deadlocks can be very difficult to debug.</span></span> <span data-ttu-id="99166-107">協助程式開發，<xref:System.Threading.SpinLock?displayProperty=nameWithType>支援一個執行緒追蹤模式，造成執行緒嘗試重新輸入已經保留的鎖定時擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="99166-107">As an aid to development, <xref:System.Threading.SpinLock?displayProperty=nameWithType> supports a thread-tracking mode that causes an exception to be thrown when a thread attempts to re-enter a lock that it already holds.</span></span> <span data-ttu-id="99166-108">這可讓您更輕鬆地找出的鎖定不結束正常的點。</span><span class="sxs-lookup"><span data-stu-id="99166-108">This lets you more easily locate the point at which the lock was not exited correctly.</span></span> <span data-ttu-id="99166-109">您可以藉由開啟執行緒追蹤模式<xref:System.Threading.SpinLock>建構函式會採用布林值的輸入參數，並傳入的引數`true`。</span><span class="sxs-lookup"><span data-stu-id="99166-109">You can turn on thread-tracking mode by using the <xref:System.Threading.SpinLock> constructor that takes a Boolean input parameter, and passing in an argument of `true`.</span></span> <span data-ttu-id="99166-110">開發和測試階段完成之後，關閉執行緒追蹤模式，以提升效能。</span><span class="sxs-lookup"><span data-stu-id="99166-110">After you complete the development and testing phases, turn off thread-tracking mode for better performance.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99166-111">範例</span><span class="sxs-lookup"><span data-stu-id="99166-111">Example</span></span>  
 <span data-ttu-id="99166-112">下列範例會示範執行緒追蹤模式。</span><span class="sxs-lookup"><span data-stu-id="99166-112">The following example demonstrates thread-tracking mode.</span></span> <span data-ttu-id="99166-113">正確地結束鎖定行標記為註解來模擬發生編碼錯誤，導致其中一個下列結果：</span><span class="sxs-lookup"><span data-stu-id="99166-113">The lines that correctly exit the lock are commented out to simulate a coding error that causes one of the following results:</span></span>  
  
-   <span data-ttu-id="99166-114">如果擲回例外狀況<xref:System.Threading.SpinLock>使用的引數建立`true`(`True`在 Visual Basic 中)。</span><span class="sxs-lookup"><span data-stu-id="99166-114">An exception is thrown if the <xref:System.Threading.SpinLock> was created by using an argument of `true` (`True` in Visual Basic).</span></span>  
  
-   <span data-ttu-id="99166-115">如果發生死結<xref:System.Threading.SpinLock>使用的引數建立`false`(`False`在 Visual Basic 中)。</span><span class="sxs-lookup"><span data-stu-id="99166-115">Deadlock if the <xref:System.Threading.SpinLock> was created by using an argument of `false` (`False` in Visual Basic).</span></span>  
  
 [!code-csharp[CDS_SpinLock#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinlock/cs/spinlockdemo.cs#01)]
 [!code-vb[CDS_SpinLock#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinlock/vb/spinlock_threadtracking.vb#01)]  
  
## <a name="see-also"></a><span data-ttu-id="99166-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99166-116">See Also</span></span>  
 [<span data-ttu-id="99166-117">SpinLock</span><span class="sxs-lookup"><span data-stu-id="99166-117">SpinLock</span></span>](../../../docs/standard/threading/spinlock.md)
