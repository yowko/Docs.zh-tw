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
ms.openlocfilehash: 2c6ed14f9238d653b15d26dec9d954c05238817c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213448"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>ICorDebugManagedCallback2::ChangeConnection 方法
通知偵錯工具與指定的連接相關聯的工作集已變更。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a>參數  
 `pProcess`  
 在"ICorDebugProcess" 物件的指標，表示包含已變更之連接的進程。  
  
 `dwConnectionId`  
 在已變更之連接的識別碼。  
  
## <a name="remarks"></a>備註  
 `ChangeConnection`在下列任一情況下，將會引發回呼：  
  
- 當偵錯工具附加至包含連接的進程時。 在此情況下，執行時間會針對進程中的每個連接產生並分派[ICorDebugManagedCallback2：： CreateConnection](icordebugmanagedcallback2-createconnection-method.md)事件和 `ChangeConnection` 事件。 `ChangeConnection`會針對每個現有的連接產生事件，而不論該連接的工作集是在建立後是否已經變更。  
  
- 當主機在[裝載 API](../hosting/index.md)中呼叫[ICLRDebugManager：： SetConnectionTasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)時。  
  
 偵錯工具應該掃描進程中的所有線程，以挑選新的變更。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICorDebugManagedCallback2 介面](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback 介面](icordebugmanagedcallback-interface.md)
