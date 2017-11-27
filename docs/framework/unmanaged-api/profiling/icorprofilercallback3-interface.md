---
title: "ICorProfilerCallback3 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback3
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback3
helpviewer_keywords: ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c62dfb9b44999309ab2be7dfdcdfba3bb5dde29c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="d3db7-102">ICorProfilerCallback3 介面</span><span class="sxs-lookup"><span data-stu-id="d3db7-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="d3db7-103">提供 common language runtime (CLR) 用來通訊的回呼方法附加和卸離狀態資訊給分析工具。</span><span class="sxs-lookup"><span data-stu-id="d3db7-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3db7-104">方法</span><span class="sxs-lookup"><span data-stu-id="d3db7-104">Methods</span></span>  
  
|<span data-ttu-id="d3db7-105">方法</span><span class="sxs-lookup"><span data-stu-id="d3db7-105">Method</span></span>|<span data-ttu-id="d3db7-106">說明</span><span class="sxs-lookup"><span data-stu-id="d3db7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3db7-107">InitializeForAttach 方法</span><span class="sxs-lookup"><span data-stu-id="d3db7-107">InitializeForAttach Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="d3db7-108">由 CLR 讓分析工具有機會初始化其狀態在附加作業之後呼叫。</span><span class="sxs-lookup"><span data-stu-id="d3db7-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="d3db7-109">ProfilerAttachComplete 方法</span><span class="sxs-lookup"><span data-stu-id="d3db7-109">ProfilerAttachComplete Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="d3db7-110">由 CLR 的指示分析工具現在可以呼叫更新方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="d3db7-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="d3db7-111">ProfilerDetachSucceeded 方法</span><span class="sxs-lookup"><span data-stu-id="d3db7-111">ProfilerDetachSucceeded Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="d3db7-112">通知分析工具 Common Language Runtime (CLR) 即將卸載分析工具 DLL。</span><span class="sxs-lookup"><span data-stu-id="d3db7-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3db7-113">備註</span><span class="sxs-lookup"><span data-stu-id="d3db7-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3db7-114">需求</span><span class="sxs-lookup"><span data-stu-id="d3db7-114">Requirements</span></span>  
 <span data-ttu-id="d3db7-115">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d3db7-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3db7-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d3db7-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d3db7-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3db7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3db7-118">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3db7-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3db7-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3db7-119">See Also</span></span>  
 [<span data-ttu-id="d3db7-120">分析介面</span><span class="sxs-lookup"><span data-stu-id="d3db7-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="d3db7-121">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="d3db7-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="d3db7-122">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="d3db7-122">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="d3db7-123">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="d3db7-123">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
