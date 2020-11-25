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
ms.openlocfilehash: 7f8963403c60815bbf1cd3008ed7fec73d849fea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720252"
---
# <a name="iclrtask2endpreventasyncabort-method"></a>ICLRTask2::EndPreventAsyncAbort 方法

允許新的或擱置中的執行緒中止要求，導致執行緒在目前線程上中止。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT EndPreventAsyncAbort();  
```  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|HOST_E_INVALIDOPERATION|方法是在不是目前線程的執行緒上呼叫。|  
  
## <a name="remarks"></a>備註  

 呼叫這個方法會將目前線程的延遲線程中止計數器遞減一。  
  
 呼叫 [ICLRTask2：： BeginPreventAsyncAbort](iclrtask2-beginpreventasyncabort-method.md) 和 `EndPreventAsyncAbort` 可以進行嵌套。 只要計數器大於零，目前線程的執行緒中止就會延遲。  
  
 虛擬機器 (VM) 會在內部使用這項功能所公開的功能。 誤用這些方法可能會導致 VM 未指定的行為。 例如，呼叫 `EndPreventAsyncAbort` 時若未先呼叫， `BeginPreventAsyncAbort` 就可以在 VM 先前遞增計數器時，將計數器設定為零。 同樣地，不會檢查內部計數器是否有溢位。 如果它超過整數限制，因為它會同時由主機和 VM 遞增，則會未指定產生的行為。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [BeginPreventAsyncAbort 方法](iclrtask2-beginpreventasyncabort-method.md)
- [ICLRTask2 介面](iclrtask2-interface.md)
- [ICLRTaskManager 介面](iclrtaskmanager-interface.md)
- [IHostTask 介面](ihosttask-interface.md)
- [IHostTaskManager 介面](ihosttaskmanager-interface.md)
- [裝載介面](hosting-interfaces.md)
