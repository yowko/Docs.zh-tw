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
ms.openlocfilehash: 6514606290bf006443d7011c1a428bebb4cca0f6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865825"
---
# <a name="icorprofilercallbackthreadcreated-method"></a><span data-ttu-id="c72d1-102">ICorProfilerCallback::ThreadCreated 方法</span><span class="sxs-lookup"><span data-stu-id="c72d1-102">ICorProfilerCallback::ThreadCreated Method</span></span>
<span data-ttu-id="c72d1-103">通知分析工具已建立執行緒。</span><span class="sxs-lookup"><span data-stu-id="c72d1-103">Notifies the profiler that a thread has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c72d1-104">語法</span><span class="sxs-lookup"><span data-stu-id="c72d1-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
## <a name="parameters"></a><span data-ttu-id="c72d1-105">參數</span><span class="sxs-lookup"><span data-stu-id="c72d1-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="c72d1-106">在已建立之執行緒的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c72d1-106">[in] The ID of the thread that has been created.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c72d1-107">備註</span><span class="sxs-lookup"><span data-stu-id="c72d1-107">Remarks</span></span>  
 <span data-ttu-id="c72d1-108">`threadId` 值會立即生效。</span><span class="sxs-lookup"><span data-stu-id="c72d1-108">The `threadId` value is immediately valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c72d1-109">需求</span><span class="sxs-lookup"><span data-stu-id="c72d1-109">Requirements</span></span>  
 <span data-ttu-id="c72d1-110">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c72d1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c72d1-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c72d1-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c72d1-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c72d1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c72d1-113">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c72d1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c72d1-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="c72d1-114">See also</span></span>

- [<span data-ttu-id="c72d1-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c72d1-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c72d1-116">ThreadDestroyed 方法</span><span class="sxs-lookup"><span data-stu-id="c72d1-116">ThreadDestroyed Method</span></span>](icorprofilercallback-threaddestroyed-method.md)
