---
title: ICorDebugStepper::IsActive 方法
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4166b63e0bb0ae276c48abb961e381809cc9792
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471416"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="2fd31-102">ICorDebugStepper::IsActive 方法</span><span class="sxs-lookup"><span data-stu-id="2fd31-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="2fd31-103">取得值，指出此 ICorDebugStepper 目前是否正在執行的步驟。</span><span class="sxs-lookup"><span data-stu-id="2fd31-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fd31-104">語法</span><span class="sxs-lookup"><span data-stu-id="2fd31-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fd31-105">參數</span><span class="sxs-lookup"><span data-stu-id="2fd31-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="2fd31-106">[out]會傳回`true`步進目前正在執行的步驟; 否則會傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="2fd31-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2fd31-107">備註</span><span class="sxs-lookup"><span data-stu-id="2fd31-107">Remarks</span></span>  
 <span data-ttu-id="2fd31-108">任何步驟動作維持作用，直到偵錯工具收到[icordebugmanagedcallback:: Stepcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)呼叫，這會自動停用步進。</span><span class="sxs-lookup"><span data-stu-id="2fd31-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="2fd31-109">步進可能也會停用不當藉由呼叫[icordebugstepper:: Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)在回呼之前條件為止。</span><span class="sxs-lookup"><span data-stu-id="2fd31-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fd31-110">需求</span><span class="sxs-lookup"><span data-stu-id="2fd31-110">Requirements</span></span>  
 <span data-ttu-id="2fd31-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2fd31-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fd31-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2fd31-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2fd31-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2fd31-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2fd31-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fd31-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
