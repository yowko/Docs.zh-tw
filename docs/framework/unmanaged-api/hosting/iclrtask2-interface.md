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
ms.openlocfilehash: 9332b3462ba389783a113d173e32850d40427ce2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720226"
---
# <a name="iclrtask2-interface"></a>ICLRTask2 介面

提供 [ICLRTask](iclrtask-interface.md) 介面的所有功能;此外，還提供可讓執行緒中止在目前線程上延遲的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BeginPreventAsyncAbort 方法](iclrtask2-beginpreventasyncabort-method.md)|延遲目前線程上的新執行緒中止要求。|  
|[EndPreventAsyncAbort 方法](iclrtask2-endpreventasyncabort-method.md)|允許新的或擱置中的執行緒中止要求，導致執行緒在目前線程上中止。|  
  
## <a name="remarks"></a>備註  

 `ICLRTask2`介面會繼承 `ICLRTask` 介面，並加入可讓主機延遲線程中止的方法，以保護不能失敗的程式碼區域。 呼叫 `BeginPreventAsyncAbort` 會遞增目前線程的延遲線程中止計數器，並呼叫 `EndPreventAsyncAbort` 遞減。 對和的呼叫 `BeginPreventAsyncAbort` `EndPreventAsyncAbort` 可以嵌套。 只要計數器大於零，目前線程的執行緒中止就會延遲。  
  
 如果對 `BeginPreventAsyncAbort` 和 `EndPreventAsyncAbort` 的呼叫未配對，則可能會達到無法將執行緒中止傳遞給目前線程的狀態。  
  
 中止本身的執行緒不會接受延遲。  
  
 虛擬機器 (VM) 會在內部使用這項功能所公開的功能。 誤用這些方法可能會導致 VM 未指定的行為。 例如，呼叫 `EndPreventAsyncAbort` 時若未先呼叫， `BeginPreventAsyncAbort` 就可以在 VM 先前遞增計數器時，將計數器設定為零。 同樣地，不會檢查內部計數器是否有溢位。 如果它超過整數限制，因為它會同時由主機和 VM 遞增，則會未指定產生的行為。  
  
 如需有關繼承自此介面之其他用法的成員和的詳細資訊 `ICLRTask` ，請參閱 [ICLRTask](iclrtask-interface.md) 介面。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRTask 介面](iclrtask-interface.md)
- [ICLRTaskManager 介面](iclrtaskmanager-interface.md)
- [IHostTask 介面](ihosttask-interface.md)
- [IHostTaskManager 介面](ihosttaskmanager-interface.md)
- [裝載介面](hosting-interfaces.md)
