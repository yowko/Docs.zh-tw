---
title: ICorRuntimeHost::CurrentDomain 方法
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CurrentDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CurrentDomain
helpviewer_keywords:
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
- CurrentDomain method [.NET Framework hosting]
ms.assetid: dd2afb38-675b-4c3c-a9f3-8ab3b133eb02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 96cda3f504910d8fb70905f66b45f417158c505d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="icorruntimehostcurrentdomain-method"></a>ICorRuntimeHost::CurrentDomain 方法
取得類型的介面指標<xref:System.AppDomain?displayProperty=nameWithType>，代表目前執行緒上載入的網域。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pAppDomain`  
 [out]類型的指標<xref:System.AppDomain?displayProperty=nameWithType>代表執行緒的目前應用程式定義域。 此指標為型別`IUnknown`，因此呼叫端通常應該呼叫`QueryInterface`取得型別的指標<xref:System._AppDomain>。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|此作業成功。|  
|S_FALSE|無法完成操作。|  
|E_FAIL|發生未知的嚴重失敗。 若方法會傳回 E_FAIL，common language runtime (CLR) 就不會再處理序中。 任何裝載的應用程式開發介面的後續呼叫會傳回 HOST_E_CLRNOTAVAILABLE。|  
|HOST_E_CLRNOTAVAILABLE|CLR 尚未載入到處理程序，或 CLR 正在中它無法執行 managed 程式碼，或成功地處理呼叫的狀態。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** 1.0、 1.1  
  
## <a name="see-also"></a>另請參閱  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
