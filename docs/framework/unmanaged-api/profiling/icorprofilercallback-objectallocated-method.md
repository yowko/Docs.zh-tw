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
ms.openlocfilehash: 38d9e83e9fa0e9cd0586fb10a6fd79c29bead4a6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866100"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="2b363-102">ICorProfilerCallback::ObjectAllocated 方法</span><span class="sxs-lookup"><span data-stu-id="2b363-102">ICorProfilerCallback::ObjectAllocated Method</span></span>
<span data-ttu-id="2b363-103">通知分析工具，堆積內的記憶體已配置給物件。</span><span class="sxs-lookup"><span data-stu-id="2b363-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b363-104">語法</span><span class="sxs-lookup"><span data-stu-id="2b363-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b363-105">參數</span><span class="sxs-lookup"><span data-stu-id="2b363-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="2b363-106">在配置記憶體之物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="2b363-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="2b363-107">在物件為實例之類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="2b363-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b363-108">備註</span><span class="sxs-lookup"><span data-stu-id="2b363-108">Remarks</span></span>  
 <span data-ttu-id="2b363-109">不會針對來自堆疊或非受控記憶體的配置呼叫 `ObjectedAllocated` 方法。</span><span class="sxs-lookup"><span data-stu-id="2b363-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="2b363-110">`classId` 參數可以參考尚未載入之 managed 程式碼中的類別。</span><span class="sxs-lookup"><span data-stu-id="2b363-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="2b363-111">分析工具會在 `ObjectAllocated` 回呼之後，立即收到該類別的類別載入回呼。</span><span class="sxs-lookup"><span data-stu-id="2b363-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b363-112">需求</span><span class="sxs-lookup"><span data-stu-id="2b363-112">Requirements</span></span>  
 <span data-ttu-id="2b363-113">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="2b363-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b363-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2b363-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2b363-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b363-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b363-116">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b363-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b363-117">請參閱</span><span class="sxs-lookup"><span data-stu-id="2b363-117">See also</span></span>

- [<span data-ttu-id="2b363-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="2b363-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2b363-119">ClassLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="2b363-119">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="2b363-120">ClassLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="2b363-120">ClassLoadFinished Method</span></span>](icorprofilercallback-classloadfinished-method.md)
