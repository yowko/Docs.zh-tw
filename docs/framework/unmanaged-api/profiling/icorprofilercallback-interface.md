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
ms.openlocfilehash: 8451f100f9e1b8d68045050d1b584ae44c29195d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684066"
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback 介面

提供 common language runtime (CLR) 所使用的方法，以在分析工具已訂閱的事件發生時通知程式碼分析工具。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AppDomainCreationFinished 方法](icorprofilercallback-appdomaincreationfinished-method.md)|通知 profiler 已建立應用程式域。|  
|[AppDomainCreationStarted 方法](icorprofilercallback-appdomaincreationstarted-method.md)|通知 profiler 正在建立應用程式域。|  
|[AppDomainShutdownFinished 方法](icorprofilercallback-appdomainshutdownfinished-method.md)|通知分析工具，已從進程卸載應用程式域。|  
|[AppDomainShutdownStarted 方法](icorprofilercallback-appdomainshutdownstarted-method.md)|通知分析工具正在從進程卸載應用程式域。|  
|[AssemblyLoadFinished 方法](icorprofilercallback-assemblyloadfinished-method.md)|通知 profiler 元件已完成載入。|  
|[AssemblyLoadStarted 方法](icorprofilercallback-assemblyloadstarted-method.md)|通知分析工具正在載入元件。|  
|[AssemblyUnloadFinished 方法](icorprofilercallback-assemblyunloadfinished-method.md)|通知分析工具元件已卸載。|  
|[AssemblyUnloadStarted 方法](icorprofilercallback-assemblyunloadstarted-method.md)|通知分析工具元件正在卸載。|  
|[ClassLoadFinished 方法](icorprofilercallback-classloadfinished-method.md)|通知分析工具某個類別已完成載入。|  
|[ClassLoadStarted 方法](icorprofilercallback-classloadstarted-method.md)|通知 profiler 正在載入類別。|  
|[ClassUnloadFinished 方法](icorprofilercallback-classunloadfinished-method.md)|通知分析工具，類別已完成卸載。|  
|[ClassUnloadStarted 方法](icorprofilercallback-classunloadstarted-method.md)|通知分析工具有正在卸載的類別。|  
|[COMClassicVTableCreated 方法](icorprofilercallback-comclassicvtablecreated-method.md)|通知分析工具，已建立指定 IID 和類別的執行時間可呼叫包裝函式 (RCW) 。|  
|[COMClassicVTableDestroyed 方法](icorprofilercallback-comclassicvtabledestroyed-method.md)|通知分析工具已終結 RCW。|  
|[ExceptionCatcherEnter 方法](icorprofilercallback-exceptioncatcherenter-method.md)|通知分析工具，控制項正在傳遞至適當的 `catch` 區塊。|  
|[ExceptionCatcherLeave 方法](icorprofilercallback-exceptioncatcherleave-method.md)|通知分析工具，控制項即將從適當的 `catch` 區塊傳遞。|  
|[ExceptionCLRCatcherExecute 方法](icorprofilercallback-exceptionclrcatcherexecute-method.md)|.NET Framework 版本2.0 中已淘汰。|  
|[ExceptionCLRCatcherFound 方法](icorprofilercallback-exceptionclrcatcherfound-method.md)|.NET Framework 2.0 中已淘汰。|  
|[ExceptionOSHandlerEnter 方法](icorprofilercallback-exceptionoshandlerenter-method.md)|未實作。 需要非受控例外狀況資訊的 profiler 必須透過其他方式取得此資訊。|  
|[ExceptionOSHandlerLeave 方法](icorprofilercallback-exceptionoshandlerleave-method.md)|未實作。 需要非受控例外狀況資訊的 profiler 必須透過其他方式取得此資訊。|  
|[ExceptionSearchCatcherFound 方法](icorprofilercallback-exceptionsearchcatcherfound-method.md)|通知分析工具，例外狀況處理的搜尋階段已找出所擲回例外狀況的處理常式。|  
|[ExceptionSearchFilterEnter 方法](icorprofilercallback-exceptionsearchfilterenter-method.md)|通知 profiler 正在執行使用者篩選。|  
|[ExceptionSearchFilterLeave 方法](icorprofilercallback-exceptionsearchfilterleave-method.md)|通知分析工具使用者篩選器已完成執行。|  
|[ExceptionSearchFunctionEnter 方法](icorprofilercallback-exceptionsearchfunctionenter-method.md)|通知分析工具例外狀況處理的搜尋階段已進入函數。|  
|[ExceptionSearchFunctionLeave 方法](icorprofilercallback-exceptionsearchfunctionleave-method.md)|通知分析工具，例外狀況處理的搜尋階段已完成搜尋函數。|  
|[ExceptionThrown 方法](icorprofilercallback-exceptionthrown-method.md)|通知分析工具已擲回例外狀況。|  
|[ExceptionUnwindFinallyEnter 方法](icorprofilercallback-exceptionunwindfinallyenter-method.md)|通知分析工具，例外狀況處理的回溯階段是輸入指定之函式 `finally` 中所包含的子句。|  
|[ExceptionUnwindFinallyLeave 方法](icorprofilercallback-exceptionunwindfinallyleave-method.md)|通知分析工具，例外狀況處理的回溯階段已離開 `finally` 子句。|  
|[ExceptionUnwindFunctionEnter 方法](icorprofilercallback-exceptionunwindfunctionenter-method.md)|通知分析工具例外狀況處理的回溯階段已進入函數。|  
|[ExceptionUnwindFunctionLeave 方法](icorprofilercallback-exceptionunwindfunctionleave-method.md)|通知分析工具，例外狀況處理的回溯階段已完成回溯函式。|  
|[FunctionUnloadStarted 方法](icorprofilercallback-functionunloadstarted-method.md)|通知分析工具，執行時間已開始卸載函數。|  
|[Initialize 方法](icorprofilercallback-initialize-method.md)|呼叫以在每次啟動新的 CLR 應用程式時初始化分析工具。|  
|[JITCachedFunctionSearchFinished 方法](icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|通知分析工具，在先前使用 NGen.exe 編譯的函式已完成搜尋。|  
|[JITCachedFunctionSearchStarted 方法](icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|通知分析工具，已針對先前使用 NGen.exe 編譯的函式開始搜尋。|  
|[JITCompilationFinished 方法](icorprofilercallback-jitcompilationfinished-method.md)|通知分析工具，JIT 編譯程式已完成函式的編譯。|  
|[JITCompilationStarted 方法](icorprofilercallback-jitcompilationstarted-method.md)|通知分析工具，及時 (JIT) 編譯器已開始編譯函式。|  
|[JITFunctionPitched 方法](icorprofilercallback-jitfunctionpitched-method.md)|通知分析工具，已從記憶體中移除已進行 JIT 編譯的函式。|  
|[JITInlining 方法](icorprofilercallback-jitinlining-method.md)|通知分析工具，JIT 編譯程式即將將函式插入至另一個函式的行。|  
|[ManagedToUnmanagedTransition 方法](icorprofilercallback-managedtounmanagedtransition-method.md)|通知分析工具將 managed 程式碼轉換為非受控程式碼時發生。|  
|[ModuleAttachedToAssembly 方法](icorprofilercallback-moduleattachedtoassembly-method.md)|通知分析工具正在將模組附加至其父元件。|  
|[ModuleLoadFinished 方法](icorprofilercallback-moduleloadfinished-method.md)|通知分析工具模組已完成載入。|  
|[ModuleLoadStarted 方法](icorprofilercallback-moduleloadstarted-method.md)|通知 profiler 正在載入模組。|  
|[ModuleUnloadFinished 方法](icorprofilercallback-moduleunloadfinished-method.md)|通知分析工具模組已完成卸載。|  
|[ModuleUnloadStarted 方法](icorprofilercallback-moduleunloadstarted-method.md)|通知分析工具正在卸載模組。|  
|[MovedReferences 方法](icorprofilercallback-movedreferences-method.md)|通知分析工具有關在垃圾收集期間移動的物件參考。|  
|[ObjectAllocated 方法](icorprofilercallback-objectallocated-method.md)|通知分析工具，堆積內的記憶體已配置給物件。|  
|[ObjectReferences 方法](icorprofilercallback-objectreferences-method.md)|通知分析工具有關指定物件所參考記憶體中的物件。|  
|[ObjectsAllocatedByClass 方法](icorprofilercallback-objectsallocatedbyclass-method.md)|通知分析工具有關在上一次垃圾收集之後所建立之每個指定類別的實例數目。|  
|[RemotingClientInvocationFinished 方法](icorprofilercallback-remotingclientinvocationfinished-method.md)|通知分析工具，遠端呼叫已在用戶端上執行完成。|  
|[RemotingClientInvocationStarted 方法](icorprofilercallback-remotingclientinvocationstarted-method.md)|通知分析工具已啟動遠端呼叫。|  
|[RemotingClientReceivingReply 方法](icorprofilercallback-remotingclientreceivingreply-method.md)|通知分析工具，遠端呼叫的伺服器端部分已完成，而且用戶端現在已在接收及處理回復。|  
|[RemotingClientSendingMessage 方法](icorprofilercallback-remotingclientsendingmessage-method.md)|通知分析工具用戶端正在將要求傳送至伺服器。|  
|[RemotingServerInvocationReturned 方法](icorprofilercallback-remotingserverinvocationreturned-method.md)|通知分析工具，進程已完成叫用方法來回應遠端方法調用要求。|  
|[RemotingServerInvocationStarted 方法](icorprofilercallback-remotingserverinvocationstarted-method.md)|通知分析工具，進程正在叫用方法來回應遠端方法調用要求。|  
|[RemotingServerReceivingMessage 方法](icorprofilercallback-remotingserverreceivingmessage-method.md)|通知分析工具進程正在接收遠端方法調用或啟用要求。|  
|[RemotingServerSendingReply 方法](icorprofilercallback-remotingserversendingreply-method.md)|通知分析工具進程已完成遠端方法調用要求的處理，而且即將透過通道傳送回復。|  
|[RootReferences 方法](icorprofilercallback-rootreferences-method.md)|在垃圾收集之後，以根參考的相關語音總機 profiler。|  
|[RuntimeResumeFinished 方法](icorprofilercallback-runtimeresumefinished-method.md)|通知分析工具，執行時間已繼續所有運行時間表程，並已恢復正常作業。|  
|[RuntimeResumeStarted 方法](icorprofilercallback-runtimeresumestarted-method.md)|通知分析工具，執行時間正在繼續所有運行時間表程。|  
|[RuntimeSuspendAborted 方法](icorprofilercallback-runtimesuspendaborted-method.md)|通知分析工具，執行時間已中止發生的執行時間暫止。|  
|[RuntimeSuspendFinished 方法](icorprofilercallback-runtimesuspendfinished-method.md)|通知分析工具，執行時間已完成所有運行時間表程的擱置。|  
|[RuntimeSuspendStarted 方法](icorprofilercallback-runtimesuspendstarted-method.md)|通知分析工具，執行時間即將暫止所有運行時間表程。|  
|[RuntimeThreadResumed 方法](icorprofilercallback-runtimethreadresumed-method.md)|通知分析工具，指定的執行緒在暫止之後已繼續。|  
|[RuntimeThreadSuspended 方法](icorprofilercallback-runtimethreadsuspended-method.md)|通知分析工具，指定的執行緒已經或即將暫停。|  
|[Shutdown 方法](icorprofilercallback-shutdown-method.md)|通知 profiler 應用程式正在關閉。|  
|[ThreadAssignedToOSThread 方法](icorprofilercallback-threadassignedtoosthread-method.md)|通知分析工具，使用特定作業系統 (OS) 執行緒來執行受控執行緒。|  
|[ThreadCreated 方法](icorprofilercallback-threadcreated-method.md)|通知分析工具已建立執行緒。|  
|[ThreadDestroyed 方法](icorprofilercallback-threaddestroyed-method.md)|通知分析工具，執行緒已損毀。|  
|[UnmanagedToManagedTransition 方法](icorprofilercallback-unmanagedtomanagedtransition-method.md)|通知分析工具，從非受控程式碼轉換成 managed 程式碼時發生。|  
  
## <a name="remarks"></a>備註  

 CLR `ICorProfilerCallback` 會呼叫 (或 [ICorProfilerCallback2](icorprofilercallback2-interface.md)) 介面中的方法，以在分析工具已訂閱的事件發生時通知分析工具。 這是 CLR 用來與程式碼分析工具通訊的主要回呼介面。  
  
 程式碼分析工具必須執行介面的方法 `ICorProfilerCallback` 。 針對 .NET Framework 2.0 版或更新版本，分析工具也必須執行 `ICorProfilerCallback2` 方法。 每個方法的執行都必須傳回一個 HRESULT，其值為 [成功] 或 [失敗時 E_FAIL] S_OK。 目前，CLR 會忽略每個回呼所傳回的 HRESULT，但 [ICorProfilerCallback：： ObjectReferences](icorprofilercallback-objectreferences-method.md)除外。  
  
 在 Microsoft Windows 登錄中，程式碼分析工具必須將其元件物件模型註冊 (COM) 物件，該物件會實 `ICorProfilerCallback` 和 `ICorProfilerCallback2` 介面。 程式碼分析工具會藉由呼叫 [ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)，訂閱其想要接收通知的事件。 這通常是在分析工具的 [ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)的執行中完成。 當事件即將發生或發生在執行中的執行時間進程時，分析工具就可以接收來自執行時間的通知。  
  
> [!NOTE]
> Profiler 會註冊單一 COM 物件。 如果分析工具的目標是 .NET Framework 版本1.0 或1.1，則該 COM 物件只需要執行的方法 `ICorProfilerCallback` 。 如果它的目標是 .NET Framework 2.0 版或更新版本，則 COM 物件也必須執行的方法 `ICorProfilerCallback2` 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析介面](profiling-interfaces.md)
- [ICorProfilerCallback2 介面](icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 介面](icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 介面](icorprofilercallback4-interface.md)
