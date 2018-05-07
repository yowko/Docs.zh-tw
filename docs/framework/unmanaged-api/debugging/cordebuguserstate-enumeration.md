---
title: CorDebugUserState 列舉
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f489ab29726292f6c55151169ad9efc6f0fbfbcf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cordebuguserstate-enumeration"></a>CorDebugUserState 列舉
指出執行緒的使用者狀態。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a>成員  
  
|值|描述|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|已要求終止執行緒。|  
|`USER_SUSPEND_REQUESTED`|已要求暫止執行緒。|  
|`USER_BACKGROUND`|執行緒在背景中執行。|  
|`USER_UNSTARTED`|執行緒尚未啟動執行。|  
|`USER_STOPPED`|執行緒已經終止。|  
|`USER_WAIT_SLEEP_JOIN`|執行緒正在等候另一個執行緒完成工作。|  
|`USER_SUSPENDED`|執行緒已經暫止。|  
|`USER_UNSAFE_POINT`|執行緒是不安全的點。 也就是的執行緒已在執行中的點，它可能會封鎖記憶體回收。<br /><br /> 偵錯事件可能會分派從 unsafe 點，但在不安全點暫停執行緒極可能會造成死結執行緒繼續執行之前。 安全和不安全的點是由在 just-in-time (JIT) 和記憶體回收集合實作決定。|  
|`USER_THREADPOOL`|執行緒是從執行緒集區。|  
  
## <a name="remarks"></a>備註  
 使用者狀態是執行緒的執行緒時偵錯工具會檢查它所擁有的狀態。 執行緒可能會有使用者狀態的組合。  
  
 使用[icordebugthread:: Getuserstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md)方法來擷取執行緒的使用者狀態。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
