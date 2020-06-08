---
title: ICorProfilerCallback::ExceptionSearchFunctionLeave 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionLeave
helpviewer_keywords:
- ExceptionSearchFunctionLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionLeave method [.NET Framework profiling]
ms.assetid: 01de7ac6-0aad-42ef-bf93-50737667b0a4
topic_type:
- apiref
ms.openlocfilehash: 11ce99fe650f68b80c380c740472e5e0ac8904db
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500178"
---
# <a name="icorprofilercallbackexceptionsearchfunctionleave-method"></a><span data-ttu-id="6b9e2-102">ICorProfilerCallback::ExceptionSearchFunctionLeave 方法</span><span class="sxs-lookup"><span data-stu-id="6b9e2-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Method</span></span>
<span data-ttu-id="6b9e2-103">通知分析工具，例外狀況處理的搜尋階段已完成搜尋函數。</span><span class="sxs-lookup"><span data-stu-id="6b9e2-103">Notifies the profiler that the search phase of exception handling has finished searching a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b9e2-104">語法</span><span class="sxs-lookup"><span data-stu-id="6b9e2-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="6b9e2-105">規格需求</span><span class="sxs-lookup"><span data-stu-id="6b9e2-105">Requirements</span></span>  
 <span data-ttu-id="6b9e2-106">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="6b9e2-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b9e2-107">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6b9e2-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6b9e2-108">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b9e2-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b9e2-109">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b9e2-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b9e2-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b9e2-110">See also</span></span>

- [<span data-ttu-id="6b9e2-111">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="6b9e2-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="6b9e2-112">ExceptionSearchFunctionEnter 方法</span><span class="sxs-lookup"><span data-stu-id="6b9e2-112">ExceptionSearchFunctionEnter Method</span></span>](icorprofilercallback-exceptionsearchfunctionenter-method.md)
