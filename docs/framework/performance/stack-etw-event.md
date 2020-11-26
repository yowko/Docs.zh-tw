---
title: 堆疊 ETW 事件
description: 閱讀堆疊 ETW 事件的相關資訊，此事件應該與其他事件一起使用，以在引發事件之後產生堆疊追蹤。
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
ms.openlocfilehash: 3b890e587abd5cb1b7315fe41897f24638fd4604
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236204"
---
# <a name="stack-etw-event"></a><span data-ttu-id="36fe8-103">堆疊 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="36fe8-103">Stack ETW Event</span></span>

<span data-ttu-id="36fe8-104">堆疊事件應該搭配其他事件一起使用，以在引發事件之後產生堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="36fe8-104">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="36fe8-105">它會在啟用執行階段提供者時記錄。</span><span class="sxs-lookup"><span data-stu-id="36fe8-105">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="36fe8-106">這是非常高頻率的事件，因為每當引發另一個執行階段事件時，就會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="36fe8-106">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="36fe8-107">基於這個理由，我們建議您小心使用此事件。</span><span class="sxs-lookup"><span data-stu-id="36fe8-107">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="36fe8-108">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="36fe8-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="36fe8-109">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="36fe8-109">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="36fe8-110">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="36fe8-110">Keyword for raising the event</span></span>|<span data-ttu-id="36fe8-111">層級</span><span class="sxs-lookup"><span data-stu-id="36fe8-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="36fe8-112">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="36fe8-112">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="36fe8-113">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="36fe8-113">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="36fe8-114">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="36fe8-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="36fe8-115">事件</span><span class="sxs-lookup"><span data-stu-id="36fe8-115">Event</span></span>|<span data-ttu-id="36fe8-116">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="36fe8-116">Event ID</span></span>|<span data-ttu-id="36fe8-117">引發的時機</span><span class="sxs-lookup"><span data-stu-id="36fe8-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="36fe8-118">82</span><span class="sxs-lookup"><span data-stu-id="36fe8-118">82</span></span>|<span data-ttu-id="36fe8-119">搭配其他事件，來產生事件之後的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="36fe8-119">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="36fe8-120">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="36fe8-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="36fe8-121">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="36fe8-121">Field name</span></span>|<span data-ttu-id="36fe8-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="36fe8-122">Data Type</span></span>|<span data-ttu-id="36fe8-123">描述</span><span class="sxs-lookup"><span data-stu-id="36fe8-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="36fe8-124">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="36fe8-124">ClrInstanceID</span></span>|<span data-ttu-id="36fe8-125">win:Uint16</span><span class="sxs-lookup"><span data-stu-id="36fe8-125">win:Uint16</span></span>|<span data-ttu-id="36fe8-126">唯一執行階段識別項。</span><span class="sxs-lookup"><span data-stu-id="36fe8-126">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="36fe8-127">Reserved1</span><span class="sxs-lookup"><span data-stu-id="36fe8-127">Reserved1</span></span>|<span data-ttu-id="36fe8-128">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="36fe8-128">win:UInt8</span></span>|<span data-ttu-id="36fe8-129">保留的。</span><span class="sxs-lookup"><span data-stu-id="36fe8-129">Reserved.</span></span>|  
|<span data-ttu-id="36fe8-130">Reserved2</span><span class="sxs-lookup"><span data-stu-id="36fe8-130">Reserved2</span></span>|<span data-ttu-id="36fe8-131">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="36fe8-131">win:UInt8</span></span>|<span data-ttu-id="36fe8-132">保留的。</span><span class="sxs-lookup"><span data-stu-id="36fe8-132">Reserved.</span></span>|  
|<span data-ttu-id="36fe8-133">FrameCount</span><span class="sxs-lookup"><span data-stu-id="36fe8-133">FrameCount</span></span>|<span data-ttu-id="36fe8-134">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="36fe8-134">win:UInt32</span></span>|<span data-ttu-id="36fe8-135">堆疊追蹤裡的框架數。</span><span class="sxs-lookup"><span data-stu-id="36fe8-135">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="36fe8-136">Stack</span><span class="sxs-lookup"><span data-stu-id="36fe8-136">Stack</span></span>|<span data-ttu-id="36fe8-137">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="36fe8-137">win:Pointer</span></span>|<span data-ttu-id="36fe8-138">指令指標的資料行。</span><span class="sxs-lookup"><span data-stu-id="36fe8-138">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="36fe8-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="36fe8-139">See also</span></span>

- [<span data-ttu-id="36fe8-140">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="36fe8-140">CLR ETW Events</span></span>](clr-etw-events.md)
