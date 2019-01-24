---
title: 爭用 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 90beb1487581ff4c031d6f10fb613430207dc026
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575563"
---
# <a name="contention-etw-events"></a><span data-ttu-id="95aca-102">爭用 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="95aca-102">Contention ETW Events</span></span>
<span data-ttu-id="95aca-103">只要爭用執行階段所使用的 <xref:System.Threading.Monitor?displayProperty=nameWithType> 鎖定或原生鎖定，就會引發爭用事件。</span><span class="sxs-lookup"><span data-stu-id="95aca-103">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="95aca-104">如果某個執行緒等待鎖定，而另一個執行緒擁有該鎖定，則會發生爭用。</span><span class="sxs-lookup"><span data-stu-id="95aca-104">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>  
  
 <span data-ttu-id="95aca-105">下表顯示引發爭用事件的關鍵字以及事件層級。</span><span class="sxs-lookup"><span data-stu-id="95aca-105">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="95aca-106">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="95aca-106">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="95aca-107">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="95aca-107">Keyword for raising the event</span></span>|<span data-ttu-id="95aca-108">層級</span><span class="sxs-lookup"><span data-stu-id="95aca-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="95aca-109">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="95aca-109">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="95aca-110">告知性 (4)</span><span class="sxs-lookup"><span data-stu-id="95aca-110">Informational (4)</span></span>|  
  
 <span data-ttu-id="95aca-111">下表顯示事件資訊。</span><span class="sxs-lookup"><span data-stu-id="95aca-111">The following table shows event information.</span></span>  
  
|<span data-ttu-id="95aca-112">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="95aca-112">Event</span></span>|<span data-ttu-id="95aca-113">事件 ID</span><span class="sxs-lookup"><span data-stu-id="95aca-113">Event ID</span></span>|<span data-ttu-id="95aca-114">引發的時機</span><span class="sxs-lookup"><span data-stu-id="95aca-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|<span data-ttu-id="95aca-115">81</span><span class="sxs-lookup"><span data-stu-id="95aca-115">81</span></span>|<span data-ttu-id="95aca-116">爭用開始。</span><span class="sxs-lookup"><span data-stu-id="95aca-116">Contention starts.</span></span> <span data-ttu-id="95aca-117">此事件未包含執行緒等候取得鎖定之前的微調時間量；只有在執行緒等候取得鎖定時才會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="95aca-117">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|  
|`ContentionStop`|<span data-ttu-id="95aca-118">81</span><span class="sxs-lookup"><span data-stu-id="95aca-118">81</span></span>|<span data-ttu-id="95aca-119">爭用結束。</span><span class="sxs-lookup"><span data-stu-id="95aca-119">Contention ends.</span></span>|  
  
 <span data-ttu-id="95aca-120">下表顯示事件資料。</span><span class="sxs-lookup"><span data-stu-id="95aca-120">The following table shows event data.</span></span>  
  
|<span data-ttu-id="95aca-121">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="95aca-121">Field name</span></span>|<span data-ttu-id="95aca-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="95aca-122">Data type</span></span>|<span data-ttu-id="95aca-123">描述</span><span class="sxs-lookup"><span data-stu-id="95aca-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="95aca-124">旗標</span><span class="sxs-lookup"><span data-stu-id="95aca-124">Flags</span></span>|<span data-ttu-id="95aca-125">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="95aca-125">win:UInt8</span></span>|<span data-ttu-id="95aca-126">0 表示 Managed；1 表示原生。</span><span class="sxs-lookup"><span data-stu-id="95aca-126">0 for managed; 1 for native.</span></span>|  
|<span data-ttu-id="95aca-127">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="95aca-127">ClrInstanceID</span></span>|<span data-ttu-id="95aca-128">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="95aca-128">win:UInt16</span></span>|<span data-ttu-id="95aca-129">CLR 執行個體的唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="95aca-129">Unique ID for the instance of CLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95aca-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="95aca-130">See also</span></span>
- [<span data-ttu-id="95aca-131">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="95aca-131">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
