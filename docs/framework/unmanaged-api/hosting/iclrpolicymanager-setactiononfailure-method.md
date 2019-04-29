---
title: ICLRPolicyManager::SetActionOnFailure 方法
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34d9e1a3747ecf3dffc925d7883599b773dd51f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638966"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a>ICLRPolicyManager::SetActionOnFailure 方法
指定在發生指定的失敗時，應該採取 common language runtime (CLR) 的原則動作。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>參數  
 `failure`  
 [in]其中一個[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)值，表示要採取的動作失敗的類型。  
  
 `action`  
 [in]其中一個[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)值，指出發生失敗時要採取的動作。 如需支援的值的清單，請參閱 < 備註 > 一節。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`SetActionOnFailure` 已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
|HOST_E_TIMEOUT|呼叫已逾時。|  
|HOST_E_NOT_OWNER|呼叫端未擁有鎖定。|  
|HOST_E_ABANDONED|事件已取消時已封鎖的執行緒或 fiber 等候它。|  
|E_FAIL|發生未知的嚴重錯誤。 方法會傳回 E_FAIL 之後，CLR 不再使用舊的處理序內。 若要裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_INVALIDARG|無法為指定的作業，設定原則動作或作業已指定無效的原則動作。|  
  
## <a name="remarks"></a>備註  
 根據預設，CLR 會配置的資源，例如記憶體失敗時擲回例外狀況。 `SetActionOnFailure` 可讓主機覆寫這個行為，藉由指定原則来採取的動作時失敗。 下表顯示的組合[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)並[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)所支援的值。 (FAIL_ 前置詞會略過[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)值。)  
  
||NonCriticalResource|CriticalResource|FatalRuntime|OrphanedLock|StackOverflow|AccessViolation|CodeContract|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|X|X||||N/A||  
|eThrowException|X|X||||N/A||  
|`eAbortThread`|X|X||||N/A|X|  
|`eRudeAbortThread`|X|X||||N/A|X|  
|`eUnloadAppDomain`|X|X||X||N/A|X|  
|`eRudeUnloadAppDomain`|X|X||X|X|N/A|X|  
|`eExitProcess`|X|X||X|X|N/A|X|  
|eFastExitProcess|X|X||X|X|N/A||  
|`eRudeExitProcess`|X|X|X|X|X|N/A||  
|`eDisableRuntime`|X|X|X|X|X|N/A||  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EClrFailure 列舉](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EPolicyAction 列舉](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRPolicyManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
