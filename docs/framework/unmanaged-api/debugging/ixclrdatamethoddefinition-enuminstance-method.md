---
title: IXCLRDataMethodDefinition：： EnumInstance 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EnumInstance Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: b6393d7fa4853c230203521e665bbe89d7b228e2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790435"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a>IXCLRDataMethodDefinition：： EnumInstance 方法

列舉這個方法定義的實例。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a>參數

`handle`\
[in、out]列舉實例的控制碼。

`instance`\
脫銷列舉的實例。

## <a name="remarks"></a>備註

提供的方法是 `IXCLRDataMethodDefinition` 介面的一部分，而且會對應至虛擬方法資料表的第四個插槽。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** 無  
連結**庫：** 無  
**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>請參閱

- [CLRDataSourceType 列舉](clrdatasourcetype-enumeration.md)
- [偵錯](index.md)
- [IXCLRDataMethodDefinition 介面](ixclrdatamethoddefinition-interface.md)
- [IXCLRDataMethodInstance 介面](ixclrdatamethodinstance-interface.md)
