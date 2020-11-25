---
title: ICorProfilerCallback::ThreadDestroyed 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadDestroyed
helpviewer_keywords:
- ThreadDestroyed method [.NET Framework profiling]
- ICorProfilerCallback::ThreadDestroyed method [.NET Framework profiling]
ms.assetid: 4c2b66fd-0595-40a3-8931-f9c4fff97ac8
topic_type:
- apiref
ms.openlocfilehash: 0cef868861155d553aba42fe28c3f1f1b86763b0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731965"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a><span data-ttu-id="511c2-102">ICorProfilerCallback::ThreadDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="511c2-102">ICorProfilerCallback::ThreadDestroyed Method</span></span>

<span data-ttu-id="511c2-103">通知分析工具，執行緒已損毀。</span><span class="sxs-lookup"><span data-stu-id="511c2-103">Notifies the profiler that a thread has been destroyed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="511c2-104">語法</span><span class="sxs-lookup"><span data-stu-id="511c2-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="511c2-105">參數</span><span class="sxs-lookup"><span data-stu-id="511c2-105">Parameters</span></span>  

 `threadId`  
 <span data-ttu-id="511c2-106">在已損毀之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="511c2-106">[in] The ID of the thread that has been destroyed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="511c2-107">備註</span><span class="sxs-lookup"><span data-stu-id="511c2-107">Remarks</span></span>  

 <span data-ttu-id="511c2-108">`threadId`此值在此呼叫時不再有效。</span><span class="sxs-lookup"><span data-stu-id="511c2-108">The `threadId` value is no longer valid at the time of this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="511c2-109">需求</span><span class="sxs-lookup"><span data-stu-id="511c2-109">Requirements</span></span>  

 <span data-ttu-id="511c2-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="511c2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="511c2-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="511c2-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="511c2-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="511c2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="511c2-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="511c2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="511c2-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="511c2-114">See also</span></span>

- [<span data-ttu-id="511c2-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="511c2-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="511c2-116">ThreadCreated 方法</span><span class="sxs-lookup"><span data-stu-id="511c2-116">ThreadCreated Method</span></span>](icorprofilercallback-threadcreated-method.md)
