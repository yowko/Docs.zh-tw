---
title: Exception Thrown_V1 ETW 事件
description: 查看 ExceptionThrown_V1 ETW 事件的詳細資訊。 系統會為擲回的例外狀況指定事件資料，例如功能變數名稱、資料類型和描述。
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
ms.openlocfilehash: c1ba994b291bd278a95e34beb0b02ed6581786e8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96263473"
---
# <a name="exception-thrown_v1-etw-event"></a><span data-ttu-id="c0b4e-104">Exception Thrown_V1 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="c0b4e-104">Exception Thrown_V1 ETW Event</span></span>

<span data-ttu-id="c0b4e-105">此事件會擷取被擲回的例外狀況相關資訊。</span><span class="sxs-lookup"><span data-stu-id="c0b4e-105">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="c0b4e-106">下表顯示引發事件的關鍵字以及事件層級。</span><span class="sxs-lookup"><span data-stu-id="c0b4e-106">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="c0b4e-107">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="c0b4e-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="c0b4e-108">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="c0b4e-108">Keyword for raising the event</span></span>|<span data-ttu-id="c0b4e-109">層級</span><span class="sxs-lookup"><span data-stu-id="c0b4e-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="c0b4e-110">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="c0b4e-110">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="c0b4e-111">警告 (2)</span><span class="sxs-lookup"><span data-stu-id="c0b4e-111">Warning (2)</span></span>|  
  
 <span data-ttu-id="c0b4e-112">下表顯示事件資訊。</span><span class="sxs-lookup"><span data-stu-id="c0b4e-112">The following table shows event information.</span></span>  
  
|<span data-ttu-id="c0b4e-113">事件</span><span class="sxs-lookup"><span data-stu-id="c0b4e-113">Event</span></span>|<span data-ttu-id="c0b4e-114">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c0b4e-114">Event ID</span></span>|<span data-ttu-id="c0b4e-115">引發的時機</span><span class="sxs-lookup"><span data-stu-id="c0b4e-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="c0b4e-116">80</span><span class="sxs-lookup"><span data-stu-id="c0b4e-116">80</span></span>|<span data-ttu-id="c0b4e-117">擲回 Managed 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c0b4e-117">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="c0b4e-118">下表顯示事件資料。</span><span class="sxs-lookup"><span data-stu-id="c0b4e-118">The following table shows event data.</span></span>  
  
|<span data-ttu-id="c0b4e-119">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="c0b4e-119">Field name</span></span>|<span data-ttu-id="c0b4e-120">資料類型</span><span class="sxs-lookup"><span data-stu-id="c0b4e-120">Data type</span></span>|<span data-ttu-id="c0b4e-121">描述</span><span class="sxs-lookup"><span data-stu-id="c0b4e-121">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="c0b4e-122">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="c0b4e-122">Exception Type</span></span>|<span data-ttu-id="c0b4e-123">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c0b4e-123">win:UnicodeString</span></span>|<span data-ttu-id="c0b4e-124">例外狀況類型，例如 `System.NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="c0b4e-124">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="c0b4e-125">例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="c0b4e-125">Exception Message</span></span>|<span data-ttu-id="c0b4e-126">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="c0b4e-126">win:UnicodeString</span></span>|<span data-ttu-id="c0b4e-127">實際的例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="c0b4e-127">Actual exception message.</span></span>|  
|<span data-ttu-id="c0b4e-128">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="c0b4e-128">EIPCodeThrow</span></span>|<span data-ttu-id="c0b4e-129">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="c0b4e-129">win:Pointer</span></span>|<span data-ttu-id="c0b4e-130">發生例外狀況的指令指標。</span><span class="sxs-lookup"><span data-stu-id="c0b4e-130">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="c0b4e-131">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="c0b4e-131">ExceptionHR</span></span>|<span data-ttu-id="c0b4e-132">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="c0b4e-132">win:UInt32</span></span>|<span data-ttu-id="c0b4e-133">例外狀況 [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a)。</span><span class="sxs-lookup"><span data-stu-id="c0b4e-133">Exception [HRESULT](/openspecs/windows_protocols/ms-erref/0642cb2f-2075-4469-918c-4441e69c548a).</span></span>|  
|<span data-ttu-id="c0b4e-134">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="c0b4e-134">ExceptionFlags</span></span>|<span data-ttu-id="c0b4e-135">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c0b4e-135">win:UInt16</span></span>|<span data-ttu-id="c0b4e-136">0x01：HasInnerException (請參閱 Visual Basic 文件的 [CLR ETW 事件](clr-etw-events.md))。</span><span class="sxs-lookup"><span data-stu-id="c0b4e-136">0x01: HasInnerException (see [CLR ETW Events](clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="c0b4e-137">0x02：IsNestedException。</span><span class="sxs-lookup"><span data-stu-id="c0b4e-137">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="c0b4e-138">0x04：IsRethrownException。</span><span class="sxs-lookup"><span data-stu-id="c0b4e-138">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="c0b4e-139">0x08： IsCorruptedStateException (表示進程狀態已損毀;請參閱 [處理損毀狀態例外狀況](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)) 。</span><span class="sxs-lookup"><span data-stu-id="c0b4e-139">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](/archive/msdn-magazine/2009/february/clr-inside-out-handling-corrupted-state-exceptions)).</span></span><br /><br /> <span data-ttu-id="c0b4e-140">0x10：IsCLSCompliant (衍生自 <xref:System.Exception> 的例外狀況符合 CLS 標準，否則與 CLS 不相容)。</span><span class="sxs-lookup"><span data-stu-id="c0b4e-140">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="c0b4e-141">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="c0b4e-141">ClrInstanceID</span></span>|<span data-ttu-id="c0b4e-142">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="c0b4e-142">win:UInt16</span></span>|<span data-ttu-id="c0b4e-143">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="c0b4e-143">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0b4e-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0b4e-144">See also</span></span>

- [<span data-ttu-id="c0b4e-145">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="c0b4e-145">CLR ETW Events</span></span>](clr-etw-events.md)
