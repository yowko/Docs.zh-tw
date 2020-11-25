---
title: ICorProfilerCallback::ExceptionCatcherEnter 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherEnter
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCatcherEnter method [.NET Framework profiling]
- ExceptionCatcherEnter method [.NET Framework profiling]
ms.assetid: 41462329-a648-46f0-ae6d-728b94c31aa9
topic_type:
- apiref
ms.openlocfilehash: 97b9f517a24a7d82b7697cd0723628ede073b537
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700150"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="c0488-102">ICorProfilerCallback::ExceptionCatcherEnter 方法</span><span class="sxs-lookup"><span data-stu-id="c0488-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>

<span data-ttu-id="c0488-103">通知分析工具，控制項正在傳遞至適當的 `catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="c0488-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0488-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0488-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0488-105">參數</span><span class="sxs-lookup"><span data-stu-id="c0488-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="c0488-106">\[in] 包含區塊的函式識別碼 `catch` 。</span><span class="sxs-lookup"><span data-stu-id="c0488-106">\[in] The identifier of the function containing the `catch` block.</span></span>
  
- `objectId`

  <span data-ttu-id="c0488-107">\[in] 所處理之例外狀況的識別碼。</span><span class="sxs-lookup"><span data-stu-id="c0488-107">\[in] The identifier of the exception being handled.</span></span>

## <a name="remarks"></a><span data-ttu-id="c0488-108">備註</span><span class="sxs-lookup"><span data-stu-id="c0488-108">Remarks</span></span>  

 <span data-ttu-id="c0488-109">`ExceptionCatcherEnter`只有當 catch 點位於以及時 (JIT) 編譯器編譯的程式碼中時，才會呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="c0488-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="c0488-110">在非受控碼或執行時間內部程式碼中攔截到的例外狀況，不會呼叫此通知。</span><span class="sxs-lookup"><span data-stu-id="c0488-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="c0488-111">`objectId`因為垃圾收集可能會在通知之後移動物件，所以會再次傳遞值 `ExceptionThrown` 。</span><span class="sxs-lookup"><span data-stu-id="c0488-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="c0488-112">分析工具不應該在其實作為此方法的實中封鎖，因為堆疊可能不是處於允許垃圾收集的狀態，因此無法啟用搶先式垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="c0488-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="c0488-113">如果分析工具在此封鎖並嘗試垃圾收集，則執行時間會封鎖，直到回呼傳回為止。</span><span class="sxs-lookup"><span data-stu-id="c0488-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="c0488-114">分析工具在執行此方法時，不應呼叫 managed 程式碼，或以任何方式造成受控記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="c0488-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0488-115">需求</span><span class="sxs-lookup"><span data-stu-id="c0488-115">Requirements</span></span>  

 <span data-ttu-id="c0488-116">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="c0488-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0488-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c0488-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c0488-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0488-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0488-119">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0488-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0488-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0488-120">See also</span></span>

- [<span data-ttu-id="c0488-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="c0488-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="c0488-122">ExceptionCatcherLeave 方法</span><span class="sxs-lookup"><span data-stu-id="c0488-122">ExceptionCatcherLeave Method</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)
