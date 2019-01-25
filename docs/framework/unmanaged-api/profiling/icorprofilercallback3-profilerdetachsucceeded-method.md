---
title: ICorProfilerCallback3::ProfilerDetachSucceeded 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 52803fc04aa55f40a131e2d53dc4ef7dba70bcde
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54727114"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="d02c5-102">ICorProfilerCallback3::ProfilerDetachSucceeded 方法</span><span class="sxs-lookup"><span data-stu-id="d02c5-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>
<span data-ttu-id="d02c5-103">通知分析工具 Common Language Runtime (CLR) 即將卸載分析工具 DLL。</span><span class="sxs-lookup"><span data-stu-id="d02c5-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d02c5-104">語法</span><span class="sxs-lookup"><span data-stu-id="d02c5-104">Syntax</span></span>  
  
```  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="d02c5-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="d02c5-105">Return Value</span></span>  
 <span data-ttu-id="d02c5-106">忽略此回呼傳回的值。</span><span class="sxs-lookup"><span data-stu-id="d02c5-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d02c5-107">備註</span><span class="sxs-lookup"><span data-stu-id="d02c5-107">Remarks</span></span>  
 <span data-ttu-id="d02c5-108">所有執行緒都結束分析工具的程式碼後，就會核發 `ProfilerDetachSucceeded` 回呼。</span><span class="sxs-lookup"><span data-stu-id="d02c5-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="d02c5-109">呼叫這個方法時，分析工具應該執行任何不適合其解構函式的最後一刻工作，例如通知其 UI 或記錄元件。</span><span class="sxs-lookup"><span data-stu-id="d02c5-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="d02c5-110">不過，程式碼剖析工具不得呼叫函式會在回呼期間 CLR 所提供的介面上 (例如[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)或`IMetaData*`介面)。</span><span class="sxs-lookup"><span data-stu-id="d02c5-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="d02c5-111">CLR 會在 Windows 應用程式事件記錄檔中建立項目，表示中斷連結作業成功。</span><span class="sxs-lookup"><span data-stu-id="d02c5-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="d02c5-112">分析工具從回呼傳回之後，CLR 釋放此分析工具物件並卸載分析工具 DLL。</span><span class="sxs-lookup"><span data-stu-id="d02c5-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="d02c5-113">因此，在分析工具從此回呼傳回之後，不可執行任何可能導致在分析工具 DLL 中執行的動作。</span><span class="sxs-lookup"><span data-stu-id="d02c5-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="d02c5-114">例如，它不可建立執行緒或註冊計時器回呼。</span><span class="sxs-lookup"><span data-stu-id="d02c5-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d02c5-115">需求</span><span class="sxs-lookup"><span data-stu-id="d02c5-115">Requirements</span></span>  
 <span data-ttu-id="d02c5-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d02c5-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d02c5-117">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d02c5-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d02c5-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d02c5-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d02c5-119">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d02c5-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d02c5-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d02c5-120">See also</span></span>
- [<span data-ttu-id="d02c5-121">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="d02c5-121">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="d02c5-122">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="d02c5-122">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="d02c5-123">分析介面</span><span class="sxs-lookup"><span data-stu-id="d02c5-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="d02c5-124">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="d02c5-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
