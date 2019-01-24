---
title: ICorProfilerCallback9 Interface
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a6c480af921fb0259ef85beec8d8f65bdd430522
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689298"
---
# <a name="icorprofilercallback9-interface"></a>ICorProfilerCallback9 Interface
[.NET Framework 4.7.2 和更新版本中支援]  

 子類別[ICorProfilerCallback8](icorprofilercallback8-interface.md)提供一種回呼方法，common language runtime 用來通知分析工具的動態方法已被記憶體回收，並接著卸載。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[DynamicMethodUnloaded 方法](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|通知的動態方法已被記憶體回收，並接著卸載分析工具。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
**.NET framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>另請參閱
- [分析介面](profiling-interfaces.md)
- [ICorProfilerCallback8 介面](icorprofilercallback9-interface.md)
- [ICorProfilerCallback8.DynamicMethodJITCompilationStarted 方法](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8.DynamicMethodJITCompilationFinished 方法](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
