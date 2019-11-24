---
title: ICorProfilerCallback::FunctionUnloadStarted 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.FunctionUnloadStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::FunctionUnloadStarted
helpviewer_keywords:
- FunctionUnloadStarted method [.NET Framework profiling]
- ICorProfilerCallback::FunctionUnloadStarted method [.NET Framework profiling]
ms.assetid: d6a5fa8b-09c6-47a5-b60e-6cf2e355df30
topic_type:
- apiref
ms.openlocfilehash: f57a3ed70267de65daed85305ad7d623b4ca0337
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448025"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="e9a6e-102">ICorProfilerCallback::FunctionUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="e9a6e-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="e9a6e-103">Notifies the profiler that the runtime has started to unload a function.</span><span class="sxs-lookup"><span data-stu-id="e9a6e-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9a6e-104">語法</span><span class="sxs-lookup"><span data-stu-id="e9a6e-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="e9a6e-105">參數</span><span class="sxs-lookup"><span data-stu-id="e9a6e-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="e9a6e-106">[in] The ID of the function that is being unloaded.</span><span class="sxs-lookup"><span data-stu-id="e9a6e-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9a6e-107">備註</span><span class="sxs-lookup"><span data-stu-id="e9a6e-107">Remarks</span></span>  
 <span data-ttu-id="e9a6e-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span><span class="sxs-lookup"><span data-stu-id="e9a6e-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9a6e-109">需求</span><span class="sxs-lookup"><span data-stu-id="e9a6e-109">Requirements</span></span>  
 <span data-ttu-id="e9a6e-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e9a6e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9a6e-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e9a6e-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e9a6e-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9a6e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9a6e-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9a6e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a6e-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="e9a6e-114">See also</span></span>

- [<span data-ttu-id="e9a6e-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="e9a6e-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
