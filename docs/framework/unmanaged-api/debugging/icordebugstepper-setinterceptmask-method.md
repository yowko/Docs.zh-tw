---
title: ICorDebugStepper::SetInterceptMask 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetInterceptMask
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type:
- apiref
ms.openlocfilehash: 9792abb4ee38a45aae59eaf79f1f0499539bd2ae
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791758"
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="8f6c1-102">ICorDebugStepper::SetInterceptMask 方法</span><span class="sxs-lookup"><span data-stu-id="8f6c1-102">ICorDebugStepper::SetInterceptMask Method</span></span>
<span data-ttu-id="8f6c1-103">設定值，指定要逐步執行的程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="8f6c1-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f6c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="8f6c1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f6c1-105">參數</span><span class="sxs-lookup"><span data-stu-id="8f6c1-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="8f6c1-106">在CorDebugIntercept 列舉的值組合，指定程式碼的類型。</span><span class="sxs-lookup"><span data-stu-id="8f6c1-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f6c1-107">備註</span><span class="sxs-lookup"><span data-stu-id="8f6c1-107">Remarks</span></span>  
 <span data-ttu-id="8f6c1-108">如果已設定攔截器的位，當遇到指定的攔截程式碼類型時，分檔器就會完成。</span><span class="sxs-lookup"><span data-stu-id="8f6c1-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="8f6c1-109">如果清除此位，將會略過攔截程式碼。</span><span class="sxs-lookup"><span data-stu-id="8f6c1-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="8f6c1-110">`SetInterceptMask` 方法可能與[ICorDebugStepper：： SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) （從使用者的觀點來看）發生未預期的互動。</span><span class="sxs-lookup"><span data-stu-id="8f6c1-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="8f6c1-111">例如，如果類別初始化程式碼中唯一可見的（亦即非內部）部分缺少對應資訊，而且未設定 STOP_NO_MAPPING_INFO （請參閱[ICorDebugStepper：： SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md)方法和 CorDebugUnmappedStop 列舉），則分檔器將不會跳過類別初始化。</span><span class="sxs-lookup"><span data-stu-id="8f6c1-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="8f6c1-112">根據預設，只會使用 `CorDebugIntercept` 列舉的 INTERCEPT_NONE 值。</span><span class="sxs-lookup"><span data-stu-id="8f6c1-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f6c1-113">需求</span><span class="sxs-lookup"><span data-stu-id="8f6c1-113">Requirements</span></span>  
 <span data-ttu-id="8f6c1-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f6c1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f6c1-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8f6c1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f6c1-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f6c1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f6c1-117">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f6c1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
