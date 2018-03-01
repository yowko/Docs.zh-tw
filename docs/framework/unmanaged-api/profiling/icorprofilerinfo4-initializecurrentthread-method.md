---
title: "ICorProfilerInfo4::InitializeCurrentThread 方法"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f3c261068b38861dca2633a490e46d9f44371d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="7094e-102">ICorProfilerInfo4::InitializeCurrentThread 方法</span><span class="sxs-lookup"><span data-stu-id="7094e-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="7094e-103">初始化目前的執行緒之前後續程式碼剖析工具應用程式開發介面呼叫，在相同執行緒，因此可以避免發生死結。</span><span class="sxs-lookup"><span data-stu-id="7094e-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7094e-104">語法</span><span class="sxs-lookup"><span data-stu-id="7094e-104">Syntax</span></span>  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7094e-105">備註</span><span class="sxs-lookup"><span data-stu-id="7094e-105">Remarks</span></span>  
 <span data-ttu-id="7094e-106">我們建議您呼叫`InitializeCurrentThread`會呼叫程式碼剖析工具的任何執行緒上應用程式開發介面有暫止的執行緒。</span><span class="sxs-lookup"><span data-stu-id="7094e-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="7094e-107">這個方法通常由取樣分析工具，建立自己的執行緒來呼叫[icorprofilerinfo2:: Dostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)方法，以執行堆疊會引導目標執行緒暫停。</span><span class="sxs-lookup"><span data-stu-id="7094e-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="7094e-108">藉由呼叫`InitializeCurrentThread`之後當分析工具會先建立取樣執行緒，分析工具可確保每個執行緒延遲初始設定，另外執行 CLR 的第一個呼叫期間`DoStackSnapshot`現在可能安全地當沒有其他執行緒都在暫止。</span><span class="sxs-lookup"><span data-stu-id="7094e-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7094e-109">`InitializeCurrentThread`未初始化事先完成的工作取得鎖定，鎖定，而且可能會發生死結。</span><span class="sxs-lookup"><span data-stu-id="7094e-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="7094e-110">呼叫`InitializeCurrentThread`時，才有任何暫止的執行緒。</span><span class="sxs-lookup"><span data-stu-id="7094e-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7094e-111">需求</span><span class="sxs-lookup"><span data-stu-id="7094e-111">Requirements</span></span>  
 <span data-ttu-id="7094e-112">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7094e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7094e-113">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7094e-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7094e-114">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7094e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7094e-115">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7094e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7094e-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="7094e-116">See Also</span></span>  
 [<span data-ttu-id="7094e-117">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="7094e-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="7094e-118">分析介面</span><span class="sxs-lookup"><span data-stu-id="7094e-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="7094e-119">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="7094e-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
