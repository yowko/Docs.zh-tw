---
title: Interop ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c52c9bf37e67e4d26867d2b3754945e86e2bf609
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422416"
---
# <a name="interop-etw-events"></a><span data-ttu-id="eacd3-102">Interop ETW 事件</span><span class="sxs-lookup"><span data-stu-id="eacd3-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="eacd3-103">Interop 事件會擷取 Microsoft 中繼語言 (MSIL) Stub 之產生和快取的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eacd3-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="eacd3-104">這個類別包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="eacd3-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="eacd3-105">ILStubGenerated 事件</span><span class="sxs-lookup"><span data-stu-id="eacd3-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
- [<span data-ttu-id="eacd3-106">ILStubCacheHit 事件</span><span class="sxs-lookup"><span data-stu-id="eacd3-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="eacd3-107">ILStubGenerated 事件</span><span class="sxs-lookup"><span data-stu-id="eacd3-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="eacd3-108">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="eacd3-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="eacd3-109">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="eacd3-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="eacd3-110">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="eacd3-110">Keyword for raising the event</span></span>|<span data-ttu-id="eacd3-111">層級</span><span class="sxs-lookup"><span data-stu-id="eacd3-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="eacd3-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="eacd3-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="eacd3-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="eacd3-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="eacd3-114">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="eacd3-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="eacd3-115">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="eacd3-115">Event</span></span>|<span data-ttu-id="eacd3-116">事件 ID</span><span class="sxs-lookup"><span data-stu-id="eacd3-116">Event ID</span></span>|<span data-ttu-id="eacd3-117">引發的時機</span><span class="sxs-lookup"><span data-stu-id="eacd3-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="eacd3-118">88</span><span class="sxs-lookup"><span data-stu-id="eacd3-118">88</span></span>|<span data-ttu-id="eacd3-119">已產生 MSIL 虛設常式。</span><span class="sxs-lookup"><span data-stu-id="eacd3-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="eacd3-120">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="eacd3-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="eacd3-121">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="eacd3-121">Field name</span></span>|<span data-ttu-id="eacd3-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="eacd3-122">Data type</span></span>|<span data-ttu-id="eacd3-123">描述</span><span class="sxs-lookup"><span data-stu-id="eacd3-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="eacd3-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="eacd3-124">ModuleID</span></span>|<span data-ttu-id="eacd3-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="eacd3-125">win:UInt16</span></span>|<span data-ttu-id="eacd3-126">模組識別項。</span><span class="sxs-lookup"><span data-stu-id="eacd3-126">The module identifier.</span></span>|  
|<span data-ttu-id="eacd3-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="eacd3-127">StubMethodID</span></span>|<span data-ttu-id="eacd3-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="eacd3-128">win:UInt64</span></span>|<span data-ttu-id="eacd3-129">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="eacd3-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="eacd3-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="eacd3-130">StubFlags</span></span>|<span data-ttu-id="eacd3-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="eacd3-131">win:UInt64</span></span>|<span data-ttu-id="eacd3-132">虛設常式的旗標：</span><span class="sxs-lookup"><span data-stu-id="eacd3-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="eacd3-133">0x1 - 反向 interop。</span><span class="sxs-lookup"><span data-stu-id="eacd3-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="eacd3-134">0x2 - COM interop。</span><span class="sxs-lookup"><span data-stu-id="eacd3-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="eacd3-135">0x4 - NGen.exe 所產生的虛設常式。</span><span class="sxs-lookup"><span data-stu-id="eacd3-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="eacd3-136">0x8 - 委派。</span><span class="sxs-lookup"><span data-stu-id="eacd3-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="eacd3-137">0x10-變數引數。</span><span class="sxs-lookup"><span data-stu-id="eacd3-137">0x10 - Variable argument.</span></span><br /><br /> <span data-ttu-id="eacd3-138">0x20 - Unmanaged 被呼叫者。</span><span class="sxs-lookup"><span data-stu-id="eacd3-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="eacd3-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="eacd3-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="eacd3-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="eacd3-140">win:UInt32</span></span>|<span data-ttu-id="eacd3-141">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="eacd3-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="eacd3-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="eacd3-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="eacd3-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="eacd3-143">win:UnicodeString</span></span>|<span data-ttu-id="eacd3-144">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="eacd3-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="eacd3-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="eacd3-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="eacd3-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="eacd3-146">win:UnicodeString</span></span>|<span data-ttu-id="eacd3-147">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="eacd3-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="eacd3-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="eacd3-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="eacd3-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="eacd3-149">win:UnicodeString</span></span>|<span data-ttu-id="eacd3-150">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="eacd3-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="eacd3-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="eacd3-151">NativeMethodSignature</span></span>|<span data-ttu-id="eacd3-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="eacd3-152">win:UnicodeString</span></span>|<span data-ttu-id="eacd3-153">原生方法簽章。</span><span class="sxs-lookup"><span data-stu-id="eacd3-153">The native method signature.</span></span>|  
|<span data-ttu-id="eacd3-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="eacd3-154">StubMethodSignature</span></span>|<span data-ttu-id="eacd3-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="eacd3-155">win:UnicodeString</span></span>|<span data-ttu-id="eacd3-156">虛設常式方法簽章。</span><span class="sxs-lookup"><span data-stu-id="eacd3-156">The stub method signature.</span></span>|  
|<span data-ttu-id="eacd3-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="eacd3-157">StubMethodILCode</span></span>|<span data-ttu-id="eacd3-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="eacd3-158">win:UnicodeString</span></span>|<span data-ttu-id="eacd3-159">虛設常式方法的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="eacd3-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="eacd3-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="eacd3-160">ClrInstanceID</span></span>|<span data-ttu-id="eacd3-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="eacd3-161">win:UInt16</span></span>|<span data-ttu-id="eacd3-162">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="eacd3-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="eacd3-163">回到頁首</span><span class="sxs-lookup"><span data-stu-id="eacd3-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="eacd3-164">ILStubCacheHit 事件</span><span class="sxs-lookup"><span data-stu-id="eacd3-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="eacd3-165">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="eacd3-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="eacd3-166">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="eacd3-166">Keyword for raising the event</span></span>|<span data-ttu-id="eacd3-167">層級</span><span class="sxs-lookup"><span data-stu-id="eacd3-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="eacd3-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="eacd3-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="eacd3-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="eacd3-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="eacd3-170">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="eacd3-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="eacd3-171">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="eacd3-171">Event</span></span>|<span data-ttu-id="eacd3-172">事件 ID</span><span class="sxs-lookup"><span data-stu-id="eacd3-172">Event ID</span></span>|<span data-ttu-id="eacd3-173">引發的時機</span><span class="sxs-lookup"><span data-stu-id="eacd3-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="eacd3-174">89</span><span class="sxs-lookup"><span data-stu-id="eacd3-174">89</span></span>|<span data-ttu-id="eacd3-175">已存取 MSIL 快取。</span><span class="sxs-lookup"><span data-stu-id="eacd3-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="eacd3-176">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="eacd3-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="eacd3-177">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="eacd3-177">Field name</span></span>|<span data-ttu-id="eacd3-178">資料類型</span><span class="sxs-lookup"><span data-stu-id="eacd3-178">Data type</span></span>|<span data-ttu-id="eacd3-179">描述</span><span class="sxs-lookup"><span data-stu-id="eacd3-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="eacd3-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="eacd3-180">ModuleID</span></span>|<span data-ttu-id="eacd3-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="eacd3-181">win:UInt16</span></span>|<span data-ttu-id="eacd3-182">模組識別項。</span><span class="sxs-lookup"><span data-stu-id="eacd3-182">The module identifier.</span></span>|  
|<span data-ttu-id="eacd3-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="eacd3-183">StubMethodID</span></span>|<span data-ttu-id="eacd3-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="eacd3-184">win:UInt64</span></span>|<span data-ttu-id="eacd3-185">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="eacd3-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="eacd3-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="eacd3-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="eacd3-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="eacd3-187">win:UInt32</span></span>|<span data-ttu-id="eacd3-188">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="eacd3-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="eacd3-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="eacd3-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="eacd3-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="eacd3-190">win:UnicodeString</span></span>|<span data-ttu-id="eacd3-191">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="eacd3-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="eacd3-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="eacd3-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="eacd3-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="eacd3-193">win:UnicodeString</span></span>|<span data-ttu-id="eacd3-194">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="eacd3-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="eacd3-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="eacd3-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="eacd3-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="eacd3-196">win:UnicodeString</span></span>|<span data-ttu-id="eacd3-197">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="eacd3-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="eacd3-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="eacd3-198">ClrInstanceID</span></span>|<span data-ttu-id="eacd3-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="eacd3-199">win:UInt16</span></span>|<span data-ttu-id="eacd3-200">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="eacd3-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="eacd3-201">回到頁首</span><span class="sxs-lookup"><span data-stu-id="eacd3-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="eacd3-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eacd3-202">See also</span></span>

- [<span data-ttu-id="eacd3-203">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="eacd3-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
