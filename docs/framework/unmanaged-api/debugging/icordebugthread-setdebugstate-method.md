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
ms.openlocfilehash: ada120b9cb4100bfadff83d96e0226f911958bf7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420761"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="4d153-102">ICorDebugThread::SetDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="4d153-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="4d153-103">設定旗標，敘述此 ICorDebugThread 偵錯狀態。</span><span class="sxs-lookup"><span data-stu-id="4d153-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d153-104">語法</span><span class="sxs-lookup"><span data-stu-id="4d153-104">Syntax</span></span>  
  
```  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d153-105">參數</span><span class="sxs-lookup"><span data-stu-id="4d153-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="4d153-106">[in]CorDebugThreadState 列舉值，指定這個執行緒的偵錯狀態的位元組合。</span><span class="sxs-lookup"><span data-stu-id="4d153-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d153-107">備註</span><span class="sxs-lookup"><span data-stu-id="4d153-107">Remarks</span></span>  
 <span data-ttu-id="4d153-108">`SetDebugState` 設定執行緒的目前偵錯狀態。</span><span class="sxs-lookup"><span data-stu-id="4d153-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="4d153-109">（如果處理程序繼續進行，不實際的目前狀態 「 目前的偵錯狀態 」 表示偵錯狀態）。這一般值為 THREAD_RUNNING。</span><span class="sxs-lookup"><span data-stu-id="4d153-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUNNING.</span></span> <span data-ttu-id="4d153-110">偵錯工具可能會影響執行緒的偵錯狀態。</span><span class="sxs-lookup"><span data-stu-id="4d153-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="4d153-111">偵錯狀態執行上一次透過持續發生，所以如果您想要保留的執行緒，透過多個 THREAD_SUSPENDed 會繼續，您可以設定一次並之後不需要擔心。</span><span class="sxs-lookup"><span data-stu-id="4d153-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="4d153-112">暫止執行緒，並繼續處理序可能會造成死結，它通常不太可能也一樣。</span><span class="sxs-lookup"><span data-stu-id="4d153-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="4d153-113">這是內建的品質的執行緒和處理序，而且是依設計。</span><span class="sxs-lookup"><span data-stu-id="4d153-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="4d153-114">偵錯工具以非同步方式可以中斷和繼續執行緒，以破除死結。</span><span class="sxs-lookup"><span data-stu-id="4d153-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="4d153-115">如果執行緒的使用者狀態包含 USER_UNSAFE_POINT，執行緒可能會封鎖在記憶體回收 (GC)。</span><span class="sxs-lookup"><span data-stu-id="4d153-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="4d153-116">這表示在暫停的執行緒具有較高機率造成死結。</span><span class="sxs-lookup"><span data-stu-id="4d153-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="4d153-117">這可能會影響偵錯事件已排入佇列。</span><span class="sxs-lookup"><span data-stu-id="4d153-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="4d153-118">因此偵錯工具應該清空整個事件佇列 (藉由呼叫[icordebugcontroller:: Hasqueuedcallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) 暫停或繼續執行緒之前。</span><span class="sxs-lookup"><span data-stu-id="4d153-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="4d153-119">否則可能會有事件它認為已經暫止的執行緒上。</span><span class="sxs-lookup"><span data-stu-id="4d153-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d153-120">需求</span><span class="sxs-lookup"><span data-stu-id="4d153-120">Requirements</span></span>  
 <span data-ttu-id="4d153-121">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d153-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d153-122">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d153-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d153-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d153-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d153-124">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d153-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
