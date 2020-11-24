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
ms.openlocfilehash: fda234a6a280aeea1f497ad195d6d41efb6aa951
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674318"
---
# <a name="icorprofilercallbackobjectallocated-method"></a><span data-ttu-id="e90a0-102">ICorProfilerCallback::ObjectAllocated 方法</span><span class="sxs-lookup"><span data-stu-id="e90a0-102">ICorProfilerCallback::ObjectAllocated Method</span></span>

<span data-ttu-id="e90a0-103">通知分析工具，堆積內的記憶體已配置給物件。</span><span class="sxs-lookup"><span data-stu-id="e90a0-103">Notifies the profiler that memory within the heap has been allocated for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e90a0-104">語法</span><span class="sxs-lookup"><span data-stu-id="e90a0-104">Syntax</span></span>  
  
```cpp  
HRESULT ObjectAllocated(  
    [in] ObjectID objectId,  
    [in] ClassID classId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e90a0-105">參數</span><span class="sxs-lookup"><span data-stu-id="e90a0-105">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="e90a0-106">在配置記憶體之物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e90a0-106">[in] The ID of the object for which memory was allocated.</span></span>  
  
 `classId`  
 <span data-ttu-id="e90a0-107">在物件是實例之類別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="e90a0-107">[in] The ID of the class of which the object is an instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e90a0-108">備註</span><span class="sxs-lookup"><span data-stu-id="e90a0-108">Remarks</span></span>  

 <span data-ttu-id="e90a0-109">`ObjectedAllocated`從堆疊或非受控記憶體進行配置時，不會呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="e90a0-109">The `ObjectedAllocated` method is not called for allocations from either the stack or unmanaged memory.</span></span> <span data-ttu-id="e90a0-110">`classId`參數可以參考尚未載入之 managed 程式碼中的類別。</span><span class="sxs-lookup"><span data-stu-id="e90a0-110">The `classId` parameter can refer to a class in managed code that has not been loaded yet.</span></span> <span data-ttu-id="e90a0-111">分析工具會在回呼之後立即接收該類別的類別載入回呼 `ObjectAllocated` 。</span><span class="sxs-lookup"><span data-stu-id="e90a0-111">The profiler will receive a class load callback for that class immediately after the `ObjectAllocated` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e90a0-112">需求</span><span class="sxs-lookup"><span data-stu-id="e90a0-112">Requirements</span></span>  

 <span data-ttu-id="e90a0-113">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="e90a0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e90a0-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e90a0-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e90a0-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e90a0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e90a0-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e90a0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e90a0-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e90a0-117">See also</span></span>

- [<span data-ttu-id="e90a0-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="e90a0-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e90a0-119">ClassLoadStarted 方法</span><span class="sxs-lookup"><span data-stu-id="e90a0-119">ClassLoadStarted Method</span></span>](icorprofilercallback-classloadstarted-method.md)
- [<span data-ttu-id="e90a0-120">ClassLoadFinished 方法</span><span class="sxs-lookup"><span data-stu-id="e90a0-120">ClassLoadFinished Method</span></span>](icorprofilercallback-classloadfinished-method.md)
