---
title: ICorProfilerInfo9::GetILToNativeMapping3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetILToNativeMapping3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 14391a0fe046b44aedca1da2bc42c7d962e1a5e7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541274"
---
# <a name="icorprofilerinfo9getiltonativemapping3-method"></a>ICorProfilerInfo9：： GetILToNativeMapping3 方法

在指定機器碼起始位址的情況下，傳回此程式碼的程式碼的原生對應資訊。

## <a name="syntax"></a>語法

```cpp
HRESULT GetILToNativeMapping3( [in]  UINT_PTR pNativeCodeStartAddress,
                               [in]  ULONG32 cMap,
                               [out] ULONG32 *pcMap,
                               [out] COR_DEBUG_IL_TO_NATIVE_MAP map[]);
```

## <a name="parameters"></a>參數

- `pNativeCodeStartAddress`

  \[in] 原生函數開頭的指標。

- `cMap`

  \[in] 陣列的大小上限 `map` 。

- `pcMap`

  \[out）可用 COR_DEBUG_IL_TO_NATIVE_MAP 結構的總數。

- `map`

  \[out] [COR_DEBUG_IL_TO_NATIVE_MAP](../debugging/cor-debug-il-to-native-map-structure.md) 結構的陣列，其中每個結構都指定位移。 `GetILToNativeMapping3` 方法傳回之後，`map` 將會包含部分或所有 `COR_DEBUG_IL_TO_NATIVE_MAP` 結構。

## <a name="remarks"></a>備註

啟用分層式編譯時，方法可能會有一個以上的機器碼主體。 [ICorProfilerInfo9：： GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md) 會傳回所有原生程式碼主體的起始位址。

## <a name="requirements"></a>需求

**平臺：** 請參閱 [.Net Core 支援的作業系統](../../../core/install/windows.md?pivots=os-windows)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.NET Framework 版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo9 介面](icorprofilerinfo9-interface.md)
