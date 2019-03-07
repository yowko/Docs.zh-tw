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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c001606e1b1642bc10377425d262676cfc2b9f15
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498233"
---
# <a name="icorprofilercallback2finalizeableobjectqueued-method"></a><span data-ttu-id="97dae-102">ICorProfilerCallback2::FinalizeableObjectQueued 方法</span><span class="sxs-lookup"><span data-stu-id="97dae-102">ICorProfilerCallback2::FinalizeableObjectQueued Method</span></span>
<span data-ttu-id="97dae-103">通知程式碼分析工具的完成設定式物件，已加入佇列至完成項執行緒執行其`Finalize`方法。</span><span class="sxs-lookup"><span data-stu-id="97dae-103">Notifies the code profiler that an object with a finalizer has been queued to the finalizer thread for execution of its `Finalize` method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97dae-104">語法</span><span class="sxs-lookup"><span data-stu-id="97dae-104">Syntax</span></span>  
  
```  
HRESULT FinalizeableObjectQueued(  
    [in] DWORD finalizerFlags,  
    [in] ObjectID objectID);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97dae-105">參數</span><span class="sxs-lookup"><span data-stu-id="97dae-105">Parameters</span></span>  
 `finalizerFlags`  
 <span data-ttu-id="97dae-106">[in]值為[COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md)各個面向說明的完成項的列舉型別。</span><span class="sxs-lookup"><span data-stu-id="97dae-106">[in] A value of the [COR_PRF_FINALIZER_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-finalizer-flags-enumeration.md) enumeration that describes aspects of the finalizer.</span></span>  
  
 `objectID`  
 <span data-ttu-id="97dae-107">[in]已排入佇列的物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="97dae-107">[in] The ID of the object that has been queued.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97dae-108">需求</span><span class="sxs-lookup"><span data-stu-id="97dae-108">Requirements</span></span>  
 <span data-ttu-id="97dae-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="97dae-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97dae-110">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="97dae-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="97dae-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97dae-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97dae-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97dae-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97dae-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="97dae-113">See also</span></span>
- [<span data-ttu-id="97dae-114">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="97dae-114">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="97dae-115">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="97dae-115">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
