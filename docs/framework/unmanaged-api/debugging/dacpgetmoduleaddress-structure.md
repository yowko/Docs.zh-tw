---
title: DacpGetModuleAddress 結構
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress Structure
helpviewer.keywords:
- DacpGetModuleAddress Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a65fa9974165fa36e59a7fb83dca6dd902f7d8dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724390"
---
# <a name="dacpgetmoduleaddress-structure"></a>DacpGetModuleAddress 結構

定義模組位址要求的容器。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```cpp
struct DacpGetModuleAddress
{
    CLRDATA_ADDRESS ModulePtr;
};
```

## <a name="members"></a>成員

| member      | 描述                |
| ----------- | -------------------------- |
| `ModulePtr` | 模組的指標。 |

## <a name="methods"></a>方法

| 方法                                                                                               | 描述                                                                    |
| ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------ |
| [要求](dacpgetmoduleaddress-request-method.md) | 執行要求，以從指定的執行時間結構填入結構。 |

## <a name="remarks"></a>備註

此結構存在於執行時間內，且不會透過任何標頭或程式庫檔案來公開。 若要使用它，請依照上面所指定的方式定義結構，其中 `CLRDATA_ADDRESS` 是64位不帶正負號的整數。

## <a name="requirements"></a>需求

**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
**標頭：** 沒有  
連結 **庫：** 沒有  
**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [偵錯結構](debugging-structures.md)
