---
title: "ICorDebugController::SetAllThreadsDebugState 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugController.SetAllThreadsDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::SetAllThreadsDebugState
helpviewer_keywords:
- SetAllThreadsDebugState method [.NET Framework debugging]
- ICorDebugController::SetAllThreadsDebugState method [.NET Framework debugging]
ms.assetid: bdda4bd7-4743-4d58-a22b-8067e967db95
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b8c9904c3c86e405660dcafe9963fe05049524b4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="ddb17-102">ICorDebugController::SetAllThreadsDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="ddb17-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="ddb17-103">設定偵錯狀態的所有 managed 執行緒處理序中。</span><span class="sxs-lookup"><span data-stu-id="ddb17-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddb17-104">語法</span><span class="sxs-lookup"><span data-stu-id="ddb17-104">Syntax</span></span>  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ddb17-105">參數</span><span class="sxs-lookup"><span data-stu-id="ddb17-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="ddb17-106">[in]指定偵錯執行緒的狀態 」 CorDebugThreadState 」 列舉值。</span><span class="sxs-lookup"><span data-stu-id="ddb17-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="ddb17-107">[in]表示執行緒豁免的偵錯狀態設定 」 ICorDebugThread 」 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="ddb17-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="ddb17-108">如果這個值是 null，就會不豁免任何執行緒。</span><span class="sxs-lookup"><span data-stu-id="ddb17-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddb17-109">備註</span><span class="sxs-lookup"><span data-stu-id="ddb17-109">Remarks</span></span>  
 <span data-ttu-id="ddb17-110">`SetAllThreadsDebugState`方法可能會影響執行緒不會顯示透過[EnumerateThreads 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)，因此執行緒被暫止與`SetAllThreadsDebugState`方法必須使用繼續`SetAllThreadsDebugState`方法。</span><span class="sxs-lookup"><span data-stu-id="ddb17-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddb17-111">需求</span><span class="sxs-lookup"><span data-stu-id="ddb17-111">Requirements</span></span>  
 <span data-ttu-id="ddb17-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ddb17-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddb17-113">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ddb17-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ddb17-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddb17-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ddb17-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ddb17-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddb17-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="ddb17-116">See Also</span></span>  
 
