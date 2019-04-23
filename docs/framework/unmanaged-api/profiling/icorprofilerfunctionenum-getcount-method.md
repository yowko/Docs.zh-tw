---
title: ICorProfilerFunctionEnum::GetCount 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.GetCount Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::GetCount
helpviewer_keywords:
- ICorProfilerFunctionEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 62ec65e3-3e9d-400b-ae61-d24b8963995b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5061750489c74e0385f2ce020c88518604b3167
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169282"
---
# <a name="icorprofilerfunctionenumgetcount-method"></a><span data-ttu-id="ab80b-102">ICorProfilerFunctionEnum::GetCount 方法</span><span class="sxs-lookup"><span data-stu-id="ab80b-102">ICorProfilerFunctionEnum::GetCount Method</span></span>
<span data-ttu-id="ab80b-103">取得應用程式已載入的或分析工具強制載入的函式數目。</span><span class="sxs-lookup"><span data-stu-id="ab80b-103">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab80b-104">語法</span><span class="sxs-lookup"><span data-stu-id="ab80b-104">Syntax</span></span>  
  
```  
HRESULT GetCount([out] ULONG * pcelt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab80b-105">參數</span><span class="sxs-lookup"><span data-stu-id="ab80b-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ab80b-106">[out]已載入的函式數目。</span><span class="sxs-lookup"><span data-stu-id="ab80b-106">[out] The number of functions that were loaded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab80b-107">需求</span><span class="sxs-lookup"><span data-stu-id="ab80b-107">Requirements</span></span>  
 <span data-ttu-id="ab80b-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ab80b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab80b-109">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ab80b-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ab80b-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab80b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab80b-111">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab80b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab80b-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ab80b-112">See also</span></span>

- [<span data-ttu-id="ab80b-113">ICorProfilerFunctionEnum 介面</span><span class="sxs-lookup"><span data-stu-id="ab80b-113">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="ab80b-114">分析介面</span><span class="sxs-lookup"><span data-stu-id="ab80b-114">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
