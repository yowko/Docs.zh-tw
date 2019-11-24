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
ms.openlocfilehash: a212a0499b1091f1c77b52951ecef2cb2cace4df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447842"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="bfb4c-102">ICorProfilerFunctionEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="bfb4c-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="bfb4c-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="bfb4c-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfb4c-104">語法</span><span class="sxs-lookup"><span data-stu-id="bfb4c-104">Syntax</span></span>  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bfb4c-105">參數</span><span class="sxs-lookup"><span data-stu-id="bfb4c-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="bfb4c-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="bfb4c-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="bfb4c-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span><span class="sxs-lookup"><span data-stu-id="bfb4c-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="bfb4c-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span><span class="sxs-lookup"><span data-stu-id="bfb4c-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfb4c-109">需求</span><span class="sxs-lookup"><span data-stu-id="bfb4c-109">Requirements</span></span>  
 <span data-ttu-id="bfb4c-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bfb4c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfb4c-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bfb4c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bfb4c-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfb4c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfb4c-113">**.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfb4c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfb4c-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="bfb4c-114">See also</span></span>

- [<span data-ttu-id="bfb4c-115">ICorProfilerFunctionEnum 介面</span><span class="sxs-lookup"><span data-stu-id="bfb4c-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="bfb4c-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="bfb4c-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
