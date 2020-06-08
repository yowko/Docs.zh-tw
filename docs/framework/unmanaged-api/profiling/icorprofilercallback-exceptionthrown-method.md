---
title: ICorProfilerCallback::ExceptionThrown 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
ms.openlocfilehash: cd8030d6e57932a4605413fc2acc25a59de6c385
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500165"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="0f446-102">ICorProfilerCallback::ExceptionThrown 方法</span><span class="sxs-lookup"><span data-stu-id="0f446-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="0f446-103">通知分析工具已擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="0f446-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0f446-104">只有在例外狀況到達 managed 程式碼時，才會呼叫這個函式。</span><span class="sxs-lookup"><span data-stu-id="0f446-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f446-105">語法</span><span class="sxs-lookup"><span data-stu-id="0f446-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f446-106">參數</span><span class="sxs-lookup"><span data-stu-id="0f446-106">Parameters</span></span>

- `thrownObjectId`

  <span data-ttu-id="0f446-107">\[in] 導致擲回例外狀況之物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="0f446-107">\[in] The ID of the object that caused the exception to be thrown.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="0f446-108">備註</span><span class="sxs-lookup"><span data-stu-id="0f446-108">Remarks</span></span>  
 <span data-ttu-id="0f446-109">分析工具不應在此方法的執行中封鎖，因為堆疊可能不是處於允許垃圾收集的狀態，因此無法啟用「搶先垃圾收集」。</span><span class="sxs-lookup"><span data-stu-id="0f446-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="0f446-110">如果分析工具在此處封鎖並嘗試垃圾收集，執行時間將會封鎖，直到這個回呼傳回為止。</span><span class="sxs-lookup"><span data-stu-id="0f446-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="0f446-111">分析工具的此方法的執行不應呼叫 managed 程式碼，或以任何方式進行，以造成 managed 記憶體配置。</span><span class="sxs-lookup"><span data-stu-id="0f446-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f446-112">規格需求</span><span class="sxs-lookup"><span data-stu-id="0f446-112">Requirements</span></span>  
 <span data-ttu-id="0f446-113">**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0f446-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f446-114">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0f446-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0f446-115">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0f446-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0f446-116">**.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f446-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f446-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f446-117">See also</span></span>

- [<span data-ttu-id="0f446-118">ICorProfilerCallback 介面</span><span class="sxs-lookup"><span data-stu-id="0f446-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
