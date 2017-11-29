---
title: "ICorProfilerCallback::ExceptionSearchFunctionEnter 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionSearchFunctionEnter
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionSearchFunctionEnter
helpviewer_keywords:
- ExceptionSearchFunctionEnter method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionSearchFunctionEnter method [.NET Framework profiling]
ms.assetid: bfd54573-b7e6-4bd1-a184-7f08a8b39fae
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3fc6d1708a6a2daea0d0a9dc815bc07736644b49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionsearchfunctionenter-method"></a><span data-ttu-id="5b4e1-102">ICorProfilerCallback::ExceptionSearchFunctionEnter 方法</span><span class="sxs-lookup"><span data-stu-id="5b4e1-102">ICorProfilerCallback::ExceptionSearchFunctionEnter Method</span></span>
<span data-ttu-id="5b4e1-103">通知分析工具 「 搜尋 」 階段的例外狀況處理已經開始搜尋來尋找目前的例外狀況處理常式的函式。</span><span class="sxs-lookup"><span data-stu-id="5b4e1-103">Notifies the profiler that the search phase of exception handling has begun searching a function to find a handler for the current exception.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b4e1-104">語法</span><span class="sxs-lookup"><span data-stu-id="5b4e1-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFunctionEnter(  
    [in] FunctionID functionId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5b4e1-105">參數</span><span class="sxs-lookup"><span data-stu-id="5b4e1-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="5b4e1-106">[in]已輸入函數的識別碼。</span><span class="sxs-lookup"><span data-stu-id="5b4e1-106">[in] The ID of the function that has been entered.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b4e1-107">需求</span><span class="sxs-lookup"><span data-stu-id="5b4e1-107">Requirements</span></span>  
 <span data-ttu-id="5b4e1-108">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="5b4e1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b4e1-109">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5b4e1-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5b4e1-110">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5b4e1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5b4e1-111">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5b4e1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b4e1-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b4e1-112">See Also</span></span>  
 [<span data-ttu-id="5b4e1-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="5b4e1-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="5b4e1-114">ExceptionSearchFunctionLeave 方法</span><span class="sxs-lookup"><span data-stu-id="5b4e1-114">ExceptionSearchFunctionLeave Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)
