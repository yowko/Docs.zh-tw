---
title: ICorDebugController::SetAllThreadsDebugState 方法
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 280dc3f0271d7326fe4c22b813abebfd4d45c89e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59138472"
---
# <a name="icordebugcontrollersetallthreadsdebugstate-method"></a><span data-ttu-id="cb04b-102">ICorDebugController::SetAllThreadsDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="cb04b-102">ICorDebugController::SetAllThreadsDebugState Method</span></span>
<span data-ttu-id="cb04b-103">設定程序中的所有 managed 執行緒的偵錯狀態。</span><span class="sxs-lookup"><span data-stu-id="cb04b-103">Sets the debug state of all managed threads in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb04b-104">語法</span><span class="sxs-lookup"><span data-stu-id="cb04b-104">Syntax</span></span>  
  
```  
HRESULT SetAllThreadsDebugState (  
    [in] CorDebugThreadState  state,  
    [in] ICorDebugThread      *pExceptThisThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb04b-105">參數</span><span class="sxs-lookup"><span data-stu-id="cb04b-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="cb04b-106">[in]指定偵錯執行緒的狀態 」 CorDebugThreadState 」 列舉值。</span><span class="sxs-lookup"><span data-stu-id="cb04b-106">[in] A value of the "CorDebugThreadState" enumeration that specifies the state of the thread for debugging.</span></span>  
  
 `pExceptThisThread`  
 <span data-ttu-id="cb04b-107">[in]表示執行緒偵錯的 [狀態] 設定要免除"ICorDebugThread 」 物件的指標。</span><span class="sxs-lookup"><span data-stu-id="cb04b-107">[in] A pointer to an "ICorDebugThread" object that represents a thread to be exempted from the debug state setting.</span></span> <span data-ttu-id="cb04b-108">如果此值是 null，為免不套用的任何執行緒。</span><span class="sxs-lookup"><span data-stu-id="cb04b-108">If this value is null, no thread is exempted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb04b-109">備註</span><span class="sxs-lookup"><span data-stu-id="cb04b-109">Remarks</span></span>  
 <span data-ttu-id="cb04b-110">`SetAllThreadsDebugState`方法可能會影響執行緒不會顯示透過[EnumerateThreads 方法](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md)，因此已暫止的執行緒`SetAllThreadsDebugState`方法都要繼續使用`SetAllThreadsDebugState`方法。</span><span class="sxs-lookup"><span data-stu-id="cb04b-110">The `SetAllThreadsDebugState` method may affect threads that are not visible via [EnumerateThreads Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-enumeratethreads-method.md), so threads that were suspended with the `SetAllThreadsDebugState` method will need to be resumed with the `SetAllThreadsDebugState` method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb04b-111">需求</span><span class="sxs-lookup"><span data-stu-id="cb04b-111">Requirements</span></span>  
 <span data-ttu-id="cb04b-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="cb04b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb04b-113">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cb04b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cb04b-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cb04b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cb04b-115">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb04b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb04b-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb04b-116">See also</span></span>
