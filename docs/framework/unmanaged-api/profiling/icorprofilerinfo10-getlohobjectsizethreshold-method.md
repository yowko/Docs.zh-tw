---
title: ICorProfilerInfo10::GetLOHObjectSizeThreshold
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.GetLOHObjectSizeThreshold
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 280f0a401f87f81e1ef9d4a2c85c06599442b5ec
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90543942"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a>ICorProfilerInfo10：： GetLOHObjectSizeThreshold 方法

取得已設定之大型物件堆積 (LOH) 臨界值的值。

## <a name="syntax"></a>語法

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a>參數

- `pThreshold`

  \[out）大型物件堆積閾值（以位元組為單位）。

## <a name="remarks"></a>備註

大於大型物件堆積閾值的物件將會配置在大型物件堆積上。 從 .NET Core 3.0 開始，可以設定大型物件堆積閾值，其中 `pThreshold` 將包含使用中的大型物件堆積閾值大小（以位元組為單位）。

## <a name="requirements"></a>需求

**平臺：** 請參閱 [.Net Core 支援的作業系統](../../../core/install/windows.md?pivots=os-windows)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.Net 版本：**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo10 介面](icorprofilerinfo10-interface.md)
