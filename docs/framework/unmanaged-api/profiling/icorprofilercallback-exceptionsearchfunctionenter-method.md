---
title: ICorProfilerCallback::ExceptionSearchFunctionEnter 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFunctionEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFunctionEnter
helpviewer_keywords:
- ExceptionSearchFunctionEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionEnter method [.NET Framework profiling]
ms.assetid: bfd54573-b7e6-4bd1-a184-7f08a8b39fae
topic_type:
- apiref
ms.openlocfilehash: 244227aadb50720514f7511be563089d520b4bf5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500191"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="b92cd-102">ICorProfilerCallback::ExceptionSearchFunctionEnter 方法</span><span class="sxs-lookup"><span data-stu-id="b92cd-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="b92cd-103">通知分析工具，例外狀況處理的搜尋階段已開始搜尋函式，以尋找目前例外狀況的處理常式。</span><span class="sxs-lookup"><span data-stu-id="b92cd-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b92cd-104">語法</span><span class="sxs-lookup"><span data-stu-id="b92cd-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b92cd-105">參數</span><span class="sxs-lookup"><span data-stu-id="b92cd-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="b92cd-106">\[in] 已輸入的函式識別碼。</span><span class="sxs-lookup"><span data-stu-id="b92cd-106">\[in] The ID of the function that has been entered.</span></span>
  
## <a name="requirements"></a><span data-ttu-id="b92cd-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="b92cd-107">Requirements</span></span>  
 <span data-ttu-id="b92cd-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b92cd-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b92cd-109">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b92cd-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b92cd-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b92cd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b92cd-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b92cd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b92cd-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b92cd-112">See also</span></span>

- [<span data-ttu-id="b92cd-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b92cd-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b92cd-114">ExceptionSearchFunctionLeave 方法</span><span class="sxs-lookup"><span data-stu-id="b92cd-114">ExceptionSearchFunctionLeave Method</span></span>](icorprofilercallback-exceptionsearchfunctionleave-method.md)
