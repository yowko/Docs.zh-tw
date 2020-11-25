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
ms.openlocfilehash: 814bf87039ef57056f13994af1b873f8f57c7804
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95718211"
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="b6345-102">ICorDebugStepper::SetInterceptMask 方法</span><span class="sxs-lookup"><span data-stu-id="b6345-102">ICorDebugStepper::SetInterceptMask Method</span></span>

<span data-ttu-id="b6345-103">設定值，這個值會指定逐步執行的程式碼類型。</span><span class="sxs-lookup"><span data-stu-id="b6345-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6345-104">語法</span><span class="sxs-lookup"><span data-stu-id="b6345-104">Syntax</span></span>  
  
```cpp  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6345-105">參數</span><span class="sxs-lookup"><span data-stu-id="b6345-105">Parameters</span></span>  

 `mask`  
 <span data-ttu-id="b6345-106">在CorDebugIntercept 列舉值的組合，可指定程式碼的類型。</span><span class="sxs-lookup"><span data-stu-id="b6345-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6345-107">備註</span><span class="sxs-lookup"><span data-stu-id="b6345-107">Remarks</span></span>  

 <span data-ttu-id="b6345-108">如果設定攔截器的位，則在遇到指定的攔截程式碼類型時，就會完成分檔器。</span><span class="sxs-lookup"><span data-stu-id="b6345-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="b6345-109">如果已清除此位，則會略過攔截程式碼。</span><span class="sxs-lookup"><span data-stu-id="b6345-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="b6345-110">`SetInterceptMask`從使用者的觀點來看，方法可能與[ICorDebugStepper：： SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (之間的互動) 。</span><span class="sxs-lookup"><span data-stu-id="b6345-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="b6345-111">例如，如果唯一可見的 (（類別初始化程式碼的非內部) 部分缺少對應資訊，而且 STOP_NO_MAPPING_INFO 未設定 (請參閱 [ICorDebugStepper：： SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) 方法和 CorDebugUnmappedStop 列舉) ，則分檔器將不會跳過類別初始化。</span><span class="sxs-lookup"><span data-stu-id="b6345-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="b6345-112">依預設，只 `CorDebugIntercept` 會使用列舉的 INTERCEPT_NONE 值。</span><span class="sxs-lookup"><span data-stu-id="b6345-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6345-113">需求</span><span class="sxs-lookup"><span data-stu-id="b6345-113">Requirements</span></span>  

 <span data-ttu-id="b6345-114">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b6345-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6345-115">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6345-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6345-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6345-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6345-117">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6345-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
