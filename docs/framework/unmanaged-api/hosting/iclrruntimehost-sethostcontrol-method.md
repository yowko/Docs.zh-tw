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
ms.openlocfilehash: 644b31ae8e8f0c51c08bcad57220a028406cfd3a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504068"
---
# <a name="iclrruntimehostsethostcontrol-method"></a>ICLRRuntimeHost::SetHostControl 方法
設定 common language runtime （CLR）可用來取得[IHostControl 介面](ihostcontrol-interface.md)之主機的介面指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a>參數  
 `pHostControl`  
 在主機的[IHostControl 介面](ihostcontrol-interface.md)的介面指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|`SetHostControl`已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 如果方法傳回 E_FAIL，就無法在進程內使用 CLR。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_CLR_ALREADY_STARTED|CLR 已經初始化。|  
  
## <a name="remarks"></a>備註  
 您必須在 `SetHostControl` CLR 初始化之前呼叫，也就是在呼叫[Start 方法](iclrruntimehost-start-method.md)或使用任何[中繼資料介面](../metadata/metadata-interfaces.md)之前。 建議您在 `SetHostControl` 呼叫[CorBindToCurrentRuntime 函數](corbindtocurrentruntime-function.md)或[CorBindToRuntimeEx 函數](corbindtoruntimeex-function.md)之後立即呼叫。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRRuntimeHost 介面](iclrruntimehost-interface.md)
- [IHostControl 介面](ihostcontrol-interface.md)
