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
ms.openlocfilehash: 1a59d8bce6ae565687e7ed906f6c14332f0c5c71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416828"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="8519f-102">ICorDebugHeapValue3 介面</span><span class="sxs-lookup"><span data-stu-id="8519f-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="8519f-103">公開物件的監視器鎖定屬性。</span><span class="sxs-lookup"><span data-stu-id="8519f-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="8519f-104">這個介面會擴充的 ICorDebugHeapValue 和 ICorDebugHeapValue2 介面。</span><span class="sxs-lookup"><span data-stu-id="8519f-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8519f-105">方法</span><span class="sxs-lookup"><span data-stu-id="8519f-105">Methods</span></span>  
  
|<span data-ttu-id="8519f-106">方法</span><span class="sxs-lookup"><span data-stu-id="8519f-106">Method</span></span>|<span data-ttu-id="8519f-107">描述</span><span class="sxs-lookup"><span data-stu-id="8519f-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8519f-108">GetThreadOwningMonitorLock 方法</span><span class="sxs-lookup"><span data-stu-id="8519f-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="8519f-109">傳回擁有此物件的監視器鎖定的 managed 的執行緒。</span><span class="sxs-lookup"><span data-stu-id="8519f-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="8519f-110">GetMonitorEventWaitList 方法</span><span class="sxs-lookup"><span data-stu-id="8519f-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="8519f-111">提供與監視鎖定相關事件的執行緒已排入佇列的已排序的清單。</span><span class="sxs-lookup"><span data-stu-id="8519f-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8519f-112">備註</span><span class="sxs-lookup"><span data-stu-id="8519f-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8519f-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="8519f-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8519f-114">需求</span><span class="sxs-lookup"><span data-stu-id="8519f-114">Requirements</span></span>  
 <span data-ttu-id="8519f-115">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8519f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8519f-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8519f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8519f-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8519f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8519f-118">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8519f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8519f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8519f-119">See Also</span></span>  
 [<span data-ttu-id="8519f-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="8519f-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8519f-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="8519f-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
