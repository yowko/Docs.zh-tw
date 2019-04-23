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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f613842c12b50b8a58aac1b71bf2f3c53aaf961f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59231093"
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="e0998-102">ICorProfilerCallback2::GarbageCollectionFinished 方法</span><span class="sxs-lookup"><span data-stu-id="e0998-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="e0998-103">記憶體回收完成，並為它已發行所有記憶體回收回呼會通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="e0998-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0998-104">語法</span><span class="sxs-lookup"><span data-stu-id="e0998-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e0998-105">備註</span><span class="sxs-lookup"><span data-stu-id="e0998-105">Remarks</span></span>  
 <span data-ttu-id="e0998-106">它是安全的程式碼剖析工具來檢查其最終位置中的物件時`GarbageCollectionFinished`呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="e0998-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0998-107">需求</span><span class="sxs-lookup"><span data-stu-id="e0998-107">Requirements</span></span>  
 <span data-ttu-id="e0998-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e0998-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0998-109">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e0998-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e0998-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0998-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0998-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0998-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0998-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0998-112">See also</span></span>

- [<span data-ttu-id="e0998-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="e0998-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="e0998-114">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="e0998-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
