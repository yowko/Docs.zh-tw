---
title: ICorDebugHeapValue3 介面
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3
helpviewer_keywords:
- ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60d3b22d8dc140bf16af7f59781d5ed103dafbf4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765475"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="84e10-102">ICorDebugHeapValue3 介面</span><span class="sxs-lookup"><span data-stu-id="84e10-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="84e10-103">公開物件的監視器鎖定屬性。</span><span class="sxs-lookup"><span data-stu-id="84e10-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="84e10-104">這個介面會擴充 ICorDebugHeapValue 和 ICorDebugHeapValue2 介面。</span><span class="sxs-lookup"><span data-stu-id="84e10-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="84e10-105">方法</span><span class="sxs-lookup"><span data-stu-id="84e10-105">Methods</span></span>  
  
|<span data-ttu-id="84e10-106">方法</span><span class="sxs-lookup"><span data-stu-id="84e10-106">Method</span></span>|<span data-ttu-id="84e10-107">描述</span><span class="sxs-lookup"><span data-stu-id="84e10-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="84e10-108">GetThreadOwningMonitorLock 方法</span><span class="sxs-lookup"><span data-stu-id="84e10-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="84e10-109">傳回擁有此物件的監視器鎖定的 managed 的執行緒。</span><span class="sxs-lookup"><span data-stu-id="84e10-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="84e10-110">GetMonitorEventWaitList 方法</span><span class="sxs-lookup"><span data-stu-id="84e10-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="84e10-111">提供的監視器鎖定相關聯的事件的執行緒已排入佇列的已排序的清單。</span><span class="sxs-lookup"><span data-stu-id="84e10-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84e10-112">備註</span><span class="sxs-lookup"><span data-stu-id="84e10-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84e10-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="84e10-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84e10-114">需求</span><span class="sxs-lookup"><span data-stu-id="84e10-114">Requirements</span></span>  
 <span data-ttu-id="84e10-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="84e10-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84e10-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84e10-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84e10-117">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84e10-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84e10-118">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84e10-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84e10-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84e10-119">See also</span></span>

- [<span data-ttu-id="84e10-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="84e10-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="84e10-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="84e10-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
