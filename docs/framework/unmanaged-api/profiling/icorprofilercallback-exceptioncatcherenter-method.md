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
ms.openlocfilehash: 534e0672820cc2509f32765274ad970fda69ec5d
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866503"
---
# <a name="icorprofilercallbackexceptioncatcherenter-method"></a><span data-ttu-id="0fd4b-102">ICorProfilerCallback::ExceptionCatcherEnter 方法</span><span class="sxs-lookup"><span data-stu-id="0fd4b-102">ICorProfilerCallback::ExceptionCatcherEnter Method</span></span>
<span data-ttu-id="0fd4b-103">通知分析工具，控制項正傳遞至適當的 `catch` 區塊。</span><span class="sxs-lookup"><span data-stu-id="0fd4b-103">Notifies the profiler that control is being passed to the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fd4b-104">語法</span><span class="sxs-lookup"><span data-stu-id="0fd4b-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherEnter(  
    [in] FunctionID functionId,  
    [in] ObjectID   objectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fd4b-105">參數</span><span class="sxs-lookup"><span data-stu-id="0fd4b-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="0fd4b-106">\[in] 包含 `catch` 區塊之函式的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0fd4b-106">\[in] The identifier of the function containing the `catch` block.</span></span>
  
- `objectId`

  <span data-ttu-id="0fd4b-107">中的 \[] 所處理之例外狀況的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0fd4b-107">\[in] The identifier of the exception being handled.</span></span>

## <a name="remarks"></a><span data-ttu-id="0fd4b-108">備註</span><span class="sxs-lookup"><span data-stu-id="0fd4b-108">Remarks</span></span>  
 <span data-ttu-id="0fd4b-109">只有當 catch 點位於以即時（JIT）編譯器編譯的程式碼中時，才會呼叫 `ExceptionCatcherEnter` 方法。</span><span class="sxs-lookup"><span data-stu-id="0fd4b-109">The `ExceptionCatcherEnter` method is called only if the catch point is in code compiled with the just-in-time (JIT) compiler.</span></span> <span data-ttu-id="0fd4b-110">在非受控碼或執行時間的內部程式碼中攔截到的例外狀況不會呼叫此通知。</span><span class="sxs-lookup"><span data-stu-id="0fd4b-110">An exception that is caught in unmanaged code or in the internal code of the runtime will not call this notification.</span></span> <span data-ttu-id="0fd4b-111">因為 `ExceptionThrown` 通知之後，垃圾收集可能已經移動物件，所以會再次傳遞 `objectId` 值。</span><span class="sxs-lookup"><span data-stu-id="0fd4b-111">The `objectId` value is passed again since a garbage collection could have moved the object since the `ExceptionThrown` notification.</span></span>  
  
 <span data-ttu-id="0fd4b-112">分析工具不應在此方法的執行中封鎖，因為堆疊可能不是處於允許垃圾收集的狀態，因此無法啟用「搶先垃圾收集」。</span><span class="sxs-lookup"><span data-stu-id="0fd4b-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="0fd4b-113">如果分析工具在此處封鎖並嘗試垃圾收集，執行時間將會封鎖，直到這個回呼傳回為止。</span><span class="sxs-lookup"><span data-stu-id="0fd4b-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="0fd4b-114">分析工具的此方法的執行不應呼叫 managed 程式碼，或以任何方式進行，以造成 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="0fd4b-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fd4b-115">需求</span><span class="sxs-lookup"><span data-stu-id="0fd4b-115">Requirements</span></span>  
 <span data-ttu-id="0fd4b-116">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0fd4b-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fd4b-117">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0fd4b-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0fd4b-118">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fd4b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fd4b-119">**.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fd4b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fd4b-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="0fd4b-120">See also</span></span>

- [<span data-ttu-id="0fd4b-121">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="0fd4b-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0fd4b-122">ExceptionCatcherLeave 方法</span><span class="sxs-lookup"><span data-stu-id="0fd4b-122">ExceptionCatcherLeave Method</span></span>](icorprofilercallback-exceptioncatcherleave-method.md)
