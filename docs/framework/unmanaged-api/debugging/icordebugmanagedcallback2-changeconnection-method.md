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
ms.openlocfilehash: 4ba04b1a4815587b40d03819fdac795dcc7f2c4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697268"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>ICorDebugManagedCallback2::ChangeConnection 方法

通知偵錯工具，與指定之連接相關聯的工作集已變更。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a>參數  

 `pProcess`  
 在"ICorDebugProcess" 物件的指標，代表包含變更之連接的進程。  
  
 `dwConnectionId`  
 在變更之連接的識別碼。  
  
## <a name="remarks"></a>備註  

 `ChangeConnection`回呼將會在下列其中一個情況下引發：  
  
- 當偵錯工具附加至包含連接的進程時。 在此情況下，執行時間會為進程中的每個連接產生並分派 [ICorDebugManagedCallback2：： CreateConnection](icordebugmanagedcallback2-createconnection-method.md) 事件和 `ChangeConnection` 事件。 `ChangeConnection`每個現有的連接都會產生一個事件，不論連接的工作集自從建立之後是否已變更。  
  
- 當主機在[裝載 API](../hosting/index.md)中呼叫[ICLRDebugManager：： SetConnectionTasks](../hosting/iclrdebugmanager-setconnectiontasks-method.md)時。  
  
 偵錯工具應該掃描進程中的所有線程，以挑選新的變更。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** CorDebug.idl、CorDebug.h  
  
 **程式庫：** CorGuids.lib  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICorDebugManagedCallback2 介面](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback 介面](icordebugmanagedcallback-interface.md)
