---
title: "Interop ETW 事件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 55097e38161ea5c76f4e46584241344ec5a52cb9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="interop-etw-events"></a><span data-ttu-id="e6a88-102">Interop ETW 事件</span><span class="sxs-lookup"><span data-stu-id="e6a88-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="e6a88-103">Interop 事件會擷取 Microsoft 中繼語言 (MSIL) Stub 之產生和快取的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e6a88-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="e6a88-104">這個類別包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="e6a88-104">This category consists of the following events:</span></span>  
  
-   [<span data-ttu-id="e6a88-105">ILStubGenerated 事件</span><span class="sxs-lookup"><span data-stu-id="e6a88-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
-   [<span data-ttu-id="e6a88-106">ILStubCacheHit 事件</span><span class="sxs-lookup"><span data-stu-id="e6a88-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="e6a88-107">ILStubGenerated 事件</span><span class="sxs-lookup"><span data-stu-id="e6a88-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="e6a88-108">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="e6a88-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="e6a88-109">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="e6a88-109">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="e6a88-110">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="e6a88-110">Keyword for raising the event</span></span>|<span data-ttu-id="e6a88-111">層級</span><span class="sxs-lookup"><span data-stu-id="e6a88-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e6a88-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="e6a88-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="e6a88-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="e6a88-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="e6a88-114">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="e6a88-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e6a88-115">事件</span><span class="sxs-lookup"><span data-stu-id="e6a88-115">Event</span></span>|<span data-ttu-id="e6a88-116">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e6a88-116">Event ID</span></span>|<span data-ttu-id="e6a88-117">引發的時機</span><span class="sxs-lookup"><span data-stu-id="e6a88-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="e6a88-118">88</span><span class="sxs-lookup"><span data-stu-id="e6a88-118">88</span></span>|<span data-ttu-id="e6a88-119">已產生 MSIL 虛設常式。</span><span class="sxs-lookup"><span data-stu-id="e6a88-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="e6a88-120">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="e6a88-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e6a88-121">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="e6a88-121">Field name</span></span>|<span data-ttu-id="e6a88-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="e6a88-122">Data type</span></span>|<span data-ttu-id="e6a88-123">描述</span><span class="sxs-lookup"><span data-stu-id="e6a88-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e6a88-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="e6a88-124">ModuleID</span></span>|<span data-ttu-id="e6a88-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e6a88-125">win:UInt16</span></span>|<span data-ttu-id="e6a88-126">模組識別項。</span><span class="sxs-lookup"><span data-stu-id="e6a88-126">The module identifier.</span></span>|  
|<span data-ttu-id="e6a88-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="e6a88-127">StubMethodID</span></span>|<span data-ttu-id="e6a88-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e6a88-128">win:UInt64</span></span>|<span data-ttu-id="e6a88-129">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="e6a88-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="e6a88-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="e6a88-130">StubFlags</span></span>|<span data-ttu-id="e6a88-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e6a88-131">win:UInt64</span></span>|<span data-ttu-id="e6a88-132">虛設常式的旗標：</span><span class="sxs-lookup"><span data-stu-id="e6a88-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="e6a88-133">0x1 - 反向 interop。</span><span class="sxs-lookup"><span data-stu-id="e6a88-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="e6a88-134">0x2 - COM interop。</span><span class="sxs-lookup"><span data-stu-id="e6a88-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="e6a88-135">0x4 - NGen.exe 所產生的虛設常式。</span><span class="sxs-lookup"><span data-stu-id="e6a88-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="e6a88-136">0x8 - 委派。</span><span class="sxs-lookup"><span data-stu-id="e6a88-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="e6a88-137">0x10 - 變數引數。</span><span class="sxs-lookup"><span data-stu-id="e6a88-137">0x10 - Variable arrgument.</span></span><br /><br /> <span data-ttu-id="e6a88-138">0x20 - Unmanaged 被呼叫者。</span><span class="sxs-lookup"><span data-stu-id="e6a88-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="e6a88-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="e6a88-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="e6a88-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e6a88-140">win:UInt32</span></span>|<span data-ttu-id="e6a88-141">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e6a88-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="e6a88-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="e6a88-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="e6a88-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="e6a88-143">win:UnicodeString</span></span>|<span data-ttu-id="e6a88-144">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="e6a88-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="e6a88-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="e6a88-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="e6a88-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="e6a88-146">win:UnicodeString</span></span>|<span data-ttu-id="e6a88-147">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="e6a88-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="e6a88-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="e6a88-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="e6a88-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="e6a88-149">win:UnicodeString</span></span>|<span data-ttu-id="e6a88-150">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="e6a88-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="e6a88-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="e6a88-151">NativeMethodSignature</span></span>|<span data-ttu-id="e6a88-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="e6a88-152">win:UnicodeString</span></span>|<span data-ttu-id="e6a88-153">原生方法簽章。</span><span class="sxs-lookup"><span data-stu-id="e6a88-153">The native method signature.</span></span>|  
|<span data-ttu-id="e6a88-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="e6a88-154">StubMethodSignature</span></span>|<span data-ttu-id="e6a88-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="e6a88-155">win:UnicodeString</span></span>|<span data-ttu-id="e6a88-156">虛設常式方法簽章。</span><span class="sxs-lookup"><span data-stu-id="e6a88-156">The stub method signature.</span></span>|  
|<span data-ttu-id="e6a88-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="e6a88-157">StubMethodILCode</span></span>|<span data-ttu-id="e6a88-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="e6a88-158">win:UnicodeString</span></span>|<span data-ttu-id="e6a88-159">虛設常式方法的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="e6a88-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="e6a88-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e6a88-160">ClrInstanceID</span></span>|<span data-ttu-id="e6a88-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e6a88-161">win:UInt16</span></span>|<span data-ttu-id="e6a88-162">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e6a88-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="e6a88-163">回到頁首</span><span class="sxs-lookup"><span data-stu-id="e6a88-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="e6a88-164">ILStubCacheHit 事件</span><span class="sxs-lookup"><span data-stu-id="e6a88-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="e6a88-165">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="e6a88-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="e6a88-166">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="e6a88-166">Keyword for raising the event</span></span>|<span data-ttu-id="e6a88-167">層級</span><span class="sxs-lookup"><span data-stu-id="e6a88-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e6a88-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="e6a88-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="e6a88-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="e6a88-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="e6a88-170">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="e6a88-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="e6a88-171">事件</span><span class="sxs-lookup"><span data-stu-id="e6a88-171">Event</span></span>|<span data-ttu-id="e6a88-172">事件 ID</span><span class="sxs-lookup"><span data-stu-id="e6a88-172">Event ID</span></span>|<span data-ttu-id="e6a88-173">引發的時機</span><span class="sxs-lookup"><span data-stu-id="e6a88-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="e6a88-174">89</span><span class="sxs-lookup"><span data-stu-id="e6a88-174">89</span></span>|<span data-ttu-id="e6a88-175">已存取 MSIL 快取。</span><span class="sxs-lookup"><span data-stu-id="e6a88-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="e6a88-176">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="e6a88-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="e6a88-177">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="e6a88-177">Field name</span></span>|<span data-ttu-id="e6a88-178">資料類型</span><span class="sxs-lookup"><span data-stu-id="e6a88-178">Data type</span></span>|<span data-ttu-id="e6a88-179">描述</span><span class="sxs-lookup"><span data-stu-id="e6a88-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e6a88-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="e6a88-180">ModuleID</span></span>|<span data-ttu-id="e6a88-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e6a88-181">win:UInt16</span></span>|<span data-ttu-id="e6a88-182">模組識別項。</span><span class="sxs-lookup"><span data-stu-id="e6a88-182">The module identifier.</span></span>|  
|<span data-ttu-id="e6a88-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="e6a88-183">StubMethodID</span></span>|<span data-ttu-id="e6a88-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="e6a88-184">win:UInt64</span></span>|<span data-ttu-id="e6a88-185">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="e6a88-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="e6a88-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="e6a88-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="e6a88-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="e6a88-187">win:UInt32</span></span>|<span data-ttu-id="e6a88-188">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="e6a88-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="e6a88-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="e6a88-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="e6a88-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="e6a88-190">win:UnicodeString</span></span>|<span data-ttu-id="e6a88-191">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="e6a88-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="e6a88-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="e6a88-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="e6a88-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="e6a88-193">win:UnicodeString</span></span>|<span data-ttu-id="e6a88-194">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="e6a88-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="e6a88-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="e6a88-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="e6a88-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="e6a88-196">win:UnicodeString</span></span>|<span data-ttu-id="e6a88-197">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="e6a88-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="e6a88-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e6a88-198">ClrInstanceID</span></span>|<span data-ttu-id="e6a88-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="e6a88-199">win:UInt16</span></span>|<span data-ttu-id="e6a88-200">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="e6a88-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="e6a88-201">回到頁首</span><span class="sxs-lookup"><span data-stu-id="e6a88-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="e6a88-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6a88-202">See Also</span></span>  
 [<span data-ttu-id="e6a88-203">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="e6a88-203">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
