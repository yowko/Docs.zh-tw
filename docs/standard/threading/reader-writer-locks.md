---
title: "Reader-Writer 鎖定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ReaderWriterLock class, about ReaderWriterLock class
- threading [.NET Framework], ReaderWriterLock class
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: df06e83165906199774f99de4140ace9b7396cbb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="reader-writer-locks"></a><span data-ttu-id="50298-102">Reader-Writer 鎖定</span><span class="sxs-lookup"><span data-stu-id="50298-102">Reader-Writer Locks</span></span>
<span data-ttu-id="50298-103"><xref:System.Threading.ReaderWriterLockSlim>類別可讓多個執行緒同時也會讀取資源，但需要等候獨佔鎖定，才能寫入至資源的執行緒。</span><span class="sxs-lookup"><span data-stu-id="50298-103">The <xref:System.Threading.ReaderWriterLockSlim> class enables multiple threads to read a resource concurrently, but requires a thread to wait for an exclusive lock in order to write to the resource.</span></span>  
  
 <span data-ttu-id="50298-104">您可能會使用<xref:System.Threading.ReaderWriterLockSlim>提供存取共用的資源的執行緒之間的合作式同步處理的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="50298-104">You might use a <xref:System.Threading.ReaderWriterLockSlim> in your application to provide cooperative synchronization among threads that access a shared resource.</span></span> <span data-ttu-id="50298-105">所持有的鎖定<xref:System.Threading.ReaderWriterLockSlim>本身。</span><span class="sxs-lookup"><span data-stu-id="50298-105">Locks are taken on the <xref:System.Threading.ReaderWriterLockSlim> itself.</span></span>  
  
 <span data-ttu-id="50298-106">因為任何執行緒的同步處理機制，您必須確定沒有任何執行緒略過所提供的鎖定<xref:System.Threading.ReaderWriterLockSlim>。</span><span class="sxs-lookup"><span data-stu-id="50298-106">As with any thread synchronization mechanism, you must ensure that no threads bypass the locking that is provided by <xref:System.Threading.ReaderWriterLockSlim>.</span></span> <span data-ttu-id="50298-107">若要確保這一個方法是設計封裝共用的資源的類別。</span><span class="sxs-lookup"><span data-stu-id="50298-107">One way to ensure this is to design a class that encapsulates the shared resource.</span></span> <span data-ttu-id="50298-108">這個類別會提供可存取私用的共用的資源，並使用私用成員<xref:System.Threading.ReaderWriterLockSlim>進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="50298-108">This class would provide members that access the private shared resource and that use a private <xref:System.Threading.ReaderWriterLockSlim> for synchronization.</span></span> <span data-ttu-id="50298-109">如需範例，請參閱的程式碼範例<xref:System.Threading.ReaderWriterLockSlim>類別。</span><span class="sxs-lookup"><span data-stu-id="50298-109">For an example, see the code example for the <xref:System.Threading.ReaderWriterLockSlim> class.</span></span> <span data-ttu-id="50298-110"><xref:System.Threading.ReaderWriterLockSlim>很有效率，足以用來同步處理個別物件。</span><span class="sxs-lookup"><span data-stu-id="50298-110"><xref:System.Threading.ReaderWriterLockSlim> is efficient enough to be used to synchronize individual objects.</span></span>  
  
 <span data-ttu-id="50298-111">最小化的持續時間的讀取和寫入作業將應用程式的結構。</span><span class="sxs-lookup"><span data-stu-id="50298-111">Structure your application to minimize the duration of read and write operations.</span></span> <span data-ttu-id="50298-112">長的寫入作業直接影響輸送量，因為獨佔寫入鎖定。</span><span class="sxs-lookup"><span data-stu-id="50298-112">Long write operations affect throughput directly because the write lock is exclusive.</span></span> <span data-ttu-id="50298-113">長時間的讀取作業封鎖等候寫入器，如果至少一個執行緒正在等候寫入權限，要求讀取權限的執行緒會被如此封鎖。</span><span class="sxs-lookup"><span data-stu-id="50298-113">Long read operations block waiting writers, and if at least one thread is waiting for write access, threads that request read access will be blocked as well.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50298-114">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]有兩個讀取器-寫入器鎖定，<xref:System.Threading.ReaderWriterLockSlim>和<xref:System.Threading.ReaderWriterLock>。</span><span class="sxs-lookup"><span data-stu-id="50298-114">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] has two reader-writer locks, <xref:System.Threading.ReaderWriterLockSlim> and <xref:System.Threading.ReaderWriterLock>.</span></span> <span data-ttu-id="50298-115"><xref:System.Threading.ReaderWriterLockSlim>建議所有新的開發。</span><span class="sxs-lookup"><span data-stu-id="50298-115"><xref:System.Threading.ReaderWriterLockSlim> is recommended for all new development.</span></span> <span data-ttu-id="50298-116"><xref:System.Threading.ReaderWriterLockSlim>類似於<xref:System.Threading.ReaderWriterLock>，但它已簡化遞迴以及升級和降級鎖定狀態的規則。</span><span class="sxs-lookup"><span data-stu-id="50298-116"><xref:System.Threading.ReaderWriterLockSlim> is similar to <xref:System.Threading.ReaderWriterLock>, but it has simplified rules for recursion and for upgrading and downgrading lock state.</span></span> <span data-ttu-id="50298-117"><xref:System.Threading.ReaderWriterLockSlim>可避免可能發生死結的許多情況。</span><span class="sxs-lookup"><span data-stu-id="50298-117"><xref:System.Threading.ReaderWriterLockSlim> avoids many cases of potential deadlock.</span></span> <span data-ttu-id="50298-118">此外，效能<xref:System.Threading.ReaderWriterLockSlim>明顯優於<xref:System.Threading.ReaderWriterLock>。</span><span class="sxs-lookup"><span data-stu-id="50298-118">In addition, the performance of <xref:System.Threading.ReaderWriterLockSlim> is significantly better than <xref:System.Threading.ReaderWriterLock>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50298-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50298-119">See Also</span></span>  
 <xref:System.Threading.ReaderWriterLockSlim>  
 <xref:System.Threading.ReaderWriterLock>  
 [<span data-ttu-id="50298-120">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="50298-120">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="50298-121">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="50298-121">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
