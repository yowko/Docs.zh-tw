---
title: COR_PRF_SUSPEND_REASON 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
ms.openlocfilehash: f7d76c72ed5db95425f5b1fa2db5e4346983daa4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95696670"
---
# <a name="cor_prf_suspend_reason-enumeration"></a><span data-ttu-id="f149d-102">COR_PRF_SUSPEND_REASON 列舉</span><span class="sxs-lookup"><span data-stu-id="f149d-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>

<span data-ttu-id="f149d-103">指出執行時間暫止的原因。</span><span class="sxs-lookup"><span data-stu-id="f149d-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f149d-104">語法</span><span class="sxs-lookup"><span data-stu-id="f149d-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="f149d-105">成員</span><span class="sxs-lookup"><span data-stu-id="f149d-105">Members</span></span>  
  
|<span data-ttu-id="f149d-106">member</span><span class="sxs-lookup"><span data-stu-id="f149d-106">Member</span></span>|<span data-ttu-id="f149d-107">描述</span><span class="sxs-lookup"><span data-stu-id="f149d-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="f149d-108">執行時間因未指定原因而暫止。</span><span class="sxs-lookup"><span data-stu-id="f149d-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="f149d-109">執行時間已暫止，以服務垃圾收集要求。</span><span class="sxs-lookup"><span data-stu-id="f149d-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="f149d-110">垃圾收集相關的回呼發生在 [ICorProfilerCallback：： RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) 與 [ICorProfilerCallback：： RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) 回呼之間。</span><span class="sxs-lookup"><span data-stu-id="f149d-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="f149d-111">執行時間已暫停，因此 `AppDomain` 可以關閉。</span><span class="sxs-lookup"><span data-stu-id="f149d-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="f149d-112">當執行時間暫止時，執行時間會判斷哪些執行緒正在關閉中， `AppDomain` 並將它們設定為在繼續時中止。</span><span class="sxs-lookup"><span data-stu-id="f149d-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="f149d-113">`AppDomain`這種暫停期間沒有特定的回呼。</span><span class="sxs-lookup"><span data-stu-id="f149d-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="f149d-114">執行時間已暫止，因此可能會發生程式碼推銷。</span><span class="sxs-lookup"><span data-stu-id="f149d-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="f149d-115">只有當即時 (JIT) 編譯器在啟用程式碼推銷的情況下，才會接踵而來程式碼推銷。</span><span class="sxs-lookup"><span data-stu-id="f149d-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="f149d-116">程式碼推銷回呼是在 `ICorProfilerCallback::RuntimeSuspendFinished` 和 `ICorProfilerCallback::RuntimeResumeStarted` 回呼之間進行。</span><span class="sxs-lookup"><span data-stu-id="f149d-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="f149d-117">**注意：**  CLR JIT 不會將 .NET Framework 版本2.0 中的函式，因此不會在2.0 中使用此值。</span><span class="sxs-lookup"><span data-stu-id="f149d-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="f149d-118">執行時間已暫止，使其可以關閉。</span><span class="sxs-lookup"><span data-stu-id="f149d-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="f149d-119">它必須暫停所有線程才能完成作業。</span><span class="sxs-lookup"><span data-stu-id="f149d-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="f149d-120">執行時間已暫止以進行同進程的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="f149d-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="f149d-121">暫停執行時間以準備進行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="f149d-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="f149d-122">暫停執行時間以進行 JIT 重新編譯。</span><span class="sxs-lookup"><span data-stu-id="f149d-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f149d-123">備註</span><span class="sxs-lookup"><span data-stu-id="f149d-123">Remarks</span></span>  

 <span data-ttu-id="f149d-124">在非受控碼中的所有運行時間表程都可以繼續執行，直到他們嘗試重新進入執行時間為止，此時它們也會暫止，直到執行時間恢復為止。</span><span class="sxs-lookup"><span data-stu-id="f149d-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="f149d-125">這也適用于進入執行時間的新執行緒。</span><span class="sxs-lookup"><span data-stu-id="f149d-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="f149d-126">執行時間中的所有線程如果是可中斷程式碼，則會立即暫停，或在到達可中斷的程式碼時要求暫停。</span><span class="sxs-lookup"><span data-stu-id="f149d-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f149d-127">需求</span><span class="sxs-lookup"><span data-stu-id="f149d-127">Requirements</span></span>  

 <span data-ttu-id="f149d-128">**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="f149d-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f149d-129">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f149d-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f149d-130">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f149d-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f149d-131">**.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f149d-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f149d-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f149d-132">See also</span></span>

- [<span data-ttu-id="f149d-133">分析列舉</span><span class="sxs-lookup"><span data-stu-id="f149d-133">Profiling Enumerations</span></span>](profiling-enumerations.md)
