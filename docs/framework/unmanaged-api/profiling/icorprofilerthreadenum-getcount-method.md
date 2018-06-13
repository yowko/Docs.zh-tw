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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b803c83b905df47b3957e07c0d64e7ce6f6d303
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455474"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="f93c1-102">ICorProfilerThreadEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="f93c1-102">ICorProfilerThreadEnum::GetCount Method</span></span>
<span data-ttu-id="f93c1-103">取得應用程式所使用的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="f93c1-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f93c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="f93c1-104">Syntax</span></span>  
  
```  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f93c1-105">參數</span><span class="sxs-lookup"><span data-stu-id="f93c1-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="f93c1-106">[out]應用程式所使用的執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="f93c1-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f93c1-107">需求</span><span class="sxs-lookup"><span data-stu-id="f93c1-107">Requirements</span></span>  
 <span data-ttu-id="f93c1-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f93c1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f93c1-109">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f93c1-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f93c1-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f93c1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f93c1-111">**.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f93c1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f93c1-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f93c1-112">See Also</span></span>  
 [<span data-ttu-id="f93c1-113">ICorProfilerThreadEnum 介面</span><span class="sxs-lookup"><span data-stu-id="f93c1-113">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="f93c1-114">分析介面</span><span class="sxs-lookup"><span data-stu-id="f93c1-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
