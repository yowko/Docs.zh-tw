---
title: ICorDebugManagedCallback2::ChangeConnection 方法
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8a8f84d3dfd8f1e64197078d7e20d2aebef2323
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2019
ms.locfileid: "67761219"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>ICorDebugManagedCallback2::ChangeConnection 方法
告知偵錯工具與指定的連接相關聯的工作集合已變更。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a>參數  
 `pProcess`  
 [in]代表包含已變更的連接程序 」 ICorDebugProcess 」 物件的指標。  
  
 `dwConnectionId`  
 [in]變更連線的識別碼。  
  
## <a name="remarks"></a>備註  
 A`ChangeConnection`回呼會在下列情況下引發：  
  
- 當偵錯工具附加至包含連線的處理序。 在此情況下，執行階段會產生，並分派[ICorDebugManagedCallback2::CreateConnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)事件和`ChangeConnection`程序中每個連接的事件。 A`ChangeConnection`的每個現有的連接，不論是否已變更該連接的一組工作自建立後會產生事件。  
  
- 當主機呼叫[iclrdebugmanager:: Setconnectiontasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)中[裝載 API](../../../../docs/framework/unmanaged-api/hosting/index.md)。  
  
 偵錯工具應掃描中取得最新變更的程序中的所有執行緒。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **LIBRARY:** CorGuids.lib  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugManagedCallback2 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback 介面](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
