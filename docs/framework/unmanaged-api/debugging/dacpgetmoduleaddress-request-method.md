---
title: DacpGetModule 位址:請求方法
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
ms.openlocfilehash: 4dbe6a2c295e5afae1b6761f0c7b695fdb906428
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102903"
---
# <a name="dacpgetmoduleaddressrequest-method"></a>DacpGetModule 位址:請求方法

執行請求,從給定的運行時結構填充結構。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a>參數

`pDataModule`\
[在]指向種子數據模組的指標。

## <a name="remarks"></a>備註

此結構位於運行時內,不會通過任何標頭或庫文件公開。 要使用它,最簡單的方法是模擬實現:

- 使用以下參數返回從呼叫`Request``IXCLRDataModule*`參數上的方法獲得的值:`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`

## <a name="requirements"></a>需求

**平臺:** 請參考[系統要求](../../../../docs/framework/get-started/system-requirements.md)\
**標題:** 無。
**庫:** 無。
**.NET 框架版本:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [DacpGetModule 位址結構](dacpgetmoduleaddress-structure.md)
