---
title: ICLRDomainManager::SetAppDomainManagerType 方法
ms.date: 03/30/2017
api_name:
- ICLRDomainManager.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDomainManager::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRDomainManager interface [.NET Framework hosting]
- ICLRDomainManager::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ee91abb0-cb74-41dd-927b-e117fb8ffdf4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c2927195b650f1098292f3d59cd887e084aea21
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490056"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType 方法
指定的型別，衍生自<xref:System.AppDomainManager?displayProperty=nameWithType>類別，將會用來初始化預設應用程式定義域的應用程式定義域管理員。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `wszAppDomainManagerAssembly`  
 [in]包含應用程式定義域管理員類型; 組件的顯示名稱例如：「 AdMgrExample，version=1.0.0.0，Culture = neutral，PublicKeyToken = 6856bccf150f00b3"。  
  
 `wszAppDomainManagerType`  
 [in]應用程式定義域管理員，包括命名空間型別名稱。  
  
 `dwInitializeDomainFlags`  
 [in]組合[EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)提供應用程式定義域管理員的相關資訊的列舉值。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入到處理程序，或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
  
## <a name="remarks"></a>備註  
 目前，唯一定義的值`dwInitializeDomainFlags`已`eInitializeNewDomainFlags_NoSecurityChanges`，這會告知 common language runtime (CLR)，應用程式定義域管理員不會修改安全性設定執行期間<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>方法。 這可讓 CLR 的最佳化的條件式的組件載入<xref:System.Security.AllowPartiallyTrustedCallersAttribute>(APTCA) 屬性。 如果這個集合的組件的可轉移關閉很大，這會導致啟動時間大幅提升。  
  
> [!IMPORTANT]
>  如果指定了主機`eInitializeNewDomainFlags_NoSecurityChanges`應用程式網域管理員，<xref:System.InvalidOperationException>任何嘗試修改應用程式定義域的安全性，便會擲回。  
  
 呼叫[iclrcontrol:: Setappdomainmanagertype](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)方法就相當於呼叫`ICLRDomainManager::SetAppDomainManagerType`使用`eInitializeNewDomainFlags_None`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags 列舉](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
