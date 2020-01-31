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
ms.openlocfilehash: 95473a8ce8d5fd7540228ecd9767448e51b5b326
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868980"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a>ICorProfilerInfo10：： GetLOHObjectSizeThreshold 方法

取得已設定的大型物件堆積（LOH）閾值的值。

## <a name="syntax"></a>語法

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

## <a name="parameters"></a>參數

- `pThreshold`

  \[out] 大型物件堆積閾值（以位元組為單位）。

## <a name="remarks"></a>備註

大於大型物件堆積閾值的物件將會配置在大型物件堆積上。 從 .NET Core 3.0 開始，可設定大型物件堆積閾值，`pThreshold` 將包含作用中的大型物件堆積閾值大小（以位元組為單位）。

## <a name="requirements"></a>需求

**平臺：** 請參閱[.Net Core 支援的作業系統](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows)。

**標頭：** CorProf.idl、CorProf.h

**程式庫：** CorGuids.lib

**.Net 版本：** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>請參閱

- [ICorProfilerInfo10 介面](icorprofilerinfo10-interface.md)
