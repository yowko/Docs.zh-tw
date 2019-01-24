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
ms.openlocfilehash: 8cfb474eaa0a770c2bb101787d34072e4ed98714
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501733"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="1b53b-102">ICorProfilerInfo4::EnumThreads 方法</span><span class="sxs-lookup"><span data-stu-id="1b53b-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="1b53b-103">傳回提供循序逐一查看集合的已分析的處理序中的所有 managed 執行緒的方法的列舉。</span><span class="sxs-lookup"><span data-stu-id="1b53b-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b53b-104">語法</span><span class="sxs-lookup"><span data-stu-id="1b53b-104">Syntax</span></span>  
  
```  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b53b-105">參數</span><span class="sxs-lookup"><span data-stu-id="1b53b-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="1b53b-106">[out]指標[ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="1b53b-106">[out] A pointer to an [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1b53b-107">備註</span><span class="sxs-lookup"><span data-stu-id="1b53b-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b53b-108">需求</span><span class="sxs-lookup"><span data-stu-id="1b53b-108">Requirements</span></span>  
 <span data-ttu-id="1b53b-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="1b53b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b53b-110">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1b53b-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1b53b-111">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b53b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b53b-112">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b53b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b53b-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1b53b-113">See also</span></span>
- [<span data-ttu-id="1b53b-114">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="1b53b-114">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="1b53b-115">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="1b53b-115">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="1b53b-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="1b53b-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="1b53b-117">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="1b53b-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
