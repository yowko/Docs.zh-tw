---
title: IXCLRDataModule::GetMethodDefinitionByToken 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetMethodDefinitionByToken Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method
helpviewer.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 2c0cf56f108396226b7c7399f6da75e5f47d36f3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744678"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a>IXCLRDataModule::GetMethodDefinitionByToken 方法

取得對應至指定的中繼資料語彙基元的方法定義。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a>參數

`token`\
[in]方法的語彙基元。

`methodDefinition`\
[out]方法定義。

## <a name="remarks"></a>備註

提供的方法是一部分`IXCLRDataModule`介面，並對應至的虛擬方法表 25 的位置。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** None  
**LIBRARY:** None  
**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  
 
## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [IXCLRDataModule 介面](ixclrdatamodule-interface.md)
