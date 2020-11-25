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
ms.openlocfilehash: b16feb1af0d4975411876e78940d21096750d2ae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726581"
---
# <a name="cordebugblockingobject-structure"></a>CorDebugBlockingObject 結構

定義封鎖執行緒的物件，以及封鎖執行緒的特定原因。  
  
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
  
|member|描述|  
|------------|-----------------|  
|`pBlockingObject`|執行緒封鎖所在的物件。 只有在目前已同步處理狀態的持續時間內，此物件才有效。 如果兩個執行緒在相同物件的相同同步處理狀態中封鎖，您可能會預期 [ICorDebugValue：： GetAddress](icordebugvalue-getaddress-method.md) 方法會傳回相同的值。 不過，介面可能會或可能不是指標相等。|  
|`dwTimeout`|封鎖作業超時之前的毫秒數，或值無限，表示不會超時。超時值指定封鎖作業的總時間長度，而不是剩餘的時間。|  
|`blockingReason`|此物件封鎖執行緒的原因。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Cordebug.h .idl  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](debugging-structures.md)
- [偵錯](index.md)
