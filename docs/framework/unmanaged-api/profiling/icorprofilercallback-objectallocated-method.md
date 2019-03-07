---
title: ICorProfilerCallback::ObjectAllocated 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectAllocated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectAllocated
helpviewer_keywords:
- ObjectAllocated method [.NET Framework profiling]
- ICorProfilerCallback::ObjectAllocated method [.NET Framework profiling]
ms.assetid: eb412622-77cc-4abd-a2cd-c910fe8edd54
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0deadc3783663fe595d8217a167d18e6916c6be9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57465994"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="efc46-102">ICorProfilerCallback::ObjectAllocated 方法</span><span class="sxs-lookup"><span data-stu-id="efc46-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="efc46-103">通知分析工具已配置的記憶體中堆積物件。</span><span class="sxs-lookup"><span data-stu-id="efc46-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efc46-104">語法</span><span class="sxs-lookup"><span data-stu-id="efc46-104">Syntax</span></span>  
  
```  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efc46-105">參數</span><span class="sxs-lookup"><span data-stu-id="efc46-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="efc46-106">[in]配置記憶體的物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="efc46-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="efc46-107">[in]類別物件的執行個體的識別碼。</span><span class="sxs-lookup"><span data-stu-id="efc46-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efc46-108">備註</span><span class="sxs-lookup"><span data-stu-id="efc46-108">Remarks</span></span>  
 <span data-ttu-id="efc46-109">`ObjectedAllocated`不會從堆疊或未受管理的記憶體配置呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="efc46-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="efc46-110">`classId`參數可以參考尚未載入的 managed 程式碼中的類別。</span><span class="sxs-lookup"><span data-stu-id="efc46-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="efc46-111">分析工具將會收到該類別的類別載入回呼之後立即`ObjectAllocated`回呼。</span><span class="sxs-lookup"><span data-stu-id="efc46-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efc46-112">需求</span><span class="sxs-lookup"><span data-stu-id="efc46-112">Requirements</span></span>  
 <span data-ttu-id="efc46-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="efc46-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efc46-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="efc46-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="efc46-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efc46-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="efc46-116">**.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="efc46-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efc46-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efc46-117">See also</span></span>
- [<span data-ttu-id="efc46-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="efc46-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="efc46-119">ClassLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="efc46-119">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="efc46-120">ClassLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="efc46-120">ClassLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
