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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6d20aa04b292fd29b60d68b844ef410258d90d31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546578"
---
# <a name="icorprofilercallbackexceptionsearchfunctionleave-method"></a><span data-ttu-id="4e54f-102">ICorProfilerCallback::ExceptionSearchFunctionLeave 方法</span><span class="sxs-lookup"><span data-stu-id="4e54f-102">ICorProfilerCallback::ExceptionSearchFunctionLeave Method</span></span>
<span data-ttu-id="4e54f-103">通知分析工具的例外狀況處理 「 搜尋 」 階段已完成搜尋函式。</span><span class="sxs-lookup"><span data-stu-id="4e54f-103">Notifies the profiler that the search phase of exception handling has finished searching a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e54f-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e54f-104">Syntax</span></span>  
  
```  
HRESULT ExceptionSearchFunctionLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="4e54f-105">需求</span><span class="sxs-lookup"><span data-stu-id="4e54f-105">Requirements</span></span>  
 <span data-ttu-id="4e54f-106">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="4e54f-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e54f-107">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4e54f-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4e54f-108">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e54f-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e54f-109">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e54f-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e54f-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e54f-110">See also</span></span>
- [<span data-ttu-id="4e54f-111">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="4e54f-111">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="4e54f-112">ExceptionSearchFunctionEnter 方法</span><span class="sxs-lookup"><span data-stu-id="4e54f-112">ExceptionSearchFunctionEnter Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)
