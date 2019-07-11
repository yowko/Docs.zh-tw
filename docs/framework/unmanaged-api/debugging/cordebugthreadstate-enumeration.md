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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce252f5a4b5fbcdbbc7b70c8b1c829490f8f63e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739523"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="263ad-102">CorDebugThreadState 列舉</span><span class="sxs-lookup"><span data-stu-id="263ad-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="263ad-103">指定要偵錯的執行緒狀態。</span><span class="sxs-lookup"><span data-stu-id="263ad-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="263ad-104">語法</span><span class="sxs-lookup"><span data-stu-id="263ad-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="263ad-105">成員</span><span class="sxs-lookup"><span data-stu-id="263ad-105">Members</span></span>  
  
|<span data-ttu-id="263ad-106">成員</span><span class="sxs-lookup"><span data-stu-id="263ad-106">Member</span></span>|<span data-ttu-id="263ad-107">說明</span><span class="sxs-lookup"><span data-stu-id="263ad-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="263ad-108">除非偵錯事件，就會發生，則執行緒會執行免費。</span><span class="sxs-lookup"><span data-stu-id="263ad-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="263ad-109">無法執行執行緒。</span><span class="sxs-lookup"><span data-stu-id="263ad-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="263ad-110">備註</span><span class="sxs-lookup"><span data-stu-id="263ad-110">Remarks</span></span>  
 <span data-ttu-id="263ad-111">偵錯工具會使用`CorDebugThreadState`列舉來控制執行緒的執行。</span><span class="sxs-lookup"><span data-stu-id="263ad-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="263ad-112">可以透過設定執行緒的狀態[icordebugthread:: Setdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)或是[icordebugcontroller:: Setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="263ad-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="263ad-113">提供給回呼[裝載 API](../../../../docs/framework/unmanaged-api/hosting/index.md)啟用訊息幫浦，因此不需要中斷的狀態。</span><span class="sxs-lookup"><span data-stu-id="263ad-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="263ad-114">需求</span><span class="sxs-lookup"><span data-stu-id="263ad-114">Requirements</span></span>  
 <span data-ttu-id="263ad-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="263ad-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="263ad-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="263ad-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="263ad-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="263ad-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="263ad-118">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="263ad-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="263ad-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="263ad-119">See also</span></span>

- [<span data-ttu-id="263ad-120">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="263ad-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
