---
title: ICorProfilerCallback3 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
ms.openlocfilehash: ad9c5445cbef0be7919570db64b027556d923752
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865567"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="e9986-102">ICorProfilerCallback3 介面</span><span class="sxs-lookup"><span data-stu-id="e9986-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="e9986-103">提供公用語言執行時間（CLR）用來將附加和卸離狀態資訊傳達給分析工具的回呼方法。</span><span class="sxs-lookup"><span data-stu-id="e9986-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e9986-104">方法</span><span class="sxs-lookup"><span data-stu-id="e9986-104">Methods</span></span>  
  
|<span data-ttu-id="e9986-105">方法</span><span class="sxs-lookup"><span data-stu-id="e9986-105">Method</span></span>|<span data-ttu-id="e9986-106">描述</span><span class="sxs-lookup"><span data-stu-id="e9986-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e9986-107">InitializeForAttach 方法</span><span class="sxs-lookup"><span data-stu-id="e9986-107">InitializeForAttach Method</span></span>](icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="e9986-108">由 CLR 呼叫，讓分析工具在附加作業之後有機會初始化其狀態。</span><span class="sxs-lookup"><span data-stu-id="e9986-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="e9986-109">ProfilerAttachComplete 方法</span><span class="sxs-lookup"><span data-stu-id="e9986-109">ProfilerAttachComplete Method</span></span>](icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="e9986-110">由 CLR 呼叫以指出分析工具現在可以呼叫 catch 方法。</span><span class="sxs-lookup"><span data-stu-id="e9986-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="e9986-111">ProfilerDetachSucceeded 方法</span><span class="sxs-lookup"><span data-stu-id="e9986-111">ProfilerDetachSucceeded Method</span></span>](icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="e9986-112">通知分析工具 Common Language Runtime (CLR) 即將卸載分析工具 DLL。</span><span class="sxs-lookup"><span data-stu-id="e9986-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9986-113">備註</span><span class="sxs-lookup"><span data-stu-id="e9986-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9986-114">需求</span><span class="sxs-lookup"><span data-stu-id="e9986-114">Requirements</span></span>  
 <span data-ttu-id="e9986-115">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e9986-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9986-116">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e9986-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e9986-117">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9986-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9986-118">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9986-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9986-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="e9986-119">See also</span></span>

- [<span data-ttu-id="e9986-120">分析介面</span><span class="sxs-lookup"><span data-stu-id="e9986-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="e9986-121">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="e9986-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="e9986-122">ICorProfilerCallback2 介面</span><span class="sxs-lookup"><span data-stu-id="e9986-122">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
- [<span data-ttu-id="e9986-123">ICorProfilerCallback4 介面</span><span class="sxs-lookup"><span data-stu-id="e9986-123">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)
