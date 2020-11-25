---
title: ICorProfilerThreadEnum::Clone 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Clone method [.NET Framework profiling]
ms.assetid: 5a278bc9-88e2-4c69-b035-9d550dd77081
topic_type:
- apiref
ms.openlocfilehash: de2584b56701f4cffb6a108a5872641ec40e5762
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702520"
---
# <a name="icorprofilerthreadenumclone-method"></a>ICorProfilerThreadEnum::Clone 方法

取得這個 [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) 介面複本的介面指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>參數  

 `ppEnum`  
 擴展指向介面指標的指標，再指向這個 [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md) 介面的複本。 列舉值的複本會從這個列舉值分開維護自己的列舉狀態。 但是，複製的初始游標位置與列舉值目前的資料指標位置相同。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md)
- [分析介面](profiling-interfaces.md)
