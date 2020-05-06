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
ms.openlocfilehash: e460264e2393858c028ba51aec4a4f2c01649994
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860834"
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

這個結構存在於執行時間中，而且不會透過任何標頭或程式庫檔案來公開。 若要使用它，請定義如上所指定的結構`CLRDATA_ADDRESS` ，其中是64位不帶正負號的整數。

## <a name="requirements"></a>需求
**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
**標頭：** 無  
連結**庫：** 無  
**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>請參閱

- [偵錯](index.md)
- [偵錯結構](debugging-structures.md)
