---
title: ICorProfilerThreadEnum::GetCount 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2b803c83b905df47b3957e07c0d64e7ce6f6d303
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerthreadenumgetcount-method"></a>ICorProfilerThreadEnum::GetCount 方法
取得應用程式所使用的執行緒數目。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [out]應用程式所使用的執行緒數目。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerThreadEnum 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
