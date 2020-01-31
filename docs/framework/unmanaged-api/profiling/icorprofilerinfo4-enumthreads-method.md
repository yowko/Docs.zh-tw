---
title: ICorProfilerInfo4::EnumThreads 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.EnumThreads
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::EnumThreads
helpviewer_keywords:
- ICorProfilerInfo4::EnumThreads method [.NET Framework profiling]
- EnumThreads method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: bca7a5b4-c207-4894-918c-0733926296dd
topic_type:
- apiref
ms.openlocfilehash: 5bea1b75e94d8011d3582d4f07d36bbc7a560502
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862213"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="24aa2-102">ICorProfilerInfo4::EnumThreads 方法</span><span class="sxs-lookup"><span data-stu-id="24aa2-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="24aa2-103">傳回列舉值，提供逐步逐一查看已分析進程中所有 managed 執行緒集合的方法。</span><span class="sxs-lookup"><span data-stu-id="24aa2-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24aa2-104">語法</span><span class="sxs-lookup"><span data-stu-id="24aa2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24aa2-105">參數</span><span class="sxs-lookup"><span data-stu-id="24aa2-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="24aa2-106">脫銷指向[ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="24aa2-106">[out] A pointer to an [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24aa2-107">備註</span><span class="sxs-lookup"><span data-stu-id="24aa2-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24aa2-108">需求</span><span class="sxs-lookup"><span data-stu-id="24aa2-108">Requirements</span></span>  
 <span data-ttu-id="24aa2-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="24aa2-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24aa2-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="24aa2-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24aa2-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24aa2-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24aa2-112">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24aa2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24aa2-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="24aa2-113">See also</span></span>

- [<span data-ttu-id="24aa2-114">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="24aa2-114">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="24aa2-115">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="24aa2-115">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="24aa2-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="24aa2-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="24aa2-117">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="24aa2-117">Profiling</span></span>](index.md)
