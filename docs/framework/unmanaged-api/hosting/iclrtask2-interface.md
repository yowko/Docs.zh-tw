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
ms.openlocfilehash: 8cbd627eff9318fce38ec238e5fa686cc9d759b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627183"
---
# <a name="iclrtask2-interface"></a>ICLRTask2 介面
提供的所有功能[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)介面; 此外，都提供方法，可讓執行緒中止延遲在目前的執行緒上。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginPreventAsyncAbort 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|延遲新執行緒中止目前的執行緒上的要求。|  
|[EndPreventAsyncAbort 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|可讓新的或暫止的執行緒中止要求，導致執行緒中止目前的執行緒上。|  
  
## <a name="remarks"></a>備註  
 `ICLRTask2`介面繼承`ICLRTask`介面，並將新增方法，可讓主應用程式延遲執行緒中止，以保護絕不能失敗的程式碼區域。 呼叫`BeginPreventAsyncAbort`遞增目前的執行緒，並呼叫的延遲執行緒中止計數器`EndPreventAsyncAbort`遞減它。 若要呼叫`BeginPreventAsyncAbort`和`EndPreventAsyncAbort`可以巢狀。 計數器是小於或等於零，因為目前執行緒的執行緒中止都延遲。  
  
 如果呼叫`BeginPreventAsyncAbort`和`EndPreventAsyncAbort`是未配對，就能夠達到在哪一個執行緒中止不能傳遞到目前執行緒的狀態。  
  
 中止本身的執行緒不被接受的延遲。  
  
 這項功能所公開的功能會在內部使用虛擬機器 (VM)。 不當使用這些方法可能會導致未指定的行為，在 VM 中。 例如，呼叫`EndPreventAsyncAbort`情況下先呼叫`BeginPreventAsyncAbort`VM 先前會遞增它時，無法設定計數器為零。 同樣地，內部的計數器不會溢位檢查。 如果它超過其整數類資料的限制，因為它就會增加主機和 VM，產生的行為是未指定。  
  
 從繼承的成員資訊`ICLRTask`和此介面的其他用法，請參閱[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)介面。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
