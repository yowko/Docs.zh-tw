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
ms.openlocfilehash: 9048d314404859a4264621a5da91c43c525027f9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868196"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="e76da-102">ICorProfilerThreadEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="e76da-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="e76da-103">取得此[ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md)介面之複本的介面指標。</span><span class="sxs-lookup"><span data-stu-id="e76da-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e76da-104">語法</span><span class="sxs-lookup"><span data-stu-id="e76da-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e76da-105">參數</span><span class="sxs-lookup"><span data-stu-id="e76da-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="e76da-106">脫銷介面指標的指標，接著指向這個[ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md)介面的複本。</span><span class="sxs-lookup"><span data-stu-id="e76da-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="e76da-107">列舉值的複本會與此列舉值分開維護自己的列舉狀態。</span><span class="sxs-lookup"><span data-stu-id="e76da-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="e76da-108">不過，複本的初始游標位置與列舉值的目前資料指標位置相同。</span><span class="sxs-lookup"><span data-stu-id="e76da-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e76da-109">需求</span><span class="sxs-lookup"><span data-stu-id="e76da-109">Requirements</span></span>  
 <span data-ttu-id="e76da-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e76da-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e76da-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e76da-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e76da-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e76da-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e76da-113">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e76da-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e76da-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="e76da-114">See also</span></span>

- [<span data-ttu-id="e76da-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="e76da-115">ICorProfilerThreadEnum</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="e76da-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="e76da-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
