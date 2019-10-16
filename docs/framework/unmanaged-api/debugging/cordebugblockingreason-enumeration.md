---
title: CorDebugBlockingReason 列舉
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99fcf160b3e3b2b238520e3db5ba2e74b270380a
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274135"
---
# <a name="cordebugblockingreason-enumeration"></a>CorDebugBlockingReason 列舉
指定給定物件上封鎖執行緒的原因。  
  
## <a name="syntax"></a>語法  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`BLOCKING_NONE`|僅供內部使用。|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|執行緒正在嘗試取得與物件上的監視器鎖定相關聯的重要區段。 一般而言，當您呼叫其中一個<xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>或<xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>方法時，就會發生這種情況。|  
|`BLOCKING_MONITOR_EVENT`|執行緒正在等候與物件的監視器鎖定相關聯的事件。 一般而言，當您呼叫其中一個<xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait`方法時，就會發生這種情況。|  
  
## <a name="remarks"></a>備註  
 `pBlockingObject`當或成員`BLOCKING_MONITOR_EVENT`用於 [CorDebugBlockingObject](cordebugblockingobject-structure.md) 結構時，結構的成員會指向代表所輸入之物件的 "ICorDebugValue" 介面。`BLOCKING_MONITOR_CRITICAL_SECTION` 它也保證會執行[ICorDebugHeapValue3](icordebugheapvalue3-interface.md)介面。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯列舉](debugging-enumerations.md)
- [偵錯](index.md)
