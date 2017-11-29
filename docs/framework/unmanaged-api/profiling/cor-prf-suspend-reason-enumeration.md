---
title: "COR_PRF_SUSPEND_REASON 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_SUSPEND_REASON
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_SUSPEND_REASON
helpviewer_keywords: COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: aef9688d3da047645d53f6fcf113153393780c8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="corprfsuspendreason-enumeration"></a><span data-ttu-id="0a15b-102">COR_PRF_SUSPEND_REASON 列舉</span><span class="sxs-lookup"><span data-stu-id="0a15b-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="0a15b-103">指出執行階段已暫止的原因。</span><span class="sxs-lookup"><span data-stu-id="0a15b-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a15b-104">語法</span><span class="sxs-lookup"><span data-stu-id="0a15b-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="0a15b-105">成員</span><span class="sxs-lookup"><span data-stu-id="0a15b-105">Members</span></span>  
  
|<span data-ttu-id="0a15b-106">成員</span><span class="sxs-lookup"><span data-stu-id="0a15b-106">Member</span></span>|<span data-ttu-id="0a15b-107">說明</span><span class="sxs-lookup"><span data-stu-id="0a15b-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="0a15b-108">執行階段會暫停，未指定原因。</span><span class="sxs-lookup"><span data-stu-id="0a15b-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="0a15b-109">執行階段會暫停服務記憶體回收要求。</span><span class="sxs-lookup"><span data-stu-id="0a15b-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="0a15b-110">記憶體回收相關集合回呼之間發生[icorprofilercallback:: Runtimesuspendfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)和[icorprofilercallback:: Runtimeresumestarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)回呼。</span><span class="sxs-lookup"><span data-stu-id="0a15b-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="0a15b-111">執行階段會暫停，讓`AppDomain`可以關機。</span><span class="sxs-lookup"><span data-stu-id="0a15b-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="0a15b-112">執行階段暫停時，執行階段會判定哪一個執行緒中`AppDomain`也就是正在關閉，並將它們設中止時即會回復。</span><span class="sxs-lookup"><span data-stu-id="0a15b-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="0a15b-113">有沒有`AppDomain`-擱置期間的特定回呼。</span><span class="sxs-lookup"><span data-stu-id="0a15b-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="0a15b-114">執行階段會暫停，以便推銷程式碼進行。</span><span class="sxs-lookup"><span data-stu-id="0a15b-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="0a15b-115">推銷程式碼展示僅當在 just-in-time (JIT) 編譯器在作用中與推銷程式碼啟用。</span><span class="sxs-lookup"><span data-stu-id="0a15b-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="0a15b-116">程式碼之間發生推銷碼回呼`ICorProfilerCallback::RuntimeSuspendFinished`和`ICorProfilerCallback::RuntimeResumeStarted`回呼。</span><span class="sxs-lookup"><span data-stu-id="0a15b-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="0a15b-117">**注意：** CLR JIT 不形函式在.NET Framework 2.0 版中，所以此值不會使用 2.0 中。</span><span class="sxs-lookup"><span data-stu-id="0a15b-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="0a15b-118">執行階段會暫停，讓它可以關機。</span><span class="sxs-lookup"><span data-stu-id="0a15b-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="0a15b-119">它必須暫停所有執行緒完成作業。</span><span class="sxs-lookup"><span data-stu-id="0a15b-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="0a15b-120">暫止執行階段同處理序偵錯。</span><span class="sxs-lookup"><span data-stu-id="0a15b-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="0a15b-121">執行階段會暫停來準備記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="0a15b-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="0a15b-122">執行階段會暫停進行 JIT 重新編譯。</span><span class="sxs-lookup"><span data-stu-id="0a15b-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a15b-123">備註</span><span class="sxs-lookup"><span data-stu-id="0a15b-123">Remarks</span></span>  
 <span data-ttu-id="0a15b-124">允許在 unmanaged 程式碼中的所有執行階段執行緒繼續執行，直到嘗試重新進入執行階段，此時它們也會暫止之前執行階段會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="0a15b-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="0a15b-125">這也適用於新的執行緒進入執行階段。</span><span class="sxs-lookup"><span data-stu-id="0a15b-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="0a15b-126">在執行階段內的所有執行緒會立即暫停，如果它們是在可中斷的程式碼，或是要求暫止時執行到可中斷的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0a15b-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a15b-127">需求</span><span class="sxs-lookup"><span data-stu-id="0a15b-127">Requirements</span></span>  
 <span data-ttu-id="0a15b-128">**平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="0a15b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a15b-129">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0a15b-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0a15b-130">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a15b-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a15b-131">**.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a15b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a15b-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a15b-132">See Also</span></span>  
 [<span data-ttu-id="0a15b-133">分析列舉</span><span class="sxs-lookup"><span data-stu-id="0a15b-133">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
