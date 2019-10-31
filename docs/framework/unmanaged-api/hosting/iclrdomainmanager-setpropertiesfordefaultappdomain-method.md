---
title: ICLRDomainManager::SetPropertiesForDefaultAppDomain 方法
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetPropertiesForDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain
helpviewer_keywords:
- ICLRDomainManager::SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
- SetPropertiesForDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 43e61c4b-c435-45ec-9ef6-c68403aa4200
ms.openlocfilehash: 37919be2d0ebd7d243615bc5845b0781ac13e574
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129320"
---
# <a name="iclrdomainmanagersetpropertiesfordefaultappdomain-method"></a>ICLRDomainManager::SetPropertiesForDefaultAppDomain 方法
設定將用來初始化預設應用程式域的屬性。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetPropertiesForDefaultAppDomain(  
    [in] DWORD nProperties,  
    [in] LPCWSTR *pwszPropertyNames,  
    [in] LPCWSTR *pwszPropertyValues  
);  
```  
  
## <a name="parameters"></a>參數  
 `nProperties`  
 在`pwszPropertyNames` 和 `pwszPropertyValues`中的專案數。  
  
 `pwszPropertyNames`  
 在屬性名稱的陣列，如果沒有屬性，則為 null。 目前，這個方法所能辨識的屬性名稱是 "PARTIAL_TRUST_VISIBLE_ASSEMBLIES"。  
  
 `pwszPropertyValues`  
 在屬性值的陣列，如果沒有屬性，則為 null。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|HRESULT_FROM_WIN32(ERROR_UNKNOWN_PROPERTY)|`pwszPropertyNames` 包含此方法無法辨識的屬性名稱。|  
  
## <a name="remarks"></a>備註  
 "PARTIAL_TRUST_VISIBLE_ASSEMBLIES" 的屬性值是具有 [<xref:System.Security.PartialTrustVisibilityLevel.NotVisibleByDefault?displayProperty=nameWithType>] 旗標的 [條件式 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> （APTCA）] 屬性的元件清單，這會在預設應用程式域中對部分信任的呼叫者顯示為可見。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
