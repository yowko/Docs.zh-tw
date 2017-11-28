---
title: "ICorDebugStepper::IsActive 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugStepper.IsActive
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 25e4b59c59ee4340c14da22143f49c645e1dcc7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugstepperisactive-method"></a><span data-ttu-id="d2e02-102">ICorDebugStepper::IsActive 方法</span><span class="sxs-lookup"><span data-stu-id="d2e02-102">ICorDebugStepper::IsActive Method</span></span>
<span data-ttu-id="d2e02-103">取得值，指出是否此 ICorDebugStepper 目前正在執行的步驟。</span><span class="sxs-lookup"><span data-stu-id="d2e02-103">Gets a value that indicates whether this ICorDebugStepper is currently executing a step.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2e02-104">語法</span><span class="sxs-lookup"><span data-stu-id="d2e02-104">Syntax</span></span>  
  
```  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d2e02-105">參數</span><span class="sxs-lookup"><span data-stu-id="d2e02-105">Parameters</span></span>  
 `pbActive`  
 <span data-ttu-id="d2e02-106">[out]傳回`true`如果 stepper 正在執行一個步驟中; 否則傳回`false`。</span><span class="sxs-lookup"><span data-stu-id="d2e02-106">[out] Returns `true` if the stepper is currently executing a step; otherwise, returns `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2e02-107">備註</span><span class="sxs-lookup"><span data-stu-id="d2e02-107">Remarks</span></span>  
 <span data-ttu-id="d2e02-108">任何步驟動作維持作用，直到接收偵錯工具[icordebugmanagedcallback:: Stepcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)呼叫時，它會自動停用 stepper。</span><span class="sxs-lookup"><span data-stu-id="d2e02-108">Any step action remains active until the debugger receives a [ICorDebugManagedCallback::StepComplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) call, which automatically deactivates the stepper.</span></span> <span data-ttu-id="d2e02-109">Stepper 可能會一併被停用不當藉由呼叫[icordebugstepper:: Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)在回呼之前條件為止。</span><span class="sxs-lookup"><span data-stu-id="d2e02-109">A stepper may also be deactivated prematurely by calling [ICorDebugStepper::Deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) before the callback condition is reached.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2e02-110">需求</span><span class="sxs-lookup"><span data-stu-id="d2e02-110">Requirements</span></span>  
 <span data-ttu-id="d2e02-111">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d2e02-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2e02-112">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2e02-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2e02-113">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2e02-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2e02-114">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2e02-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
