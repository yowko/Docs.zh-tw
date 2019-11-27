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
ms.openlocfilehash: ce34d43091cdee0bca88f94711e49072fa4fd08c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430061"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="1bcd3-102">ICorProfilerCallback5 介面</span><span class="sxs-lookup"><span data-stu-id="1bcd3-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="1bcd3-103">當搭配[ICorProfilerCallback：： RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)或[ICorProfilerCallback2：： RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)方法與[ICorProfilerCallback：： ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)和[ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)方法一起使用時，可協助 profiler 識別即時物件的完整關閉。</span><span class="sxs-lookup"><span data-stu-id="1bcd3-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="1bcd3-104">`ICorProfilerCallback5` 必須由 managed 記憶體分析工具執行，才能訂閱與相依控制碼相關的通知。</span><span class="sxs-lookup"><span data-stu-id="1bcd3-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1bcd3-105">備註</span><span class="sxs-lookup"><span data-stu-id="1bcd3-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1bcd3-106">方法</span><span class="sxs-lookup"><span data-stu-id="1bcd3-106">Methods</span></span>  
  
|<span data-ttu-id="1bcd3-107">方法</span><span class="sxs-lookup"><span data-stu-id="1bcd3-107">Method</span></span>|<span data-ttu-id="1bcd3-108">描述</span><span class="sxs-lookup"><span data-stu-id="1bcd3-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1bcd3-109">ConditionalWeakTableElementReferences 方法</span><span class="sxs-lookup"><span data-stu-id="1bcd3-109">ConditionalWeakTableElementReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="1bcd3-110">識別那些根目錄透過直接成員欄位參考以及透過 `ConditionalWeakTable` 相依性來參考之物件的可轉移結束。</span><span class="sxs-lookup"><span data-stu-id="1bcd3-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1bcd3-111">需求</span><span class="sxs-lookup"><span data-stu-id="1bcd3-111">Requirements</span></span>  
 <span data-ttu-id="1bcd3-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1bcd3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bcd3-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1bcd3-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1bcd3-114">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bcd3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bcd3-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="1bcd3-115">See also</span></span>

- [<span data-ttu-id="1bcd3-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="1bcd3-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="1bcd3-117">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="1bcd3-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
