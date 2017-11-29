---
title: "ICorDebugStepper::StepRange 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.StepRange
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 72a68000691dd23a55b77265cae839bea8b4ae1e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="02913-102">ICorDebugStepper::StepRange 方法</span><span class="sxs-lookup"><span data-stu-id="02913-102">ICorDebugStepper::StepRange Method</span></span>
<span data-ttu-id="02913-103">會導致此 ICorDebugStepper 單一步驟透過其包含的執行緒，並傳回當它到達程式碼超出指定範圍的最後一個。</span><span class="sxs-lookup"><span data-stu-id="02913-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02913-104">語法</span><span class="sxs-lookup"><span data-stu-id="02913-104">Syntax</span></span>  
  
```  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="02913-105">參數</span><span class="sxs-lookup"><span data-stu-id="02913-105">Parameters</span></span>  
 `bStepIn`  
 <span data-ttu-id="02913-106">[in]設定為`true`逐步執行至呼叫的執行緒內的函式。</span><span class="sxs-lookup"><span data-stu-id="02913-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="02913-107">設定為`false`進入函式。</span><span class="sxs-lookup"><span data-stu-id="02913-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="02913-108">[in]COR_DEBUG_STEP_RANGE 結構陣列，其中每個指定的範圍。</span><span class="sxs-lookup"><span data-stu-id="02913-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="02913-109">[in] `ranges` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="02913-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02913-110">備註</span><span class="sxs-lookup"><span data-stu-id="02913-110">Remarks</span></span>  
 <span data-ttu-id="02913-111">`StepRange`方法的運作方式類似[icordebugstepper:: Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)方法，不同之處在於未指定範圍外的程式碼直到完成為止。</span><span class="sxs-lookup"><span data-stu-id="02913-111">The `StepRange` method works like the [ICorDebugStepper::Step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="02913-112">這可以是比一次一個指令碼逐步偵錯更有效率。</span><span class="sxs-lookup"><span data-stu-id="02913-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="02913-113">範圍會指定為從 stepper 框架開頭的位移組的清單。</span><span class="sxs-lookup"><span data-stu-id="02913-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="02913-114">範圍是相對於方法的 Microsoft intermediate language (MSIL) 程式碼。</span><span class="sxs-lookup"><span data-stu-id="02913-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="02913-115">呼叫[icordebugstepper:: Setrangeil](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)與`false`讓方法的原生程式碼的相對範圍。</span><span class="sxs-lookup"><span data-stu-id="02913-115">Call [ICorDebugStepper::SetRangeIL](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02913-116">需求</span><span class="sxs-lookup"><span data-stu-id="02913-116">Requirements</span></span>  
 <span data-ttu-id="02913-117">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="02913-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02913-118">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02913-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02913-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02913-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02913-120">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02913-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
