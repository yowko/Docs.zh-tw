---
title: ICorDebugManagedCallback::ExitThread 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85247f2f3672e7827f4dd0c93e50cd5da914ee8f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755772"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a>ICorDebugManagedCallback::ExitThread 方法
已結束執行緒所執行的 managed 程式碼會告知偵錯工具。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a>參數  
 `pAppDomain`  
 [in]表示包含 managed 的執行緒的應用程式網域的 ICorDebugAppDomain 物件指標。  
  
 `thread`  
 [in]ICorDebugThread 物件，表示 managed 的執行緒指標。  
  
## <a name="remarks"></a>備註  
 一次`ExitThread`引發回呼時，執行緒不會再出現在 執行緒列舉型別。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
