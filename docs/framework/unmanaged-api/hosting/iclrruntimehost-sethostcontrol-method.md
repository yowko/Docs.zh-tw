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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 46cfaa5870d7bbc7edcbe438ddf57fe5f70ad938
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrruntimehostsethostcontrol-method"></a>ICLRRuntimeHost::SetHostControl 方法
設定 common language runtime (CLR) 可用來取得主機實作的介面指標[IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pHostControl`  
 [in]主應用程式的實作的介面指標[IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`SetHostControl` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重失敗。 若方法會傳回 E_FAIL，CLR 就不會再處理序內。 裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_CLR_ALREADY_STARTED|CLR 已經初始化。|  
  
## <a name="remarks"></a>備註  
 您必須呼叫`SetHostControl`初始化 CLR 時，也就是在呼叫之前先[啟動方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)或使用任何[中繼資料介面](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)。 建議您呼叫`SetHostControl`後立即呼叫[CorBindToCurrentRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)或[CorBindToRuntimeEx 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
