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
ms.openlocfilehash: 5f8eca3e8eb755e31e704e557ae614a6e5c1f534
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61915268"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="02e00-102">ICorProfilerCallback::ThreadCreated 方法</span><span class="sxs-lookup"><span data-stu-id="02e00-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="02e00-103">通知分析工具已建立的執行緒。</span><span class="sxs-lookup"><span data-stu-id="02e00-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02e00-104">語法</span><span class="sxs-lookup"><span data-stu-id="02e00-104">Syntax</span></span>  
  
```  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="02e00-105">參數</span><span class="sxs-lookup"><span data-stu-id="02e00-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="02e00-106">[in]已建立的執行緒識別碼。</span><span class="sxs-lookup"><span data-stu-id="02e00-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02e00-107">備註</span><span class="sxs-lookup"><span data-stu-id="02e00-107">Remarks</span></span>  
 <span data-ttu-id="02e00-108">`threadId`值是立即有效。</span><span class="sxs-lookup"><span data-stu-id="02e00-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02e00-109">需求</span><span class="sxs-lookup"><span data-stu-id="02e00-109">Requirements</span></span>  
 <span data-ttu-id="02e00-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="02e00-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02e00-111">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="02e00-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="02e00-112">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02e00-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02e00-113">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02e00-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02e00-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02e00-114">See also</span></span>

- [<span data-ttu-id="02e00-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="02e00-115">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="02e00-116">ThreadDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="02e00-116">ThreadDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)
