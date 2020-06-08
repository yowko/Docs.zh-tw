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
ms.openlocfilehash: 02a690503d7b6323f19dcb66247d8a552b760b1c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499203"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="d7bc5-102">ICorProfilerCallback5 介面</span><span class="sxs-lookup"><span data-stu-id="d7bc5-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="d7bc5-103">當搭配[ICorProfilerCallback：： RootReferences](icorprofilercallback-rootreferences-method.md)或[ICorProfilerCallback2：： RootReferences2](icorprofilercallback2-rootreferences2-method.md)方法與[ICorProfilerCallback：： ObjectReferences](icorprofilercallback-objectreferences-method.md)和[ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md)方法一起使用時，可協助 profiler 識別即時物件的完整關閉。</span><span class="sxs-lookup"><span data-stu-id="d7bc5-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="d7bc5-104">`ICorProfilerCallback5` 必須由 Managed 記憶體分析工具實作，以訂閱與相依性控制代碼相關的通知。</span><span class="sxs-lookup"><span data-stu-id="d7bc5-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7bc5-105">備註</span><span class="sxs-lookup"><span data-stu-id="d7bc5-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7bc5-106">方法</span><span class="sxs-lookup"><span data-stu-id="d7bc5-106">Methods</span></span>  
  
|<span data-ttu-id="d7bc5-107">方法</span><span class="sxs-lookup"><span data-stu-id="d7bc5-107">Method</span></span>|<span data-ttu-id="d7bc5-108">描述</span><span class="sxs-lookup"><span data-stu-id="d7bc5-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7bc5-109">ConditionalWeakTableElementReferences 方法</span><span class="sxs-lookup"><span data-stu-id="d7bc5-109">ConditionalWeakTableElementReferences Method</span></span>](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="d7bc5-110">識別那些根目錄透過直接成員欄位參考以及透過 `ConditionalWeakTable` 相依性來參考之物件的可轉移結束。</span><span class="sxs-lookup"><span data-stu-id="d7bc5-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d7bc5-111">規格需求</span><span class="sxs-lookup"><span data-stu-id="d7bc5-111">Requirements</span></span>  
 <span data-ttu-id="d7bc5-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d7bc5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7bc5-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d7bc5-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d7bc5-114">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7bc5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7bc5-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7bc5-115">See also</span></span>

- [<span data-ttu-id="d7bc5-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="d7bc5-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="d7bc5-117">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="d7bc5-117">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
