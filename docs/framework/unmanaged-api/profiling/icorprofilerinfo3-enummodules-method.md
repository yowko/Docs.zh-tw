---
title: ICorProfilerInfo3::EnumModules 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumModules Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumModules
helpviewer_keywords:
- ICorProfilerInfo3::EnumModules method [.NET Framework profiling]
- EnumModules method [.NET Framework profiling]
ms.assetid: 1bf00b42-69da-4019-91b3-bf88026e83fb
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be5d05c34272b9fa5755b4d0e22fa9094707c5ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703552"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="07839-102">ICorProfilerInfo3::EnumModules 方法</span><span class="sxs-lookup"><span data-stu-id="07839-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="07839-103">傳回提供循序逐一查看 Managed 模組集合方法的列舉，其中該模組被載入至應用程式中。</span><span class="sxs-lookup"><span data-stu-id="07839-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07839-104">語法</span><span class="sxs-lookup"><span data-stu-id="07839-104">Syntax</span></span>  
  
```  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07839-105">參數</span><span class="sxs-lookup"><span data-stu-id="07839-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="07839-106">[out]指標[ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)介面。</span><span class="sxs-lookup"><span data-stu-id="07839-106">[out] A pointer to an [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="07839-107">備註</span><span class="sxs-lookup"><span data-stu-id="07839-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07839-108">需求</span><span class="sxs-lookup"><span data-stu-id="07839-108">Requirements</span></span>  
 <span data-ttu-id="07839-109">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="07839-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07839-110">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="07839-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07839-111">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07839-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07839-112">**.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07839-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07839-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="07839-113">See also</span></span>

- [<span data-ttu-id="07839-114">ICorProfilerFunctionEnum 介面</span><span class="sxs-lookup"><span data-stu-id="07839-114">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="07839-115">ICorProfilerInfo3 介面</span><span class="sxs-lookup"><span data-stu-id="07839-115">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="07839-116">分析介面</span><span class="sxs-lookup"><span data-stu-id="07839-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="07839-117">程式碼剖析</span><span class="sxs-lookup"><span data-stu-id="07839-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
