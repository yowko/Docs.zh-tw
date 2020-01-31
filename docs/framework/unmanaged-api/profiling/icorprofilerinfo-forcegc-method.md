---
title: ICorProfilerInfo::ForceGC 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
ms.openlocfilehash: e1fe38419cda328c919f0840d51cf6336919aa60
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864189"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="9fb9f-102">ICorProfilerInfo::ForceGC 方法</span><span class="sxs-lookup"><span data-stu-id="9fb9f-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="9fb9f-103">強制在 common language runtime （CLR）中進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="9fb9f-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fb9f-104">語法</span><span class="sxs-lookup"><span data-stu-id="9fb9f-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="9fb9f-105">備註</span><span class="sxs-lookup"><span data-stu-id="9fb9f-105">Remarks</span></span>  
 <span data-ttu-id="9fb9f-106">只能從從未執行 managed 程式碼，且在其堆疊上沒有任何分析工具回呼的執行緒呼叫 `ForceGC` 方法。</span><span class="sxs-lookup"><span data-stu-id="9fb9f-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="9fb9f-107">最方便的執行方式是在分析工具內建立個別的執行緒，以在收到信號時呼叫 `ForceGC`。</span><span class="sxs-lookup"><span data-stu-id="9fb9f-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fb9f-108">需求</span><span class="sxs-lookup"><span data-stu-id="9fb9f-108">Requirements</span></span>  
 <span data-ttu-id="9fb9f-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9fb9f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fb9f-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9fb9f-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9fb9f-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fb9f-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fb9f-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fb9f-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fb9f-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="9fb9f-113">See also</span></span>

- [<span data-ttu-id="9fb9f-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="9fb9f-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
