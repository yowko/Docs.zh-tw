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
ms.openlocfilehash: 3836bd349423670a19a19dda67eba75419507a29
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724282"
---
# <a name="iclrdebugmanager-interface"></a>ICLRDebugManager 介面

提供可讓主機將一組工作與識別碼和易記名稱產生關聯的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginConnection 方法](iclrdebugmanager-beginconnection-method.md)|在主機和偵錯工具之間建立新的連接，以將工作與識別碼和易記名稱產生關聯。|  
|[EndConnection 方法](iclrdebugmanager-endconnection-method.md)|移除工作清單與識別碼和易記名稱之間的關聯。|  
|[GetDacl 方法](iclrdebugmanager-getdacl-method.md)|這個方法尚未實作。|  
|[IsDebuggerAttached 方法](iclrdebugmanager-isdebuggerattached-method.md)|取得值，表示偵錯工具是否附加至處理序。|  
|[SetConnectionTasks 方法](iclrdebugmanager-setconnectiontasks-method.md)|將 [ICLRTask](iclrtask-interface.md) 實例清單與識別碼和易記名稱產生關聯。|  
|[SetDacl 方法](iclrdebugmanager-setdacl-method.md)|這個方法尚未實作。|  
|[SetSymbolReadingPolicy 方法](iclrdebugmanager-setsymbolreadingpolicy-method.md)|設定用來讀取程式資料庫 (PDB) 檔的原則。 此原則會決定行號和檔案的相關資訊是否包含在呼叫堆疊中。|  
  
## <a name="remarks"></a>備註  

 在偵錯工具案例中，主機可能會想要根據自己的程式設計邏輯將工作分組。 例如，群組可讓開發人員只查看開發人員 Api 所需的工作，而不是看到在進程中執行的每項工作。 `ICLRDebugManager` 允許主機執行這種群組。  
  
> [!IMPORTANT]
> 三個 `ICLRDebugManager` 方法 `BeginConnection` （ `SetConnectionTasks` 和 `EndConnection` ）彼此相依。 您必須以指定的順序呼叫它們，才能如預期般運作。  
  
 群組，以及主機指派給群組的識別碼和易記名稱，對 common language runtime (CLR) 沒有任何意義。 CLR 只會將資訊傳送至偵錯工具。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](hosting-interfaces.md)
