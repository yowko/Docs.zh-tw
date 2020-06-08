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
ms.openlocfilehash: 6822757608429ca5f4ef9520ab7574d440b67b26
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495252"
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

  \[in] managed 程式碼中的指令指標。

- `pFunctionId`

  \[out] 函數識別碼。

- `pReJitId`

  \[out] 函式之 JIT 重新編譯版本的識別。

## <a name="remarks"></a>備註

這個方法適用于動態和非動態方法。 它是[GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md)的超集合，僅適用于具有中繼資料的函式。

## <a name="requirements"></a>規格需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.NET Framework 版本：**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo8 介面](icorprofilerinfo8-interface.md)
