---
title: CorDebugThreadState 列舉
ms.date: 03/30/2017
api_name:
- CorDebugThreadState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugThreadState
helpviewer_keywords:
- CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type:
- apiref
ms.openlocfilehash: 1ff36e8ef6b7c02eea5b02bc22587bc3889df093
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133697"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="a326b-102">CorDebugThreadState 列舉</span><span class="sxs-lookup"><span data-stu-id="a326b-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="a326b-103">指定要偵錯的執行緒狀態。</span><span class="sxs-lookup"><span data-stu-id="a326b-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a326b-104">語法</span><span class="sxs-lookup"><span data-stu-id="a326b-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="a326b-105">Members</span><span class="sxs-lookup"><span data-stu-id="a326b-105">Members</span></span>  
  
|<span data-ttu-id="a326b-106">成員</span><span class="sxs-lookup"><span data-stu-id="a326b-106">Member</span></span>|<span data-ttu-id="a326b-107">描述</span><span class="sxs-lookup"><span data-stu-id="a326b-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="a326b-108">除非發生 debug 事件，否則執行緒會自由執行。</span><span class="sxs-lookup"><span data-stu-id="a326b-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="a326b-109">無法執行執行緒。</span><span class="sxs-lookup"><span data-stu-id="a326b-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a326b-110">備註</span><span class="sxs-lookup"><span data-stu-id="a326b-110">Remarks</span></span>  
 <span data-ttu-id="a326b-111">偵錯工具會使用 `CorDebugThreadState` 列舉來控制執行緒的執行。</span><span class="sxs-lookup"><span data-stu-id="a326b-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="a326b-112">您可以使用[ICorDebugThread：： SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)或[ICorDebugController：： SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)方法來設定執行緒的狀態。</span><span class="sxs-lookup"><span data-stu-id="a326b-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="a326b-113">提供給[裝載 API](../../../../docs/framework/unmanaged-api/hosting/index.md)的回呼可啟用訊息提取，因此不需要中斷的狀態。</span><span class="sxs-lookup"><span data-stu-id="a326b-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a326b-114">需求</span><span class="sxs-lookup"><span data-stu-id="a326b-114">Requirements</span></span>  
 <span data-ttu-id="a326b-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="a326b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a326b-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a326b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a326b-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a326b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a326b-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a326b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a326b-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="a326b-119">See also</span></span>

- [<span data-ttu-id="a326b-120">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="a326b-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
