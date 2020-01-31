---
title: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
ms.openlocfilehash: b4ab5c8f7cdca1303cb4fbbc4fa39db3c5977c15
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867005"
---
# <a name="corprof_e_unsupported_call_sequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT

CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT 是在 .NET Framework 版本2.0 中引進。 .NET Framework 4 會在兩種情況下傳回此 HRESULT：  
  
- 當劫持分析工具在任意時間強制重設執行緒的暫存器內容時，執行緒會嘗試存取處於不一致狀態的結構。  
  
- 當分析工具嘗試呼叫從禁止垃圾收集的回呼方法觸發垃圾收集的資訊方法時。  
  
下列各節將討論這兩個案例。  
  
## <a name="hijacking-profilers"></a>劫持分析工具  

  （此案例主要是劫持分析工具的問題，但在某些情況下，非劫持分析工具可以看到此 HRESULT）。  
  
 在此案例中，劫持分析工具會強制隨時重設執行緒的暫存器內容，讓執行緒可以輸入 profiler 程式碼，或透過[ICorProfilerInfo](icorprofilerinfo-interface.md)方法重新輸入 common language RUNTIME （CLR）。  
  
 分析 API 在 CLR 中提供指向資料結構的許多識別碼。 許多 `ICorProfilerInfo` 呼叫只會讀取這些資料結構的資訊，並將其傳回。 不過，CLR 可能會在執行時變更這些結構中的專案，而且可能會使用鎖定來執行此動作。 假設 CLR 已經保留（或嘗試取得）分析工具劫持執行緒時的鎖定。 如果執行緒重新進入 CLR，並嘗試取得更多鎖定或檢查正在修改的結構，這些結構可能會處於不一致的狀態。 鎖死和存取違規在這種情況下很容易發生。  
  
 一般而言，當非劫持分析工具在[ICorProfilerCallback](icorprofilercallback-interface.md)方法內執行程式碼，並使用有效的參數呼叫 `ICorProfilerInfo` 方法時，它應該不會鎖死或收到存取違規。 例如，在[ICorProfilerCallback：： ClassLoadFinished](icorprofilercallback-classloadfinished-method.md)方法內執行的 profiler 程式碼，可以藉由呼叫[ICorProfilerInfo2：： GetClassIDInfo2](icorprofilerinfo2-getclassidinfo2-method.md)方法，來要求類別的相關資訊。 此程式碼可能會收到 CORPROF_E_DATAINCOMPLETE HRESULT，以指出資訊無法使用。 不過，它不會鎖死或收到存取違規。 這些對 `ICorProfilerInfo` 的呼叫會視為同步，因為是從 `ICorProfilerCallback` 方法進行。  
  
 不過，執行不在 `ICorProfilerCallback` 方法中之程式碼的 managed 執行緒會被視為進行非同步呼叫。 在 .NET Framework 版本1中，很難以判斷非同步呼叫中可能發生的狀況。 呼叫可能會鎖死、當機，或提供不正確答案。 .NET Framework 版本2.0 引進了一些簡單的檢查，可協助您避免這個問題。 在 .NET Framework 2.0 中，如果您以非同步方式呼叫不安全的 `ICorProfilerInfo` 函式，它會失敗並產生 CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT。  
  
 一般來說，非同步呼叫不是安全的。 不過，下列方法是安全的，而且特別支援非同步呼叫：  
  
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
  
 如需詳細資訊，請參閱  
  
## <a name="triggering-garbage-collections"></a>觸發垃圾收集  
 此案例牽涉到在回呼方法內執行的分析工具（例如，其中一個 `ICorProfilerCallback` 方法），這會禁止垃圾收集。 如果分析工具嘗試呼叫可能會觸發垃圾收集的參考方法（例如，`ICorProfilerInfo` 介面上的方法），則資訊方法會失敗，並產生 CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT。  
  
 下表顯示禁止垃圾收集的回呼方法，以及可能觸發垃圾收集的資訊方法。 如果分析工具在其中一個列出的回呼方法內執行，並呼叫其中一個列出的參考方法，則該資訊方法會失敗並出現 CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT。  
  
|禁止垃圾收集的回呼方法|觸發垃圾收集的資訊方法|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter](icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave](icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted](icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences](icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences](icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [RootReferences2](icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap](icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo](icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 介面](icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 介面](icorprofilercallback3-interface.md)
- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](icorprofilerinfo2-interface.md)
- [ICorProfilerInfo3 介面](icorprofilerinfo3-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
