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
ms.openlocfilehash: 50b4de2de3e74a5835ee5706999892735269d4c2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861732"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a>ICorProfilerInfo8：： IsFunctionDynamic 方法

判斷函數是否沒有相關聯的中繼資料。

## <a name="syntax"></a>語法

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a>參數

- `functionId`

  \[in] 識別有問題之函式的 `FunctionID`。

- `isDynamic`

  \[out] `BOOL` 的指標，其中會包含一個值，指出函數是否沒有中繼資料。

## <a name="remarks"></a>備註

如果函式沒有中繼資料，則會將其視為動態。 某些方法（例如 IL Stub 或 LCG 方法）沒有相關聯的中繼資料可使用 IMetaDataImport Api 來抓取。 分析工具可以透過指令指標或接聽[ICorProfilerCallback：:D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)，來發現這些方法。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>請參閱

- [ICorProfilerInfo8 介面](icorprofilerinfo8-interface.md)
