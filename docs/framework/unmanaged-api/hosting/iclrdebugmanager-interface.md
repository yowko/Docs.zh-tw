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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d123177bf9f1b5eee1a2ba4d9b7f2042ddc07aa2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434935"
---
# <a name="iclrdebugmanager-interface"></a>ICLRDebugManager 介面
提供方法，讓主應用程式能夠與識別項和好記的名稱產生關聯的一組工作。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginConnection 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|建立新的連接，主機和偵錯工具可以將工作識別碼和易記名稱與之間。|  
|[EndConnection 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|移除關聯的工作清單和識別項和好記的名稱。|  
|[GetDacl 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|這個方法尚未實作。|  
|[IsDebuggerAttached 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|取得值，表示偵錯工具是否附加至處理序。|  
|[SetConnectionTasks 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|將一份[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)識別碼和易記名稱與執行個體。|  
|[SetDacl 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|這個方法尚未實作。|  
|[SetSymbolReadingPolicy 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|設定用於讀取程式資料庫 (PDB) 檔案的原則。 原則會決定是否在呼叫堆疊中包含行號和檔案的相關資訊。|  
  
## <a name="remarks"></a>備註  
 在偵錯狀況下，主機可能會想要將工作分組根據自己的程式設計邏輯。 例如，群組可讓開發人員若要查看只將所需的開發人員的 Api，而不是查看每項工作處理序中執行的工作。 `ICLRDebugManager` 可讓主機實作此類型的群組。  
  
> [!IMPORTANT]
>  三個`ICLRDebugManager`方法`BeginConnection`，`SetConnectionTasks`和`EndConnection`，依存於彼此。 您必須呼叫指定的順序如預期般運作。  
  
 群組的識別碼和易記名稱，主機會指派給群組，沒有任何意義的 common language runtime (CLR)。 CLR 只會將資訊傳遞至偵錯工具。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
