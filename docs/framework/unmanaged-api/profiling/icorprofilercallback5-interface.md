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
ms.openlocfilehash: 7981e7d2d2a4588e56d3c30d0ede2d003fdcd32e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865021"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="9244a-102">ICorProfilerCallback5 介面</span><span class="sxs-lookup"><span data-stu-id="9244a-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="9244a-103">當搭配[ICorProfilerCallback：： RootReferences](icorprofilercallback-rootreferences-method.md)或[ICorProfilerCallback2：： RootReferences2](icorprofilercallback2-rootreferences2-method.md)方法與[ICorProfilerCallback：： ObjectReferences](icorprofilercallback-objectreferences-method.md)和[ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md)方法一起使用時，可協助 profiler 識別即時物件的完整關閉。</span><span class="sxs-lookup"><span data-stu-id="9244a-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="9244a-104">`ICorProfilerCallback5` 必須由 Managed 記憶體分析工具實作，以訂閱與相依性控制代碼相關的通知。</span><span class="sxs-lookup"><span data-stu-id="9244a-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9244a-105">備註</span><span class="sxs-lookup"><span data-stu-id="9244a-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9244a-106">方法</span><span class="sxs-lookup"><span data-stu-id="9244a-106">Methods</span></span>  
  
|<span data-ttu-id="9244a-107">方法</span><span class="sxs-lookup"><span data-stu-id="9244a-107">Method</span></span>|<span data-ttu-id="9244a-108">描述</span><span class="sxs-lookup"><span data-stu-id="9244a-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9244a-109">ConditionalWeakTableElementReferences 方法</span><span class="sxs-lookup"><span data-stu-id="9244a-109">ConditionalWeakTableElementReferences Method</span></span>](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="9244a-110">識別那些根目錄透過直接成員欄位參考以及透過 `ConditionalWeakTable` 相依性來參考之物件的可轉移結束。</span><span class="sxs-lookup"><span data-stu-id="9244a-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9244a-111">需求</span><span class="sxs-lookup"><span data-stu-id="9244a-111">Requirements</span></span>  
 <span data-ttu-id="9244a-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9244a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9244a-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9244a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9244a-114">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9244a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9244a-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="9244a-115">See also</span></span>

- [<span data-ttu-id="9244a-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="9244a-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="9244a-117">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="9244a-117">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
