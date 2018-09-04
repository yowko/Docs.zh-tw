---
title: Exception Thrown_V1 ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- ExceptionThrown_V1 event [.NET Framework]
- ETW, ExceptionThrown_V1 event (CLR)
ms.assetid: 0d3da389-6b7b-40f6-a877-fac546d6019c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 865b7b16d5807bd9161855f453128a63c84eab96
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505219"
---
# <a name="exception-thrownv1-etw-event"></a><span data-ttu-id="10a3c-102">Exception Thrown_V1 ETW 事件</span><span class="sxs-lookup"><span data-stu-id="10a3c-102">Exception Thrown_V1 ETW Event</span></span>
<span data-ttu-id="10a3c-103">此事件會擷取被擲回的例外狀況相關資訊。</span><span class="sxs-lookup"><span data-stu-id="10a3c-103">This event captures information about the exceptions that are thrown.</span></span>  
  
 <span data-ttu-id="10a3c-104">下表顯示引發事件的關鍵字以及事件層級。</span><span class="sxs-lookup"><span data-stu-id="10a3c-104">The following table shows the keyword under which the event is raised, and the level of the event.</span></span> <span data-ttu-id="10a3c-105">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="10a3c-105">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="10a3c-106">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="10a3c-106">Keyword for raising the event</span></span>|<span data-ttu-id="10a3c-107">層級</span><span class="sxs-lookup"><span data-stu-id="10a3c-107">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="10a3c-108">`ExceptionKeyword` (0x8000)</span><span class="sxs-lookup"><span data-stu-id="10a3c-108">`ExceptionKeyword` (0x8000)</span></span>|<span data-ttu-id="10a3c-109">警告 (2)</span><span class="sxs-lookup"><span data-stu-id="10a3c-109">Warning (2)</span></span>|  
  
 <span data-ttu-id="10a3c-110">下表顯示事件資訊。</span><span class="sxs-lookup"><span data-stu-id="10a3c-110">The following table shows event information.</span></span>  
  
|<span data-ttu-id="10a3c-111">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="10a3c-111">Event</span></span>|<span data-ttu-id="10a3c-112">事件 ID</span><span class="sxs-lookup"><span data-stu-id="10a3c-112">Event ID</span></span>|<span data-ttu-id="10a3c-113">引發的時機</span><span class="sxs-lookup"><span data-stu-id="10a3c-113">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ExceptionThrown_V1`|<span data-ttu-id="10a3c-114">80</span><span class="sxs-lookup"><span data-stu-id="10a3c-114">80</span></span>|<span data-ttu-id="10a3c-115">擲回 Managed 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="10a3c-115">A managed exception is thrown.</span></span>|  
  
 <span data-ttu-id="10a3c-116">下表顯示事件資料。</span><span class="sxs-lookup"><span data-stu-id="10a3c-116">The following table shows event data.</span></span>  
  
|<span data-ttu-id="10a3c-117">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="10a3c-117">Field name</span></span>|<span data-ttu-id="10a3c-118">資料類型</span><span class="sxs-lookup"><span data-stu-id="10a3c-118">Data type</span></span>|<span data-ttu-id="10a3c-119">描述</span><span class="sxs-lookup"><span data-stu-id="10a3c-119">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="10a3c-120">例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="10a3c-120">Exception Type</span></span>|<span data-ttu-id="10a3c-121">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="10a3c-121">win:UnicodeString</span></span>|<span data-ttu-id="10a3c-122">例外狀況類型，例如 `System.NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="10a3c-122">Type of the exception; for example, `System.NullReferenceException`.</span></span>|  
|<span data-ttu-id="10a3c-123">例外狀況訊息</span><span class="sxs-lookup"><span data-stu-id="10a3c-123">Exception Message</span></span>|<span data-ttu-id="10a3c-124">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="10a3c-124">win:UnicodeString</span></span>|<span data-ttu-id="10a3c-125">實際的例外狀況訊息。</span><span class="sxs-lookup"><span data-stu-id="10a3c-125">Actual exception message.</span></span>|  
|<span data-ttu-id="10a3c-126">EIPCodeThrow</span><span class="sxs-lookup"><span data-stu-id="10a3c-126">EIPCodeThrow</span></span>|<span data-ttu-id="10a3c-127">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="10a3c-127">win:Pointer</span></span>|<span data-ttu-id="10a3c-128">發生例外狀況的指令指標。</span><span class="sxs-lookup"><span data-stu-id="10a3c-128">Instruction pointer where exception occurred.</span></span>|  
|<span data-ttu-id="10a3c-129">ExceptionHR</span><span class="sxs-lookup"><span data-stu-id="10a3c-129">ExceptionHR</span></span>|<span data-ttu-id="10a3c-130">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="10a3c-130">win:UInt32</span></span>|<span data-ttu-id="10a3c-131">例外狀況 [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679)。</span><span class="sxs-lookup"><span data-stu-id="10a3c-131">Exception [HRESULT](https://go.microsoft.com/fwlink/?LinkId=179679).</span></span>|  
|<span data-ttu-id="10a3c-132">ExceptionFlags</span><span class="sxs-lookup"><span data-stu-id="10a3c-132">ExceptionFlags</span></span>|<span data-ttu-id="10a3c-133">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="10a3c-133">win:UInt16</span></span>|<span data-ttu-id="10a3c-134">0x01：HasInnerException (請參閱 Visual Basic 文件的 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md))。</span><span class="sxs-lookup"><span data-stu-id="10a3c-134">0x01: HasInnerException (see [CLR ETW Events](../../../docs/framework/performance/clr-etw-events.md) in the Visual Basic documentation).</span></span><br /><br /> <span data-ttu-id="10a3c-135">0x02：IsNestedException。</span><span class="sxs-lookup"><span data-stu-id="10a3c-135">0x02: IsNestedException.</span></span><br /><br /> <span data-ttu-id="10a3c-136">0x04：IsRethrownException。</span><span class="sxs-lookup"><span data-stu-id="10a3c-136">0x04: IsRethrownException.</span></span><br /><br /> <span data-ttu-id="10a3c-137">0x08：IsCorruptedStateException (表示處理序狀態已損毀，請參閱 MSDN 上的[處理損毀狀態的例外狀況](https://go.microsoft.com/fwlink/?LinkId=179681))。</span><span class="sxs-lookup"><span data-stu-id="10a3c-137">0x08: IsCorruptedStateException (indicates that the process state is corrupt; see [Handling Corrupted State Exceptions](https://go.microsoft.com/fwlink/?LinkId=179681) on MSDN).</span></span><br /><br /> <span data-ttu-id="10a3c-138">0x10：IsCLSCompliant (衍生自 <xref:System.Exception> 的例外狀況符合 CLS 標準，否則與 CLS 不相容)。</span><span class="sxs-lookup"><span data-stu-id="10a3c-138">0x10: IsCLSCompliant (an exception that derives from <xref:System.Exception> is CLS-compliant; otherwise, it is not CLS-compliant).</span></span>|  
|<span data-ttu-id="10a3c-139">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="10a3c-139">ClrInstanceID</span></span>|<span data-ttu-id="10a3c-140">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="10a3c-140">win:UInt16</span></span>|<span data-ttu-id="10a3c-141">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="10a3c-141">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="10a3c-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="10a3c-142">See Also</span></span>  
 [<span data-ttu-id="10a3c-143">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="10a3c-143">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
