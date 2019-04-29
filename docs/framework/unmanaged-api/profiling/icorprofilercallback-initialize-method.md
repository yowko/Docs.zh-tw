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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 16001c4af2bcd8aa8d5fff6b06fa8c275bc24cb9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597474"
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="d6375-102">ICorProfilerCallback::Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="d6375-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="d6375-103">呼叫以初始化程式碼剖析工具，每次啟動新的 common language runtime (CLR) 應用程式時。</span><span class="sxs-lookup"><span data-stu-id="d6375-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6375-104">語法</span><span class="sxs-lookup"><span data-stu-id="d6375-104">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6375-105">參數</span><span class="sxs-lookup"><span data-stu-id="d6375-105">Parameters</span></span>  
 `pICorProfilerInfoUnk`  
 <span data-ttu-id="d6375-106">[在 ](/cpp/atl/iunknown)分析工具必須查詢的介面[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)介面指標。</span><span class="sxs-lookup"><span data-stu-id="d6375-106">[in](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6375-107">備註</span><span class="sxs-lookup"><span data-stu-id="d6375-107">Remarks</span></span>  
 <span data-ttu-id="d6375-108">`Initialize`呼叫是唯一的機會，啟用 （或停用） 是固定不變的回呼。</span><span class="sxs-lookup"><span data-stu-id="d6375-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="d6375-109">一旦啟用回呼`Initialize`呼叫時，它不能使用停用之後[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)。</span><span class="sxs-lookup"><span data-stu-id="d6375-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="d6375-110">COR_PRF_MONITOR_IMMUTABLE 值[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉，指出哪些事件是固定不變。</span><span class="sxs-lookup"><span data-stu-id="d6375-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6375-111">需求</span><span class="sxs-lookup"><span data-stu-id="d6375-111">Requirements</span></span>  
 <span data-ttu-id="d6375-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d6375-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6375-113">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d6375-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d6375-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6375-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6375-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6375-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6375-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6375-116">See also</span></span>

- [<span data-ttu-id="d6375-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d6375-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d6375-118">Shutdown 方法</span><span class="sxs-lookup"><span data-stu-id="d6375-118">Shutdown Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
