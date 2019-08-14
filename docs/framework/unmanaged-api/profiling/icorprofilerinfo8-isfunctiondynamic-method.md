---
title: ICorProfilerInfo8::IsFunctionDynamic
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 71c4e749368dce65d5250b9ab78fd8713e9d61a0
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973868"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a>ICorProfilerInfo8:: IsFunctionDynamic 方法
  
  判斷函數是否沒有相關聯的中繼資料。    
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```  
  
#### <a name="parameters"></a>參數  
 `functionId` \
  在 `FunctionID`識別有問題之函數的。

  `isDynamic` \
  脫銷的指標`BOOL` , 其中會包含一個值, 指出函式是否沒有中繼資料。

## <a name="remarks"></a>備註  
 如果函式沒有中繼資料, 則會將其視為動態。 某些方法 (例如 IL Stub 或 LCG 方法) 沒有相關聯的中繼資料可使用 IMetaDataImport Api 來抓取。 分析工具可以透過指令指標或接聽[ICorProfilerCallback::D ynamicmethodjitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md), 來發現這些方法。

## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Corprof.idl .idl, Corprof.idl。h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET Framework 版本:** [!包含[net_current_v472plus](../../../../includes/net-current-v472plus.md)  
  
## <a name="see-also"></a>另請參閱
- [ICorProfilerInfo8 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)

