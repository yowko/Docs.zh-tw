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
ms.openlocfilehash: ddd03d70656ad52fd9d577beedc60b51c7b305d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95672847"
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
  
|member|描述|  
|------------|-----------------|  
|`BLOCKING_NONE`|僅供內部使用。|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|執行緒正在嘗試取得與物件上的監視器鎖定相關聯的重要區段。 一般來說，當您呼叫其中一個或方法時，就會發生這種情況 <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> 。|  
|`BLOCKING_MONITOR_EVENT`|執行緒正在等候與物件的監視器鎖定相關聯的事件。 一般來說，當您呼叫其中一個方法時，就會發生這種情況 <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` 。|  
  
## <a name="remarks"></a>備註  

 在 `BLOCKING_MONITOR_CRITICAL_SECTION` `BLOCKING_MONITOR_EVENT` [CorDebugBlockingObject](cordebugblockingobject-structure.md) 結構中使用或成員時， `pBlockingObject` 結構的成員會指向 "ICorDebugValue" 介面，此介面表示所要輸入的物件。 也保證會執行 [ICorDebugHeapValue3](icordebugheapvalue3-interface.md) 介面。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯列舉](debugging-enumerations.md)
- [偵錯](index.md)
