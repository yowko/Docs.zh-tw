---
title: ICorProfilerCallback::ExceptionSearchFilterEnter 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterEnter
helpviewer_keywords:
- ExceptionSearchFilterEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFilterEnter method [.NET Framework profiling]
ms.assetid: acc239ce-3eef-418c-b1df-c5a6dd8e8a4c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: be91772f07e1a06c7df5b16fd70812e6a522d736
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192585"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="281a7-102">ICorProfilerCallback::ExceptionSearchFilterEnter 方法</span><span class="sxs-lookup"><span data-stu-id="281a7-102">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>
<span data-ttu-id="281a7-103">通知分析工具，例外狀況處理的搜尋階段已開始執行使用者定義的例外狀況篩選條件。</span><span class="sxs-lookup"><span data-stu-id="281a7-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="281a7-104">語法</span><span class="sxs-lookup"><span data-stu-id="281a7-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="281a7-105">參數</span><span class="sxs-lookup"><span data-stu-id="281a7-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="281a7-106">[in]包含篩選條件的函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="281a7-106">[in] The ID of the function that contains the filter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="281a7-107">需求</span><span class="sxs-lookup"><span data-stu-id="281a7-107">Requirements</span></span>  
 <span data-ttu-id="281a7-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="281a7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="281a7-109">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="281a7-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="281a7-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="281a7-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="281a7-111">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="281a7-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="281a7-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="281a7-112">See also</span></span>

- [<span data-ttu-id="281a7-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="281a7-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="281a7-114">ExceptionSearchFilterLeave 方法</span><span class="sxs-lookup"><span data-stu-id="281a7-114">ExceptionSearchFilterLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)
