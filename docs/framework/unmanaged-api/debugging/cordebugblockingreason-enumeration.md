---
title: "CorDebugBlockingReason 列舉"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugBlockingReason
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugBlockingReason
helpviewer_keywords: CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 84c09de4e0ce6e436c2c814c4cd9990db012d422
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugblockingreason-enumeration"></a>CorDebugBlockingReason 列舉
指定給定物件上封鎖執行緒的原因。  
  
## <a name="syntax"></a>語法  
  
```  
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
|`BLOCKING_MONITOR_CRITICAL_SECTION`|執行緒嘗試取得監視器鎖定物件相關聯的重要區段。 通常，發生這種情況時您呼叫其中一個<xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>或<xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>方法。|  
|`BLOCKING_MONITOR_EVENT`|執行緒正在等候物件監視器鎖定相關聯的事件。 通常，發生這種情況時您呼叫其中一個<xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait`方法。|  
  
## <a name="remarks"></a>備註  
 當`BLOCKING_MONITOR_CRITICAL_SECTION`或`BLOCKING_MONITOR_EVENT`成員用於[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)結構`pBlockingObject`"ICorDebugValue 」 介面，表示正在輸入的物件指向的結構的成員. 它也保證實作[ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)介面。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
