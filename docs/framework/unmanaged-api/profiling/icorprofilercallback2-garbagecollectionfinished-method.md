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
ms.openlocfilehash: 47f25dbb1f88dbf580b096246016cd46f2d0d89c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499818"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="327b5-102">ICorProfilerCallback2::GarbageCollectionFinished 方法</span><span class="sxs-lookup"><span data-stu-id="327b5-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="327b5-103">通知分析工具，垃圾收集已完成，且已發出所有垃圾收集回呼。</span><span class="sxs-lookup"><span data-stu-id="327b5-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="327b5-104">語法</span><span class="sxs-lookup"><span data-stu-id="327b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="327b5-105">備註</span><span class="sxs-lookup"><span data-stu-id="327b5-105">Remarks</span></span>  
 <span data-ttu-id="327b5-106">呼叫方法時，分析工具可以安全地檢查其最終位置中的物件 `GarbageCollectionFinished` 。</span><span class="sxs-lookup"><span data-stu-id="327b5-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="327b5-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="327b5-107">Requirements</span></span>  
 <span data-ttu-id="327b5-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="327b5-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="327b5-109">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="327b5-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="327b5-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="327b5-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="327b5-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="327b5-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="327b5-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="327b5-112">See also</span></span>

- [<span data-ttu-id="327b5-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="327b5-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="327b5-114">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="327b5-114">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
