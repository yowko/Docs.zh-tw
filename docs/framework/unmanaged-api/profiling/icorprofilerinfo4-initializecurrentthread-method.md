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
ms.openlocfilehash: 51f16523c00cc3dd95b786f1586ccfd75ce8d5f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733824"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="4efc9-102">ICorProfilerInfo4::InitializeCurrentThread 方法</span><span class="sxs-lookup"><span data-stu-id="4efc9-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>

<span data-ttu-id="4efc9-103">在相同執行緒上的後續分析工具 API 呼叫之前，初始化目前的執行緒，因此可以避免鎖死。</span><span class="sxs-lookup"><span data-stu-id="4efc9-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4efc9-104">語法</span><span class="sxs-lookup"><span data-stu-id="4efc9-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="4efc9-105">備註</span><span class="sxs-lookup"><span data-stu-id="4efc9-105">Remarks</span></span>  

 <span data-ttu-id="4efc9-106">建議您 `InitializeCurrentThread` 在有暫止的執行緒時，于任何將呼叫 PROFILER API 的執行緒上呼叫。</span><span class="sxs-lookup"><span data-stu-id="4efc9-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="4efc9-107">這種方法通常是由取樣分析工具所使用，它會建立自己的執行緒來呼叫 [ICorProfilerInfo2：:D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) 方法，以便在目標執行緒暫停時執行堆疊的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="4efc9-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="4efc9-108">藉由在分析工具 `InitializeCurrentThread` 第一次建立取樣執行緒時呼叫一次，分析工具可以確定在第一次呼叫期間，CLR 會以其他方式執行的延遲個別執行緒初始化， `DoStackSnapshot` 現在可以在沒有其他執行緒暫止時安全地發生。</span><span class="sxs-lookup"><span data-stu-id="4efc9-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4efc9-109">`InitializeCurrentThread` 會事先進行初始化以完成可鎖定的工作，而且可能會發生鎖死。</span><span class="sxs-lookup"><span data-stu-id="4efc9-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="4efc9-110">`InitializeCurrentThread`只有在沒有暫止的執行緒時呼叫。</span><span class="sxs-lookup"><span data-stu-id="4efc9-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4efc9-111">需求</span><span class="sxs-lookup"><span data-stu-id="4efc9-111">Requirements</span></span>  

 <span data-ttu-id="4efc9-112">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4efc9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4efc9-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4efc9-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4efc9-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4efc9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4efc9-115">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4efc9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4efc9-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4efc9-116">See also</span></span>

- [<span data-ttu-id="4efc9-117">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="4efc9-117">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="4efc9-118">分析介面</span><span class="sxs-lookup"><span data-stu-id="4efc9-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="4efc9-119">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="4efc9-119">Profiling</span></span>](index.md)
