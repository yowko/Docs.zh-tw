---
title: ICorProfilerInfo4::InitializeCurrentThread 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
ms.openlocfilehash: b52a0e7f993629c1005883723c734996d75300a7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868430"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="c1085-102">ICorProfilerInfo4::InitializeCurrentThread 方法</span><span class="sxs-lookup"><span data-stu-id="c1085-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="c1085-103">在同一個執行緒上的後續分析工具 API 呼叫之前，將目前的執行緒初始化，以便避免鎖死。</span><span class="sxs-lookup"><span data-stu-id="c1085-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1085-104">語法</span><span class="sxs-lookup"><span data-stu-id="c1085-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="c1085-105">備註</span><span class="sxs-lookup"><span data-stu-id="c1085-105">Remarks</span></span>  
 <span data-ttu-id="c1085-106">我們建議您在有擱置的執行緒時，于將呼叫 profiler API 的任何執行緒上呼叫 `InitializeCurrentThread`。</span><span class="sxs-lookup"><span data-stu-id="c1085-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="c1085-107">這個方法通常是由取樣分析工具所使用，它會建立自己的執行緒來呼叫[ICorProfilerInfo2：:D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md)方法，以便在目標執行緒暫停時執行堆疊的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="c1085-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="c1085-108">藉由在分析工具第一次建立取樣執行緒時呼叫 `InitializeCurrentThread` 一次，分析工具可以確保在第一次呼叫 `DoStackSnapshot` 期間，CLR 原本就會執行的延遲每一線程初始化，現在可以在沒有其他執行緒暫停時安全地進行。</span><span class="sxs-lookup"><span data-stu-id="c1085-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1085-109">`InitializeCurrentThread` 會事先進行初始化，以完成會產生鎖定的工作，而且可能會鎖死。</span><span class="sxs-lookup"><span data-stu-id="c1085-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="c1085-110">只有在沒有暫止的執行緒時，才呼叫 `InitializeCurrentThread`。</span><span class="sxs-lookup"><span data-stu-id="c1085-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1085-111">需求</span><span class="sxs-lookup"><span data-stu-id="c1085-111">Requirements</span></span>  
 <span data-ttu-id="c1085-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c1085-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1085-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c1085-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c1085-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1085-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1085-115">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1085-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1085-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="c1085-116">See also</span></span>

- [<span data-ttu-id="c1085-117">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="c1085-117">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="c1085-118">分析介面</span><span class="sxs-lookup"><span data-stu-id="c1085-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="c1085-119">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="c1085-119">Profiling</span></span>](index.md)
