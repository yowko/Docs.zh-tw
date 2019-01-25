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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6481d647541af40b956c38a76d281ccb84e7c7f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602542"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="490c5-102">ICorProfilerCallback5 介面</span><span class="sxs-lookup"><span data-stu-id="490c5-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="490c5-103">為了識別實際物件的完整結束時搭配分析工具的資訊做補充[icorprofilercallback:: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)或[ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)方法並搭配[icorprofilercallback:: Objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)並[ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)方法。</span><span class="sxs-lookup"><span data-stu-id="490c5-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="490c5-104">`ICorProfilerCallback5` 必須由 Managed 記憶體分析工具實作，以訂閱與相依性控制代碼相關的通知。</span><span class="sxs-lookup"><span data-stu-id="490c5-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="490c5-105">備註</span><span class="sxs-lookup"><span data-stu-id="490c5-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="490c5-106">方法</span><span class="sxs-lookup"><span data-stu-id="490c5-106">Methods</span></span>  
  
|<span data-ttu-id="490c5-107">方法</span><span class="sxs-lookup"><span data-stu-id="490c5-107">Method</span></span>|<span data-ttu-id="490c5-108">描述</span><span class="sxs-lookup"><span data-stu-id="490c5-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="490c5-109">ConditionalWeakTableElementReferences 方法</span><span class="sxs-lookup"><span data-stu-id="490c5-109">ConditionalWeakTableElementReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="490c5-110">識別那些根目錄透過直接成員欄位參考以及透過 `ConditionalWeakTable` 相依性來參考之物件的可轉移結束。</span><span class="sxs-lookup"><span data-stu-id="490c5-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="490c5-111">需求</span><span class="sxs-lookup"><span data-stu-id="490c5-111">Requirements</span></span>  
 <span data-ttu-id="490c5-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="490c5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="490c5-113">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="490c5-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="490c5-114">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="490c5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="490c5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="490c5-115">See also</span></span>
- [<span data-ttu-id="490c5-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="490c5-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="490c5-117">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="490c5-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
