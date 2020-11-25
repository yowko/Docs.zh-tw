---
title: IHostIoCompletionManager::Bind 方法
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.Bind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type:
- apiref
ms.openlocfilehash: 5231db8de6129ed593e4e0d508b312b7034c01f0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733902"
---
# <a name="ihostiocompletionmanagerbind-method"></a>IHostIoCompletionManager::Bind 方法

將指定的控制碼系結至先前呼叫 [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md)所建立的 i/o 完成通訊埠。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a>參數  

 `hPort`  
 在要系結的 i/o 完成通訊埠 `hHandle` 。 如果的值 `hPort` 是 null， `hHandle` 就會系結至預設的 i/o 完成通訊埠。  
  
 `hHandle`  
 在要系結的作業系統控制碼 `hPort` 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`Bind` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  

 I/o 完成通訊埠是使用的呼叫所建立 `CreateIoCompletionPort` 。 CLR 會呼叫 `Bind` 以將控制碼系結至該埠。  
  
> [!NOTE]
> 當 i/o 要求完成時，主機必須呼叫 [ICLRIoCompletionManager：： OnComplete](iclriocompletionmanager-oncomplete-method.md) 方法。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRIoCompletionManager 介面](iclriocompletionmanager-interface.md)
