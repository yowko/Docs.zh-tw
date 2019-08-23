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
ms.openlocfilehash: 9b142f1a05036eddf44c69d8b7da95091dc8f445
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963097"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType 方法
指定將用來初始化預設應用<xref:System.AppDomainManager?displayProperty=nameWithType>程式域之應用程式網域管理員的類型 (衍生自類別)。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT SetAppDomainManagerType(  
    [in] LPCWSTR wszAppDomainManagerAssembly,  
    [in] LPCWSTR wszAppDomainManagerType,  
    [in] EInitializeNewDomainFlags dwInitializeDomainFlags  
);  
```  
  
## <a name="parameters"></a>參數  
 `wszAppDomainManagerAssembly`  
 在包含應用程式域管理員類型之元件的顯示名稱;例如:"AdMgrExample, Version = 1.0.0.0, Culture = 中性, PublicKeyToken = 6856bccf150f00b3"。  
  
 `wszAppDomainManagerType`  
 在應用程式域管理員的類型名稱, 包括命名空間。  
  
 `dwInitializeDomainFlags`  
 在[EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)列舉值的組合, 可提供應用程式域管理員的相關資訊。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime (CLR) 尚未載入進程中, 或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
  
## <a name="remarks"></a>備註  
 目前, 唯一定義的值`dwInitializeDomainFlags`是, 它會`eInitializeNewDomainFlags_NoSecurityChanges`告知 common language runtime (CLR), 應用程式域管理員在<xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType>方法執行期間將不會修改安全性設定。 這可讓 CLR 優化具有條件<xref:System.Security.AllowPartiallyTrustedCallersAttribute>式 (APTCA) 屬性之元件的載入。 如果這組元件的可轉移關閉很大, 這會導致啟動時間大幅改善。  
  
> [!IMPORTANT]
> 如果主機為應用`eInitializeNewDomainFlags_NoSecurityChanges`程式域管理員指定<xref:System.InvalidOperationException> , 則在嘗試修改應用程式域的安全性時, 就會擲回。  
  
 呼叫[ICLRControl:: SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)方法相當於使用`ICLRDomainManager::SetAppDomainManagerType` `eInitializeNewDomainFlags_None`呼叫。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **LIBRARY:** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags 列舉](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
