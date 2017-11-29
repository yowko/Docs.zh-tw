---
title: "ICorDebugStepper::SetInterceptMask 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.SetInterceptMask
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::SetInterceptMask
helpviewer_keywords:
- SetInterceptMask method [.NET Framework debugging]
- ICorDebugStepper::SetInterceptMask method [.NET Framework debugging]
ms.assetid: 6245e2ae-5cc2-43ff-8cc1-71953d12113a
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2a99b504c0ce58ca6b89153667598cd4c2c682d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugsteppersetinterceptmask-method"></a><span data-ttu-id="9120a-102">ICorDebugStepper::SetInterceptMask 方法</span><span class="sxs-lookup"><span data-stu-id="9120a-102">ICorDebugStepper::SetInterceptMask Method</span></span>
<span data-ttu-id="9120a-103">設定值，指定類型，也就逐步執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="9120a-103">Sets a value that specifies the types of code that are stepped into.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9120a-104">語法</span><span class="sxs-lookup"><span data-stu-id="9120a-104">Syntax</span></span>  
  
```  
HRESULT SetInterceptMask (  
    [in] CorDebugIntercept    mask  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9120a-105">參數</span><span class="sxs-lookup"><span data-stu-id="9120a-105">Parameters</span></span>  
 `mask`  
 <span data-ttu-id="9120a-106">[in]CorDebugIntercept 列舉，指定類型的程式碼值的組合。</span><span class="sxs-lookup"><span data-stu-id="9120a-106">[in] A combination of values of the CorDebugIntercept enumeration that specifies the types of code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9120a-107">備註</span><span class="sxs-lookup"><span data-stu-id="9120a-107">Remarks</span></span>  
 <span data-ttu-id="9120a-108">設定攔截器的位元，如果遇到攔截的程式碼的指定型別時，將會完成的 stepper。</span><span class="sxs-lookup"><span data-stu-id="9120a-108">If the bit for an interceptor is set, the stepper will complete when the given type of intercepting code is encountered.</span></span> <span data-ttu-id="9120a-109">如果位元會清除，攔截的程式碼將會略過。</span><span class="sxs-lookup"><span data-stu-id="9120a-109">If the bit is cleared, the intercepting code will be skipped.</span></span>  
  
 <span data-ttu-id="9120a-110">`SetInterceptMask`方法可能會發生未預期的互動[icordebugstepper:: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) （從使用者的觀點來看）。</span><span class="sxs-lookup"><span data-stu-id="9120a-110">The `SetInterceptMask` method may have unforeseen interactions with [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) (from the user's point of view).</span></span> <span data-ttu-id="9120a-111">比方說，如果唯一可見 (亦即，非內部) 一部分的類別初始化程式碼缺少對應的資訊，且未設定 STOP_NO_MAPPING_INFO (請參閱[icordebugstepper:: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)方法和CorDebugUnmappedStop 列舉型別），則 stepper 會不進入類別初始設定。</span><span class="sxs-lookup"><span data-stu-id="9120a-111">For example, if the only visible (that is, non-internal) portion of class initialization code lacks mapping information and STOP_NO_MAPPING_INFO isn't set (see the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method and the CorDebugUnmappedStop enumeration), the stepper will step over the class initialization.</span></span> <span data-ttu-id="9120a-112">根據預設，只有 INTERCEPT_NONE 的值`CorDebugIntercept`將用於列舉型別。</span><span class="sxs-lookup"><span data-stu-id="9120a-112">By default, only the INTERCEPT_NONE value of the `CorDebugIntercept` enumeration will be used.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9120a-113">需求</span><span class="sxs-lookup"><span data-stu-id="9120a-113">Requirements</span></span>  
 <span data-ttu-id="9120a-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9120a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9120a-115">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9120a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9120a-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9120a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9120a-117">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9120a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
