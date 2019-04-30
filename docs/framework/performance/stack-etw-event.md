---
title: 堆疊 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7cba2bd1dd5b83e29c7a6c192a1a7e5e2d33ecc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949145"
---
# <a name="stack-etw-event"></a><span data-ttu-id="633cc-102">堆疊 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="633cc-102">Stack ETW Event</span></span>
<span data-ttu-id="633cc-103">堆疊事件應該搭配其他事件一起使用，以在引發事件之後產生堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="633cc-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="633cc-104">它會在啟用執行階段提供者時記錄。</span><span class="sxs-lookup"><span data-stu-id="633cc-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="633cc-105">這是非常高頻率的事件，因為每當引發另一個執行階段事件時，就會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="633cc-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="633cc-106">基於這個理由，我們建議您小心使用此事件。</span><span class="sxs-lookup"><span data-stu-id="633cc-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="633cc-107">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="633cc-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="633cc-108">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="633cc-108">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="633cc-109">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="633cc-109">Keyword for raising the event</span></span>|<span data-ttu-id="633cc-110">層級</span><span class="sxs-lookup"><span data-stu-id="633cc-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="633cc-111">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="633cc-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="633cc-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="633cc-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="633cc-113">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="633cc-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="633cc-114">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="633cc-114">Event</span></span>|<span data-ttu-id="633cc-115">事件 ID</span><span class="sxs-lookup"><span data-stu-id="633cc-115">Event ID</span></span>|<span data-ttu-id="633cc-116">引發的時機</span><span class="sxs-lookup"><span data-stu-id="633cc-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="633cc-117">82</span><span class="sxs-lookup"><span data-stu-id="633cc-117">82</span></span>|<span data-ttu-id="633cc-118">搭配其他事件，來產生事件之後的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="633cc-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="633cc-119">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="633cc-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="633cc-120">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="633cc-120">Field name</span></span>|<span data-ttu-id="633cc-121">資料類型</span><span class="sxs-lookup"><span data-stu-id="633cc-121">Data Type</span></span>|<span data-ttu-id="633cc-122">描述</span><span class="sxs-lookup"><span data-stu-id="633cc-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="633cc-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="633cc-123">ClrInstanceID</span></span>|<span data-ttu-id="633cc-124">win:Uint16</span><span class="sxs-lookup"><span data-stu-id="633cc-124">win:Uint16</span></span>|<span data-ttu-id="633cc-125">唯一執行階段識別項。</span><span class="sxs-lookup"><span data-stu-id="633cc-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="633cc-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="633cc-126">Reserved1</span></span>|<span data-ttu-id="633cc-127">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="633cc-127">win:UInt8</span></span>|<span data-ttu-id="633cc-128">保留的。</span><span class="sxs-lookup"><span data-stu-id="633cc-128">Reserved.</span></span>|  
|<span data-ttu-id="633cc-129">Reserved2</span><span class="sxs-lookup"><span data-stu-id="633cc-129">Reserved2</span></span>|<span data-ttu-id="633cc-130">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="633cc-130">win:UInt8</span></span>|<span data-ttu-id="633cc-131">保留的。</span><span class="sxs-lookup"><span data-stu-id="633cc-131">Reserved.</span></span>|  
|<span data-ttu-id="633cc-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="633cc-132">FrameCount</span></span>|<span data-ttu-id="633cc-133">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="633cc-133">win:UInt32</span></span>|<span data-ttu-id="633cc-134">堆疊追蹤裡的框架數。</span><span class="sxs-lookup"><span data-stu-id="633cc-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="633cc-135">堆疊</span><span class="sxs-lookup"><span data-stu-id="633cc-135">Stack</span></span>|<span data-ttu-id="633cc-136">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="633cc-136">win:Pointer</span></span>|<span data-ttu-id="633cc-137">指令指標的資料行。</span><span class="sxs-lookup"><span data-stu-id="633cc-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="633cc-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="633cc-138">See also</span></span>

- [<span data-ttu-id="633cc-139">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="633cc-139">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
