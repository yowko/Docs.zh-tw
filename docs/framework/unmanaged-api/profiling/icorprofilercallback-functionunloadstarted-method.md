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
ms.openlocfilehash: 988843559e55cc4cacd2a40bb3e6ac51721e99b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175157"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="5b670-102">ICorProfilerCallback::FunctionUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="5b670-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="5b670-103">通知探測器運行時已開始卸載函數。</span><span class="sxs-lookup"><span data-stu-id="5b670-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b670-104">語法</span><span class="sxs-lookup"><span data-stu-id="5b670-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);
```  
  
## <a name="parameters"></a><span data-ttu-id="5b670-105">參數</span><span class="sxs-lookup"><span data-stu-id="5b670-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="5b670-106">\[in] 要卸載的函數的 ID。</span><span class="sxs-lookup"><span data-stu-id="5b670-106">\[in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b670-107">備註</span><span class="sxs-lookup"><span data-stu-id="5b670-107">Remarks</span></span>  
 <span data-ttu-id="5b670-108">此方法返回到調用方`functionId`後，參數的值不再有效。</span><span class="sxs-lookup"><span data-stu-id="5b670-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b670-109">需求</span><span class="sxs-lookup"><span data-stu-id="5b670-109">Requirements</span></span>  
 <span data-ttu-id="5b670-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5b670-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b670-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5b670-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b670-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b670-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b670-113">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b670-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b670-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b670-114">See also</span></span>

- [<span data-ttu-id="5b670-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="5b670-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
