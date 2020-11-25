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
ms.openlocfilehash: 968874a46279b7eac651d45c3890429a326651b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726947"
---
# <a name="cordebuguserstate-enumeration"></a>CorDebugUserState 列舉

指出執行緒的使用者狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
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
|`USER_STOP_REQUESTED`|已要求執行緒終止。|  
|`USER_SUSPEND_REQUESTED`|已要求暫停執行緒。|  
|`USER_BACKGROUND`|執行緒正在背景中執行。|  
|`USER_UNSTARTED`|執行緒尚未開始執行。|  
|`USER_STOPPED`|執行緒已經結束。|  
|`USER_WAIT_SLEEP_JOIN`|執行緒正在等候另一個執行緒完成工作。|  
|`USER_SUSPENDED`|執行緒已經暫止。|  
|`USER_UNSAFE_POINT`|執行緒處於不安全的時間點。 也就是說，執行緒是在執行的某個點上，它可能會封鎖垃圾收集。<br /><br /> 偵錯工具事件可能會從不安全的點分派，但在不安全的點暫停執行緒很可能會造成鎖死，直到執行緒繼續為止。 安全且不安全的點取決於及時 (JIT) 和垃圾收集執行。|  
|`USER_THREADPOOL`|執行緒來自執行緒集區。|  
  
## <a name="remarks"></a>備註  

 執行緒的使用者狀態是偵錯工具檢查時執行緒的狀態。 執行緒可能會有使用者狀態的組合。  
  
 使用 [ICorDebugThread：： GetUserState](icordebugthread-getuserstate-method.md) 方法來取出執行緒的使用者狀態。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [偵錯列舉](debugging-enumerations.md)
