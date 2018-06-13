---
title: Interop ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3bc9a90e9d889673d8f67e4f9158edebcb65235b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396363"
---
# <a name="interop-etw-events"></a><span data-ttu-id="90c53-102">Interop ETW 事件</span><span class="sxs-lookup"><span data-stu-id="90c53-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="90c53-103">Interop 事件會擷取 Microsoft 中繼語言 (MSIL) Stub 之產生和快取的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="90c53-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="90c53-104">這個類別包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="90c53-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="90c53-105">ILStubGenerated 事件</span><span class="sxs-lookup"><span data-stu-id="90c53-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="90c53-106">ILStubCacheHit 事件</span><span class="sxs-lookup"><span data-stu-id="90c53-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="90c53-107">ILStubGenerated 事件</span><span class="sxs-lookup"><span data-stu-id="90c53-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="90c53-108">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="90c53-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="90c53-109">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="90c53-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="90c53-110">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="90c53-110">Keyword for raising the event</span></span>|<span data-ttu-id="90c53-111">層級</span><span class="sxs-lookup"><span data-stu-id="90c53-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90c53-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="90c53-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="90c53-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="90c53-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="90c53-114">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="90c53-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90c53-115">事件</span><span class="sxs-lookup"><span data-stu-id="90c53-115">Event</span></span>|<span data-ttu-id="90c53-116">事件 ID</span><span class="sxs-lookup"><span data-stu-id="90c53-116">Event ID</span></span>|<span data-ttu-id="90c53-117">引發的時機</span><span class="sxs-lookup"><span data-stu-id="90c53-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="90c53-118">88</span><span class="sxs-lookup"><span data-stu-id="90c53-118">88</span></span>|<span data-ttu-id="90c53-119">已產生 MSIL 虛設常式。</span><span class="sxs-lookup"><span data-stu-id="90c53-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="90c53-120">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="90c53-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90c53-121">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="90c53-121">Field name</span></span>|<span data-ttu-id="90c53-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="90c53-122">Data type</span></span>|<span data-ttu-id="90c53-123">描述</span><span class="sxs-lookup"><span data-stu-id="90c53-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90c53-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="90c53-124">ModuleID</span></span>|<span data-ttu-id="90c53-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="90c53-125">win:UInt16</span></span>|<span data-ttu-id="90c53-126">模組識別項。</span><span class="sxs-lookup"><span data-stu-id="90c53-126">The module identifier.</span></span>|  
|<span data-ttu-id="90c53-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="90c53-127">StubMethodID</span></span>|<span data-ttu-id="90c53-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="90c53-128">win:UInt64</span></span>|<span data-ttu-id="90c53-129">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="90c53-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="90c53-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="90c53-130">StubFlags</span></span>|<span data-ttu-id="90c53-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="90c53-131">win:UInt64</span></span>|<span data-ttu-id="90c53-132">虛設常式的旗標：</span><span class="sxs-lookup"><span data-stu-id="90c53-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="90c53-133">0x1 - 反向 interop。</span><span class="sxs-lookup"><span data-stu-id="90c53-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="90c53-134">0x2 - COM interop。</span><span class="sxs-lookup"><span data-stu-id="90c53-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="90c53-135">0x4 - NGen.exe 所產生的虛設常式。</span><span class="sxs-lookup"><span data-stu-id="90c53-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="90c53-136">0x8 - 委派。</span><span class="sxs-lookup"><span data-stu-id="90c53-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="90c53-137">0x10 - 變數引數。</span><span class="sxs-lookup"><span data-stu-id="90c53-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="90c53-138">0x20 - Unmanaged 被呼叫者。</span><span class="sxs-lookup"><span data-stu-id="90c53-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="90c53-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="90c53-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="90c53-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="90c53-140">win:UInt32</span></span>|<span data-ttu-id="90c53-141">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="90c53-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="90c53-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="90c53-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="90c53-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="90c53-143">win:UnicodeString</span></span>|<span data-ttu-id="90c53-144">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="90c53-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="90c53-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="90c53-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="90c53-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="90c53-146">win:UnicodeString</span></span>|<span data-ttu-id="90c53-147">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="90c53-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="90c53-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="90c53-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="90c53-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="90c53-149">win:UnicodeString</span></span>|<span data-ttu-id="90c53-150">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="90c53-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="90c53-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="90c53-151">NativeMethodSignature</span></span>|<span data-ttu-id="90c53-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="90c53-152">win:UnicodeString</span></span>|<span data-ttu-id="90c53-153">原生方法簽章。</span><span class="sxs-lookup"><span data-stu-id="90c53-153">The native method signature.</span></span>|  
|<span data-ttu-id="90c53-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="90c53-154">StubMethodSignature</span></span>|<span data-ttu-id="90c53-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="90c53-155">win:UnicodeString</span></span>|<span data-ttu-id="90c53-156">虛設常式方法簽章。</span><span class="sxs-lookup"><span data-stu-id="90c53-156">The stub method signature.</span></span>|  
|<span data-ttu-id="90c53-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="90c53-157">StubMethodILCode</span></span>|<span data-ttu-id="90c53-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="90c53-158">win:UnicodeString</span></span>|<span data-ttu-id="90c53-159">虛設常式方法的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="90c53-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="90c53-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90c53-160">ClrInstanceID</span></span>|<span data-ttu-id="90c53-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="90c53-161">win:UInt16</span></span>|<span data-ttu-id="90c53-162">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="90c53-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="90c53-163">回到頁首</span><span class="sxs-lookup"><span data-stu-id="90c53-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="90c53-164">ILStubCacheHit 事件</span><span class="sxs-lookup"><span data-stu-id="90c53-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="90c53-165">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="90c53-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="90c53-166">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="90c53-166">Keyword for raising the event</span></span>|<span data-ttu-id="90c53-167">層級</span><span class="sxs-lookup"><span data-stu-id="90c53-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="90c53-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="90c53-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="90c53-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="90c53-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="90c53-170">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="90c53-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="90c53-171">事件</span><span class="sxs-lookup"><span data-stu-id="90c53-171">Event</span></span>|<span data-ttu-id="90c53-172">事件 ID</span><span class="sxs-lookup"><span data-stu-id="90c53-172">Event ID</span></span>|<span data-ttu-id="90c53-173">引發的時機</span><span class="sxs-lookup"><span data-stu-id="90c53-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="90c53-174">89</span><span class="sxs-lookup"><span data-stu-id="90c53-174">89</span></span>|<span data-ttu-id="90c53-175">已存取 MSIL 快取。</span><span class="sxs-lookup"><span data-stu-id="90c53-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="90c53-176">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="90c53-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="90c53-177">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="90c53-177">Field name</span></span>|<span data-ttu-id="90c53-178">資料類型</span><span class="sxs-lookup"><span data-stu-id="90c53-178">Data type</span></span>|<span data-ttu-id="90c53-179">描述</span><span class="sxs-lookup"><span data-stu-id="90c53-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="90c53-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="90c53-180">ModuleID</span></span>|<span data-ttu-id="90c53-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="90c53-181">win:UInt16</span></span>|<span data-ttu-id="90c53-182">模組識別項。</span><span class="sxs-lookup"><span data-stu-id="90c53-182">The module identifier.</span></span>|  
|<span data-ttu-id="90c53-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="90c53-183">StubMethodID</span></span>|<span data-ttu-id="90c53-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="90c53-184">win:UInt64</span></span>|<span data-ttu-id="90c53-185">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="90c53-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="90c53-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="90c53-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="90c53-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="90c53-187">win:UInt32</span></span>|<span data-ttu-id="90c53-188">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="90c53-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="90c53-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="90c53-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="90c53-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="90c53-190">win:UnicodeString</span></span>|<span data-ttu-id="90c53-191">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="90c53-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="90c53-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="90c53-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="90c53-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="90c53-193">win:UnicodeString</span></span>|<span data-ttu-id="90c53-194">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="90c53-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="90c53-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="90c53-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="90c53-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="90c53-196">win:UnicodeString</span></span>|<span data-ttu-id="90c53-197">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="90c53-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="90c53-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="90c53-198">ClrInstanceID</span></span>|<span data-ttu-id="90c53-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="90c53-199">win:UInt16</span></span>|<span data-ttu-id="90c53-200">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="90c53-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="90c53-201">回到頁首</span><span class="sxs-lookup"><span data-stu-id="90c53-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="90c53-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90c53-202">See Also</span></span>  
 [<span data-ttu-id="90c53-203">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="90c53-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
