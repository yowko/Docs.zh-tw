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
ms.openlocfilehash: 04cb45cd021532b6cb3d74a195cbd62e1ab8d31d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615848"
---
# <a name="iclrcontrolgetclrmanager-method"></a>ICLRControl::GetCLRManager 方法
取得主機可以用來設定 common language runtime （CLR）之任何管理員類型的實例介面指標。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a>參數  
 `riid`  
 在`IID`要傳回之管理員類型的。 支援下列 `IID` 值。  
  
- IID_ICLRDebugManager：指定 `ppObject` 將屬於[ICLRDebugManager](iclrdebugmanager-interface.md)類型。  
  
- IID_ICLRErrorReportingManager：指定 `ppObject` 將屬於[ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md)類型。  
  
- IID_ICLRGCManager：指定 `ppObject` 將屬於[ICLRGCManager](iclrgcmanager-interface.md)類型。  
  
- IID_ICLRHostProtectionManager：指定 `ppObject` 將屬於[ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md)類型。  
  
- IID_ICLROnEventManager：指定 `ppObject` 將屬於[ICLROnEventManager](iclroneventmanager-interface.md)類型。  
  
- IID_ICLRPolicyManager：指定 `ppObject` 將屬於[ICLRPolicyManager](iclrpolicymanager-interface.md)類型。  
  
- IID_ICLRTaskManager：指定 `ppObject` 將屬於[ICLRTaskManager](iclrtaskmanager-interface.md)類型。  
  
 `ppObject`  
 脫銷要求之管理員的介面指標，如果要求的管理員類型無效，則為 null。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|說明|  
|-------------|-----------------|  
|S_OK|此方法已成功傳回。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 在方法傳回 E_FAIL 之後，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|E_NOINTERFACE|不支援介面類別型。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRControl 介面](iclrcontrol-interface.md)
- [IHostControl 介面](ihostcontrol-interface.md)
