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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ba8bca6d14308284c869b923853f7e27e045bca5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402935"
---
# <a name="cordebugthreadstate-enumeration"></a>CorDebugThreadState 列舉
指定要偵錯的執行緒狀態。  
  
## <a name="syntax"></a>語法  
  
```  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a>成員  
  
|成員|描述|  
|------------|-----------------|  
|`THREAD_RUN`|執行緒會執行自由，除非偵錯事件，就會發生。|  
|`THREAD_SUSPEND`|無法執行執行緒。|  
  
## <a name="remarks"></a>備註  
 偵錯工具會使用`CorDebugThreadState`列舉型別來控制執行緒的執行。 執行緒的狀態可以透過設定[icordebugthread:: Setdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md)或[icordebugcontroller:: Setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)方法。  
  
 提供給回呼[裝載 API](../../../../docs/framework/unmanaged-api/hosting/index.md)啟用訊息幫浦，因此不需要中斷的狀態。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、 CorDegug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [偵錯列舉](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
