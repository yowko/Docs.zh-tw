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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c54b2af6e7a200db89bfd7335868a629d7a886fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61724092"
---
# <a name="cordebuguserstate-enumeration"></a><span data-ttu-id="d7711-102">CorDebugUserState 列舉</span><span class="sxs-lookup"><span data-stu-id="d7711-102">CorDebugUserState Enumeration</span></span>
<span data-ttu-id="d7711-103">指出執行緒的使用者狀態。</span><span class="sxs-lookup"><span data-stu-id="d7711-103">Indicates the user state of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7711-104">語法</span><span class="sxs-lookup"><span data-stu-id="d7711-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="d7711-105">成員</span><span class="sxs-lookup"><span data-stu-id="d7711-105">Members</span></span>  
  
|<span data-ttu-id="d7711-106">值</span><span class="sxs-lookup"><span data-stu-id="d7711-106">Value</span></span>|<span data-ttu-id="d7711-107">描述</span><span class="sxs-lookup"><span data-stu-id="d7711-107">Description</span></span>|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|<span data-ttu-id="d7711-108">已要求終止執行緒。</span><span class="sxs-lookup"><span data-stu-id="d7711-108">A termination of the thread has been requested.</span></span>|  
|`USER_SUSPEND_REQUESTED`|<span data-ttu-id="d7711-109">已要求暫止執行緒。</span><span class="sxs-lookup"><span data-stu-id="d7711-109">A suspension of the thread has been requested.</span></span>|  
|`USER_BACKGROUND`|<span data-ttu-id="d7711-110">執行緒在背景中執行。</span><span class="sxs-lookup"><span data-stu-id="d7711-110">The thread is running in the background.</span></span>|  
|`USER_UNSTARTED`|<span data-ttu-id="d7711-111">執行緒尚未開始執行。</span><span class="sxs-lookup"><span data-stu-id="d7711-111">The thread has not started executing.</span></span>|  
|`USER_STOPPED`|<span data-ttu-id="d7711-112">執行緒已經終止。</span><span class="sxs-lookup"><span data-stu-id="d7711-112">The thread has been terminated.</span></span>|  
|`USER_WAIT_SLEEP_JOIN`|<span data-ttu-id="d7711-113">執行緒正在等候另一個執行緒完成工作。</span><span class="sxs-lookup"><span data-stu-id="d7711-113">The thread is waiting for another thread to complete a task.</span></span>|  
|`USER_SUSPENDED`|<span data-ttu-id="d7711-114">已暫停的執行緒。</span><span class="sxs-lookup"><span data-stu-id="d7711-114">The thread has been suspended.</span></span>|  
|`USER_UNSAFE_POINT`|<span data-ttu-id="d7711-115">執行緒是在不安全的時間點。</span><span class="sxs-lookup"><span data-stu-id="d7711-115">The thread is at an unsafe point.</span></span> <span data-ttu-id="d7711-116">也就是執行緒是在執行中的某一點，它可能會封鎖記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="d7711-116">That is, the thread is at a point in execution where it may block garbage collection.</span></span><br /><br /> <span data-ttu-id="d7711-117">偵錯可能不安全的點，從分派事件，但在不安全點暫停執行緒極可能會造成死結，執行緒會繼續直到。</span><span class="sxs-lookup"><span data-stu-id="d7711-117">Debug events may be dispatched from unsafe points, but suspending a thread at an unsafe point  will very likely cause a deadlock until the thread is resumed.</span></span> <span data-ttu-id="d7711-118">安全和不安全點取決於在 just-in-time (JIT) 和記憶體回收集合實作。</span><span class="sxs-lookup"><span data-stu-id="d7711-118">The safe and unsafe points are determined by the just-in-time (JIT) and garbage collection implementation.</span></span>|  
|`USER_THREADPOOL`|<span data-ttu-id="d7711-119">執行緒是在執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="d7711-119">The thread is from the thread pool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7711-120">備註</span><span class="sxs-lookup"><span data-stu-id="d7711-120">Remarks</span></span>  
 <span data-ttu-id="d7711-121">使用者狀態是執行緒的執行緒有時偵錯工具會檢查它的狀態。</span><span class="sxs-lookup"><span data-stu-id="d7711-121">The user state of a thread is the state that the thread has when the debugger examines it.</span></span> <span data-ttu-id="d7711-122">執行緒可能會有使用者狀態的組合。</span><span class="sxs-lookup"><span data-stu-id="d7711-122">A thread may have a combination of user states.</span></span>  
  
 <span data-ttu-id="d7711-123">使用[icordebugthread:: Getuserstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)方法來擷取執行緒的使用者狀態。</span><span class="sxs-lookup"><span data-stu-id="d7711-123">Use the [ICorDebugThread::GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) method to retrieve a thread's user state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7711-124">需求</span><span class="sxs-lookup"><span data-stu-id="d7711-124">Requirements</span></span>  
 <span data-ttu-id="d7711-125">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7711-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7711-126">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7711-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7711-127">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7711-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7711-128">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7711-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7711-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7711-129">See also</span></span>

- [<span data-ttu-id="d7711-130">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="d7711-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
