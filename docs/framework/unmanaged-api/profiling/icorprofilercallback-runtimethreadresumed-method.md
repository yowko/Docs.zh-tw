---
title: ICorProfilerCallback::RuntimeThreadResumed 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadResumed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadResumed
helpviewer_keywords:
- ICorProfilerCallback::RuntimeThreadResumed method [.NET Framework profiling]
- RuntimeThreadResumed method [.NET Framework profiling]
ms.assetid: da984f89-4f53-4ab0-ae6f-3e2ee6085994
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 810875d1b91265fe886ce3cd11970cad7fee122d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228857"
---
# <a name="icorprofilercallbackruntimethreadresumed-method"></a><span data-ttu-id="b3b92-102">ICorProfilerCallback::RuntimeThreadResumed 方法</span><span class="sxs-lookup"><span data-stu-id="b3b92-102">ICorProfilerCallback::RuntimeThreadResumed Method</span></span>
<span data-ttu-id="b3b92-103">指定的執行緒已恢復在暫停之後會通知分析工具。</span><span class="sxs-lookup"><span data-stu-id="b3b92-103">Notifies the profiler that the specified thread has resumed after being suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3b92-104">語法</span><span class="sxs-lookup"><span data-stu-id="b3b92-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadResumed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3b92-105">參數</span><span class="sxs-lookup"><span data-stu-id="b3b92-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="b3b92-106">[in]已繼續執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b3b92-106">[in] The ID of the thread that has been resumed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3b92-107">需求</span><span class="sxs-lookup"><span data-stu-id="b3b92-107">Requirements</span></span>  
 <span data-ttu-id="b3b92-108">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b3b92-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3b92-109">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b3b92-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b3b92-110">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3b92-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b3b92-111">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="b3b92-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b3b92-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3b92-112">See also</span></span>

- [<span data-ttu-id="b3b92-113">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b3b92-113">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b3b92-114">RuntimeThreadSuspended 方法</span><span class="sxs-lookup"><span data-stu-id="b3b92-114">RuntimeThreadSuspended Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)
