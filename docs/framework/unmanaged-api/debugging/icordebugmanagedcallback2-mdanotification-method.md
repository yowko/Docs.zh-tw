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
ms.openlocfilehash: f850b3cd35fda8bd554b99e14553100008cb4eca
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208521"
---
# <a name="icordebugmanagedcallback2mdanotification-method"></a><span data-ttu-id="abe80-102">ICorDebugManagedCallback2::MDANotification 方法</span><span class="sxs-lookup"><span data-stu-id="abe80-102">ICorDebugManagedCallback2::MDANotification Method</span></span>
<span data-ttu-id="abe80-103">提供通知，指出程式碼執行在正在進行調試的應用程式中遇到受管理的調試助理（MDA）。</span><span class="sxs-lookup"><span data-stu-id="abe80-103">Provides notification that code execution has encountered a managed debugging assistant (MDA) in the application that is being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abe80-104">語法</span><span class="sxs-lookup"><span data-stu-id="abe80-104">Syntax</span></span>  
  
```cpp  
HRESULT MDANotification(  
    [in] ICorDebugController  *pController,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugMDA         *pMDA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="abe80-105">參數</span><span class="sxs-lookup"><span data-stu-id="abe80-105">Parameters</span></span>  
 `pController`  
 <span data-ttu-id="abe80-106">在ICorDebugController 介面的指標，它會公開發生 MDA 的進程或應用程式域。</span><span class="sxs-lookup"><span data-stu-id="abe80-106">[in] A pointer to an ICorDebugController interface that exposes the process or application domain in which the MDA occurred.</span></span>  
  
 <span data-ttu-id="abe80-107">偵錯工具不應該對控制器是否為進程或應用程式域進行任何假設，雖然它一定可以查詢介面來進行判斷。</span><span class="sxs-lookup"><span data-stu-id="abe80-107">A debugger should not make any assumptions about whether the controller is a process or an application domain, although it can always query the interface to make a determination.</span></span>  
  
 `pThread`  
 <span data-ttu-id="abe80-108">在ICorDebugThread 介面的指標，它會公開發生 debug 事件的 managed 執行緒。</span><span class="sxs-lookup"><span data-stu-id="abe80-108">[in] A pointer to an ICorDebugThread interface that exposes the managed thread on which the debug event occurred.</span></span>  
  
 <span data-ttu-id="abe80-109">如果 MDA 發生在未受管理的執行緒上，的值 `pThread` 將會是 null。</span><span class="sxs-lookup"><span data-stu-id="abe80-109">If the MDA occurred on an unmanaged thread, the value of `pThread` will be null.</span></span>  
  
 <span data-ttu-id="abe80-110">您必須從 MDA 物件本身取得作業系統（OS）執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="abe80-110">You must get the operating system (OS) thread ID from the MDA object itself.</span></span>  
  
 `pMDA`  
 <span data-ttu-id="abe80-111">在公開 MDA 資訊之[ICorDebugMDA](icordebugmda-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="abe80-111">[in] A pointer to an [ICorDebugMDA](icordebugmda-interface.md) interface that exposes the MDA information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="abe80-112">備註</span><span class="sxs-lookup"><span data-stu-id="abe80-112">Remarks</span></span>  
 <span data-ttu-id="abe80-113">MDA 是啟發式警告，而且不需要任何明確的偵錯工具動作，除非呼叫[ICorDebugController：： Continue 繼續](icordebugcontroller-continue-method.md)執行正在進行調試的應用程式。</span><span class="sxs-lookup"><span data-stu-id="abe80-113">An MDA is a heuristic warning and does not require any explicit debugger action except for calling [ICorDebugController::Continue](icordebugcontroller-continue-method.md) to resume execution of the application that is being debugged.</span></span>  
  
 <span data-ttu-id="abe80-114">Common language runtime （CLR）可以判斷哪些 Mda 會引發，而哪些資料會在任何指定的 MDA 中。</span><span class="sxs-lookup"><span data-stu-id="abe80-114">The common language runtime (CLR) can determine which MDAs are fired and which data is in any given MDA at any point.</span></span> <span data-ttu-id="abe80-115">因此，偵錯工具不應建立任何需要特定 MDA 模式的功能。</span><span class="sxs-lookup"><span data-stu-id="abe80-115">Therefore, debuggers should not build any functionality requiring specific MDA patterns.</span></span>  
  
 <span data-ttu-id="abe80-116">在遇到 MDA 之後，Mda 可能會排入佇列並很快引發。</span><span class="sxs-lookup"><span data-stu-id="abe80-116">MDAs may be queued and fired shortly after the MDA is encountered.</span></span> <span data-ttu-id="abe80-117">如果執行時間必須等到到達安全點才能引發 MDA，就會發生這種情況，而不是在遇到 MDA 時引發它。</span><span class="sxs-lookup"><span data-stu-id="abe80-117">This could happen if the runtime needs to wait until it reaches a safe point for firing the MDA, instead of firing the MDA when it encounters it.</span></span> <span data-ttu-id="abe80-118">這也表示執行時間可能會在一組排入佇列的回呼中引發數個 Mda （類似于「附加」事件操作）。</span><span class="sxs-lookup"><span data-stu-id="abe80-118">It also means that the runtime may fire a number of MDAs in a single set of queued callbacks (similar to an "attach" event operation).</span></span>  
  
 <span data-ttu-id="abe80-119">偵錯工具應該會在 `ICorDebugMDA` 從回呼傳回之後立即釋放對實例的參考 `MDANotification` ，以允許 CLR 回收 MDA 所耗用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="abe80-119">A debugger should release the reference to an `ICorDebugMDA` instance immediately after returning from the `MDANotification` callback, to allow the CLR to recycle the memory consumed by an MDA.</span></span> <span data-ttu-id="abe80-120">如果有許多 Mda 引發，發行實例可能會改善效能。</span><span class="sxs-lookup"><span data-stu-id="abe80-120">Releasing the instance may improve performance if many MDAs are firing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abe80-121">需求</span><span class="sxs-lookup"><span data-stu-id="abe80-121">Requirements</span></span>  
 <span data-ttu-id="abe80-122">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="abe80-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abe80-123">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abe80-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abe80-124">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abe80-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abe80-125">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abe80-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abe80-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="abe80-126">See also</span></span>

- [<span data-ttu-id="abe80-127">使用 Managed 偵錯助理診斷錯誤</span><span class="sxs-lookup"><span data-stu-id="abe80-127">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="abe80-128">ICorDebugManagedCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="abe80-128">ICorDebugManagedCallback2 Interface</span></span>](icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="abe80-129">ICorDebugManagedCallback 介面</span><span class="sxs-lookup"><span data-stu-id="abe80-129">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
