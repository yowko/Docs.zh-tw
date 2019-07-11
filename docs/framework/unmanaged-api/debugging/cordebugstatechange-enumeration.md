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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 676489880cb30ca540cb78d70797dbf4eedf7395
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739593"
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

| 成員            | 描述                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | 處理序透過向前執行已達到新的記憶體狀態。            |
| `FLUSH_ALL`       | 指定的處理序記憶體可能與先前的記憶體不同。 |

## <a name="remarks"></a>備註

 成員`CorDebugStateChange`列舉型別提供做為引數，當偵錯工具呼叫`ProcessStateChanged`方法使用[ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md)或[ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)

## <a name="requirements"></a>需求

 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。

 **標頭：** CorDebug.idl、CorDebug.h

 **LIBRARY:** CorGuids.lib

 **.NET framework 版本：** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>另請參閱

- [偵錯列舉](debugging-enumerations.md)
- [偵錯](index.md)
