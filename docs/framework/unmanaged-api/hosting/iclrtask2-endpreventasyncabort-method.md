---
title: ICLRTask2::EndPreventAsyncAbort 方法
ms.date: 03/30/2017
api_name:
- ICLRTask2.EndPreventAsyncAbort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTask2::EndPreventAsyncAbort
helpviewer_keywords:
- EndPreventAsyncAbort method [.NET Framework hosting]
- ICLRTask2::EndPreventAsyncAbort method [.NET Framework hosting]
ms.assetid: d8013659-e3df-44b3-814f-a6b534ce62f8
topic_type:
- apiref
ms.openlocfilehash: 8ae66e0bf96138e5bc2f33e4c14ad86e7dabc6b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124545"
---
# <a name="iclrtask2endpreventasyncabort-method"></a>ICLRTask2::EndPreventAsyncAbort 方法
允許新的或暫止的執行緒中止要求，導致目前線程上的執行緒中止。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|HOST_E_INVALIDOPERATION|在不是目前線程的執行緒上呼叫方法。|  
  
## <a name="remarks"></a>備註  
 呼叫這個方法會將目前線程的延遲線程中止計數器減一。  
  
 [ICLRTask2：： BeginPreventAsyncAbort](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)和 `EndPreventAsyncAbort` 的呼叫可以進行嵌套。 只要計數器大於零，就會延遲目前線程的執行緒中止。  
  
 這項功能所公開的功能會在虛擬機器（VM）內部使用。 誤用這些方法可能會導致 VM 中未指定的行為。 例如，在沒有第一次呼叫 `BeginPreventAsyncAbort` 的情況下呼叫 `EndPreventAsyncAbort`，會在 VM 先前已遞增時，將計數器設定為零。 同樣地，內部計數器也不會檢查溢位。 如果它超過其整數限制，因為它是由主機和 VM 增加，則會未指定所產生的行為。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [BeginPreventAsyncAbort 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)
- [ICLRTask2 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)
- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
