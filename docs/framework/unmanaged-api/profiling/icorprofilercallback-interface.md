---
title: ICorProfilerCallback 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback
helpviewer_keywords:
- ICorProfilerCallback interface [.NET Framework profiling]
ms.assetid: 4bae06f7-94d7-4ba8-b250-648b2da78674
topic_type:
- apiref
ms.openlocfilehash: 487f347c19ab513f328a9f1a02601fc72c233eb5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449935"
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback 介面
Provides methods that are used by the common language runtime (CLR) to notify a code profiler when the events to which the profiler has subscribed occur.  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AppDomainCreationFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|Notifies the profiler that an application domain has been created.|  
|[AppDomainCreationStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|Notifies the profiler that an application domain is being created.|  
|[AppDomainShutdownFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|Notifies the profiler that an application domain has been unloaded from a process.|  
|[AppDomainShutdownStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|Notifies the profiler that an application domain is being unloaded from a process.|  
|[AssemblyLoadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|Notifies the profiler that an assembly has finished loading.|  
|[AssemblyLoadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|Notifies the profiler that an assembly is being loaded.|  
|[AssemblyUnloadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|Notifies the profiler that an assembly has been unloaded.|  
|[AssemblyUnloadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|Notifies the profiler that an assembly is being unloaded.|  
|[ClassLoadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|Notifies the profiler that a class has finished loading.|  
|[ClassLoadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|Notifies the profiler that a class is being loaded.|  
|[ClassUnloadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|Notifies the profiler that a class has finished unloading.|  
|[ClassUnloadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|Notifies the profiler that a class is being unloaded.|  
|[COMClassicVTableCreated 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|Notifies the profiler that a runtime callable wrapper (RCW) for the specified IID and class has been created.|  
|[COMClassicVTableDestroyed 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|Notifies the profiler that an RCW is being destroyed.|  
|[ExceptionCatcherEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|Notifies the profiler that control is being passed to the appropriate `catch` block.|  
|[ExceptionCatcherLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|Notifies the profiler that control is being passed out of the appropriate `catch` block.|  
|[ExceptionCLRCatcherExecute 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|Obsolete in the .NET Framework version 2.0.|  
|[ExceptionCLRCatcherFound 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|Obsolete in the .NET Framework 2.0.|  
|[ExceptionOSHandlerEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|未實作。 A profiler that needs unmanaged exception information must obtain this information through other means.|  
|[ExceptionOSHandlerLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|未實作。 A profiler that needs unmanaged exception information must obtain this information through other means.|  
|[ExceptionSearchCatcherFound 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|Notifies the profiler that the search phase of exception handling has located a handler for the exception that was thrown.|  
|[ExceptionSearchFilterEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|Notifies the profiler that a user filter is being executed.|  
|[ExceptionSearchFilterLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|Notifies the profiler that a user filter has just finished executing.|  
|[ExceptionSearchFunctionEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|Notifies the profiler that the search phase of exception handling has entered a function.|  
|[ExceptionSearchFunctionLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|Notifies the profiler that the search phase of exception handling has finished searching a function.|  
|[ExceptionThrown 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|Notifies the profiler that an exception has been thrown.|  
|[ExceptionUnwindFinallyEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|Notifies the profiler that the unwind phase of exception handling is entering a `finally` clause contained in the specified function.|  
|[ExceptionUnwindFinallyLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|Notifies the profiler that the unwind phase of exception handling has left a `finally` clause.|  
|[ExceptionUnwindFunctionEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|Notifies the profiler that the unwind phase of exception handling has entered a function.|  
|[ExceptionUnwindFunctionLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|Notifies the profiler that the unwind phase of exception handling has finished unwinding a function.|  
|[FunctionUnloadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|Notifies the profiler that the runtime has started to unload a function.|  
|[Initialize 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|Called to initialize the profiler whenever a new CLR application is started.|  
|[JITCachedFunctionSearchFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|Notifies the profiler that a search has finished for a function that was compiled previously using NGen.exe.|  
|[JITCachedFunctionSearchStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|Notifies the profiler that a search has started for a function that was compiled previously using NGen.exe.|  
|[JITCompilationFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|Notifies the profiler that the JIT compiler has finished compiling a function.|  
|[JITCompilationStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|Notifies the profiler that the just-in-time (JIT) compiler has started to compile a function.|  
|[JITFunctionPitched 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|Notifies the profiler that a function that has been JIT-compiled has been removed from memory.|  
|[JITInlining 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|Notifies the profiler that the JIT compiler is about to insert a function in line with another function.|  
|[ManagedToUnmanagedTransition 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|Notifies the profiler that a transition from managed code to unmanaged code has occurred.|  
|[ModuleAttachedToAssembly 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|Notifies the profiler that a module is being attached to its parent assembly.|  
|[ModuleLoadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|Notifies the profiler that a module has finished loading.|  
|[ModuleLoadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|Notifies the profiler that a module is being loaded.|  
|[ModuleUnloadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|Notifies the profiler that a module has finished unloading.|  
|[ModuleUnloadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|Notifies the profiler that a module is being unloaded.|  
|[MovedReferences 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|Notifies the profiler about object references that were moved during garbage collection.|  
|[ObjectAllocated 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|Notifies the profiler that memory within the heap has been allocated for an object.|  
|[ObjectReferences 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|Notifies the profiler about objects in memory referenced by the specified object.|  
|[ObjectsAllocatedByClass 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|Notifies the profiler about the number of instances of each specified class that have been created since the previous garbage collection.|  
|[RemotingClientInvocationFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|Notifies the profiler that a remoting call has run to completion on the client.|  
|[RemotingClientInvocationStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|Notifies the profiler that a remoting call has started.|  
|[RemotingClientReceivingReply 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|Notifies the profiler that the server-side portion of a remoting call has completed and the client is now receiving and about to process the reply.|  
|[RemotingClientSendingMessage 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|Notifies the profiler that the client is sending a request to the server.|  
|[RemotingServerInvocationReturned 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|Notifies the profiler that the process has finished invoking a method in response to a remote method invocation request.|  
|[RemotingServerInvocationStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|Notifies the profiler that the process is invoking a method in response to a remote method invocation request.|  
|[RemotingServerReceivingMessage 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|Notifies the profiler that the process is receiving a remote method invocation or activation request.|  
|[RemotingServerSendingReply 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|Notifies the profiler that the process has finished processing a remote method invocation request and is about to transmit the reply through a channel.|  
|[RootReferences 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|Notifies the profiler with information about root references after garbage collection.|  
|[RuntimeResumeFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|Notifies the profiler that the runtime has resumed all runtime threads and has returned to normal operation.|  
|[RuntimeResumeStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|Notifies the profiler that the runtime is resuming all run-time threads.|  
|[RuntimeSuspendAborted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|Notifies the profiler that the runtime has aborted the run-time suspension that was occurring.|  
|[RuntimeSuspendFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|Notifies the profiler that the runtime has completed suspension of all run-time threads.|  
|[RuntimeSuspendStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|Notifies the profiler that the runtime is about to suspend all run-time threads.|  
|[RuntimeThreadResumed 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|Notifies the profiler that the specified thread has resumed after being suspended.|  
|[RuntimeThreadSuspended 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|Notifies the profiler that the specified thread has been, or is about to be, suspended.|  
|[Shutdown 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|Notifies the profiler that the application is shutting down.|  
|[ThreadAssignedToOSThread 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|Notifies the profiler that a managed thread is being implemented using a particular operating system (OS) thread.|  
|[ThreadCreated 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|Notifies the profiler that a thread has been created.|  
|[ThreadDestroyed 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|Notifies the profiler that a thread has been destroyed.|  
|[UnmanagedToManagedTransition 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|Notifies the profiler that a transition from unmanaged code to managed code has occurred.|  
  
## <a name="remarks"></a>備註  
 The CLR calls a method in the `ICorProfilerCallback` (or [ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) interface to notify the profiler when an event, to which the profiler has subscribed, occurs. This is the primary callback interface through which the CLR communicates with the code profiler.  
  
 A code profiler must implement the methods of the `ICorProfilerCallback` interface. For the .NET Framework version 2.0 or later, the profiler must also implement the `ICorProfilerCallback2` methods. Each method implementation must return an HRESULT that has a value of S_OK on success or E_FAIL on failure. Currently, the CLR ignores the HRESULT that is returned by each callback except [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 In the Microsoft Windows registry, a code profiler must register its Component Object Model (COM) object that implements the `ICorProfilerCallback` and `ICorProfilerCallback2` interfaces. A code profiler subscribes to the events for which it wants to receive notification by calling [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). This is usually done in the profiler's implementation of [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). The profiler is then able to receive notification from the runtime when an event is about to occur or has just occurred in an executing runtime process.  
  
> [!NOTE]
> The profiler registers a single COM object. If the profiler is targeting the .NET Framework version 1.0 or 1.1, that COM object needs to implement only the methods of `ICorProfilerCallback`. If it is targeting .NET Framework version 2.0 or later, the COM object must also implement the methods of `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
