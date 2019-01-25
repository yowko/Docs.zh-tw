---
title: ICLRAppDomainResourceMonitor::GetCurrentSurvived 方法
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentSurvived
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentSurvived method [.NET Framework hosting]
- GetCurrentSurvived method [.NET Framework hosting]
ms.assetid: 392e9009-40ef-40e3-ad4d-7ce93a989e78
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 648a2c044920b7524ad96ff656e83268ffd55652
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54612212"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a>ICLRAppDomainResourceMonitor::GetCurrentSurvived 方法
取得最後一個完整的封鎖記憶體回收回收的和目前的應用程式定義域所參考之位元組數目。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
#### <a name="parameters"></a>參數  
 `dwAppDomainId`  
 [in]要求的應用程式定義域的識別碼。  
  
 `pAppDomainBytesSurvived`  
 [out]在上一個記憶體回收後殘留下來這個應用程式定義域所持有的位元組數目指標。 在完整收集之後, 這個數字是精確且完整。 暫時的集合，這個數字之後可能不完整。 這個參數可以是 `null`。  
  
 `pRuntimeBytesSurvived`  
 [out]從上一個記憶體回收中存活下來的位元組總數目指標。 在完整收集之後, 這個數字代表 managed 堆積保留的位元組數目。 在暫時的集合之後, 這個數字會代表持有即時暫時層代中的位元組數目。 這個參數可以是 `null`。  
  
## <a name="return-value"></a>傳回值  
 這個方法會傳回下列特定的 HRESULT 以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|COR_E_APPDOMAINUNLOADED|應用程式定義域已卸載或不存在。|  
  
## <a name="remarks"></a>備註  
 完整的封鎖記憶體回收; 之後，才會更新統計資料也就是的集合，其中包含所有層代和，以停止應用程式，這時集合就會發生。 比方說，<xref:System.GC.Collect?displayProperty=nameWithType>方法多載會執行完整、 阻斷式收集。 並行記憶體回收會在背景進行，並不會封鎖應用程式。  
  
 `GetCurrentSurvived`方法相當於未受管理的受管理<xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>屬性。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **程式庫：** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [ICLRAppDomainResourceMonitor 介面](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)
- [應用程式定義域資源監視](../../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
