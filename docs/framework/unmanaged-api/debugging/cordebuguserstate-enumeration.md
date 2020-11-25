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
ms.openlocfilehash: 968874a46279b7eac651d45c3890429a326651b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726947"
---
# <a name="cordebuguserstate-enumeration"></a><span data-ttu-id="895b3-102">CorDebugUserState 列舉</span><span class="sxs-lookup"><span data-stu-id="895b3-102">CorDebugUserState Enumeration</span></span>

<span data-ttu-id="895b3-103">指出執行緒的使用者狀態。</span><span class="sxs-lookup"><span data-stu-id="895b3-103">Indicates the user state of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="895b3-104">語法</span><span class="sxs-lookup"><span data-stu-id="895b3-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="895b3-105">成員</span><span class="sxs-lookup"><span data-stu-id="895b3-105">Members</span></span>  
  
|<span data-ttu-id="895b3-106">值</span><span class="sxs-lookup"><span data-stu-id="895b3-106">Value</span></span>|<span data-ttu-id="895b3-107">描述</span><span class="sxs-lookup"><span data-stu-id="895b3-107">Description</span></span>|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|<span data-ttu-id="895b3-108">已要求執行緒終止。</span><span class="sxs-lookup"><span data-stu-id="895b3-108">A termination of the thread has been requested.</span></span>|  
|`USER_SUSPEND_REQUESTED`|<span data-ttu-id="895b3-109">已要求暫停執行緒。</span><span class="sxs-lookup"><span data-stu-id="895b3-109">A suspension of the thread has been requested.</span></span>|  
|`USER_BACKGROUND`|<span data-ttu-id="895b3-110">執行緒正在背景中執行。</span><span class="sxs-lookup"><span data-stu-id="895b3-110">The thread is running in the background.</span></span>|  
|`USER_UNSTARTED`|<span data-ttu-id="895b3-111">執行緒尚未開始執行。</span><span class="sxs-lookup"><span data-stu-id="895b3-111">The thread has not started executing.</span></span>|  
|`USER_STOPPED`|<span data-ttu-id="895b3-112">執行緒已經結束。</span><span class="sxs-lookup"><span data-stu-id="895b3-112">The thread has been terminated.</span></span>|  
|`USER_WAIT_SLEEP_JOIN`|<span data-ttu-id="895b3-113">執行緒正在等候另一個執行緒完成工作。</span><span class="sxs-lookup"><span data-stu-id="895b3-113">The thread is waiting for another thread to complete a task.</span></span>|  
|`USER_SUSPENDED`|<span data-ttu-id="895b3-114">執行緒已經暫止。</span><span class="sxs-lookup"><span data-stu-id="895b3-114">The thread has been suspended.</span></span>|  
|`USER_UNSAFE_POINT`|<span data-ttu-id="895b3-115">執行緒處於不安全的時間點。</span><span class="sxs-lookup"><span data-stu-id="895b3-115">The thread is at an unsafe point.</span></span> <span data-ttu-id="895b3-116">也就是說，執行緒是在執行的某個點上，它可能會封鎖垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="895b3-116">That is, the thread is at a point in execution where it may block garbage collection.</span></span><br /><br /> <span data-ttu-id="895b3-117">偵錯工具事件可能會從不安全的點分派，但在不安全的點暫停執行緒很可能會造成鎖死，直到執行緒繼續為止。</span><span class="sxs-lookup"><span data-stu-id="895b3-117">Debug events may be dispatched from unsafe points, but suspending a thread at an unsafe point  will very likely cause a deadlock until the thread is resumed.</span></span> <span data-ttu-id="895b3-118">安全且不安全的點取決於及時 (JIT) 和垃圾收集執行。</span><span class="sxs-lookup"><span data-stu-id="895b3-118">The safe and unsafe points are determined by the just-in-time (JIT) and garbage collection implementation.</span></span>|  
|`USER_THREADPOOL`|<span data-ttu-id="895b3-119">執行緒來自執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="895b3-119">The thread is from the thread pool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="895b3-120">備註</span><span class="sxs-lookup"><span data-stu-id="895b3-120">Remarks</span></span>  

 <span data-ttu-id="895b3-121">執行緒的使用者狀態是偵錯工具檢查時執行緒的狀態。</span><span class="sxs-lookup"><span data-stu-id="895b3-121">The user state of a thread is the state that the thread has when the debugger examines it.</span></span> <span data-ttu-id="895b3-122">執行緒可能會有使用者狀態的組合。</span><span class="sxs-lookup"><span data-stu-id="895b3-122">A thread may have a combination of user states.</span></span>  
  
 <span data-ttu-id="895b3-123">使用 [ICorDebugThread：： GetUserState](icordebugthread-getuserstate-method.md) 方法來取出執行緒的使用者狀態。</span><span class="sxs-lookup"><span data-stu-id="895b3-123">Use the [ICorDebugThread::GetUserState](icordebugthread-getuserstate-method.md) method to retrieve a thread's user state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="895b3-124">需求</span><span class="sxs-lookup"><span data-stu-id="895b3-124">Requirements</span></span>  

 <span data-ttu-id="895b3-125">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="895b3-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="895b3-126">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="895b3-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="895b3-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="895b3-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="895b3-128">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="895b3-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="895b3-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="895b3-129">See also</span></span>

- [<span data-ttu-id="895b3-130">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="895b3-130">Debugging Enumerations</span></span>](debugging-enumerations.md)
