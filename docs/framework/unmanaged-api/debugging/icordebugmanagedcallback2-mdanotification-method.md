---
title: ICorDebugManagedCallback2::MDANotification 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.MDANotification
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::MDANotification
helpviewer_keywords:
- MDANotification method [.NET Framework debugging]
- ICorDebugManagedCallback2::MDANotification method [.NET Framework debugging]
ms.assetid: 93f79627-bd31-4f4f-b95d-46a032a52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90c805a5f1f1da990564034fc292562d5f933d71
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608085"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="8162f-102">ICorDebugManagedCallback2::MDANotification 方法</span><span class="sxs-lookup"><span data-stu-id="8162f-102">ICorDebugManagedCallback2::MDANotification Method</span></span>
<span data-ttu-id="8162f-103">提供執行程式碼發生在應用程式進行偵錯 managed 偵錯助理 (MDA) 的通知。</span><span class="sxs-lookup"><span data-stu-id="8162f-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8162f-104">語法</span><span class="sxs-lookup"><span data-stu-id="8162f-104">Syntax</span></span>  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8162f-105">參數</span><span class="sxs-lookup"><span data-stu-id="8162f-105">Parameters</span></span>  
 `pController`  
 <span data-ttu-id="8162f-106">[in]ICorDebugController 介面，公開程序或應用程式定義域發生 MDA 的指標。</span><span class="sxs-lookup"><span data-stu-id="8162f-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="8162f-107">雖然永遠可以查詢的介面，以決定偵錯工具不應建立任何假設該控制器是處理程序或應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="8162f-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="8162f-108">[in]ICorDebugThread 介面會公開 managed 偵錯事件發生所在的執行緒指標。</span><span class="sxs-lookup"><span data-stu-id="8162f-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="8162f-109">如果 MDA 發生 unmanaged 執行緒，值`pThread`將會是 null。</span><span class="sxs-lookup"><span data-stu-id="8162f-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="8162f-110">您必須取得作業系統 (OS) 執行緒識別碼，來自 MDA 物件本身。</span><span class="sxs-lookup"><span data-stu-id="8162f-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="8162f-111">[in]指標[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) MDA 資訊公開 （expose） 的介面。</span><span class="sxs-lookup"><span data-stu-id="8162f-111">[in] A pointer to an [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8162f-112">備註</span><span class="sxs-lookup"><span data-stu-id="8162f-112">Remarks</span></span>  
 <span data-ttu-id="8162f-113">MDA 是啟發式的警告，而且不需要任何明確的偵錯工具動作，但呼叫除外[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)以繼續執行應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="8162f-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="8162f-114">Mda 會引發以及哪些資料是在任何給定的 MDA，在任何時間點，可以判斷 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="8162f-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="8162f-115">因此，偵錯工具應該不會建置需要特定的 MDA 模式的任何功能。</span><span class="sxs-lookup"><span data-stu-id="8162f-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="8162f-116">Mda 可能已排入佇列，不久之後遇到 MDA 時，才引發。</span><span class="sxs-lookup"><span data-stu-id="8162f-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="8162f-117">如果執行階段必須等候，直到它到達安全點引發 MDA，而不是它遇到時引發之 MDA 的則會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="8162f-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="8162f-118">這也表示執行階段可能會引發 Mda 已排入佇列的回呼 （類似於 「 附加 」 事件作業） 的以一組數目。</span><span class="sxs-lookup"><span data-stu-id="8162f-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="8162f-119">偵錯工具應該釋放的參考`ICorDebugMDA`之後立即從傳回的執行個體`MDANotification`回呼，以允許 CLR 回收 MDA 所耗用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="8162f-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="8162f-120">釋放此執行個體可能會改善效能，如果引發許多 Mda。</span><span class="sxs-lookup"><span data-stu-id="8162f-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8162f-121">需求</span><span class="sxs-lookup"><span data-stu-id="8162f-121">Requirements</span></span>  
 <span data-ttu-id="8162f-122">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8162f-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8162f-123">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8162f-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8162f-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8162f-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8162f-125">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8162f-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8162f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8162f-126">See also</span></span>
- [<span data-ttu-id="8162f-127">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="8162f-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="8162f-128">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="8162f-128">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="8162f-129">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="8162f-129">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
