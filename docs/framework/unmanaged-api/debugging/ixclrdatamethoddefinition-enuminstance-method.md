---
title: IXCLRDataMethodDefinition::EnumInstance 方法
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
ms.openlocfilehash: 7ad1a9957e9bffd7b28aa241723dedba1d11f4cd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775877"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a>IXCLRDataMethodDefinition::EnumInstance 方法

列舉的執行個體，這個方法定義。

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
[in、 out]列舉的執行個體控制代碼。

`instance`\
[out]列舉的執行個體。

## <a name="remarks"></a>備註

提供的方法是一部分`IXCLRDataMethodDefinition`介面，而對應的虛擬方法表的第四個插槽。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** 無  
**LIBRARY:** None  
**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [CLRDataSourceType 列舉](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [IXCLRDataMethodDefinition 介面](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethoddefinition-interface.md)
- [IXCLRDataMethodInstance 介面](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamethodinstance-interface.md)
