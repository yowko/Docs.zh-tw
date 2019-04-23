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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083604"
---
# <a name="interop-etw-events"></a><span data-ttu-id="79518-102">Interop ETW 事件</span><span class="sxs-lookup"><span data-stu-id="79518-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="79518-103">Interop 事件會擷取 Microsoft 中繼語言 (MSIL) Stub 之產生和快取的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="79518-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="79518-104">這個類別包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="79518-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="79518-105">ILStubGenerated 事件</span><span class="sxs-lookup"><span data-stu-id="79518-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="79518-106">ILStubCacheHit 事件</span><span class="sxs-lookup"><span data-stu-id="79518-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="79518-107">ILStubGenerated 事件</span><span class="sxs-lookup"><span data-stu-id="79518-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="79518-108">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="79518-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="79518-109">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="79518-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="79518-110">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="79518-110">Keyword for raising the event</span></span>|<span data-ttu-id="79518-111">層級</span><span class="sxs-lookup"><span data-stu-id="79518-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="79518-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="79518-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="79518-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="79518-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="79518-114">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="79518-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="79518-115">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="79518-115">Event</span></span>|<span data-ttu-id="79518-116">事件 ID</span><span class="sxs-lookup"><span data-stu-id="79518-116">Event ID</span></span>|<span data-ttu-id="79518-117">引發的時機</span><span class="sxs-lookup"><span data-stu-id="79518-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="79518-118">88</span><span class="sxs-lookup"><span data-stu-id="79518-118">88</span></span>|<span data-ttu-id="79518-119">已產生 MSIL 虛設常式。</span><span class="sxs-lookup"><span data-stu-id="79518-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="79518-120">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="79518-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="79518-121">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="79518-121">Field name</span></span>|<span data-ttu-id="79518-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="79518-122">Data type</span></span>|<span data-ttu-id="79518-123">描述</span><span class="sxs-lookup"><span data-stu-id="79518-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="79518-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="79518-124">ModuleID</span></span>|<span data-ttu-id="79518-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="79518-125">win:UInt16</span></span>|<span data-ttu-id="79518-126">模組識別項。</span><span class="sxs-lookup"><span data-stu-id="79518-126">The module identifier.</span></span>|  
|<span data-ttu-id="79518-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="79518-127">StubMethodID</span></span>|<span data-ttu-id="79518-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="79518-128">win:UInt64</span></span>|<span data-ttu-id="79518-129">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="79518-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="79518-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="79518-130">StubFlags</span></span>|<span data-ttu-id="79518-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="79518-131">win:UInt64</span></span>|<span data-ttu-id="79518-132">虛設常式的旗標：</span><span class="sxs-lookup"><span data-stu-id="79518-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="79518-133">0x1 - 反向 interop。</span><span class="sxs-lookup"><span data-stu-id="79518-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="79518-134">0x2 - COM interop。</span><span class="sxs-lookup"><span data-stu-id="79518-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="79518-135">0x4 - NGen.exe 所產生的虛設常式。</span><span class="sxs-lookup"><span data-stu-id="79518-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="79518-136">0x8 - 委派。</span><span class="sxs-lookup"><span data-stu-id="79518-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="79518-137">0x10 - 變數引數。</span><span class="sxs-lookup"><span data-stu-id="79518-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="79518-138">0x20 - Unmanaged 被呼叫者。</span><span class="sxs-lookup"><span data-stu-id="79518-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="79518-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="79518-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="79518-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="79518-140">win:UInt32</span></span>|<span data-ttu-id="79518-141">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="79518-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="79518-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="79518-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="79518-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="79518-143">win:UnicodeString</span></span>|<span data-ttu-id="79518-144">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="79518-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="79518-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="79518-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="79518-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="79518-146">win:UnicodeString</span></span>|<span data-ttu-id="79518-147">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="79518-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="79518-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="79518-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="79518-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="79518-149">win:UnicodeString</span></span>|<span data-ttu-id="79518-150">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="79518-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="79518-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="79518-151">NativeMethodSignature</span></span>|<span data-ttu-id="79518-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="79518-152">win:UnicodeString</span></span>|<span data-ttu-id="79518-153">原生方法簽章。</span><span class="sxs-lookup"><span data-stu-id="79518-153">The native method signature.</span></span>|  
|<span data-ttu-id="79518-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="79518-154">StubMethodSignature</span></span>|<span data-ttu-id="79518-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="79518-155">win:UnicodeString</span></span>|<span data-ttu-id="79518-156">虛設常式方法簽章。</span><span class="sxs-lookup"><span data-stu-id="79518-156">The stub method signature.</span></span>|  
|<span data-ttu-id="79518-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="79518-157">StubMethodILCode</span></span>|<span data-ttu-id="79518-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="79518-158">win:UnicodeString</span></span>|<span data-ttu-id="79518-159">虛設常式方法的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="79518-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="79518-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="79518-160">ClrInstanceID</span></span>|<span data-ttu-id="79518-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="79518-161">win:UInt16</span></span>|<span data-ttu-id="79518-162">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="79518-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="79518-163">回到頁首</span><span class="sxs-lookup"><span data-stu-id="79518-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="79518-164">ILStubCacheHit 事件</span><span class="sxs-lookup"><span data-stu-id="79518-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="79518-165">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="79518-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="79518-166">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="79518-166">Keyword for raising the event</span></span>|<span data-ttu-id="79518-167">層級</span><span class="sxs-lookup"><span data-stu-id="79518-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="79518-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="79518-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="79518-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="79518-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="79518-170">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="79518-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="79518-171">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="79518-171">Event</span></span>|<span data-ttu-id="79518-172">事件 ID</span><span class="sxs-lookup"><span data-stu-id="79518-172">Event ID</span></span>|<span data-ttu-id="79518-173">引發的時機</span><span class="sxs-lookup"><span data-stu-id="79518-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="79518-174">89</span><span class="sxs-lookup"><span data-stu-id="79518-174">89</span></span>|<span data-ttu-id="79518-175">已存取 MSIL 快取。</span><span class="sxs-lookup"><span data-stu-id="79518-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="79518-176">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="79518-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="79518-177">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="79518-177">Field name</span></span>|<span data-ttu-id="79518-178">資料類型</span><span class="sxs-lookup"><span data-stu-id="79518-178">Data type</span></span>|<span data-ttu-id="79518-179">描述</span><span class="sxs-lookup"><span data-stu-id="79518-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="79518-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="79518-180">ModuleID</span></span>|<span data-ttu-id="79518-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="79518-181">win:UInt16</span></span>|<span data-ttu-id="79518-182">模組識別項。</span><span class="sxs-lookup"><span data-stu-id="79518-182">The module identifier.</span></span>|  
|<span data-ttu-id="79518-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="79518-183">StubMethodID</span></span>|<span data-ttu-id="79518-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="79518-184">win:UInt64</span></span>|<span data-ttu-id="79518-185">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="79518-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="79518-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="79518-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="79518-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="79518-187">win:UInt32</span></span>|<span data-ttu-id="79518-188">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="79518-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="79518-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="79518-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="79518-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="79518-190">win:UnicodeString</span></span>|<span data-ttu-id="79518-191">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="79518-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="79518-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="79518-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="79518-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="79518-193">win:UnicodeString</span></span>|<span data-ttu-id="79518-194">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="79518-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="79518-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="79518-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="79518-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="79518-196">win:UnicodeString</span></span>|<span data-ttu-id="79518-197">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="79518-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="79518-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="79518-198">ClrInstanceID</span></span>|<span data-ttu-id="79518-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="79518-199">win:UInt16</span></span>|<span data-ttu-id="79518-200">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="79518-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="79518-201">回到頁首</span><span class="sxs-lookup"><span data-stu-id="79518-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="79518-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79518-202">See also</span></span>

- [<span data-ttu-id="79518-203">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="79518-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
