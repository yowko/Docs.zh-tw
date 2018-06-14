---
title: ICorProfilerCallback8 介面
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b92120cc5948efca696d922448da215601f9e6b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455279"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 介面
[在.NET Framework 4.7 和更新版本中支援]  

 子類別[ICorProfilerCallback7](icorprofilercallback7-interface.md)提供 common language runtime 用於通知的動態方法的 JIT 編譯已啟動及完成的分析工具回呼方法。 
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted 方法](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|通知分析工具的動態方法的 JIT 編譯已啟動。|  
|[DynamicMethodJITCompilationFinished 方法](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|通知分析工具已完成的動態方法的 JIT 編譯。|  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱  
[分析介面](profiling-interfaces.md)   
[ICorProfilerCallback9 介面](icorprofilercallback9-interface.md)
