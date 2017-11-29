---
title: "ICorProfilerCallback::ThreadCreated 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ThreadCreated
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ThreadCreated
helpviewer_keywords:
- ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]
- ThreadCreated method [.NET Framework profiling]
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b62d5d1129bb71a95ac4e98624558272b08f0683
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="2bc64-102">ICorProfilerCallback::ThreadCreated 方法</span><span class="sxs-lookup"><span data-stu-id="2bc64-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="2bc64-103">通知分析工具已建立一個執行緒。</span><span class="sxs-lookup"><span data-stu-id="2bc64-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bc64-104">語法</span><span class="sxs-lookup"><span data-stu-id="2bc64-104">Syntax</span></span>  
  
```  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="2bc64-105">參數</span><span class="sxs-lookup"><span data-stu-id="2bc64-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="2bc64-106">[in]已建立的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="2bc64-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2bc64-107">備註</span><span class="sxs-lookup"><span data-stu-id="2bc64-107">Remarks</span></span>  
 <span data-ttu-id="2bc64-108">`threadId`值是立即有效。</span><span class="sxs-lookup"><span data-stu-id="2bc64-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bc64-109">需求</span><span class="sxs-lookup"><span data-stu-id="2bc64-109">Requirements</span></span>  
 <span data-ttu-id="2bc64-110">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2bc64-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2bc64-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2bc64-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2bc64-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2bc64-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2bc64-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2bc64-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bc64-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bc64-114">See Also</span></span>  
 [<span data-ttu-id="2bc64-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="2bc64-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="2bc64-116">ThreadDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="2bc64-116">ThreadDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)
