---
title: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8c65ec6acc5ff87501392eb41909fcd6ebf1e3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599103"
---
# <a name="corprofeunsupportedcallsequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
.NET Framework 2.0 版中引進了 CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT。 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]兩個案例中會傳回此 HRESULT:  
  
- 當攔截分析工具強制重設的執行緒時登錄內容在任意時間，執行緒嘗試存取結構處於不一致的狀態。  
  
- 當分析工具會嘗試呼叫觸發從回呼方法，禁止記憶體回收的記憶體回收回收告知性方法。  
  
 下列各節中討論這兩種情況。  
  
## <a name="hijacking-profilers"></a>攔截程式碼剖析工具  
 （此案例中是主要的問題雖然有非攔截程式碼剖析工具可以在其中看到此 HRESULT 的情況下攔截程式碼剖析工具）。  
  
 在此案例中，攔截分析工具強制重設執行緒的暫存器內容在任意時間，以便在執行緒可以輸入程式碼剖析工具的程式碼或重新輸入 common language runtime (CLR) 透過[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)方法。  
  
 許多程式碼剖析 API 提供指向在 CLR 中的資料結構的識別碼。 許多`ICorProfilerInfo`呼叫只會讀取這些資料結構中的資訊，並將它們傳回。 不過，CLR 在執行時，以及它可能會使用鎖定來執行這項操作，可能會變更這些結構中的項目。 假設 CLR 是已保留 （或嘗試取得） 時的鎖定程式碼剖析工具該執行緒。 如果執行緒重新進入 CLR，並嘗試採取更多的鎖定，或檢查已修改的過程中的結構，這些結構可能不一致的狀態。 在此情況下可能輕易地死結和存取違規。  
  
 一般情況下，當非攔截程式碼剖析工具執行內的程式碼時，才[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)方法，並呼叫`ICorProfilerInfo`方法的有效參數，它不應該發生死結或收到存取違規。 比方說，程式碼剖析工具執行的程式碼內[icorprofilercallback:: Classloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)方法可能會藉由呼叫要求類別的相關資訊[ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)方法。 程式碼可能會收到 CORPROF_E_DATAINCOMPLETE HRESULT，指出資訊無法使用;不過，它不會發生死結或收到存取違規。 這個類別的呼叫`ICorProfilerInfo`稱為同步的因為它們都會從`ICorProfilerCallback`方法。  
  
 不過，managed 的執行緒執行程式碼，不符合`ICorProfilerCallback`方法會被視為進行非同步呼叫。 在.NET Framework 第 1 版中，很難判斷非同步呼叫中可能會發生什麼事。 呼叫可能鎖死、 當機，或提供無效的回應。 .NET Framework 2.0 版導入了一些簡單的檢查，以協助您避免這個問題。 在.NET Framework 2.0 中，如果您呼叫的不安全`ICorProfilerInfo`函式以非同步方式，它會失敗並 CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT。  
  
 一般情況下，是不安全的非同步呼叫。 不過，下列方法會很安全，而且特別是支援非同步呼叫：  
  
- [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)  
  
- [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)  
  
- [GetCurrentThreadID](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)  
  
- [GetThreadContext](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)  
  
- [GetThreadAppDomain](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)  
  
- [GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)  
  
- [GetFunctionInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)  
  
- [GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)  
  
- [GetCodeInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)  
  
- [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
  
- [GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)  
  
- [GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)  
  
- [GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)  
  
- [IsArrayClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)  
  
- [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
  
- [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
  
 如需詳細資訊，請參閱文章[為什麼我們 CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://go.microsoft.com/fwlink/?LinkId=169156) CLR 程式碼剖析 API 部落格中。  
  
## <a name="triggering-garbage-collections"></a>觸發記憶體回收  
 此案例牽涉到的回呼方法內執行的分析工具 (例如，其中一個`ICorProfilerCallback`方法)，禁止記憶體回收。 如果分析工具嘗試呼叫告知性方法 (例如，在方法`ICorProfilerInfo`介面)，可能會觸發記憶體回收，告知性方法將會失敗，CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT。  
  
 下表顯示回呼方法，禁止記憶體回收，以及可能會觸發記憶體回收的告知性方法。 如果分析工具會執行內其中一個列出的回呼方法，並呼叫其中一個列出的告知性方法，該告知性方法 CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT 而失敗。  
  
|禁止記憶體回收的回呼方法|觸發記憶體回收的告知性方法|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [ICorProfilerInfo3 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [程式碼剖析](../../../../docs/framework/unmanaged-api/profiling/index.md)
