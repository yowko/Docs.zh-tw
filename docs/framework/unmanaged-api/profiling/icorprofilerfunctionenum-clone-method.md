---
title: ICorProfilerFunctionEnum::Clone 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b6c1efe2a7d831f26556dbf501176f02588f2e0d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780330"
---
# <a name="icorprofilerfunctionenumclone-method"></a>ICorProfilerFunctionEnum::Clone 方法
取得介面指標，這一份[ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)介面。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
## <a name="parameters"></a>參數  
 `ppEnum`  
 [out]介面指標，其中，依次指向的副本的指標[ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)介面。 列舉值的複本會維護它自己分開這個列舉值的列舉型別狀態。 不過，複本的初始資料指標位置會是這個列舉值目前的游標位置相同。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl, CorProf.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorProfilerFunctionEnum 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
