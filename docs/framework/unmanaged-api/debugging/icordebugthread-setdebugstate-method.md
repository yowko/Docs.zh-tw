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
ms.openlocfilehash: e28d37e4477862ff2ebeeb05ea5f5386e157cd83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678710"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="963bb-102">ICorDebugThread::SetDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="963bb-102">ICorDebugThread::SetDebugState Method</span></span>

<span data-ttu-id="963bb-103">設定旗標，描述此 ICorDebugThread 的偵錯工具狀態。</span><span class="sxs-lookup"><span data-stu-id="963bb-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="963bb-104">語法</span><span class="sxs-lookup"><span data-stu-id="963bb-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="963bb-105">參數</span><span class="sxs-lookup"><span data-stu-id="963bb-105">Parameters</span></span>  

 `state`  
 <span data-ttu-id="963bb-106">在CorDebugThreadState 列舉值的位元組合，指定此執行緒的偵錯工具狀態。</span><span class="sxs-lookup"><span data-stu-id="963bb-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="963bb-107">備註</span><span class="sxs-lookup"><span data-stu-id="963bb-107">Remarks</span></span>  

 <span data-ttu-id="963bb-108">`SetDebugState` 設定執行緒目前的偵錯工具狀態。</span><span class="sxs-lookup"><span data-stu-id="963bb-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="963bb-109"> (「目前的偵錯工具狀態」表示進程即將繼續，而非實際的目前狀態時的「偵測」狀態。 ) 這個的一般值是 THREAD_RUN。</span><span class="sxs-lookup"><span data-stu-id="963bb-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUN.</span></span> <span data-ttu-id="963bb-110">只有偵錯工具會影響執行緒的偵錯工具狀態。</span><span class="sxs-lookup"><span data-stu-id="963bb-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="963bb-111">調試狀態最後會繼續執行，因此如果您想要讓執行緒 THREAD_SUSPENDed 超過多個作業，您可以將它設定為一次，之後就不必擔心。</span><span class="sxs-lookup"><span data-stu-id="963bb-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="963bb-112">擱置執行緒和繼續進程可能會造成鎖死，但通常不太可能發生。</span><span class="sxs-lookup"><span data-stu-id="963bb-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="963bb-113">這是執行緒和進程的內建品質，而且是設計的。</span><span class="sxs-lookup"><span data-stu-id="963bb-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="963bb-114">偵錯工具可以非同步地中斷和繼續執行緒，以中斷鎖死。</span><span class="sxs-lookup"><span data-stu-id="963bb-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="963bb-115">如果執行緒的使用者狀態包含 USER_UNSAFE_POINT，則執行緒可能會封鎖垃圾收集 (GC) 。</span><span class="sxs-lookup"><span data-stu-id="963bb-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="963bb-116">這表示暫停的執行緒有更高的機率造成鎖死。</span><span class="sxs-lookup"><span data-stu-id="963bb-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="963bb-117">這可能不會影響已排入佇列的 debug 事件。</span><span class="sxs-lookup"><span data-stu-id="963bb-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="963bb-118">因此，偵錯工具應該在暫止或繼續執行緒之前呼叫 [ICorDebugController：： HasQueuedCallbacks](icordebugcontroller-hasqueuedcallbacks-method.md)) ，以清空整個事件佇列 (。</span><span class="sxs-lookup"><span data-stu-id="963bb-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="963bb-119">否則，它可能會在已暫停的執行緒上取得事件。</span><span class="sxs-lookup"><span data-stu-id="963bb-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="963bb-120">需求</span><span class="sxs-lookup"><span data-stu-id="963bb-120">Requirements</span></span>  

 <span data-ttu-id="963bb-121">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="963bb-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="963bb-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="963bb-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="963bb-123">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="963bb-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="963bb-124">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="963bb-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
