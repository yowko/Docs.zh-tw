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
ms.openlocfilehash: c07b37e58141f7aff747bd3772be265ae0da42ac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222012"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="b38a5-102">ICorProfilerCallback::ObjectAllocated 方法</span><span class="sxs-lookup"><span data-stu-id="b38a5-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="b38a5-103">通知分析工具已配置的記憶體中堆積物件。</span><span class="sxs-lookup"><span data-stu-id="b38a5-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b38a5-104">語法</span><span class="sxs-lookup"><span data-stu-id="b38a5-104">Syntax</span></span>  
  
```  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b38a5-105">參數</span><span class="sxs-lookup"><span data-stu-id="b38a5-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="b38a5-106">[in]配置記憶體的物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="b38a5-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="b38a5-107">[in]類別物件的執行個體的識別碼。</span><span class="sxs-lookup"><span data-stu-id="b38a5-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b38a5-108">備註</span><span class="sxs-lookup"><span data-stu-id="b38a5-108">Remarks</span></span>  
 <span data-ttu-id="b38a5-109">`ObjectedAllocated`不會從堆疊或未受管理的記憶體配置呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="b38a5-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="b38a5-110">`classId`參數可以參考尚未載入的 managed 程式碼中的類別。</span><span class="sxs-lookup"><span data-stu-id="b38a5-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="b38a5-111">分析工具將會收到該類別的類別載入回呼之後立即`ObjectAllocated`回呼。</span><span class="sxs-lookup"><span data-stu-id="b38a5-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b38a5-112">需求</span><span class="sxs-lookup"><span data-stu-id="b38a5-112">Requirements</span></span>  
 <span data-ttu-id="b38a5-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="b38a5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b38a5-114">**標頭：** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b38a5-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b38a5-115">**LIBRARY:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b38a5-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b38a5-116">.NET Framework 版本：</span><span class="sxs-lookup"><span data-stu-id="b38a5-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b38a5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b38a5-117">See also</span></span>

- [<span data-ttu-id="b38a5-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="b38a5-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="b38a5-119">ClassLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="b38a5-119">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="b38a5-120">ClassLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="b38a5-120">ClassLoadFinished Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)
