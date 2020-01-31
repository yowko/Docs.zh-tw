---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 6d50a5d74eccff6fe39aca111f768bac4d8f2e2e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868326"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a>ICorProfilerInfo8：： GetFunctionFromIP3 方法

將 managed 程式碼指令指標對應至 FunctionID。 這個方法適用于動態和非動態方法。

## <a name="syntax"></a>語法

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a>參數

- `ip`

  中的 \[] managed 程式碼中的指令指標。

- `pFunctionId`

  \[out] 函數識別碼。

- `pReJitId`

  \[out] 函式之 JIT 重新編譯版本的識別。

## <a name="remarks"></a>備註

這個方法適用于動態和非動態方法。 它是[GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md)的超集合，僅適用于具有中繼資料的函式。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.NET framework 版本：** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>請參閱

- [ICorProfilerInfo8 介面](icorprofilerinfo8-interface.md)
