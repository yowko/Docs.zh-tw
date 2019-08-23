---
title: ICorDebugEnum 介面
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
ms.openlocfilehash: b25c47e101ad0fb8e8cbdbb2718a41c9be6c0c22
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931989"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="b68b6-102">ICorDebugEnum 介面</span><span class="sxs-lookup"><span data-stu-id="b68b6-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="b68b6-103">做為偵錯工具所使用之枚舉器的抽象基底介面。</span><span class="sxs-lookup"><span data-stu-id="b68b6-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b68b6-104">方法</span><span class="sxs-lookup"><span data-stu-id="b68b6-104">Methods</span></span>  
  
|<span data-ttu-id="b68b6-105">方法</span><span class="sxs-lookup"><span data-stu-id="b68b6-105">Method</span></span>|<span data-ttu-id="b68b6-106">說明</span><span class="sxs-lookup"><span data-stu-id="b68b6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b68b6-107">Clone 方法</span><span class="sxs-lookup"><span data-stu-id="b68b6-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-clone-method.md)|<span data-ttu-id="b68b6-108">建立這個`ICorDebugEnum`物件的複本。</span><span class="sxs-lookup"><span data-stu-id="b68b6-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="b68b6-109">GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="b68b6-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-getcount-method.md)|<span data-ttu-id="b68b6-110">取得列舉中的專案數。</span><span class="sxs-lookup"><span data-stu-id="b68b6-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="b68b6-111">Reset 方法</span><span class="sxs-lookup"><span data-stu-id="b68b6-111">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-reset-method.md)|<span data-ttu-id="b68b6-112">將游標移至列舉的開頭。</span><span class="sxs-lookup"><span data-stu-id="b68b6-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="b68b6-113">Skip 方法</span><span class="sxs-lookup"><span data-stu-id="b68b6-113">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-skip-method.md)|<span data-ttu-id="b68b6-114">在列舉中, 將資料指標向後移動指定的專案數。</span><span class="sxs-lookup"><span data-stu-id="b68b6-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b68b6-115">備註</span><span class="sxs-lookup"><span data-stu-id="b68b6-115">Remarks</span></span>  
 <span data-ttu-id="b68b6-116">下列枚舉器衍生自`ICorDebugEnum`:</span><span class="sxs-lookup"><span data-stu-id="b68b6-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="b68b6-117">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="b68b6-118">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="b68b6-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-119">ICorDebugBlockingObjectEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="b68b6-120">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="b68b6-121">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="b68b6-122">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="b68b6-123">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="b68b6-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-124">ICorDebugExceptionObjectCallStackEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="b68b6-125">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="b68b6-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-126">ICorDebugGCReferenceEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="b68b6-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-127">ICorDebugGuidToTypeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="b68b6-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-128">ICorDebugHeapEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="b68b6-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-129">ICorDebugHeapSegmentEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="b68b6-130">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="b68b6-131">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="b68b6-132">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="b68b6-133">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="b68b6-134">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="b68b6-135">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="b68b6-136">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="b68b6-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="b68b6-137">ICorDebugVariableHomeEnum</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="b68b6-138">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="b68b6-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b68b6-139">需求</span><span class="sxs-lookup"><span data-stu-id="b68b6-139">Requirements</span></span>  
 <span data-ttu-id="b68b6-140">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b68b6-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b68b6-141">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b68b6-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b68b6-142">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b68b6-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b68b6-143">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b68b6-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b68b6-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b68b6-144">See also</span></span>

- [<span data-ttu-id="b68b6-145">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="b68b6-145">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
