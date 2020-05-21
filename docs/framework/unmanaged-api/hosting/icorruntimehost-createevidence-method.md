---
title: ICorRuntimeHost::CreateEvidence 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
ms.openlocfilehash: 4a91f57126c0cf2074bd086ddb2fb4cd9e0716d4
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762314"
---
# <a name="icorruntimehostcreateevidence-method"></a>ICorRuntimeHost::CreateEvidence 方法
取得類型的介面指標 <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> ，可讓主機建立要傳遞至[CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)或[CreateDomainEx](icorruntimehost-createdomainex-method.md)方法的安全性辨識項。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a>參數  
 `pEvidence`  
 脫銷實例的介面指標， <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> 用來建立安全性辨識項。 這個指標具有類型 `IUnknown` ，因此呼叫端通常會 `QueryInterface` 在這個介面上呼叫，以取得的指標 <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> 。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|Description|  
|-------------|-----------------|  
|S_OK|作業成功。|  
|S_FALSE|作業無法完成。|  
|E_FAIL|發生未知的嚴重失敗。 如果方法傳回 E_FAIL，則 common language runtime （CLR）就無法在進程中使用。 後續對任何裝載 Api 的呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回無法從機器碼填入的空集合。 您應該改為使用 <xref:System.Security.Policy.Evidence> 方法。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：** 1.0、1。1  
  
## <a name="see-also"></a>另請參閱

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost 介面](icorruntimehost-interface.md)
