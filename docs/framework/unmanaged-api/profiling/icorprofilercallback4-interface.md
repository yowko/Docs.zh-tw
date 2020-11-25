---
title: ICorProfilerCallback4 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
ms.openlocfilehash: 942ee8234b79c6579acc009960f4571801fc3185
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730288"
---
# <a name="icorprofilercallback4-interface"></a>ICorProfilerCallback4 介面

提供 common language runtime (CLR) 用來將資訊傳達給 profiler 的回呼方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetReJITParameters 方法](icorprofilercallback4-getrejitparameters-method.md)|允許程式碼分析工具為新重新編譯的方法主體設定替代程式碼產生旗標。|  
|[MovedReferences2 方法](icorprofilercallback4-movedreferences2-method.md)|在壓縮垃圾收集之後，報告堆積中物件的新版面配置。|  
|[ReJITCompilationFinished 方法](icorprofilercallback4-rejitcompilationfinished-method.md)|通知分析工具，及時 (JIT) 編譯器已完成函式的重新編譯。|  
|[ReJITCompilationStarted 方法](icorprofilercallback4-rejitcompilationstarted-method.md)|通知分析工具，及時 (JIT) 編譯器已開始重新編譯函數。|  
|[ReJITError 方法](icorprofilercallback4-rejiterror-method.md)|報告處理重新編譯要求時發生錯誤。|  
|[SurvivingReferences2 方法](icorprofilercallback4-survivingreferences2-method.md)|報告非壓縮記憶體回收造成的堆積中物件配置。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback2 介面](icorprofilercallback2-interface.md)
- [分析介面](profiling-interfaces.md)
- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
