---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 8412020fb98fde245b873a2f0c6a355f6436f712
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868274"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>ICorProfilerInfo9：： GetNativeCodeStartAddresses 方法

假設有 functionId 和 rejitId，會列舉此程式碼中所有目前存在之已編譯版本的原生程式碼起始位址。

## <a name="syntax"></a>語法

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a>參數

- `functionId`

  中的 \[] 應傳回其機器碼起始位址的函式識別碼。

- `reJitId`

  \[in] JIT 重新編譯函式的身分識別。

- `cCodeStartAddresses`

  \[in] `codeStartAddresses` 陣列的大小上限。

- `pcCodeStartAddresses`

  \[out] 可用的位址數目。

- `codeStartAddresses`

  \[out] `UINT_PTR`的陣列，其中每一個都是所指定函式的原生主體的起始位址。

## <a name="remarks"></a>備註

啟用階層式編譯時，函數可能會有一個以上的機器碼主體。

## <a name="requirements"></a>需求

**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.Net 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>請參閱

- [ICorProfilerInfo9 介面](icorprofilerinfo9-interface.md)
