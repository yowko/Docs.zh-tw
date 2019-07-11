---
title: ICorDebugStepper::StepRange 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e1ace501bf5de741ea110fe4d3bb4bc44843bf8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760532"
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="acaee-102">ICorDebugStepper::StepRange 方法</span><span class="sxs-lookup"><span data-stu-id="acaee-102">ICorDebugStepper::StepRange Method</span></span>
<span data-ttu-id="acaee-103">會導致此 ICorDebugStepper 單一步驟透過其包含的執行緒，並傳回在到達指定範圍的最後一個以外的程式碼。</span><span class="sxs-lookup"><span data-stu-id="acaee-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="acaee-104">語法</span><span class="sxs-lookup"><span data-stu-id="acaee-104">Syntax</span></span>  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="acaee-105">參數</span><span class="sxs-lookup"><span data-stu-id="acaee-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="acaee-106">[in]若要設定`true`逐步執行至呼叫執行緒內的函式。</span><span class="sxs-lookup"><span data-stu-id="acaee-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="acaee-107">若要設定`false`進入函式。</span><span class="sxs-lookup"><span data-stu-id="acaee-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="acaee-108">[in]每一個都會指定範圍之 COR_DEBUG_STEP_RANGE 結構陣列。</span><span class="sxs-lookup"><span data-stu-id="acaee-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="acaee-109">[in] `ranges` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="acaee-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acaee-110">備註</span><span class="sxs-lookup"><span data-stu-id="acaee-110">Remarks</span></span>  
 <span data-ttu-id="acaee-111">`StepRange`方法的運作方式類似[icordebugstepper:: Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)方法，不同之處在於未指定的範圍之外的程式碼直到完成為止。</span><span class="sxs-lookup"><span data-stu-id="acaee-111">The `StepRange` method works like the [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="acaee-112">這可以是比一次一個指令碼逐步偵錯更有效率。</span><span class="sxs-lookup"><span data-stu-id="acaee-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="acaee-113">範圍會指定為從步進框架的開頭的位移組的清單。</span><span class="sxs-lookup"><span data-stu-id="acaee-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="acaee-114">範圍是相對於方法的 Microsoft intermediate language (MSIL) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="acaee-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="acaee-115">呼叫[icordebugstepper:: Setrangeil](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)與`false`進行相對於方法的原生程式碼範圍。</span><span class="sxs-lookup"><span data-stu-id="acaee-115">Call [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acaee-116">需求</span><span class="sxs-lookup"><span data-stu-id="acaee-116">Requirements</span></span>  
 <span data-ttu-id="acaee-117">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="acaee-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acaee-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="acaee-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acaee-119">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="acaee-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acaee-120">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acaee-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
