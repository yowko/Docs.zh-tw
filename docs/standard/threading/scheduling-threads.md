---
title: "排程執行緒"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2e1fb7d61b8e250884b2c57cad8c5106bc77787a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="scheduling-threads"></a><span data-ttu-id="ee171-102">排程執行緒</span><span class="sxs-lookup"><span data-stu-id="ee171-102">Scheduling Threads</span></span>
<span data-ttu-id="ee171-103">每個執行緒有指派給它的執行緒優先順序。</span><span class="sxs-lookup"><span data-stu-id="ee171-103">Every thread has a thread priority assigned to it.</span></span> <span data-ttu-id="ee171-104">Common language runtime 中建立的執行緒一開始會被指派優先權**ThreadPriority.Normal**。</span><span class="sxs-lookup"><span data-stu-id="ee171-104">Threads created within the common language runtime are initially assigned the priority of **ThreadPriority.Normal**.</span></span> <span data-ttu-id="ee171-105">執行階段外部建立的執行緒會保留它們進入 managed 的環境之前，原本的優先權。</span><span class="sxs-lookup"><span data-stu-id="ee171-105">Threads created outside the runtime retain the priority they had before they entered the managed environment.</span></span> <span data-ttu-id="ee171-106">您可以取得或設定與任何執行緒的優先權**Thread.Priority**屬性。</span><span class="sxs-lookup"><span data-stu-id="ee171-106">You can get or set the priority of any thread with the **Thread.Priority** property.</span></span>  
  
 <span data-ttu-id="ee171-107">執行緒都會排定執行會依據其優先順序。</span><span class="sxs-lookup"><span data-stu-id="ee171-107">Threads are scheduled for execution based on their priority.</span></span> <span data-ttu-id="ee171-108">即使在執行階段內執行的執行緒，所有執行緒會由作業系統都指派處理器時間配量。</span><span class="sxs-lookup"><span data-stu-id="ee171-108">Even though threads are executing within the runtime, all threads are assigned processor time slices by the operating system.</span></span> <span data-ttu-id="ee171-109">用來決定執行緒執行的順序的排程演算法的詳細資料會隨著每個作業系統。</span><span class="sxs-lookup"><span data-stu-id="ee171-109">The details of the scheduling algorithm used to determine the order in which threads are executed varies with each operating system.</span></span> <span data-ttu-id="ee171-110">在某些作業系統上，具有最高優先權執行緒可以執行） （屬於執行緒一定會排定執行第一次。</span><span class="sxs-lookup"><span data-stu-id="ee171-110">Under some operating systems, the thread with the highest priority (of those threads that can be executed) is always scheduled to run first.</span></span> <span data-ttu-id="ee171-111">如果優先權相同的多個執行緒都可供，排程器不斷循環的執行緒的優先權，讓每個執行緒執行所在的固定的時間配量。</span><span class="sxs-lookup"><span data-stu-id="ee171-111">If multiple threads with the same priority are all available, the scheduler cycles through the threads at that priority, giving each thread a fixed time slice in which to execute.</span></span> <span data-ttu-id="ee171-112">為具有較高優先順序的執行緒可執行，則不會執行較低優先權的執行緒。</span><span class="sxs-lookup"><span data-stu-id="ee171-112">As long as a thread with a higher priority is available to run, lower priority threads do not get to execute.</span></span> <span data-ttu-id="ee171-113">當有沒有其他可執行的執行緒在指定的優先順序時，排程器將移到下一個較低的優先順序，並排程上執行的該優先順序的執行緒。</span><span class="sxs-lookup"><span data-stu-id="ee171-113">When there are no more runnable threads at a given priority, the scheduler moves to the next lower priority and schedules the threads at that priority for execution.</span></span> <span data-ttu-id="ee171-114">如果高優先順序的執行緒成為可執行，會佔用較低優先順序的執行緒，高優先順序的執行緒，允許一次重新執行。</span><span class="sxs-lookup"><span data-stu-id="ee171-114">If a higher priority thread becomes runnable, the lower priority thread is preempted and the higher priority thread is allowed to execute once again.</span></span> <span data-ttu-id="ee171-115">在頂端，作業系統也可以調整執行緒的優先順序動態前景與背景之間移動應用程式的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="ee171-115">On top of all that, the operating system can also adjust thread priorities dynamically as an application's user interface is moved between foreground and background.</span></span> <span data-ttu-id="ee171-116">其他作業系統可能會選擇使用不同的排程演算法。</span><span class="sxs-lookup"><span data-stu-id="ee171-116">Other operating systems might choose to use a different scheduling algorithm.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee171-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee171-117">See Also</span></span>  
 [<span data-ttu-id="ee171-118">使用執行緒和執行緒處理</span><span class="sxs-lookup"><span data-stu-id="ee171-118">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 [<span data-ttu-id="ee171-119">Windows 中的 Managed 和 Unmanaged 執行緒處理</span><span class="sxs-lookup"><span data-stu-id="ee171-119">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)
