---
title: DacpGetModuleAddress::Request Method
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
ms.openlocfilehash: 298620092c37b2c02332e9135f73584272e326bd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111679"
---
# <a name="dacpgetmoduleaddressrequest-method"></a>DacpGetModuleAddress::Request Method

會執行要求，以填入指定的執行階段結構中的結構。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a>參數

`pDataModule`\
[in]種子資料模組指標。

## <a name="remarks"></a>備註

此結構內執行階段，而且不會公開透過任何標頭或程式庫檔案。 若要使用它，最簡單的方法是模擬的實作：

- 傳回從呼叫取得的值`Request`方法`IXCLRDataModule*`參數搭配下列參數： `((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** None     
**LIBRARY:** None  
**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [DacpGetModuleAddress Interface](dacpgetmoduleaddress-structure.md)