---
title: "ICorProfilerCallback::Initialize 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.Initialize
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::Initialize
helpviewer_keywords:
- Initialize method, ICorProfilerCallback interface [.NET Framework profiling]
- ICorProfilerCallback::Initialize method [.NET Framework profiling]
ms.assetid: dc5fab2a-4b45-4b12-8727-b89c9915f23e
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2eebe596b3459d51afe66df4bb81f74e93f3526e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackinitialize-method"></a><span data-ttu-id="0d8d5-102">ICorProfilerCallback::Initialize 方法</span><span class="sxs-lookup"><span data-stu-id="0d8d5-102">ICorProfilerCallback::Initialize Method</span></span>
<span data-ttu-id="0d8d5-103">呼叫以初始化程式碼剖析工具，每當新的 common language runtime (CLR) 應用程式已啟動。</span><span class="sxs-lookup"><span data-stu-id="0d8d5-103">Called to initialize the code profiler whenever a new common language runtime (CLR) application is started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d8d5-104">語法</span><span class="sxs-lookup"><span data-stu-id="0d8d5-104">Syntax</span></span>  
  
```  
HRESULT Initialize(  
    [in] IUnknown     *pICorProfilerInfoUnk);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0d8d5-105">參數</span><span class="sxs-lookup"><span data-stu-id="0d8d5-105">Parameters</span></span>  
 `pICorProfilerInfoUnk`  
 <span data-ttu-id="0d8d5-106">[在](/cpp/atl/iunknown)必須在查詢分析工具的介面[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)介面指標。</span><span class="sxs-lookup"><span data-stu-id="0d8d5-106">[in](/cpp/atl/iunknown) interface that the profiler must query for an [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d8d5-107">備註</span><span class="sxs-lookup"><span data-stu-id="0d8d5-107">Remarks</span></span>  
 <span data-ttu-id="0d8d5-108">`Initialize`呼叫是唯一的機會，啟用 （或停用） 是不變的回呼。</span><span class="sxs-lookup"><span data-stu-id="0d8d5-108">The `Initialize` call is the only opportunity to enable (or disable) callbacks that are immutable.</span></span> <span data-ttu-id="0d8d5-109">一旦回呼會啟用`Initialize`呼叫，所以無法停用更新版本使用[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)。</span><span class="sxs-lookup"><span data-stu-id="0d8d5-109">Once a callback is enabled by the `Initialize` call, it cannot be disabled later using [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md).</span></span> <span data-ttu-id="0d8d5-110">COR_PRF_MONITOR_IMMUTABLE 值[COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md)列舉型別指示哪些事件是不變。</span><span class="sxs-lookup"><span data-stu-id="0d8d5-110">The COR_PRF_MONITOR_IMMUTABLE value of the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration indicates which events are immutable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d8d5-111">需求</span><span class="sxs-lookup"><span data-stu-id="0d8d5-111">Requirements</span></span>  
 <span data-ttu-id="0d8d5-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0d8d5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d8d5-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0d8d5-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0d8d5-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0d8d5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d8d5-115">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d8d5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d8d5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d8d5-116">See Also</span></span>  
 [<span data-ttu-id="0d8d5-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="0d8d5-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="0d8d5-118">Shutdown 方法</span><span class="sxs-lookup"><span data-stu-id="0d8d5-118">Shutdown Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)
