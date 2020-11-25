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
ms.openlocfilehash: 46708acc77dad00727ee35e7d06e4228eacbd502
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723034"
---
# <a name="dacprejitdata-structure"></a>DacpReJitData Structure

定義指定分析工具檢測方法的基本資訊。

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
| `flags`          | 旗標，表示指定版本之方法 ReJit 檢測的目前狀態。 |
| `NativeCodeAddr` | 方法的 rejitted 實址的基底位址。                                         |

## <a name="remarks"></a>備註

此結構存在於執行時間內，且不會透過任何標頭或程式庫檔案來公開。 若要使用它，請依照上述指定的方式定義結構。 如果不使用 Microsoft 編譯器，也必須使用封裝來定義結構 `ms_struct` 。

## <a name="requirements"></a>需求

**平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
**標頭：** 沒有  
連結 **庫：** 沒有  
**.NET Framework 版本：**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>另請參閱

- [偵錯](index.md)
- [偵錯結構](debugging-structures.md)
