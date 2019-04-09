---
title: ICorProfilerThreadEnum::Clone 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Clone method [.NET Framework profiling]
ms.assetid: 5a278bc9-88e2-4c69-b035-9d550dd77081
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0301334621a2e393a59e7cc34f2964450a81213f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074166"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="e3667-102">ICorProfilerThreadEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="e3667-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="e3667-103">取得介面指標，這一份[ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="e3667-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3667-104">語法</span><span class="sxs-lookup"><span data-stu-id="e3667-104">Syntax</span></span>  
  
```  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3667-105">參數</span><span class="sxs-lookup"><span data-stu-id="e3667-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="e3667-106">[out]介面指標，其中，依次指向的副本的指標[ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="e3667-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="e3667-107">列舉值的複本會維護它自己分開這個列舉值的列舉型別狀態。</span><span class="sxs-lookup"><span data-stu-id="e3667-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="e3667-108">不過，初始的資料指標位置是複本的這個目前的游標位置的列舉值相同。</span><span class="sxs-lookup"><span data-stu-id="e3667-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3667-109">需求</span><span class="sxs-lookup"><span data-stu-id="e3667-109">Requirements</span></span>  
 <span data-ttu-id="e3667-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e3667-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3667-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e3667-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e3667-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e3667-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e3667-113">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="e3667-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e3667-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3667-114">See also</span></span>

- [<span data-ttu-id="e3667-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="e3667-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="e3667-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="e3667-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
