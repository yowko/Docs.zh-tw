---
title: IXCLRDataProcess::EnumMethodInstanceByAddress 方法
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 825cb8ea94bee980f9e10b90cddf04db32c1a33f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491905"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a>IXCLRDataProcess::EnumMethodInstanceByAddress 方法

列舉位址位移處開始此程序的方法執行的個體。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

### <a name="parameters"></a>參數

`handle` [in]列舉的方法執行個體控制代碼。

`mod` [out]列舉的方法執行個體。

## <a name="remarks"></a>備註

提供的方法是一部分`IXCLRDataProcess`介面，而對應的虛擬方法表的第 28 插槽。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。   
**標頭：** 無   
**程式庫：** 無   
**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]   
 
## <a name="see-also"></a>另請參閱
- [CLRDataSourceType 列舉](../../../../docs/framework/unmanaged-api/debugging/clrdatasourcetype-enumeration.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [IXCLRDataProcess 介面](../../../../docs/framework/unmanaged-api/debugging/ixclrdataprocess-interface.md)
