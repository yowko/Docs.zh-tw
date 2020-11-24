---
title: ICorProfilerCallback5 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback5
helpviewer_keywords:
- ICorProfilerCallback5 interface [.NET Framework profiling]
ms.assetid: 61d2e9ef-5f1f-4771-8847-239616e35d84
topic_type:
- apiref
ms.openlocfilehash: 8e94aebc489fff1c81593e54b17c471e7228d810
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689286"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="f726d-102">ICorProfilerCallback5 介面</span><span class="sxs-lookup"><span data-stu-id="f726d-102">ICorProfilerCallback5 Interface</span></span>

<span data-ttu-id="f726d-103">當搭配使用 [ICorProfilerCallback：： RootReferences](icorprofilercallback-rootreferences-method.md) 或 [ICorProfilerCallback2：： RootReferences2](icorprofilercallback2-rootreferences2-method.md) 方法搭配 [ICorProfilerCallback：： ObjectReferences](icorprofilercallback-objectreferences-method.md) 和 [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) 方法時，補充資訊以協助 profiler 識別即時物件的完整關閉。</span><span class="sxs-lookup"><span data-stu-id="f726d-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="f726d-104">`ICorProfilerCallback5` 必須由 Managed 記憶體分析工具實作，以訂閱與相依性控制代碼相關的通知。</span><span class="sxs-lookup"><span data-stu-id="f726d-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f726d-105">備註</span><span class="sxs-lookup"><span data-stu-id="f726d-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f726d-106">方法</span><span class="sxs-lookup"><span data-stu-id="f726d-106">Methods</span></span>  
  
|<span data-ttu-id="f726d-107">方法</span><span class="sxs-lookup"><span data-stu-id="f726d-107">Method</span></span>|<span data-ttu-id="f726d-108">描述</span><span class="sxs-lookup"><span data-stu-id="f726d-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f726d-109">ConditionalWeakTableElementReferences 方法</span><span class="sxs-lookup"><span data-stu-id="f726d-109">ConditionalWeakTableElementReferences Method</span></span>](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="f726d-110">識別那些根目錄透過直接成員欄位參考以及透過 `ConditionalWeakTable` 相依性來參考之物件的可轉移結束。</span><span class="sxs-lookup"><span data-stu-id="f726d-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f726d-111">需求</span><span class="sxs-lookup"><span data-stu-id="f726d-111">Requirements</span></span>  

 <span data-ttu-id="f726d-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f726d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f726d-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f726d-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f726d-114">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f726d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f726d-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f726d-115">See also</span></span>

- [<span data-ttu-id="f726d-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="f726d-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="f726d-117">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="f726d-117">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
