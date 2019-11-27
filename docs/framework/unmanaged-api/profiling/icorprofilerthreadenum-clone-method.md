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
ms.openlocfilehash: ca29655d1d0eb819dfe8b5f9910cd20ef47843c4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74441539"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="8f9f8-102">ICorProfilerThreadEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="8f9f8-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="8f9f8-103">取得此[ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)介面之複本的介面指標。</span><span class="sxs-lookup"><span data-stu-id="8f9f8-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f9f8-104">語法</span><span class="sxs-lookup"><span data-stu-id="8f9f8-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f9f8-105">參數</span><span class="sxs-lookup"><span data-stu-id="8f9f8-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="8f9f8-106">脫銷介面指標的指標，接著指向這個[ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)介面的複本。</span><span class="sxs-lookup"><span data-stu-id="8f9f8-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="8f9f8-107">列舉值的複本會與此列舉值分開維護自己的列舉狀態。</span><span class="sxs-lookup"><span data-stu-id="8f9f8-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="8f9f8-108">不過，複本的初始游標位置與列舉值的目前資料指標位置相同。</span><span class="sxs-lookup"><span data-stu-id="8f9f8-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f9f8-109">需求</span><span class="sxs-lookup"><span data-stu-id="8f9f8-109">Requirements</span></span>  
 <span data-ttu-id="8f9f8-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8f9f8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f9f8-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8f9f8-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8f9f8-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8f9f8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f9f8-113">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f9f8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f9f8-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f9f8-114">See also</span></span>

- [<span data-ttu-id="8f9f8-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="8f9f8-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="8f9f8-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="8f9f8-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
