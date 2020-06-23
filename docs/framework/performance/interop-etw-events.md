---
title: Interop ETW 事件
description: 請參閱 interop ETW （Windows 事件追蹤）事件，其會在 .NET 中捕捉 Microsoft 中繼語言（MSIL） stub 產生 & 快取的相關資訊。
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
ms.openlocfilehash: 9dac9bc70cd070eb3e94969ce47ce24325a6f89d
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904243"
---
# <a name="interop-etw-events"></a><span data-ttu-id="a6c77-103">Interop ETW 事件</span><span class="sxs-lookup"><span data-stu-id="a6c77-103">Interop ETW Events</span></span>
<span data-ttu-id="a6c77-104">Interop 事件會擷取 Microsoft 中繼語言 (MSIL) Stub 之產生和快取的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="a6c77-104">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  

## <a name="ilstubgenerated-event"></a><span data-ttu-id="a6c77-105">ILStubGenerated 事件</span><span class="sxs-lookup"><span data-stu-id="a6c77-105">ILStubGenerated Event</span></span>

<span data-ttu-id="a6c77-106">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="a6c77-106">The following table shows the keyword and level.</span></span> <span data-ttu-id="a6c77-107">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="a6c77-107">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="a6c77-108">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a6c77-108">Keyword for raising the event</span></span>|<span data-ttu-id="a6c77-109">層級</span><span class="sxs-lookup"><span data-stu-id="a6c77-109">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="a6c77-110">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="a6c77-110">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="a6c77-111">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a6c77-111">Informational(4)</span></span>|  
  
 <span data-ttu-id="a6c77-112">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="a6c77-112">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a6c77-113">事件</span><span class="sxs-lookup"><span data-stu-id="a6c77-113">Event</span></span>|<span data-ttu-id="a6c77-114">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a6c77-114">Event ID</span></span>|<span data-ttu-id="a6c77-115">引發的時機</span><span class="sxs-lookup"><span data-stu-id="a6c77-115">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="a6c77-116">88</span><span class="sxs-lookup"><span data-stu-id="a6c77-116">88</span></span>|<span data-ttu-id="a6c77-117">已產生 MSIL 虛設常式。</span><span class="sxs-lookup"><span data-stu-id="a6c77-117">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="a6c77-118">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="a6c77-118">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="a6c77-119">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="a6c77-119">Field name</span></span>|<span data-ttu-id="a6c77-120">資料類型</span><span class="sxs-lookup"><span data-stu-id="a6c77-120">Data type</span></span>|<span data-ttu-id="a6c77-121">描述</span><span class="sxs-lookup"><span data-stu-id="a6c77-121">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a6c77-122">ModuleID</span><span class="sxs-lookup"><span data-stu-id="a6c77-122">ModuleID</span></span>|<span data-ttu-id="a6c77-123">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a6c77-123">win:UInt16</span></span>|<span data-ttu-id="a6c77-124">模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="a6c77-124">The module identifier.</span></span>|  
|<span data-ttu-id="a6c77-125">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="a6c77-125">StubMethodID</span></span>|<span data-ttu-id="a6c77-126">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a6c77-126">win:UInt64</span></span>|<span data-ttu-id="a6c77-127">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="a6c77-127">The stub method identifier.</span></span>|  
|<span data-ttu-id="a6c77-128">StubFlags</span><span class="sxs-lookup"><span data-stu-id="a6c77-128">StubFlags</span></span>|<span data-ttu-id="a6c77-129">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a6c77-129">win:UInt64</span></span>|<span data-ttu-id="a6c77-130">虛設常式的旗標：</span><span class="sxs-lookup"><span data-stu-id="a6c77-130">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="a6c77-131">0x1 - 反向 interop。</span><span class="sxs-lookup"><span data-stu-id="a6c77-131">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="a6c77-132">0x2 - COM interop。</span><span class="sxs-lookup"><span data-stu-id="a6c77-132">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="a6c77-133">0x4 - NGen.exe 所產生的虛設常式。</span><span class="sxs-lookup"><span data-stu-id="a6c77-133">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="a6c77-134">0x8 - 委派。</span><span class="sxs-lookup"><span data-stu-id="a6c77-134">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="a6c77-135">0x10-變數引數。</span><span class="sxs-lookup"><span data-stu-id="a6c77-135">0x10 - Variable argument.</span></span><br /><br /> <span data-ttu-id="a6c77-136">0x20 - Unmanaged 被呼叫者。</span><span class="sxs-lookup"><span data-stu-id="a6c77-136">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="a6c77-137">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="a6c77-137">ManagedInteropMethodToken</span></span>|<span data-ttu-id="a6c77-138">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a6c77-138">win:UInt32</span></span>|<span data-ttu-id="a6c77-139">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a6c77-139">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="a6c77-140">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="a6c77-140">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="a6c77-141">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a6c77-141">win:UnicodeString</span></span>|<span data-ttu-id="a6c77-142">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a6c77-142">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="a6c77-143">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="a6c77-143">ManagedInteropMethodName</span></span>|<span data-ttu-id="a6c77-144">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a6c77-144">win:UnicodeString</span></span>|<span data-ttu-id="a6c77-145">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="a6c77-145">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="a6c77-146">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="a6c77-146">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="a6c77-147">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a6c77-147">win:UnicodeString</span></span>|<span data-ttu-id="a6c77-148">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="a6c77-148">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="a6c77-149">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="a6c77-149">NativeMethodSignature</span></span>|<span data-ttu-id="a6c77-150">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a6c77-150">win:UnicodeString</span></span>|<span data-ttu-id="a6c77-151">原生方法簽章。</span><span class="sxs-lookup"><span data-stu-id="a6c77-151">The native method signature.</span></span>|  
|<span data-ttu-id="a6c77-152">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="a6c77-152">StubMethodSignature</span></span>|<span data-ttu-id="a6c77-153">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a6c77-153">win:UnicodeString</span></span>|<span data-ttu-id="a6c77-154">虛設常式方法簽章。</span><span class="sxs-lookup"><span data-stu-id="a6c77-154">The stub method signature.</span></span>|  
|<span data-ttu-id="a6c77-155">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="a6c77-155">StubMethodILCode</span></span>|<span data-ttu-id="a6c77-156">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a6c77-156">win:UnicodeString</span></span>|<span data-ttu-id="a6c77-157">虛設常式方法的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="a6c77-157">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="a6c77-158">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a6c77-158">ClrInstanceID</span></span>|<span data-ttu-id="a6c77-159">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a6c77-159">win:UInt16</span></span>|<span data-ttu-id="a6c77-160">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="a6c77-160">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="ilstubcachehit-event"></a><span data-ttu-id="a6c77-161">ILStubCacheHit 事件</span><span class="sxs-lookup"><span data-stu-id="a6c77-161">ILStubCacheHit Event</span></span>  

<span data-ttu-id="a6c77-162">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="a6c77-162">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="a6c77-163">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="a6c77-163">Keyword for raising the event</span></span>|<span data-ttu-id="a6c77-164">層級</span><span class="sxs-lookup"><span data-stu-id="a6c77-164">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="a6c77-165">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="a6c77-165">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="a6c77-166">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="a6c77-166">Informational(4)</span></span>|  
  
 <span data-ttu-id="a6c77-167">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="a6c77-167">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="a6c77-168">事件</span><span class="sxs-lookup"><span data-stu-id="a6c77-168">Event</span></span>|<span data-ttu-id="a6c77-169">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a6c77-169">Event ID</span></span>|<span data-ttu-id="a6c77-170">引發的時機</span><span class="sxs-lookup"><span data-stu-id="a6c77-170">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="a6c77-171">89</span><span class="sxs-lookup"><span data-stu-id="a6c77-171">89</span></span>|<span data-ttu-id="a6c77-172">已存取 MSIL 快取。</span><span class="sxs-lookup"><span data-stu-id="a6c77-172">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="a6c77-173">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="a6c77-173">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="a6c77-174">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="a6c77-174">Field name</span></span>|<span data-ttu-id="a6c77-175">資料類型</span><span class="sxs-lookup"><span data-stu-id="a6c77-175">Data type</span></span>|<span data-ttu-id="a6c77-176">描述</span><span class="sxs-lookup"><span data-stu-id="a6c77-176">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="a6c77-177">ModuleID</span><span class="sxs-lookup"><span data-stu-id="a6c77-177">ModuleID</span></span>|<span data-ttu-id="a6c77-178">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a6c77-178">win:UInt16</span></span>|<span data-ttu-id="a6c77-179">模組識別碼。</span><span class="sxs-lookup"><span data-stu-id="a6c77-179">The module identifier.</span></span>|  
|<span data-ttu-id="a6c77-180">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="a6c77-180">StubMethodID</span></span>|<span data-ttu-id="a6c77-181">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="a6c77-181">win:UInt64</span></span>|<span data-ttu-id="a6c77-182">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="a6c77-182">The stub method identifier.</span></span>|  
|<span data-ttu-id="a6c77-183">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="a6c77-183">ManagedInteropMethodToken</span></span>|<span data-ttu-id="a6c77-184">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="a6c77-184">win:UInt32</span></span>|<span data-ttu-id="a6c77-185">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="a6c77-185">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="a6c77-186">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="a6c77-186">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="a6c77-187">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a6c77-187">win:UnicodeString</span></span>|<span data-ttu-id="a6c77-188">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="a6c77-188">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="a6c77-189">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="a6c77-189">ManagedInteropMethodName</span></span>|<span data-ttu-id="a6c77-190">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a6c77-190">win:UnicodeString</span></span>|<span data-ttu-id="a6c77-191">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="a6c77-191">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="a6c77-192">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="a6c77-192">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="a6c77-193">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="a6c77-193">win:UnicodeString</span></span>|<span data-ttu-id="a6c77-194">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="a6c77-194">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="a6c77-195">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="a6c77-195">ClrInstanceID</span></span>|<span data-ttu-id="a6c77-196">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="a6c77-196">win:UInt16</span></span>|<span data-ttu-id="a6c77-197">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="a6c77-197">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6c77-198">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6c77-198">See also</span></span>

- [<span data-ttu-id="a6c77-199">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="a6c77-199">CLR ETW Events</span></span>](clr-etw-events.md)
