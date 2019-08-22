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
ms.openlocfilehash: 8c9a85e9f00027f597795eea55a9bbb0364790f8
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661232"
---
# <a name="icorprofilerinfo10getlohobjectsizethreshold-method"></a>ICorProfilerInfo10:: GetLOHObjectSizeThreshold 方法

取得已設定的大型物件堆積 (LOH) 閾值的值。

## <a name="syntax"></a>語法

```cpp
HRESULT GetLOHObjectSizeThreshold( [out] DWORD *pThreshold );
```

#### <a name="parameters"></a>參數

`pThreshold` \
脫銷大型物件堆積閾值 (以位元組為單位)。

## <a name="remarks"></a>備註

大於大型物件堆積閾值的物件將會配置在大型物件堆積上。 從 .net Core 3.0 開始, 大型物件堆積閾值是可設定`pThreshold`的, 它會包含作用中的大型物件堆積閾值大小 (以位元組為單位)。

## <a name="requirements"></a>需求

**平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。

**標頭：** Corprof.idl .idl, Corprof.idl。h

**LIBRARY:** CorGuids.lib

**.Net 版本:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo10 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
