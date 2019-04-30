---
title: Interop ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 09b2848619256a255cc27f0268d46e5e6db8cbe4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949301"
---
# <a name="interop-etw-events"></a><span data-ttu-id="f853a-102">Interop ETW 事件</span><span class="sxs-lookup"><span data-stu-id="f853a-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="f853a-103">Interop 事件會擷取 Microsoft 中繼語言 (MSIL) Stub 之產生和快取的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="f853a-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="f853a-104">這個類別包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="f853a-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="f853a-105">ILStubGenerated 事件</span><span class="sxs-lookup"><span data-stu-id="f853a-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
- [<span data-ttu-id="f853a-106">ILStubCacheHit 事件</span><span class="sxs-lookup"><span data-stu-id="f853a-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="f853a-107">ILStubGenerated 事件</span><span class="sxs-lookup"><span data-stu-id="f853a-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="f853a-108">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="f853a-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="f853a-109">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="f853a-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="f853a-110">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="f853a-110">Keyword for raising the event</span></span>|<span data-ttu-id="f853a-111">層級</span><span class="sxs-lookup"><span data-stu-id="f853a-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f853a-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="f853a-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="f853a-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="f853a-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="f853a-114">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="f853a-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f853a-115">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="f853a-115">Event</span></span>|<span data-ttu-id="f853a-116">事件 ID</span><span class="sxs-lookup"><span data-stu-id="f853a-116">Event ID</span></span>|<span data-ttu-id="f853a-117">引發的時機</span><span class="sxs-lookup"><span data-stu-id="f853a-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="f853a-118">88</span><span class="sxs-lookup"><span data-stu-id="f853a-118">88</span></span>|<span data-ttu-id="f853a-119">已產生 MSIL 虛設常式。</span><span class="sxs-lookup"><span data-stu-id="f853a-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="f853a-120">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="f853a-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f853a-121">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="f853a-121">Field name</span></span>|<span data-ttu-id="f853a-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="f853a-122">Data type</span></span>|<span data-ttu-id="f853a-123">描述</span><span class="sxs-lookup"><span data-stu-id="f853a-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f853a-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="f853a-124">ModuleID</span></span>|<span data-ttu-id="f853a-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f853a-125">win:UInt16</span></span>|<span data-ttu-id="f853a-126">模組識別項。</span><span class="sxs-lookup"><span data-stu-id="f853a-126">The module identifier.</span></span>|  
|<span data-ttu-id="f853a-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="f853a-127">StubMethodID</span></span>|<span data-ttu-id="f853a-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f853a-128">win:UInt64</span></span>|<span data-ttu-id="f853a-129">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="f853a-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="f853a-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="f853a-130">StubFlags</span></span>|<span data-ttu-id="f853a-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f853a-131">win:UInt64</span></span>|<span data-ttu-id="f853a-132">虛設常式的旗標：</span><span class="sxs-lookup"><span data-stu-id="f853a-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="f853a-133">0x1 - 反向 interop。</span><span class="sxs-lookup"><span data-stu-id="f853a-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="f853a-134">0x2 - COM interop。</span><span class="sxs-lookup"><span data-stu-id="f853a-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="f853a-135">0x4 - NGen.exe 所產生的虛設常式。</span><span class="sxs-lookup"><span data-stu-id="f853a-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="f853a-136">0x8 - 委派。</span><span class="sxs-lookup"><span data-stu-id="f853a-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="f853a-137">0x10 - 變數引數。</span><span class="sxs-lookup"><span data-stu-id="f853a-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="f853a-138">0x20 - Unmanaged 被呼叫者。</span><span class="sxs-lookup"><span data-stu-id="f853a-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="f853a-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="f853a-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="f853a-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f853a-140">win:UInt32</span></span>|<span data-ttu-id="f853a-141">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f853a-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="f853a-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="f853a-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="f853a-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f853a-143">win:UnicodeString</span></span>|<span data-ttu-id="f853a-144">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f853a-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="f853a-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="f853a-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="f853a-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f853a-146">win:UnicodeString</span></span>|<span data-ttu-id="f853a-147">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="f853a-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="f853a-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="f853a-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="f853a-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f853a-149">win:UnicodeString</span></span>|<span data-ttu-id="f853a-150">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="f853a-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="f853a-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="f853a-151">NativeMethodSignature</span></span>|<span data-ttu-id="f853a-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f853a-152">win:UnicodeString</span></span>|<span data-ttu-id="f853a-153">原生方法簽章。</span><span class="sxs-lookup"><span data-stu-id="f853a-153">The native method signature.</span></span>|  
|<span data-ttu-id="f853a-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="f853a-154">StubMethodSignature</span></span>|<span data-ttu-id="f853a-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f853a-155">win:UnicodeString</span></span>|<span data-ttu-id="f853a-156">虛設常式方法簽章。</span><span class="sxs-lookup"><span data-stu-id="f853a-156">The stub method signature.</span></span>|  
|<span data-ttu-id="f853a-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="f853a-157">StubMethodILCode</span></span>|<span data-ttu-id="f853a-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f853a-158">win:UnicodeString</span></span>|<span data-ttu-id="f853a-159">虛設常式方法的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="f853a-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="f853a-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f853a-160">ClrInstanceID</span></span>|<span data-ttu-id="f853a-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f853a-161">win:UInt16</span></span>|<span data-ttu-id="f853a-162">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="f853a-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f853a-163">回到頁首</span><span class="sxs-lookup"><span data-stu-id="f853a-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="f853a-164">ILStubCacheHit 事件</span><span class="sxs-lookup"><span data-stu-id="f853a-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="f853a-165">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="f853a-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="f853a-166">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="f853a-166">Keyword for raising the event</span></span>|<span data-ttu-id="f853a-167">層級</span><span class="sxs-lookup"><span data-stu-id="f853a-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="f853a-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="f853a-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="f853a-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="f853a-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="f853a-170">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="f853a-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="f853a-171">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="f853a-171">Event</span></span>|<span data-ttu-id="f853a-172">事件 ID</span><span class="sxs-lookup"><span data-stu-id="f853a-172">Event ID</span></span>|<span data-ttu-id="f853a-173">引發的時機</span><span class="sxs-lookup"><span data-stu-id="f853a-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="f853a-174">89</span><span class="sxs-lookup"><span data-stu-id="f853a-174">89</span></span>|<span data-ttu-id="f853a-175">已存取 MSIL 快取。</span><span class="sxs-lookup"><span data-stu-id="f853a-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="f853a-176">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="f853a-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="f853a-177">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="f853a-177">Field name</span></span>|<span data-ttu-id="f853a-178">資料類型</span><span class="sxs-lookup"><span data-stu-id="f853a-178">Data type</span></span>|<span data-ttu-id="f853a-179">描述</span><span class="sxs-lookup"><span data-stu-id="f853a-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="f853a-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="f853a-180">ModuleID</span></span>|<span data-ttu-id="f853a-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f853a-181">win:UInt16</span></span>|<span data-ttu-id="f853a-182">模組識別項。</span><span class="sxs-lookup"><span data-stu-id="f853a-182">The module identifier.</span></span>|  
|<span data-ttu-id="f853a-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="f853a-183">StubMethodID</span></span>|<span data-ttu-id="f853a-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="f853a-184">win:UInt64</span></span>|<span data-ttu-id="f853a-185">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="f853a-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="f853a-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="f853a-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="f853a-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="f853a-187">win:UInt32</span></span>|<span data-ttu-id="f853a-188">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="f853a-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="f853a-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="f853a-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="f853a-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f853a-190">win:UnicodeString</span></span>|<span data-ttu-id="f853a-191">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f853a-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="f853a-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="f853a-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="f853a-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f853a-193">win:UnicodeString</span></span>|<span data-ttu-id="f853a-194">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="f853a-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="f853a-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="f853a-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="f853a-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="f853a-196">win:UnicodeString</span></span>|<span data-ttu-id="f853a-197">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="f853a-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="f853a-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="f853a-198">ClrInstanceID</span></span>|<span data-ttu-id="f853a-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="f853a-199">win:UInt16</span></span>|<span data-ttu-id="f853a-200">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="f853a-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="f853a-201">回到頁首</span><span class="sxs-lookup"><span data-stu-id="f853a-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="f853a-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f853a-202">See also</span></span>

- [<span data-ttu-id="f853a-203">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="f853a-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
