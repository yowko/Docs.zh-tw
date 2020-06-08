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
ms.openlocfilehash: ea4fc8ab39d616415106150f56f4b7afd5f68237
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500100"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="90ced-102">ICorProfilerCallback::Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="90ced-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="90ced-103">呼叫以在每次啟動新的 common language runtime （CLR）應用程式時初始化程式碼分析工具。</span><span class="sxs-lookup"><span data-stu-id="90ced-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90ced-104">語法</span><span class="sxs-lookup"><span data-stu-id="90ced-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90ced-105">參數</span><span class="sxs-lookup"><span data-stu-id="90ced-105">Parameters</span></span>

- `pICorProfilerInfoUnk`

  <span data-ttu-id="90ced-106">\[in] [IUnknown](/cpp/atl/iunknown)介面的指標，分析工具必須查詢[ICorProfilerInfo](icorprofilerinfo-interface.md)介面指標。</span><span class="sxs-lookup"><span data-stu-id="90ced-106">\[in] Pointer to an [IUnknown](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](icorprofilerinfo-interface.md) interface pointer.</span></span>  

## <a name="remarks"></a><span data-ttu-id="90ced-107">備註</span><span class="sxs-lookup"><span data-stu-id="90ced-107">Remarks</span></span>  
 <span data-ttu-id="90ced-108">`Initialize`呼叫是啟用（或停用）不變回呼的唯一機會。</span><span class="sxs-lookup"><span data-stu-id="90ced-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="90ced-109">一旦呼叫啟用回呼 `Initialize` ，稍後將無法使用[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)予以停用。</span><span class="sxs-lookup"><span data-stu-id="90ced-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="90ced-110">[COR_PRF_MONITOR](cor-prf-monitor-enumeration.md)列舉的 COR_PRF_MONITOR_IMMUTABLE 值會指出哪些事件是不可變的。</span><span class="sxs-lookup"><span data-stu-id="90ced-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90ced-111">規格需求</span><span class="sxs-lookup"><span data-stu-id="90ced-111">Requirements</span></span>  
 <span data-ttu-id="90ced-112">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="90ced-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90ced-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="90ced-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="90ced-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90ced-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90ced-115">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90ced-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90ced-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90ced-116">See also</span></span>

- [<span data-ttu-id="90ced-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="90ced-117">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="90ced-118">Shutdown 方法</span><span class="sxs-lookup"><span data-stu-id="90ced-118">Shutdown Method</span></span>](icorprofilercallback-shutdown-method.md)
