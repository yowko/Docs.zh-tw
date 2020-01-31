---
title: ICorProfilerFunctionEnum::Next 方法
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Next Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Next
helpviewer_keywords:
- ICorProfilerFunctionEnum::Next method [.NET Framework profiling]
- Next method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 5ed4aa83-ce56-4b9f-9237-5da7587787fe
topic_type:
- apiref
ms.openlocfilehash: 9c7fa25712858d1119b45fc742a5d23454b55273
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864462"
---
# <a name="icorprofilerfunctionenumnext-method"></a>ICorProfilerFunctionEnum::Next 方法
從循序函式集合中取得指定的連續函式數目，從序列中列舉值的目前位置開始。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Next([in]  ULONG      celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                    COR_PRF_FUNCTION ids[],  
             [out] ULONG *   pceltFetched);  
```  
  
## <a name="parameters"></a>參數  
 `celt`  
 [in] 要擷取的函式數目。  
  
 `ids`  
 [out] `COR_PRF_FUNCTION` 值的陣列，每個值各代表一個擷取的函式。  
  
 `pceltFetched`  
 [out] `ids` 陣列中實際傳回之函式數目的指標。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已傳回 `celt` 項目。|  
|S_FALSE|傳回少於 `celt` 的項目數，表示列舉已完成。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorProf.idl、CorProf.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorProfilerFunctionEnum 介面](icorprofilerfunctionenum-interface.md)
- [分析介面](profiling-interfaces.md)
