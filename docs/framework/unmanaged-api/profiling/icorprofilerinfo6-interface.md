---
title: ICorProfilerInfo6 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo6
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 6f2bb148-1e2b-4e45-a5a5-0ceddc40064b
ms.openlocfilehash: 80ac17a96e5c1c8c32cfc336da6c2be30eaf80fd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868365"
---
# <a name="icorprofilerinfo6-interface"></a>ICorProfilerInfo6 介面
[在 .NET Framework 4.6 和更新版本中支援]  
  
 [ICorProfilerInfo5](icorprofilerinfo5-interface.md)的子類別，可為指定 NGen 模組中定義的所有方法提供列舉值，並內嵌指定的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod 方法](icorprofilerinfo6-enumngenmodulemethodsinliningthismethod-method.md)|針對屬於給定 NGen 模組並內嵌在指定方法主體中的所有方法，傳回列舉值。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [分析介面](profiling-interfaces.md)
