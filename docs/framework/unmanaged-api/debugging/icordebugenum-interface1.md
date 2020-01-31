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
ms.openlocfilehash: cc5598f9cbec4b97bb75f83fb18ccf8742904272
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783013"
---
# <a name="icordebugenum-interface"></a><span data-ttu-id="3c95f-102">ICorDebugEnum 介面</span><span class="sxs-lookup"><span data-stu-id="3c95f-102">ICorDebugEnum Interface</span></span>

<span data-ttu-id="3c95f-103">做為偵錯工具所使用之枚舉器的抽象基底介面。</span><span class="sxs-lookup"><span data-stu-id="3c95f-103">Serves as the abstract base interface for the enumerators that are used by a debugging application.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3c95f-104">方法</span><span class="sxs-lookup"><span data-stu-id="3c95f-104">Methods</span></span>  
  
|<span data-ttu-id="3c95f-105">方法</span><span class="sxs-lookup"><span data-stu-id="3c95f-105">Method</span></span>|<span data-ttu-id="3c95f-106">描述</span><span class="sxs-lookup"><span data-stu-id="3c95f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3c95f-107">Clone 方法</span><span class="sxs-lookup"><span data-stu-id="3c95f-107">Clone Method</span></span>](icordebugenum-clone-method.md)|<span data-ttu-id="3c95f-108">建立這個 `ICorDebugEnum` 物件的複本。</span><span class="sxs-lookup"><span data-stu-id="3c95f-108">Creates a copy of this `ICorDebugEnum` object.</span></span>|  
|[<span data-ttu-id="3c95f-109">GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="3c95f-109">GetCount Method</span></span>](icordebugenum-getcount-method.md)|<span data-ttu-id="3c95f-110">取得列舉中的專案數。</span><span class="sxs-lookup"><span data-stu-id="3c95f-110">Gets the number of items in the enumeration.</span></span>|  
|[<span data-ttu-id="3c95f-111">Reset 方法</span><span class="sxs-lookup"><span data-stu-id="3c95f-111">Reset Method</span></span>](icordebugenum-reset-method.md)|<span data-ttu-id="3c95f-112">將游標移至列舉的開頭。</span><span class="sxs-lookup"><span data-stu-id="3c95f-112">Moves the cursor to the beginning of the enumeration.</span></span>|  
|[<span data-ttu-id="3c95f-113">Skip 方法</span><span class="sxs-lookup"><span data-stu-id="3c95f-113">Skip Method</span></span>](icordebugenum-skip-method.md)|<span data-ttu-id="3c95f-114">在列舉中，將資料指標向後移動指定的專案數。</span><span class="sxs-lookup"><span data-stu-id="3c95f-114">Moves the cursor forward in the enumeration by the specified number of items.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c95f-115">備註</span><span class="sxs-lookup"><span data-stu-id="3c95f-115">Remarks</span></span>  
 <span data-ttu-id="3c95f-116">下列枚舉器衍生自 `ICorDebugEnum`：</span><span class="sxs-lookup"><span data-stu-id="3c95f-116">The following enumerators derive from `ICorDebugEnum`:</span></span>  
  
- <span data-ttu-id="3c95f-117">ICorDebugAppDomainEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-117">"ICorDebugAppDomainEnum"</span></span>  
  
- <span data-ttu-id="3c95f-118">ICorDebugAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-118">"ICorDebugAssemblyEnum"</span></span>  
  
- [<span data-ttu-id="3c95f-119">ICorDebugBlockingObjectEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-119">ICorDebugBlockingObjectEnum</span></span>](icordebugblockingobjectenum-interface.md)  
  
- <span data-ttu-id="3c95f-120">ICorDebugBreakpointEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-120">"ICorDebugBreakpointEnum"</span></span>  
  
- <span data-ttu-id="3c95f-121">ICorDebugChainEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-121">"ICorDebugChainEnum"</span></span>  
  
- <span data-ttu-id="3c95f-122">ICorDebugCodeEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-122">"ICorDebugCodeEnum"</span></span>  
  
- <span data-ttu-id="3c95f-123">ICorDebugErrorInfoEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-123">"ICorDebugErrorInfoEnum"</span></span>  
  
- [<span data-ttu-id="3c95f-124">ICorDebugExceptionObjectCallStackEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-124">ICorDebugExceptionObjectCallStackEnum</span></span>](icordebugexceptionobjectcallstackenum-interface.md)  
  
- <span data-ttu-id="3c95f-125">ICorDebugFrameEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-125">"ICorDebugFrameEnum"</span></span>  
  
- [<span data-ttu-id="3c95f-126">ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-126">ICorDebugGCReferenceEnum</span></span>](icordebuggcreferenceenum-interface.md)  
  
- [<span data-ttu-id="3c95f-127">ICorDebugGuidToTypeEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-127">ICorDebugGuidToTypeEnum</span></span>](icordebugguidtotypeenum-interface.md)  
  
- [<span data-ttu-id="3c95f-128">ICorDebugHeapEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-128">ICorDebugHeapEnum</span></span>](icordebugheapenum-interface.md)  
  
- [<span data-ttu-id="3c95f-129">ICorDebugHeapSegmentEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-129">ICorDebugHeapSegmentEnum</span></span>](icordebugheapsegmentenum-interface.md)  
  
- <span data-ttu-id="3c95f-130">ICorDebugModuleEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-130">"ICorDebugModuleEnum"</span></span>  
  
- <span data-ttu-id="3c95f-131">ICorDebugObjectEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-131">"ICorDebugObjectEnum"</span></span>  
  
- <span data-ttu-id="3c95f-132">ICorDebugProcessEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-132">"ICorDebugProcessEnum"</span></span>  
  
- <span data-ttu-id="3c95f-133">ICorDebugStepperEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-133">"ICorDebugStepperEnum"</span></span>  
  
- <span data-ttu-id="3c95f-134">ICorDebugThreadEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-134">"ICorDebugThreadEnum"</span></span>  
  
- <span data-ttu-id="3c95f-135">ICorDebugTypeEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-135">"ICorDebugTypeEnum"</span></span>  
  
- <span data-ttu-id="3c95f-136">ICorDebugValueEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-136">"ICorDebugValueEnum"</span></span>  
  
- [<span data-ttu-id="3c95f-137">ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="3c95f-137">ICorDebugVariableHomeEnum</span></span>](icordebugvariablehomeenum-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="3c95f-138">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="3c95f-138">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c95f-139">需求</span><span class="sxs-lookup"><span data-stu-id="3c95f-139">Requirements</span></span>  
 <span data-ttu-id="3c95f-140">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="3c95f-140">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c95f-141">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c95f-141">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c95f-142">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c95f-142">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c95f-143">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c95f-143">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c95f-144">請參閱</span><span class="sxs-lookup"><span data-stu-id="3c95f-144">See also</span></span>

- [<span data-ttu-id="3c95f-145">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="3c95f-145">Debugging Interfaces</span></span>](debugging-interfaces.md)
