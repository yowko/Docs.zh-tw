---
title: ICLRRuntimeHost::SetHostControl 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.SetHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type:
- apiref
ms.openlocfilehash: 32483be43d4d4fe9d185c091e15a13c6feb95600
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728819"
---
# <a name="iclrruntimehostsethostcontrol-method"></a>ICLRRuntimeHost::SetHostControl 方法

設定 common language runtime (CLR) 可用來取得主機 [IHostControl 介面](ihostcontrol-interface.md)之實作為的介面指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a>參數  

 `pHostControl`  
 在主機的 [IHostControl 介面](ihostcontrol-interface.md)介面指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`SetHostControl` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_CLR_ALREADY_STARTED|CLR 已初始化。|  
  
## <a name="remarks"></a>備註  

 您必須在 `SetHostControl` CLR 初始化之前呼叫，也就是在呼叫 [Start 方法](iclrruntimehost-start-method.md) 或使用任何 [中繼資料介面](../metadata/metadata-interfaces.md)之前。 建議您在 `SetHostControl` 呼叫 [CorBindToCurrentRuntime 函數](corbindtocurrentruntime-function.md) 或 [CorBindToRuntimeEx 函數](corbindtoruntimeex-function.md)之後立即呼叫。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRRuntimeHost 介面](iclrruntimehost-interface.md)
- [IHostControl 介面](ihostcontrol-interface.md)
