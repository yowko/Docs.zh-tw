---
title: ICorProfilerCallback::ExceptionCatcherLeave 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCatcherLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCatcherLeave
helpviewer_keywords:
- ExceptionCatcherLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCatcherLeave method [.NET Framework profiling]
ms.assetid: 1f3dbdf5-db0c-4b07-bbb7-375de2a63673
topic_type:
- apiref
ms.openlocfilehash: c0a24a8f9b7c40d87f9b9b6fe77eba7d6c0ea89f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700024"
---
# <a name="icorprofilercallbackexceptioncatcherleave-method"></a><span data-ttu-id="77bdd-102">ICorProfilerCallback::ExceptionCatcherLeave 方法</span><span class="sxs-lookup"><span data-stu-id="77bdd-102">ICorProfilerCallback::ExceptionCatcherLeave Method</span></span>

<span data-ttu-id="77bdd-103">通知分析工具，控制項即將從適當的 `catch` 區塊傳遞。</span><span class="sxs-lookup"><span data-stu-id="77bdd-103">Notifies the profiler that control is being passed out of the appropriate `catch` block.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77bdd-104">語法</span><span class="sxs-lookup"><span data-stu-id="77bdd-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCatcherLeave();  
```  
  
## <a name="remarks"></a><span data-ttu-id="77bdd-105">備註</span><span class="sxs-lookup"><span data-stu-id="77bdd-105">Remarks</span></span>  

 <span data-ttu-id="77bdd-106">分析工具不應該在其實作為此方法的實中封鎖，因為堆疊可能不是處於允許垃圾收集的狀態，因此無法啟用搶先式垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="77bdd-106">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="77bdd-107">如果分析工具在此封鎖並嘗試垃圾收集，則執行時間會封鎖，直到回呼傳回為止。</span><span class="sxs-lookup"><span data-stu-id="77bdd-107">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="77bdd-108">分析工具在執行此方法時，不應呼叫 managed 程式碼，或以任何方式造成受控記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="77bdd-108">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77bdd-109">需求</span><span class="sxs-lookup"><span data-stu-id="77bdd-109">Requirements</span></span>  

 <span data-ttu-id="77bdd-110">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="77bdd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77bdd-111">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="77bdd-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="77bdd-112">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77bdd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77bdd-113">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77bdd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77bdd-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77bdd-114">See also</span></span>

- [<span data-ttu-id="77bdd-115">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="77bdd-115">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="77bdd-116">ExceptionCatcherEnter 方法</span><span class="sxs-lookup"><span data-stu-id="77bdd-116">ExceptionCatcherEnter Method</span></span>](icorprofilercallback-exceptioncatcherenter-method.md)
