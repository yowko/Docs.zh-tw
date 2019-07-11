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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: abcbfaf803e930baaaf798986a585a7da5f9134d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780804"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="bd1d0-102">ICorProfilerInfo4::InitializeCurrentThread 方法</span><span class="sxs-lookup"><span data-stu-id="bd1d0-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="bd1d0-103">初始化目前的執行緒之前後續的程式碼剖析工具 API 呼叫在相同的執行緒，因此可以避免死結。</span><span class="sxs-lookup"><span data-stu-id="bd1d0-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd1d0-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd1d0-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="bd1d0-105">備註</span><span class="sxs-lookup"><span data-stu-id="bd1d0-105">Remarks</span></span>  
 <span data-ttu-id="bd1d0-106">我們建議您呼叫`InitializeCurrentThread`在任何執行緒會呼叫程式碼剖析工具 API 有暫止執行緒。</span><span class="sxs-lookup"><span data-stu-id="bd1d0-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="bd1d0-107">這個方法通常由建立自己的執行緒來呼叫的取樣分析工具[ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)目標執行緒暫停執行時，會逐步引導方法，以執行堆疊。</span><span class="sxs-lookup"><span data-stu-id="bd1d0-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="bd1d0-108">藉由呼叫`InitializeCurrentThread`分析工具之後當分析工具會先建立取樣執行緒，可以確保的第一個呼叫期間，否則執行 CLR，每個執行緒延遲初始設定`DoStackSnapshot`現在可能安全地當沒有其他執行緒都在暫止。</span><span class="sxs-lookup"><span data-stu-id="bd1d0-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd1d0-109">`InitializeCurrentThread` 會初始化事先完成工作，會取得鎖定，並可能會發生死結。</span><span class="sxs-lookup"><span data-stu-id="bd1d0-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="bd1d0-110">呼叫`InitializeCurrentThread`只在不有任何暫止的執行緒。</span><span class="sxs-lookup"><span data-stu-id="bd1d0-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd1d0-111">需求</span><span class="sxs-lookup"><span data-stu-id="bd1d0-111">Requirements</span></span>  
 <span data-ttu-id="bd1d0-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd1d0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd1d0-113">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bd1d0-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bd1d0-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd1d0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd1d0-115">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd1d0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd1d0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd1d0-116">See also</span></span>

- [<span data-ttu-id="bd1d0-117">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="bd1d0-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="bd1d0-118">分析介面</span><span class="sxs-lookup"><span data-stu-id="bd1d0-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="bd1d0-119">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="bd1d0-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
