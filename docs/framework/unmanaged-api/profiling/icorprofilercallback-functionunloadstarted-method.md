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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6dd7792fe298aa1950b23053a7c5cd576b62e7b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755889"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="ae748-102">ICorProfilerCallback::FunctionUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="ae748-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="ae748-103">通知分析工具執行階段已啟動卸載函式。</span><span class="sxs-lookup"><span data-stu-id="ae748-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae748-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae748-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="ae748-105">參數</span><span class="sxs-lookup"><span data-stu-id="ae748-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="ae748-106">[in]正在卸載模組函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ae748-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae748-107">備註</span><span class="sxs-lookup"><span data-stu-id="ae748-107">Remarks</span></span>  
 <span data-ttu-id="ae748-108">值`functionId`參數之後，這個方法會傳回給呼叫者已不再有效。</span><span class="sxs-lookup"><span data-stu-id="ae748-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae748-109">需求</span><span class="sxs-lookup"><span data-stu-id="ae748-109">Requirements</span></span>  
 <span data-ttu-id="ae748-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ae748-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae748-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ae748-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ae748-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae748-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae748-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae748-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae748-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae748-114">See also</span></span>

- [<span data-ttu-id="ae748-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ae748-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
