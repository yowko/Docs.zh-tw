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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083604"
---
# <a name="interop-etw-events"></a><span data-ttu-id="b6ce5-102">Interop ETW 事件</span><span class="sxs-lookup"><span data-stu-id="b6ce5-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="b6ce5-103">Interop 事件會擷取 Microsoft 中繼語言 (MSIL) Stub 之產生和快取的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="b6ce5-104">這個類別包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="b6ce5-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="b6ce5-105">ILStubGenerated 事件</span><span class="sxs-lookup"><span data-stu-id="b6ce5-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="b6ce5-106">ILStubCacheHit 事件</span><span class="sxs-lookup"><span data-stu-id="b6ce5-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="b6ce5-107">ILStubGenerated 事件</span><span class="sxs-lookup"><span data-stu-id="b6ce5-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="b6ce5-108">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="b6ce5-109">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="b6ce5-110">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="b6ce5-110">Keyword for raising the event</span></span>|<span data-ttu-id="b6ce5-111">層級</span><span class="sxs-lookup"><span data-stu-id="b6ce5-111">Level</span></span>|  
|-----------------------------------|-----------|  
|`InteropKeyword` <span data-ttu-id="b6ce5-112">(0x2000)</span><span class="sxs-lookup"><span data-stu-id="b6ce5-112">(0x2000)</span></span>|<span data-ttu-id="b6ce5-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="b6ce5-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="b6ce5-114">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b6ce5-115">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="b6ce5-115">Event</span></span>|<span data-ttu-id="b6ce5-116">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b6ce5-116">Event ID</span></span>|<span data-ttu-id="b6ce5-117">引發的時機</span><span class="sxs-lookup"><span data-stu-id="b6ce5-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="b6ce5-118">88</span><span class="sxs-lookup"><span data-stu-id="b6ce5-118">88</span></span>|<span data-ttu-id="b6ce5-119">已產生 MSIL 虛設常式。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="b6ce5-120">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="b6ce5-121">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="b6ce5-121">Field name</span></span>|<span data-ttu-id="b6ce5-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="b6ce5-122">Data type</span></span>|<span data-ttu-id="b6ce5-123">描述</span><span class="sxs-lookup"><span data-stu-id="b6ce5-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="b6ce5-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="b6ce5-124">ModuleID</span></span>|<span data-ttu-id="b6ce5-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="b6ce5-125">win:UInt16</span></span>|<span data-ttu-id="b6ce5-126">模組識別項。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-126">The module identifier.</span></span>|  
|<span data-ttu-id="b6ce5-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="b6ce5-127">StubMethodID</span></span>|<span data-ttu-id="b6ce5-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="b6ce5-128">win:UInt64</span></span>|<span data-ttu-id="b6ce5-129">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="b6ce5-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="b6ce5-130">StubFlags</span></span>|<span data-ttu-id="b6ce5-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="b6ce5-131">win:UInt64</span></span>|<span data-ttu-id="b6ce5-132">虛設常式的旗標：</span><span class="sxs-lookup"><span data-stu-id="b6ce5-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="b6ce5-133">0x1 - 反向 interop。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="b6ce5-134">0x2 - COM interop。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="b6ce5-135">0x4 - NGen.exe 所產生的虛設常式。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="b6ce5-136">0x8 - 委派。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="b6ce5-137">0x10 - 變數引數。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="b6ce5-138">0x20 - Unmanaged 被呼叫者。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="b6ce5-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="b6ce5-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="b6ce5-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b6ce5-140">win:UInt32</span></span>|<span data-ttu-id="b6ce5-141">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="b6ce5-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="b6ce5-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="b6ce5-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b6ce5-143">win:UnicodeString</span></span>|<span data-ttu-id="b6ce5-144">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="b6ce5-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="b6ce5-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="b6ce5-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b6ce5-146">win:UnicodeString</span></span>|<span data-ttu-id="b6ce5-147">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="b6ce5-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="b6ce5-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="b6ce5-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b6ce5-149">win:UnicodeString</span></span>|<span data-ttu-id="b6ce5-150">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="b6ce5-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="b6ce5-151">NativeMethodSignature</span></span>|<span data-ttu-id="b6ce5-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b6ce5-152">win:UnicodeString</span></span>|<span data-ttu-id="b6ce5-153">原生方法簽章。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-153">The native method signature.</span></span>|  
|<span data-ttu-id="b6ce5-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="b6ce5-154">StubMethodSignature</span></span>|<span data-ttu-id="b6ce5-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b6ce5-155">win:UnicodeString</span></span>|<span data-ttu-id="b6ce5-156">虛設常式方法簽章。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-156">The stub method signature.</span></span>|  
|<span data-ttu-id="b6ce5-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="b6ce5-157">StubMethodILCode</span></span>|<span data-ttu-id="b6ce5-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b6ce5-158">win:UnicodeString</span></span>|<span data-ttu-id="b6ce5-159">虛設常式方法的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="b6ce5-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b6ce5-160">ClrInstanceID</span></span>|<span data-ttu-id="b6ce5-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="b6ce5-161">win:UInt16</span></span>|<span data-ttu-id="b6ce5-162">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="b6ce5-163">回到頁首</span><span class="sxs-lookup"><span data-stu-id="b6ce5-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="b6ce5-164">ILStubCacheHit 事件</span><span class="sxs-lookup"><span data-stu-id="b6ce5-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="b6ce5-165">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="b6ce5-166">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="b6ce5-166">Keyword for raising the event</span></span>|<span data-ttu-id="b6ce5-167">層級</span><span class="sxs-lookup"><span data-stu-id="b6ce5-167">Level</span></span>|  
|-----------------------------------|-----------|  
|`InteropKeyword` <span data-ttu-id="b6ce5-168">(0x2000)</span><span class="sxs-lookup"><span data-stu-id="b6ce5-168">(0x2000)</span></span>|<span data-ttu-id="b6ce5-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="b6ce5-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="b6ce5-170">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="b6ce5-171">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="b6ce5-171">Event</span></span>|<span data-ttu-id="b6ce5-172">事件 ID</span><span class="sxs-lookup"><span data-stu-id="b6ce5-172">Event ID</span></span>|<span data-ttu-id="b6ce5-173">引發的時機</span><span class="sxs-lookup"><span data-stu-id="b6ce5-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="b6ce5-174">89</span><span class="sxs-lookup"><span data-stu-id="b6ce5-174">89</span></span>|<span data-ttu-id="b6ce5-175">已存取 MSIL 快取。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="b6ce5-176">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="b6ce5-177">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="b6ce5-177">Field name</span></span>|<span data-ttu-id="b6ce5-178">資料類型</span><span class="sxs-lookup"><span data-stu-id="b6ce5-178">Data type</span></span>|<span data-ttu-id="b6ce5-179">描述</span><span class="sxs-lookup"><span data-stu-id="b6ce5-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="b6ce5-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="b6ce5-180">ModuleID</span></span>|<span data-ttu-id="b6ce5-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="b6ce5-181">win:UInt16</span></span>|<span data-ttu-id="b6ce5-182">模組識別項。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-182">The module identifier.</span></span>|  
|<span data-ttu-id="b6ce5-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="b6ce5-183">StubMethodID</span></span>|<span data-ttu-id="b6ce5-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="b6ce5-184">win:UInt64</span></span>|<span data-ttu-id="b6ce5-185">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="b6ce5-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="b6ce5-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="b6ce5-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="b6ce5-187">win:UInt32</span></span>|<span data-ttu-id="b6ce5-188">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="b6ce5-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="b6ce5-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="b6ce5-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b6ce5-190">win:UnicodeString</span></span>|<span data-ttu-id="b6ce5-191">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="b6ce5-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="b6ce5-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="b6ce5-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b6ce5-193">win:UnicodeString</span></span>|<span data-ttu-id="b6ce5-194">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="b6ce5-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="b6ce5-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="b6ce5-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="b6ce5-196">win:UnicodeString</span></span>|<span data-ttu-id="b6ce5-197">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="b6ce5-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="b6ce5-198">ClrInstanceID</span></span>|<span data-ttu-id="b6ce5-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="b6ce5-199">win:UInt16</span></span>|<span data-ttu-id="b6ce5-200">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="b6ce5-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="b6ce5-201">回到頁首</span><span class="sxs-lookup"><span data-stu-id="b6ce5-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="b6ce5-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6ce5-202">See also</span></span>

- [<span data-ttu-id="b6ce5-203">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="b6ce5-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
