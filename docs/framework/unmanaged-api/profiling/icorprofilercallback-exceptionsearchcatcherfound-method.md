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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a4dc6b66aff34bae869737591040e5fc1e552834
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499663"
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="32f2e-102">ICorProfilerCallback::ExceptionSearchCatcherFound 方法</span><span class="sxs-lookup"><span data-stu-id="32f2e-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="32f2e-103">通知分析工具的例外狀況處理 「 搜尋 」 階段，位於所擲回的例外狀況的處理常式。</span><span class="sxs-lookup"><span data-stu-id="32f2e-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32f2e-104">語法</span><span class="sxs-lookup"><span data-stu-id="32f2e-104">Syntax</span></span>  
  
```  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32f2e-105">參數</span><span class="sxs-lookup"><span data-stu-id="32f2e-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="32f2e-106">[in]包含例外狀況處理常式的函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="32f2e-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32f2e-107">需求</span><span class="sxs-lookup"><span data-stu-id="32f2e-107">Requirements</span></span>  
 <span data-ttu-id="32f2e-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="32f2e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32f2e-109">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="32f2e-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="32f2e-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32f2e-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32f2e-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32f2e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32f2e-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32f2e-112">See also</span></span>
- [<span data-ttu-id="32f2e-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="32f2e-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
