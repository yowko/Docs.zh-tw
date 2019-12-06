---
title: ICorRuntimeHost::GetDefaultDomain 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
ms.openlocfilehash: 6dc25cbeef2576a2ecc6ec39b2cb3f9abb7b9964
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139562"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a>ICorRuntimeHost::GetDefaultDomain 方法
取得類型 <xref:System._AppDomain?displayProperty=nameWithType> 的介面指標，表示目前進程的預設網域。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a>參數  
 `pAppDomain`  
 脫銷類型的介面指標，<xref:System._AppDomain?displayProperty=nameWithType> 指向代表進程之預設應用程式域的 <xref:System.AppDomain> 實例。  
  
 這個指標的型別 `IUnknown`，因此呼叫端通常應該呼叫 `QueryInterface` 來取得型別 <xref:System._AppDomain?displayProperty=nameWithType>的介面指標。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|作業成功。|  
|S_FALSE|作業無法完成。|  
|E_FAIL|發生未知的嚴重失敗。 如果方法傳回 E_FAIL，則 common language runtime （CLR）在進程中就不再可用。 對任何裝載 Api 的後續呼叫都會傳回 HOST_E_CLRNOTAVAILABLE。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入進程中，或 CLR 處於無法執行 managed 程式碼或成功處理呼叫的狀態。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：** 1.0、1.1  
  
## <a name="see-also"></a>請參閱

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
