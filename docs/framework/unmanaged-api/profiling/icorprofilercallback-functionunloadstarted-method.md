---
title: "ICorProfilerCallback::FunctionUnloadStarted 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 957b5a89dbb3e780b0e5512afe405e669fdbecce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="d1085-102">ICorProfilerCallback::FunctionUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="d1085-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="d1085-103">通知分析工具執行階段已開始卸載函式。</span><span class="sxs-lookup"><span data-stu-id="d1085-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1085-104">語法</span><span class="sxs-lookup"><span data-stu-id="d1085-104">Syntax</span></span>  
  
```  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="d1085-105">參數</span><span class="sxs-lookup"><span data-stu-id="d1085-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="d1085-106">[in]正在解除載入的函式 ID。</span><span class="sxs-lookup"><span data-stu-id="d1085-106">[in] The ID of the function that is being unloaded.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1085-107">備註</span><span class="sxs-lookup"><span data-stu-id="d1085-107">Remarks</span></span>  
 <span data-ttu-id="d1085-108">值`functionId`參數之後，這個方法會傳回給呼叫者已不再有效。</span><span class="sxs-lookup"><span data-stu-id="d1085-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1085-109">需求</span><span class="sxs-lookup"><span data-stu-id="d1085-109">Requirements</span></span>  
 <span data-ttu-id="d1085-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="d1085-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1085-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d1085-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d1085-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1085-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1085-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1085-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1085-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="d1085-114">See Also</span></span>  
 [<span data-ttu-id="d1085-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="d1085-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
