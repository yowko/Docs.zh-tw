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
ms.openlocfilehash: ea54fdd83b9470db4a08daceaa695e450f5ca1af
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764818"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a>ISOSDacInterface::GetMethodDescData 方法

取得指定 MethodDesc 指標的資料。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```cpp
HRESULT GetMethodDescData(
    CLRDATA_ADDRESS            methodDesc,
    CLRDATA_ADDRESS            ip,
    DacpMethodDescData *data,
    ULONG                      cRevertedRejitVersions,
    DacpReJitData      *rgRevertedRejitData,
    void                      *pcNeededRevertedRejitData
);
```

## <a name="parameters"></a>參數

`methodDesc`\
[in]MethodDesc 位址。

`ip`\
[in]方法的 IP 位址。

`data`\
[out]傳回從內部 Api，與 MethodDesc 相關的資料。

`cRevertedRejitVersions`\
[out]已還原的 rejit 版本數目。

`rgRevertedRejitData`\
[out]傳回的內部 Api，以還原的 rejit 版本相關聯的資料。

`pcNeededRevertedRejitData`\
[out]儲存與還原的 ReJit 版本相關聯的資料所需的位元組數目。

## <a name="remarks"></a>備註

提供的方法是一部分`ISOSDacInterface`介面，並對應至 20 虛擬方法表的位置。 若要能夠使用它們[ `CLRDATA_ADDRESS` ](../common-data-types-unmanaged-api-reference.md)必須定義為 64 位元不帶正負號的整數。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** 無  
**LIBRARY:** None  
**.NET framework 版本：** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [ISOSDacInterface 介面](isosdacinterface-interface.md)
