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
ms.openlocfilehash: ef25d55defee2fdcfc7d744e481060eb7a7782ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699868"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="22c1c-102">ICorProfilerCallback::ExceptionSearchCatcherFound 方法</span><span class="sxs-lookup"><span data-stu-id="22c1c-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>

<span data-ttu-id="22c1c-103">通知分析工具，例外狀況處理的搜尋階段已找出所擲回例外狀況的處理常式。</span><span class="sxs-lookup"><span data-stu-id="22c1c-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22c1c-104">語法</span><span class="sxs-lookup"><span data-stu-id="22c1c-104">Syntax</span></span>  
  
```cpp  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22c1c-105">參數</span><span class="sxs-lookup"><span data-stu-id="22c1c-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="22c1c-106">\[in] 包含例外狀況處理常式之函數的識別碼。</span><span class="sxs-lookup"><span data-stu-id="22c1c-106">\[in] The ID of the function that contains the exception handler.</span></span>

## <a name="requirements"></a><span data-ttu-id="22c1c-107">需求</span><span class="sxs-lookup"><span data-stu-id="22c1c-107">Requirements</span></span>  

 <span data-ttu-id="22c1c-108">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="22c1c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22c1c-109">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="22c1c-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="22c1c-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22c1c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22c1c-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22c1c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22c1c-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="22c1c-112">See also</span></span>

- [<span data-ttu-id="22c1c-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="22c1c-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
