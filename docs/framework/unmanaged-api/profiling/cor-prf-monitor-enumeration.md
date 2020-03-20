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
ms.openlocfilehash: b6c3dc78b9c503747c7a2d404706eb797790b931
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175196"
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
 以下各節按`COR_PRF_MONITOR`類別列出枚舉成員。 類別包括：  
  
- [未設置標誌](#None)  
  
- [回呼旗標](#Callback)  
  
- [功能啟用旗標](#Feature)  
  
- [組態旗標](#Config)  
  
- [組合旗標](#Composite)  
  
<a name="None"></a>
### <a name="no-flags-set"></a>未設置標誌  
  
|member|描述|  
|------------|-----------------|  
|`COR_PRF_MONITOR_NONE`|沒有設定旗標。|  
  
<a name="Callback"></a>
### <a name="callback-flags"></a>回呼旗標  
  
|member|描述|  
|------------|-----------------|  
|`COR_PRF_MONITOR_ALL`|啟用所有回呼事件。|  
|`COR_PRF_MONITOR_APPDOMAIN_LOADS`|控制`AppDomainCreation*`[ICorProfiler 回檔](icorprofilercallback-interface.md)介面中的 和`AppDomainShutdown*`回檔。|  
|`COR_PRF_MONITOR_ASSEMBLY_LOADS`|控制`AssemblyLoad*`[ICorProfiler 回檔](icorprofilercallback-interface.md)介面中的 和`AssemblyUnload*`回檔。|  
|`COR_PRF_MONITOR_CACHE_SEARCHES`|`JITCachedFunctionSearch*`控制[ICorProfiler 回檔](icorprofilercallback-interface.md)介面中的回檔。<br /><br /> 此旗標的行為已在 .NET Framework 2.0 版中變更。|  
|`COR_PRF_MONITOR_CCW`|`COMClassicVTable*`控制[ICorProfiler 回檔](icorprofilercallback-interface.md)介面中的回檔。|  
|`COR_PRF_MONITOR_CLASS_LOADS`|控制`ClassLoad*`[ICorProfiler 回檔](icorprofilercallback-interface.md)介面中的 和`ClassUnload*`回檔。|  
|`COR_PRF_MONITOR_CLR_EXCEPTIONS`|`ExceptionCLRCatcher*`控制[ICorProfiler 回檔](icorprofilercallback-interface.md)介面中的回檔。|  
|`COR_PRF_MONITOR_CODE_TRANSITIONS`|在[ICorProfiler 回檔](icorprofilercallback-interface.md)介面中控制[非託管到託管轉換](icorprofilercallback-unmanagedtomanagedtransition-method.md)和[託管到非託管轉換](icorprofilercallback-managedtounmanagedtransition-method.md)回檔|  
|`COR_PRF_MONITOR_ENTERLEAVE`|控制`FunctionEnter*`、 `FunctionLeave*` `FunctionTailCall*`[和分析全域靜態函數](profiling-global-static-functions.md)。|  
|`COR_PRF_MONITOR_EXCEPTIONS`|在[ICorProfiler](icorprofilercallback-interface.md)回檔`ExceptionSearch*`介面`ExceptionOSHandler*`中`ExceptionUnwind*`控制[異常引發](icorprofilercallback-exceptionthrown-method.md)回檔和 、 、 和`ExceptionCatcher*`回檔。|  
|`COR_PRF_MONITOR_FUNCTION_UNLOADS`|在[ICorProfiler 回檔](icorprofilercallback-interface.md)介面中控制[函數未載入啟動](icorprofilercallback-functionunloadstarted-method.md)回檔。|  
|`COR_PRF_MONITOR_GC`|`ICorProfilerCallback*`控制在介面中[啟動的垃圾回收](icorprofilercallback2-garbagecollectionstarted-method.md)、[垃圾回收完成](icorprofilercallback2-garbagecollectionfinished-method.md)、[移動引用](icorprofilercallback-movedreferences-method.md)、[移動引用 2、](icorprofilercallback4-movedreferences2-method.md)[倖存引用](icorprofilercallback2-survivingreferences-method.md)、[倖存引用 2、](icorprofilercallback4-survivingreferences2-method.md)[物件引用](icorprofilercallback-objectreferences-method.md)、[物件分配、](icorprofilercallback-objectsallocatedbyclass-method.md)[根引用](icorprofilercallback-rootreferences-method.md)、[根引用 2、](icorprofilercallback2-rootreferences2-method.md)[控制碼已創建](icorprofilercallback2-handlecreated-method.md)、[控制碼銷毀](icorprofilercallback2-handledestroyed-method.md)和[可最終物件排隊](icorprofilercallback2-finalizeableobjectqueued-method.md)回檔。 分配`COR_PRF_MONITOR_GC`後，併發垃圾回收將被關閉。|  
|`COR_PRF_MONITOR_JIT_COMPILATION`|控制`JITCompilation*`[ICorProfiler 回檔](icorprofilercallback-interface.md)介面中的[.JIT功能音調](icorprofilercallback-jitfunctionpitched-method.md)和[JITInlining](icorprofilercallback-jitinlining-method.md)回檔。|  
|`COR_PRF_MONITOR_MODULE_LOADS`|控制`ModuleLoad*`[ICorProfiler 回檔](icorprofilercallback-interface.md)介面中的 、`ModuleUnload*`和[模組附加元件](icorprofilercallback-moduleattachedtoassembly-method.md)回檔。|  
|`COR_PRF_MONITOR_OBJECT_ALLOCATED`|在[ICorProfiler 回檔](icorprofilercallback-interface.md)介面中控制[物件分配](icorprofilercallback-objectallocated-method.md)回檔。|  
|`COR_PRF_MONITOR_REMOTING`|`Remoting*`控制[ICorProfiler 回檔](icorprofilercallback-interface.md)介面中的回檔。|  
|`COR_PRF_MONITOR_REMOTING_ASYNC`|控制 `Remoting*` 回呼是否會監視非同步事件。|  
|`COR_PRF_MONITOR_REMOTING_COOKIE`|控制 Cookie 是否傳遞至 `Remoting*` 回呼。|  
|`COR_PRF_MONITOR_SUSPENDS`|在`RuntimeSuspend*`[ICorProfiler 回檔](icorprofilercallback-interface.md)介面中控制`RuntimeResume*`[、、運行時執行緒掛起](icorprofilercallback-runtimethreadsuspended-method.md)和[運行時執行緒恢復](icorprofilercallback-runtimethreadresumed-method.md)回檔。|  
|`COR_PRF_MONITOR_THREADS`|在[ICorProfiler 回檔](icorprofilercallback-interface.md)和[ICorProfilerCallback2](icorprofilercallback2-interface.md)介面中控制[執行緒創建](icorprofilercallback-threadcreated-method.md)、[執行緒銷毀](icorprofilercallback-threaddestroyed-method.md)、[執行緒分配到 OS 執行緒](icorprofilercallback-threadassignedtoosthread-method.md)和[執行緒名稱更改](icorprofilercallback2-threadnamechanged-method.md)回檔。|  
  
<a name="Feature"></a>
### <a name="feature-enabling-flags"></a>功能啟用旗標  
  
|member|描述|  
|------------|-----------------|  
|`COR_PRF_ENABLE_FRAME_INFO`|通過調用[GetEinfo2](icorprofilerinfo2-getfunctioninfo2-method.md)方法，使用`COR_PRF_FRAME_INFO`[函數Enter2](functionenter2-function.md)回檔返回的值，啟用對泛型函數的精確`ClassID`檢索。|  
|`COR_PRF_ENABLE_FUNCTION_ARGS`|使用[函數Enter2](functionenter2-function.md)回檔或[函數Enter3與Info](functionenter3withinfo-function.md)回檔和[GetFunctionEnter3Info](icorprofilerinfo3-getfunctionenter3info-method.md)方法啟用參數跟蹤。|  
|`COR_PRF_ENABLE_FUNCTION_RETVAL`|通過使用[函數Leave2](functionleave2-function.md)回檔或[函數Leave3Info](functionleave3withinfo-function.md)回檔和[Get功能Leave3Info](icorprofilerinfo3-getfunctionleave3info-method.md)方法，啟用傳回值的跟蹤。|  
|`COR_PRF_ENABLE_INPROC_DEBUGGING`|已被取代。<br /><br /> 不支援同處理序偵錯。 此旗標無效。|  
|`COR_PRF_ENABLE_JIT_MAPS`|已被取代。<br /><br /> 允許探測器使用[GetILToNativemap](icorprofilerinfo-getiltonativemapping-method.md)獲取 IL 到本機映射。 從 .NET Framework 2.0 開始，執行階段會一律追蹤 IL 與原生的對應；所以會一律將此旗標視為必須設定。|  
|`COR_PRF_ENABLE_OBJECT_ALLOCATED`|通知執行階段，分析工具可能想要物件配置通知。 必須在初始化期間設定此旗標。 它允許探測器隨後使用`COR_PRF_MONITOR_OBJECT_ALLOCATED`標誌接收[物件分配的](icorprofilercallback-objectallocated-method.md)回檔。|  
|`COR_PRF_ENABLE_REJIT`|啟用對請求[ReJIT](icorprofilerinfo4-requestrejit-method.md)和[請求還原方法的](icorprofilerinfo4-requestrevert-method.md)調用。 分析工具必須在啟動時設定此旗標。  若分析工具指定此旗標，則必須也要指定 `COR_PRF_DISABLE_ALL_NGEN_IMAGES`。|  
|`COR_PRF_ENABLE_STACK_SNAPSHOT`|啟用對[DoStack 快照](icorprofilerinfo2-dostacksnapshot-method.md)方法的調用。|  
  
<a name="Config"></a>
### <a name="configuration-flags"></a>組態旗標  
  
|member|描述|  
|------------|-----------------|  
|`COR_PRF_DISABLE_ALL_NGEN_IMAGES`|防止載入所有原生映像 (包含分析工具增強型映像)。  若指定此旗標及 `COR_PRF_USE_PROFILE_IMAGES` 旗標，則使用 `COR_PRF_DISABLE_ALL_NGEN_IMAGES`。|  
|`COR_PRF_DISABLE_INLINING`|停用所有內嵌。|  
|`COR_PRF_DISABLE_OPTIMIZATIONS`|停用所有程式碼最佳化。|  
|`COR_PRF_DISABLE_TRANSPARENCY_CHECKS_UNDER_FULL_TRUST`|針對完全信任組件，停用通常在 Just-in-time (JIT) 編譯及類別載入期間完成的安全性透明度檢查。 這可讓一些實作更容易執行。|  
|`COR_PRF_USE_PROFILE_IMAGES`|使原生映像搜尋尋找分析工具增強型映像。 若沒有找到指定組件的分析工具增強型映像，Common Language Runtime 會回復為該組件的 JIT。 若指定此旗標及 `COR_PRF_DISABLE_ALL_NGEN_IMAGES` 旗標，則使用 `COR_PRF_DISABLE_ALL_NGEN_IMAGES`。|  
  
<a name="Composite"></a>
### <a name="composite-flags"></a>組合旗標  
  
|member|描述|  
|------------|-----------------|  
|`COR_PRF_ALL`|代表所有 `COR_PRF_MONITOR` 旗標值。|  
|`COR_PRF_ALLOWABLE_AFTER_ATTACH`|代表所有 `COR_PRF_MONITOR` 旗標，這些旗標可在分析工具連結至執行中的應用程式之後加以設定。 語法區段指出此位元遮罩中存在的個別旗標。|  
|`COR_PRF_MONITOR_ALL`|啟用所有回呼事件。|  
|`COR_PRF_MONITOR_IMMUTABLE`|代表所有 `COR_PRF_MONITOR` 旗標，這些旗標只能在初始化期間加以設定。 嘗試在初始化之後變更任何這些旗標，會傳回指出失敗的 `HRESULT` 值。|  
|`COR_PRF_REQUIRE_PROFILE_IMAGE`|代表需要設定檔增強影像的所有 `COR_PRF_MONITOR` 旗標。|  
  
## <a name="remarks"></a>備註  
 值`COR_PRF_MONITOR`與[ICorProfilerInfo：：GetEventMask](icorprofilerinfo-geteventmask-method.md)和[ICorProfilerInfo：setEventMask](icorprofilerinfo-seteventmask-method.md)方法一起使用，用於定義通用語言運行時對探測器的事件通知。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析列舉](profiling-enumerations.md)
- [GetEventMask 方法](icorprofilerinfo-geteventmask-method.md)
- [SetEventMask 方法](icorprofilerinfo-seteventmask-method.md)
