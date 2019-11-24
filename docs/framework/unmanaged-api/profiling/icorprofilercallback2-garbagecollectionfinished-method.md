---
title: ICorProfilerCallback2::GarbageCollectionFinished 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished
helpviewer_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished method [.NET Framework profiling]
- GarbageCollectionFinished method [.NET Framework profiling]
ms.assetid: 1a5758ea-2354-43c0-92a3-32c9909d64e1
topic_type:
- apiref
ms.openlocfilehash: 1217bb30be8b88f8ba1cf21f03f2531778358d4b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439837"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="7e289-102">ICorProfilerCallback2::GarbageCollectionFinished 方法</span><span class="sxs-lookup"><span data-stu-id="7e289-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="7e289-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span><span class="sxs-lookup"><span data-stu-id="7e289-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e289-104">語法</span><span class="sxs-lookup"><span data-stu-id="7e289-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7e289-105">備註</span><span class="sxs-lookup"><span data-stu-id="7e289-105">Remarks</span></span>  
 <span data-ttu-id="7e289-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span><span class="sxs-lookup"><span data-stu-id="7e289-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e289-107">需求</span><span class="sxs-lookup"><span data-stu-id="7e289-107">Requirements</span></span>  
 <span data-ttu-id="7e289-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7e289-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e289-109">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7e289-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7e289-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e289-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e289-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e289-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e289-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="7e289-112">See also</span></span>

- [<span data-ttu-id="7e289-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7e289-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="7e289-114">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="7e289-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
