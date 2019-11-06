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
ms.openlocfilehash: 239e3a82df0e6010278669f9f429bfad0d163319
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133716"
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

## <a name="members"></a>Members

| 成員            | 描述                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | 處理序透過向前執行已達到新的記憶體狀態。            |
| `FLUSH_ALL`       | 指定的處理序記憶體可能與先前的記憶體不同。 |

## <a name="remarks"></a>備註

 當偵錯工具以[ICorDebugProcess4：:P rocessstatechanged](icordebugprocess4-processstatechanged-method.md)或[ICorDebugProcess6：:P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)呼叫 `ProcessStateChanged` 方法時，會提供 `CorDebugStateChange` 列舉的成員做為引數。

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

 **標頭：** CorDebug.idl、CorDebug.h

 **程式庫：** CorGuids.lib

 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>請參閱

- [偵錯列舉](debugging-enumerations.md)
- [偵錯](index.md)
