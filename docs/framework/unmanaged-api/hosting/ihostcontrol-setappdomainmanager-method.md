---
title: IHostControl::SetAppDomainManager 方法
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
ms.openlocfilehash: de264135450190fd028eb8cf12017d94cc65ffac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134728"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a>IHostControl::SetAppDomainManager 方法
通知主機已建立應用程式域。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a>參數  
 `dwAppDomainID`  
 在所選取 <xref:System.AppDomain>的數值識別碼。  
  
 `pUnkAppDomainManager`  
 在主機實作為 `IUnknown`之 <xref:System.AppDomainManager> 物件的指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功傳回 `SetAppDomainManager`。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|呼叫端沒有擁有鎖定。|  
|HOST_E_ABANDONED|已封鎖的執行緒或光纖在等候時取消了事件。|  
|E_FAIL|發生不明的嚴重失敗。 當方法傳回 E_FAIL 時，CLR 就無法在進程內使用。 對裝載方法的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 <xref:System.AppDomainManager> 提供主機一個機制來啟動 managed 程式碼，以及控制每個 <xref:System.AppDomain>的建立和設定。 建立該 <xref:System.AppDomain> 時，會將 <xref:System.AppDomainManager> 載入每個 <xref:System.AppDomain>。 如果選擇，CLR 會藉由設定 `pUnkAppDomainManager` 參數的值，來通知主機已建立應用程式域。  
  
 在它的 `SetAppDomainManager` 方法的執行中，主機可以設定應用程式域管理員的元件名稱和類型。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [IHostControl 介面](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
