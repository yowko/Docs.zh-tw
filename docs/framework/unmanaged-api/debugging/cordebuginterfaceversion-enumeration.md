---
title: CorDebugInterfaceVersion 列舉
ms.date: 03/30/2017
api_name:
- CorDebugInterfaceVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInterfaceVersion
helpviewer_keywords:
- CorDebugInterfaceVersion enumeration [.NET Framework debugging]
ms.assetid: 7d1e6cd9-2a15-41c6-9b68-008705a4ed90
topic_type:
- apiref
ms.openlocfilehash: 70d9ee06d64cc80306a1988aa6e28859cadb9ecf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778409"
---
# <a name="cordebuginterfaceversion-enumeration"></a><span data-ttu-id="2bf1d-102">CorDebugInterfaceVersion 列舉</span><span class="sxs-lookup"><span data-stu-id="2bf1d-102">CorDebugInterfaceVersion Enumeration</span></span>
<span data-ttu-id="2bf1d-103">指定介面、.NET Framework 版本，或是已引進介面的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-103">Specifies an interface, a version of the .NET Framework, or a version of the .NET Framework in which an interface was introduced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bf1d-104">語法</span><span class="sxs-lookup"><span data-stu-id="2bf1d-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugInterfaceVersion {  
  
    CorDebugInvalidVersion            = 0,  
    CorDebugVersion_1_0               = CorDebugInvalidVersion + 1,  
  
    ver_ICorDebugManagedCallback      = CorDebugVersion_1_0,  
    ver_ICorDebugUnmanagedCallback    = CorDebugVersion_1_0,  
    ver_ICorDebug                     = CorDebugVersion_1_0,  
    ver_ICorDebugController           = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomain            = CorDebugVersion_1_0,  
    ver_ICorDebugAssembly             = CorDebugVersion_1_0,  
    ver_ICorDebugProcess              = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpoint           = CorDebugVersion_1_0,  
    ver_ICorDebugFunctionBreakpoint   = CorDebugVersion_1_0,  
    ver_ICorDebugModuleBreakpoint     = CorDebugVersion_1_0,  
    ver_ICorDebugValueBreakpoint      = CorDebugVersion_1_0,  
    ver_ICorDebugStepper              = CorDebugVersion_1_0,  
    ver_ICorDebugRegisterSet          = CorDebugVersion_1_0,  
    ver_ICorDebugThread               = CorDebugVersion_1_0,  
    ver_ICorDebugChain                = CorDebugVersion_1_0,  
    ver_ICorDebugFrame                = CorDebugVersion_1_0,  
    ver_ICorDebugILFrame              = CorDebugVersion_1_0,  
    ver_ICorDebugNativeFrame          = CorDebugVersion_1_0,  
    ver_ICorDebugModule               = CorDebugVersion_1_0,  
    ver_ICorDebugFunction             = CorDebugVersion_1_0,  
    ver_ICorDebugCode                 = CorDebugVersion_1_0,  
    ver_ICorDebugClass                = CorDebugVersion_1_0,  
    ver_ICorDebugEval                 = CorDebugVersion_1_0,  
    ver_ICorDebugValue                = CorDebugVersion_1_0,  
    ver_ICorDebugGenericValue         = CorDebugVersion_1_0,  
    ver_ICorDebugReferenceValue       = CorDebugVersion_1_0,  
    ver_ICorDebugHeapValue            = CorDebugVersion_1_0,  
    ver_ICorDebugObjectValue          = CorDebugVersion_1_0,  
    ver_ICorDebugBoxValue             = CorDebugVersion_1_0,  
    ver_ICorDebugStringValue          = CorDebugVersion_1_0,  
    ver_ICorDebugArrayValue           = CorDebugVersion_1_0,  
    ver_ICorDebugContext              = CorDebugVersion_1_0,  
    ver_ICorDebugEnum                 = CorDebugVersion_1_0,  
    ver_ICorDebugObjectEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugBreakpointEnum       = CorDebugVersion_1_0,  
    ver_ICorDebugStepperEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugProcessEnum          = CorDebugVersion_1_0,  
    ver_ICorDebugThreadEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugFrameEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugChainEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugModuleEnum           = CorDebugVersion_1_0,  
    ver_ICorDebugValueEnum            = CorDebugVersion_1_0,  
    ver_ICorDebugCodeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugTypeEnum             = CorDebugVersion_1_0,  
    ver_ICorDebugErrorInfoEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAppDomainEnum        = CorDebugVersion_1_0,  
    ver_ICorDebugAssemblyEnum         = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueErrorInfo   
                                      = CorDebugVersion_1_0,  
    ver_ICorDebugEditAndContinueSnapshot   
                                      = CorDebugVersion_1_0,  
  
    CorDebugVersion_1_1               = CorDebugVersion_1_0 + 1,  
    // No interface definitions in version 1.1.  
  
    CorDebugVersion_2_0 = CorDebugVersion_1_1 + 1,  
  
    ver_ICorDebugManagedCallback2    = CorDebugVersion_2_0,  
    ver_ICorDebugAppDomain2          = CorDebugVersion_2_0,  
    ver_ICorDebugProcess2            = CorDebugVersion_2_0,  
    ver_ICorDebugStepper2            = CorDebugVersion_2_0,  
    ver_ICorDebugRegisterSet2        = CorDebugVersion_2_0,  
    ver_ICorDebugThread2             = CorDebugVersion_2_0,  
    ver_ICorDebugILFrame2            = CorDebugVersion_2_0,  
    ver_ICorDebugModule2             = CorDebugVersion_2_0,  
    ver_ICorDebugFunction2           = CorDebugVersion_2_0,  
    ver_ICorDebugCode2               = CorDebugVersion_2_0,  
    ver_ICorDebugClass2              = CorDebugVersion_2_0,  
    ver_ICorDebugValue2              = CorDebugVersion_2_0,  
    ver_ICorDebugEval2               = CorDebugVersion_2_0,  
    ver_ICorDebugObjectValue2        = CorDebugVersion_2_0,  
  
    // CLR v4 - next major CLR version after CLR v2  
    // Includes Silverlight 4  
    CorDebugVersion_4_0 = CorDebugVersion_2_0 + 1,  
  
    ver_ICorDebugThread3             = CorDebugVersion_4_0,  
    ver_ICorDebugThread4             = CorDebugVersion_4_0,  
    ver_ICorDebugStackWalk           = CorDebugVersion_4_0,  
    ver_ICorDebugNativeFrame2        = CorDebugVersion_4_0,  
    ver_ICorDebugInternalFrame2      = CorDebugVersion_4_0,  
    ver_ICorDebugRuntimeUnwindableFrame = CorDebugVersion_4_0,  
    ver_ICorDebugHeapValue3          = CorDebugVersion_4_0,  
    ver_ICorDebugBlockingObjectEnum  = CorDebugVersion_4_0,  
    ver_ICorDebugValue3 = CorDebugVersion_4_0,  
  
    CorDebugVersion_4_5 = CorDebugVersion_4_0 + 1,  
  
    ver_ICorDebugComObjectValue = CorDebugVersion_4_5,  
    ver_ICorDebugAppDomain3 = CorDebugVersion_4_5,  
    ver_ICorDebugCode3 = CorDebugVersion_4_5,  
    ver_ICorDebugILFrame3 = CorDebugVersion_4_5,  
  
    CorDebugLatestVersion = CorDebugVersion_4_5  
  
} CorDebugInterfaceVersion;  
```  
  
## <a name="members"></a><span data-ttu-id="2bf1d-105">Members</span><span class="sxs-lookup"><span data-stu-id="2bf1d-105">Members</span></span>  
 <span data-ttu-id="2bf1d-106">下表提供從每個列舉值到對應介面的連結。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-106">The following table provides links from each enumeration value to the corresponding interface.</span></span> <span data-ttu-id="2bf1d-107">此外，該資料表也會指出支援介面的第一個 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-107">In addition, the table indicates the first version of the .NET Framework that the interface was supported in.</span></span>  
  
|<span data-ttu-id="2bf1d-108">成員</span><span class="sxs-lookup"><span data-stu-id="2bf1d-108">Member</span></span>|<span data-ttu-id="2bf1d-109">指定</span><span class="sxs-lookup"><span data-stu-id="2bf1d-109">Specifies</span></span>|<span data-ttu-id="2bf1d-110">.NET Framework 版本</span><span class="sxs-lookup"><span data-stu-id="2bf1d-110">.NET Framework version</span></span>|  
|------------|---------------|----------------------------|  
|`CorDebugInvalidVersion`|<span data-ttu-id="2bf1d-111">.NET Framework 版本無效。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-111">The version of the .NET Framework is invalid.</span></span>|-|  
|`CorDebugVersion_1_0`|<span data-ttu-id="2bf1d-112">.NET Framework 的版本 (包括其所有 Service Pack) 為 1.0。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-112">The version of the .NET Framework, including all its service packs, is 1.0.</span></span>|<span data-ttu-id="2bf1d-113">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-113">1.0</span></span>|  
|`CorDebugVersion_1_1`|<span data-ttu-id="2bf1d-114">.NET Framework 的版本 (包括所有 Service Pack) 為 1.1。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-114">The version of the .NET Framework, including all service packs, is 1.1.</span></span>|<span data-ttu-id="2bf1d-115">1.1</span><span class="sxs-lookup"><span data-stu-id="2bf1d-115">1.1</span></span>|  
|`CorDebugVersion_2_0`|<span data-ttu-id="2bf1d-116">.NET Framework 的版本 (包括所有 Service Pack) 為 2.0。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-116">The version of the .NET Framework, including all service packs, is 2.0.</span></span>|<span data-ttu-id="2bf1d-117">2.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-117">2.0</span></span>|  
|`CorDebugVersion_4_0`|<span data-ttu-id="2bf1d-118">.NET Framework 的版本 (包括所有 Service Pack) 為 4。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-118">The version of the .NET Framework, including all service packs, is 4.</span></span>|<span data-ttu-id="2bf1d-119">4</span><span class="sxs-lookup"><span data-stu-id="2bf1d-119">4</span></span>|  
|`CorDebugVersion_4_5`|<span data-ttu-id="2bf1d-120">.NET Framework 的版本 (包括所有 Service Pack) 為 4.5。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-120">The version of the .NET Framework, including all service packs, is 4.5.</span></span>|<span data-ttu-id="2bf1d-121">4.5</span><span class="sxs-lookup"><span data-stu-id="2bf1d-121">4.5</span></span>|  
|`ver_ICorDebugManagedCallback`|[<span data-ttu-id="2bf1d-122">ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="2bf1d-122">ICorDebugManagedCallback</span></span>](icordebugmanagedcallback-interface.md)|<span data-ttu-id="2bf1d-123">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-123">1.0</span></span>|  
|`ver_ICorDebugUnmanagedCallback`|[<span data-ttu-id="2bf1d-124">ICorDebugUnmanagedCallback</span><span class="sxs-lookup"><span data-stu-id="2bf1d-124">ICorDebugUnmanagedCallback</span></span>](icordebugunmanagedcallback-interface.md)|<span data-ttu-id="2bf1d-125">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-125">1.0</span></span>|  
|`ver_ICorDebug`|[<span data-ttu-id="2bf1d-126">ICorDebug</span><span class="sxs-lookup"><span data-stu-id="2bf1d-126">ICorDebug</span></span>](icordebug-interface.md)|<span data-ttu-id="2bf1d-127">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-127">1.0</span></span>|  
|`ver_ICorDebugController`|[<span data-ttu-id="2bf1d-128">ICorDebugController</span><span class="sxs-lookup"><span data-stu-id="2bf1d-128">ICorDebugController</span></span>](icordebugcontroller-interface.md)|<span data-ttu-id="2bf1d-129">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-129">1.0</span></span>|  
|`ver_ICorDebugAppDomain`|[<span data-ttu-id="2bf1d-130">ICorDebugAppDomain</span><span class="sxs-lookup"><span data-stu-id="2bf1d-130">ICorDebugAppDomain</span></span>](icordebugappdomain-interface.md)|<span data-ttu-id="2bf1d-131">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-131">1.0</span></span>|  
|`ver_ICorDebugAssembly`|[<span data-ttu-id="2bf1d-132">ICorDebugAssembly</span><span class="sxs-lookup"><span data-stu-id="2bf1d-132">ICorDebugAssembly</span></span>](icordebugassembly-interface.md)|<span data-ttu-id="2bf1d-133">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-133">1.0</span></span>|  
|`ver_ICorDebugProcess`|[<span data-ttu-id="2bf1d-134">ICorDebugProcess</span><span class="sxs-lookup"><span data-stu-id="2bf1d-134">ICorDebugProcess</span></span>](icordebugprocess-interface.md)|<span data-ttu-id="2bf1d-135">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-135">1.0</span></span>|  
|`ver_ICorDebugBreakpoint`|[<span data-ttu-id="2bf1d-136">ICorDebugBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2bf1d-136">ICorDebugBreakpoint</span></span>](icordebugbreakpoint-interface.md)|<span data-ttu-id="2bf1d-137">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-137">1.0</span></span>|  
|`ver_ICorDebugFunctionBreakpoint`|[<span data-ttu-id="2bf1d-138">ICorDebugFunctionBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2bf1d-138">ICorDebugFunctionBreakpoint</span></span>](icordebugfunctionbreakpoint-interface.md)|<span data-ttu-id="2bf1d-139">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-139">1.0</span></span>|  
|`ver_ICorDebugModuleBreakpoint`|[<span data-ttu-id="2bf1d-140">ICorDebugModuleBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2bf1d-140">ICorDebugModuleBreakpoint</span></span>](icordebugmodulebreakpoint-interface.md)|<span data-ttu-id="2bf1d-141">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-141">1.0</span></span>|  
|`ver_ICorDebugValueBreakpoint`|[<span data-ttu-id="2bf1d-142">ICorDebugValueBreakpoint</span><span class="sxs-lookup"><span data-stu-id="2bf1d-142">ICorDebugValueBreakpoint</span></span>](icordebugvaluebreakpoint-interface.md)|<span data-ttu-id="2bf1d-143">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-143">1.0</span></span>|  
|`ver_ICorDebugStepper`|[<span data-ttu-id="2bf1d-144">ICorDebugStepper</span><span class="sxs-lookup"><span data-stu-id="2bf1d-144">ICorDebugStepper</span></span>](icordebugstepper-interface.md)|<span data-ttu-id="2bf1d-145">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-145">1.0</span></span>|  
|`ver_ICorDebugRegisterSet`|[<span data-ttu-id="2bf1d-146">ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="2bf1d-146">ICorDebugRegisterSet</span></span>](icordebugregisterset-interface.md)|<span data-ttu-id="2bf1d-147">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-147">1.0</span></span>|  
|`ver_ICorDebugThread`|[<span data-ttu-id="2bf1d-148">ICorDebugThread</span><span class="sxs-lookup"><span data-stu-id="2bf1d-148">ICorDebugThread</span></span>](icordebugthread-interface.md)|<span data-ttu-id="2bf1d-149">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-149">1.0</span></span>|  
|`ver_ICorDebugChain`|[<span data-ttu-id="2bf1d-150">ICorDebugChain</span><span class="sxs-lookup"><span data-stu-id="2bf1d-150">ICorDebugChain</span></span>](icordebugchain-interface.md)|<span data-ttu-id="2bf1d-151">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-151">1.0</span></span>|  
|`ver_ICorDebugFrame`|[<span data-ttu-id="2bf1d-152">ICorDebugFrame</span><span class="sxs-lookup"><span data-stu-id="2bf1d-152">ICorDebugFrame</span></span>](icordebugframe-interface.md)|<span data-ttu-id="2bf1d-153">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-153">1.0</span></span>|  
|`ver_ICorDebugILFrame`|[<span data-ttu-id="2bf1d-154">ICorDebugILFrame</span><span class="sxs-lookup"><span data-stu-id="2bf1d-154">ICorDebugILFrame</span></span>](icordebugilframe-interface.md)|<span data-ttu-id="2bf1d-155">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-155">1.0</span></span>|  
|`ver_ICorDebugNativeFrame`|[<span data-ttu-id="2bf1d-156">ICorDebugNativeFrame</span><span class="sxs-lookup"><span data-stu-id="2bf1d-156">ICorDebugNativeFrame</span></span>](icordebugnativeframe-interface.md)|<span data-ttu-id="2bf1d-157">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-157">1.0</span></span>|  
|`ver_ICorDebugModule`|[<span data-ttu-id="2bf1d-158">ICorDebugModule</span><span class="sxs-lookup"><span data-stu-id="2bf1d-158">ICorDebugModule</span></span>](icordebugmodule-interface.md)|<span data-ttu-id="2bf1d-159">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-159">1.0</span></span>|  
|`ver_ICorDebugFunction`|[<span data-ttu-id="2bf1d-160">ICorDebugFunction</span><span class="sxs-lookup"><span data-stu-id="2bf1d-160">ICorDebugFunction</span></span>](icordebugfunction-interface1.md)|<span data-ttu-id="2bf1d-161">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-161">1.0</span></span>|  
|`ver_ICorDebugCode`|[<span data-ttu-id="2bf1d-162">ICorDebugCode</span><span class="sxs-lookup"><span data-stu-id="2bf1d-162">ICorDebugCode</span></span>](icordebugcode-interface1.md)|<span data-ttu-id="2bf1d-163">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-163">1.0</span></span>|  
|`ver_ICorDebugClass`|[<span data-ttu-id="2bf1d-164">ICorDebugClass</span><span class="sxs-lookup"><span data-stu-id="2bf1d-164">ICorDebugClass</span></span>](icordebugclass-interface.md)|<span data-ttu-id="2bf1d-165">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-165">1.0</span></span>|  
|`ver_ICorDebugEval`|[<span data-ttu-id="2bf1d-166">ICorDebugEval</span><span class="sxs-lookup"><span data-stu-id="2bf1d-166">ICorDebugEval</span></span>](icordebugeval-interface.md)|<span data-ttu-id="2bf1d-167">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-167">1.0</span></span>|  
|`ver_ICorDebugValue`|[<span data-ttu-id="2bf1d-168">ICorDebugValue</span><span class="sxs-lookup"><span data-stu-id="2bf1d-168">ICorDebugValue</span></span>](icordebugvalue-interface.md)|<span data-ttu-id="2bf1d-169">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-169">1.0</span></span>|  
|`ver_ICorDebugGenericValue`|[<span data-ttu-id="2bf1d-170">ICorDebugGenericValue</span><span class="sxs-lookup"><span data-stu-id="2bf1d-170">ICorDebugGenericValue</span></span>](icordebuggenericvalue-interface.md)|<span data-ttu-id="2bf1d-171">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-171">1.0</span></span>|  
|`ver_ICorDebugReferenceValue`|[<span data-ttu-id="2bf1d-172">ICorDebugReferenceValue</span><span class="sxs-lookup"><span data-stu-id="2bf1d-172">ICorDebugReferenceValue</span></span>](icordebugreferencevalue-interface.md)|<span data-ttu-id="2bf1d-173">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-173">1.0</span></span>|  
|`ver_ICorDebugHeapValue`|[<span data-ttu-id="2bf1d-174">ICorDebugHeapValue</span><span class="sxs-lookup"><span data-stu-id="2bf1d-174">ICorDebugHeapValue</span></span>](icordebugheapvalue-interface.md)|<span data-ttu-id="2bf1d-175">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-175">1.0</span></span>|  
|`ver_ICorDebugObjectValue`|[<span data-ttu-id="2bf1d-176">ICorDebugObjectValue</span><span class="sxs-lookup"><span data-stu-id="2bf1d-176">ICorDebugObjectValue</span></span>](icordebugobjectvalue-interface.md)|<span data-ttu-id="2bf1d-177">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-177">1.0</span></span>|  
|`ver_ICorDebugBoxValue`|[<span data-ttu-id="2bf1d-178">ICorDebugBoxValue</span><span class="sxs-lookup"><span data-stu-id="2bf1d-178">ICorDebugBoxValue</span></span>](icordebugboxvalue-interface.md)|<span data-ttu-id="2bf1d-179">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-179">1.0</span></span>|  
|`ver_ICorDebugStringValue`|[<span data-ttu-id="2bf1d-180">ICorDebugStringValue</span><span class="sxs-lookup"><span data-stu-id="2bf1d-180">ICorDebugStringValue</span></span>](icordebugstringvalue-interface.md)|<span data-ttu-id="2bf1d-181">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-181">1.0</span></span>|  
|`ver_ICorDebugArrayValue`|[<span data-ttu-id="2bf1d-182">ICorDebugArrayValue</span><span class="sxs-lookup"><span data-stu-id="2bf1d-182">ICorDebugArrayValue</span></span>](icordebugarrayvalue-interface.md)|<span data-ttu-id="2bf1d-183">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-183">1.0</span></span>|  
|`ver_ICorDebugContext`|[<span data-ttu-id="2bf1d-184">ICorDebugCoNtext</span><span class="sxs-lookup"><span data-stu-id="2bf1d-184">ICorDebugContext</span></span>](icordebugcontext-interface.md)|<span data-ttu-id="2bf1d-185">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-185">1.0</span></span>|  
|`ver_ICorDebugEnum`|[<span data-ttu-id="2bf1d-186">ICorDebugEnum</span><span class="sxs-lookup"><span data-stu-id="2bf1d-186">ICorDebugEnum</span></span>](icordebugenum-interface1.md)|<span data-ttu-id="2bf1d-187">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-187">1.0</span></span>|  
|`ver_ICorDebugObjectEnum`|[<span data-ttu-id="2bf1d-188">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="2bf1d-188">ICorDebugObjectEnum</span></span>](icordebugobjectenum-interface.md)|<span data-ttu-id="2bf1d-189">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-189">1.0</span></span>|  
|`ver_ICorDebugBreakpointEnum`|[<span data-ttu-id="2bf1d-190">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="2bf1d-190">ICorDebugBreakpointEnum</span></span>](icordebugbreakpointenum-interface.md)|<span data-ttu-id="2bf1d-191">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-191">1.0</span></span>|  
|`ver_ICorDebugStepperEnum`|[<span data-ttu-id="2bf1d-192">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="2bf1d-192">ICorDebugStepperEnum</span></span>](icordebugstepperenum-interface.md)|<span data-ttu-id="2bf1d-193">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-193">1.0</span></span>|  
|`ver_ICorDebugProcessEnum`|[<span data-ttu-id="2bf1d-194">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="2bf1d-194">ICorDebugProcessEnum</span></span>](icordebugprocessenum-interface.md)|<span data-ttu-id="2bf1d-195">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-195">1.0</span></span>|  
|`ver_ICorDebugThreadEnum`|[<span data-ttu-id="2bf1d-196">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="2bf1d-196">ICorDebugThreadEnum</span></span>](icordebugthreadenum-interface1.md)|<span data-ttu-id="2bf1d-197">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-197">1.0</span></span>|  
|`ver_ICorDebugFrameEnum`|[<span data-ttu-id="2bf1d-198">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="2bf1d-198">ICorDebugFrameEnum</span></span>](icordebugframeenum-interface.md)|<span data-ttu-id="2bf1d-199">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-199">1.0</span></span>|  
|`ver_ICorDebugChainEnum`|[<span data-ttu-id="2bf1d-200">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="2bf1d-200">ICorDebugChainEnum</span></span>](icordebugchainenum-interface.md)|<span data-ttu-id="2bf1d-201">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-201">1.0</span></span>|  
|`ver_ICorDebugModuleEnum`|[<span data-ttu-id="2bf1d-202">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="2bf1d-202">ICorDebugModuleEnum</span></span>](icordebugmoduleenum-interface.md)|<span data-ttu-id="2bf1d-203">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-203">1.0</span></span>|  
|`ver_ICorDebugValueEnum`|[<span data-ttu-id="2bf1d-204">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="2bf1d-204">ICorDebugValueEnum</span></span>](icordebugvalueenum-interface.md)|<span data-ttu-id="2bf1d-205">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-205">1.0</span></span>|  
|`ver_ICorDebugCodeEnum`|[<span data-ttu-id="2bf1d-206">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="2bf1d-206">ICorDebugCodeEnum</span></span>](icordebugcodeenum-interface.md)|<span data-ttu-id="2bf1d-207">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-207">1.0</span></span>|  
|`ver_ICorDebugTypeEnum`|[<span data-ttu-id="2bf1d-208">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="2bf1d-208">ICorDebugTypeEnum</span></span>](icordebugtypeenum-interface.md)|<span data-ttu-id="2bf1d-209">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-209">1.0</span></span>|  
|`ver_ICorDebugErrorInfoEnum`|[<span data-ttu-id="2bf1d-210">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="2bf1d-210">ICorDebugErrorInfoEnum</span></span>](icordebugerrorinfoenum-interface.md)|<span data-ttu-id="2bf1d-211">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-211">1.0</span></span>|  
|`ver_ICorDebugAppDomainEnum`|[<span data-ttu-id="2bf1d-212">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="2bf1d-212">ICorDebugAppDomainEnum</span></span>](icordebugappdomainenum-interface.md)|<span data-ttu-id="2bf1d-213">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-213">1.0</span></span>|  
|`ver_ICorDebugAssemblyEnum`|[<span data-ttu-id="2bf1d-214">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="2bf1d-214">ICorDebugAssemblyEnum</span></span>](icordebugassemblyenum-interface.md)|<span data-ttu-id="2bf1d-215">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-215">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueErrorInfo`|[<span data-ttu-id="2bf1d-216">ICorDebugEditAndContinueErrorInfo</span><span class="sxs-lookup"><span data-stu-id="2bf1d-216">ICorDebugEditAndContinueErrorInfo</span></span>](icordebugeditandcontinueerrorinfo-interface.md)|<span data-ttu-id="2bf1d-217">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-217">1.0</span></span>|  
|`ver_ICorDebugEditAndContinueSnapshot`|[<span data-ttu-id="2bf1d-218">ICorDebugEditAndContinueSnapshot</span><span class="sxs-lookup"><span data-stu-id="2bf1d-218">ICorDebugEditAndContinueSnapshot</span></span>](icordebugeditandcontinuesnapshot-interface.md)|<span data-ttu-id="2bf1d-219">1.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-219">1.0</span></span>|  
|`ver_ICorDebugManagedCallback2`|[<span data-ttu-id="2bf1d-220">ICorDebugManagedCallback2</span><span class="sxs-lookup"><span data-stu-id="2bf1d-220">ICorDebugManagedCallback2</span></span>](icordebugmanagedcallback2-interface.md)|<span data-ttu-id="2bf1d-221">2.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-221">2.0</span></span>|  
|`ver_ICorDebugAppDomain2`|[<span data-ttu-id="2bf1d-222">ICorDebugAppDomain2</span><span class="sxs-lookup"><span data-stu-id="2bf1d-222">ICorDebugAppDomain2</span></span>](icordebugappdomain2-interface.md)|<span data-ttu-id="2bf1d-223">2.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-223">2.0</span></span>|  
|`ver_ICorDebugProcess2`|[<span data-ttu-id="2bf1d-224">ICorDebugProcess2</span><span class="sxs-lookup"><span data-stu-id="2bf1d-224">ICorDebugProcess2</span></span>](icordebugprocess2-interface1.md)|<span data-ttu-id="2bf1d-225">2.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-225">2.0</span></span>|  
|`ver_ICorDebugStepper2`|[<span data-ttu-id="2bf1d-226">ICorDebugStepper2</span><span class="sxs-lookup"><span data-stu-id="2bf1d-226">ICorDebugStepper2</span></span>](icordebugstepper2-interface1.md)|<span data-ttu-id="2bf1d-227">2.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-227">2.0</span></span>|  
|`ver_ICorDebugRegisterSet2`|[<span data-ttu-id="2bf1d-228">ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="2bf1d-228">ICorDebugRegisterSet2</span></span>](icordebugregisterset2-interface.md)|<span data-ttu-id="2bf1d-229">2.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-229">2.0</span></span>|  
|`ver_ICorDebugThread2`|[<span data-ttu-id="2bf1d-230">ICorDebugThread2</span><span class="sxs-lookup"><span data-stu-id="2bf1d-230">ICorDebugThread2</span></span>](icordebugthread2-interface.md)|<span data-ttu-id="2bf1d-231">2.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-231">2.0</span></span>|  
|`ver_ICorDebugILFrame2`|[<span data-ttu-id="2bf1d-232">ICorDebugILFrame2</span><span class="sxs-lookup"><span data-stu-id="2bf1d-232">ICorDebugILFrame2</span></span>](icordebugilframe2-interface.md)|<span data-ttu-id="2bf1d-233">2.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-233">2.0</span></span>|  
|`ver_ICorDebugModule2`|[<span data-ttu-id="2bf1d-234">ICorDebugModule2</span><span class="sxs-lookup"><span data-stu-id="2bf1d-234">ICorDebugModule2</span></span>](icordebugmodule2-interface.md)|<span data-ttu-id="2bf1d-235">2.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-235">2.0</span></span>|  
|`ver_ICorDebugFunction2`|[<span data-ttu-id="2bf1d-236">ICorDebugFunction2</span><span class="sxs-lookup"><span data-stu-id="2bf1d-236">ICorDebugFunction2</span></span>](icordebugfunction2-interface.md)|<span data-ttu-id="2bf1d-237">2.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-237">2.0</span></span>|  
|`ver_ICorDebugCode2`|[<span data-ttu-id="2bf1d-238">ICorDebugCode2</span><span class="sxs-lookup"><span data-stu-id="2bf1d-238">ICorDebugCode2</span></span>](icordebugcode2-interface.md)|<span data-ttu-id="2bf1d-239">2.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-239">2.0</span></span>|  
|`ver_ICorDebugClass2`|<span data-ttu-id="2bf1d-240">ICorDebugClass2</span><span class="sxs-lookup"><span data-stu-id="2bf1d-240">"ICorDebugClass2"</span></span>|<span data-ttu-id="2bf1d-241">2.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-241">2.0</span></span>|  
|`ver_ICorDebugValue2`|<span data-ttu-id="2bf1d-242">ICorDebugValue2</span><span class="sxs-lookup"><span data-stu-id="2bf1d-242">"ICorDebugValue2"</span></span>|<span data-ttu-id="2bf1d-243">2.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-243">2.0</span></span>|  
|`ver_ICorDebugEval2`|<span data-ttu-id="2bf1d-244">"ICorDebugEval2"。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-244">The "ICorDebugEval2".</span></span>|<span data-ttu-id="2bf1d-245">2.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-245">2.0</span></span>|  
|`ver_ICorDebugObjectValue2`|<span data-ttu-id="2bf1d-246">ICorDebugObjectValue2</span><span class="sxs-lookup"><span data-stu-id="2bf1d-246">"ICorDebugObjectValue2"</span></span>|<span data-ttu-id="2bf1d-247">2.0</span><span class="sxs-lookup"><span data-stu-id="2bf1d-247">2.0</span></span>|  
|`ver_ICorDebugThread3`|[<span data-ttu-id="2bf1d-248">ICorDebugThread3</span><span class="sxs-lookup"><span data-stu-id="2bf1d-248">ICorDebugThread3</span></span>](icordebugthread3-interface.md)|<span data-ttu-id="2bf1d-249">4</span><span class="sxs-lookup"><span data-stu-id="2bf1d-249">4</span></span>|  
|`ver_ICorDebugThread4`|[<span data-ttu-id="2bf1d-250">ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="2bf1d-250">ICorDebugThread4</span></span>](icordebugthread4-interface.md)|<span data-ttu-id="2bf1d-251">4</span><span class="sxs-lookup"><span data-stu-id="2bf1d-251">4</span></span>|  
|`ver_ICorDebugStackWalk`|[<span data-ttu-id="2bf1d-252">ICorDebugStackWalk</span><span class="sxs-lookup"><span data-stu-id="2bf1d-252">ICorDebugStackWalk</span></span>](icordebugstackwalk-interface.md)|<span data-ttu-id="2bf1d-253">4</span><span class="sxs-lookup"><span data-stu-id="2bf1d-253">4</span></span>|  
|`ver_ICorDebugNativeFrame2`|[<span data-ttu-id="2bf1d-254">ICorDebugNativeFrame2</span><span class="sxs-lookup"><span data-stu-id="2bf1d-254">ICorDebugNativeFrame2</span></span>](icordebugnativeframe2-interface.md)|<span data-ttu-id="2bf1d-255">4</span><span class="sxs-lookup"><span data-stu-id="2bf1d-255">4</span></span>|  
|`ver_ICorDebugInternalFrame2`|[<span data-ttu-id="2bf1d-256">ICorDebugInternalFrame2</span><span class="sxs-lookup"><span data-stu-id="2bf1d-256">ICorDebugInternalFrame2</span></span>](icordebuginternalframe2-interface.md)|<span data-ttu-id="2bf1d-257">4</span><span class="sxs-lookup"><span data-stu-id="2bf1d-257">4</span></span>|  
|`ver_ICorDebugRuntimeUnwindableFrame`|[<span data-ttu-id="2bf1d-258">ICorDebugRuntimeUnwindableFrame</span><span class="sxs-lookup"><span data-stu-id="2bf1d-258">ICorDebugRuntimeUnwindableFrame</span></span>](icordebugruntimeunwindableframe-interface.md)|<span data-ttu-id="2bf1d-259">4</span><span class="sxs-lookup"><span data-stu-id="2bf1d-259">4</span></span>|  
|`ver_ICorDebugHeapValue3`|[<span data-ttu-id="2bf1d-260">ICorDebugHeapValue3 介面</span><span class="sxs-lookup"><span data-stu-id="2bf1d-260">ICorDebugHeapValue3 Interface</span></span>](icordebugheapvalue3-interface.md)|<span data-ttu-id="2bf1d-261">4</span><span class="sxs-lookup"><span data-stu-id="2bf1d-261">4</span></span>|  
|`ver_ICorDebugBlockingObjectEnum`|[<span data-ttu-id="2bf1d-262">ICorDebugBlockingObjectEnum 介面</span><span class="sxs-lookup"><span data-stu-id="2bf1d-262">ICorDebugBlockingObjectEnum Interface</span></span>](icordebugblockingobjectenum-interface.md)|<span data-ttu-id="2bf1d-263">4</span><span class="sxs-lookup"><span data-stu-id="2bf1d-263">4</span></span>|  
|`ver_ICorDebugValue3`|[<span data-ttu-id="2bf1d-264">ICorDebugValue3</span><span class="sxs-lookup"><span data-stu-id="2bf1d-264">ICorDebugValue3</span></span>](icordebugvalue3-interface.md)|<span data-ttu-id="2bf1d-265">4</span><span class="sxs-lookup"><span data-stu-id="2bf1d-265">4</span></span>|  
|`ver_ICorDebugComObjectValue`|[<span data-ttu-id="2bf1d-266">ICorDebugComObjectValue</span><span class="sxs-lookup"><span data-stu-id="2bf1d-266">ICorDebugComObjectValue</span></span>](icordebugcomobjectvalue-interface.md)|<span data-ttu-id="2bf1d-267">4.5</span><span class="sxs-lookup"><span data-stu-id="2bf1d-267">4.5</span></span>|  
|`ver_ICorDebugAppDomain3`|[<span data-ttu-id="2bf1d-268">ICorDebugAppDomain3</span><span class="sxs-lookup"><span data-stu-id="2bf1d-268">ICorDebugAppDomain3</span></span>](icordebugappdomain3-interface.md)|<span data-ttu-id="2bf1d-269">4.5</span><span class="sxs-lookup"><span data-stu-id="2bf1d-269">4.5</span></span>|  
|`ver_ICorDebugCode3`|[<span data-ttu-id="2bf1d-270">ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="2bf1d-270">ICorDebugCode3</span></span>](icordebugcode3-interface.md)|<span data-ttu-id="2bf1d-271">4.5</span><span class="sxs-lookup"><span data-stu-id="2bf1d-271">4.5</span></span>|  
|`ver_ICorDebugILFrame3`|[<span data-ttu-id="2bf1d-272">ICorDebugILFrame3</span><span class="sxs-lookup"><span data-stu-id="2bf1d-272">ICorDebugILFrame3</span></span>](icordebugilframe3-interface.md)|<span data-ttu-id="2bf1d-273">4.5</span><span class="sxs-lookup"><span data-stu-id="2bf1d-273">4.5</span></span>|  
|`CorDebugLatestVersion`|<span data-ttu-id="2bf1d-274">.NET Framework 的版本 (包括其所有 Service Pack) 為最新版本。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-274">The version of the .NET Framework, including all of its service packs, is the latest version.</span></span>|-|  
  
## <a name="remarks"></a><span data-ttu-id="2bf1d-275">備註</span><span class="sxs-lookup"><span data-stu-id="2bf1d-275">Remarks</span></span>  
 <span data-ttu-id="2bf1d-276">偵錯工具可以在[CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md)函式中使用 `CorDebugInterfaceVersion` 列舉，以指定偵錯工具支援之 .NET Framework 的最高版本。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-276">A debugger can use the `CorDebugInterfaceVersion` enumeration in the [CreateDebuggingInterfaceFromVersion](../../../../docs/framework/unmanaged-api/hosting/createdebugginginterfacefromversion-function.md) function to specify the highest version of the .NET Framework that the debugger supports.</span></span>  
  
## <a name="interface-names"></a><span data-ttu-id="2bf1d-277">介面名稱</span><span class="sxs-lookup"><span data-stu-id="2bf1d-277">Interface Names</span></span>  
 <span data-ttu-id="2bf1d-278">在偵錯 API (例如，`ICorDebugThread3` 中的 "3") 中，出現在介面名稱結尾的號碼是指定介面版本，而不是 .NET Framework 的版本。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-278">The number that appears at the end of the interface names in the debugging API (for example, the "3" in `ICorDebugThread3`) specifies the version of the interface, not the version of the .NET Framework.</span></span> <span data-ttu-id="2bf1d-279">偵錯 API 中的所有介面名稱都有包含版本號碼，但 .NET Framework 第 1 版中導入的介面除外。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-279">All interface names in the debugging API include version numbers except for interfaces that were introduced in the .NET Framework version 1.</span></span> <span data-ttu-id="2bf1d-280">介面版本號碼與 .NET Framework 版本號碼之間的任何對應都是巧合。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-280">Any correspondence between interface version numbers and.NET Framework version numbers are coincidental.</span></span>  
  
- <span data-ttu-id="2bf1d-281">.NET Framework 1.0 版中導入的介面沒有包含號碼，因為全都隱含為第 1 版。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-281">Interfaces that were introduced in the .NET Framework version 1.0 do not include numbers, because they are all implicitly version 1.</span></span>  
  
- <span data-ttu-id="2bf1d-282">.NET Framework 1.1 版使用 1.0 版介面，而且沒有導入任何新偵錯介面。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-282">The .NET Framework version 1.1 uses version 1.0 interfaces, and does not introduce any new debugging interfaces.</span></span>  
  
- <span data-ttu-id="2bf1d-283">在 .NET Framework 2.0 版中導入的 14 個偵錯介面是其第 1 版相對版本的邏輯擴充功能，並且在其名稱中包含數字 "2"。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-283">The 14 debugging interfaces introduced in the .NET Framework version 2.0 are logical extensions of their version 1 counterparts and include the number "2" in their names.</span></span>  
  
- <span data-ttu-id="2bf1d-284">.NET Framework 3.0 和 3.5 版使用現有的 .NET Framework 2.0 介面，而且沒有導入任何新介面。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-284">The .NET Framework versions 3.0 and 3.5 use the existing .NET Framework 2.0 interfaces, and do not introduce any new interfaces.</span></span>  
  
- <span data-ttu-id="2bf1d-285">.NET Framework 4 引進了介面版本的混合。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-285">The .NET Framework 4 introduces a mix of interface versions.</span></span> <span data-ttu-id="2bf1d-286">例如，`ICorDebugThread3` 和 `ICorDebugThread4` 會以 `ICorDebugThread` 介面的第三和第四版出現。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-286">For example, both `ICorDebugThread3` and `ICorDebugThread4` appear as the third and fourth versions of the `ICorDebugThread` interface.</span></span> <span data-ttu-id="2bf1d-287">.NET Framework 4 也引進第一版的 `ICorDebugStackWalk` 介面和第二版的 `ICorDebugNativeFrame` 介面（`ICorDebugNativeFrame2`）。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-287">The .NET Framework 4 also introduces the first version of the `ICorDebugStackWalk` interface and the second version of the `ICorDebugNativeFrame` interface (`ICorDebugNativeFrame2`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bf1d-288">需求</span><span class="sxs-lookup"><span data-stu-id="2bf1d-288">Requirements</span></span>  
 <span data-ttu-id="2bf1d-289">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2bf1d-289">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bf1d-290">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2bf1d-290">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2bf1d-291">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bf1d-291">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bf1d-292">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bf1d-292">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bf1d-293">請參閱</span><span class="sxs-lookup"><span data-stu-id="2bf1d-293">See also</span></span>

- [<span data-ttu-id="2bf1d-294">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="2bf1d-294">Debugging Enumerations</span></span>](debugging-enumerations.md)
