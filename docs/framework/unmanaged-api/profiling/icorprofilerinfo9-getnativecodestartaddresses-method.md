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
ms.openlocfilehash: ca1643dfa980fa647164accf6432082428124acb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541235"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a>ICorProfilerInfo9：： GetNativeCodeStartAddresses 方法

在指定 functionId 和 rejitId 的情況下，列舉此程式碼目前存在的所有可編譯版本的機器碼開始位址。

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

  \[in] 應傳回其原生程式碼起始位址的函式識別碼。

- `reJitId`

  \[in] JIT 重新編譯函式的識別。

- `cCodeStartAddresses`

  \[in] 陣列的大小上限 `codeStartAddresses` 。

- `pcCodeStartAddresses`

  \[out] 可用的位址數目。

- `codeStartAddresses`

  \[out）的陣列 `UINT_PTR` ，其中每一個都是指定之函式之原生主體的起始位址。

## <a name="remarks"></a>備註

啟用分層式編譯時，函式可能會有一個以上的機器碼主體。

## <a name="requirements"></a>需求

**平臺：** 請參閱 [.Net Core 支援的作業系統](../../../core/install/windows.md?pivots=os-windows)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.Net 版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo9 介面](icorprofilerinfo9-interface.md)
