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
ms.openlocfilehash: 11cc6e4108a2064a8a9fcefa760bf3c3411d63fb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679854"
---
# <a name="icordebugcontrollerstop-method"></a><span data-ttu-id="66942-102">ICorDebugController::Stop 方法</span><span class="sxs-lookup"><span data-stu-id="66942-102">ICorDebugController::Stop Method</span></span>

<span data-ttu-id="66942-103">在進程中執行 managed 程式碼的所有線程上執行合作式停止。</span><span class="sxs-lookup"><span data-stu-id="66942-103">Performs a cooperative stop on all threads that are running managed code in the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66942-104">語法</span><span class="sxs-lookup"><span data-stu-id="66942-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66942-105">參數</span><span class="sxs-lookup"><span data-stu-id="66942-105">Parameters</span></span>  

 `dwTimeoutIgnored`  
 <span data-ttu-id="66942-106">未使用。</span><span class="sxs-lookup"><span data-stu-id="66942-106">Not used.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66942-107">備註</span><span class="sxs-lookup"><span data-stu-id="66942-107">Remarks</span></span>  

 <span data-ttu-id="66942-108">`Stop` 在進程中執行 managed 程式碼的所有線程上執行合作式停止。</span><span class="sxs-lookup"><span data-stu-id="66942-108">`Stop` performs a cooperative stop on all threads running managed code in the process.</span></span> <span data-ttu-id="66942-109">在僅限 managed 的偵錯工具期間，非受控執行緒可能會繼續執行 (但在嘗試呼叫 managed 程式碼) 時將會遭到封鎖。</span><span class="sxs-lookup"><span data-stu-id="66942-109">During a managed-only debugging session, unmanaged threads may continue to run (but will be blocked when trying to call managed code).</span></span> <span data-ttu-id="66942-110">在 interop 偵錯工具期間，也會停止非受控執行緒。</span><span class="sxs-lookup"><span data-stu-id="66942-110">During an interop debugging session, unmanaged threads will also be stopped.</span></span> <span data-ttu-id="66942-111">`dwTimeoutIgnored`目前會忽略此值，並將其視為無限 (-1) 。</span><span class="sxs-lookup"><span data-stu-id="66942-111">The `dwTimeoutIgnored` value is currently ignored and treated as INFINITE (-1).</span></span> <span data-ttu-id="66942-112">如果合作性停止因鎖死而失敗，則會暫止所有線程，並傳回 E_TIMEOUT。</span><span class="sxs-lookup"><span data-stu-id="66942-112">If the cooperative stop fails due to a deadlock, all threads are suspended and E_TIMEOUT is returned.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="66942-113">`Stop` 是偵錯工具 API 中唯一的同步方法。</span><span class="sxs-lookup"><span data-stu-id="66942-113">`Stop` is the only synchronous method in the debugging API.</span></span> <span data-ttu-id="66942-114">當傳回 `Stop` S_OK 時，會停止處理常式。</span><span class="sxs-lookup"><span data-stu-id="66942-114">When `Stop` returns S_OK, the process is stopped.</span></span> <span data-ttu-id="66942-115">未提供回呼以通知接聽程式停止。</span><span class="sxs-lookup"><span data-stu-id="66942-115">No callback is given to notify listeners of the stop.</span></span> <span data-ttu-id="66942-116">偵錯工具必須呼叫 [ICorDebugController：： Continue](icordebugcontroller-continue-method.md) 以允許進程繼續執行。</span><span class="sxs-lookup"><span data-stu-id="66942-116">The debugger must call [ICorDebugController::Continue](icordebugcontroller-continue-method.md) to allow the process to resume.</span></span>  
  
 <span data-ttu-id="66942-117">偵錯工具會維護一個停止計數器。</span><span class="sxs-lookup"><span data-stu-id="66942-117">The debugger maintains a stop counter.</span></span> <span data-ttu-id="66942-118">當計數器移至零時，控制器就會繼續。</span><span class="sxs-lookup"><span data-stu-id="66942-118">When the counter goes to zero, the controller is resumed.</span></span> <span data-ttu-id="66942-119">每次呼叫 `Stop` 或每個分派的回呼都會遞增計數器。</span><span class="sxs-lookup"><span data-stu-id="66942-119">Each call to `Stop` or each dispatched callback increments the counter.</span></span> <span data-ttu-id="66942-120">每次呼叫以 `ICorDebugController::Continue` 遞減計數器。</span><span class="sxs-lookup"><span data-stu-id="66942-120">Each call to `ICorDebugController::Continue` decrements the counter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66942-121">需求</span><span class="sxs-lookup"><span data-stu-id="66942-121">Requirements</span></span>  

 <span data-ttu-id="66942-122">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="66942-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66942-123">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66942-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66942-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66942-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66942-125">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66942-125">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66942-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66942-126">See also</span></span>
