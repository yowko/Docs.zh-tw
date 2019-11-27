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
ms.openlocfilehash: 9f97da4e68d4b76178198e91c3fb8f08b56dda7b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448195"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="15e5e-102">ICorProfilerInfo::ForceGC 方法</span><span class="sxs-lookup"><span data-stu-id="15e5e-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="15e5e-103">強制在 common language runtime （CLR）中進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="15e5e-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15e5e-104">語法</span><span class="sxs-lookup"><span data-stu-id="15e5e-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="15e5e-105">備註</span><span class="sxs-lookup"><span data-stu-id="15e5e-105">Remarks</span></span>  
 <span data-ttu-id="15e5e-106">只能從從未執行 managed 程式碼，且在其堆疊上沒有任何分析工具回呼的執行緒呼叫 `ForceGC` 方法。</span><span class="sxs-lookup"><span data-stu-id="15e5e-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="15e5e-107">最方便的執行方式是在分析工具內建立個別的執行緒，以在收到信號時呼叫 `ForceGC`。</span><span class="sxs-lookup"><span data-stu-id="15e5e-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15e5e-108">需求</span><span class="sxs-lookup"><span data-stu-id="15e5e-108">Requirements</span></span>  
 <span data-ttu-id="15e5e-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="15e5e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15e5e-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="15e5e-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="15e5e-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15e5e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15e5e-112">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15e5e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15e5e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15e5e-113">See also</span></span>

- [<span data-ttu-id="15e5e-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="15e5e-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
