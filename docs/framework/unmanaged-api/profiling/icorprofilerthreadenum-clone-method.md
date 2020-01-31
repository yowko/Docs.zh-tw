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
ms.openlocfilehash: 9048d314404859a4264621a5da91c43c525027f9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868196"
---
# <a name="icorprofilerthreadenumclone-method"></a>ICorProfilerThreadEnum::Clone 方法
取得此[ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md)介面之複本的介面指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>參數  
 `ppEnum`  
 脫銷介面指標的指標，接著指向這個[ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md)介面的複本。 列舉值的複本會與此列舉值分開維護自己的列舉狀態。 不過，複本的初始游標位置與列舉值的目前資料指標位置相同。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerThreadEnum](icorprofilerthreadenum-interface.md)
- [分析介面](profiling-interfaces.md)
