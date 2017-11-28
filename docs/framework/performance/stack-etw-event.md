---
title: "堆疊 ETW 事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 55219fe755f49b6edbd3b53cc686bf4f9087aa08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="stack-etw-event"></a><span data-ttu-id="0fc8d-102">堆疊 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="0fc8d-102">Stack ETW Event</span></span>
<span data-ttu-id="0fc8d-103">堆疊事件應該搭配其他事件一起使用，以在引發事件之後產生堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="0fc8d-104">它會在啟用執行階段提供者時記錄。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="0fc8d-105">這是非常高頻率的事件，因為每當引發另一個執行階段事件時，就會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="0fc8d-106">基於這個理由，我們建議您小心使用此事件。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="0fc8d-107">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="0fc8d-108">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-108">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="0fc8d-109">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="0fc8d-109">Keyword for raising the event</span></span>|<span data-ttu-id="0fc8d-110">層級</span><span class="sxs-lookup"><span data-stu-id="0fc8d-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="0fc8d-111">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="0fc8d-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="0fc8d-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="0fc8d-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="0fc8d-113">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="0fc8d-114">事件</span><span class="sxs-lookup"><span data-stu-id="0fc8d-114">Event</span></span>|<span data-ttu-id="0fc8d-115">事件 ID</span><span class="sxs-lookup"><span data-stu-id="0fc8d-115">Event ID</span></span>|<span data-ttu-id="0fc8d-116">引發的時機</span><span class="sxs-lookup"><span data-stu-id="0fc8d-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="0fc8d-117">82</span><span class="sxs-lookup"><span data-stu-id="0fc8d-117">82</span></span>|<span data-ttu-id="0fc8d-118">搭配其他事件，來產生事件之後的堆疊追蹤。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="0fc8d-119">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="0fc8d-120">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="0fc8d-120">Field name</span></span>|<span data-ttu-id="0fc8d-121">資料類型</span><span class="sxs-lookup"><span data-stu-id="0fc8d-121">Data Type</span></span>|<span data-ttu-id="0fc8d-122">描述</span><span class="sxs-lookup"><span data-stu-id="0fc8d-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="0fc8d-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="0fc8d-123">ClrInstanceID</span></span>|<span data-ttu-id="0fc8d-124">win:Uint16</span><span class="sxs-lookup"><span data-stu-id="0fc8d-124">win:Uint16</span></span>|<span data-ttu-id="0fc8d-125">唯一執行階段識別項。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="0fc8d-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="0fc8d-126">Reserved1</span></span>|<span data-ttu-id="0fc8d-127">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="0fc8d-127">win:UInt8</span></span>|<span data-ttu-id="0fc8d-128">保留的。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-128">Reserved.</span></span>|  
|<span data-ttu-id="0fc8d-129">Reserved2</span><span class="sxs-lookup"><span data-stu-id="0fc8d-129">Reserved2</span></span>|<span data-ttu-id="0fc8d-130">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="0fc8d-130">win:UInt8</span></span>|<span data-ttu-id="0fc8d-131">保留的。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-131">Reserved.</span></span>|  
|<span data-ttu-id="0fc8d-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="0fc8d-132">FrameCount</span></span>|<span data-ttu-id="0fc8d-133">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="0fc8d-133">win:UInt32</span></span>|<span data-ttu-id="0fc8d-134">堆疊追蹤裡的框架數。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="0fc8d-135">堆疊</span><span class="sxs-lookup"><span data-stu-id="0fc8d-135">Stack</span></span>|<span data-ttu-id="0fc8d-136">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="0fc8d-136">win:Pointer</span></span>|<span data-ttu-id="0fc8d-137">指令指標的資料行。</span><span class="sxs-lookup"><span data-stu-id="0fc8d-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0fc8d-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fc8d-138">See Also</span></span>  
 [<span data-ttu-id="0fc8d-139">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="0fc8d-139">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
