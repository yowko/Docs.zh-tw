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
ms.openlocfilehash: fce89cc2b3b0104ba017b7df9105dea3f6ec4e91
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868222"
---
# <a name="icorprofilerobjectenum-interface"></a>ICorProfilerObjectEnum 介面
提供方法，依序逐一查看[ngen.exe （原生映射](../../../../docs/framework/tools/ngen-exe-native-image-generator.md)產生器）所產生的凍結物件集合。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Clone 方法](icorprofilerobjectenum-clone-method.md)|取得這個 `ICorProfilerObjectEnum` 介面複本的介面指標。|  
|[GetCount 方法](icorprofilerobjectenum-getcount-method.md)|取得集合中凍結物件的總數。|  
|[Next 方法](icorprofilerobjectenum-next-method.md)|從序列中列舉值的目前位置開始，從物件的連續集合中取得指定的連續物件數目。|  
|[Reset 方法](icorprofilerobjectenum-reset-method.md)|將這個列舉值的資料指標移至序列的開始位置。|  
|[Skip 方法](icorprofilerobjectenum-skip-method.md)|將此列舉值的資料指標從其目前位置前移，以略過指定數目的元素。|  
  
## <a name="remarks"></a>備註  
 `ICorProfilerObjectEnum` 介面是列舉值。 它可讓陣列的接收端以適合接收端的速率，從傳送端提取項目。 換句話說，接收者可以明確控制陣列元素的流程，藉此避免傳遞大型陣列做為方法參數的相關問題。  
  
 使用[ICorProfilerInfo2：： EnumModuleFrozenObjects](icorprofilerinfo2-enummodulefrozenobjects-method.md)取得 `ICorProfilerObjectEnum` 介面的指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [分析介面](profiling-interfaces.md)
- [EnumModuleFrozenObjects 方法](icorprofilerinfo2-enummodulefrozenobjects-method.md)
