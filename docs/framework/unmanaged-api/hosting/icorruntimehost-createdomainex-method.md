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
ms.openlocfilehash: 4e5856fbcda83c1dd30559c6f59f63495faea78d
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762340"
---
# <a name="icorruntimehostcreatedomainex-method"></a>ICorRuntimeHost::CreateDomainEx 方法
建立應用程式域。 呼叫端會接收類型的介面指標， <xref:System._AppDomain> 其型別為的實例 <xref:System.AppDomain?displayProperty=nameWithType> 。 這個方法可讓呼叫端傳遞 IAppDomainSetup 實例，以設定傳回之實例的其他功能 <xref:System._AppDomain> 。  
  
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
 在選擇性參數，用來為定義域提供易記名稱。 這個易記名稱可以在使用者介面（例如偵錯工具）中顯示，以識別網域。  
  
 `pSetup`  
 在類型的選擇性介面指標 `IAppDomainSetup` ，由呼叫[ICorRuntimeHost：： CreateDomainSetup](icorruntimehost-createdomainsetup-method.md)方法所取得。  
  
 `pIdentityArray`  
 在指向實例的選擇性陣列， `IIdentity` 表示透過安全性原則對應的辨識項，以建立許可權集合。 您 `IIdentity` 可以藉由呼叫[CreateEvidence](icorruntimehost-createevidence-method.md)方法來取得物件。  
  
 `pAppDomain`  
 脫銷實例之類型的介面指標， <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> 可用於進一步控制定義域。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|作業成功。|  
|S_FALSE|作業無法完成。|  
|E_FAIL|發生未知的嚴重失敗。 如果方法傳回 E_FAIL，則 common language runtime （CLR）就無法在進程中使用。 後續對任何裝載 Api 的呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
  
## <a name="remarks"></a>備註  
 `CreateDomainEx`藉由允許呼叫端以屬性值傳入實例以設定應用程式域，來擴充[CreateDomain](icorruntimehost-createdomain-method.md)的功能 `IAppDomainSetup` 。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：** 1.0、1。1  
  
## <a name="see-also"></a>另請參閱

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [CreateDomain 方法](icorruntimehost-createdomain-method.md)
- [ICorRuntimeHost 介面](icorruntimehost-interface.md)
