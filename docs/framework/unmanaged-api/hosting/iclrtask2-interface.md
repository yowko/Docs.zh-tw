---
title: ICLRTask2 介面
ms.date: 03/30/2017
api_name:
- ICLRTask2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2
helpviewer_keywords:
- ICLRTask2 interface [.NET Framework hosting]
ms.assetid: b5a22ebc-0582-49de-91f9-97a3d9789290
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed0d2ff3b64bab026087e13d54314eca86181d8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438804"
---
# <a name="iclrtask2-interface"></a>ICLRTask2 介面
提供的所有功能[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)介面; 此外，都提供方法，讓執行緒中止目前的執行緒上延遲。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginPreventAsyncAbort 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|延遲新執行緒中止目前的執行緒上的要求。|  
|[EndPreventAsyncAbort 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|可讓新的或暫止的執行緒中止要求，以產生的執行緒會中止目前的執行緒上。|  
  
## <a name="remarks"></a>備註  
 `ICLRTask2`介面繼承`ICLRTask`介面，並加入方法，可讓主應用程式延遲執行緒中止，若要保護的程式碼必須通過的區域。 呼叫`BeginPreventAsyncAbort`遞增延遲執行緒中止計數器目前的執行緒和呼叫`EndPreventAsyncAbort`遞減它。 呼叫`BeginPreventAsyncAbort`和`EndPreventAsyncAbort`可以巢狀。 只要計數器是小於或等於零，執行緒中止目前的執行緒會延遲。  
  
 如果呼叫`BeginPreventAsyncAbort`和`EndPreventAsyncAbort`會不成對的便可達到在哪一個執行緒中止無法傳遞至目前執行緒的狀態。  
  
 中止本身的執行緒不是接受的延遲。  
  
 這項功能所公開的功能是由虛擬機器 (VM) 內部使用。 不當使用這些方法可能導致 VM 未指定的行為。 例如，呼叫`EndPreventAsyncAbort`情況下先呼叫`BeginPreventAsyncAbort`VM 之前會遞增它時，無法設定計數器為零。 同樣地，內部計數器不會檢查溢位。 如果它超過其整數類資料的限制，因為主機和 VM，就會遞增，結果行為是未指定。  
  
 從繼承成員的相關資訊`ICLRTask`和此介面的其他用途，請參閱[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)介面。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
