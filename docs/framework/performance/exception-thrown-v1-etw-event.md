---
title: Exception Thrown_V1 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: 80faf6e607755ee79c7ec17f2d7d3d5bdce822b7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716057"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="6fccc-102">Exception Thrown_V1 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="6fccc-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="6fccc-103">此事件會擷取被擲回的例外狀況相關資訊。</span><span class="sxs-lookup"><span data-stu-id="6fccc-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="6fccc-104">下表顯示引發事件的關鍵字以及事件層級。</span><span class="sxs-lookup"><span data-stu-id="6fccc-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="6fccc-105">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="6fccc-105">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="6fccc-106">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="6fccc-106">Keyword for raising the event</span></span>|<span data-ttu-id="6fccc-107">Level</span><span class="sxs-lookup"><span data-stu-id="6fccc-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="6fccc-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="6fccc-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="6fccc-109">警告 (2)</span><span class="sxs-lookup"><span data-stu-id="6fccc-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="6fccc-110">下表顯示事件資訊。</span><span class="sxs-lookup"><span data-stu-id="6fccc-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="6fccc-111">Event</span><span class="sxs-lookup"><span data-stu-id="6fccc-111">Event</span></span>|<span data-ttu-id="6fccc-112">事件 ID</span><span class="sxs-lookup"><span data-stu-id="6fccc-112">Event ID</span></span>|<span data-ttu-id="6fccc-113">引發的時機</span><span class="sxs-lookup"><span data-stu-id="6fccc-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="6fccc-114">80</span><span class="sxs-lookup"><span data-stu-id="6fccc-114">80</span></span>|<span data-ttu-id="6fccc-115">擲回 Managed 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="6fccc-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="6fccc-116">下表顯示事件資料。</span><span class="sxs-lookup"><span data-stu-id="6fccc-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="6fccc-117">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="6fccc-117">Field name</span></span>|<span data-ttu-id="6fccc-118">資料類型</span><span class="sxs-lookup"><span data-stu-id="6fccc-118">Data type</span></span>|<span data-ttu-id="6fccc-119">描述</span><span class="sxs-lookup"><span data-stu-id="6fccc-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="6fccc-120">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="6fccc-120">Exception Type</span></span>|<span data-ttu-id="6fccc-121">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="6fccc-121">win:UnicodeString</span></span>|<span data-ttu-id="6fccc-122">例外狀況類型，例如 `System.NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="6fccc-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="6fccc-123">例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="6fccc-123">Exception Message</span></span>|<span data-ttu-id="6fccc-124">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="6fccc-124">win:UnicodeString</span></span>|<span data-ttu-id="6fccc-125">實際的例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="6fccc-125">Actual exception message.</span></span>|  
|<span data-ttu-id="6fccc-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="6fccc-126">EIPCodeThrow</span></span>|<span data-ttu-id="6fccc-127">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="6fccc-127">win:Pointer</span></span>|<span data-ttu-id="6fccc-128">發生例外狀況的指令指標。</span><span class="sxs-lookup"><span data-stu-id="6fccc-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="6fccc-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="6fccc-129">ExceptionHR</span></span>|<span data-ttu-id="6fccc-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="6fccc-130">win:UInt32</span></span>|<span data-ttu-id="6fccc-131">例外狀況 [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a)。</span><span class="sxs-lookup"><span data-stu-id="6fccc-131">Exception [HRESULT](https://docs.microsoft.com/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="6fccc-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="6fccc-132">ExceptionFlags</span></span>|<span data-ttu-id="6fccc-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="6fccc-133">win:UInt16</span></span>|<span data-ttu-id="6fccc-134">0x01：HasInnerException (請參閱 Visual Basic 文件的 [CLR ETW 事件](clr-etw-events.md))。</span><span class="sxs-lookup"><span data-stu-id="6fccc-134">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="6fccc-135">0x02：IsNestedException。</span><span class="sxs-lookup"><span data-stu-id="6fccc-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="6fccc-136">0x04：IsRethrownException。</span><span class="sxs-lookup"><span data-stu-id="6fccc-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="6fccc-137">0x08： IsCorruptedStateException （表示進程狀態已損毀，請參閱[處理損毀狀態例外狀況](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)）。</span><span class="sxs-lookup"><span data-stu-id="6fccc-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://docs.microsoft.com/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="6fccc-138">0x10：IsCLSCompliant (衍生自 <xref:System.Exception> 的例外狀況符合 CLS 標準，否則與 CLS 不相容)。</span><span class="sxs-lookup"><span data-stu-id="6fccc-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="6fccc-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="6fccc-139">ClrInstanceID</span></span>|<span data-ttu-id="6fccc-140">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="6fccc-140">win:UInt16</span></span>|<span data-ttu-id="6fccc-141">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="6fccc-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6fccc-142">請參閱</span><span class="sxs-lookup"><span data-stu-id="6fccc-142">See also</span></span>

- [<span data-ttu-id="6fccc-143">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="6fccc-143">CLR ETW Events</span></span>](clr-etw-events.md)
