---
title: "ICorProfilerCallback2 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2
helpviewer_keywords: ICorProfilerCallback2 interface [.NET Framework profiling]
ms.assetid: 4a261dba-450d-4f1f-8d98-865b58bfc992
topic_type: apiref
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7927d3b4d41731c9b69154fa8895a8f698f53e31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2 介面
提供用來在分析工具已訂閱的事件發生時，通知程式碼分析工具 common language runtime (CLR) 的方法。 `ICorProfilerCallback2`介面是延伸[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)介面。 也就是說，它會提供.NET Framework 2.0 版中導入新的回呼。  
  
> [!NOTE]
>  每個方法實作必須傳回值 s_ok 只在成功或 E_FAIL 失敗 HRESULT。 目前，CLR 會忽略除了每個回撥所傳回的 HRESULT [icorprofilercallback:: Objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[FinalizeableObjectQueued 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|通知程式碼分析工具的物件具有完成項佇列中的完成項執行緒執行其`Finalize`方法。|  
|[GarbageCollectionFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|記憶體回收回收完成，並為其已發行所有記憶體回收回呼通知分析工具。|  
|[GarbageCollectionStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|已開始在記憶體回收通知的程式碼分析工具。|  
|[HandleCreated 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|通知記憶體回收控制代碼已建立的程式碼分析工具。|  
|[HandleDestroyed 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|通知記憶體回收控制代碼已終結的程式碼分析工具。|  
|[RootReferences2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|在記憶體回收發生後，請通知根參考的相關程式碼剖析工具。 這個方法是延伸[icorprofilercallback:: Rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)方法。|  
|[SurvivingReferences 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|通知分析工具需有未被記憶體回收的物件參考。|  
|[ThreadNameChanged 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|通知程式碼剖析工具，執行緒的名稱已變更。|  
  
## <a name="remarks"></a>備註  
 CLR 會呼叫的方法`ICorProfilerCallback`(或`ICorProfilerCallback2`) 介面，以通知分析工具事件，要在分析工具已訂閱時，就會發生。 這是主要的回呼介面，透過此 CLR 與程式碼分析工具的通訊。  
  
 程式碼分析工具必須實作的方法`ICorProfilerCallback`介面。 .NET Framework 2.0 和更新版本中，分析工具也必須實作`ICorProfilerCallback2`方法。 每個方法實作必須傳回值 s_ok 只在成功或 E_FAIL 失敗 HRESULT。 目前，CLR 會忽略除了每個回撥所傳回的 HRESULT [icorprofilercallback:: Objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)。  
  
 程式碼分析工具必須註冊在 Microsoft Windows 登錄中，其會實作的 COM 物件`ICorProfilerCallback`和`ICorProfilerCallback2`介面。 程式碼分析工具訂閱它要接收通知，藉由呼叫的事件[icorprofilerinfo:: Seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)。 這通常會在程式碼剖析工具實作[icorprofilercallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)。 程式碼剖析工具就能夠從執行階段時通知事件會發生或剛執行的執行階段程序中發生。  
  
> [!NOTE]
>  分析工具註冊單一的 COM 物件。 如果程式碼剖析工具的目標.NET Framework 1.0 或 1.1 版，此 COM 物件只需要實作的方法`ICorProfilerCallback`。 如果它設為目標.NET Framework 2.0 版和更新版本中，COM 物件也必須實作的方法`ICorProfilerCallback2`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerCallback 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback3 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [ICorProfilerCallback4 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
