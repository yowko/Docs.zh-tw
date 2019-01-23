---
title: ICorProfilerObjectEnum 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum
helpviewer_keywords:
- ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 13e1651c-9523-40ef-bfd7-87fb94519f8b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1cb6e12e7badff9bcd00196f50bf1291df630122
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54500180"
---
# <a name="icorprofilerobjectenum-interface"></a>ICorProfilerObjectEnum 介面
提供方法，以循序逐一查看所產生的凍結物件的集合[Ngen.exe （原生映像產生器）](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Clone 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-clone-method.md)|取得這個 `ICorProfilerObjectEnum` 介面複本的介面指標。|  
|[GetCount 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-getcount-method.md)|取得集合中的凍結物件總數。|  
|[Next 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-next-method.md)|取得指定的數目的連續物件從物件，從序列中列舉值的目前位置開始的循序集合。|  
|[Reset 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-reset-method.md)|將這個列舉值的資料指標移至序列的開始位置。|  
|[Skip 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-skip-method.md)|將這個列舉值的資料指標從其目前位置前移，以略過指定的數目的項目。|  
  
## <a name="remarks"></a>備註  
 `ICorProfilerObjectEnum` 介面是列舉值。 它可讓陣列的接收端以適合接收端的速率，從傳送端提取項目。 換句話說，接收者就能夠明確控制陣列元素，藉此避免傳遞大型陣列做為方法參數的相關問題。  
  
 使用[ICorProfilerInfo2::EnumModuleFrozenObjects](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)若要取得的指標`ICorProfilerObjectEnum`介面。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [EnumModuleFrozenObjects 方法](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-enummodulefrozenobjects-method.md)
