---
title: ICorProfilerCallback3::ProfilerAttachComplete 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: 8168f6f1079ec34b9fb53a485da0f32175446719
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865424"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a>ICorProfilerCallback3::ProfilerAttachComplete 方法
由 common language runtime （CLR）呼叫，表示分析工具現在可以呼叫[ICorProfilerInfo3：： EnumJITedFunctions](icorprofilerinfo3-enumjitedfunctions-method.md)和[ICorProfilerInfo3：： EnumModules](icorprofilerinfo3-enummodules-method.md) catch 方法。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a>備註  
 呼叫[ICorProfilerCallback3：： InitializeForAttach](icorprofilercallback3-initializeforattach-method.md)方法之後，就會發出 `ProfilerAttachComplete` 回呼。 這表示：  
  
- `InitializeForAttach` 中分析工具所要求的回呼已啟動。  
  
- 分析工具現在可以對關聯的 ID 執行更新，而不必擔心遺漏通知。  
  
 CLR 會忽略這個回呼的傳回值。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerCallback 介面](icorprofilercallback-interface.md)
- [ICorProfilerInfo3 介面](icorprofilerinfo3-interface.md)
- [分析介面](profiling-interfaces.md)
- [程式碼剖析](index.md)
