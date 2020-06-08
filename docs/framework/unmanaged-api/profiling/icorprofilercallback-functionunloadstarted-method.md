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
ms.openlocfilehash: 320aaf074452fd02cd8ee8e80194a4c35b831eb4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503376"
---
# <a name="icorprofilercallbackfunctionunloadstarted-method"></a><span data-ttu-id="914a7-102">ICorProfilerCallback::FunctionUnloadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="914a7-102">ICorProfilerCallback::FunctionUnloadStarted Method</span></span>
<span data-ttu-id="914a7-103">通知分析工具，執行時間已開始卸載函數。</span><span class="sxs-lookup"><span data-stu-id="914a7-103">Notifies the profiler that the runtime has started to unload a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="914a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="914a7-104">Syntax</span></span>  
  
```cpp  
HRESULT FunctionUnloadStarted(  
    [in] FunctionID functionId);
```  
  
## <a name="parameters"></a><span data-ttu-id="914a7-105">參數</span><span class="sxs-lookup"><span data-stu-id="914a7-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="914a7-106">\[in] 要卸載之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="914a7-106">\[in] The ID of the function that is being unloaded.</span></span>

## <a name="remarks"></a><span data-ttu-id="914a7-107">備註</span><span class="sxs-lookup"><span data-stu-id="914a7-107">Remarks</span></span>  
 <span data-ttu-id="914a7-108">`functionId`這個方法傳回給呼叫端之後，參數的值已不再有效。</span><span class="sxs-lookup"><span data-stu-id="914a7-108">The value of the `functionId` parameter is no longer valid after this method returns to the caller.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="914a7-109">規格需求</span><span class="sxs-lookup"><span data-stu-id="914a7-109">Requirements</span></span>  
 <span data-ttu-id="914a7-110">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="914a7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="914a7-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="914a7-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="914a7-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="914a7-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="914a7-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="914a7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="914a7-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="914a7-114">See also</span></span>

- [<span data-ttu-id="914a7-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="914a7-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
