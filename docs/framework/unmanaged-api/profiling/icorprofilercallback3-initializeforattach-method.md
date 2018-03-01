---
title: "ICorProfilerCallback3::InitializeForAttach 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback3.InitializeForAttach Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::InitializeForAttach
helpviewer_keywords:
- InitializeForAttach method [.NET Framework profiling]
- ICorProfilerCallback3::InitializeForAttach method [.NET Framework profiling]
ms.assetid: bed097b3-6d52-46c9-bee7-ac7910b6fc3f
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 124e27e446e129173018aed9d3ab770582342c72
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="dca68-102">ICorProfilerCallback3::InitializeForAttach 方法</span><span class="sxs-lookup"><span data-stu-id="dca68-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="dca68-103">由 Common Language Runtime (CLR) 呼叫，讓分析工具在附加作業之後有機會初始化其狀態。</span><span class="sxs-lookup"><span data-stu-id="dca68-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dca68-104">語法</span><span class="sxs-lookup"><span data-stu-id="dca68-104">Syntax</span></span>  
  
```  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dca68-105">參數</span><span class="sxs-lookup"><span data-stu-id="dca68-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="dca68-106">[in] `ICorProfilerInfo*` 介面的介面指標。</span><span class="sxs-lookup"><span data-stu-id="dca68-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="dca68-107">[in]資料指標傳遞至[iclrprofiling:: Attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)方法在其`pvClientData`參數。</span><span class="sxs-lookup"><span data-stu-id="dca68-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="dca68-108">如果這個參數為 null，則 `cbClientData` 將會是 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="dca68-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="dca68-109">從 `InitializeForAttach` 傳回時，CLR 會釋放這個記憶體。</span><span class="sxs-lookup"><span data-stu-id="dca68-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="dca68-110">[in] `pvClientData` 指向的資料大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="dca68-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dca68-111">備註</span><span class="sxs-lookup"><span data-stu-id="dca68-111">Remarks</span></span>  
 <span data-ttu-id="dca68-112">CLR 會呼叫 `InitializeForAttach`，讓分析工具有機會要求回呼。</span><span class="sxs-lookup"><span data-stu-id="dca68-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dca68-113">需求</span><span class="sxs-lookup"><span data-stu-id="dca68-113">Requirements</span></span>  
 <span data-ttu-id="dca68-114">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="dca68-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dca68-115">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dca68-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dca68-116">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dca68-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dca68-117">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dca68-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dca68-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="dca68-118">See Also</span></span>  
 [<span data-ttu-id="dca68-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="dca68-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="dca68-120">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="dca68-120">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="dca68-121">分析介面</span><span class="sxs-lookup"><span data-stu-id="dca68-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="dca68-122">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="dca68-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
