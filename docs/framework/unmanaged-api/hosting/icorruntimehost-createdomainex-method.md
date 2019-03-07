---
title: ICorRuntimeHost::CreateDomainEx 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5ed45c3975c58331490f89d8ca705f080d01d74e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466800"
---
# <a name="icorruntimehostcreatedomainex-method"></a>ICorRuntimeHost::CreateDomainEx 方法
建立應用程式定義域。 呼叫端會收到類型的介面指標<xref:System._AppDomain>，執行個體的型別<xref:System.AppDomain?displayProperty=nameWithType>。 這個方法可讓呼叫端傳遞 IAppDomainSetup 執行個體來設定傳回的其他功能<xref:System._AppDomain>執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a>參數  
 `pwzFriendlyName`  
 [in]選擇性參數，可用來為網域指定的易記名稱。 此易記名稱可以顯示在使用者介面，例如偵錯工具，以識別該定義域。  
  
 `pSetup`  
 [in]選擇性的介面指標的型別`IAppDomainSetup`呼叫得到[icorruntimehost:: Createdomainsetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)方法。  
  
 `pIdentityArray`  
 [in]選擇性的指標陣列`IIdentity`執行個體，表示對應到安全性原則，以建立權限集合的辨識項。 `IIdentity`物件，可由呼叫[CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)方法。  
  
 `pAppDomain`  
 [out]類型的介面指標<xref:System._AppDomain>的執行個體<xref:System.AppDomain?displayProperty=nameWithType>，可用來進一步控制網域。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|此作業成功。|  
|S_FALSE|作業無法完成。|  
|E_FAIL|發生不明、 重大失敗。 如果方法會傳回 E_FAIL，common language runtime (CLR) 不再使用舊處理序中。 任何裝載 api 的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|HOST_E_CLRNOTAVAILABLE|不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
  
## <a name="remarks"></a>備註  
 `CreateDomainEx` 擴充功能[CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)藉由呼叫者傳入`IAppDomainSetup`與設定應用程式定義域的屬性值的執行個體。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** 1.0, 1.1  
  
## <a name="see-also"></a>另請參閱
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [CreateDomain 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)
- [ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
