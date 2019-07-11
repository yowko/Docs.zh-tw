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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3d4cffc7c407db6acd15462e1e00769101e44b40
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780861"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="ccc90-102">ICorProfilerInfo4::EnumThreads 方法</span><span class="sxs-lookup"><span data-stu-id="ccc90-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="ccc90-103">傳回提供循序逐一查看集合的已分析的處理序中的所有 managed 執行緒的方法的列舉。</span><span class="sxs-lookup"><span data-stu-id="ccc90-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccc90-104">語法</span><span class="sxs-lookup"><span data-stu-id="ccc90-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccc90-105">參數</span><span class="sxs-lookup"><span data-stu-id="ccc90-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="ccc90-106">[out]指標[ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="ccc90-106">[out] A pointer to an [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccc90-107">備註</span><span class="sxs-lookup"><span data-stu-id="ccc90-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccc90-108">需求</span><span class="sxs-lookup"><span data-stu-id="ccc90-108">Requirements</span></span>  
 <span data-ttu-id="ccc90-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ccc90-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccc90-110">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ccc90-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ccc90-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccc90-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccc90-112">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccc90-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccc90-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccc90-113">See also</span></span>

- [<span data-ttu-id="ccc90-114">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="ccc90-114">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="ccc90-115">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="ccc90-115">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="ccc90-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="ccc90-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ccc90-117">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="ccc90-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
