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
ms.openlocfilehash: e536e61a8d812e442e1e54188c99d6a1d4586757
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049722"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 介面
[.NET Framework 4.7 及更新版本中支援]  

 子類別[ICorProfilerCallback7](icorprofilercallback7-interface.md)提供 common language runtime 用來通知分析工具中的動態方法的 JIT 編譯已啟動並完成的回呼方法。 
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted 方法](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|通知分析工具已啟動的動態方法的 JIT 編譯。|  
|[DynamicMethodJITCompilationFinished 方法](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|通知分析工具已完成的動態方法的 JIT 編譯。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [分析介面](profiling-interfaces.md)
- [ICorProfilerCallback9 介面](icorprofilercallback9-interface.md)
