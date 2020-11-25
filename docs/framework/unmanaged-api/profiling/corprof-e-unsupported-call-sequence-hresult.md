---
title: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
ms.openlocfilehash: 1a75b51b57bdf2923ca6386f42c19c0b2f44fd39
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717470"
---
# <a name="corprof_e_unsupported_call_sequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT

CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT 是在 .NET Framework 2.0 版中引進。 在兩種情況下，.NET Framework 4 會傳回此 HRESULT：  
  
- 當劫持分析工具在任意時間強制重設執行緒的註冊內容時，執行緒會嘗試存取處於不一致狀態的結構。  
  
- 當分析工具嘗試呼叫的參考方法，會從禁止垃圾收集的回呼方法觸發垃圾收集。  
  
下列各節將討論這兩個案例。  
  
## <a name="hijacking-profilers"></a>劫持分析工具  

   (此案例主要是劫持分析工具的問題，不過在某些情況下，非劫持分析工具可以看到此 HRESULT。 )   
  
 在此案例中，劫持分析工具會在任意時間強制重設執行緒的暫存器內容，讓執行緒可以進入 profiler 程式碼，或透過 [ICorProfilerInfo](icorprofilerinfo-interface.md) 方法，重新輸入 common language RUNTIME (CLR) 。  
  
 分析 API 提供的許多識別碼會指向 CLR 中的資料結構。 許多 `ICorProfilerInfo` 呼叫只會讀取這些資料結構的資訊並將其傳回。 不過，CLR 可能會在執行時變更這些結構中的專案，而且可能會使用鎖定來執行此作業。 假設 CLR 已經保存 (或嘗試在分析工具劫持執行緒時取得) 鎖定。 如果執行緒重新進入 CLR 並嘗試取得更多鎖定，或檢查正在修改的結構，這些結構可能會處於不一致的狀態。 在這種情況下，很容易就會發生鎖死和存取違規。  
  
 一般來說，當非劫持分析工具在 [ICorProfilerCallback](icorprofilercallback-interface.md) 方法內執行程式碼，並呼叫 `ICorProfilerInfo` 具有有效參數的方法時，它不應該鎖死或收到存取違規。 例如，在 [ICorProfilerCallback：： ClassLoadFinished](icorprofilercallback-classloadfinished-method.md) 方法內執行的 profiler 程式碼，可能會藉由呼叫 [ICorProfilerInfo2：： GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md) 方法，要求提供有關類別的資訊。 程式碼可能會收到 CORPROF_E_DATAINCOMPLETE 的 HRESULT，指出資訊無法使用。 不過，它不會鎖死或收到存取違規。 這些呼叫 `ICorProfilerInfo` 會被視為同步，因為它們是從方法進行的 `ICorProfilerCallback` 。  
  
 不過，執行不在方法中之程式碼的 managed 執行緒 `ICorProfilerCallback` 會被視為進行非同步呼叫。 在 .NET Framework 第1版中，很難判斷非同步呼叫可能發生的情況。 呼叫可能會鎖死、損毀，或提供不正確答案。 .NET Framework 2.0 版引進了一些簡單的檢查，以協助您避免這個問題。 在 .NET Framework 2.0 中，如果您以非同步方式呼叫 unsafe 函式 `ICorProfilerInfo` ，它會失敗並出現 CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT。  
  
 一般情況下，非同步呼叫並不安全。 但是，下列方法是安全的，且特別支援非同步呼叫：  
  
- [GetEventMask](icorprofilerinfo-geteventmask-method.md)  
  
- [SetEventMask](icorprofilerinfo-seteventmask-method.md)  
  
- [GetCurrentThreadID](icorprofilerinfo-getcurrentthreadid-method.md)  
  
- [GetThreadCoNtext](icorprofilerinfo-getthreadcontext-method.md)  
  
- [GetThreadAppDomain](icorprofilerinfo2-getthreadappdomain-method.md)  
  
- [GetFunctionFromIP](icorprofilerinfo-getfunctionfromip-method.md)  
  
- [GetFunctionInfo](icorprofilerinfo-getfunctioninfo-method.md)  
  
- [GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md)  
  
- [GetCodeInfo](icorprofilerinfo-getcodeinfo-method.md)  
  
- [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md)  
  
- [GetModuleInfo](icorprofilerinfo-getmoduleinfo-method.md)  
  
- [GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md)  
  
- [GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md)  
  
- [IsArrayClass](icorprofilerinfo-isarrayclass-method.md)  
  
- [SetFunctionIDMapper](icorprofilerinfo-setfunctionidmapper-method.md)  
  
- [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md)  
  
 如需詳細資訊，請參閱 [我們](/archive/blogs/davbr/why-we-have-corprof_e_unsupported_call_sequence) 在 CLR 分析 API 中 CORPROF_E_UNSUPPORTED_CALL_SEQUENCE 的專案。  
  
## <a name="triggering-garbage-collections"></a>觸發垃圾收集  

 此案例牽涉到在回呼方法內執行的分析工具 (例如，其中一個會 `ICorProfilerCallback` 禁止垃圾收集的方法) 。 如果分析工具嘗試呼叫參考方法 (例如，) 介面上的方法 `ICorProfilerInfo` 可能會觸發垃圾收集，則參考方法會失敗，並出現 CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT。  
  
 下表顯示禁止垃圾收集的回呼方法，以及可能會觸發垃圾收集的資訊方法。 如果分析工具是在其中一個所列出的回呼方法內執行，並呼叫其中一個列出的參考方法，該資訊方法會失敗並顯示 CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT。  
  
|禁止垃圾收集的回呼方法|觸發垃圾收集的參考方法|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted](icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences](icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences](icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [RootReferences2](icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo](icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 介面](icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 介面](icorprofilercallback3-interface.md)
- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
- [ICorProfilerInfo3 介面](icorprofilerinfo3-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
