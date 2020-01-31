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
ms.openlocfilehash: 703f454f7ed1d2a959b761726f433db22cb73b01
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791780"
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="c6be2-102">ICorDebugStepper::IsActive 方法</span><span class="sxs-lookup"><span data-stu-id="c6be2-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="c6be2-103">取得值，指出這個 ICorDebugStepper 目前是否正在執行步驟。</span><span class="sxs-lookup"><span data-stu-id="c6be2-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6be2-104">語法</span><span class="sxs-lookup"><span data-stu-id="c6be2-104">Syntax</span></span>  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6be2-105">參數</span><span class="sxs-lookup"><span data-stu-id="c6be2-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="c6be2-106">脫銷如果分檔器目前正在執行步驟，則傳回 `true`;否則，會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="c6be2-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6be2-107">備註</span><span class="sxs-lookup"><span data-stu-id="c6be2-107">Remarks</span></span>  
 <span data-ttu-id="c6be2-108">任何步驟動作都會維持作用中狀態，直到偵錯工具收到[ICorDebugManagedCallback：： StepComplete](icordebugmanagedcallback-stepcomplete-method.md)呼叫，這會自動停用分檔器。</span><span class="sxs-lookup"><span data-stu-id="c6be2-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="c6be2-109">在達到回呼條件之前，也可以藉由呼叫[ICorDebugStepper：:D eactivate](icordebugstepper-deactivate-method.md) ，提前停用分檔器。</span><span class="sxs-lookup"><span data-stu-id="c6be2-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6be2-110">需求</span><span class="sxs-lookup"><span data-stu-id="c6be2-110">Requirements</span></span>  
 <span data-ttu-id="c6be2-111">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c6be2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6be2-112">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6be2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6be2-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6be2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6be2-114">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6be2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
