---
title: ICLRAppDomainResourceMonitor::GetCurrentCpuTime 方法
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53deeab574716a426c1c4617abe279e72f27c04e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a>ICLRAppDomainResourceMonitor::GetCurrentCpuTime 方法
取得後應用程式定義域建立以來，在目前的應用程式定義域中執行時用掉的所有執行緒的處理器總時間。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
#### <a name="parameters"></a>參數  
 `dwAppDomainId`  
 [in]要求的應用程式定義域的識別碼。  
  
 `pMilliseconds`  
 [out]已使用的所有執行緒的應用程式定義域建立以來，在目前的應用程式定義域中執行時的總處理器時間指標。 這個參數可以是 `null`。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|COR_E_APPDOMAINUNLOADED|應用程式定義域已卸載或不存在。|  
|E_FAIL|未啟用應用程式定義域資源監視。<br /><br /> -或-<br /><br /> 所有其他失敗。|  
  
## <a name="remarks"></a>備註  
 這個方法相當於 unmanaged 的 managed<xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>屬性。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [ICLRAppDomainResourceMonitor 介面](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [應用程式定義域資源監視](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)  
 [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
