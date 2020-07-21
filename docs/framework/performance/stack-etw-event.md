---
title: 堆疊 ETW 事件
description: 閱讀堆疊 ETW 事件，這應該與其他事件搭配使用，以便在引發事件之後產生堆疊追蹤。
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
ms.openlocfilehash: cab496615c4ef17831895b72c8987917e3c06e77
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474133"
---
# <a name="stack-etw-event"></a><span data-ttu-id="4adae-103">堆疊 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="4adae-103">Stack ETW Event</span></span>
<span data-ttu-id="4adae-104">堆疊事件應該搭配其他事件一起使用，以在引發事件之後產生堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="4adae-104">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="4adae-105">它會在啟用執行階段提供者時記錄。</span><span class="sxs-lookup"><span data-stu-id="4adae-105">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="4adae-106">這是非常高頻率的事件，因為每當引發另一個執行階段事件時，就會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="4adae-106">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="4adae-107">基於這個理由，我們建議您小心使用此事件。</span><span class="sxs-lookup"><span data-stu-id="4adae-107">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="4adae-108">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="4adae-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="4adae-109">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="4adae-109">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="4adae-110">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="4adae-110">Keyword for raising the event</span></span>|<span data-ttu-id="4adae-111">層級</span><span class="sxs-lookup"><span data-stu-id="4adae-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="4adae-112">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="4adae-112">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="4adae-113">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="4adae-113">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="4adae-114">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="4adae-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="4adae-115">事件</span><span class="sxs-lookup"><span data-stu-id="4adae-115">Event</span></span>|<span data-ttu-id="4adae-116">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="4adae-116">Event ID</span></span>|<span data-ttu-id="4adae-117">引發的時機</span><span class="sxs-lookup"><span data-stu-id="4adae-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="4adae-118">82</span><span class="sxs-lookup"><span data-stu-id="4adae-118">82</span></span>|<span data-ttu-id="4adae-119">搭配其他事件，來產生事件之後的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="4adae-119">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="4adae-120">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="4adae-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="4adae-121">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="4adae-121">Field name</span></span>|<span data-ttu-id="4adae-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="4adae-122">Data Type</span></span>|<span data-ttu-id="4adae-123">描述</span><span class="sxs-lookup"><span data-stu-id="4adae-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="4adae-124">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="4adae-124">ClrInstanceID</span></span>|<span data-ttu-id="4adae-125">win:Uint16</span><span class="sxs-lookup"><span data-stu-id="4adae-125">win:Uint16</span></span>|<span data-ttu-id="4adae-126">唯一執行階段識別項。</span><span class="sxs-lookup"><span data-stu-id="4adae-126">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="4adae-127">Reserved1</span><span class="sxs-lookup"><span data-stu-id="4adae-127">Reserved1</span></span>|<span data-ttu-id="4adae-128">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="4adae-128">win:UInt8</span></span>|<span data-ttu-id="4adae-129">已保留。</span><span class="sxs-lookup"><span data-stu-id="4adae-129">Reserved.</span></span>|  
|<span data-ttu-id="4adae-130">Reserved2</span><span class="sxs-lookup"><span data-stu-id="4adae-130">Reserved2</span></span>|<span data-ttu-id="4adae-131">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="4adae-131">win:UInt8</span></span>|<span data-ttu-id="4adae-132">已保留。</span><span class="sxs-lookup"><span data-stu-id="4adae-132">Reserved.</span></span>|  
|<span data-ttu-id="4adae-133">FrameCount</span><span class="sxs-lookup"><span data-stu-id="4adae-133">FrameCount</span></span>|<span data-ttu-id="4adae-134">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="4adae-134">win:UInt32</span></span>|<span data-ttu-id="4adae-135">堆疊追蹤裡的框架數。</span><span class="sxs-lookup"><span data-stu-id="4adae-135">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="4adae-136">Stack</span><span class="sxs-lookup"><span data-stu-id="4adae-136">Stack</span></span>|<span data-ttu-id="4adae-137">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="4adae-137">win:Pointer</span></span>|<span data-ttu-id="4adae-138">指令指標的資料行。</span><span class="sxs-lookup"><span data-stu-id="4adae-138">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4adae-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4adae-139">See also</span></span>

- [<span data-ttu-id="4adae-140">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="4adae-140">CLR ETW Events</span></span>](clr-etw-events.md)
