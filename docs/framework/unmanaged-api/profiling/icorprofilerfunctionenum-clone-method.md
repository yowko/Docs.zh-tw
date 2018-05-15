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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ce5d5187ee4082bb851fa24bbcda2b099e37b89f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="7ce73-102">ICorProfilerFunctionEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="7ce73-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="7ce73-103">取得這個複本的介面指標[ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="7ce73-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ce73-104">語法</span><span class="sxs-lookup"><span data-stu-id="7ce73-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7ce73-105">參數</span><span class="sxs-lookup"><span data-stu-id="7ce73-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="7ce73-106">[out]介面指標，其中，依次指向的副本的指標[ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="7ce73-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="7ce73-107">列舉值的複本會維護其本身列舉狀態分開這個列舉值。</span><span class="sxs-lookup"><span data-stu-id="7ce73-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="7ce73-108">不過的複本初始的游標位置是與此列舉值的目前游標位置相同。</span><span class="sxs-lookup"><span data-stu-id="7ce73-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ce73-109">需求</span><span class="sxs-lookup"><span data-stu-id="7ce73-109">Requirements</span></span>  
 <span data-ttu-id="7ce73-110">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7ce73-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ce73-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7ce73-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7ce73-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ce73-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ce73-113">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ce73-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ce73-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ce73-114">See Also</span></span>  
 [<span data-ttu-id="7ce73-115">ICorProfilerFunctionEnum 介面</span><span class="sxs-lookup"><span data-stu-id="7ce73-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="7ce73-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="7ce73-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
