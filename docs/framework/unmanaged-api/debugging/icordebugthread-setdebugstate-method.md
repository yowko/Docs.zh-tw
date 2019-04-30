---
title: ICorDebugThread::SetDebugState 方法
ms.date: 03/30/2017
api_name:
- ICorDebugThread.SetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::SetDebugState
helpviewer_keywords:
- ICorDebugThread::SetDebugState method [.NET Framework debugging]
- SetDebugState method [.NET Framework debugging]
ms.assetid: 6382bdf6-d488-4952-b653-cb09b6e1c6c2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d29f5cefd22592fa8949ff5361109c09c0972b24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987138"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="e1dc7-102">ICorDebugThread::SetDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="e1dc7-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="e1dc7-103">設定描述這個 ICorDebugThread 偵錯狀態的旗標。</span><span class="sxs-lookup"><span data-stu-id="e1dc7-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1dc7-104">語法</span><span class="sxs-lookup"><span data-stu-id="e1dc7-104">Syntax</span></span>  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e1dc7-105">參數</span><span class="sxs-lookup"><span data-stu-id="e1dc7-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="e1dc7-106">[in]CorDebugThreadState 列舉值，指定這個執行緒的偵錯狀態的位元組合。</span><span class="sxs-lookup"><span data-stu-id="e1dc7-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1dc7-107">備註</span><span class="sxs-lookup"><span data-stu-id="e1dc7-107">Remarks</span></span>  
 <span data-ttu-id="e1dc7-108">`SetDebugState` 設定執行緒的目前偵錯狀態。</span><span class="sxs-lookup"><span data-stu-id="e1dc7-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="e1dc7-109">（如果此程序繼續執行，不實際的目前狀態 「 目前的偵錯狀態 」 表示偵錯狀態）。此設定的一般值為 THREAD_RUNNING。</span><span class="sxs-lookup"><span data-stu-id="e1dc7-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUNNING.</span></span> <span data-ttu-id="e1dc7-110">偵錯工具可能會影響偵錯執行緒的狀態。</span><span class="sxs-lookup"><span data-stu-id="e1dc7-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="e1dc7-111">偵錯狀態執行最後的持續發生，因此如果您想要保留的執行緒，透過多個 THREAD_SUSPENDed 會繼續，您可以設定一次，並之後不需要擔心它。</span><span class="sxs-lookup"><span data-stu-id="e1dc7-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="e1dc7-112">暫停執行緒，並繼續處理序可能會導致死結，但它通常是不可能。</span><span class="sxs-lookup"><span data-stu-id="e1dc7-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="e1dc7-113">這是內建的品質的執行緒和處理序，而且是依據設計。</span><span class="sxs-lookup"><span data-stu-id="e1dc7-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="e1dc7-114">偵錯工具以非同步方式可以中斷和繼續執行緒，以破除死結。</span><span class="sxs-lookup"><span data-stu-id="e1dc7-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="e1dc7-115">如果執行緒的使用者狀態包含 USER_UNSAFE_POINT，執行緒可能會封鎖在記憶體回收 (GC)。</span><span class="sxs-lookup"><span data-stu-id="e1dc7-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="e1dc7-116">這表示暫止的執行緒具有較高機率的而導致死結。</span><span class="sxs-lookup"><span data-stu-id="e1dc7-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="e1dc7-117">這可能不會影響偵錯事件已排入佇列。</span><span class="sxs-lookup"><span data-stu-id="e1dc7-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="e1dc7-118">因此在偵錯工具應該清空整個事件佇列 (藉由呼叫[icordebugcontroller:: Hasqueuedcallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) 暫停或繼續執行緒之前。</span><span class="sxs-lookup"><span data-stu-id="e1dc7-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="e1dc7-119">否則，它可能認為已暫止的執行緒上取得事件。</span><span class="sxs-lookup"><span data-stu-id="e1dc7-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1dc7-120">需求</span><span class="sxs-lookup"><span data-stu-id="e1dc7-120">Requirements</span></span>  
 <span data-ttu-id="e1dc7-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e1dc7-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1dc7-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1dc7-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1dc7-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1dc7-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1dc7-124">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1dc7-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
