---
title: ICorProfilerAssemblyReferenceProvider 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerAssemblyReferenceProvider
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffb891e61fcb34e6d33a069fc32e68865739b86b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a>ICorProfilerAssemblyReferenceProvider 介面
[在 .NET Framework 4.5.2 及更新版本中支援]  
  
 可讓分析工具通知分析工具會在中加入的組件參考的 common language runtime (CLR) [icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AddAssemblyReference 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|通知分析工具計劃要在加入的組件參考的 CLR [ModuleLoadFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)回呼。|  
  
## <a name="remarks"></a>備註  
 CLR 會傳遞分析工具`ICorProfilerAssemblyReferenceProvider`介面中的物件[icorprofilercallback6:: Getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)回呼。 這可讓分析工具通知分析工具計劃要在稍後加入的組件參考的 CLR [icorprofilercallback:: Moduleloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)。 回呼中。 這會增進 CLR 組件參考結束查核器及其演算法的精確度，以判定組件是否可以共用。  
  
 這個介面可以只能用在[icorprofilercallback6:: Getassemblyreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)將此介面物件傳遞至分析工具回呼。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
