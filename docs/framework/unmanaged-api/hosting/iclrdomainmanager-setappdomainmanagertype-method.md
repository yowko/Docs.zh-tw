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
ms.openlocfilehash: 5c61e2e1208cec0bda1492964a8d02bd71f5a1c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129324"
---
# <a name="iclrdomainmanagersetappdomainmanagertype-method"></a>ICLRDomainManager::SetAppDomainManagerType 方法
指定將用來初始化預設應用程式域之應用程式網域管理員的衍生自 <xref:System.AppDomainManager?displayProperty=nameWithType> 類別的型別。  
  
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
 在包含應用程式域管理員類型之元件的顯示名稱;例如： "AdMgrExample，Version = 1.0.0.0，Culture = 中性，PublicKeyToken = 6856bccf150f00b3"。  
  
 `wszAppDomainManagerType`  
 在應用程式域管理員的類型名稱，包括命名空間。  
  
 `dwInitializeDomainFlags`  
 在[EInitializeNewDomainFlags](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)列舉值的組合，可提供應用程式域管理員的相關資訊。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|HOST_E_CLRNOTAVAILABLE|Common language runtime （CLR）尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
  
## <a name="remarks"></a>備註  
 目前，`dwInitializeDomainFlags` 的唯一定義值是 `eInitializeNewDomainFlags_NoSecurityChanges`，它會告知 common language runtime （CLR），應用程式域管理員在執行 <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=nameWithType> 方法期間將不會修改安全性設定。 這可讓 CLR 將具有條件式 <xref:System.Security.AllowPartiallyTrustedCallersAttribute> （APTCA）屬性的元件載入優化。 如果這組元件的可轉移關閉很大，這會導致啟動時間大幅改善。  
  
> [!IMPORTANT]
> 如果主機指定應用程式域管理員的 `eInitializeNewDomainFlags_NoSecurityChanges`，如果有任何嘗試修改應用程式域的安全性，則會擲回 <xref:System.InvalidOperationException>。  
  
 呼叫[ICLRControl：： SetAppDomainManagerType](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-setappdomainmanagertype-method.md)方法相當於使用 `eInitializeNewDomainFlags_None`呼叫 `ICLRDomainManager::SetAppDomainManagerType`。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRDomainManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)
- [EInitializeNewDomainFlags 列舉](../../../../docs/framework/unmanaged-api/hosting/einitializenewdomainflags-enumeration.md)
