---
title: "ICorDebugController::Stop 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugController.Stop
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7a8699a54814b37cc03404b72330812f3eb2b2f9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="dcd63-102">ICorDebugController::Stop 方法</span><span class="sxs-lookup"><span data-stu-id="dcd63-102">ICorDebugController::Stop Method</span></span>
<span data-ttu-id="dcd63-103">在 managed 程式碼執行處理序中的所有執行緒上執行合作式停止。</span><span class="sxs-lookup"><span data-stu-id="dcd63-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcd63-104">語法</span><span class="sxs-lookup"><span data-stu-id="dcd63-104">Syntax</span></span>  
  
```  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dcd63-105">參數</span><span class="sxs-lookup"><span data-stu-id="dcd63-105">Parameters</span></span>  
 `dwTimeoutIgnored`  
 <span data-ttu-id="dcd63-106">未使用。</span><span class="sxs-lookup"><span data-stu-id="dcd63-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcd63-107">備註</span><span class="sxs-lookup"><span data-stu-id="dcd63-107">Remarks</span></span>  
 <span data-ttu-id="dcd63-108">`Stop`會執行合作式停止執行的所有執行緒在 managed 程式碼中處理程序。</span><span class="sxs-lookup"><span data-stu-id="dcd63-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="dcd63-109">僅限 managed 偵錯工作階段，unmanaged 的執行緒可能會繼續執行 （但是將會封鎖嘗試呼叫 managed 程式碼時）。</span><span class="sxs-lookup"><span data-stu-id="dcd63-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="dcd63-110">在 interop 偵錯工作階段，unmanaged 的執行緒也將會停止。</span><span class="sxs-lookup"><span data-stu-id="dcd63-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="dcd63-111">`dwTimeoutIgnored`值目前已忽略，並且視為 INFINITE (-1)。</span><span class="sxs-lookup"><span data-stu-id="dcd63-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="dcd63-112">由於死結合作式的停駐點時，所有執行緒都會都暫停，並傳回 E_TIMEOUT。</span><span class="sxs-lookup"><span data-stu-id="dcd63-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dcd63-113">`Stop`是偵錯 API 中的只同步方法。</span><span class="sxs-lookup"><span data-stu-id="dcd63-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="dcd63-114">當`Stop`傳回 S_OK 時，處理程序已停止。</span><span class="sxs-lookup"><span data-stu-id="dcd63-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="dcd63-115">通知停駐點的接聽程式會不提供任何回呼。</span><span class="sxs-lookup"><span data-stu-id="dcd63-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="dcd63-116">偵錯工具必須呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)允許繼續執行的程序。</span><span class="sxs-lookup"><span data-stu-id="dcd63-116">The debugger must call [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="dcd63-117">偵錯工具會維持停止計數器。</span><span class="sxs-lookup"><span data-stu-id="dcd63-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="dcd63-118">當計數器為零，控制器會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="dcd63-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="dcd63-119">每次呼叫`Stop`或每個分派的回呼會遞增計數器。</span><span class="sxs-lookup"><span data-stu-id="dcd63-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="dcd63-120">每次呼叫`ICorDebugController::Continue`遞減的計數器。</span><span class="sxs-lookup"><span data-stu-id="dcd63-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcd63-121">需求</span><span class="sxs-lookup"><span data-stu-id="dcd63-121">Requirements</span></span>  
 <span data-ttu-id="dcd63-122">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dcd63-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcd63-123">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dcd63-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dcd63-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dcd63-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcd63-125">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcd63-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcd63-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="dcd63-126">See Also</span></span>  
 
