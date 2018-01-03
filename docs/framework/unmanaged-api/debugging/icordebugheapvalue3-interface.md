---
title: "ICorDebugHeapValue3 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugHeapValue3
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugHeapValue3
helpviewer_keywords: ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c7110ea2e39411d65d70ea14992959cdddc1d3bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="7cfef-102">ICorDebugHeapValue3 介面</span><span class="sxs-lookup"><span data-stu-id="7cfef-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="7cfef-103">公開物件的監視器鎖定屬性。</span><span class="sxs-lookup"><span data-stu-id="7cfef-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="7cfef-104">這個介面會擴充的 ICorDebugHeapValue 和 ICorDebugHeapValue2 介面。</span><span class="sxs-lookup"><span data-stu-id="7cfef-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7cfef-105">方法</span><span class="sxs-lookup"><span data-stu-id="7cfef-105">Methods</span></span>  
  
|<span data-ttu-id="7cfef-106">方法</span><span class="sxs-lookup"><span data-stu-id="7cfef-106">Method</span></span>|<span data-ttu-id="7cfef-107">描述</span><span class="sxs-lookup"><span data-stu-id="7cfef-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7cfef-108">GetThreadOwningMonitorLock 方法</span><span class="sxs-lookup"><span data-stu-id="7cfef-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="7cfef-109">傳回擁有此物件的監視器鎖定的 managed 的執行緒。</span><span class="sxs-lookup"><span data-stu-id="7cfef-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="7cfef-110">GetMonitorEventWaitList 方法</span><span class="sxs-lookup"><span data-stu-id="7cfef-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="7cfef-111">提供與監視鎖定相關事件的執行緒已排入佇列的已排序的清單。</span><span class="sxs-lookup"><span data-stu-id="7cfef-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cfef-112">備註</span><span class="sxs-lookup"><span data-stu-id="7cfef-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7cfef-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="7cfef-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cfef-114">需求</span><span class="sxs-lookup"><span data-stu-id="7cfef-114">Requirements</span></span>  
 <span data-ttu-id="7cfef-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7cfef-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cfef-116">**標頭：** CorDebug.idl、 CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7cfef-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7cfef-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cfef-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7cfef-118">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7cfef-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cfef-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="7cfef-119">See Also</span></span>  
 [<span data-ttu-id="7cfef-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="7cfef-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7cfef-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="7cfef-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
