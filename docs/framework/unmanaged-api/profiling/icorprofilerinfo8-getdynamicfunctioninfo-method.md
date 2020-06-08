---
title: ICorProfilerInfo8::GetDynamicFunctionInfo
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetDynamicFunctionInfo
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: eaf33f3b0de7a18e400cd16d29c046784e2e190f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495316"
---
# <a name="icorprofilerinfo8getdynamicfunctioninfo-method"></a>ICorProfilerInfo8：： GetDynamicFunctionInfo 方法

抓取動態方法的相關資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetDynamicFunctionInfo( [in]  FunctionID              functionId,
                                [out] ModuleID                *moduleId,
                                [out] PCCOR_SIGNATURE         *ppvSig,
                                [out] ULONG                   *pbSig,
                                [in]  ULONG                   cchName,
                                [out] ULONG                   *pcchName,
                                [out] WCHAR                   wszName[]);
```

## <a name="parameters"></a>參數

- `functionId`

  \[in] 要取得其資訊的函式識別碼。

- `moduleId`

  \[in] 定義函式之父類別所在模組的指標。

- `ppvSig`

  \[out] 函式簽章的指標。

- `pbSig`

  \[out] 函式簽章的位元組計數指標。

- `cchName`

  \[in] 陣列的大小上限 `wszName` 。

- `pcchName`

  \[out] 陣列中的字元數 `wszName` 。

- `wszName`

  \[out] 陣列 `WCHAR` ，其中是函式的名稱（如果有的話）。

## <a name="remarks"></a>備註

某些方法（例如 IL Stub 或 LCG）沒有相關聯的中繼資料可使用[IMetaDataImport](../metadata/imetadataimport-interface.md)和[IMetaDataImport2](../metadata/imetadataimport2-interface.md) api 來抓取。 分析工具可以透過指令指標或接聽[ICorProfilerCallback8：:D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)，來遇到這類方法。

此 API 可用於抓取動態方法的相關資訊，包括易記名稱（如果有的話）。

## <a name="requirements"></a>規格需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo8 介面](icorprofilerinfo8-interface.md)
