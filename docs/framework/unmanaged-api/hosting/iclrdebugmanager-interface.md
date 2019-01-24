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
ms.openlocfilehash: 515eb0633c82c3e1386487d1866de79c9898c9cd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654603"
---
# <a name="iclrdebugmanager-interface"></a>ICLRDebugManager 介面
提供方法，可讓主應用程式相關聯的一組工作識別碼和易記名稱。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginConnection 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|建立主應用程式與偵錯工具，將關聯工作識別碼和易記名稱之間的新連線。|  
|[EndConnection 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|移除工作清單和識別項和易記名稱之間的關聯。|  
|[GetDacl 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|這個方法尚未實作。|  
|[IsDebuggerAttached 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|取得值，表示偵錯工具是否附加至處理序。|  
|[SetConnectionTasks 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|將一份[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)識別碼和易記名稱的執行個體。|  
|[SetDacl 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|這個方法尚未實作。|  
|[SetSymbolReadingPolicy 方法](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|設定用於讀取程式資料庫 (PDB) 檔案的原則。 原則會決定是否在呼叫堆疊中包含行號和檔案的相關資訊。|  
  
## <a name="remarks"></a>備註  
 在偵錯案例中，主機可能會想要根據自己的程式設計邏輯的群組工作。 例如，群組可讓開發人員若要查看只將開發人員的 Api，而不是看到處理序中執行的每項工作所需的工作。 `ICLRDebugManager` 可讓主應用程式實作此類型的群組。  
  
> [!IMPORTANT]
>  三個`ICLRDebugManager`方法， `BeginConnection`，`SetConnectionTasks`和`EndConnection`，依存於彼此。 在指定的順序，如預期般運作，必須呼叫它們。  
  
 群組，以及識別碼和主應用程式會將指派給群組的易記名稱已對 common language runtime (CLR) 而言沒有意義。 只是，CLR 會將資訊傳遞給偵錯工具。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
