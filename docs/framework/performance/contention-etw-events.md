---
title: 爭用 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3487b67ea49cecfd0da2b5b3f993ea54d562145d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397516"
---
# <a name="contention-etw-events"></a><span data-ttu-id="bb1fa-102">爭用 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="bb1fa-102">Contention ETW Events</span></span>
<span data-ttu-id="bb1fa-103">只要爭用執行階段所使用的 <xref:System.Threading.Monitor?displayProperty=nameWithType> 鎖定或原生鎖定，就會引發爭用事件。</span><span class="sxs-lookup"><span data-stu-id="bb1fa-103">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="bb1fa-104">如果某個執行緒等待鎖定，而另一個執行緒擁有該鎖定，則會發生爭用。</span><span class="sxs-lookup"><span data-stu-id="bb1fa-104">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>  
  
 <span data-ttu-id="bb1fa-105">下表顯示引發爭用事件的關鍵字以及事件層級。</span><span class="sxs-lookup"><span data-stu-id="bb1fa-105">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="bb1fa-106">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="bb1fa-106">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="bb1fa-107">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="bb1fa-107">Keyword for raising the event</span></span>|<span data-ttu-id="bb1fa-108">層級</span><span class="sxs-lookup"><span data-stu-id="bb1fa-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="bb1fa-109">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="bb1fa-109">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="bb1fa-110">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="bb1fa-110">Informational (4)</span></span>|  
  
 <span data-ttu-id="bb1fa-111">下表顯示事件資訊。</span><span class="sxs-lookup"><span data-stu-id="bb1fa-111">The following table shows event information.</span></span>  
  
|<span data-ttu-id="bb1fa-112">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="bb1fa-112">Event</span></span>|<span data-ttu-id="bb1fa-113">事件 ID</span><span class="sxs-lookup"><span data-stu-id="bb1fa-113">Event ID</span></span>|<span data-ttu-id="bb1fa-114">引發的時機</span><span class="sxs-lookup"><span data-stu-id="bb1fa-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|<span data-ttu-id="bb1fa-115">81</span><span class="sxs-lookup"><span data-stu-id="bb1fa-115">81</span></span>|<span data-ttu-id="bb1fa-116">爭用開始。</span><span class="sxs-lookup"><span data-stu-id="bb1fa-116">Contention starts.</span></span> <span data-ttu-id="bb1fa-117">此事件未包含執行緒等候取得鎖定之前的微調時間量；只有在執行緒等候取得鎖定時才會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="bb1fa-117">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|  
|`ContentionStop`|<span data-ttu-id="bb1fa-118">81</span><span class="sxs-lookup"><span data-stu-id="bb1fa-118">81</span></span>|<span data-ttu-id="bb1fa-119">爭用結束。</span><span class="sxs-lookup"><span data-stu-id="bb1fa-119">Contention ends.</span></span>|  
  
 <span data-ttu-id="bb1fa-120">下表顯示事件資料。</span><span class="sxs-lookup"><span data-stu-id="bb1fa-120">The following table shows event data.</span></span>  
  
|<span data-ttu-id="bb1fa-121">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="bb1fa-121">Field name</span></span>|<span data-ttu-id="bb1fa-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="bb1fa-122">Data type</span></span>|<span data-ttu-id="bb1fa-123">描述</span><span class="sxs-lookup"><span data-stu-id="bb1fa-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="bb1fa-124">旗標</span><span class="sxs-lookup"><span data-stu-id="bb1fa-124">Flags</span></span>|<span data-ttu-id="bb1fa-125">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="bb1fa-125">win:UInt8</span></span>|<span data-ttu-id="bb1fa-126">0 表示 Managed；1 表示原生。</span><span class="sxs-lookup"><span data-stu-id="bb1fa-126">0 for managed; 1 for native.</span></span>|  
|<span data-ttu-id="bb1fa-127">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="bb1fa-127">ClrInstanceID</span></span>|<span data-ttu-id="bb1fa-128">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="bb1fa-128">win:UInt16</span></span>|<span data-ttu-id="bb1fa-129">CLR 執行個體的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="bb1fa-129">Unique ID for the instance of CLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bb1fa-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb1fa-130">See Also</span></span>  
 [<span data-ttu-id="bb1fa-131">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="bb1fa-131">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
