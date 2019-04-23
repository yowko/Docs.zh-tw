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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 724db8c5c8dbb5bf3ff8bc7202a60397180b7b38
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59183387"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="8b4ad-102">ICorDebugController::Stop 方法</span><span class="sxs-lookup"><span data-stu-id="8b4ad-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="8b4ad-103">在此程序中執行 managed 程式碼的所有執行緒上執行合作式的停駐點。</span><span class="sxs-lookup"><span data-stu-id="8b4ad-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b4ad-104">語法</span><span class="sxs-lookup"><span data-stu-id="8b4ad-104">Syntax</span></span>  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b4ad-105">參數</span><span class="sxs-lookup"><span data-stu-id="8b4ad-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="8b4ad-106">未使用。</span><span class="sxs-lookup"><span data-stu-id="8b4ad-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8b4ad-107">備註</span><span class="sxs-lookup"><span data-stu-id="8b4ad-107">Remarks</span></span>  
 <span data-ttu-id="8b4ad-108">`Stop` 處理序中，會執行合作式停止執行的所有執行緒上受管理程式碼。</span><span class="sxs-lookup"><span data-stu-id="8b4ad-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="8b4ad-109">僅限 managed 偵錯工作階段期間，未受管理的執行緒可能會繼續執行 （但會被封鎖，嘗試呼叫 managed 程式碼時）。</span><span class="sxs-lookup"><span data-stu-id="8b4ad-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="8b4ad-110">在 interop 偵錯工作階段中，也將停止未受管理的執行緒。</span><span class="sxs-lookup"><span data-stu-id="8b4ad-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="8b4ad-111">`dwTimeoutIgnored`目前會忽略並視為無限 (-1) 值。</span><span class="sxs-lookup"><span data-stu-id="8b4ad-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="8b4ad-112">如果由於死結之故，失敗的合作式的停駐點，所有執行緒都會都暫停，並傳回 E_TIMEOUT。</span><span class="sxs-lookup"><span data-stu-id="8b4ad-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8b4ad-113">`Stop` 是偵錯 API 中只同步的方法。</span><span class="sxs-lookup"><span data-stu-id="8b4ad-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="8b4ad-114">當`Stop`傳回 s_ok 時，此程序已停止。</span><span class="sxs-lookup"><span data-stu-id="8b4ad-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="8b4ad-115">通知停駐點的接聽程式會不提供任何回呼。</span><span class="sxs-lookup"><span data-stu-id="8b4ad-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="8b4ad-116">偵錯工具必須呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)允許繼續執行的程序。</span><span class="sxs-lookup"><span data-stu-id="8b4ad-116">The debugger must call [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="8b4ad-117">偵錯工具會維持停止的計數器。</span><span class="sxs-lookup"><span data-stu-id="8b4ad-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="8b4ad-118">計數器歸零時，則控制器會繼續。</span><span class="sxs-lookup"><span data-stu-id="8b4ad-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="8b4ad-119">每次呼叫`Stop`或每個分派的回呼遞增的計數器。</span><span class="sxs-lookup"><span data-stu-id="8b4ad-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="8b4ad-120">每次呼叫`ICorDebugController::Continue`遞減計數器。</span><span class="sxs-lookup"><span data-stu-id="8b4ad-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b4ad-121">需求</span><span class="sxs-lookup"><span data-stu-id="8b4ad-121">Requirements</span></span>  
 <span data-ttu-id="8b4ad-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8b4ad-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b4ad-123">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b4ad-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b4ad-124">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b4ad-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b4ad-125">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b4ad-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b4ad-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b4ad-126">See also</span></span>
