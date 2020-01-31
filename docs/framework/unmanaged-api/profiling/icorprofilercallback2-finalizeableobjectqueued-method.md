---
title: ICorProfilerCallback2::FinalizeableObjectQueued 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.FinalizeableObjectQueued
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::FinalizeableObjectQueued
helpviewer_keywords:
- FinalizeableObjectQueued method [.NET Framework profiling]
- ICorProfilerCallback2::FinalizeableObjectQueued method [.NET Framework profiling]
ms.assetid: 92d76893-683c-475d-9996-5bff03cdb10f
topic_type:
- apiref
ms.openlocfilehash: b9093f920a8c14247bc51471da3682c7e500afa4
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865801"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="c8294-102">ICorProfilerCallback2::FinalizeableObjectQueued 方法</span><span class="sxs-lookup"><span data-stu-id="c8294-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="c8294-103">通知程式碼分析工具，已將具有完成項的物件排入等候執行緒，以執行其 `Finalize` 方法。</span><span class="sxs-lookup"><span data-stu-id="c8294-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8294-104">語法</span><span class="sxs-lookup"><span data-stu-id="c8294-104">Syntax</span></span>  
  
```cpp  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8294-105">參數</span><span class="sxs-lookup"><span data-stu-id="c8294-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="c8294-106">在描述完成項各個層面之[COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md)列舉的值。</span><span class="sxs-lookup"><span data-stu-id="c8294-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="c8294-107">在已排入佇列之物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c8294-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8294-108">需求</span><span class="sxs-lookup"><span data-stu-id="c8294-108">Requirements</span></span>  
 <span data-ttu-id="c8294-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c8294-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8294-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c8294-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c8294-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8294-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8294-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8294-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8294-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="c8294-113">See also</span></span>

- [<span data-ttu-id="c8294-114">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c8294-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c8294-115">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="c8294-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
