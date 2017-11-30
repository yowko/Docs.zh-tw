---
title: "ICorProfilerModuleEnum::Next 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum.Next Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerModuleEnum::Next
helpviewer_keywords:
- ICorProfilerModuleEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: a3cea59d-7622-4323-897a-0a464c40f77f
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c20b6970c0df30b75bacf76f52c7610bd4a3a5e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilermoduleenumnext-method"></a>ICorProfilerModuleEnum::Next 方法
從循序模組集合中取得指定的連續模組數目，從序列中列舉值的目前位置開始。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    ModuleID ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
#### <a name="parameters"></a>參數  
 `celt`  
 [in] 要擷取的模組數目。  
  
 `ids`  
 [out] `ModuleID` 值的陣列，每個值各代表一個擷取的模組。  
  
 `pceltFetched`  
 [out] `ids` 陣列中實際傳回之項目數目的指標。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT 以及 HRESULT 錯誤，以指出方法失敗。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已傳回 `celt` 項目。|  
|S_FALSE|傳回少於 `celt` 的項目數，表示列舉已完成。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICorProfilerModuleEnum 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)  
 [分析介面](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
