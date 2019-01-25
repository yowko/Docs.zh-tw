---
title: ICorDebugEnum 介面 1
ms.date: 03/30/2017
api_name:
- ICorDebugEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum
helpviewer_keywords:
- ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 80be7efe-2c32-4b9f-8c52-40c6f6268219
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 97080f7d850e67d635f9a65ee85ad3ddddbb244d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732748"
---
# <a name="icordebugenum-interface1"></a><span data-ttu-id="7bfe1-102">ICorDebugEnum 介面 1</span><span class="sxs-lookup"><span data-stu-id="7bfe1-102">ICorDebugEnum Interface1</span></span>
<span data-ttu-id="7bfe1-103">做為 偵錯的應用程式所使用的列舉值的抽象基底介面。</span><span class="sxs-lookup"><span data-stu-id="7bfe1-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7bfe1-104">方法</span><span class="sxs-lookup"><span data-stu-id="7bfe1-104">Methods</span></span>  
  
|<span data-ttu-id="7bfe1-105">方法</span><span class="sxs-lookup"><span data-stu-id="7bfe1-105">Method</span></span>|<span data-ttu-id="7bfe1-106">描述</span><span class="sxs-lookup"><span data-stu-id="7bfe1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7bfe1-107">Clone 方法</span><span class="sxs-lookup"><span data-stu-id="7bfe1-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="7bfe1-108">建立一份這`ICorDebugEnum`物件。</span><span class="sxs-lookup"><span data-stu-id="7bfe1-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="7bfe1-109">GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="7bfe1-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="7bfe1-110">列舉中取得的項目數。</span><span class="sxs-lookup"><span data-stu-id="7bfe1-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="7bfe1-111">Reset 方法</span><span class="sxs-lookup"><span data-stu-id="7bfe1-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="7bfe1-112">將游標移至列舉型別的開頭。</span><span class="sxs-lookup"><span data-stu-id="7bfe1-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="7bfe1-113">Skip 方法</span><span class="sxs-lookup"><span data-stu-id="7bfe1-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="7bfe1-114">將游標移往前列舉中所指定的項目數。</span><span class="sxs-lookup"><span data-stu-id="7bfe1-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bfe1-115">備註</span><span class="sxs-lookup"><span data-stu-id="7bfe1-115">Remarks</span></span>  
 <span data-ttu-id="7bfe1-116">下列的列舉值衍生自`ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="7bfe1-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
-   <span data-ttu-id="7bfe1-117">"ICorDebugAppDomainEnum"</span><span class="sxs-lookup"><span data-stu-id="7bfe1-117">"ICorDebugAppDomainEnum"</span></span>  
  
-   <span data-ttu-id="7bfe1-118">「 ICorDebugAssemblyEnum"</span><span class="sxs-lookup"><span data-stu-id="7bfe1-118">"ICorDebugAssemblyEnum"</span></span>  
  
-   [<span data-ttu-id="7bfe1-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="7bfe1-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
-   <span data-ttu-id="7bfe1-120">"ICorDebugBreakpointEnum"</span><span class="sxs-lookup"><span data-stu-id="7bfe1-120">"ICorDebugBreakpointEnum"</span></span>  
  
-   <span data-ttu-id="7bfe1-121">「 ICorDebugChainEnum"</span><span class="sxs-lookup"><span data-stu-id="7bfe1-121">"ICorDebugChainEnum"</span></span>  
  
-   <span data-ttu-id="7bfe1-122">「 ICorDebugCodeEnum"</span><span class="sxs-lookup"><span data-stu-id="7bfe1-122">"ICorDebugCodeEnum"</span></span>  
  
-   <span data-ttu-id="7bfe1-123">「 ICorDebugErrorInfoEnum"</span><span class="sxs-lookup"><span data-stu-id="7bfe1-123">"ICorDebugErrorInfoEnum"</span></span>  
  
-   [<span data-ttu-id="7bfe1-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="7bfe1-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
-   <span data-ttu-id="7bfe1-125">"ICorDebugFrameEnum"</span><span class="sxs-lookup"><span data-stu-id="7bfe1-125">"ICorDebugFrameEnum"</span></span>  
  
-   [<span data-ttu-id="7bfe1-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="7bfe1-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
-   [<span data-ttu-id="7bfe1-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="7bfe1-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
-   [<span data-ttu-id="7bfe1-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="7bfe1-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
-   [<span data-ttu-id="7bfe1-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="7bfe1-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
-   <span data-ttu-id="7bfe1-130">「 ICorDebugModuleEnum"</span><span class="sxs-lookup"><span data-stu-id="7bfe1-130">"ICorDebugModuleEnum"</span></span>  
  
-   <span data-ttu-id="7bfe1-131">"ICorDebugObjectEnum"</span><span class="sxs-lookup"><span data-stu-id="7bfe1-131">"ICorDebugObjectEnum"</span></span>  
  
-   <span data-ttu-id="7bfe1-132">"ICorDebugProcessEnum"</span><span class="sxs-lookup"><span data-stu-id="7bfe1-132">"ICorDebugProcessEnum"</span></span>  
  
-   <span data-ttu-id="7bfe1-133">"ICorDebugStepperEnum"</span><span class="sxs-lookup"><span data-stu-id="7bfe1-133">"ICorDebugStepperEnum"</span></span>  
  
-   <span data-ttu-id="7bfe1-134">「 ICorDebugThreadEnum"</span><span class="sxs-lookup"><span data-stu-id="7bfe1-134">"ICorDebugThreadEnum"</span></span>  
  
-   <span data-ttu-id="7bfe1-135">「 ICorDebugTypeEnum"</span><span class="sxs-lookup"><span data-stu-id="7bfe1-135">"ICorDebugTypeEnum"</span></span>  
  
-   <span data-ttu-id="7bfe1-136">「 ICorDebugValueEnum"</span><span class="sxs-lookup"><span data-stu-id="7bfe1-136">"ICorDebugValueEnum"</span></span>  
  
-   [<span data-ttu-id="7bfe1-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="7bfe1-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="7bfe1-138">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="7bfe1-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bfe1-139">需求</span><span class="sxs-lookup"><span data-stu-id="7bfe1-139">Requirements</span></span>  
 <span data-ttu-id="7bfe1-140">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7bfe1-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bfe1-141">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7bfe1-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bfe1-142">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bfe1-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bfe1-143">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bfe1-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bfe1-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bfe1-144">See also</span></span>
- [<span data-ttu-id="7bfe1-145">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7bfe1-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
