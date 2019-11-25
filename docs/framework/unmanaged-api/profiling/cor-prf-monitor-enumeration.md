---
title: COR_PRF_MONITOR 列舉
ms.date: 03/30/2017
api_name:
- COR_PRF_MONITOR
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_MONITOR
helpviewer_keywords:
- COR_PRF_MONITOR enumeration [.NET Framework profiling]
ms.assetid: 9294d702-b4e5-441c-a930-e63d27b86bfd
topic_type:
- apiref
ms.openlocfilehash: 321ad53ca5f773191c5b5d1084b36caa6aeae4dc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137054"
---
# <a name="cor_prf_monitor-enumeration"></a><span data-ttu-id="17ea7-102">COR_PRF_MONITOR 列舉</span><span class="sxs-lookup"><span data-stu-id="17ea7-102">COR_PRF_MONITOR Enumeration</span></span>
<span data-ttu-id="17ea7-103">包含值，這些值用於指定分析工具想要訂閱的行為、功能或事件。</span><span class="sxs-lookup"><span data-stu-id="17ea7-103">Contains values that are used to specify behavior, capabilities, or events to which the profiler wishes to subscribe.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17ea7-104">語法</span><span class="sxs-lookup"><span data-stu-id="17ea7-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_MONITOR_NONE                = 0x00000000,  
    COR_PRF_MONITOR_FUNCTION_UNLOADS    = 0x00000001,  
    COR_PRF_MONITOR_CLASS_LOADS         = 0x00000002,  
    COR_PRF_MONITOR_MODULE_LOADS        = 0x00000004,  
    COR_PRF_MONITOR_ASSEMBLY_LOADS      = 0x00000008,  
    COR_PRF_MONITOR_APPDOMAIN_LOADS     = 0x00000010,  
    COR_PRF_MONITOR_JIT_COMPILATION     = 0x00000020,  
    COR_PRF_MONITOR_EXCEPTIONS          = 0x00000040,  
    COR_PRF_MONITOR_GC                  = 0x00000080,  
    COR_PRF_MONITOR_OBJECT_ALLOCATED    = 0x00000100,  
    COR_PRF_MONITOR_THREADS             = 0x00000200,  
    COR_PRF_MONITOR_REMOTING            = 0x00000400,  
    COR_PRF_MONITOR_CODE_TRANSITIONS    = 0x00000800,  
    COR_PRF_MONITOR_ENTERLEAVE          = 0x00001000,  
    COR_PRF_MONITOR_CCW                 = 0x00002000,  
    COR_PRF_MONITOR_REMOTING_COOKIE     = 0x00004000 |   
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_REMOTING_ASYNC      = 0x00008000 |   
                                          COR_PRF_MONITOR_REMOTING,  
    COR_PRF_MONITOR_SUSPENDS            = 0x00010000,  
    COR_PRF_MONITOR_CACHE_SEARCHES      = 0x00020000,  
    COR_PRF_ENABLE_REJIT                = 0x00040000,  
    COR_PRF_ENABLE_INPROC_DEBUGGING     = 0x00080000,  
    COR_PRF_ENABLE_JIT_MAPS             = 0x00100000,  
    COR_PRF_DISABLE_INLINING            = 0x00200000,  
    COR_PRF_DISABLE_OPTIMIZATIONS       = 0x00400000,  
    COR_PRF_ENABLE_OBJECT_ALLOCATED     = 0x00800000,  
    COR_PRF_MONITOR_CLR_EXCEPTIONS      = 0x01000000,  
    COR_PRF_MONITOR_ALL                 = 0x0107FFFF,  
    COR_PRF_ENABLE_FUNCTION_ARGS        = 0X02000000,  
    COR_PRF_ENABLE_FUNCTION_RETVAL      = 0X04000000,  
    COR_PRF_ENABLE_FRAME_INFO           = 0X08000000,  
    COR_PRF_ENABLE_STACK_SNAPSHOT       = 0X10000000,  
    COR_PRF_USE_PROFILE_IMAGES          = 0x20000000,  
    COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST  
                                        = 0x40000000,  
    COR_PRF_DISABLE_ALL_NGEN_IMAGES     = 0x80000000,  
    COR_PRF_ALL                         = 0x8FFFFFFF,  
    COR_PRF_REQUIRE_PROFILE_IMAGE       = COR_PRF_USE_PROFILE_IMAGES |   
                                          COR_PRF_MONITOR_CODE_TRANSITIONS |   
                                          COR_PRF_MONITOR_ENTERLEAVE,  
    COR_PRF_ALLOWABLE_AFTER_ATTACH      = COR_PRF_MONITOR_THREADS |  
                                          COR_PRF_MONITOR_MODULE_LOADS |  
                                          COR_PRF_MONITOR_ASSEMBLY_LOADS |  
                                          COR_PRF_MONITOR_APPDOMAIN_LOADS |  
                                          COR_PRF_ENABLE_STACK_SNAPSHOT |  
                                          COR_PRF_MONITOR_GC |  
                                          COR_PRF_MONITOR_SUSPENDS |  
                                          COR_PRF_MONITOR_CLASS_LOADS |  
                                          COR_PRF_MONITOR_JIT_COMPILATION,  
    COR_PRF_MONITOR_IMMUTABLE           = COR_PRF_MONITOR_CODE_TRANSITIONS |  
                                          COR_PRF_MONITOR_REMOTING |  
                                          COR_PRF_MONITOR_REMOTING_COOKIE |  
                                          COR_PRF_MONITOR_REMOTING_ASYNC |  
                                          COR_PRF_ENABLE_REJIT |  
                                          COR_PRF_ENABLE_INPROC_DEBUGGING |  
                                          COR_PRF_ENABLE_JIT_MAPS |  
                                          COR_PRF_DISABLE_OPTIMIZATIONS |  
                                          COR_PRF_DISABLE_INLINING |  
                                          COR_PRF_ENABLE_OBJECT_ALLOCATED |  
                                          COR_PRF_ENABLE_FUNCTION_ARGS |  
                                          COR_PRF_ENABLE_FUNCTION_RETVAL |  
                                          COR_PRF_ENABLE_FRAME_INFO |  
                                          COR_PRF_USE_PROFILE_IMAGES |  
                     COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST |  
                                          COR_PRF_DISABLE_ALL_NGEN_IMAGES  
} COR_PRF_MONITOR;  
```  
  
## <a name="members"></a><span data-ttu-id="17ea7-105">Members</span><span class="sxs-lookup"><span data-stu-id="17ea7-105">Members</span></span>  
 <span data-ttu-id="17ea7-106">下列各節依類別列出 `COR_PRF_MONITOR` 列舉成員。</span><span class="sxs-lookup"><span data-stu-id="17ea7-106">The following sections list `COR_PRF_MONITOR` enumeration members by category.</span></span> <span data-ttu-id="17ea7-107">分類包括：</span><span class="sxs-lookup"><span data-stu-id="17ea7-107">The categories are:</span></span>  
  
- [<span data-ttu-id="17ea7-108">未設定任何旗標</span><span class="sxs-lookup"><span data-stu-id="17ea7-108">No flags set</span></span>](#None)  
  
- [<span data-ttu-id="17ea7-109">回呼旗標</span><span class="sxs-lookup"><span data-stu-id="17ea7-109">Callback flags</span></span>](#Callback)  
  
- [<span data-ttu-id="17ea7-110">功能啟用旗標</span><span class="sxs-lookup"><span data-stu-id="17ea7-110">Feature-enabling flags</span></span>](#Feature)  
  
- [<span data-ttu-id="17ea7-111">設定旗標</span><span class="sxs-lookup"><span data-stu-id="17ea7-111">Configuration flags</span></span>](#Config)  
  
- [<span data-ttu-id="17ea7-112">複合旗標</span><span class="sxs-lookup"><span data-stu-id="17ea7-112">Composite flags</span></span>](#Composite)  
  
<a name="None"></a>   
### <a name="no-flags-set"></a><span data-ttu-id="17ea7-113">未設定任何旗標</span><span class="sxs-lookup"><span data-stu-id="17ea7-113">No flags set</span></span>  
  
|<span data-ttu-id="17ea7-114">成員</span><span class="sxs-lookup"><span data-stu-id="17ea7-114">Member</span></span>|<span data-ttu-id="17ea7-115">描述</span><span class="sxs-lookup"><span data-stu-id="17ea7-115">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|<span data-ttu-id="17ea7-116">沒有設定旗標。</span><span class="sxs-lookup"><span data-stu-id="17ea7-116">No flags are set.</span></span>|  
  
<a name="Callback"></a>   
### <a name="callback-flags"></a><span data-ttu-id="17ea7-117">回呼旗標</span><span class="sxs-lookup"><span data-stu-id="17ea7-117">Callback flags</span></span>  
  
|<span data-ttu-id="17ea7-118">成員</span><span class="sxs-lookup"><span data-stu-id="17ea7-118">Member</span></span>|<span data-ttu-id="17ea7-119">描述</span><span class="sxs-lookup"><span data-stu-id="17ea7-119">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="17ea7-120">啟用所有回呼事件。</span><span class="sxs-lookup"><span data-stu-id="17ea7-120">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|<span data-ttu-id="17ea7-121">控制 `AppDomainCreation*`ICorProfilerCallback`AppDomainShutdown*` 介面中的 [ 及 ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-121">Controls the `AppDomainCreation*` and `AppDomainShutdown*` callbacks in the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|<span data-ttu-id="17ea7-122">控制 `AssemblyLoad*`ICorProfilerCallback`AssemblyUnload*` 介面中的 [ 及 ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-122">Controls the `AssemblyLoad*` and `AssemblyUnload*` callbacks in the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|<span data-ttu-id="17ea7-123">控制 `JITCachedFunctionSearch*`ICorProfilerCallback[ 介面中的 ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-123">Controls the `JITCachedFunctionSearch*` callbacks in the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.</span></span><br /><br /> <span data-ttu-id="17ea7-124">此旗標的行為已在 .NET Framework 2.0 版中變更。</span><span class="sxs-lookup"><span data-stu-id="17ea7-124">The behavior of this flag is changed in the .NET Framework version 2.0.</span></span>|  
|`COR_PRF_MONITOR_CCW`|<span data-ttu-id="17ea7-125">控制 `COMClassicVTable*`ICorProfilerCallback[ 介面中的 ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-125">Controls the `COMClassicVTable*` callbacks in the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLASS_LOADS`|<span data-ttu-id="17ea7-126">控制 `ClassLoad*`ICorProfilerCallback`ClassUnload*` 介面中的 [ 及 ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-126">Controls the `ClassLoad*` and `ClassUnload*` callbacks in the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|<span data-ttu-id="17ea7-127">控制 `ExceptionCLRCatcher*`ICorProfilerCallback[ 介面中的 ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-127">Controls the `ExceptionCLRCatcher*` callbacks in the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|<span data-ttu-id="17ea7-128">控制 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) 介面中的 [UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) 及 [ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-128">Controls the [UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) and [ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) callbacks in the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface</span></span>|  
|`COR_PRF_MONITOR_ENTERLEAVE`|<span data-ttu-id="17ea7-129">控制 `FunctionEnter*`、`FunctionLeave*`和 `FunctionTailCall*`[分析全域靜態](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)函式。</span><span class="sxs-lookup"><span data-stu-id="17ea7-129">Controls the `FunctionEnter*`,  `FunctionLeave*`, and `FunctionTailCall*`[profiling global static functions](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md).</span></span>|  
|`COR_PRF_MONITOR_EXCEPTIONS`|<span data-ttu-id="17ea7-130">控制 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md) 介面中的 `ExceptionSearch*`ExceptionThrown`ExceptionOSHandler*` 回呼以及 `ExceptionUnwind*`、`ExceptionCatcher*`、[ 及 ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-130">Controls the [ExceptionThrown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md) callback and the `ExceptionSearch*`, `ExceptionOSHandler*`, `ExceptionUnwind*`, and `ExceptionCatcher*` callbacks in the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|<span data-ttu-id="17ea7-131">控制 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md) 介面中的 [FunctionUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-131">Controls the [FunctionUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md) callback in the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_GC`|<span data-ttu-id="17ea7-132">控制 [ 介面中的 ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)GarbageCollectionStarted[、](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)GarbageCollectionFinished[、](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)MovedReferences[、](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)MovedReferences2[、](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)SurvivingReferences[、](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)SurvivingReferences2[、](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)ObjectReferences[、](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)ObjectsAllocatedByClass[、](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)RootReferences[、](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)RootReferences2[、](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)HandleCreated[、](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)HandleDestroyed[ 及 ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)FinalizeableObjectQueued`ICorProfilerCallback*` 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-132">Controls the [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md),   [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md),  [MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md), [MovedReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md),    [SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md),  [SurvivingReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md), [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md),   [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md),  [RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md), [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md), [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md),  [HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md), and [FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) callbacks in the `ICorProfilerCallback*` interfaces.</span></span> <span data-ttu-id="17ea7-133">配置 `COR_PRF_MONITOR_GC` 時，會關閉並行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="17ea7-133">When `COR_PRF_MONITOR_GC` is allocated, concurrent garbage collection is turned off.</span></span>|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|<span data-ttu-id="17ea7-134">控制 `JITCompilation*`ICorProfilerCallback[ 介面中的 ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)、[JITFunctionPitched](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) 及 [JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-134">Controls the `JITCompilation*`, [JITFunctionPitched](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md), and [JITInlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md) callbacks in the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_MODULE_LOADS`|<span data-ttu-id="17ea7-135">控制 `ModuleLoad*`ICorProfilerCallback`ModuleUnload*` 介面中的 [、](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) 及 [ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-135">Controls the `ModuleLoad*`,  `ModuleUnload*`, and [ModuleAttachedToAssembly](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md) callbacks in the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|<span data-ttu-id="17ea7-136">控制 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md) 介面中的 [ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-136">Controls the [ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md) callback in the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING`|<span data-ttu-id="17ea7-137">控制 `Remoting*`ICorProfilerCallback[ 介面中的 ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-137">Controls the `Remoting*` callbacks in the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|<span data-ttu-id="17ea7-138">控制 `Remoting*` 回呼是否會監視非同步事件。</span><span class="sxs-lookup"><span data-stu-id="17ea7-138">Controls whether the `Remoting*` callbacks will monitor asynchronous events.</span></span>|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|<span data-ttu-id="17ea7-139">控制 Cookie 是否傳遞至 `Remoting*` 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-139">Controls whether a cookie is passed to the `Remoting*` callbacks.</span></span>|  
|`COR_PRF_MONITOR_SUSPENDS`|<span data-ttu-id="17ea7-140">控制 `RuntimeSuspend*`ICorProfilerCallback`RuntimeResume*` 介面中的 [、](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)、[RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md) 及 [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-140">Controls the `RuntimeSuspend*`, `RuntimeResume*`, [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md), and [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md) callbacks in the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) interface.</span></span>|  
|`COR_PRF_MONITOR_THREADS`|<span data-ttu-id="17ea7-141">控制 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md) 及 [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md) 介面中的 [ThreadCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)、[ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)、[ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) 及 [ThreadNameChanged](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-141">Controls the [ThreadCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md),  [ThreadDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md),  [ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md), and [ThreadNameChanged](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md) callbacks in the [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) and [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md) interfaces.</span></span>|  
  
<a name="Feature"></a>   
### <a name="feature-enabling-flags"></a><span data-ttu-id="17ea7-142">功能啟用旗標</span><span class="sxs-lookup"><span data-stu-id="17ea7-142">Feature-enabling flags</span></span>  
  
|<span data-ttu-id="17ea7-143">成員</span><span class="sxs-lookup"><span data-stu-id="17ea7-143">Member</span></span>|<span data-ttu-id="17ea7-144">描述</span><span class="sxs-lookup"><span data-stu-id="17ea7-144">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|<span data-ttu-id="17ea7-145">啟用透過搭配 `ClassID`FunctionEnter2[ 回呼所傳回的 ](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) 值呼叫 `COR_PRF_FRAME_INFO`GetFunctionInfo2[ 方法，擷取泛型函式的確切 ](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)。</span><span class="sxs-lookup"><span data-stu-id="17ea7-145">Enables the retrieval of an exact `ClassID` for a generic function by calling the [GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method with a `COR_PRF_FRAME_INFO` value returned by the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|<span data-ttu-id="17ea7-146">啟用使用 [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) 回呼，或 [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) 回呼及 [GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) 方法追蹤引數。</span><span class="sxs-lookup"><span data-stu-id="17ea7-146">Enables argument tracing using the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) callback or the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) callback and the [GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|<span data-ttu-id="17ea7-147">啟用使用 [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) 回呼，或 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) 回呼及 [GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) 方法追蹤傳回值。</span><span class="sxs-lookup"><span data-stu-id="17ea7-147">Enables tracing of return values by using the [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) callback or the [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) callback and [GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) method.</span></span>|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|<span data-ttu-id="17ea7-148">已取代。</span><span class="sxs-lookup"><span data-stu-id="17ea7-148">Deprecated.</span></span><br /><br /> <span data-ttu-id="17ea7-149">不支援同處理序偵錯。</span><span class="sxs-lookup"><span data-stu-id="17ea7-149">In process debugging is not supported.</span></span> <span data-ttu-id="17ea7-150">此旗標無效。</span><span class="sxs-lookup"><span data-stu-id="17ea7-150">This flag has no effect.</span></span>|  
|`COR_PRF_ENABLE_JIT_MAPS`|<span data-ttu-id="17ea7-151">已取代。</span><span class="sxs-lookup"><span data-stu-id="17ea7-151">Deprecated.</span></span><br /><br /> <span data-ttu-id="17ea7-152">允許分析工具使用 [GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) 取得 IL 與原生 (IL-to-native) 的對應。</span><span class="sxs-lookup"><span data-stu-id="17ea7-152">Allows the profiler to obtain IL-to-native maps by using [GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md).</span></span> <span data-ttu-id="17ea7-153">從 .NET Framework 2.0 開始，執行階段會一律追蹤 IL 與原生的對應；所以會一律將此旗標視為必須設定。</span><span class="sxs-lookup"><span data-stu-id="17ea7-153">Starting with the .NET Framework 2.0, the runtime always tracks IL-to-native maps; therefore, this flag is always considered to be set.</span></span>|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|<span data-ttu-id="17ea7-154">通知執行階段，分析工具可能想要物件配置通知。</span><span class="sxs-lookup"><span data-stu-id="17ea7-154">Informs the runtime that the profiler may want object allocation notifications.</span></span> <span data-ttu-id="17ea7-155">必須在初始化期間設定此旗標。</span><span class="sxs-lookup"><span data-stu-id="17ea7-155">This flag must be set during initialization.</span></span> <span data-ttu-id="17ea7-156">這可讓分析工具在後續使用 `COR_PRF_MONITOR_OBJECT_ALLOCATED` 旗標接收 [ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md) 回呼。</span><span class="sxs-lookup"><span data-stu-id="17ea7-156">It allows the profiler to subsequently use the `COR_PRF_MONITOR_OBJECT_ALLOCATED` flag to receive [ObjectAllocated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md) callbacks.</span></span>|  
|`COR_PRF_ENABLE_REJIT`|<span data-ttu-id="17ea7-157">啟用呼叫 [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) 及 [RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="17ea7-157">Enables calls to the [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md) and [RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md) methods.</span></span> <span data-ttu-id="17ea7-158">分析工具必須在啟動時設定此旗標。</span><span class="sxs-lookup"><span data-stu-id="17ea7-158">The profiler must set this flag on startup.</span></span>  <span data-ttu-id="17ea7-159">若分析工具指定此旗標，則必須也要指定 `COR_PRF_DISABLE_ALL_NGEN_IMAGES`。</span><span class="sxs-lookup"><span data-stu-id="17ea7-159">If the profiler specifies this flag, it must also specify `COR_PRF_DISABLE_ALL_NGEN_IMAGES`.</span></span>|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|<span data-ttu-id="17ea7-160">啟用呼叫 [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) 方法。</span><span class="sxs-lookup"><span data-stu-id="17ea7-160">Enables calls to the [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>|  
  
<a name="Config"></a>   
### <a name="configuration-flags"></a><span data-ttu-id="17ea7-161">組態旗標</span><span class="sxs-lookup"><span data-stu-id="17ea7-161">Configuration flags</span></span>  
  
|<span data-ttu-id="17ea7-162">成員</span><span class="sxs-lookup"><span data-stu-id="17ea7-162">Member</span></span>|<span data-ttu-id="17ea7-163">描述</span><span class="sxs-lookup"><span data-stu-id="17ea7-163">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|<span data-ttu-id="17ea7-164">防止載入所有原生映像 (包含分析工具增強型映像)。</span><span class="sxs-lookup"><span data-stu-id="17ea7-164">Prevents all native images (including profiler-enhanced images) from loading.</span></span>  <span data-ttu-id="17ea7-165">若指定此旗標及 `COR_PRF_USE_PROFILE_IMAGES` 旗標，則使用 `COR_PRF_DISABLE_ALL_NGEN_IMAGES`。</span><span class="sxs-lookup"><span data-stu-id="17ea7-165">If this flag and the `COR_PRF_USE_PROFILE_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
|`COR_PRF_DISABLE_INLINING`|<span data-ttu-id="17ea7-166">停用所有內嵌。</span><span class="sxs-lookup"><span data-stu-id="17ea7-166">Disables all inlining.</span></span>|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|<span data-ttu-id="17ea7-167">停用所有程式碼最佳化。</span><span class="sxs-lookup"><span data-stu-id="17ea7-167">Disables all code optimizations.</span></span>|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|<span data-ttu-id="17ea7-168">針對完全信任組件，停用通常在 Just-in-time (JIT) 編譯及類別載入期間完成的安全性透明度檢查。</span><span class="sxs-lookup"><span data-stu-id="17ea7-168">Disables security transparency checks that are normally done during just-in-time (JIT) compilation and class loading for full-trust assemblies.</span></span> <span data-ttu-id="17ea7-169">這可讓一些實作更容易執行。</span><span class="sxs-lookup"><span data-stu-id="17ea7-169">This can make some instrumentation easier to perform.</span></span>|  
|`COR_PRF_USE_PROFILE_IMAGES`|<span data-ttu-id="17ea7-170">使原生映像搜尋尋找分析工具增強型映像。</span><span class="sxs-lookup"><span data-stu-id="17ea7-170">Causes the native image search to look for profiler-enhanced images.</span></span> <span data-ttu-id="17ea7-171">若沒有找到指定組件的分析工具增強型映像，Common Language Runtime 會回復為該組件的 JIT。</span><span class="sxs-lookup"><span data-stu-id="17ea7-171">If no profiler-enhanced image is found for a given assembly, the common language runtime falls back to JIT for that assembly.</span></span> <span data-ttu-id="17ea7-172">若指定此旗標及 `COR_PRF_DISABLE_ALL_NGEN_IMAGES` 旗標，則使用 `COR_PRF_DISABLE_ALL_NGEN_IMAGES`。</span><span class="sxs-lookup"><span data-stu-id="17ea7-172">If this flag and the `COR_PRF_DISABLE_ALL_NGEN_IMAGES` flag are both specified, `COR_PRF_DISABLE_ALL_NGEN_IMAGES` is used.</span></span>|  
  
<a name="Composite"></a>   
### <a name="composite-flags"></a><span data-ttu-id="17ea7-173">組合旗標</span><span class="sxs-lookup"><span data-stu-id="17ea7-173">Composite flags</span></span>  
  
|<span data-ttu-id="17ea7-174">成員</span><span class="sxs-lookup"><span data-stu-id="17ea7-174">Member</span></span>|<span data-ttu-id="17ea7-175">描述</span><span class="sxs-lookup"><span data-stu-id="17ea7-175">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_ALL`|<span data-ttu-id="17ea7-176">代表所有 `COR_PRF_MONITOR` 旗標值。</span><span class="sxs-lookup"><span data-stu-id="17ea7-176">Represents all `COR_PRF_MONITOR` flag values.</span></span>|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|<span data-ttu-id="17ea7-177">代表所有 `COR_PRF_MONITOR` 旗標，這些旗標可在分析工具連結至執行中的應用程式之後加以設定。</span><span class="sxs-lookup"><span data-stu-id="17ea7-177">Represents all `COR_PRF_MONITOR` flags that can be set after the profiler is attached to a running app.</span></span> <span data-ttu-id="17ea7-178">語法區段指出此位元遮罩中存在的個別旗標。</span><span class="sxs-lookup"><span data-stu-id="17ea7-178">The syntax section indicates the individual flags that are present in this bitmask.</span></span>|  
|`COR_PRF_MONITOR_ALL`|<span data-ttu-id="17ea7-179">啟用所有回呼事件。</span><span class="sxs-lookup"><span data-stu-id="17ea7-179">Enables all callback events.</span></span>|  
|`COR_PRF_MONITOR_IMMUTABLE`|<span data-ttu-id="17ea7-180">代表所有 `COR_PRF_MONITOR` 旗標，這些旗標只能在初始化期間加以設定。</span><span class="sxs-lookup"><span data-stu-id="17ea7-180">Represents all `COR_PRF_MONITOR` flags that can be set only during initialization.</span></span> <span data-ttu-id="17ea7-181">嘗試在初始化之後變更任何這些旗標，會傳回指出失敗的 `HRESULT` 值。</span><span class="sxs-lookup"><span data-stu-id="17ea7-181">Trying to change any of these flags after initialization returns an `HRESULT` value that indicates failure.</span></span>|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|<span data-ttu-id="17ea7-182">代表需要設定檔增強影像的所有 `COR_PRF_MONITOR` 旗標。</span><span class="sxs-lookup"><span data-stu-id="17ea7-182">Represents all `COR_PRF_MONITOR` flags that require profile-enhanced images.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17ea7-183">備註</span><span class="sxs-lookup"><span data-stu-id="17ea7-183">Remarks</span></span>  
 <span data-ttu-id="17ea7-184">`COR_PRF_MONITOR` 值可用於搭配 [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) 及 [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) 方法，定義 Common Language Runtime 建立給分析工具的事件通知。</span><span class="sxs-lookup"><span data-stu-id="17ea7-184">A `COR_PRF_MONITOR` value is used with the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) and [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) methods to define the event notifications that the common language runtime makes to the profiler.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17ea7-185">需求</span><span class="sxs-lookup"><span data-stu-id="17ea7-185">Requirements</span></span>  
 <span data-ttu-id="17ea7-186">**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。</span><span class="sxs-lookup"><span data-stu-id="17ea7-186">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17ea7-187">**標頭：** CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="17ea7-187">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="17ea7-188">**程式庫：** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17ea7-188">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17ea7-189">**.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17ea7-189">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17ea7-190">請參閱</span><span class="sxs-lookup"><span data-stu-id="17ea7-190">See also</span></span>

- [<span data-ttu-id="17ea7-191">分析列舉</span><span class="sxs-lookup"><span data-stu-id="17ea7-191">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
- [<span data-ttu-id="17ea7-192">GetEventMask 方法</span><span class="sxs-lookup"><span data-stu-id="17ea7-192">GetEventMask Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)
- [<span data-ttu-id="17ea7-193">SetEventMask 方法</span><span class="sxs-lookup"><span data-stu-id="17ea7-193">SetEventMask Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)
