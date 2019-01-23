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
ms.openlocfilehash: 5b9d3224370dac0f8a52affef9201e5cbec43de0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54547432"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="67236-102">ICorProfilerThreadEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="67236-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="67236-103">取得介面指標，這一份[ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="67236-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="67236-104">語法</span><span class="sxs-lookup"><span data-stu-id="67236-104">Syntax</span></span>  
  
```  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="67236-105">參數</span><span class="sxs-lookup"><span data-stu-id="67236-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="67236-106">[out]介面指標，其中，依次指向的副本的指標[ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="67236-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="67236-107">列舉值的複本會維護它自己分開這個列舉值的列舉型別狀態。</span><span class="sxs-lookup"><span data-stu-id="67236-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="67236-108">不過，初始的資料指標位置是複本的這個目前的游標位置的列舉值相同。</span><span class="sxs-lookup"><span data-stu-id="67236-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67236-109">需求</span><span class="sxs-lookup"><span data-stu-id="67236-109">Requirements</span></span>  
 <span data-ttu-id="67236-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="67236-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67236-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="67236-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="67236-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67236-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67236-113">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67236-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67236-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67236-114">See also</span></span>
- [<span data-ttu-id="67236-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="67236-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="67236-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="67236-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
