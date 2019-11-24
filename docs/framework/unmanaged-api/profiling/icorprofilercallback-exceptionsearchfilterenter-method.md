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
ms.openlocfilehash: 65765795c13948175a7eb5bd78843968d55953d8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445378"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="33143-102">ICorProfilerCallback::ExceptionSearchFilterEnter 方法</span><span class="sxs-lookup"><span data-stu-id="33143-102">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>
<span data-ttu-id="33143-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span><span class="sxs-lookup"><span data-stu-id="33143-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33143-104">語法</span><span class="sxs-lookup"><span data-stu-id="33143-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33143-105">參數</span><span class="sxs-lookup"><span data-stu-id="33143-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="33143-106">[in] The ID of the function that contains the filter.</span><span class="sxs-lookup"><span data-stu-id="33143-106">[in] The ID of the function that contains the filter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33143-107">需求</span><span class="sxs-lookup"><span data-stu-id="33143-107">Requirements</span></span>  
 <span data-ttu-id="33143-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="33143-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33143-109">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="33143-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="33143-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33143-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33143-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33143-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33143-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="33143-112">See also</span></span>

- [<span data-ttu-id="33143-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="33143-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="33143-114">ExceptionSearchFilterLeave 方法</span><span class="sxs-lookup"><span data-stu-id="33143-114">ExceptionSearchFilterLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)
