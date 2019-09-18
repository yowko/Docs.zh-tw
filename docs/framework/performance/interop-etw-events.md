---
title: Interop ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 787c6221b651a53dbb932a5a9d0edea123e1d97d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046428"
---
# <a name="interop-etw-events"></a><span data-ttu-id="83586-102">Interop ETW 事件</span><span class="sxs-lookup"><span data-stu-id="83586-102">Interop ETW Events</span></span>
<a name="top"></a> <span data-ttu-id="83586-103">Interop 事件會擷取 Microsoft 中繼語言 (MSIL) Stub 之產生和快取的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="83586-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  
  
 <span data-ttu-id="83586-104">這個類別包含下列事件：</span><span class="sxs-lookup"><span data-stu-id="83586-104">This category consists of the following events:</span></span>  
  
- [<span data-ttu-id="83586-105">ILStubGenerated 事件</span><span class="sxs-lookup"><span data-stu-id="83586-105">ILStubGenerated Event</span></span>](#ilstubgenerated_event)  
  
- [<span data-ttu-id="83586-106">ILStubCacheHit 事件</span><span class="sxs-lookup"><span data-stu-id="83586-106">ILStubCacheHit Event</span></span>](#ilstubcachehit_event)  
  
<a name="ilstubgenerated_event"></a>   
## <a name="ilstubgenerated-event"></a><span data-ttu-id="83586-107">ILStubGenerated 事件</span><span class="sxs-lookup"><span data-stu-id="83586-107">ILStubGenerated Event</span></span>  
 <span data-ttu-id="83586-108">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="83586-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="83586-109">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="83586-109">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="83586-110">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="83586-110">Keyword for raising the event</span></span>|<span data-ttu-id="83586-111">層級</span><span class="sxs-lookup"><span data-stu-id="83586-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="83586-112">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="83586-112">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="83586-113">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="83586-113">Informational(4)</span></span>|  
  
 <span data-ttu-id="83586-114">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="83586-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="83586-115">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="83586-115">Event</span></span>|<span data-ttu-id="83586-116">事件 ID</span><span class="sxs-lookup"><span data-stu-id="83586-116">Event ID</span></span>|<span data-ttu-id="83586-117">引發的時機</span><span class="sxs-lookup"><span data-stu-id="83586-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="83586-118">88</span><span class="sxs-lookup"><span data-stu-id="83586-118">88</span></span>|<span data-ttu-id="83586-119">已產生 MSIL 虛設常式。</span><span class="sxs-lookup"><span data-stu-id="83586-119">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="83586-120">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="83586-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="83586-121">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="83586-121">Field name</span></span>|<span data-ttu-id="83586-122">資料類型</span><span class="sxs-lookup"><span data-stu-id="83586-122">Data type</span></span>|<span data-ttu-id="83586-123">描述</span><span class="sxs-lookup"><span data-stu-id="83586-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="83586-124">ModuleID</span><span class="sxs-lookup"><span data-stu-id="83586-124">ModuleID</span></span>|<span data-ttu-id="83586-125">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="83586-125">win:UInt16</span></span>|<span data-ttu-id="83586-126">模組識別項。</span><span class="sxs-lookup"><span data-stu-id="83586-126">The module identifier.</span></span>|  
|<span data-ttu-id="83586-127">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="83586-127">StubMethodID</span></span>|<span data-ttu-id="83586-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="83586-128">win:UInt64</span></span>|<span data-ttu-id="83586-129">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="83586-129">The stub method identifier.</span></span>|  
|<span data-ttu-id="83586-130">StubFlags</span><span class="sxs-lookup"><span data-stu-id="83586-130">StubFlags</span></span>|<span data-ttu-id="83586-131">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="83586-131">win:UInt64</span></span>|<span data-ttu-id="83586-132">虛設常式的旗標：</span><span class="sxs-lookup"><span data-stu-id="83586-132">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="83586-133">0x1 - 反向 interop。</span><span class="sxs-lookup"><span data-stu-id="83586-133">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="83586-134">0x2 - COM interop。</span><span class="sxs-lookup"><span data-stu-id="83586-134">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="83586-135">0x4 - NGen.exe 所產生的虛設常式。</span><span class="sxs-lookup"><span data-stu-id="83586-135">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="83586-136">0x8 - 委派。</span><span class="sxs-lookup"><span data-stu-id="83586-136">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="83586-137">0x10-變數引數。</span><span class="sxs-lookup"><span data-stu-id="83586-137">0x10 - Variable argument.</span></span><br /><br /> <span data-ttu-id="83586-138">0x20 - Unmanaged 被呼叫者。</span><span class="sxs-lookup"><span data-stu-id="83586-138">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="83586-139">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="83586-139">ManagedInteropMethodToken</span></span>|<span data-ttu-id="83586-140">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="83586-140">win:UInt32</span></span>|<span data-ttu-id="83586-141">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="83586-141">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="83586-142">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="83586-142">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="83586-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="83586-143">win:UnicodeString</span></span>|<span data-ttu-id="83586-144">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="83586-144">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="83586-145">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="83586-145">ManagedInteropMethodName</span></span>|<span data-ttu-id="83586-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="83586-146">win:UnicodeString</span></span>|<span data-ttu-id="83586-147">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="83586-147">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="83586-148">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="83586-148">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="83586-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="83586-149">win:UnicodeString</span></span>|<span data-ttu-id="83586-150">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="83586-150">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="83586-151">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="83586-151">NativeMethodSignature</span></span>|<span data-ttu-id="83586-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="83586-152">win:UnicodeString</span></span>|<span data-ttu-id="83586-153">原生方法簽章。</span><span class="sxs-lookup"><span data-stu-id="83586-153">The native method signature.</span></span>|  
|<span data-ttu-id="83586-154">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="83586-154">StubMethodSignature</span></span>|<span data-ttu-id="83586-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="83586-155">win:UnicodeString</span></span>|<span data-ttu-id="83586-156">虛設常式方法簽章。</span><span class="sxs-lookup"><span data-stu-id="83586-156">The stub method signature.</span></span>|  
|<span data-ttu-id="83586-157">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="83586-157">StubMethodILCode</span></span>|<span data-ttu-id="83586-158">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="83586-158">win:UnicodeString</span></span>|<span data-ttu-id="83586-159">虛設常式方法的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="83586-159">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="83586-160">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="83586-160">ClrInstanceID</span></span>|<span data-ttu-id="83586-161">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="83586-161">win:UInt16</span></span>|<span data-ttu-id="83586-162">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="83586-162">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="83586-163">回到頁首</span><span class="sxs-lookup"><span data-stu-id="83586-163">Back to top</span></span>](#top)  
  
<a name="ilstubcachehit_event"></a>   
## <a name="ilstubcachehit-event"></a><span data-ttu-id="83586-164">ILStubCacheHit 事件</span><span class="sxs-lookup"><span data-stu-id="83586-164">ILStubCacheHit Event</span></span>  
 <span data-ttu-id="83586-165">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="83586-165">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="83586-166">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="83586-166">Keyword for raising the event</span></span>|<span data-ttu-id="83586-167">層級</span><span class="sxs-lookup"><span data-stu-id="83586-167">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="83586-168">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="83586-168">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="83586-169">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="83586-169">Informational(4)</span></span>|  
  
 <span data-ttu-id="83586-170">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="83586-170">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="83586-171">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="83586-171">Event</span></span>|<span data-ttu-id="83586-172">事件 ID</span><span class="sxs-lookup"><span data-stu-id="83586-172">Event ID</span></span>|<span data-ttu-id="83586-173">引發的時機</span><span class="sxs-lookup"><span data-stu-id="83586-173">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="83586-174">89</span><span class="sxs-lookup"><span data-stu-id="83586-174">89</span></span>|<span data-ttu-id="83586-175">已存取 MSIL 快取。</span><span class="sxs-lookup"><span data-stu-id="83586-175">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="83586-176">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="83586-176">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="83586-177">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="83586-177">Field name</span></span>|<span data-ttu-id="83586-178">資料類型</span><span class="sxs-lookup"><span data-stu-id="83586-178">Data type</span></span>|<span data-ttu-id="83586-179">描述</span><span class="sxs-lookup"><span data-stu-id="83586-179">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="83586-180">ModuleID</span><span class="sxs-lookup"><span data-stu-id="83586-180">ModuleID</span></span>|<span data-ttu-id="83586-181">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="83586-181">win:UInt16</span></span>|<span data-ttu-id="83586-182">模組識別項。</span><span class="sxs-lookup"><span data-stu-id="83586-182">The module identifier.</span></span>|  
|<span data-ttu-id="83586-183">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="83586-183">StubMethodID</span></span>|<span data-ttu-id="83586-184">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="83586-184">win:UInt64</span></span>|<span data-ttu-id="83586-185">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="83586-185">The stub method identifier.</span></span>|  
|<span data-ttu-id="83586-186">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="83586-186">ManagedInteropMethodToken</span></span>|<span data-ttu-id="83586-187">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="83586-187">win:UInt32</span></span>|<span data-ttu-id="83586-188">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="83586-188">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="83586-189">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="83586-189">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="83586-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="83586-190">win:UnicodeString</span></span>|<span data-ttu-id="83586-191">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="83586-191">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="83586-192">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="83586-192">ManagedInteropMethodName</span></span>|<span data-ttu-id="83586-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="83586-193">win:UnicodeString</span></span>|<span data-ttu-id="83586-194">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="83586-194">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="83586-195">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="83586-195">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="83586-196">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="83586-196">win:UnicodeString</span></span>|<span data-ttu-id="83586-197">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="83586-197">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="83586-198">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="83586-198">ClrInstanceID</span></span>|<span data-ttu-id="83586-199">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="83586-199">win:UInt16</span></span>|<span data-ttu-id="83586-200">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="83586-200">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
 [<span data-ttu-id="83586-201">回到頁首</span><span class="sxs-lookup"><span data-stu-id="83586-201">Back to top</span></span>](#top)  
  
## <a name="see-also"></a><span data-ttu-id="83586-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="83586-202">See also</span></span>

- [<span data-ttu-id="83586-203">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="83586-203">CLR ETW Events</span></span>](clr-etw-events.md)
