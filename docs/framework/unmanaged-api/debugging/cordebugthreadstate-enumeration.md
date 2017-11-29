---
title: "CorDebugThreadState 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugThreadState
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugThreadState
helpviewer_keywords: CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dc3555d0ecd85208688a4aae69aef7c6c88303b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="f25ee-102">CorDebugThreadState 列舉</span><span class="sxs-lookup"><span data-stu-id="f25ee-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="f25ee-103">指定要偵錯的執行緒狀態。</span><span class="sxs-lookup"><span data-stu-id="f25ee-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f25ee-104">語法</span><span class="sxs-lookup"><span data-stu-id="f25ee-104">Syntax</span></span>  
  
```  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="f25ee-105">成員</span><span class="sxs-lookup"><span data-stu-id="f25ee-105">Members</span></span>  
  
|<span data-ttu-id="f25ee-106">成員</span><span class="sxs-lookup"><span data-stu-id="f25ee-106">Member</span></span>|<span data-ttu-id="f25ee-107">說明</span><span class="sxs-lookup"><span data-stu-id="f25ee-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="f25ee-108">執行緒會執行自由，除非偵錯事件，就會發生。</span><span class="sxs-lookup"><span data-stu-id="f25ee-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="f25ee-109">無法執行執行緒。</span><span class="sxs-lookup"><span data-stu-id="f25ee-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f25ee-110">備註</span><span class="sxs-lookup"><span data-stu-id="f25ee-110">Remarks</span></span>  
 <span data-ttu-id="f25ee-111">偵錯工具會使用`CorDebugThreadState`列舉型別來控制執行緒的執行。</span><span class="sxs-lookup"><span data-stu-id="f25ee-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="f25ee-112">執行緒的狀態可以透過設定[icordebugthread:: Setdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)或[icordebugcontroller:: Setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="f25ee-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="f25ee-113">提供給回呼[裝載 API](../../../../docs/framework/unmanaged-api/hosting/index.md)啟用訊息幫浦，因此不需要中斷的狀態。</span><span class="sxs-lookup"><span data-stu-id="f25ee-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f25ee-114">需求</span><span class="sxs-lookup"><span data-stu-id="f25ee-114">Requirements</span></span>  
 <span data-ttu-id="f25ee-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f25ee-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f25ee-116">**標頭：** CorDebug.idl、 CorDegug.h</span><span class="sxs-lookup"><span data-stu-id="f25ee-116">**Header:** CorDebug.idl, CorDegug.h</span></span>  
  
 <span data-ttu-id="f25ee-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f25ee-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f25ee-118">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f25ee-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f25ee-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f25ee-119">See Also</span></span>  
 [<span data-ttu-id="f25ee-120">偵錯列舉</span><span class="sxs-lookup"><span data-stu-id="f25ee-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
