---
title: ISOSDacInterface：： GetModuleData 方法
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetModuleData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetModuleData Method
helpviewer.keywords:
- ISOSDacInterface::GetModuleData Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: b302100eb6cbfa83896cd358762c496ea01f7509
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420977"
---
# <a name="isosdacinterfacegetmoduledata-method"></a>ISOSDacInterface：： GetModuleData 方法

提取對應至在指定位址載入之模組的資料。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT GetModuleData(
    CLRDATA_ADDRESS moduleAddr,
    DacpModuleData *data
);
```

## <a name="parameters"></a>參數

`moduleAddr`\
在要為其取得資訊的模組位址。

`data`\
脫銷用來保存已載入模組之資訊的[dacpmethoddata 結構](dacpmoduledata-structure.md)。

## <a name="remarks"></a>備註

提供的方法是介面的一部分 `ISOSDacInterface` ，而且會對應至虛擬方法資料表的第14個位置。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
**標頭：** 無  
連結**庫：** 無  
**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [ISOSDacInterface 介面](isosdacinterface-interface.md)
