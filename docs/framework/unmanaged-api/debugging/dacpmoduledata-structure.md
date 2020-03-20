---
title: DacpMethodData 結構
ms.date: 02/01/2019
api.name:
- DacpModuleData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpModuleData Structure
helpviewer.keywords:
- DacpModuleData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: c24bdce64eb7e208bf3830940d7beab1ebf92e78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179193"
---
# <a name="dacpmoduledata-structure"></a>DacpMethodData 結構

為模組的運行時資訊定義傳輸緩衝區。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a>成員

| member    | 描述                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | 模組物件的位址。                                           |
| `File`    | 指向可攜式可執行檔 （PE） 檔的指標。                       |
| `ilBase`  | 載入圖像的基的位址。                                 |
| `payLoad` | 用於運行時使用的其他模組資訊的有效負載緩衝區。 |

## <a name="remarks"></a>備註

此結構位於運行時內，不會通過任何標頭或庫檔公開。 要使用它，請定義上面指定的結構。

## <a name="requirements"></a>需求
**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標題：** 沒有  
**庫：** 沒有  
**.NET 框架版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [偵錯結構](debugging-structures.md)
