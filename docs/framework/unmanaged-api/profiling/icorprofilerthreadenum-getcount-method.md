---
title: ICorProfilerThreadEnum::GetCount 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type:
- apiref
ms.openlocfilehash: 695b720119854de4645b2f14dd55811f2465504a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447648"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="bd230-102">ICorProfilerThreadEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="bd230-102">ICorProfilerThreadEnum::GetCount Method</span></span>
<span data-ttu-id="bd230-103">取得應用程式所使用的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="bd230-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd230-104">語法</span><span class="sxs-lookup"><span data-stu-id="bd230-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bd230-105">參數</span><span class="sxs-lookup"><span data-stu-id="bd230-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="bd230-106">[out] The number of threads used by the application.</span><span class="sxs-lookup"><span data-stu-id="bd230-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd230-107">需求</span><span class="sxs-lookup"><span data-stu-id="bd230-107">Requirements</span></span>  
 <span data-ttu-id="bd230-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="bd230-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd230-109">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bd230-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bd230-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd230-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd230-111">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd230-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd230-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="bd230-112">See also</span></span>

- [<span data-ttu-id="bd230-113">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="bd230-113">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="bd230-114">分析介面</span><span class="sxs-lookup"><span data-stu-id="bd230-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
