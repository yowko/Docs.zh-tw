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
ms.openlocfilehash: a1f4964c89aa3b658c57946d4b5a0327797118f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728702"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="4d39a-102">ICorDebugHeapValue3 介面</span><span class="sxs-lookup"><span data-stu-id="4d39a-102">ICorDebugHeapValue3 Interface</span></span>

<span data-ttu-id="4d39a-103">公開物件的監視器鎖定屬性。</span><span class="sxs-lookup"><span data-stu-id="4d39a-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="4d39a-104">這個介面會擴充 ICorDebugHeapValue 和 ICorDebugHeapValue2 介面。</span><span class="sxs-lookup"><span data-stu-id="4d39a-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d39a-105">方法</span><span class="sxs-lookup"><span data-stu-id="4d39a-105">Methods</span></span>  
  
|<span data-ttu-id="4d39a-106">方法</span><span class="sxs-lookup"><span data-stu-id="4d39a-106">Method</span></span>|<span data-ttu-id="4d39a-107">描述</span><span class="sxs-lookup"><span data-stu-id="4d39a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d39a-108">GetThreadOwningMonitorLock 方法</span><span class="sxs-lookup"><span data-stu-id="4d39a-108">GetThreadOwningMonitorLock Method</span></span>](icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="4d39a-109">傳回在這個物件上擁有監視器鎖定的 managed 執行緒。</span><span class="sxs-lookup"><span data-stu-id="4d39a-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="4d39a-110">GetMonitorEventWaitList 方法</span><span class="sxs-lookup"><span data-stu-id="4d39a-110">GetMonitorEventWaitList Method</span></span>](icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="4d39a-111">提供已排序的執行緒清單，這些執行緒會排入與監視器鎖定相關聯的事件上。</span><span class="sxs-lookup"><span data-stu-id="4d39a-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d39a-112">備註</span><span class="sxs-lookup"><span data-stu-id="4d39a-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d39a-113">這個介面不支援跨電腦或跨處理序的遠端呼叫。</span><span class="sxs-lookup"><span data-stu-id="4d39a-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d39a-114">需求</span><span class="sxs-lookup"><span data-stu-id="4d39a-114">Requirements</span></span>  

 <span data-ttu-id="4d39a-115">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4d39a-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d39a-116">**標頭：** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d39a-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d39a-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d39a-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d39a-118">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d39a-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d39a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4d39a-119">See also</span></span>

- [<span data-ttu-id="4d39a-120">偵錯介面</span><span class="sxs-lookup"><span data-stu-id="4d39a-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4d39a-121">偵錯</span><span class="sxs-lookup"><span data-stu-id="4d39a-121">Debugging</span></span>](index.md)
