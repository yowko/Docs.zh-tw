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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0615f37d97359f73eb1277da174b7e6401bfc313
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57500339"
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="114a9-102">ICorProfilerCallback::ExceptionSearchFunctionEnter 方法</span><span class="sxs-lookup"><span data-stu-id="114a9-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="114a9-103">通知分析工具，例外狀況處理的搜尋階段已開始搜尋來尋找目前的例外狀況處理常式的函式。</span><span class="sxs-lookup"><span data-stu-id="114a9-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="114a9-104">語法</span><span class="sxs-lookup"><span data-stu-id="114a9-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="114a9-105">參數</span><span class="sxs-lookup"><span data-stu-id="114a9-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="114a9-106">[in]已輸入函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="114a9-106">[in] The ID of the function that has been entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="114a9-107">需求</span><span class="sxs-lookup"><span data-stu-id="114a9-107">Requirements</span></span>  
 <span data-ttu-id="114a9-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="114a9-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="114a9-109">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="114a9-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="114a9-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="114a9-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="114a9-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="114a9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="114a9-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="114a9-112">See also</span></span>
- [<span data-ttu-id="114a9-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="114a9-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="114a9-114">ExceptionSearchFunctionLeave 方法</span><span class="sxs-lookup"><span data-stu-id="114a9-114">ExceptionSearchFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)
