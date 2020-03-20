---
title: IHostSecurityManager::GetSecurityContext 方法
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.GetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type:
- apiref
ms.openlocfilehash: 7198698edce48546c4f9a82ace18d5a6e71891ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176249"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a>IHostSecurityManager::GetSecurityContext 方法
從主機獲取請求的[IHost 安全上下文](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)。  
  
## <a name="syntax"></a>語法  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a>參數  
 `eContextType`  
 [在][ECoNtextType](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)值之一，指示要返回的安全上下文的類型。  
  
 `ppSecurityContext`  
 [出]指向 的`IHostSecurityContext`介面指標的位址`eContextType`。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|`GetSecurityContext`已成功返回。|  
|HOST_E_CLRNOTAVAILABLE|公共語言運行時 （CLR） 尚未載入到進程中，或者 CLR 處於無法運行託管代碼或成功處理調用的狀態。|  
|HOST_E_TIMEOUT|呼叫超時。|  
|HOST_E_NOT_OWNER|調用方不擁有鎖。|  
|HOST_E_ABANDONED|當阻塞的執行緒或光纖等待事件時，事件已被取消。|  
|E_FAIL|發生了未知的災難性故障。 當方法返回E_FAIL時，CLR 在進程中不再可用。 對託管方法的後續調用返回HOST_E_CLRNOTAVAILABLE。|  
  
## <a name="remarks"></a>備註  
 主機可以通過 CLR 和使用者代碼控制對執行緒權杖的所有代碼訪問。 它還可確保在具有受限代碼存取權限的非同步作業或代碼點傳遞完整的安全上下文資訊。 `IHostSecurityContext`封裝此安全上下文資訊，這些資訊對 CLR 是不透明的。 CLR 捕獲此資訊並將其跨執行緒池輔助工項調度、終端子執行以及模組和類構造移動。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** 作為資源包含在 MSCorEE.dll 中  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [EContextType 列舉](../../../../docs/framework/unmanaged-api/hosting/econtexttype-enumeration.md)
- [IHostSecurityContext 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager 介面](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
