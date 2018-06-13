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
ms.openlocfilehash: 08ac7eddf96ac54ce16696355f7d5bb5694f872b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450979"
---
# <a name="icorprofilercallbackexceptionsearchfilterenter-method"></a><span data-ttu-id="5fcd3-102">ICorProfilerCallback::ExceptionSearchFilterEnter 方法</span><span class="sxs-lookup"><span data-stu-id="5fcd3-102">ICorProfilerCallback::ExceptionSearchFilterEnter Method</span></span>
<span data-ttu-id="5fcd3-103">通知分析工具的例外狀況處理的搜尋階段已開始執行使用者定義的例外狀況篩選條件。</span><span class="sxs-lookup"><span data-stu-id="5fcd3-103">Notifies the profiler that the search phase of exception handling has begun executing a user-defined exception filter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fcd3-104">語法</span><span class="sxs-lookup"><span data-stu-id="5fcd3-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFilterEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5fcd3-105">參數</span><span class="sxs-lookup"><span data-stu-id="5fcd3-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="5fcd3-106">[in]包含篩選條件的函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5fcd3-106">[in] The ID of the function that contains the filter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fcd3-107">需求</span><span class="sxs-lookup"><span data-stu-id="5fcd3-107">Requirements</span></span>  
 <span data-ttu-id="5fcd3-108">**平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5fcd3-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fcd3-109">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5fcd3-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5fcd3-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fcd3-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fcd3-111">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fcd3-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fcd3-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fcd3-112">See Also</span></span>  
 [<span data-ttu-id="5fcd3-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="5fcd3-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="5fcd3-114">ExceptionSearchFilterLeave 方法</span><span class="sxs-lookup"><span data-stu-id="5fcd3-114">ExceptionSearchFilterLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)
