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
ms.openlocfilehash: 47c6dd9045636bcfbe07c909fec3fda515d28ee8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124530"
---
# <a name="iclrtask2-interface"></a>ICLRTask2 介面
提供[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)介面的所有功能;此外，也提供可讓執行緒中止在目前線程上延遲的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginPreventAsyncAbort 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-beginpreventasyncabort-method.md)|延遲目前線程上的新執行緒中止要求。|  
|[EndPreventAsyncAbort 方法](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-endpreventasyncabort-method.md)|允許新的或暫止的執行緒中止要求，導致目前線程上的執行緒中止。|  
  
## <a name="remarks"></a>備註  
 `ICLRTask2` 介面會繼承 `ICLRTask` 介面，並新增可讓主機延遲線程中止的方法，以保護不能失敗的程式碼區域。 呼叫 `BeginPreventAsyncAbort` 會遞增目前線程的延遲線程中止計數器，而呼叫 `EndPreventAsyncAbort` 會將其遞減。 `BeginPreventAsyncAbort` 和 `EndPreventAsyncAbort` 的呼叫可以進行嵌套。 只要計數器大於零，就會延遲目前線程的執行緒中止。  
  
 如果 `BeginPreventAsyncAbort` 和 `EndPreventAsyncAbort` 的呼叫未配對，則可能會到達無法將執行緒中止傳遞至目前線程的狀態。  
  
 中斷本身的執行緒不會接受延遲。  
  
 這項功能所公開的功能會在虛擬機器（VM）內部使用。 誤用這些方法可能會導致 VM 中未指定的行為。 例如，在沒有第一次呼叫 `BeginPreventAsyncAbort` 的情況下呼叫 `EndPreventAsyncAbort`，會在 VM 先前已遞增時，將計數器設定為零。 同樣地，內部計數器也不會檢查溢位。 如果它超過其整數限制，因為它是由主機和 VM 增加，則會未指定所產生的行為。  
  
 如需繼承自 `ICLRTask` 的成員以及此介面的其他用法的詳細資訊，請參閱[ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)介面。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [ICLRTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [IHostTask 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [IHostTaskManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
