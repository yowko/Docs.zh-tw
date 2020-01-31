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
ms.openlocfilehash: 9b5059d9e4bf9b79dc67664c7a7971041d1cf35b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861680"
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

  在中 \[] 要取得其資訊的函式識別碼。

- `moduleId`

  \[in]：定義函式之父類別所在模組的指標。

- `ppvSig`

  \[out] 函式簽章的指標。

- `pbSig`

  \[out] 函式簽章的位元組計數指標。

- `cchName`

  \[in] `wszName` 陣列的大小上限。

- `pcchName`

  \[out] `wszName` 陣列中的字元數。

- `wszName`

  \[out] `WCHAR` 的陣列，這是函式的名稱（如果有的話）。

## <a name="remarks"></a>備註

某些方法（例如 IL Stub 或 LCG）沒有相關聯的中繼資料可使用[IMetaDataImport](../metadata/imetadataimport-interface.md)和[IMetaDataImport2](../metadata/imetadataimport2-interface.md) api 來抓取。 分析工具可以透過指令指標或接聽[ICorProfilerCallback8：:D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)，來遇到這類方法。

此 API 可用於抓取動態方法的相關資訊，包括易記名稱（如果有的話）。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>請參閱

- [ICorProfilerInfo8 介面](icorprofilerinfo8-interface.md)
