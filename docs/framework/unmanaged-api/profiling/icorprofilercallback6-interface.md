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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05e571149a794cbffa9e602255455d779a83e2a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback6-interface"></a>ICorProfilerCallback6 介面
[在 .NET Framework 4.5.2 及更新版本中支援]  
  
 子類別[ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)提供 common language runtime 用於通知分析工具組件載入的回撥方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetAssemblyReferences 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|當 Common Language Runtime 執行組件參考關閉查核時，通知分析工具組件處於非常早期的載入中階段。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
