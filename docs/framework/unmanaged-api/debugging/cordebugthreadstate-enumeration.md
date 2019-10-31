---
title: CorDebugThreadState 列舉
ms.date: 03/30/2017
api_name:
- CorDebugThreadState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugThreadState
helpviewer_keywords:
- CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type:
- apiref
ms.openlocfilehash: 1ff36e8ef6b7c02eea5b02bc22587bc3889df093
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133697"
---
# <a name="cordebugthreadstate-enumeration"></a>CorDebugThreadState 列舉
指定要偵錯的執行緒狀態。  
  
## <a name="syntax"></a>語法  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a>Members  
  
|成員|描述|  
|------------|-----------------|  
|`THREAD_RUN`|除非發生 debug 事件，否則執行緒會自由執行。|  
|`THREAD_SUSPEND`|無法執行執行緒。|  
  
## <a name="remarks"></a>備註  
 偵錯工具會使用 `CorDebugThreadState` 列舉來控制執行緒的執行。 您可以使用[ICorDebugThread：： SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)或[ICorDebugController：： SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)方法來設定執行緒的狀態。  
  
 提供給[裝載 API](../../../../docs/framework/unmanaged-api/hosting/index.md)的回呼可啟用訊息提取，因此不需要中斷的狀態。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
