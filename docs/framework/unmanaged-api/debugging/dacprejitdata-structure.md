---
title: DacpReJitData Structure
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 4436ece72b0a6a405fc41cba5413093fc42ce750
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860774"
---
# <a name="dacprejitdata-structure"></a>DacpReJitData Structure

定義指定之分析工具檢測方法的基本資訊。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>語法

```cpp
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a>成員

| member           | 描述                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | 方法的 ReJit 修訂編號。                                                          |
| `flags`          | 旗標，指出方法的 ReJit 檢測在指定版本中的目前狀態。 |
| `NativeCodeAddr` | 方法的 rejitted 實址的基底位址。                                         |

## <a name="remarks"></a>備註

這個結構存在於執行時間中，而且不會透過任何標頭或程式庫檔案來公開。 若要使用它，請依照上面的指定定義結構。 如果未使用 Microsoft 編譯器，則`ms_struct`也必須使用封裝來定義結構。

## <a name="requirements"></a>需求
**平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
**標頭：** 無  
連結**庫：** 無  
**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>請參閱

- [偵錯](index.md)
- [偵錯結構](debugging-structures.md)
