---
title: ICLRTask2::BeginPreventAsyncAbort 方法
ms.date: 03/30/2017
api_name:
- ICLRTask2.BeginPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 85a43fef7f6dfa6dbe0bb9f1c4caec2c9c224b93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763427"
---
# <a name="iclrtask2beginpreventasyncabort-method"></a>ICLRTask2::BeginPreventAsyncAbort 方法
延遲執行緒中止的新要求導致執行緒中止目前的執行緒上。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|HOST_E_INVALIDOPERATION|這不是目前執行緒的執行緒上呼叫方法。|  
  
## <a name="remarks"></a>備註  
 呼叫這個方法的其中一個遞增目前執行緒的延遲執行緒中止計數器。  
  
 若要呼叫`BeginPreventAsyncAbort`並[ICLRTask2::EndPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)可以巢狀。 計數器是小於或等於零，因為目前執行緒的執行緒中止都延遲。 如果此呼叫未配對的呼叫`EndPreventAsyncAbort`方法，您就能夠達到在哪一個執行緒中止不能傳遞到目前執行緒的狀態。  
  
 中止本身的執行緒不被接受的延遲。  
  
 這項功能所公開的功能會在內部使用虛擬機器 (VM)。 不當使用這些方法可能會導致未指定的行為，在 VM 中。 例如，呼叫`EndPreventAsyncAbort`情況下先呼叫`BeginPreventAsyncAbort`VM 先前會遞增它時，無法設定計數器為零。 同樣地，內部的計數器不會溢位檢查。 如果它超過其整數類資料的限制，因為它就會增加主機和 VM，產生的行為是未指定。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EndPreventAsyncAbort 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)
- [ICLRTask2 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
