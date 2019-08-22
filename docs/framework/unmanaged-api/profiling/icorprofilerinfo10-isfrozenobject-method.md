---
title: ICorProfilerInfo10::IsFrozenObject
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.IsFrozenObject
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: d212c06c7ddc9f22095c0b95f19fd1083482435c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69661227"
---
# <a name="icorprofilerinfo10isfrozenobject-method"></a>ICorProfilerInfo10:: IsFrozenObject 方法

給定 ObjectID, 判斷物件是否在唯讀區段中。

## <a name="syntax"></a>語法

```cpp
HRESULT IsFrozenObject( [in]  ObjectID objectId,
                        [out] BOOL *pbFrozen);
```

#### <a name="parameters"></a>參數

`objectId` \
在要檢查的物件。

`pbFrozen` \
脫銷`BOOL` , 指出物件是否在唯讀區段中。

## <a name="requirements"></a>需求

**平台：** 請參閱[.Net Core 支援的作業系統](../../../core/windows-prerequisites.md#net-core-supported-operating-systems)。

**標頭：** Corprof.idl .idl, Corprof.idl。h

**LIBRARY:** CorGuids.lib

**.Net 版本:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>另請參閱

- [ICorProfilerInfo10 介面](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
