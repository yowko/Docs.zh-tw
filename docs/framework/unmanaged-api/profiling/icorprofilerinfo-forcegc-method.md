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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5672d1b89b4260d1ebfbf444deb2702f215a0e95
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078079"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="65ef3-102">ICorProfilerInfo::ForceGC 方法</span><span class="sxs-lookup"><span data-stu-id="65ef3-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="65ef3-103">強制記憶體回收發生 common language runtime (CLR) 中。</span><span class="sxs-lookup"><span data-stu-id="65ef3-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65ef3-104">語法</span><span class="sxs-lookup"><span data-stu-id="65ef3-104">Syntax</span></span>  
  
```  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="65ef3-105">備註</span><span class="sxs-lookup"><span data-stu-id="65ef3-105">Remarks</span></span>  
 <span data-ttu-id="65ef3-106">`ForceGC`必須呼叫方法，只能從從未執行 managed 程式碼和其堆疊上沒有任何分析工具回呼的執行緒。</span><span class="sxs-lookup"><span data-stu-id="65ef3-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="65ef3-107">最方便的實作會建立個別的執行緒內呼叫程式碼剖析工具`ForceGC`時收到信號。</span><span class="sxs-lookup"><span data-stu-id="65ef3-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65ef3-108">需求</span><span class="sxs-lookup"><span data-stu-id="65ef3-108">Requirements</span></span>  
 <span data-ttu-id="65ef3-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="65ef3-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65ef3-110">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="65ef3-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65ef3-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65ef3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65ef3-112">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65ef3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ef3-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65ef3-113">See also</span></span>

- [<span data-ttu-id="65ef3-114">ICorProfilerInfo 介面</span><span class="sxs-lookup"><span data-stu-id="65ef3-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
