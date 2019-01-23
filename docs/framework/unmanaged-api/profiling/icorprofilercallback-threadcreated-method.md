---
title: ICorProfilerCallback::ThreadCreated 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadCreated
helpviewer_keywords:
- ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]
- ThreadCreated method [.NET Framework profiling]
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d85dcb462df0255ab5420db94f9d055cce2c78b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54616926"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="012c6-102">ICorProfilerCallback::ThreadCreated 方法</span><span class="sxs-lookup"><span data-stu-id="012c6-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="012c6-103">通知分析工具已建立的執行緒。</span><span class="sxs-lookup"><span data-stu-id="012c6-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="012c6-104">語法</span><span class="sxs-lookup"><span data-stu-id="012c6-104">Syntax</span></span>  
  
```  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="012c6-105">參數</span><span class="sxs-lookup"><span data-stu-id="012c6-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="012c6-106">[in]已建立的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="012c6-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="012c6-107">備註</span><span class="sxs-lookup"><span data-stu-id="012c6-107">Remarks</span></span>  
 <span data-ttu-id="012c6-108">`threadId`值是立即有效。</span><span class="sxs-lookup"><span data-stu-id="012c6-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="012c6-109">需求</span><span class="sxs-lookup"><span data-stu-id="012c6-109">Requirements</span></span>  
 <span data-ttu-id="012c6-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="012c6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="012c6-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="012c6-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="012c6-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="012c6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="012c6-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="012c6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="012c6-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="012c6-114">See also</span></span>
- [<span data-ttu-id="012c6-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="012c6-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="012c6-116">ThreadDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="012c6-116">ThreadDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)
