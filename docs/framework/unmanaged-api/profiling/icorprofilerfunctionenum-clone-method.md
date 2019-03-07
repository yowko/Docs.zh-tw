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
ms.openlocfilehash: 3e30cc8ff320c1a4a9a69fb2a07427ef4c8a4149
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485365"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="8cbb3-102">ICorProfilerFunctionEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="8cbb3-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="8cbb3-103">取得介面指標，這一份[ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="8cbb3-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cbb3-104">語法</span><span class="sxs-lookup"><span data-stu-id="8cbb3-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cbb3-105">參數</span><span class="sxs-lookup"><span data-stu-id="8cbb3-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="8cbb3-106">[out]介面指標，其中，依次指向的副本的指標[ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="8cbb3-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="8cbb3-107">列舉值的複本會維護它自己分開這個列舉值的列舉型別狀態。</span><span class="sxs-lookup"><span data-stu-id="8cbb3-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="8cbb3-108">不過，複本的初始資料指標位置會是這個列舉值目前的游標位置相同。</span><span class="sxs-lookup"><span data-stu-id="8cbb3-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cbb3-109">需求</span><span class="sxs-lookup"><span data-stu-id="8cbb3-109">Requirements</span></span>  
 <span data-ttu-id="8cbb3-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="8cbb3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cbb3-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8cbb3-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8cbb3-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8cbb3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cbb3-113">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cbb3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cbb3-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cbb3-114">See also</span></span>
- [<span data-ttu-id="8cbb3-115">ICorProfilerFunctionEnum 介面</span><span class="sxs-lookup"><span data-stu-id="8cbb3-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="8cbb3-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="8cbb3-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
