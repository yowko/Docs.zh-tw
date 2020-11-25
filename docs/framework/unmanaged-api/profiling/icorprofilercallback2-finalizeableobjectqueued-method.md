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
ms.openlocfilehash: 4429524b5f3baff3251acbd7ef7954d30a3e0093
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731944"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="705f6-102">ICorProfilerCallback2::FinalizeableObjectQueued 方法</span><span class="sxs-lookup"><span data-stu-id="705f6-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>

<span data-ttu-id="705f6-103">通知程式碼分析工具，具有完成項的物件已排入完成項執行緒，以執行其 `Finalize` 方法。</span><span class="sxs-lookup"><span data-stu-id="705f6-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="705f6-104">語法</span><span class="sxs-lookup"><span data-stu-id="705f6-104">Syntax</span></span>  
  
```cpp  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="705f6-105">參數</span><span class="sxs-lookup"><span data-stu-id="705f6-105">Parameters</span></span>  

 `finalizerFlags`  
 <span data-ttu-id="705f6-106">在描述完成項之層面的 [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) 列舉值。</span><span class="sxs-lookup"><span data-stu-id="705f6-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="705f6-107">在已排入佇列之物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="705f6-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="705f6-108">需求</span><span class="sxs-lookup"><span data-stu-id="705f6-108">Requirements</span></span>  

 <span data-ttu-id="705f6-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="705f6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="705f6-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="705f6-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="705f6-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="705f6-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="705f6-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="705f6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="705f6-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="705f6-113">See also</span></span>

- [<span data-ttu-id="705f6-114">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="705f6-114">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="705f6-115">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="705f6-115">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
