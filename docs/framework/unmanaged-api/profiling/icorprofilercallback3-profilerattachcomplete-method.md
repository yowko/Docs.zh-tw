---
title: ICorProfilerCallback3::ProfilerAttachComplete 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 26c9c85f22f9d8201214dc56f32718e055a97801
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779259"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="31308-102">ICorProfilerCallback3::ProfilerAttachComplete 方法</span><span class="sxs-lookup"><span data-stu-id="31308-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="31308-103">由 common language runtime (CLR) 來指出分析工具現在可以呼叫呼叫[ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)並[ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)更新方法。</span><span class="sxs-lookup"><span data-stu-id="31308-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31308-104">語法</span><span class="sxs-lookup"><span data-stu-id="31308-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="31308-105">備註</span><span class="sxs-lookup"><span data-stu-id="31308-105">Remarks</span></span>  
 <span data-ttu-id="31308-106">`ProfilerAttachComplete`回呼之後，會發出[ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="31308-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="31308-107">這表示：</span><span class="sxs-lookup"><span data-stu-id="31308-107">It indicates the following:</span></span>  
  
- <span data-ttu-id="31308-108">`InitializeForAttach` 中分析工具所要求的回呼已啟動。</span><span class="sxs-lookup"><span data-stu-id="31308-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="31308-109">分析工具現在可以對關聯的 ID 執行更新，而不必擔心遺漏通知。</span><span class="sxs-lookup"><span data-stu-id="31308-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="31308-110">CLR 會忽略這個回呼的傳回值。</span><span class="sxs-lookup"><span data-stu-id="31308-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31308-111">需求</span><span class="sxs-lookup"><span data-stu-id="31308-111">Requirements</span></span>  
 <span data-ttu-id="31308-112">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="31308-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31308-113">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="31308-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31308-114">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="31308-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31308-115">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31308-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31308-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="31308-116">See also</span></span>

- [<span data-ttu-id="31308-117">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="31308-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="31308-118">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="31308-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="31308-119">分析介面</span><span class="sxs-lookup"><span data-stu-id="31308-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="31308-120">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="31308-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
