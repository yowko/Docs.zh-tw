---
title: ICLRDebugManager 介面
ms.date: 03/30/2017
api_name:
- ICLRDebugManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager
helpviewer_keywords:
- ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type:
- apiref
ms.openlocfilehash: 008143c608cd19bee9dd115e97620906fb5b93b9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129399"
---
# <a name="iclrdebugmanager-interface"></a>ICLRDebugManager 介面
提供可讓主機將一組工作與識別碼和易記名稱建立關聯的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginConnection 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|在主機與偵錯工具之間建立新的連接，以將工作與識別碼和易記名稱產生關聯。|  
|[EndConnection 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|移除工作清單與識別碼和易記名稱之間的關聯。|  
|[GetDacl 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|這個方法尚未實作。|  
|[IsDebuggerAttached 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|取得值，表示偵錯工具是否附加至處理序。|  
|[SetConnectionTasks 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|將[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)實例的清單與識別碼和易記名稱產生關聯。|  
|[SetDacl 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|這個方法尚未實作。|  
|[SetSymbolReadingPolicy 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|設定用於讀取程式資料庫（PDB）檔案的原則。 此原則會決定行號和檔案的相關資訊是否包含在呼叫堆疊中。|  
  
## <a name="remarks"></a>備註  
 在偵錯工具案例中，主機可能會想要根據工作的程式設計邏輯來分組工作。 例如，群組可讓開發人員只查看開發人員的 Api 所需的工作，而不會看到在進程中執行的每個工作。 `ICLRDebugManager` 允許主機執行這種群組。  
  
> [!IMPORTANT]
> 三個 `ICLRDebugManager` 方法 `BeginConnection`、`SetConnectionTasks` 和 `EndConnection`彼此相依。 您必須在指定的順序中呼叫它們，才能如預期般運作。  
  
 群組以及主機指派給群組的識別碼和易記名稱，對 common language runtime （CLR）沒有任何意義。 CLR 只會將資訊傳遞給偵錯工具。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
