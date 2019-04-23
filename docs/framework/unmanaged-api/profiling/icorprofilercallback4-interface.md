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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3eb1f46900199db65be5d14c56bfc0b6f55bf269
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59205130"
---
# <a name="icorprofilercallback4-interface"></a>ICorProfilerCallback4 介面
提供 common language runtime (CLR) 會將資訊傳達給分析工具使用的回呼方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetReJITParameters 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)|可讓程式碼剖析工具，來設定新的重新編譯的方法主體的替代程式碼產生旗標。|  
|[MovedReferences2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)|回報新的版面配置，因為壓縮記憶體回收堆積中的物件。|  
|[ReJITCompilationFinished 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationfinished-method.md)|通知分析工具，在 just-in-time (JIT) 編譯器已完成的函式重新編譯。|  
|[ReJITCompilationStarted 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)|通知分析工具在 just-in-time (JIT) 編譯器已開始重新編譯函式。|  
|[ReJITError 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejiterror-method.md)|報表處理的重新編譯要求時發生錯誤。|  
|[SurvivingReferences2 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)|報告非壓縮記憶體回收造成的堆積中物件配置。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerCallback2 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
