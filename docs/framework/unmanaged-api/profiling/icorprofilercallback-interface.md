---
title: "ICorProfilerCallback 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c4a53687c473a87edae38207c44f89f0140f8ccd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback 介面
提供用來在分析工具已訂閱的事件發生時，通知程式碼分析工具 common language runtime (CLR) 的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AppDomainCreationFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|通知分析工具已建立應用程式定義域。|  
|[AppDomainCreationStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|通知分析工具所建立應用程式定義域。|  
|[AppDomainShutdownFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|通知分析工具，應用程式定義域已卸載的處理程序。|  
|[AppDomainShutdownStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|通知分析工具，應用程式定義域正在卸載的處理程序。|  
|[AssemblyLoadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|通知分析工具組件已完成載入。|  
|[AssemblyLoadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|通知分析工具正在載入組件。|  
|[AssemblyUnloadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|通知分析工具組件已卸載。|  
|[AssemblyUnloadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|通知分析工具正在卸載組件。|  
|[ClassLoadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|通知分析工具已完成載入類別。|  
|[ClassLoadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|通知分析工具載入的類別。|  
|[ClassUnloadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|通知分析工具已完成卸載的類別。|  
|[ClassUnloadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|通知分析工具正在卸載的類別。|  
|[COMClassicVTableCreated 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|通知分析工具已建立的執行階段可呼叫包裝函式 (RCW) 指定的 IID 和類別。|  
|[COMClassicVTableDestroyed 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|通知分析工具 RCW 正在被終結。|  
|[ExceptionCatcherEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|通知控制項已傳遞至適當的程式碼剖析工具`catch`區塊。|  
|[ExceptionCatcherLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|通知分析工具，控制會傳遞超出適當`catch`區塊。|  
|[ExceptionCLRCatcherExecute 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|.NET Framework 2.0 版中已過時。|  
|[ExceptionCLRCatcherFound 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|.NET Framework 2.0 中已過時。|  
|[ExceptionOSHandlerEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|未實作。 分析工具所需的 unmanaged 例外狀況資訊必須取得這項資訊透過其他方式。|  
|[ExceptionOSHandlerLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|未實作。 分析工具所需的 unmanaged 例外狀況資訊必須取得這項資訊透過其他方式。|  
|[ExceptionSearchCatcherFound 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|通知分析工具，「 搜尋 」 階段的例外狀況處理已經位於擲回的例外狀況的處理常式。|  
|[ExceptionSearchFilterEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|通知分析工具正在執行使用者篩選器。|  
|[ExceptionSearchFilterLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|通知分析工具，使用者篩選器剛剛完成執行。|  
|[ExceptionSearchFunctionEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|通知分析工具的例外狀況處理的搜尋階段已進入函式。|  
|[ExceptionSearchFunctionLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|通知分析工具的例外狀況處理的搜尋階段已完成搜尋函式。|  
|[ExceptionThrown 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|通知分析工具已擲回的例外狀況。|  
|[ExceptionUnwindFinallyEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|通知分析工具處理正在進入例外狀況回溯階段`finally`子句包含在指定的函式。|  
|[ExceptionUnwindFinallyLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|通知分析工具的回溯階段的例外狀況處理已離開`finally`子句。|  
|[ExceptionUnwindFunctionEnter 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|通知分析工具回溯階段的例外狀況處理已進入函式。|  
|[ExceptionUnwindFunctionLeave 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|通知分析工具已完成回溯函式回溯階段的例外狀況處理。|  
|[FunctionUnloadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|通知分析工具執行階段已開始卸載函式。|  
|[Initialize 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|呼叫以初始化程式碼剖析工具，每當新的 CLR 應用程式已啟動。|  
|[JITCachedFunctionSearchFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|通知分析工具用於先前使用 NGen.exe 所編譯的函式已完成搜尋。|  
|[JITCachedFunctionSearchStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|通知分析工具已用於先前使用 NGen.exe 所編譯的函式中開始搜尋。|  
|[JITCompilationFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|通知分析工具，JIT 編譯器已完成函式的編譯。|  
|[JITCompilationStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|通知分析工具在 just-in-time (JIT) 編譯器已開始編譯函式。|  
|[JITFunctionPitched 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|通知分析工具已從記憶體移除已進行 JIT 編譯的函式。|  
|[JITInlining 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|通知分析工具 JIT 編譯器即將插入與另一個函式的函式。|  
|[ManagedToUnmanagedTransition 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|通知分析工具，從 managed 程式碼轉換為 unmanaged 程式碼已發生。|  
|[ModuleAttachedToAssembly 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|通知分析工具模組要附加到其父組件。|  
|[ModuleLoadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|通知分析工具已完成載入模組。|  
|[ModuleLoadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|通知分析工具已載入模組。|  
|[ModuleUnloadFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|通知分析工具模組已卸載完成。|  
|[ModuleUnloadStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|通知分析工具正在卸載模組。|  
|[MovedReferences 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|通知記憶體回收期間移動的物件參考的相關程式碼剖析工具。|  
|[ObjectAllocated 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|通知分析工具，為物件配置在堆積中的記憶體。|  
|[ObjectReferences 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|通知分析工具有關所指定的物件參考的記憶體中的物件。|  
|[ObjectsAllocatedByClass 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|通知分析工具有關的每個指定的類別已建立自上一個記憶體回收的執行個體數目。|  
|[RemotingClientInvocationFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|通知分析工具的遠端呼叫已在用戶端上執行到完成。|  
|[RemotingClientInvocationStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|通知分析工具已啟動遠端呼叫。|  
|[RemotingClientReceivingReply 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|通知分析工具的遠端呼叫的伺服器端部分已完成，而且用戶端正在接收以及有關處理回覆。|  
|[RemotingClientSendingMessage 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|通知分析工具，用戶端會將要求傳送至伺服器。|  
|[RemotingServerInvocationReturned 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|通知分析工具處理序已完成叫用之遠端方法叫用要求回應中的方法。|  
|[RemotingServerInvocationStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|通知分析工具處理程序叫用之遠端方法叫用要求回應中的方法。|  
|[RemotingServerReceivingMessage 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|通知分析工具的處理序正在接收遠端方法叫用或啟用要求。|  
|[RemotingServerSendingReply 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|通知分析工具，處理程序已完成處理遠端方法叫用要求，而且即將傳送回覆，透過的通道。|  
|[RootReferences 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|通知分析工具的記憶體回收之後根參考的相關資訊。|  
|[RuntimeResumeFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|通知分析工具，執行階段已恢復所有執行階段執行緒，並且已恢復正常操作。|  
|[RuntimeResumeStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|通知分析工具執行階段會繼續執行階段的所有執行緒。|  
|[RuntimeSuspendAborted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|通知分析工具執行階段已中止執行階段暫停之前發生。|  
|[RuntimeSuspendFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|通知分析工具執行階段已完成的所有執行階段執行緒的暫停。|  
|[RuntimeSuspendStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|通知分析工具執行階段即將暫停執行階段的所有執行緒。|  
|[RuntimeThreadResumed 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|通知分析工具指定的執行緒已經在暫停之後繼續。|  
|[RuntimeThreadSuspended 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|指定的執行緒，或是即將暫止，通知分析工具。|  
|[Shutdown 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|通知分析工具的應用程式即將關閉。|  
|[ThreadAssignedToOSThread 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|通知分析工具正在使用特定作業系統 (OS) 執行緒實作 managed 的執行緒。|  
|[ThreadCreated 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|通知分析工具已建立一個執行緒。|  
|[ThreadDestroyed 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|通知分析工具已終結執行緒。|  
|[UnmanagedToManagedTransition 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|通知分析工具，從 unmanaged 程式碼轉換為 managed 程式碼已發生。|  
  
## <a name="remarks"></a>備註  
 CLR 會呼叫的方法`ICorProfilerCallback`(或[ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) 介面，以通知分析工具事件、 要分析工具已訂閱時，就會發生。 這是主要的回呼介面，透過此 CLR 與程式碼分析工具的通訊。  
  
 程式碼分析工具必須實作的方法`ICorProfilerCallback`介面。 適用於.NET Framework 2.0 版或更新版本中，分析工具也必須實作`ICorProfilerCallback2`方法。 每個方法實作必須傳回失敗 HRESULT 的值為 S_OK 成功或 E_FAIL。 目前，CLR 會忽略除了每個回撥所傳回的 HRESULT [icorprofilercallback:: Objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)。  
  
 在 Microsoft Windows 登錄中，程式碼分析工具必須登錄實作其元件物件模型 (COM) 物件`ICorProfilerCallback`和`ICorProfilerCallback2`介面。 程式碼分析工具訂閱它要接收通知，藉由呼叫的事件[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)。 這通常會在程式碼剖析工具實作[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)。 程式碼剖析工具就能夠從執行階段時通知事件會發生或剛執行的執行階段程序中發生。  
  
> [!NOTE]
>  分析工具註冊單一的 COM 物件。 如果程式碼剖析工具的目標.NET Framework 版本為 1.0 或 1.1，COM 物件必須實作的方法`ICorProfilerCallback`。 如果它以.NET Framework 2.0 版或更新版本為目標，COM 物件也必須實作的方法`ICorProfilerCallback2`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerCallback2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [ICorProfilerCallback3 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [ICorProfilerCallback4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
