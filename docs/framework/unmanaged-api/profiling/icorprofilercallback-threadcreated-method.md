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
ms.openlocfilehash: 7fb58c0eb2446253bd658434fc9d68bb857fe0e6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175118"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="ac1cf-102">ICorProfilerCallback::ThreadCreated 方法</span><span class="sxs-lookup"><span data-stu-id="ac1cf-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="ac1cf-103">通知探測器已創建執行緒。</span><span class="sxs-lookup"><span data-stu-id="ac1cf-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac1cf-104">語法</span><span class="sxs-lookup"><span data-stu-id="ac1cf-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);
```  
  
## <a name="parameters"></a><span data-ttu-id="ac1cf-105">參數</span><span class="sxs-lookup"><span data-stu-id="ac1cf-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="ac1cf-106">[在]已創建的執行緒的 ID。</span><span class="sxs-lookup"><span data-stu-id="ac1cf-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac1cf-107">備註</span><span class="sxs-lookup"><span data-stu-id="ac1cf-107">Remarks</span></span>  
 <span data-ttu-id="ac1cf-108">該`threadId`值立即有效。</span><span class="sxs-lookup"><span data-stu-id="ac1cf-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac1cf-109">需求</span><span class="sxs-lookup"><span data-stu-id="ac1cf-109">Requirements</span></span>  
 <span data-ttu-id="ac1cf-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="ac1cf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac1cf-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ac1cf-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ac1cf-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ac1cf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ac1cf-113">**.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac1cf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac1cf-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ac1cf-114">See also</span></span>

- [<span data-ttu-id="ac1cf-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="ac1cf-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="ac1cf-116">ThreadDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="ac1cf-116">ThreadDestroyed Method</span></span>](icorprofilercallback-threaddestroyed-method.md)
