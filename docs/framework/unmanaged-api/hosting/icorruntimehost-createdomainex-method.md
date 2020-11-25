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
ms.openlocfilehash: d6d9e06b6ed40bb0e5a65fd64f8bca7abe3afa84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715676"
---
# <a name="icorruntimehostcreatedomainex-method"></a>ICorRuntimeHost::CreateDomainEx 方法

建立應用程式域。 呼叫端會接收類型的介面指標， <xref:System._AppDomain> 其類型為的實例 <xref:System.AppDomain?displayProperty=nameWithType> 。 這個方法可讓呼叫端傳遞 IAppDomainSetup 實例，以設定所傳回實例的額外功能 <xref:System._AppDomain> 。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a>參數  

 `pwzFriendlyName`  
 在選擇性參數，用來為網域提供易記的名稱。 此易記名稱可以顯示在使用者介面（例如偵錯工具）中，以識別網域。  
  
 `pSetup`  
 在型別的選用介面指標 `IAppDomainSetup` ，由呼叫 [ICorRuntimeHost：： CreateDomainSetup](icorruntimehost-createdomainsetup-method.md) 方法取得。  
  
 `pIdentityArray`  
 在實例的選擇性指標陣列 `IIdentity` ，表示透過安全性原則對應的辨識項，以建立許可權集合。 您 `IIdentity` 可以藉由呼叫 [CreateEvidence](icorruntimehost-createevidence-method.md) 方法來取得物件。  
  
 `pAppDomain`  
 擴展實例的型別介面指標 <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> ，可以用來進一步控制定義域。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|作業成功。|  
|S_FALSE|作業無法完成。|  
|E_FAIL|發生未知的嚴重失敗。 如果方法傳回 E_FAIL，則程式中的 common language runtime (CLR) 將無法再使用。 對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入至進程，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
  
## <a name="remarks"></a>備註  

 `CreateDomainEx` 藉由允許呼叫端傳入具有屬性值的實例來擴充 [CreateDomain](icorruntimehost-createdomain-method.md) 的功能， `IAppDomainSetup` 以設定應用程式域。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：** 1.0、1。1  
  
## <a name="see-also"></a>另請參閱

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [CreateDomain 方法](icorruntimehost-createdomain-method.md)
- [ICorRuntimeHost 介面](icorruntimehost-interface.md)
