---
title: "ICorProfilerModuleEnum::Clone 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum.Clone Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d6e5da0912c1926fea4afe513e7140055052416
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="7b588-102">ICorProfilerModuleEnum::Clone 方法</span><span class="sxs-lookup"><span data-stu-id="7b588-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="7b588-103">取得這個複本的介面指標[ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="7b588-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b588-104">語法</span><span class="sxs-lookup"><span data-stu-id="7b588-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7b588-105">參數</span><span class="sxs-lookup"><span data-stu-id="7b588-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="7b588-106">[out]介面指標，再依序指向的副本的指標[ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="7b588-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="7b588-107">列舉值的複本會維護其本身列舉狀態分開這個列舉值。</span><span class="sxs-lookup"><span data-stu-id="7b588-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="7b588-108">不過的複本初始的游標位置是與此列舉值的目前游標位置相同。</span><span class="sxs-lookup"><span data-stu-id="7b588-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b588-109">需求</span><span class="sxs-lookup"><span data-stu-id="7b588-109">Requirements</span></span>  
 <span data-ttu-id="7b588-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="7b588-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b588-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7b588-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7b588-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b588-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b588-113">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b588-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b588-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="7b588-114">See Also</span></span>  
 [<span data-ttu-id="7b588-115">ICorProfilerModuleEnum 介面</span><span class="sxs-lookup"><span data-stu-id="7b588-115">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [<span data-ttu-id="7b588-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="7b588-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
