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
ms.openlocfilehash: b9b284de102dc75a637803ca5be0f2769da452ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730314"
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a><span data-ttu-id="c5c1f-102">ICorProfilerCallback3::ProfilerDetachSucceeded 方法</span><span class="sxs-lookup"><span data-stu-id="c5c1f-102">ICorProfilerCallback3::ProfilerDetachSucceeded Method</span></span>

<span data-ttu-id="c5c1f-103">通知分析工具 Common Language Runtime (CLR) 即將卸載分析工具 DLL。</span><span class="sxs-lookup"><span data-stu-id="c5c1f-103">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5c1f-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5c1f-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a><span data-ttu-id="c5c1f-105">傳回值</span><span class="sxs-lookup"><span data-stu-id="c5c1f-105">Return Value</span></span>  

 <span data-ttu-id="c5c1f-106">忽略此回呼傳回的值。</span><span class="sxs-lookup"><span data-stu-id="c5c1f-106">The return value from this callback is ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5c1f-107">備註</span><span class="sxs-lookup"><span data-stu-id="c5c1f-107">Remarks</span></span>  

 <span data-ttu-id="c5c1f-108">所有執行緒都結束分析工具的程式碼後，就會核發 `ProfilerDetachSucceeded` 回呼。</span><span class="sxs-lookup"><span data-stu-id="c5c1f-108">The `ProfilerDetachSucceeded` callback is issued after all threads have exited the profiler's code.</span></span> <span data-ttu-id="c5c1f-109">呼叫這個方法時，分析工具應該執行任何不適合其解構函式的最後一刻工作，例如通知其 UI 或記錄元件。</span><span class="sxs-lookup"><span data-stu-id="c5c1f-109">When this method is called, the profiler should perform any last-minute tasks that are not appropriate for its destructor, such as notifying its UI or logging component.</span></span> <span data-ttu-id="c5c1f-110">不過，分析工具在此回呼 (（例如 [ICorProfilerInfo](icorprofilerinfo-interface.md) 或介面) ）期間，不能針對 CLR 所提供的介面呼叫函數 `IMetaData*` 。</span><span class="sxs-lookup"><span data-stu-id="c5c1f-110">However, the profiler must not call functions on interfaces that are provided by the CLR during this callback (such as the [ICorProfilerInfo](icorprofilerinfo-interface.md) or `IMetaData*` interfaces).</span></span>  
  
 <span data-ttu-id="c5c1f-111">CLR 會在 Windows 應用程式事件記錄檔中建立項目，表示中斷連結作業成功。</span><span class="sxs-lookup"><span data-stu-id="c5c1f-111">The CLR creates an entry in the Windows Application event log to indicate that the detach operation is successful.</span></span>  
  
 <span data-ttu-id="c5c1f-112">分析工具從回呼傳回之後，CLR 釋放此分析工具物件並卸載分析工具 DLL。</span><span class="sxs-lookup"><span data-stu-id="c5c1f-112">After the profiler returns from this callback, the CLR releases the profiler object and unloads the profiler DLL.</span></span> <span data-ttu-id="c5c1f-113">因此，在分析工具從此回呼傳回之後，不可執行任何可能導致在分析工具 DLL 中執行的動作。</span><span class="sxs-lookup"><span data-stu-id="c5c1f-113">Therefore, the profiler must not perform any actions that would cause execution to occur inside the profiler DLL after it returns from this callback.</span></span> <span data-ttu-id="c5c1f-114">例如，它不可建立執行緒或註冊計時器回呼。</span><span class="sxs-lookup"><span data-stu-id="c5c1f-114">For example, it must not create threads or register timer callbacks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5c1f-115">需求</span><span class="sxs-lookup"><span data-stu-id="c5c1f-115">Requirements</span></span>  

 <span data-ttu-id="c5c1f-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5c1f-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5c1f-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c5c1f-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c5c1f-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5c1f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5c1f-119">**.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5c1f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5c1f-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5c1f-120">See also</span></span>

- [<span data-ttu-id="c5c1f-121">中繼資料介面</span><span class="sxs-lookup"><span data-stu-id="c5c1f-121">Metadata Interfaces</span></span>](../metadata/metadata-interfaces.md)
- [<span data-ttu-id="c5c1f-122">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="c5c1f-122">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="c5c1f-123">分析介面</span><span class="sxs-lookup"><span data-stu-id="c5c1f-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c5c1f-124">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="c5c1f-124">Profiling</span></span>](index.md)
