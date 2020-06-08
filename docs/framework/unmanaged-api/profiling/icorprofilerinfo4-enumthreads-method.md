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
ms.openlocfilehash: d42c86a458661d3559f99235a6d5b208c82d1963
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502804"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="b2d39-102">ICorProfilerInfo4::EnumThreads 方法</span><span class="sxs-lookup"><span data-stu-id="b2d39-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="b2d39-103">傳回列舉值，提供逐步逐一查看已分析進程中所有 managed 執行緒集合的方法。</span><span class="sxs-lookup"><span data-stu-id="b2d39-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2d39-104">語法</span><span class="sxs-lookup"><span data-stu-id="b2d39-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2d39-105">參數</span><span class="sxs-lookup"><span data-stu-id="b2d39-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="b2d39-106">脫銷指向[ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md)介面的指標。</span><span class="sxs-lookup"><span data-stu-id="b2d39-106">[out] A pointer to an [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2d39-107">備註</span><span class="sxs-lookup"><span data-stu-id="b2d39-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2d39-108">需求</span><span class="sxs-lookup"><span data-stu-id="b2d39-108">Requirements</span></span>  
 <span data-ttu-id="b2d39-109">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b2d39-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2d39-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b2d39-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b2d39-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2d39-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2d39-112">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2d39-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2d39-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b2d39-113">See also</span></span>

- [<span data-ttu-id="b2d39-114">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="b2d39-114">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="b2d39-115">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="b2d39-115">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="b2d39-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="b2d39-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="b2d39-117">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="b2d39-117">Profiling</span></span>](index.md)
