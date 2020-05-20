---
title: IXCLRDataMethodDefinition：： StartEnumInstances 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::StartEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: b0c37c666f23f04239ed827246b87c43ee8d5ad9
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420925"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a>IXCLRDataMethodDefinition：： StartEnumInstances 方法

提供給定的方法實例列舉的控制碼 `IXCLRDataAppDomain` 。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a>參數

`appDomain`\
在列舉的 AppDomain。

`handle`\
脫銷列舉實例的控制碼。

## <a name="remarks"></a>備註

提供的方法是介面的一部分 `IXCLRDataMethodDefinition` ，而且會對應至虛擬方法資料表的第5個位置。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
**標頭：** 無  
連結**庫：** 無  
**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [CLRDataSourceType 列舉](clrdatasourcetype-enumeration.md)
- [偵錯](index.md)
- [IXCLRDataMethodDefinition 介面](ixclrdatamethoddefinition-interface.md)
