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
ms.openlocfilehash: 15e18888e307a14c4396966afc0a623e1acba104
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332816"
---
# <a name="icordebugthreadsetdebugstate-method"></a><span data-ttu-id="d308e-102">ICorDebugThread::SetDebugState 方法</span><span class="sxs-lookup"><span data-stu-id="d308e-102">ICorDebugThread::SetDebugState Method</span></span>
<span data-ttu-id="d308e-103">設定描述此 ICorDebugThread 之偵錯工具狀態的旗標。</span><span class="sxs-lookup"><span data-stu-id="d308e-103">Sets flags that describe the debugging state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d308e-104">語法</span><span class="sxs-lookup"><span data-stu-id="d308e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebugState (  
    [in] CorDebugThreadState state  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d308e-105">參數</span><span class="sxs-lookup"><span data-stu-id="d308e-105">Parameters</span></span>  
 `state`  
 <span data-ttu-id="d308e-106">在CorDebugThreadState 列舉值的位元組合，指定此執行緒的偵錯工具狀態。</span><span class="sxs-lookup"><span data-stu-id="d308e-106">[in] A bitwise combination of CorDebugThreadState enumeration values that specify the debugging state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d308e-107">備註</span><span class="sxs-lookup"><span data-stu-id="d308e-107">Remarks</span></span>  
 <span data-ttu-id="d308e-108">`SetDebugState` 會設定執行緒目前的「調試」狀態。</span><span class="sxs-lookup"><span data-stu-id="d308e-108">`SetDebugState` sets the current debug state of the thread.</span></span> <span data-ttu-id="d308e-109">（如果進程要繼續，則為「目前的偵錯工具狀態」，而非實際的目前狀態）。此的一般值為 THREAD_RUN。</span><span class="sxs-lookup"><span data-stu-id="d308e-109">(The "current debug state" represents the debug state if the process were to be continued, not the actual current state.) The normal value for this is THREAD_RUN.</span></span> <span data-ttu-id="d308e-110">只有偵錯工具才會影響執行緒的「偵測」狀態。</span><span class="sxs-lookup"><span data-stu-id="d308e-110">Only the debugger can affect the debug state of a thread.</span></span> <span data-ttu-id="d308e-111">Debug 狀態最後會繼續進行，因此如果您想要讓執行緒 THREAD_SUSPENDed 多次，您可以將它設定一次，之後就不需要擔心。</span><span class="sxs-lookup"><span data-stu-id="d308e-111">Debug states do last across continues, so if you want to keep a thread THREAD_SUSPENDed over multiple continues, you can set it once and thereafter not have to worry about it.</span></span> <span data-ttu-id="d308e-112">暫停執行緒並繼續處理可能會導致鎖死，不過通常不太可能發生。</span><span class="sxs-lookup"><span data-stu-id="d308e-112">Suspending threads and resuming the process can cause deadlocks, though it's usually unlikely.</span></span> <span data-ttu-id="d308e-113">這是執行緒和進程的內建品質，而且是依設計的。</span><span class="sxs-lookup"><span data-stu-id="d308e-113">This is an intrinsic quality of threads and processes and is by-design.</span></span> <span data-ttu-id="d308e-114">偵錯工具可以非同步方式中斷並繼續執行緒，以中斷鎖死。</span><span class="sxs-lookup"><span data-stu-id="d308e-114">A debugger can asynchronously break and resume the threads to break the deadlock.</span></span> <span data-ttu-id="d308e-115">如果執行緒的使用者狀態包含 USER_UNSAFE_POINT，則執行緒可能會封鎖垃圾收集（GC）。</span><span class="sxs-lookup"><span data-stu-id="d308e-115">If the thread's user state includes USER_UNSAFE_POINT, then the thread may block a garbage collection (GC).</span></span> <span data-ttu-id="d308e-116">這表示暫停的執行緒有更高的機率導致鎖死。</span><span class="sxs-lookup"><span data-stu-id="d308e-116">This means the suspended thread has a much higher chance of causing a deadlock.</span></span> <span data-ttu-id="d308e-117">這可能不會影響已排入佇列的 debug 事件。</span><span class="sxs-lookup"><span data-stu-id="d308e-117">This may not affect debug events already queued.</span></span> <span data-ttu-id="d308e-118">因此，偵錯工具應該在暫停或繼續執行緒之前，清空整個事件佇列（藉由呼叫[ICorDebugController：： HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)）。</span><span class="sxs-lookup"><span data-stu-id="d308e-118">Thus a debugger should drain the entire event queue (by calling [ICorDebugController::HasQueuedCallbacks](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-hasqueuedcallbacks-method.md)) before suspending or resuming threads.</span></span> <span data-ttu-id="d308e-119">否則，它可能會線上程上取得其認為已暫停的事件。</span><span class="sxs-lookup"><span data-stu-id="d308e-119">Else it may get events on a thread that it believes it has already suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d308e-120">需求</span><span class="sxs-lookup"><span data-stu-id="d308e-120">Requirements</span></span>  
 <span data-ttu-id="d308e-121">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d308e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d308e-122">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d308e-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d308e-123">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d308e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d308e-124">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d308e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
