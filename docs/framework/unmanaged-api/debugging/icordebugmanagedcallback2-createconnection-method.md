---
title: ICorDebugManagedCallback2::CreateConnection 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10d0fc0c65d6c479ee4bf7bf527ee33615d53084
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761174"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a>ICorDebugManagedCallback2::CreateConnection 方法
告知偵錯工具已建立的新的連線。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a>參數  
 `pProcess`  
 [in]代表程序的連接原先建立"ICorDebugProcess 」 物件的指標  
  
 `dwConnectionId`  
 [in]新的連接識別碼。  
  
 `pConnName`  
 [in]新的連接名稱指標。  
  
## <a name="remarks"></a>備註  
 A`CreateConnection`回呼會在下列情況下引發：  
  
- 當偵錯工具附加至包含連線的處理序。 在此情況下，執行階段會產生，並分派`CreateConnection`事件和[ICorDebugManagedCallback2::ChangeConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)程序中每個連接的事件。  
  
- 當主機呼叫[iclrdebugmanager:: Beginconnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)中[裝載 API](../../../../docs/framework/unmanaged-api/hosting/index.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugManagedCallback2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
