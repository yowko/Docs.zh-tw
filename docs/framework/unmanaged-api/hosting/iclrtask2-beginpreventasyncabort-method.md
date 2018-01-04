---
title: "ICLRTask2::BeginPreventAsyncAbort 方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTask2.BeginPreventAsyncAbort
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTask2::BeginPreventAsyncAbort
helpviewer_keywords:
- ICLRTask2::BeginPreventAsyncAbort method [.NET Framework hosting]
- BeginPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: 75754c2f-38c7-4707-85fe-559db4542729
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7bbbf609963f06e6c0204e8d44db30bb392886e3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtask2beginpreventasyncabort-method"></a>ICLRTask2::BeginPreventAsyncAbort 方法
延遲新執行緒中止的要求結果的執行緒中止目前的執行緒上。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT BeginPreventAsyncAbort();  
```  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|HOST_E_INVALIDOPERATION|這不是目前執行緒的執行緒上呼叫方法。|  
  
## <a name="remarks"></a>備註  
 呼叫這個方法會延遲執行緒中止計數器目前的執行緒加一。  
  
 呼叫`BeginPreventAsyncAbort`和[iclrtask2:: Endpreventasyncabort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)可以巢狀。 只要計數器是小於或等於零，執行緒中止目前的執行緒會延遲。 如果此呼叫未成對的呼叫`EndPreventAsyncAbort`方法，您就能夠達到在哪一個執行緒中止無法傳遞至目前執行緒的狀態。  
  
 中止本身的執行緒不是接受的延遲。  
  
 這項功能所公開的功能是由虛擬機器 (VM) 內部使用。 不當使用這些方法可能導致 VM 未指定的行為。 例如，呼叫`EndPreventAsyncAbort`情況下先呼叫`BeginPreventAsyncAbort`VM 之前會遞增它時，無法設定計數器為零。 同樣地，內部計數器不會檢查溢位。 如果它超過其整數類資料的限制，因為主機和 VM，就會遞增，結果行為是未指定。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [EndPreventAsyncAbort 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)  
 [ICLRTask2 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
