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
ms.openlocfilehash: bd0a4149b6dc6023579e8bc5b40751d23416e3a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683846"
---
# <a name="icorprofilerinfo4enumthreads-method"></a><span data-ttu-id="2c06e-102">ICorProfilerInfo4::EnumThreads 方法</span><span class="sxs-lookup"><span data-stu-id="2c06e-102">ICorProfilerInfo4::EnumThreads Method</span></span>
<span data-ttu-id="2c06e-103">傳回提供循序逐一查看集合的已分析的處理序中的所有 managed 執行緒的方法的列舉。</span><span class="sxs-lookup"><span data-stu-id="2c06e-103">Returns an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c06e-104">語法</span><span class="sxs-lookup"><span data-stu-id="2c06e-104">Syntax</span></span>  
  
```  
HRESULT EnumThreads([out]  
            ICorProfilerThreadEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c06e-105">參數</span><span class="sxs-lookup"><span data-stu-id="2c06e-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="2c06e-106">[out]指標[ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="2c06e-106">[out] A pointer to an [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c06e-107">備註</span><span class="sxs-lookup"><span data-stu-id="2c06e-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c06e-108">需求</span><span class="sxs-lookup"><span data-stu-id="2c06e-108">Requirements</span></span>  
 <span data-ttu-id="2c06e-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2c06e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c06e-110">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2c06e-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c06e-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c06e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c06e-112">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c06e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c06e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c06e-113">See also</span></span>

- [<span data-ttu-id="2c06e-114">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="2c06e-114">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="2c06e-115">ICorProfilerInfo4 介面</span><span class="sxs-lookup"><span data-stu-id="2c06e-115">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="2c06e-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="2c06e-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="2c06e-117">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="2c06e-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
