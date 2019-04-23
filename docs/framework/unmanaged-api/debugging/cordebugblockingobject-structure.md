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
ms.openlocfilehash: 12a114ea65aca544d653704cdfb01ed15d19c581
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143217"
---
# <a name="cordebugblockingobject-structure"></a>CorDebugBlockingObject 結構
定義封鎖執行緒和執行緒已封鎖的特定原因的物件。  
  
## <a name="syntax"></a>語法  
  
```  
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
|`pBlockingObject`|物件，在其封鎖執行緒。 這個物件是有效的只會針對目前的同步處理狀態的持續時間。 如果兩個執行緒會封鎖相同的同步處理狀態中的相同物件上，您可能會預期[icordebugvalue:: Getaddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)方法來傳回相同的值。 不過，介面可能會或可能不到對等的指標。|  
|`dwTimeout`|逾時或值為 INFINITE，這表示它將會逾時，將會封鎖作業之前的毫秒數。逾時值指定時間的封鎖作業，也就是不是仍剩餘的時間總長度。|  
|`blockingReason`|執行緒已封鎖此物件上的原因。|  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯結構](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [偵錯](../../../../docs/framework/unmanaged-api/debugging/index.md)
