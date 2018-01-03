---
title: "CorDebugUserState 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugUserState
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugUserState
helpviewer_keywords: CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 57fd9df27b1911c90bd11712b67e6e64588c2b5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cordebuguserstate-enumeration"></a><span data-ttu-id="a7ebe-102">CorDebugUserState 列舉</span><span class="sxs-lookup"><span data-stu-id="a7ebe-102">CorDebugUserState Enumeration</span></span>
<span data-ttu-id="a7ebe-103">指出執行緒的使用者狀態。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-103">Indicates the user state of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7ebe-104">語法</span><span class="sxs-lookup"><span data-stu-id="a7ebe-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a7ebe-105">成員</span><span class="sxs-lookup"><span data-stu-id="a7ebe-105">Members</span></span>  
  
|<span data-ttu-id="a7ebe-106">值</span><span class="sxs-lookup"><span data-stu-id="a7ebe-106">Value</span></span>|<span data-ttu-id="a7ebe-107">描述</span><span class="sxs-lookup"><span data-stu-id="a7ebe-107">Description</span></span>|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|<span data-ttu-id="a7ebe-108">已要求終止執行緒。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-108">A termination of the thread has been requested.</span></span>|  
|`USER_SUSPEND_REQUESTED`|<span data-ttu-id="a7ebe-109">已要求暫止執行緒。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-109">A suspension of the thread has been requested.</span></span>|  
|`USER_BACKGROUND`|<span data-ttu-id="a7ebe-110">執行緒在背景中執行。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-110">The thread is running in the background.</span></span>|  
|`USER_UNSTARTED`|<span data-ttu-id="a7ebe-111">執行緒尚未啟動執行。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-111">The thread has not started executing.</span></span>|  
|`USER_STOPPED`|<span data-ttu-id="a7ebe-112">執行緒已經終止。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-112">The thread has been terminated.</span></span>|  
|`USER_WAIT_SLEEP_JOIN`|<span data-ttu-id="a7ebe-113">執行緒正在等候另一個執行緒完成工作。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-113">The thread is waiting for another thread to complete a task.</span></span>|  
|`USER_SUSPENDED`|<span data-ttu-id="a7ebe-114">執行緒已經暫止。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-114">The thread has been suspended.</span></span>|  
|`USER_UNSAFE_POINT`|<span data-ttu-id="a7ebe-115">執行緒是不安全的點。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-115">The thread is at an unsafe point.</span></span> <span data-ttu-id="a7ebe-116">也就是的執行緒已在執行中的點，它可能會封鎖記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-116">That is, the thread is at a point in execution where it may block garbage collection.</span></span><br /><br /> <span data-ttu-id="a7ebe-117">偵錯事件可能會分派從 unsafe 點，但在不安全點暫停執行緒極可能會造成死結執行緒繼續執行之前。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-117">Debug events may be dispatched from unsafe points, but suspending a thread at an unsafe point  will very likely cause a deadlock until the thread is resumed.</span></span> <span data-ttu-id="a7ebe-118">安全和不安全的點是由在 just-in-time (JIT) 和記憶體回收集合實作決定。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-118">The safe and unsafe points are determined by the just-in-time (JIT) and garbage collection implementation.</span></span>|  
|`USER_THREADPOOL`|<span data-ttu-id="a7ebe-119">執行緒是從執行緒集區。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-119">The thread is from the thread pool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7ebe-120">備註</span><span class="sxs-lookup"><span data-stu-id="a7ebe-120">Remarks</span></span>  
 <span data-ttu-id="a7ebe-121">使用者狀態是執行緒的執行緒時偵錯工具會檢查它所擁有的狀態。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-121">The user state of a thread is the state that the thread has when the debugger examines it.</span></span> <span data-ttu-id="a7ebe-122">執行緒可能會有使用者狀態的組合。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-122">A thread may have a combination of user states.</span></span>  
  
 <span data-ttu-id="a7ebe-123">使用[icordebugthread:: Getuserstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)方法來擷取執行緒的使用者狀態。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-123">Use the [ICorDebugThread::GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) method to retrieve a thread's user state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7ebe-124">需求</span><span class="sxs-lookup"><span data-stu-id="a7ebe-124">Requirements</span></span>  
 <span data-ttu-id="a7ebe-125">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a7ebe-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7ebe-126">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7ebe-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7ebe-127">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7ebe-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7ebe-128">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7ebe-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7ebe-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="a7ebe-129">See Also</span></span>  
 [<span data-ttu-id="a7ebe-130">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="a7ebe-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
