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
ms.openlocfilehash: ded15608337d040ab58cb5be45deac4711668ac3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576170"
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="eb526-102">ICorProfilerFunctionEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="eb526-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="eb526-103">取得介面指標，這一份[ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="eb526-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb526-104">語法</span><span class="sxs-lookup"><span data-stu-id="eb526-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb526-105">參數</span><span class="sxs-lookup"><span data-stu-id="eb526-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="eb526-106">[out]介面指標，其中，依次指向的副本的指標[ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="eb526-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="eb526-107">列舉值的複本會維護它自己分開這個列舉值的列舉型別狀態。</span><span class="sxs-lookup"><span data-stu-id="eb526-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="eb526-108">不過，複本的初始資料指標位置會是這個列舉值目前的游標位置相同。</span><span class="sxs-lookup"><span data-stu-id="eb526-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb526-109">需求</span><span class="sxs-lookup"><span data-stu-id="eb526-109">Requirements</span></span>  
 <span data-ttu-id="eb526-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="eb526-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb526-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eb526-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eb526-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eb526-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb526-113">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb526-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb526-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eb526-114">See also</span></span>
- [<span data-ttu-id="eb526-115">ICorProfilerFunctionEnum 介面</span><span class="sxs-lookup"><span data-stu-id="eb526-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="eb526-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="eb526-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
