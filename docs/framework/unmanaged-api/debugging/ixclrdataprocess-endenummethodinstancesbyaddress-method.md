---
title: IXCLRDataProcess::EndEnumMethodInstancesByAddress 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 378095aa2b363f4003a5372b4158df27412655e1
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757849"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a>IXCLRDataProcess::EndEnumMethodInstancesByAddress 方法

釋放執行個體列舉期間使用的內部迭代器所使用的資源。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a>參數

`handle`\
[out]列舉的方法執行個體控制代碼。

## <a name="remarks"></a>備註

提供的方法是一部分`IXCLRDataProcess`介面，並對應到第 29 虛擬方法表的位置。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** 無  
**LIBRARY:** None  
**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [CLRDataSourceType 列舉](clrdatasourcetype-enumeration.md)
- [偵錯](index.md)
- [IXCLRDataProcess 介面](ixclrdataprocess-interface.md)
