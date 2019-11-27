---
title: ICorProfilerCallback::Initialize 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Initialize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type:
- apiref
ms.openlocfilehash: 64df6a81eb23c20537238c702fd0c204d64d14bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434547"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="ac486-102">ICorProfilerCallback::Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="ac486-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="ac486-103">呼叫以在每次啟動新的 common language runtime （CLR）應用程式時初始化程式碼分析工具。</span><span class="sxs-lookup"><span data-stu-id="ac486-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac486-104">語法</span><span class="sxs-lookup"><span data-stu-id="ac486-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac486-105">參數</span><span class="sxs-lookup"><span data-stu-id="ac486-105">Parameters</span></span>  
 `pICorProfilerInfoUnk`  
 <span data-ttu-id="ac486-106">[在介面中](/cpp/atl/iunknown)，profiler 必須查詢[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)介面指標。</span><span class="sxs-lookup"><span data-stu-id="ac486-106">[in](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac486-107">備註</span><span class="sxs-lookup"><span data-stu-id="ac486-107">Remarks</span></span>  
 <span data-ttu-id="ac486-108">`Initialize` 呼叫是啟用（或停用）不變回呼的唯一機會。</span><span class="sxs-lookup"><span data-stu-id="ac486-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="ac486-109">一旦 `Initialize` 呼叫啟用回呼，稍後就無法使用[ICorProfilerInfo：： SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)予以停用。</span><span class="sxs-lookup"><span data-stu-id="ac486-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="ac486-110">[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉的 COR_PRF_MONITOR_IMMUTABLE 值會指出哪些事件是不可變的。</span><span class="sxs-lookup"><span data-stu-id="ac486-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac486-111">需求</span><span class="sxs-lookup"><span data-stu-id="ac486-111">Requirements</span></span>  
 <span data-ttu-id="ac486-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ac486-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac486-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ac486-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ac486-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac486-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac486-115">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac486-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac486-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="ac486-116">See also</span></span>

- [<span data-ttu-id="ac486-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ac486-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="ac486-118">Shutdown 方法</span><span class="sxs-lookup"><span data-stu-id="ac486-118">Shutdown Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
