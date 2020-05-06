---
title: CorDebugStateChange 列舉
ms.date: 02/07/2019
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
ms.openlocfilehash: d94422d25da91cd2a6653a95cbd852c3930a151a
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795686"
---
# <a name="cordebugstatechange-enumeration"></a>CorDebugStateChange 列舉

描述依據處理序變更而必須捨棄的快取資料量。

## <a name="syntax"></a>語法

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a>成員

| member            | 說明                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | 處理序透過向前執行已達到新的記憶體狀態。            |
| `FLUSH_ALL`       | 指定的處理序記憶體可能與先前的記憶體不同。 |

## <a name="remarks"></a>備註

 當偵錯工具以`CorDebugStateChange` `ProcessStateChanged` [ICorDebugProcess4：:P rocessStateChanged](icordebugprocess4-processstatechanged-method.md)或[ICorDebugProcess6：:P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)呼叫方法時，會將列舉的成員當做引數提供。

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。

 **標頭：** CorDebug.idl、CorDebug.h

 **程式庫：** CorGuids.lib

 **.NET Framework 版本：**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>請參閱

- [偵錯列舉](debugging-enumerations.md)
- [偵錯](index.md)
