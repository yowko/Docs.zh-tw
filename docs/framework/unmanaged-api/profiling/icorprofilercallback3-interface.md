---
title: ICorProfilerCallback3 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
ms.openlocfilehash: ad9c5445cbef0be7919570db64b027556d923752
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865567"
---
# <a name="icorprofilercallback3-interface"></a>ICorProfilerCallback3 介面
提供公用語言執行時間（CLR）用來將附加和卸離狀態資訊傳達給分析工具的回呼方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[InitializeForAttach 方法](icorprofilercallback3-initializeforattach-method.md)|由 CLR 呼叫，讓分析工具在附加作業之後有機會初始化其狀態。|  
|[ProfilerAttachComplete 方法](icorprofilercallback3-profilerattachcomplete-method.md)|由 CLR 呼叫以指出分析工具現在可以呼叫 catch 方法。|  
|[ProfilerDetachSucceeded 方法](icorprofilercallback3-profilerdetachsucceeded-method.md)|通知分析工具 Common Language Runtime (CLR) 即將卸載分析工具 DLL。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [分析介面](profiling-interfaces.md)
- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [ICorProfilerCallback2 介面](icorprofilercallback2-interface.md)
- [ICorProfilerCallback4 介面](icorprofilercallback4-interface.md)
