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
ms.openlocfilehash: d9698afa2723a5d772ecf5a055f09c5ee3bc13f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727649"
---
# <a name="icordebugsteppersteprange-method"></a><span data-ttu-id="c485d-102">ICorDebugStepper::StepRange 方法</span><span class="sxs-lookup"><span data-stu-id="c485d-102">ICorDebugStepper::StepRange Method</span></span>

<span data-ttu-id="c485d-103">讓這個 ICorDebugStepper 在其包含的執行緒上執行一次，並在到達指定範圍的最後一個程式碼時傳回。</span><span class="sxs-lookup"><span data-stu-id="c485d-103">Causes this ICorDebugStepper to single-step through its containing thread, and to return when it reaches code beyond the last of the specified ranges.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c485d-104">語法</span><span class="sxs-lookup"><span data-stu-id="c485d-104">Syntax</span></span>  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c485d-105">參數</span><span class="sxs-lookup"><span data-stu-id="c485d-105">Parameters</span></span>  

 `bStepIn`  
 <span data-ttu-id="c485d-106">在將設定為，逐步執行在 `true` 執行緒中呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="c485d-106">[in] Set to `true` to step into a function that is called within the thread.</span></span> <span data-ttu-id="c485d-107">設定為 `false` 以不進入函數。</span><span class="sxs-lookup"><span data-stu-id="c485d-107">Set to `false` to step over the function.</span></span>  
  
 `ranges`  
 <span data-ttu-id="c485d-108">在COR_DEBUG_STEP_RANGE 結構的陣列，其中每個結構都指定一個範圍。</span><span class="sxs-lookup"><span data-stu-id="c485d-108">[in] An array of COR_DEBUG_STEP_RANGE structures, each of which specifies a range.</span></span>  
  
 `cRangeCount`  
 <span data-ttu-id="c485d-109">[in] `ranges` 陣列的大小。</span><span class="sxs-lookup"><span data-stu-id="c485d-109">[in] The size of the `ranges` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c485d-110">備註</span><span class="sxs-lookup"><span data-stu-id="c485d-110">Remarks</span></span>  

 <span data-ttu-id="c485d-111">`StepRange`方法的運作方式與[ICorDebugStepper：： Step](icordebugstepper-step-method.md)方法相同，不同之處在于它不會完成，直到到達指定範圍之外的程式碼為止。</span><span class="sxs-lookup"><span data-stu-id="c485d-111">The `StepRange` method works like the [ICorDebugStepper::Step](icordebugstepper-step-method.md) method, except that it does not complete until code outside the given range is reached.</span></span>  
  
 <span data-ttu-id="c485d-112">這會比一次逐步執行一個指令更有效率。</span><span class="sxs-lookup"><span data-stu-id="c485d-112">This can be more efficient than stepping one instruction at a time.</span></span> <span data-ttu-id="c485d-113">範圍會指定為從分檔器框架開頭算起的位移組清單。</span><span class="sxs-lookup"><span data-stu-id="c485d-113">Ranges are specified as a list of offset pairs from the start of the stepper's frame.</span></span>  
  
 <span data-ttu-id="c485d-114">範圍是指方法的 Microsoft 中繼語言 (MSIL) 程式碼的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="c485d-114">Ranges are relative to the Microsoft intermediate language (MSIL) code of a method.</span></span> <span data-ttu-id="c485d-115">使用呼叫 [ICorDebugStepper：： SetRangeIL](icordebugstepper-setrangeil-method.md) ， `false` 使範圍相對於方法的機器碼。</span><span class="sxs-lookup"><span data-stu-id="c485d-115">Call [ICorDebugStepper::SetRangeIL](icordebugstepper-setrangeil-method.md) with `false` to make the ranges relative to the native code of a method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c485d-116">需求</span><span class="sxs-lookup"><span data-stu-id="c485d-116">Requirements</span></span>  

 <span data-ttu-id="c485d-117">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c485d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c485d-118">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c485d-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c485d-119">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c485d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c485d-120">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c485d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
