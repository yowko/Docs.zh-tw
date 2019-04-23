---
title: Exception Thrown_V1 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dd322d25d91bb277a4c817594c968c28a6d61d68
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136132"
---
# <a name="exception-thrownv1-etw-event"></a><span data-ttu-id="3f356-102">Exception Thrown_V1 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="3f356-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="3f356-103">此事件會擷取被擲回的例外狀況相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3f356-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="3f356-104">下表顯示引發事件的關鍵字以及事件層級。</span><span class="sxs-lookup"><span data-stu-id="3f356-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="3f356-105">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="3f356-105">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="3f356-106">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="3f356-106">Keyword for raising the event</span></span>|<span data-ttu-id="3f356-107">層級</span><span class="sxs-lookup"><span data-stu-id="3f356-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="3f356-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="3f356-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="3f356-109">警告 (2)</span><span class="sxs-lookup"><span data-stu-id="3f356-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="3f356-110">下表顯示事件資訊。</span><span class="sxs-lookup"><span data-stu-id="3f356-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="3f356-111">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="3f356-111">Event</span></span>|<span data-ttu-id="3f356-112">事件 ID</span><span class="sxs-lookup"><span data-stu-id="3f356-112">Event ID</span></span>|<span data-ttu-id="3f356-113">引發的時機</span><span class="sxs-lookup"><span data-stu-id="3f356-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="3f356-114">80</span><span class="sxs-lookup"><span data-stu-id="3f356-114">80</span></span>|<span data-ttu-id="3f356-115">擲回 Managed 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3f356-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="3f356-116">下表顯示事件資料。</span><span class="sxs-lookup"><span data-stu-id="3f356-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="3f356-117">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="3f356-117">Field name</span></span>|<span data-ttu-id="3f356-118">資料類型</span><span class="sxs-lookup"><span data-stu-id="3f356-118">Data type</span></span>|<span data-ttu-id="3f356-119">描述</span><span class="sxs-lookup"><span data-stu-id="3f356-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="3f356-120">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="3f356-120">Exception Type</span></span>|<span data-ttu-id="3f356-121">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="3f356-121">win:UnicodeString</span></span>|<span data-ttu-id="3f356-122">例外狀況類型，例如 `System.NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="3f356-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="3f356-123">例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="3f356-123">Exception Message</span></span>|<span data-ttu-id="3f356-124">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="3f356-124">win:UnicodeString</span></span>|<span data-ttu-id="3f356-125">實際的例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="3f356-125">Actual exception message.</span></span>|  
|<span data-ttu-id="3f356-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="3f356-126">EIPCodeThrow</span></span>|<span data-ttu-id="3f356-127">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="3f356-127">win:Pointer</span></span>|<span data-ttu-id="3f356-128">發生例外狀況的指令指標。</span><span class="sxs-lookup"><span data-stu-id="3f356-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="3f356-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="3f356-129">ExceptionHR</span></span>|<span data-ttu-id="3f356-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="3f356-130">win:UInt32</span></span>|<span data-ttu-id="3f356-131">例外狀況 [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679)。</span><span class="sxs-lookup"><span data-stu-id="3f356-131">Exception [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="3f356-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="3f356-132">ExceptionFlags</span></span>|<span data-ttu-id="3f356-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3f356-133">win:UInt16</span></span>|<span data-ttu-id="3f356-134">0x01:0x01:hasinnerexception (請參閱[CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)Visual Basic 文件中)。</span><span class="sxs-lookup"><span data-stu-id="3f356-134">0x01: HasInnerException (see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="3f356-135">0x02:IsNestedException.</span><span class="sxs-lookup"><span data-stu-id="3f356-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="3f356-136">0x04:0x04:isrethrownexception。</span><span class="sxs-lookup"><span data-stu-id="3f356-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="3f356-137">0x08:0x08:iscorruptedstateexception (表示處理序狀態已損毀，請參閱[處理損毀狀態例外狀況](https://go.microsoft.com/fwlink/?LinkId=179681)MSDN 上)。</span><span class="sxs-lookup"><span data-stu-id="3f356-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="3f356-138">0x10:0x10:isclscompliant (衍生自例外狀況<xref:System.Exception>符合 CLS 規範，否則它不符合 CLS 標準)。</span><span class="sxs-lookup"><span data-stu-id="3f356-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="3f356-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="3f356-139">ClrInstanceID</span></span>|<span data-ttu-id="3f356-140">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="3f356-140">win:UInt16</span></span>|<span data-ttu-id="3f356-141">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="3f356-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f356-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f356-142">See also</span></span>

- [<span data-ttu-id="3f356-143">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="3f356-143">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
