---
title: Reader-Writer 鎖定
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ReaderWriterLock class, about ReaderWriterLock class
- threading [.NET Framework], ReaderWriterLock class
ms.assetid: 8c71acf2-2c18-4f4d-8cdb-0728639265fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8be9b4eef30333fbbdc26915635d17157176d6fc
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45640929"
---
# <a name="reader-writer-locks"></a><span data-ttu-id="82b32-102">Reader-Writer 鎖定</span><span class="sxs-lookup"><span data-stu-id="82b32-102">Reader-Writer Locks</span></span>
<span data-ttu-id="82b32-103"><xref:System.Threading.ReaderWriterLockSlim> 類別可讓多個執行緒同時讀取資源，但是會要求執行緒等候獨佔鎖定，才能寫入至資源。</span><span class="sxs-lookup"><span data-stu-id="82b32-103">The <xref:System.Threading.ReaderWriterLockSlim> class enables multiple threads to read a resource concurrently, but requires a thread to wait for an exclusive lock in order to write to the resource.</span></span>  
  
 <span data-ttu-id="82b32-104">您可能會在您的應用程式中使用 <xref:System.Threading.ReaderWriterLockSlim>，以提供存取共用資源之執行緒之間的合作式同步處理。</span><span class="sxs-lookup"><span data-stu-id="82b32-104">You might use a <xref:System.Threading.ReaderWriterLockSlim> in your application to provide cooperative synchronization among threads that access a shared resource.</span></span> <span data-ttu-id="82b32-105">鎖定會在 <xref:System.Threading.ReaderWriterLockSlim> 本身上採用。</span><span class="sxs-lookup"><span data-stu-id="82b32-105">Locks are taken on the <xref:System.Threading.ReaderWriterLockSlim> itself.</span></span>  
  
 <span data-ttu-id="82b32-106">因為任何執行緒的同步處理機制，您必須確定沒有任何執行緒略過 <xref:System.Threading.ReaderWriterLockSlim> 所提供的鎖定。</span><span class="sxs-lookup"><span data-stu-id="82b32-106">As with any thread synchronization mechanism, you must ensure that no threads bypass the locking that is provided by <xref:System.Threading.ReaderWriterLockSlim>.</span></span> <span data-ttu-id="82b32-107">要確保這麼做的一個方法，就是設計一個會封裝共用資源的類別。</span><span class="sxs-lookup"><span data-stu-id="82b32-107">One way to ensure this is to design a class that encapsulates the shared resource.</span></span> <span data-ttu-id="82b32-108">這個類別會提供成員存取私用的共用資源，以及使用私用的 <xref:System.Threading.ReaderWriterLockSlim> 進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="82b32-108">This class would provide members that access the private shared resource and that use a private <xref:System.Threading.ReaderWriterLockSlim> for synchronization.</span></span> <span data-ttu-id="82b32-109">如需範例，請參閱 <xref:System.Threading.ReaderWriterLockSlim> 類別的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="82b32-109">For an example, see the code example for the <xref:System.Threading.ReaderWriterLockSlim> class.</span></span> <span data-ttu-id="82b32-110"><xref:System.Threading.ReaderWriterLockSlim> 很有效率，足以用來同步處理個別物件。</span><span class="sxs-lookup"><span data-stu-id="82b32-110"><xref:System.Threading.ReaderWriterLockSlim> is efficient enough to be used to synchronize individual objects.</span></span>  
  
 <span data-ttu-id="82b32-111">建置您應用程式的結構，以最小化讀取及寫入作業的持續時間。</span><span class="sxs-lookup"><span data-stu-id="82b32-111">Structure your application to minimize the duration of read and write operations.</span></span> <span data-ttu-id="82b32-112">長時間的寫入作業會直接影響輸送量，因為寫入是獨佔鎖定。</span><span class="sxs-lookup"><span data-stu-id="82b32-112">Long write operations affect throughput directly because the write lock is exclusive.</span></span> <span data-ttu-id="82b32-113">長時間的讀取作業會封鎖等候寫入器，且如果至少有一個執行緒正在等候寫入權限，要求讀取權限的執行緒也將會被封鎖。</span><span class="sxs-lookup"><span data-stu-id="82b32-113">Long read operations block waiting writers, and if at least one thread is waiting for write access, threads that request read access will be blocked as well.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82b32-114">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 擁有 <xref:System.Threading.ReaderWriterLockSlim> 和 <xref:System.Threading.ReaderWriterLock> 這兩個 Reader-Writer 鎖定。</span><span class="sxs-lookup"><span data-stu-id="82b32-114">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] has two reader-writer locks, <xref:System.Threading.ReaderWriterLockSlim> and <xref:System.Threading.ReaderWriterLock>.</span></span> <span data-ttu-id="82b32-115">建議針對所有新的開發使用 <xref:System.Threading.ReaderWriterLockSlim>。</span><span class="sxs-lookup"><span data-stu-id="82b32-115"><xref:System.Threading.ReaderWriterLockSlim> is recommended for all new development.</span></span> <span data-ttu-id="82b32-116"><xref:System.Threading.ReaderWriterLockSlim> 類似於 <xref:System.Threading.ReaderWriterLock>，但是它有遞迴以及升級和降級鎖定狀態的簡化規則。</span><span class="sxs-lookup"><span data-stu-id="82b32-116"><xref:System.Threading.ReaderWriterLockSlim> is similar to <xref:System.Threading.ReaderWriterLock>, but it has simplified rules for recursion and for upgrading and downgrading lock state.</span></span> <span data-ttu-id="82b32-117"><xref:System.Threading.ReaderWriterLockSlim> 可避免可能發生死結的許多情況。</span><span class="sxs-lookup"><span data-stu-id="82b32-117"><xref:System.Threading.ReaderWriterLockSlim> avoids many cases of potential deadlock.</span></span> <span data-ttu-id="82b32-118">此外，<xref:System.Threading.ReaderWriterLockSlim> 的效能明顯優於 <xref:System.Threading.ReaderWriterLock>。</span><span class="sxs-lookup"><span data-stu-id="82b32-118">In addition, the performance of <xref:System.Threading.ReaderWriterLockSlim> is significantly better than <xref:System.Threading.ReaderWriterLock>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82b32-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82b32-119">See also</span></span>

- <xref:System.Threading.ReaderWriterLockSlim>  
- <xref:System.Threading.ReaderWriterLock>  
- [<span data-ttu-id="82b32-120">執行緒處理</span><span class="sxs-lookup"><span data-stu-id="82b32-120">Threading</span></span>](../../../docs/standard/threading/index.md)  
- [<span data-ttu-id="82b32-121">執行緒物件和功能</span><span class="sxs-lookup"><span data-stu-id="82b32-121">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)
