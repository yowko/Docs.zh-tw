---
title: ICorDebugController::Stop 方法
ms.date: 03/30/2017
api_name:
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
ms.openlocfilehash: c8c6b40f7a9c63a577140209eed65436040addcb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125379"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="1ac02-102">ICorDebugController::Stop 方法</span><span class="sxs-lookup"><span data-stu-id="1ac02-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="1ac02-103">在進程中執行 managed 程式碼的所有線程上執行合作性停止。</span><span class="sxs-lookup"><span data-stu-id="1ac02-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ac02-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ac02-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1ac02-105">參數</span><span class="sxs-lookup"><span data-stu-id="1ac02-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="1ac02-106">未使用。</span><span class="sxs-lookup"><span data-stu-id="1ac02-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1ac02-107">備註</span><span class="sxs-lookup"><span data-stu-id="1ac02-107">Remarks</span></span>  
 <span data-ttu-id="1ac02-108">`Stop` 會在進程中執行 managed 程式碼的所有線程上執行合作的停止。</span><span class="sxs-lookup"><span data-stu-id="1ac02-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="1ac02-109">在僅限 managed 的偵錯工具期間，非受控執行緒可能會繼續執行（但在嘗試呼叫 managed 程式碼時將會遭到封鎖）。</span><span class="sxs-lookup"><span data-stu-id="1ac02-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="1ac02-110">在 interop 偵錯工具期間，非受控執行緒也會停止。</span><span class="sxs-lookup"><span data-stu-id="1ac02-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="1ac02-111">目前已忽略 `dwTimeoutIgnored` 值，並將其視為無限（-1）。</span><span class="sxs-lookup"><span data-stu-id="1ac02-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="1ac02-112">如果合作性停止因鎖死而失敗，則會暫止所有線程並傳回 E_TIMEOUT。</span><span class="sxs-lookup"><span data-stu-id="1ac02-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1ac02-113">`Stop` 是調試 API 中唯一的同步方法。</span><span class="sxs-lookup"><span data-stu-id="1ac02-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="1ac02-114">當 `Stop` 傳回 S_OK 時，進程就會停止。</span><span class="sxs-lookup"><span data-stu-id="1ac02-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="1ac02-115">未提供回呼以通知接聽程式停止。</span><span class="sxs-lookup"><span data-stu-id="1ac02-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="1ac02-116">偵錯工具必須呼叫[ICorDebugController：： Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) ，以允許進程繼續執行。</span><span class="sxs-lookup"><span data-stu-id="1ac02-116">The debugger must call [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="1ac02-117">偵錯工具會維護一個停止計數器。</span><span class="sxs-lookup"><span data-stu-id="1ac02-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="1ac02-118">當計數器變成零時，控制器就會繼續。</span><span class="sxs-lookup"><span data-stu-id="1ac02-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="1ac02-119">每次呼叫 `Stop` 或每個分派的回呼都會遞增計數器。</span><span class="sxs-lookup"><span data-stu-id="1ac02-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="1ac02-120">`ICorDebugController::Continue` 的每個呼叫都會遞減計數器。</span><span class="sxs-lookup"><span data-stu-id="1ac02-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1ac02-121">需求</span><span class="sxs-lookup"><span data-stu-id="1ac02-121">Requirements</span></span>  
 <span data-ttu-id="1ac02-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1ac02-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ac02-123">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1ac02-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1ac02-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1ac02-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ac02-125">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1ac02-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ac02-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="1ac02-126">See also</span></span>
