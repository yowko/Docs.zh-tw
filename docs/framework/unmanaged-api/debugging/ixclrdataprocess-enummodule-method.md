---
title: IXCLRDataProcess::EnumModule 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumModule Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumModule Method
helpviewer.keywords:
- IXCLRDataProcess::EnumModule Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: fa1e41985444324627c6b66a109b4619d85fc57f
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416458"
---
# <a name="ixclrdataprocessenummodule-method"></a>IXCLRDataProcess::EnumModule 方法

列舉此程序的模組。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

### <a name="parameters"></a>參數

`handle` [in、 out]列舉模組控制代碼。

`mod` [out]列舉的模組中。

## <a name="remarks"></a>備註

提供的方法是一部分`IXCLRDataProcess`介面，並對應至的虛擬方法表 25 的位置。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** 無  
**程式庫：** 無  
**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [CLRDataSourceType 列舉](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [IXCLRDataModule 介面](../../../../docs/framework/unmanaged-api/debugging/ixclrdatamodule-interface.md)
- [IXCLRDataProcess 介面](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
