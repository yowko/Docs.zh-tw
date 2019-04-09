---
title: ICorProfilerCallback3::InitializeForAttach 方法
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84d07fe975bab1b0af81299893b52142630b5bb9
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079743"
---
# <a name="icorprofilercallback3initializeforattach-method"></a><span data-ttu-id="7a8f0-102">ICorProfilerCallback3::InitializeForAttach 方法</span><span class="sxs-lookup"><span data-stu-id="7a8f0-102">ICorProfilerCallback3::InitializeForAttach Method</span></span>
<span data-ttu-id="7a8f0-103">由 Common Language Runtime (CLR) 呼叫，讓分析工具在附加作業之後有機會初始化其狀態。</span><span class="sxs-lookup"><span data-stu-id="7a8f0-103">Called by the common language runtime (CLR) to give the profiler an opportunity to initialize its state after an attach operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a8f0-104">語法</span><span class="sxs-lookup"><span data-stu-id="7a8f0-104">Syntax</span></span>  
  
```  
HRESULT InitializeForAttach(  
            [in] IUnknown * pCorProfilerInfoUnk,  
            [in] void * pvClientData,  
            [in] UINT cbClientData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a8f0-105">參數</span><span class="sxs-lookup"><span data-stu-id="7a8f0-105">Parameters</span></span>  
 `pCorProfilerInfoUnk`  
 <span data-ttu-id="7a8f0-106">[in] `ICorProfilerInfo*` 介面的介面指標。</span><span class="sxs-lookup"><span data-stu-id="7a8f0-106">[in] An interface pointer for the `ICorProfilerInfo*` interface.</span></span>  
  
 `pvClientData`  
 <span data-ttu-id="7a8f0-107">[in]資料指標傳遞給[iclrprofiling:: Attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)方法在其`pvClientData`參數。</span><span class="sxs-lookup"><span data-stu-id="7a8f0-107">[in] A pointer to the data passed to the [IClrProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) method in its `pvClientData` parameter.</span></span> <span data-ttu-id="7a8f0-108">如果這個參數為 null，則 `cbClientData` 將會是 0 (零)。</span><span class="sxs-lookup"><span data-stu-id="7a8f0-108">If this parameter is null, `cbClientData` will be 0 (zero).</span></span> <span data-ttu-id="7a8f0-109">從 `InitializeForAttach` 傳回時，CLR 會釋放這個記憶體。</span><span class="sxs-lookup"><span data-stu-id="7a8f0-109">The CLR frees this memory when it returns from `InitializeForAttach`.</span></span>  
  
 `cbClientData`  
 <span data-ttu-id="7a8f0-110">[in] `pvClientData` 指向的資料大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="7a8f0-110">[in] The size, in bytes, of the data that `pvClientData` points to.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a8f0-111">備註</span><span class="sxs-lookup"><span data-stu-id="7a8f0-111">Remarks</span></span>  
 <span data-ttu-id="7a8f0-112">CLR 會呼叫 `InitializeForAttach`，讓分析工具有機會要求回呼。</span><span class="sxs-lookup"><span data-stu-id="7a8f0-112">The CLR calls `InitializeForAttach` to give the profiler an opportunity to request callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a8f0-113">需求</span><span class="sxs-lookup"><span data-stu-id="7a8f0-113">Requirements</span></span>  
 <span data-ttu-id="7a8f0-114">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7a8f0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a8f0-115">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7a8f0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7a8f0-116">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a8f0-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7a8f0-117">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="7a8f0-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7a8f0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a8f0-118">See also</span></span>

- [<span data-ttu-id="7a8f0-119">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="7a8f0-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="7a8f0-120">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="7a8f0-120">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="7a8f0-121">分析介面</span><span class="sxs-lookup"><span data-stu-id="7a8f0-121">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="7a8f0-122">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="7a8f0-122">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
