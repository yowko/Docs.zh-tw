---
title: ICorProfilerCallback::ExceptionSearchCatcherFound 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchCatcherFound
helpviewer_keywords:
- ExceptionSearchCatcherFound method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchCatcherFound method [.NET Framework profiling]
ms.assetid: 190f424d-5e37-4163-a191-0895686e9476
topic_type:
- apiref
ms.openlocfilehash: 70c03d34bdf9bd315994b2bfa09631efac2565ef
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500217"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="ef75a-102">ICorProfilerCallback::ExceptionSearchCatcherFound 方法</span><span class="sxs-lookup"><span data-stu-id="ef75a-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="ef75a-103">通知分析工具，例外狀況處理的搜尋階段已找出擲回之例外狀況的處理常式。</span><span class="sxs-lookup"><span data-stu-id="ef75a-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef75a-104">語法</span><span class="sxs-lookup"><span data-stu-id="ef75a-104">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ef75a-105">參數</span><span class="sxs-lookup"><span data-stu-id="ef75a-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="ef75a-106">\[in] 包含例外狀況處理常式之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="ef75a-106">\[in] The ID of the function that contains the exception handler.</span></span>

## <a name="requirements"></a><span data-ttu-id="ef75a-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="ef75a-107">Requirements</span></span>  
 <span data-ttu-id="ef75a-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ef75a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef75a-109">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ef75a-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ef75a-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef75a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef75a-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef75a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef75a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef75a-112">See also</span></span>

- [<span data-ttu-id="ef75a-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ef75a-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
