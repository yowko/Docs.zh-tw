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
ms.openlocfilehash: 1ff167121a5bb752c70edd2c5901133503326bea
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500802"
---
# <a name="cor_prf_monitor-enumeration"></a>COR_PRF_MONITOR 列舉
包含值，這些值用於指定分析工具想要訂閱的行為、功能或事件。  
  
## <a name="syntax"></a>語法  
  
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
  
## <a name="members"></a>成員  
 下列各節 `COR_PRF_MONITOR` 依類別列出列舉成員。 分類包括：  
  
- [未設定任何旗標](#None)  
  
- [回呼旗標](#Callback)  
  
- [功能啟用旗標](#Feature)  
  
- [組態旗標](#Config)  
  
- [組合旗標](#Composite)  
  
<a name="None"></a>
### <a name="no-flags-set"></a>未設定任何旗標  
  
|成員|說明|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|沒有設定旗標。|  
  
<a name="Callback"></a>
### <a name="callback-flags"></a>回呼旗標  
  
|成員|說明|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|啟用所有回呼事件。|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|控制 `AppDomainCreation*` `AppDomainShutdown*` [ICorProfilerCallback](icorprofilercallback-interface.md)介面中的和回呼。|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|控制 `AssemblyLoad*` `AssemblyUnload*` [ICorProfilerCallback](icorprofilercallback-interface.md)介面中的和回呼。|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|控制 `JITCachedFunctionSearch*` [ICorProfilerCallback](icorprofilercallback-interface.md)介面中的回呼。<br /><br /> 此旗標的行為已在 .NET Framework 2.0 版中變更。|  
|`COR_PRF_MONITOR_CCW`|控制 `COMClassicVTable*` [ICorProfilerCallback](icorprofilercallback-interface.md)介面中的回呼。|  
|`COR_PRF_MONITOR_CLASS_LOADS`|控制 `ClassLoad*` `ClassUnload*` [ICorProfilerCallback](icorprofilercallback-interface.md)介面中的和回呼。|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|控制 `ExceptionCLRCatcher*` [ICorProfilerCallback](icorprofilercallback-interface.md)介面中的回呼。|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|控制[ICorProfilerCallback](icorprofilercallback-interface.md)介面中的[UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md)和[ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md)回呼|  
|`COR_PRF_MONITOR_ENTERLEAVE`|控制 `FunctionEnter*` 、 `FunctionLeave*` 和 `FunctionTailCall*` [分析全域靜態](profiling-global-static-functions.md)函式。|  
|`COR_PRF_MONITOR_EXCEPTIONS`|控制 ICorProfilerCallback 介面中的[ExceptionThrown](icorprofilercallback-exceptionthrown-method.md)回呼和 `ExceptionSearch*` 、 `ExceptionOSHandler*` 、 `ExceptionUnwind*` 和 `ExceptionCatcher*` 回呼。 [ICorProfilerCallback](icorprofilercallback-interface.md)|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|控制[ICorProfilerCallback](icorprofilercallback-interface.md)介面中的[FunctionUnloadStarted](icorprofilercallback-functionunloadstarted-method.md)回呼。|  
|`COR_PRF_MONITOR_GC`|控制介面中的[GarbageCollectionStarted](icorprofilercallback2-garbagecollectionstarted-method.md)、 [GarbageCollectionFinished](icorprofilercallback2-garbagecollectionfinished-method.md)、 [MovedReferences](icorprofilercallback-movedreferences-method.md)、 [MovedReferences2](icorprofilercallback4-movedreferences2-method.md)、 [SurvivingReferences](icorprofilercallback2-survivingreferences-method.md)、 [SurvivingReferences2](icorprofilercallback4-survivingreferences2-method.md)、 [ObjectReferences](icorprofilercallback-objectreferences-method.md)、 [ObjectsAllocatedByClass](icorprofilercallback-objectsallocatedbyclass-method.md)、 [RootReferences](icorprofilercallback-rootreferences-method.md)、 [RootReferences2](icorprofilercallback2-rootreferences2-method.md) [、HandleCreated、](icorprofilercallback2-handlecreated-method.md) [HandleDestroyed](icorprofilercallback2-handledestroyed-method.md)和[FinalizeableObjectQueued](icorprofilercallback2-finalizeableobjectqueued-method.md)回呼 `ICorProfilerCallback*` 。 當配置時 `COR_PRF_MONITOR_GC` ，會關閉並行垃圾收集。|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|控制 `JITCompilation*` [ICorProfilerCallback](icorprofilercallback-interface.md)介面中的、 [JITFunctionPitched](icorprofilercallback-jitfunctionpitched-method.md)和[JITInlining](icorprofilercallback-jitinlining-method.md)回呼。|  
|`COR_PRF_MONITOR_MODULE_LOADS`|控制 `ModuleLoad*` `ModuleUnload*` [ICorProfilerCallback](icorprofilercallback-interface.md)介面中的、和[ModuleAttachedToAssembly](icorprofilercallback-moduleattachedtoassembly-method.md)回呼。|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|控制[ICorProfilerCallback](icorprofilercallback-interface.md)介面中的[ObjectAllocated](icorprofilercallback-objectallocated-method.md)回呼。|  
|`COR_PRF_MONITOR_REMOTING`|控制 `Remoting*` [ICorProfilerCallback](icorprofilercallback-interface.md)介面中的回呼。|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|控制 `Remoting*` 回呼是否會監視非同步事件。|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|控制 Cookie 是否傳遞至 `Remoting*` 回呼。|  
|`COR_PRF_MONITOR_SUSPENDS`|控制 `RuntimeSuspend*` `RuntimeResume*` [ICorProfilerCallback](icorprofilercallback-interface.md)介面中的、、 [RuntimeThreadSuspended](icorprofilercallback-runtimethreadsuspended-method.md)和[RuntimeThreadResumed](icorprofilercallback-runtimethreadresumed-method.md)回呼。|  
|`COR_PRF_MONITOR_THREADS`|控制[ICorProfilerCallback](icorprofilercallback-interface.md)和[ICorProfilerCallback2](icorprofilercallback2-interface.md)介面中的[ThreadCreated](icorprofilercallback-threadcreated-method.md)、 [ThreadDestroyed](icorprofilercallback-threaddestroyed-method.md)、 [ThreadAssignedToOSThread](icorprofilercallback-threadassignedtoosthread-method.md)和[ThreadNameChanged](icorprofilercallback2-threadnamechanged-method.md)回呼。|  
  
<a name="Feature"></a>
### <a name="feature-enabling-flags"></a>功能啟用旗標  
  
|成員|說明|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|藉 `ClassID` 由呼叫[GetFunctionInfo2](icorprofilerinfo2-getfunctioninfo2-method.md)方法與 `COR_PRF_FRAME_INFO` [FunctionEnter2](functionenter2-function.md)回呼所傳回的值，啟用對泛型函式的確切抓取。|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|啟用使用[FunctionEnter2](functionenter2-function.md)回呼或[FunctionEnter3WithInfo](functionenter3withinfo-function.md)回呼和[GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md)方法的引數追蹤。|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|啟用使用[FunctionLeave2](functionleave2-function.md)回呼或[FunctionLeave3WithInfo](functionleave3withinfo-function.md)回呼和[GetFunctionLeave3Info](icorprofilerinfo3-getfunctionleave3info-method.md)方法追蹤傳回值。|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|已被取代。<br /><br /> 不支援同處理序偵錯。 此旗標無效。|  
|`COR_PRF_ENABLE_JIT_MAPS`|已被取代。<br /><br /> 可讓分析工具使用[GetILToNativeMapping](icorprofilerinfo-getiltonativemapping-method.md)來取得 IL 對原生對應。 從 .NET Framework 2.0 開始，執行階段會一律追蹤 IL 與原生的對應；所以會一律將此旗標視為必須設定。|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|通知執行階段，分析工具可能想要物件配置通知。 必須在初始化期間設定此旗標。 它可讓分析工具隨後使用 `COR_PRF_MONITOR_OBJECT_ALLOCATED` 旗標來接收[ObjectAllocated](icorprofilercallback-objectallocated-method.md)回呼。|  
|`COR_PRF_ENABLE_REJIT`|啟用對[RequestReJIT](icorprofilerinfo4-requestrejit-method.md)和[RequestRevert](icorprofilerinfo4-requestrevert-method.md)方法的呼叫。 分析工具必須在啟動時設定此旗標。  若分析工具指定此旗標，則必須也要指定 `COR_PRF_DISABLE_ALL_NGEN_IMAGES`。|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|啟用[DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md)方法的呼叫。|  
  
<a name="Config"></a>
### <a name="configuration-flags"></a>組態旗標  
  
|成員|說明|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|防止載入所有原生映像 (包含分析工具增強型映像)。  若指定此旗標及 `COR_PRF_USE_PROFILE_IMAGES` 旗標，則使用 `COR_PRF_DISABLE_ALL_NGEN_IMAGES`。|  
|`COR_PRF_DISABLE_INLINING`|停用所有內嵌。|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|停用所有程式碼最佳化。|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|針對完全信任組件，停用通常在 Just-in-time (JIT) 編譯及類別載入期間完成的安全性透明度檢查。 這可讓一些實作更容易執行。|  
|`COR_PRF_USE_PROFILE_IMAGES`|使原生映像搜尋尋找分析工具增強型映像。 若沒有找到指定組件的分析工具增強型映像，Common Language Runtime 會回復為該組件的 JIT。 若指定此旗標及 `COR_PRF_DISABLE_ALL_NGEN_IMAGES` 旗標，則使用 `COR_PRF_DISABLE_ALL_NGEN_IMAGES`。|  
  
<a name="Composite"></a>
### <a name="composite-flags"></a>組合旗標  
  
|成員|說明|  
|------------|-----------------|  
|`COR_PRF_ALL`|代表所有 `COR_PRF_MONITOR` 旗標值。|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|代表所有 `COR_PRF_MONITOR` 旗標，這些旗標可在分析工具連結至執行中的應用程式之後加以設定。 語法區段指出此位元遮罩中存在的個別旗標。|  
|`COR_PRF_MONITOR_ALL`|啟用所有回呼事件。|  
|`COR_PRF_MONITOR_IMMUTABLE`|代表所有 `COR_PRF_MONITOR` 旗標，這些旗標只能在初始化期間加以設定。 嘗試在初始化之後變更任何這些旗標，會傳回指出失敗的 `HRESULT` 值。|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|代表需要設定檔增強影像的所有 `COR_PRF_MONITOR` 旗標。|  
  
## <a name="remarks"></a>備註  
 `COR_PRF_MONITOR`值會與[ICorProfilerInfo：： GetEventMask](icorprofilerinfo-geteventmask-method.md)和[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)方法搭配使用，以定義 common language runtime 對分析工具執行的事件通知。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析列舉](profiling-enumerations.md)
- [GetEventMask 方法](icorprofilerinfo-geteventmask-method.md)
- [SetEventMask 方法](icorprofilerinfo-seteventmask-method.md)
