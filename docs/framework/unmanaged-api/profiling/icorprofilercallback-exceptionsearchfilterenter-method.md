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
ms.openlocfilehash: 304b8da670786851a70e38e6623d44b1bde71a04
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500230"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="c5fac-102">ICorProfilerCallback::ExceptionSearchFilterEnter 方法</span><span class="sxs-lookup"><span data-stu-id="c5fac-102">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>
<span data-ttu-id="c5fac-103">通知分析工具，例外狀況處理的搜尋階段已開始執行使用者定義的例外狀況篩選準則。</span><span class="sxs-lookup"><span data-stu-id="c5fac-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5fac-104">語法</span><span class="sxs-lookup"><span data-stu-id="c5fac-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5fac-105">參數</span><span class="sxs-lookup"><span data-stu-id="c5fac-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="c5fac-106">\[in] 包含篩選準則之函數的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c5fac-106">\[in] The ID of the function that contains the filter.</span></span>

## <a name="requirements"></a><span data-ttu-id="c5fac-107">規格需求</span><span class="sxs-lookup"><span data-stu-id="c5fac-107">Requirements</span></span>  
 <span data-ttu-id="c5fac-108">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c5fac-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5fac-109">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c5fac-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c5fac-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5fac-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5fac-111">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5fac-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5fac-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c5fac-112">See also</span></span>

- [<span data-ttu-id="c5fac-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c5fac-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c5fac-114">ExceptionSearchFilterLeave 方法</span><span class="sxs-lookup"><span data-stu-id="c5fac-114">ExceptionSearchFilterLeave Method</span></span>](icorprofilercallback-exceptionsearchfilterleave-method.md)
