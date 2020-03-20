---
title: CLRDATA_IL_ADDRESS_MAP 結構
ms.date: 01/16/2019
api.name:
- CLRDATA_IL_ADDRESS_MAP Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure
helpviewer.keywords:
- CLRDATA_IL_ADDRESS_MAP Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e680a7a0dc3209d1988f6c84be0864572a74b3a4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179368"
---
# <a name="clrdata_il_address_map-structure"></a>CLRDATA_IL_ADDRESS_MAP 結構

定義 IL 以解決映射。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```cpp
typedef struct
{
    ULONG32 ilOffset;
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
    CLRDataSourceType type;
} CLRDATA_IL_ADDRESS_MAP;
```

## <a name="members"></a>成員

| member         | 描述                                            |
| -------------- | ------------------------------------------------------ |
| `ilOffset`     | 包含位址範圍的 IL 偏移量              |
| `startAddress` | 範圍的起始位址。                        |
| `endAddress`   | 範圍的結束位址。                          |
| `type`         | 資料的類型。 當前未使用此值 |

## <a name="remarks"></a>備註

此結構位於運行時內，不會通過任何標頭或庫檔公開。 要使用它，請定義上面指定的結構，其中`CLRDATA_ADDRESS`是 64 位不帶正負號的整數。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
**標題：** 沒有  
**庫：** 無 **.NET 框架版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [CLRDataSource 類型枚舉](clrdatasourcetype-enumeration.md)
- [偵錯](index.md)
- [偵錯結構](debugging-structures.md)
