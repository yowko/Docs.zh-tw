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
ms.openlocfilehash: 5d27ba2de9ff6ed184b6ddf50a517d0dae7715f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723047"
---
# <a name="dacpmoduledata-structure"></a>DacpMethodData 結構

定義模組執行時間資訊的傳輸緩衝區。

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
| `File`    | 可攜式可執行檔的指標， (PE) 檔。                       |
| `ilBase`  | 已載入映射基底的位址。                                 |
| `payLoad` | 執行時間所使用之其他模組資訊的承載緩衝區。 |

## <a name="remarks"></a>備註

此結構存在於執行時間內，且不會透過任何標頭或程式庫檔案來公開。 若要使用它，請依照上述指定的方式定義結構。

## <a name="requirements"></a>需求

**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
**標頭：** 沒有  
連結 **庫：** 沒有  
**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [偵錯結構](debugging-structures.md)
