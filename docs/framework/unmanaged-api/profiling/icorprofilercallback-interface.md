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
ms.openlocfilehash: 891cca8ac47a3f8391bd7ab7b27b35d6318bbe0a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866282"
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback 介面
提供當分析工具已訂閱的事件發生時，common language runtime （CLR）用來通知程式碼分析工具的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AppDomainCreationFinished 方法](icorprofilercallback-appdomaincreationfinished-method.md)|通知分析工具已建立應用程式域。|  
|[AppDomainCreationStarted 方法](icorprofilercallback-appdomaincreationstarted-method.md)|通知分析工具，正在建立應用程式域。|  
|[AppDomainShutdownFinished 方法](icorprofilercallback-appdomainshutdownfinished-method.md)|通知分析工具，應用程式域已從進程中卸載。|  
|[AppDomainShutdownStarted 方法](icorprofilercallback-appdomainshutdownstarted-method.md)|通知分析工具，應用程式域正在從進程中卸載。|  
|[AssemblyLoadFinished 方法](icorprofilercallback-assemblyloadfinished-method.md)|通知分析工具元件已完成載入。|  
|[AssemblyLoadStarted 方法](icorprofilercallback-assemblyloadstarted-method.md)|通知分析工具已載入元件。|  
|[AssemblyUnloadFinished 方法](icorprofilercallback-assemblyunloadfinished-method.md)|通知分析工具元件已卸載。|  
|[AssemblyUnloadStarted 方法](icorprofilercallback-assemblyunloadstarted-method.md)|通知分析工具元件正在卸載。|  
|[ClassLoadFinished 方法](icorprofilercallback-classloadfinished-method.md)|通知 profiler，類別已完成載入。|  
|[ClassLoadStarted 方法](icorprofilercallback-classloadstarted-method.md)|通知分析工具，正在載入類別。|  
|[ClassUnloadFinished 方法](icorprofilercallback-classunloadfinished-method.md)|通知分析工具，類別已完成卸載。|  
|[ClassUnloadStarted 方法](icorprofilercallback-classunloadstarted-method.md)|通知分析工具，類別正在卸載。|  
|[COMClassicVTableCreated 方法](icorprofilercallback-comclassicvtablecreated-method.md)|通知分析工具，已建立指定之 IID 和類別的執行時間可呼叫包裝函式（RCW）。|  
|[COMClassicVTableDestroyed 方法](icorprofilercallback-comclassicvtabledestroyed-method.md)|通知分析工具，RCW 已終結。|  
|[ExceptionCatcherEnter 方法](icorprofilercallback-exceptioncatcherenter-method.md)|通知分析工具，控制項正傳遞至適當的 `catch` 區塊。|  
|[ExceptionCatcherLeave 方法](icorprofilercallback-exceptioncatcherleave-method.md)|通知分析工具，控制項正從適當的 `catch` 區塊傳入。|  
|[ExceptionCLRCatcherExecute 方法](icorprofilercallback-exceptionclrcatcherexecute-method.md)|在 .NET Framework 版本2.0 中已過時。|  
|[ExceptionCLRCatcherFound 方法](icorprofilercallback-exceptionclrcatcherfound-method.md)|在 .NET Framework 2.0 中已過時。|  
|[ExceptionOSHandlerEnter 方法](icorprofilercallback-exceptionoshandlerenter-method.md)|未實作。 需要非受控例外狀況資訊的 profiler 必須透過其他方式取得此資訊。|  
|[ExceptionOSHandlerLeave 方法](icorprofilercallback-exceptionoshandlerleave-method.md)|未實作。 需要非受控例外狀況資訊的 profiler 必須透過其他方式取得此資訊。|  
|[ExceptionSearchCatcherFound 方法](icorprofilercallback-exceptionsearchcatcherfound-method.md)|通知分析工具，例外狀況處理的搜尋階段已找出擲回之例外狀況的處理常式。|  
|[ExceptionSearchFilterEnter 方法](icorprofilercallback-exceptionsearchfilterenter-method.md)|通知 profiler 正在執行使用者篩選。|  
|[ExceptionSearchFilterLeave 方法](icorprofilercallback-exceptionsearchfilterleave-method.md)|通知分析工具，使用者篩選器已完成執行。|  
|[ExceptionSearchFunctionEnter 方法](icorprofilercallback-exceptionsearchfunctionenter-method.md)|通知分析工具，例外狀況處理的搜尋階段已輸入函數。|  
|[ExceptionSearchFunctionLeave 方法](icorprofilercallback-exceptionsearchfunctionleave-method.md)|通知分析工具，例外狀況處理的搜尋階段已完成搜尋函數。|  
|[ExceptionThrown 方法](icorprofilercallback-exceptionthrown-method.md)|通知分析工具已擲回例外狀況。|  
|[ExceptionUnwindFinallyEnter 方法](icorprofilercallback-exceptionunwindfinallyenter-method.md)|通知分析工具，例外狀況處理的回溯階段正在輸入包含在指定之函式中的 `finally` 子句。|  
|[ExceptionUnwindFinallyLeave 方法](icorprofilercallback-exceptionunwindfinallyleave-method.md)|通知分析工具，例外狀況處理的回溯階段已離開 `finally` 子句。|  
|[ExceptionUnwindFunctionEnter 方法](icorprofilercallback-exceptionunwindfunctionenter-method.md)|通知分析工具，例外狀況處理的回溯階段已輸入函數。|  
|[ExceptionUnwindFunctionLeave 方法](icorprofilercallback-exceptionunwindfunctionleave-method.md)|通知分析工具，例外狀況處理的回溯階段已完成函數的回溯。|  
|[FunctionUnloadStarted 方法](icorprofilercallback-functionunloadstarted-method.md)|通知分析工具，執行時間已開始卸載函數。|  
|[Initialize 方法](icorprofilercallback-initialize-method.md)|呼叫以在每次啟動新的 CLR 應用程式時初始化分析工具。|  
|[JITCachedFunctionSearchFinished 方法](icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|通知分析工具已完成先前使用 Ngen.exe 編譯之函式的搜尋。|  
|[JITCachedFunctionSearchStarted 方法](icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|通知分析工具，已針對先前使用 Ngen.exe 編譯的函式開始搜尋。|  
|[JITCompilationFinished 方法](icorprofilercallback-jitcompilationfinished-method.md)|通知分析工具，JIT 編譯程式已完成編譯函式。|  
|[JITCompilationStarted 方法](icorprofilercallback-jitcompilationstarted-method.md)|通知分析工具，及時（JIT）編譯器已開始編譯函式。|  
|[JITFunctionPitched 方法](icorprofilercallback-jitfunctionpitched-method.md)|通知分析工具，已從記憶體中移除已經過 JIT 編譯的函式。|  
|[JITInlining 方法](icorprofilercallback-jitinlining-method.md)|通知分析工具，JIT 編譯程式即將以另一個函式插入函數。|  
|[ManagedToUnmanagedTransition 方法](icorprofilercallback-managedtounmanagedtransition-method.md)|通知分析工具，已發生從 managed 程式碼到未受管理程式碼的轉換。|  
|[ModuleAttachedToAssembly 方法](icorprofilercallback-moduleattachedtoassembly-method.md)|通知 profiler，模組已附加至其父元件。|  
|[ModuleLoadFinished 方法](icorprofilercallback-moduleloadfinished-method.md)|通知 profiler 模組已完成載入。|  
|[ModuleLoadStarted 方法](icorprofilercallback-moduleloadstarted-method.md)|通知分析工具已載入模組。|  
|[ModuleUnloadFinished 方法](icorprofilercallback-moduleunloadfinished-method.md)|通知 profiler 模組已完成卸載。|  
|[ModuleUnloadStarted 方法](icorprofilercallback-moduleunloadstarted-method.md)|通知分析工具，模組正在卸載。|  
|[MovedReferences 方法](icorprofilercallback-movedreferences-method.md)|通知分析工具有關垃圾收集期間已移動的物件參考。|  
|[ObjectAllocated 方法](icorprofilercallback-objectallocated-method.md)|通知分析工具，堆積內的記憶體已配置給物件。|  
|[ObjectReferences 方法](icorprofilercallback-objectreferences-method.md)|通知分析工具有關指定物件所參考記憶體中的物件。|  
|[ObjectsAllocatedByClass 方法](icorprofilercallback-objectsallocatedbyclass-method.md)|通知分析工具有關上一次垃圾收集之後所建立之每個指定類別的實例數目。|  
|[RemotingClientInvocationFinished 方法](icorprofilercallback-remotingclientinvocationfinished-method.md)|通知分析工具，遠端呼叫已在用戶端上完成執行。|  
|[RemotingClientInvocationStarted 方法](icorprofilercallback-remotingclientinvocationstarted-method.md)|通知 profiler，遠端呼叫已啟動。|  
|[RemotingClientReceivingReply 方法](icorprofilercallback-remotingclientreceivingreply-method.md)|通知分析工具，遠端呼叫的伺服器端部分已完成，而且用戶端現在正在接收，且即將處理回復。|  
|[RemotingClientSendingMessage 方法](icorprofilercallback-remotingclientsendingmessage-method.md)|通知分析工具用戶端正在將要求傳送至伺服器。|  
|[RemotingServerInvocationReturned 方法](icorprofilercallback-remotingserverinvocationreturned-method.md)|通知分析工具，進程已完成叫用方法以回應遠端方法調用要求。|  
|[RemotingServerInvocationStarted 方法](icorprofilercallback-remotingserverinvocationstarted-method.md)|通知分析工具，進程正在叫用方法以回應遠端方法調用要求。|  
|[RemotingServerReceivingMessage 方法](icorprofilercallback-remotingserverreceivingmessage-method.md)|通知分析工具，進程正在接收遠端方法調用或啟用要求。|  
|[RemotingServerSendingReply 方法](icorprofilercallback-remotingserversendingreply-method.md)|通知分析工具，進程已完成處理遠端方法調用要求，而且即將透過通道傳送回復。|  
|[RootReferences 方法](icorprofilercallback-rootreferences-method.md)|在垃圾收集之後，使用根參考的相關資訊來通知分析工具。|  
|[RuntimeResumeFinished 方法](icorprofilercallback-runtimeresumefinished-method.md)|通知分析工具，執行時間已恢復所有運行時間表程，並已回到正常作業。|  
|[RuntimeResumeStarted 方法](icorprofilercallback-runtimeresumestarted-method.md)|通知分析工具，執行時間正在繼續所有運行時間表程。|  
|[RuntimeSuspendAborted 方法](icorprofilercallback-runtimesuspendaborted-method.md)|通知分析工具，執行時間已中止發生的運行時暫停。|  
|[RuntimeSuspendFinished 方法](icorprofilercallback-runtimesuspendfinished-method.md)|通知 profiler，執行時間已完成所有運行時間表程的暫止。|  
|[RuntimeSuspendStarted 方法](icorprofilercallback-runtimesuspendstarted-method.md)|通知分析工具，執行時間即將暫止所有運行時間表程。|  
|[RuntimeThreadResumed 方法](icorprofilercallback-runtimethreadresumed-method.md)|通知分析工具，指定的執行緒在暫止後已繼續。|  
|[RuntimeThreadSuspended 方法](icorprofilercallback-runtimethreadsuspended-method.md)|通知分析工具，指定的執行緒已經或即將暫停。|  
|[Shutdown 方法](icorprofilercallback-shutdown-method.md)|通知 profiler 應用程式正在關閉。|  
|[ThreadAssignedToOSThread 方法](icorprofilercallback-threadassignedtoosthread-method.md)|使用特定的作業系統（OS）執行緒，通知分析工具正在執行的受控執行緒。|  
|[ThreadCreated 方法](icorprofilercallback-threadcreated-method.md)|通知分析工具已建立執行緒。|  
|[ThreadDestroyed 方法](icorprofilercallback-threaddestroyed-method.md)|通知分析工具，執行緒已遭終結。|  
|[UnmanagedToManagedTransition 方法](icorprofilercallback-unmanagedtomanagedtransition-method.md)|通知分析工具，已發生從非受控碼到 managed 程式碼的轉換。|  
  
## <a name="remarks"></a>備註  
 CLR 會呼叫 `ICorProfilerCallback` （或[ICorProfilerCallback2](icorprofilercallback2-interface.md)）介面中的方法，以便在分析工具已訂閱的事件發生時，通知分析工具。 這是 CLR 用來與程式碼 profiler 通訊的主要回呼介面。  
  
 程式碼分析工具必須執行 `ICorProfilerCallback` 介面的方法。 針對 .NET Framework 2.0 版或更新版本，分析工具也必須執行 `ICorProfilerCallback2` 方法。 每個方法的執行都必須傳回 HRESULT，其值為 [成功] 或 [失敗時 E_FAIL] S_OK。 目前，CLR 會忽略[ICorProfilerCallback：： ObjectReferences](icorprofilercallback-objectreferences-method.md)以外的每個回呼所傳回的 HRESULT。  
  
 在 Microsoft Windows 登錄中，程式碼分析工具必須註冊其元件物件模型（COM）物件，以執行 `ICorProfilerCallback` 和 `ICorProfilerCallback2` 介面。 程式碼分析工具會透過呼叫[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)，訂閱想要接收通知的事件。 這通常會在分析工具的[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)的執行中完成。 然後，分析工具就能夠在事件即將發生或發生在執行中的執行時間進程時，從執行時間接收通知。  
  
> [!NOTE]
> Profiler 會註冊單一 COM 物件。 如果分析工具的目標是 .NET Framework 版本1.0 或1.1，則該 COM 物件只需要執行 `ICorProfilerCallback`的方法。 如果它是以 .NET Framework 2.0 版或更新版本為目標，則 COM 物件也必須執行 `ICorProfilerCallback2`的方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [分析介面](profiling-interfaces.md)
- [ICorProfilerCallback2 介面](icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 介面](icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 介面](icorprofilercallback4-interface.md)
