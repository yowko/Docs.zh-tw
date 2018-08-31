---
title: 排程執行緒
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a382dbea239b66e60d666a0e2e7add01d6d7bd54
ms.sourcegitcommit: c66ba2df2d2ecfb214f85ee0687d298e4941c1a8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2018
ms.locfileid: "42753587"
---
# <a name="scheduling-threads"></a><span data-ttu-id="31526-102">排程執行緒</span><span class="sxs-lookup"><span data-stu-id="31526-102">Scheduling threads</span></span>

<span data-ttu-id="31526-103">每個執行緒都擁有一個指派的執行緒優先權。</span><span class="sxs-lookup"><span data-stu-id="31526-103">Every thread has a thread priority assigned to it.</span></span> <span data-ttu-id="31526-104">Common Language Runtime 中建立的執行緒，一開始會被指派 <xref:System.Threading.ThreadPriority.Normal?displayProperty=nameWithType> 的優先權。</span><span class="sxs-lookup"><span data-stu-id="31526-104">Threads created within the common language runtime are initially assigned the priority of <xref:System.Threading.ThreadPriority.Normal?displayProperty=nameWithType>.</span></span> <span data-ttu-id="31526-105">建立在執行階段之外的執行緒，在它們進入受控環境之前，會保留它們所擁有的優先權。</span><span class="sxs-lookup"><span data-stu-id="31526-105">Threads created outside the runtime retain the priority they had before they entered the managed environment.</span></span> <span data-ttu-id="31526-106">您可以使用 <xref:System.Threading.Thread.Priority?displayProperty=nameWithType> 屬性取得或設定任何執行緒的優先權。</span><span class="sxs-lookup"><span data-stu-id="31526-106">You can get or set the priority of any thread with the <xref:System.Threading.Thread.Priority?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="31526-107">執行緒會根據它們的優先權排定執行。</span><span class="sxs-lookup"><span data-stu-id="31526-107">Threads are scheduled for execution based on their priority.</span></span> <span data-ttu-id="31526-108">即使執行緒在執行階段內執行，所有的執行緒都會由作業系統指派處理器時間配量。</span><span class="sxs-lookup"><span data-stu-id="31526-108">Even though threads are executing within the runtime, all threads are assigned processor time slices by the operating system.</span></span> <span data-ttu-id="31526-109">用來決定執行緒執行順序之排程演算法的詳細資料會隨著每個作業系統而不同。</span><span class="sxs-lookup"><span data-stu-id="31526-109">The details of the scheduling algorithm used to determine the order in which threads are executed varies with each operating system.</span></span> <span data-ttu-id="31526-110">在某些作業系統上，(在可以執行的執行緒中) 具有最高優先權的執行緒一律會排定為第一個執行。</span><span class="sxs-lookup"><span data-stu-id="31526-110">Under some operating systems, the thread with the highest priority (of those threads that can be executed) is always scheduled to run first.</span></span> <span data-ttu-id="31526-111">如果具有相同優先權的多個執行緒都可使用，排程器會針對該優先權不斷循環執行緒，讓每個執行緒在固定的時間配量中執行。</span><span class="sxs-lookup"><span data-stu-id="31526-111">If multiple threads with the same priority are all available, the scheduler cycles through the threads at that priority, giving each thread a fixed time slice in which to execute.</span></span> <span data-ttu-id="31526-112">只要具有高優先權的執行緒可以執行，低優先權的執行緒就不會執行。</span><span class="sxs-lookup"><span data-stu-id="31526-112">As long as a thread with a higher priority is available to run, lower priority threads do not get to execute.</span></span> <span data-ttu-id="31526-113">當指定的優先權沒有可執行的執行緒時，排程器將移至下一個較低的優先順序，並排程該優先順序的執行緒執行。</span><span class="sxs-lookup"><span data-stu-id="31526-113">When there are no more runnable threads at a given priority, the scheduler moves to the next lower priority and schedules the threads at that priority for execution.</span></span> <span data-ttu-id="31526-114">如果高優先順序的執行緒變成可以執行，會佔用低優先權的執行緒並允許重新執行高優先權的執行緒。</span><span class="sxs-lookup"><span data-stu-id="31526-114">If a higher priority thread becomes runnable, the lower priority thread is preempted and the higher priority thread is allowed to execute once again.</span></span> <span data-ttu-id="31526-115">除此之外，因為應用程式的使用者介面會在前景與背景之間移動，所以作業系統可以動態調整執行緒的優先權。</span><span class="sxs-lookup"><span data-stu-id="31526-115">On top of all that, the operating system can also adjust thread priorities dynamically as an application's user interface is moved between foreground and background.</span></span> <span data-ttu-id="31526-116">其他作業系統可能會選擇使用不同的排程演算法。</span><span class="sxs-lookup"><span data-stu-id="31526-116">Other operating systems might choose to use a different scheduling algorithm.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31526-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="31526-117">See Also</span></span>  
 [<span data-ttu-id="31526-118">使用執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="31526-118">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 [<span data-ttu-id="31526-119">Windows 中的 Managed 和 Unmanaged 執行緒處理</span><span class="sxs-lookup"><span data-stu-id="31526-119">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)
