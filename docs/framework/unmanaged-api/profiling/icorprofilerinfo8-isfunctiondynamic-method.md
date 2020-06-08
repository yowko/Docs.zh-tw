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
ms.openlocfilehash: c88279d361ea78a2e910c4621e92c500902d9124
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495121"
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

  \[in] 識別有問題的函式 `FunctionID` 。

- `isDynamic`

  \[out] 的指標 `BOOL` ，其中會包含一個值，指出函數是否沒有中繼資料。

## <a name="remarks"></a>備註

如果函式沒有中繼資料，則會將其視為動態。 某些方法（例如 IL Stub 或 LCG 方法）沒有相關聯的中繼資料可使用 IMetaDataImport Api 來抓取。 分析工具可以透過指令指標或接聽[ICorProfilerCallback：:D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)，來發現這些方法。

## <a name="requirements"></a>規格需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo8 介面](icorprofilerinfo8-interface.md)
