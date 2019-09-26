---
title: CorDebugBlockingObject 結構
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57de11c1c40c05befcf3c99c31c2e07e1ecaec5a
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273962"
---
# <a name="cordebugblockingobject-structure"></a>CorDebugBlockingObject 結構
定義封鎖執行緒的物件，以及執行緒遭到封鎖的特定原因。  
  
## <a name="syntax"></a>語法  
  
```cpp  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`pBlockingObject`|執行緒封鎖所在的物件。 這個物件只在目前已同步處理狀態的持續時間內有效。 如果兩個執行緒在相同物件的已同步處理狀態下封鎖，您可能會預期[ICorDebugValue：： GetAddress](icordebugvalue-getaddress-method.md)方法傳回相同的值。 不過，介面不一定是對等的指標。|  
|`dwTimeout`|封鎖作業超時前的毫秒數，或無限值，表示不會超時。超時值會指定封鎖作業的總時間長度，而不是仍然剩餘的時間。|  
|`blockingReason`|此物件上封鎖執行緒的原因。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
