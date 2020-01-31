---
title: ICorProfilerCallback2 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2
helpviewer_keywords:
- ICorProfilerCallback2 interface [.NET Framework profiling]
ms.assetid: 4a261dba-450d-4f1f-8d98-865b58bfc992
topic_type:
- apiref
ms.openlocfilehash: c565d0fe37a091095b18a6d59308f159fe7b4554
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865736"
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2 介面
提供當分析工具已訂閱的事件發生時，common language runtime （CLR）用來通知程式碼分析工具的方法。 介面是 [ICorProfilerCallback](icorprofilercallback-interface.md) 介面的延伸。`ICorProfilerCallback2` 也就是，它會提供 .NET Framework 版本2.0 中引進的新回呼。  
  
> [!NOTE]
> 每個方法的執行都必須傳回 HRESULT，其值為 [成功] 或 [失敗時 E_FAIL] S_OK。 目前，CLR 會忽略[ICorProfilerCallback：： ObjectReferences](icorprofilercallback-objectreferences-method.md)以外的每個回呼所傳回的 HRESULT。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[FinalizeableObjectQueued 方法](icorprofilercallback2-finalizeableobjectqueued-method.md)|通知程式碼分析工具，已將具有完成項的物件排入等候執行緒，以執行其 `Finalize` 方法。|  
|[GarbageCollectionFinished 方法](icorprofilercallback2-garbagecollectionfinished-method.md)|通知分析工具已完成垃圾收集，併發出所有垃圾收集回呼。|  
|[GarbageCollectionStarted 方法](icorprofilercallback2-garbagecollectionstarted-method.md)|通知程式碼分析工具已開始垃圾收集。|  
|[HandleCreated 方法](icorprofilercallback2-handlecreated-method.md)|通知程式碼分析工具，已建立垃圾收集控制碼。|  
|[HandleDestroyed 方法](icorprofilercallback2-handledestroyed-method.md)|通知程式碼分析工具，垃圾收集控制碼已遭終結。|  
|[RootReferences2 方法](icorprofilercallback2-rootreferences2-method.md)|在垃圾收集發生後，通知分析工具關於根參考。 這個方法是[ICorProfilerCallback：： RootReferences](icorprofilercallback-rootreferences-method.md)方法的延伸。|  
|[SurvivingReferences 方法](icorprofilercallback2-survivingreferences-method.md)|通知分析工具有關垃圾收集已被回收的物件參考。|  
|[ThreadNameChanged 方法](icorprofilercallback2-threadnamechanged-method.md)|通知程式碼分析工具，執行緒的名稱已變更。|  
  
## <a name="remarks"></a>備註  
 CLR 會呼叫 `ICorProfilerCallback` （或 `ICorProfilerCallback2`）介面中的方法，以便在分析工具已訂閱的事件發生時，通知分析工具。 這是 CLR 用來與程式碼 profiler 通訊的主要回呼介面。  
  
 程式碼分析工具必須執行 `ICorProfilerCallback` 介面的方法。 針對 .NET Framework 2.0 和更新版本，分析工具也必須執行 `ICorProfilerCallback2` 方法。 每個方法的執行都必須傳回 HRESULT，其值為 [成功] 或 [失敗時 E_FAIL] S_OK。 目前，CLR 會忽略[ICorProfilerCallback：： ObjectReferences](icorprofilercallback-objectreferences-method.md)以外的每個回呼所傳回的 HRESULT。  
  
 程式碼分析工具必須在 Microsoft Windows 登錄（它是執行 `ICorProfilerCallback` 和 `ICorProfilerCallback2` 介面的 COM 物件）中註冊。 程式碼分析工具會透過呼叫[ICorProfilerInfo：： SetEventMask](icorprofilerinfo-seteventmask-method.md)，訂閱想要接收通知的事件。 這通常會在分析工具的[ICorProfilerCallback：： Initialize](icorprofilercallback-initialize-method.md)的執行中完成。 然後，分析工具就能夠在事件即將發生或發生在執行中的執行時間進程時，從執行時間接收通知。  
  
> [!NOTE]
> Profiler 會註冊單一 COM 物件。 如果分析工具的目標是 .NET Framework 版本1.0 或1.1，則該 COM 物件只需要執行 `ICorProfilerCallback`的方法。 如果它的目標是 .NET Framework 2.0 版和更新版本，則 COM 物件也必須執行 `ICorProfilerCallback2`的方法。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [分析介面](profiling-interfaces.md)
- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ICorProfilerCallback3 介面](icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 介面](icorprofilercallback4-interface.md)
