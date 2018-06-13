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
ms.openlocfilehash: 64b09c173e2f66d4c650083cc12f8a0ac2c92007
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33417224"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="06af9-102">ICorDebugManagedCallback2::MDANotification 方法</span><span class="sxs-lookup"><span data-stu-id="06af9-102">ICorDebugManagedCallback2::MDANotification Method</span></span>
<span data-ttu-id="06af9-103">提供執行程式碼發現正在偵錯的應用程式中 managed 偵錯助理 (MDA) 的通知。</span><span class="sxs-lookup"><span data-stu-id="06af9-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06af9-104">語法</span><span class="sxs-lookup"><span data-stu-id="06af9-104">Syntax</span></span>  
  
```  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06af9-105">參數</span><span class="sxs-lookup"><span data-stu-id="06af9-105">Parameters</span></span>  
 `pController`  
 <span data-ttu-id="06af9-106">[in]ICorDebugController 介面，公開程序或應用程式定義域發生 MDA 的指標。</span><span class="sxs-lookup"><span data-stu-id="06af9-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="06af9-107">雖然永遠可以查詢做出判斷介面的偵錯工具不應做任何假設控制器是處理程序或應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="06af9-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="06af9-108">[in]ICorDebugThread 介面公開 managed 偵錯事件發生所在的執行緒的指標。</span><span class="sxs-lookup"><span data-stu-id="06af9-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="06af9-109">如果 MDA 發生 unmanaged 執行緒，之中的值`pThread`將會是 null。</span><span class="sxs-lookup"><span data-stu-id="06af9-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="06af9-110">您必須從 MDA 物件本身，以取得作業系統 (OS) 執行緒 ID。</span><span class="sxs-lookup"><span data-stu-id="06af9-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="06af9-111">[in]指標[ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)公開 MDA 資訊的介面。</span><span class="sxs-lookup"><span data-stu-id="06af9-111">[in] A pointer to an [ICorDebugMDA](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06af9-112">備註</span><span class="sxs-lookup"><span data-stu-id="06af9-112">Remarks</span></span>  
 <span data-ttu-id="06af9-113">MDA 是啟發式的警告，而且不需要任何明確的偵錯工具動作，除了呼叫[icordebugcontroller:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)以繼續執行應用程式進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="06af9-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="06af9-114">Mda 會引發以及哪些資料是在任何給定的 MDA，在任何時間點，可以判斷 common language runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="06af9-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="06af9-115">因此，偵錯工具應該不會建置需要特定 MDA 模式的任何功能。</span><span class="sxs-lookup"><span data-stu-id="06af9-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="06af9-116">Mda 會進入佇列並不久之後遇到的 MDA 時引發。</span><span class="sxs-lookup"><span data-stu-id="06af9-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="06af9-117">如果執行階段必須等候，直到達到安全點引發而非引發 MDA，當它遇到的 MDA，則會發生此問題。</span><span class="sxs-lookup"><span data-stu-id="06af9-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="06af9-118">這也表示執行階段可能會引發 Mda 集中單一佇列的回呼 （類似於 「 附加 」 事件作業） 的數目。</span><span class="sxs-lookup"><span data-stu-id="06af9-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="06af9-119">偵錯工具就會釋放參考`ICorDebugMDA`之後立即從傳回的執行個體`MDANotification`回呼，讓 CLR 回收 MDA 所耗用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="06af9-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="06af9-120">釋放此執行個體可改善效能，當引發許多 Mda。</span><span class="sxs-lookup"><span data-stu-id="06af9-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06af9-121">需求</span><span class="sxs-lookup"><span data-stu-id="06af9-121">Requirements</span></span>  
 <span data-ttu-id="06af9-122">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="06af9-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06af9-123">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06af9-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06af9-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06af9-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06af9-125">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06af9-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06af9-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06af9-126">See Also</span></span>  
 [<span data-ttu-id="06af9-127">診斷 Managed 偵錯助理的錯誤</span><span class="sxs-lookup"><span data-stu-id="06af9-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="06af9-128">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="06af9-128">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [<span data-ttu-id="06af9-129">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="06af9-129">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
