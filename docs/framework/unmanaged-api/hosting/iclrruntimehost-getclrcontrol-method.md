---
title: ICLRRuntimeHost::GetCLRControl 方法
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type:
- apiref
ms.openlocfilehash: 928ac05fbd3a19a17e7f37674b2a75f8bc799fc6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728864"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a>ICLRRuntimeHost::GetCLRControl 方法

取得型別 [ICLRControl 介面](iclrcontrol-interface.md) 的介面指標，該介面可供主機用來自訂 common language RUNTIME (CLR) 的各個層面。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a>參數  

 `pCLRControl`  
 擴展型別 [ICLRControl 介面](iclrcontrol-interface.md) 的介面指標，可讓主控制項設定 CLR 的其他層面。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`GetCLRControl` 傳回成功。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 如果方法傳回 E_FAIL，則 CLR 在進程內將無法再使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|HOST_E_INVALIDOPERATION|CLR 已經啟動。|  
  
## <a name="remarks"></a>備註  

 `ICLRControl` 提供 [GetCLRManager 方法](iclrcontrol-getclrmanager-method.md) 方法，可讓主機取得其中一個管理員類型的介面指標。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRControl 介面](iclrcontrol-interface.md)
- [ICLRRuntimeHost 介面](iclrruntimehost-interface.md)
