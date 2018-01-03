---
title: "Exception Thrown_V1 ETW 事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 60013d0df8c63033f6da8d61479bacac7b944094
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="exception-thrownv1-etw-event"></a><span data-ttu-id="6e503-102">Exception Thrown_V1 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="6e503-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="6e503-103">此事件會擷取被擲回的例外狀況相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6e503-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="6e503-104">下表顯示引發事件的關鍵字以及事件層級。</span><span class="sxs-lookup"><span data-stu-id="6e503-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="6e503-105">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="6e503-105">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="6e503-106">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="6e503-106">Keyword for raising the event</span></span>|<span data-ttu-id="6e503-107">層級</span><span class="sxs-lookup"><span data-stu-id="6e503-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6e503-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="6e503-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6e503-109">警告 (2)</span><span class="sxs-lookup"><span data-stu-id="6e503-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="6e503-110">下表顯示事件資訊。</span><span class="sxs-lookup"><span data-stu-id="6e503-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="6e503-111">事件</span><span class="sxs-lookup"><span data-stu-id="6e503-111">Event</span></span>|<span data-ttu-id="6e503-112">事件 ID</span><span class="sxs-lookup"><span data-stu-id="6e503-112">Event ID</span></span>|<span data-ttu-id="6e503-113">引發的時機</span><span class="sxs-lookup"><span data-stu-id="6e503-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="6e503-114">80</span><span class="sxs-lookup"><span data-stu-id="6e503-114">80</span></span>|<span data-ttu-id="6e503-115">擲回 Managed 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6e503-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="6e503-116">下表顯示事件資料。</span><span class="sxs-lookup"><span data-stu-id="6e503-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="6e503-117">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="6e503-117">Field name</span></span>|<span data-ttu-id="6e503-118">資料類型</span><span class="sxs-lookup"><span data-stu-id="6e503-118">Data type</span></span>|<span data-ttu-id="6e503-119">描述</span><span class="sxs-lookup"><span data-stu-id="6e503-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6e503-120">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="6e503-120">Exception Type</span></span>|<span data-ttu-id="6e503-121">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="6e503-121">win:UnicodeString</span></span>|<span data-ttu-id="6e503-122">例外狀況類型，例如 `System.NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="6e503-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="6e503-123">例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="6e503-123">Exception Message</span></span>|<span data-ttu-id="6e503-124">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="6e503-124">win:UnicodeString</span></span>|<span data-ttu-id="6e503-125">實際的例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="6e503-125">Actual exception message.</span></span>|  
|<span data-ttu-id="6e503-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="6e503-126">EIPCodeThrow</span></span>|<span data-ttu-id="6e503-127">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="6e503-127">win:Pointer</span></span>|<span data-ttu-id="6e503-128">發生例外狀況的指令指標。</span><span class="sxs-lookup"><span data-stu-id="6e503-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="6e503-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="6e503-129">ExceptionHR</span></span>|<span data-ttu-id="6e503-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="6e503-130">win:UInt32</span></span>|<span data-ttu-id="6e503-131">例外狀況 [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679)。</span><span class="sxs-lookup"><span data-stu-id="6e503-131">Exception [HRESULT](http://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="6e503-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="6e503-132">ExceptionFlags</span></span>|<span data-ttu-id="6e503-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="6e503-133">win:UInt16</span></span>|<span data-ttu-id="6e503-134">0x01：HasInnerException (請參閱 Visual Basic 文件的 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md))。</span><span class="sxs-lookup"><span data-stu-id="6e503-134">0x01: HasInnerException (see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="6e503-135">0x02：IsNestedException。</span><span class="sxs-lookup"><span data-stu-id="6e503-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="6e503-136">0x04：IsRethrownException。</span><span class="sxs-lookup"><span data-stu-id="6e503-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="6e503-137">0x08：IsCorruptedStateException (表示處理序狀態已損毀，請參閱 MSDN 上的[處理損毀狀態的例外狀況](http://go.microsoft.com/fwlink/?LinkId=179681))。</span><span class="sxs-lookup"><span data-stu-id="6e503-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](http://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="6e503-138">0x10：IsCLSCompliant (衍生自 <xref:System.Exception> 的例外狀況符合 CLS 標準，否則與 CLS 不相容)。</span><span class="sxs-lookup"><span data-stu-id="6e503-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="6e503-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6e503-139">ClrInstanceID</span></span>|<span data-ttu-id="6e503-140">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="6e503-140">win:UInt16</span></span>|<span data-ttu-id="6e503-141">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="6e503-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e503-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="6e503-142">See Also</span></span>  
 [<span data-ttu-id="6e503-143">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="6e503-143">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
