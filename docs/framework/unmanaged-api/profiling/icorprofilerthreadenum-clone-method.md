---
title: "ICorProfilerThreadEnum::Clone 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum.Clone
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Clone method [.NET Framework profiling]
ms.assetid: 5a278bc9-88e2-4c69-b035-9d550dd77081
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d40ef6a9a666f06a46713c6295167cf5e0798ce5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="0ef90-102">ICorProfilerThreadEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="0ef90-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="0ef90-103">取得這個複本的介面指標[ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="0ef90-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ef90-104">語法</span><span class="sxs-lookup"><span data-stu-id="0ef90-104">Syntax</span></span>  
  
```  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ef90-105">參數</span><span class="sxs-lookup"><span data-stu-id="0ef90-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="0ef90-106">[out]介面指標，其中，依次指向的副本的指標[ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="0ef90-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="0ef90-107">列舉值的複本會維護其本身列舉狀態分開這個列舉值。</span><span class="sxs-lookup"><span data-stu-id="0ef90-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="0ef90-108">不過，初始資料指標位置的複本時此列舉值的目前游標位置相同的。</span><span class="sxs-lookup"><span data-stu-id="0ef90-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ef90-109">需求</span><span class="sxs-lookup"><span data-stu-id="0ef90-109">Requirements</span></span>  
 <span data-ttu-id="0ef90-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0ef90-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ef90-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0ef90-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0ef90-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ef90-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ef90-113">**.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ef90-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ef90-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="0ef90-114">See Also</span></span>  
 [<span data-ttu-id="0ef90-115">ICorProfilerThreadEnum</span><span class="sxs-lookup"><span data-stu-id="0ef90-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="0ef90-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="0ef90-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
