---
title: DacpGetModuleAddress::要求方法
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
ms.openlocfilehash: 1755526636bed6d78663112e4c2ad5ab7c3f731c
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860847"
---
# <a name="dacpgetmoduleaddressrequest-method"></a>DacpGetModuleAddress::要求方法

執行要求，以從指定的執行時間結構填入結構。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a>參數

`pDataModule`\
在種子資料模組的指標。

## <a name="remarks"></a>備註

這個結構存在於執行時間中，而且不會透過任何標頭或程式庫檔案來公開。 若要使用它，最簡單的方法是模擬此實作為：

- 使用下列參數，傳回從呼叫`Request` `IXCLRDataModule*`參數上的方法取得的值：`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`

## <a name="requirements"></a>需求

**平臺：** 請參閱[系統需求](../../get-started/system-requirements.md)\
**標頭：** 無
連結**庫：** 無
**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>請參閱

- [偵錯](index.md)
- [DacpGetModuleAddress 結構](dacpgetmoduleaddress-structure.md)
