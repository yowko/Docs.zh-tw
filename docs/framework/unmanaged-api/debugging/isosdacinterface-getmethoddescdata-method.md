---
title: ISOSDacInterface：： GetMethodDescData 方法
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
ms.openlocfilehash: e4c44379d9db0f5e98f3ca66ec0486961ec2df3a
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396951"
---
# <a name="isosdacinterfacegetmethoddescdata-method"></a>ISOSDacInterface：： GetMethodDescData 方法

取得給定 MethodDesc 指標的資料。

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
在MethodDesc 的位址。

`ip`\
在方法的 IP 位址。

`data`\
脫銷與 MethodDesc 相關聯的資料，如同從內部 Api 傳回的。

`cRevertedRejitVersions`\
脫銷已還原的 rejit 版本數目。

`rgRevertedRejitData`\
脫銷與從內部 Api 傳回的還原 rejit 版本相關聯的資料。

`pcNeededRevertedRejitData`\
脫銷儲存與已還原之 ReJit 版本相關聯之資料所需的位元組數目。

## <a name="remarks"></a>備註

提供的方法是介面的一部分 `ISOSDacInterface` ，而且會對應至虛擬方法資料表的21個位置。 若要能夠使用它們， [`CLRDATA_ADDRESS`](../common-data-types-unmanaged-api-reference.md) 必須將定義為64位不帶正負號的整數。

## <a name="requirements"></a>需求

**平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
**標頭：** 無  
連結**庫：** 無  
**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>請參閱

- [偵錯](index.md)
- [ISOSDacInterface 介面](isosdacinterface-interface.md)
