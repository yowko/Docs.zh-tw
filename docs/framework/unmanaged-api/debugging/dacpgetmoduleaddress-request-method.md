---
title: DacpGetModule 位址：請求方法
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 6850dc256a70e0c0343104b3904e9eda62d11e7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179204"
---
# <a name="dacpgetmoduleaddressrequest-method"></a>DacpGetModule 位址：請求方法

執行請求，從給定的運行時結構填充結構。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a>參數

`pDataModule`\
[在]指向種子資料模組的指標。

## <a name="remarks"></a>備註

此結構位於運行時內，不會通過任何標頭或庫檔公開。 要使用它，最簡單的方法是類比實現：

- 使用以下參數返回從調用`Request``IXCLRDataModule*`參數上的方法獲得的值：`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標題：** 無**庫：** 無  
**.NET 框架版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [達格格獲取模組位址介面](dacpgetmoduleaddress-structure.md)
