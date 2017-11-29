---
title: "ICorProfilerThreadEnum::Skip 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerThreadEnum.Skip
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type: apiref
caps.latest.revision: "6"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: f492a455165f3b49994beb3220334e2932bf214c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerthreadenumskip-method"></a>ICorProfilerThreadEnum::Skip 方法
將列舉值的資料指標從其目前位置前移，以略過指定數目的項目。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in]要略過的項目數目。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`celt`略過項目。|  
|S_FALSE|少於`celt`項目已略過，表示已沒有多個項目。|  
  
## <a name="remarks"></a>備註  
 這個列舉值的資料指標的新位置時 （目前的位置） + `celt`。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerThreadEnum 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
