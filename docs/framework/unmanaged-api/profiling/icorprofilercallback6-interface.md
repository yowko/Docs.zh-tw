---
title: ICorProfilerCallback6 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type:
- apiref
ms.openlocfilehash: 90071121411b706052e1cbb4cb647536dae2835a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864865"
---
# <a name="icorprofilercallback6-interface"></a>ICorProfilerCallback6 介面
[.NET Framework 4.5.2 與更新版本提供支援]  
  
 [ICorProfilerCallback5](icorprofilercallback5-interface.md)的子類別，提供通用語言執行時間用來通知分析工具元件正在載入的回呼方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetAssemblyReferences 方法](icorprofilercallback6-getassemblyreferences-method.md)|當 Common Language Runtime 執行組件參考關閉查核時，通知分析工具組件處於非常早期的載入中階段。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [分析介面](profiling-interfaces.md)
