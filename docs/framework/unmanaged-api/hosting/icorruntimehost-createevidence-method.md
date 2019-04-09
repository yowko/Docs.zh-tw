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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca54f779d257314b843838d90ca9996f1eb3237b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081809"
---
# <a name="icorruntimehostcreateevidence-method"></a>ICorRuntimeHost::CreateEvidence 方法
取得類型的介面指標<xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>，可讓主應用程式建立安全性辨識項，要傳遞給[CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)或是[CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)方法。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a>參數  
 `pEvidence`  
 [out]介面指標<xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>用來建立安全性辨識項的執行個體。 這個指標型別`IUnknown`，所以通常應該呼叫的呼叫端`QueryInterface`若要取得的指標，此介面上<xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|此作業成功。|  
|S_FALSE|作業無法完成。|  
|E_FAIL|發生不明、 重大失敗。 如果方法會傳回 E_FAIL，common language runtime (CLR) 不再使用舊處理序中。 任何裝載 api 的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|HOST_E_CLRNOTAVAILABLE|不到程序中，載入 CLR 或 CLR 處於的狀態不能在其中執行 managed 程式碼，或程序呼叫成功。|  
  
## <a name="remarks"></a>備註  
 這個方法會傳回空集合無法填入從原生程式碼。 您應該使用<xref:System.Security.Policy.Evidence>方法改為。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** 1.0, 1.1  
  
## <a name="see-also"></a>另請參閱

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
