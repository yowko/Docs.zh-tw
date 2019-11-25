---
title: Interop ETW 事件
ms.date: 03/30/2017
helpviewer_keywords:
- interop events [.NET Framework]
- ETW, interop events (CLR)
ms.assetid: eb6eac2e-45f4-4923-a32c-38f203da66df
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5db68cdce0db4f8f4d85e9d1dd03720bf235d865
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974924"
---
# <a name="interop-etw-events"></a><span data-ttu-id="21653-102">Interop ETW 事件</span><span class="sxs-lookup"><span data-stu-id="21653-102">Interop ETW Events</span></span>
<span data-ttu-id="21653-103">Interop 事件會擷取 Microsoft 中繼語言 (MSIL) Stub 之產生和快取的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="21653-103">Interop events capture information about Microsoft intermediate language (MSIL) stub generation and caching.</span></span>  

## <a name="ilstubgenerated-event"></a><span data-ttu-id="21653-104">ILStubGenerated 事件</span><span class="sxs-lookup"><span data-stu-id="21653-104">ILStubGenerated Event</span></span>

<span data-ttu-id="21653-105">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="21653-105">The following table shows the keyword and level.</span></span> <span data-ttu-id="21653-106">(如需詳細資訊，請參閱 [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md))。</span><span class="sxs-lookup"><span data-stu-id="21653-106">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="21653-107">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="21653-107">Keyword for raising the event</span></span>|<span data-ttu-id="21653-108">層級</span><span class="sxs-lookup"><span data-stu-id="21653-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="21653-109">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="21653-109">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="21653-110">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="21653-110">Informational(4)</span></span>|  
  
 <span data-ttu-id="21653-111">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="21653-111">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="21653-112">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="21653-112">Event</span></span>|<span data-ttu-id="21653-113">事件 ID</span><span class="sxs-lookup"><span data-stu-id="21653-113">Event ID</span></span>|<span data-ttu-id="21653-114">引發的時機</span><span class="sxs-lookup"><span data-stu-id="21653-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubGenerated`|<span data-ttu-id="21653-115">88</span><span class="sxs-lookup"><span data-stu-id="21653-115">88</span></span>|<span data-ttu-id="21653-116">已產生 MSIL 虛設常式。</span><span class="sxs-lookup"><span data-stu-id="21653-116">The MSIL stub has been generated.</span></span>|  
  
 <span data-ttu-id="21653-117">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="21653-117">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="21653-118">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="21653-118">Field name</span></span>|<span data-ttu-id="21653-119">資料類型</span><span class="sxs-lookup"><span data-stu-id="21653-119">Data type</span></span>|<span data-ttu-id="21653-120">描述</span><span class="sxs-lookup"><span data-stu-id="21653-120">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="21653-121">ModuleID</span><span class="sxs-lookup"><span data-stu-id="21653-121">ModuleID</span></span>|<span data-ttu-id="21653-122">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="21653-122">win:UInt16</span></span>|<span data-ttu-id="21653-123">模組識別項。</span><span class="sxs-lookup"><span data-stu-id="21653-123">The module identifier.</span></span>|  
|<span data-ttu-id="21653-124">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="21653-124">StubMethodID</span></span>|<span data-ttu-id="21653-125">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="21653-125">win:UInt64</span></span>|<span data-ttu-id="21653-126">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="21653-126">The stub method identifier.</span></span>|  
|<span data-ttu-id="21653-127">StubFlags</span><span class="sxs-lookup"><span data-stu-id="21653-127">StubFlags</span></span>|<span data-ttu-id="21653-128">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="21653-128">win:UInt64</span></span>|<span data-ttu-id="21653-129">虛設常式的旗標：</span><span class="sxs-lookup"><span data-stu-id="21653-129">The flags for the stub:</span></span><br /><br /> <span data-ttu-id="21653-130">0x1 - 反向 interop。</span><span class="sxs-lookup"><span data-stu-id="21653-130">0x1 - Reverse interop.</span></span><br /><br /> <span data-ttu-id="21653-131">0x2 - COM interop。</span><span class="sxs-lookup"><span data-stu-id="21653-131">0x2 - COM interop.</span></span><br /><br /> <span data-ttu-id="21653-132">0x4 - NGen.exe 所產生的虛設常式。</span><span class="sxs-lookup"><span data-stu-id="21653-132">0x4 - Stub generated by NGen.exe.</span></span><br /><br /> <span data-ttu-id="21653-133">0x8 - 委派。</span><span class="sxs-lookup"><span data-stu-id="21653-133">0x8 - Delegate.</span></span><br /><br /> <span data-ttu-id="21653-134">0x10-變數引數。</span><span class="sxs-lookup"><span data-stu-id="21653-134">0x10 - Variable argument.</span></span><br /><br /> <span data-ttu-id="21653-135">0x20 - Unmanaged 被呼叫者。</span><span class="sxs-lookup"><span data-stu-id="21653-135">0x20 - Unmanaged callee.</span></span>|  
|<span data-ttu-id="21653-136">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="21653-136">ManagedInteropMethodToken</span></span>|<span data-ttu-id="21653-137">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="21653-137">win:UInt32</span></span>|<span data-ttu-id="21653-138">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="21653-138">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="21653-139">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="21653-139">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="21653-140">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="21653-140">win:UnicodeString</span></span>|<span data-ttu-id="21653-141">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="21653-141">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="21653-142">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="21653-142">ManagedInteropMethodName</span></span>|<span data-ttu-id="21653-143">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="21653-143">win:UnicodeString</span></span>|<span data-ttu-id="21653-144">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="21653-144">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="21653-145">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="21653-145">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="21653-146">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="21653-146">win:UnicodeString</span></span>|<span data-ttu-id="21653-147">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="21653-147">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="21653-148">NativeMethodSignature</span><span class="sxs-lookup"><span data-stu-id="21653-148">NativeMethodSignature</span></span>|<span data-ttu-id="21653-149">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="21653-149">win:UnicodeString</span></span>|<span data-ttu-id="21653-150">原生方法簽章。</span><span class="sxs-lookup"><span data-stu-id="21653-150">The native method signature.</span></span>|  
|<span data-ttu-id="21653-151">StubMethodSignature</span><span class="sxs-lookup"><span data-stu-id="21653-151">StubMethodSignature</span></span>|<span data-ttu-id="21653-152">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="21653-152">win:UnicodeString</span></span>|<span data-ttu-id="21653-153">虛設常式方法簽章。</span><span class="sxs-lookup"><span data-stu-id="21653-153">The stub method signature.</span></span>|  
|<span data-ttu-id="21653-154">StubMethodILCode</span><span class="sxs-lookup"><span data-stu-id="21653-154">StubMethodILCode</span></span>|<span data-ttu-id="21653-155">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="21653-155">win:UnicodeString</span></span>|<span data-ttu-id="21653-156">虛設常式方法的 MSIL 程式碼。</span><span class="sxs-lookup"><span data-stu-id="21653-156">The MSIL code for the stub method.</span></span>|  
|<span data-ttu-id="21653-157">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="21653-157">ClrInstanceID</span></span>|<span data-ttu-id="21653-158">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="21653-158">win:UInt16</span></span>|<span data-ttu-id="21653-159">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="21653-159">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="ilstubcachehit-event"></a><span data-ttu-id="21653-160">ILStubCacheHit 事件</span><span class="sxs-lookup"><span data-stu-id="21653-160">ILStubCacheHit Event</span></span>  

<span data-ttu-id="21653-161">下表說明關鍵字和層級。</span><span class="sxs-lookup"><span data-stu-id="21653-161">The following table shows the keyword and level.</span></span>  
  
|<span data-ttu-id="21653-162">引發事件的關鍵字</span><span class="sxs-lookup"><span data-stu-id="21653-162">Keyword for raising the event</span></span>|<span data-ttu-id="21653-163">層級</span><span class="sxs-lookup"><span data-stu-id="21653-163">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="21653-164">`InteropKeyword` (0x2000)</span><span class="sxs-lookup"><span data-stu-id="21653-164">`InteropKeyword` (0x2000)</span></span>|<span data-ttu-id="21653-165">Informational(4)</span><span class="sxs-lookup"><span data-stu-id="21653-165">Informational(4)</span></span>|  
  
 <span data-ttu-id="21653-166">下表說明事件資訊。</span><span class="sxs-lookup"><span data-stu-id="21653-166">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="21653-167">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="21653-167">Event</span></span>|<span data-ttu-id="21653-168">事件 ID</span><span class="sxs-lookup"><span data-stu-id="21653-168">Event ID</span></span>|<span data-ttu-id="21653-169">引發的時機</span><span class="sxs-lookup"><span data-stu-id="21653-169">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ILStubCacheHit`|<span data-ttu-id="21653-170">89</span><span class="sxs-lookup"><span data-stu-id="21653-170">89</span></span>|<span data-ttu-id="21653-171">已存取 MSIL 快取。</span><span class="sxs-lookup"><span data-stu-id="21653-171">The MSIL cache has been accessed.</span></span>|  
  
 <span data-ttu-id="21653-172">下表說明事件資料。</span><span class="sxs-lookup"><span data-stu-id="21653-172">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="21653-173">欄位名稱</span><span class="sxs-lookup"><span data-stu-id="21653-173">Field name</span></span>|<span data-ttu-id="21653-174">資料類型</span><span class="sxs-lookup"><span data-stu-id="21653-174">Data type</span></span>|<span data-ttu-id="21653-175">描述</span><span class="sxs-lookup"><span data-stu-id="21653-175">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="21653-176">ModuleID</span><span class="sxs-lookup"><span data-stu-id="21653-176">ModuleID</span></span>|<span data-ttu-id="21653-177">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="21653-177">win:UInt16</span></span>|<span data-ttu-id="21653-178">模組識別項。</span><span class="sxs-lookup"><span data-stu-id="21653-178">The module identifier.</span></span>|  
|<span data-ttu-id="21653-179">StubMethodID</span><span class="sxs-lookup"><span data-stu-id="21653-179">StubMethodID</span></span>|<span data-ttu-id="21653-180">win:UInt64</span><span class="sxs-lookup"><span data-stu-id="21653-180">win:UInt64</span></span>|<span data-ttu-id="21653-181">虛設常式方法識別項。</span><span class="sxs-lookup"><span data-stu-id="21653-181">The stub method identifier.</span></span>|  
|<span data-ttu-id="21653-182">ManagedInteropMethodToken</span><span class="sxs-lookup"><span data-stu-id="21653-182">ManagedInteropMethodToken</span></span>|<span data-ttu-id="21653-183">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="21653-183">win:UInt32</span></span>|<span data-ttu-id="21653-184">Managed interop 方法的語彙基元。</span><span class="sxs-lookup"><span data-stu-id="21653-184">The token for the managed interop method.</span></span>|  
|<span data-ttu-id="21653-185">ManagedInteropMethodNameSpace</span><span class="sxs-lookup"><span data-stu-id="21653-185">ManagedInteropMethodNameSpace</span></span>|<span data-ttu-id="21653-186">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="21653-186">win:UnicodeString</span></span>|<span data-ttu-id="21653-187">Managed interop 方法的命名空間。</span><span class="sxs-lookup"><span data-stu-id="21653-187">The namespace of the managed interop method.</span></span>|  
|<span data-ttu-id="21653-188">ManagedInteropMethodName</span><span class="sxs-lookup"><span data-stu-id="21653-188">ManagedInteropMethodName</span></span>|<span data-ttu-id="21653-189">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="21653-189">win:UnicodeString</span></span>|<span data-ttu-id="21653-190">Managed interop 方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="21653-190">The name of the managed interop method.</span></span>|  
|<span data-ttu-id="21653-191">ManagedInteropMethodSignature</span><span class="sxs-lookup"><span data-stu-id="21653-191">ManagedInteropMethodSignature</span></span>|<span data-ttu-id="21653-192">win:UnicodeString</span><span class="sxs-lookup"><span data-stu-id="21653-192">win:UnicodeString</span></span>|<span data-ttu-id="21653-193">Managed interop 方法的簽章。</span><span class="sxs-lookup"><span data-stu-id="21653-193">The signature of the managed interop method.</span></span>|  
|<span data-ttu-id="21653-194">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="21653-194">ClrInstanceID</span></span>|<span data-ttu-id="21653-195">win:UInt16</span><span class="sxs-lookup"><span data-stu-id="21653-195">win:UInt16</span></span>|<span data-ttu-id="21653-196">CLR 或 CoreCLR 執行個體的唯一 ID。</span><span class="sxs-lookup"><span data-stu-id="21653-196">Unique ID for the instance of CLR or CoreCLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21653-197">請參閱</span><span class="sxs-lookup"><span data-stu-id="21653-197">See also</span></span>

- [<span data-ttu-id="21653-198">CLR ETW 事件</span><span class="sxs-lookup"><span data-stu-id="21653-198">CLR ETW Events</span></span>](clr-etw-events.md)
