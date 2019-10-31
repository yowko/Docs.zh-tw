---
title: CorDebugUserState 列舉
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
ms.openlocfilehash: d0394d511197c8d0aaa366ce7b791216a3d226bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120196"
---
# <a name="cordebuguserstate-enumeration"></a><span data-ttu-id="ba797-102">CorDebugUserState 列舉</span><span class="sxs-lookup"><span data-stu-id="ba797-102">CorDebugUserState Enumeration</span></span>
<span data-ttu-id="ba797-103">指出執行緒的使用者狀態。</span><span class="sxs-lookup"><span data-stu-id="ba797-103">Indicates the user state of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba797-104">語法</span><span class="sxs-lookup"><span data-stu-id="ba797-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a><span data-ttu-id="ba797-105">Members</span><span class="sxs-lookup"><span data-stu-id="ba797-105">Members</span></span>  
  
|<span data-ttu-id="ba797-106">值</span><span class="sxs-lookup"><span data-stu-id="ba797-106">Value</span></span>|<span data-ttu-id="ba797-107">描述</span><span class="sxs-lookup"><span data-stu-id="ba797-107">Description</span></span>|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|<span data-ttu-id="ba797-108">已要求執行緒終止。</span><span class="sxs-lookup"><span data-stu-id="ba797-108">A termination of the thread has been requested.</span></span>|  
|`USER_SUSPEND_REQUESTED`|<span data-ttu-id="ba797-109">已要求暫停執行緒。</span><span class="sxs-lookup"><span data-stu-id="ba797-109">A suspension of the thread has been requested.</span></span>|  
|`USER_BACKGROUND`|<span data-ttu-id="ba797-110">執行緒正在背景中執行。</span><span class="sxs-lookup"><span data-stu-id="ba797-110">The thread is running in the background.</span></span>|  
|`USER_UNSTARTED`|<span data-ttu-id="ba797-111">執行緒尚未開始執行。</span><span class="sxs-lookup"><span data-stu-id="ba797-111">The thread has not started executing.</span></span>|  
|`USER_STOPPED`|<span data-ttu-id="ba797-112">執行緒已經終止。</span><span class="sxs-lookup"><span data-stu-id="ba797-112">The thread has been terminated.</span></span>|  
|`USER_WAIT_SLEEP_JOIN`|<span data-ttu-id="ba797-113">執行緒正在等候另一個執行緒完成工作。</span><span class="sxs-lookup"><span data-stu-id="ba797-113">The thread is waiting for another thread to complete a task.</span></span>|  
|`USER_SUSPENDED`|<span data-ttu-id="ba797-114">執行緒已暫止。</span><span class="sxs-lookup"><span data-stu-id="ba797-114">The thread has been suspended.</span></span>|  
|`USER_UNSAFE_POINT`|<span data-ttu-id="ba797-115">執行緒在不安全的點。</span><span class="sxs-lookup"><span data-stu-id="ba797-115">The thread is at an unsafe point.</span></span> <span data-ttu-id="ba797-116">也就是說，執行緒是在執行的某個點上，它可能會封鎖垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="ba797-116">That is, the thread is at a point in execution where it may block garbage collection.</span></span><br /><br /> <span data-ttu-id="ba797-117">可能會從不安全的點分派 Debug 事件，但在不安全的點暫停執行緒，很可能會造成鎖死，直到執行緒恢復為止。</span><span class="sxs-lookup"><span data-stu-id="ba797-117">Debug events may be dispatched from unsafe points, but suspending a thread at an unsafe point  will very likely cause a deadlock until the thread is resumed.</span></span> <span data-ttu-id="ba797-118">安全和不安全的點取決於及時（JIT）和垃圾收集的執行。</span><span class="sxs-lookup"><span data-stu-id="ba797-118">The safe and unsafe points are determined by the just-in-time (JIT) and garbage collection implementation.</span></span>|  
|`USER_THREADPOOL`|<span data-ttu-id="ba797-119">執行緒來自執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="ba797-119">The thread is from the thread pool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba797-120">備註</span><span class="sxs-lookup"><span data-stu-id="ba797-120">Remarks</span></span>  
 <span data-ttu-id="ba797-121">執行緒的使用者狀態就是執行緒在偵錯工具檢查時所擁有的狀態。</span><span class="sxs-lookup"><span data-stu-id="ba797-121">The user state of a thread is the state that the thread has when the debugger examines it.</span></span> <span data-ttu-id="ba797-122">執行緒可以有使用者狀態的組合。</span><span class="sxs-lookup"><span data-stu-id="ba797-122">A thread may have a combination of user states.</span></span>  
  
 <span data-ttu-id="ba797-123">使用[ICorDebugThread：： GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)方法來取出執行緒的使用者狀態。</span><span class="sxs-lookup"><span data-stu-id="ba797-123">Use the [ICorDebugThread::GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) method to retrieve a thread's user state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba797-124">需求</span><span class="sxs-lookup"><span data-stu-id="ba797-124">Requirements</span></span>  
 <span data-ttu-id="ba797-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ba797-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba797-126">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba797-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba797-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba797-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba797-128">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba797-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba797-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="ba797-129">See also</span></span>

- [<span data-ttu-id="ba797-130">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="ba797-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
