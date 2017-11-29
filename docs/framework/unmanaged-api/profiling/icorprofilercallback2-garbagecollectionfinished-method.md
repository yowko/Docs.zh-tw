---
title: "ICorProfilerCallback2::GarbageCollectionFinished 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.GarbageCollectionFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::GarbageCollectionFinished
helpviewer_keywords:
- ICorProfilerCallback2::GarbageCollectionFinished method [.NET Framework profiling]
- GarbageCollectionFinished method [.NET Framework profiling]
ms.assetid: 1a5758ea-2354-43c0-92a3-32c9909d64e1
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 287c33a80144b9b04fd7e0797071d40e46a52454
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback2garbagecollectionfinished-method"></a><span data-ttu-id="ae627-102">ICorProfilerCallback2::GarbageCollectionFinished 方法</span><span class="sxs-lookup"><span data-stu-id="ae627-102">ICorProfilerCallback2::GarbageCollectionFinished Method</span></span>
<span data-ttu-id="ae627-103">完成記憶體回收，並為其已發行所有記憶體回收回呼通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="ae627-103">Notifies the profiler that garbage collection has completed and all garbage collection callbacks have been issued for it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae627-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae627-104">Syntax</span></span>  
  
```  
HRESULT GarbageCollectionFinished();  
```  
  
## <a name="remarks"></a><span data-ttu-id="ae627-105">備註</span><span class="sxs-lookup"><span data-stu-id="ae627-105">Remarks</span></span>  
 <span data-ttu-id="ae627-106">它是安全的程式碼剖析工具來檢查其最終位置中的物件時`GarbageCollectionFinished`方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="ae627-106">It is safe for the profiler to inspect objects in their final locations when the `GarbageCollectionFinished` method is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae627-107">需求</span><span class="sxs-lookup"><span data-stu-id="ae627-107">Requirements</span></span>  
 <span data-ttu-id="ae627-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae627-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae627-109">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ae627-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ae627-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae627-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae627-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae627-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae627-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae627-112">See Also</span></span>  
 [<span data-ttu-id="ae627-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ae627-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="ae627-114">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="ae627-114">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
