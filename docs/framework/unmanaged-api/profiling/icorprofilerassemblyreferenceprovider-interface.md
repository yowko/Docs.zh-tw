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
ms.openlocfilehash: 2cee012be2665f5a7212600ec11e401b18160d8b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95691392"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a>ICorProfilerAssemblyReferenceProvider 介面

[.NET Framework 4.5.2 與更新版本提供支援]  
  
 可讓分析工具通知 common language runtime (CLR) 程式碼剖析工具將在 [ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) 回呼中加入的元件參考。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[AddAssemblyReference 方法](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|告知 CLR 程式碼剖析工具計畫在 [ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) 回呼中加入的元件參考。|  
  
## <a name="remarks"></a>備註  

 CLR 會 `ICorProfilerAssemblyReferenceProvider` 在 [ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) 回呼中傳遞介面物件給 profiler。 這可讓分析工具通知 CLR 元件參考，讓分析工具計畫稍後在 [ICorProfilerCallback：： ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)中新增。 回呼中。 這會增進 CLR 組件參考結束查核器及其演算法的精確度，以判定組件是否可以共用。  
  
 這個介面只能用在將此介面物件傳遞至分析工具的 [ICorProfilerCallback6：： GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) 回呼中。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [分析介面](profiling-interfaces.md)
