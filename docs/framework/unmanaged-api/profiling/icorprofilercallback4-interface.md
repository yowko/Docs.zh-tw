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
ms.openlocfilehash: 295d3d440529623f4569fd6c5f4debe7e4558990
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499437"
---
# <a name="icorprofilercallback4-interface"></a>ICorProfilerCallback4 介面
提供通用語言執行時間（CLR）用來將資訊傳達給分析工具的回呼方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetReJITParameters 方法](icorprofilercallback4-getrejitparameters-method.md)|可讓程式碼分析工具針對新重新編譯的方法主體，設定替代的程式碼產生旗標。|  
|[MovedReferences2 方法](icorprofilercallback4-movedreferences2-method.md)|報告壓縮垃圾收集造成的堆積中物件的新版面配置。|  
|[ReJITCompilationFinished 方法](icorprofilercallback4-rejitcompilationfinished-method.md)|通知分析工具，及時（JIT）編譯器已完成函數的重新編譯。|  
|[ReJITCompilationStarted 方法](icorprofilercallback4-rejitcompilationstarted-method.md)|通知 profiler，及時（JIT）編譯器已開始重新編譯函式。|  
|[ReJITError 方法](icorprofilercallback4-rejiterror-method.md)|回報處理重新編譯要求時所發生的錯誤。|  
|[SurvivingReferences2 方法](icorprofilercallback4-survivingreferences2-method.md)|報告非壓縮記憶體回收造成的堆積中物件配置。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback2 介面](icorprofilercallback2-interface.md)
- [分析介面](profiling-interfaces.md)
- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
