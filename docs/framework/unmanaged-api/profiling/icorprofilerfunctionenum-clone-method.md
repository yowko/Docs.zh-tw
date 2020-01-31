---
title: ICorProfilerFunctionEnum::Clone 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
ms.openlocfilehash: 2faa7185202b46e77e501d69bb471391a7c6eb68
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864618"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="65502-102">ICorProfilerFunctionEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="65502-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="65502-103">取得此[ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md)介面之複本的介面指標。</span><span class="sxs-lookup"><span data-stu-id="65502-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65502-104">語法</span><span class="sxs-lookup"><span data-stu-id="65502-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65502-105">參數</span><span class="sxs-lookup"><span data-stu-id="65502-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="65502-106">脫銷介面指標的指標，接著指向這個[ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md)介面的複本。</span><span class="sxs-lookup"><span data-stu-id="65502-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="65502-107">列舉值的複本會與此列舉值分開維護自己的列舉狀態。</span><span class="sxs-lookup"><span data-stu-id="65502-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="65502-108">不過，複本的初始游標位置與此列舉值的目前資料指標位置相同。</span><span class="sxs-lookup"><span data-stu-id="65502-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65502-109">需求</span><span class="sxs-lookup"><span data-stu-id="65502-109">Requirements</span></span>  
 <span data-ttu-id="65502-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="65502-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65502-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="65502-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65502-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65502-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65502-113">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65502-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65502-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="65502-114">See also</span></span>

- [<span data-ttu-id="65502-115">ICorProfilerFunctionEnum 介面</span><span class="sxs-lookup"><span data-stu-id="65502-115">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="65502-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="65502-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
