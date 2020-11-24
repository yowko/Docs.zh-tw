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
ms.openlocfilehash: 75f2db5e5489f02dcae3db0c3e6af19c922e0745
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95669191"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="9e497-102">ICorProfilerInfo::ForceGC 方法</span><span class="sxs-lookup"><span data-stu-id="9e497-102">ICorProfilerInfo::ForceGC Method</span></span>

<span data-ttu-id="9e497-103">在 common language runtime (CLR) 中強制進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="9e497-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e497-104">語法</span><span class="sxs-lookup"><span data-stu-id="9e497-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="9e497-105">備註</span><span class="sxs-lookup"><span data-stu-id="9e497-105">Remarks</span></span>  

 <span data-ttu-id="9e497-106">您 `ForceGC` 只能從從未執行 managed 程式碼的執行緒呼叫方法，而且它的堆疊上沒有任何 profiler 回呼。</span><span class="sxs-lookup"><span data-stu-id="9e497-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="9e497-107">最方便的執行是在分析工具內建立個別的執行緒，以在 `ForceGC` 收到信號時呼叫。</span><span class="sxs-lookup"><span data-stu-id="9e497-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e497-108">需求</span><span class="sxs-lookup"><span data-stu-id="9e497-108">Requirements</span></span>  

 <span data-ttu-id="9e497-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="9e497-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e497-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9e497-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9e497-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e497-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e497-112">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e497-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e497-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9e497-113">See also</span></span>

- [<span data-ttu-id="9e497-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="9e497-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
