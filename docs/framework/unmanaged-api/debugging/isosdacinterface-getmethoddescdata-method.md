---
title: ISOSDacInterface::GetMethodDescData 方法
ms.date: 01/16/2019
api.name:
- ISOSDacInterface::GetMethodDescData Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescData Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescData Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e56f837c4d3362ec6e71030e4fb475df42b9fba4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639941"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a>ISOSDacInterface::GetMethodDescData 方法

取得的資料指定[MethodDesc](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    void                       *data,
    ULONG                      cRevertedRejitVersions,
    void                      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

### <a name="parameters"></a>參數

`methodDesc` [in]MethodDesc 位址。

`ip` [in]方法的 IP 位址。

`data` [out]傳回從內部 Api，與 MethodDesc 相關的資料。 結構必須至少 168 個位元組。

`cRevertedRejitVersions` [out]已還原的 rejit 版本數目。

`rgRevertedRejitData` [out]傳回的內部 Api，以還原的 rejit 版本相關聯的資料。 結構必須至少在 24 個位元組。

`pcNeededRevertedRejitData` [out]儲存與還原的 ReJit 版本相關聯的資料所需的位元組數目。

## <a name="remarks"></a>備註

提供的方法是一部分`ISOSDacInterface`介面，並對應至 20 虛擬方法表的位置。 也`CLRDATA_ADDRESS`為 64 位元不帶正負號的整數。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** 無  
**程式庫：** 無  
**.NET framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [ISOSDacInterface 介面](../../../../docs/framework/unmanaged-api/debugging/isosdacinterface-interface.md)
