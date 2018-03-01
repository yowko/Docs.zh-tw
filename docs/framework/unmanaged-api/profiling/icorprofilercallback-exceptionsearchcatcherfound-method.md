---
title: "ICorProfilerCallback::ExceptionSearchCatcherFound 方法"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fc226b6102c50b118a4b13f9cd25700dd1ca7301
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackexceptionsearchcatcherfound-method"></a><span data-ttu-id="186ee-102">ICorProfilerCallback::ExceptionSearchCatcherFound 方法</span><span class="sxs-lookup"><span data-stu-id="186ee-102">ICorProfilerCallback::ExceptionSearchCatcherFound Method</span></span>
<span data-ttu-id="186ee-103">通知分析工具，「 搜尋 」 階段的例外狀況處理已經位於擲回的例外狀況的處理常式。</span><span class="sxs-lookup"><span data-stu-id="186ee-103">Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="186ee-104">語法</span><span class="sxs-lookup"><span data-stu-id="186ee-104">Syntax</span></span>  
  
```  
RESULT ExceptionSearchCatcherFound(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="186ee-105">參數</span><span class="sxs-lookup"><span data-stu-id="186ee-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="186ee-106">[in]包含例外狀況處理常式的函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="186ee-106">[in] The ID of the function that contains the exception handler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="186ee-107">需求</span><span class="sxs-lookup"><span data-stu-id="186ee-107">Requirements</span></span>  
 <span data-ttu-id="186ee-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="186ee-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="186ee-109">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="186ee-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="186ee-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="186ee-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="186ee-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="186ee-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="186ee-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="186ee-112">See Also</span></span>  
 [<span data-ttu-id="186ee-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="186ee-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
