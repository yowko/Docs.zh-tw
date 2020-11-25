---
title: ICLRControl::GetCLRManager 方法
ms.date: 03/30/2017
api_name:
- ICLRControl.GetCLRManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type:
- apiref
ms.openlocfilehash: d18b3a5c06ac0d3a86f7823f3b140c76c6c9a746
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728351"
---
# <a name="iclrcontrolgetclrmanager-method"></a>ICLRControl::GetCLRManager 方法

取得任何管理員型別的實例介面指標，主機可以用來設定 common language runtime (CLR) 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a>參數  

 `riid`  
 在要傳回的 `IID` 管理員型別的。 支援下列 `IID` 值。  
  
- IID_ICLRDebugManager：指定 `ppObject` 將為 [ICLRDebugManager](iclrdebugmanager-interface.md)類型。  
  
- IID_ICLRErrorReportingManager：指定 `ppObject` 將為 [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md)類型。  
  
- IID_ICLRGCManager：指定 `ppObject` 將為 [ICLRGCManager](iclrgcmanager-interface.md)類型。  
  
- IID_ICLRHostProtectionManager：指定 `ppObject` 將為 [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md)類型。  
  
- IID_ICLROnEventManager：指定 `ppObject` 將為 [ICLROnEventManager](iclroneventmanager-interface.md)類型。  
  
- IID_ICLRPolicyManager：指定 `ppObject` 將為 [ICLRPolicyManager](iclrpolicymanager-interface.md)類型。  
  
- IID_ICLRTaskManager：指定 `ppObject` 將為 [ICLRTaskManager](iclrtaskmanager-interface.md)類型。  
  
 `ppObject`  
 擴展要求的管理員的介面指標，如果要求的管理員類型無效，則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|此方法已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫已超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|當封鎖的執行緒或光纖正在等候時，已取消事件。|  
|E_FAIL|發生未知的嚴重失敗。 在方法傳回 E_FAIL 之後，就無法在進程中使用 CLR。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_NOINTERFACE|不支援介面類別型。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRControl 介面](iclrcontrol-interface.md)
- [IHostControl 介面](ihostcontrol-interface.md)
