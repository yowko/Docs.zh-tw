---
title: ICorProfilerThreadEnum 介面
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum
helpviewer_keywords:
- ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type:
- apiref
ms.openlocfilehash: 147694431d2c378b856577ef5a60e8a8b4e9a7a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721214"
---
# <a name="icorprofilerthreadenum-interface"></a>ICorProfilerThreadEnum 介面

提供方法，以循序逐一查看 Common Language Runtime 中的執行緒集合。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[Clone 方法](icorprofilerthreadenum-clone-method.md)|取得這個 `ICorProfilerThreadEnum` 介面複本的介面指標。|  
|[GetCount 方法](icorprofilerthreadenum-getcount-method.md)|取得應用程式所使用的執行緒數目。|  
|[下一個方法](icorprofilerthreadenum-next-method.md)|從循序執行緒集合中取得指定的連續執行緒數目，從序列中列舉值的目前位置開始。|  
|[Reset 方法](icorprofilerthreadenum-reset-method.md)|將列舉值的資料指標移至序列的開始位置。|  
|[Skip 方法](icorprofilerthreadenum-skip-method.md)|將列舉值的資料指標從其目前位置前移，以略過指定數目的項目。|  
  
## <a name="remarks"></a>備註  

 `ICorProfilerThreadEnum` 介面是列舉值。 它可讓陣列的接收端以適合接收端的速率，從傳送端提取項目。 換句話說，接收端能夠明確控制陣列項目的流程，因此可避免與傳遞大型陣列做為方法參數相關的問題發生。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo 介面](icorprofilerinfo-interface.md)
- [分析介面](profiling-interfaces.md)
