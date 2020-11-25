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
ms.openlocfilehash: df0e66c8563404d7de4f1e11f41483f2f61f519c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721552"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="1f802-102">ICorProfilerInfo4::EnumThreads 方法</span><span class="sxs-lookup"><span data-stu-id="1f802-102">ICorProfilerInfo4::EnumThreads Method</span></span>

<span data-ttu-id="1f802-103">傳回列舉值，這個列舉值會提供方法，以依序逐一查看已分析進程中所有 managed 執行緒的集合。</span><span class="sxs-lookup"><span data-stu-id="1f802-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f802-104">語法</span><span class="sxs-lookup"><span data-stu-id="1f802-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f802-105">參數</span><span class="sxs-lookup"><span data-stu-id="1f802-105">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="1f802-106">擴展 [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) 介面的指標。</span><span class="sxs-lookup"><span data-stu-id="1f802-106">[out] A pointer to an [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f802-107">備註</span><span class="sxs-lookup"><span data-stu-id="1f802-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f802-108">需求</span><span class="sxs-lookup"><span data-stu-id="1f802-108">Requirements</span></span>  

 <span data-ttu-id="1f802-109">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1f802-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f802-110">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1f802-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1f802-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f802-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f802-112">**.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f802-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f802-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f802-113">See also</span></span>

- [<span data-ttu-id="1f802-114">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="1f802-114">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="1f802-115">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="1f802-115">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="1f802-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="1f802-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="1f802-117">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="1f802-117">Profiling</span></span>](index.md)
