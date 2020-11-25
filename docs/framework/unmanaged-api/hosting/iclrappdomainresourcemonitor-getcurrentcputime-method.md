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
ms.openlocfilehash: a0b966e85bedcbef622aba2f6b181b98e0950e01
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700674"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a>ICLRAppDomainResourceMonitor::GetCurrentCpuTime 方法

取得在目前的應用程式域中執行時，在目前的應用程式域中執行之所有線程所使用的總處理器時間，因為已建立應用程式域。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a>參數  

 `dwAppDomainId`  
 在要求之應用程式域的識別碼。  
  
 `pMilliseconds`  
 擴展自建立應用程式域之後，所有線程在目前應用程式域中執行時所使用之總處理器時間的指標。 這個參數可以是 `null`。  
  
## <a name="return-value"></a>傳回值  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|COR_E_APPDOMAINUNLOADED|應用程式域已卸載或不存在。|  
|E_FAIL|未啟用應用程式域資源監視。<br /><br /> -或-<br /><br /> 所有其他失敗。|  
  
## <a name="remarks"></a>備註  

 這個方法是 managed 屬性的非受控對等專案 <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAppDomainResourceMonitor 介面](iclrappdomainresourcemonitor-interface.md)
- [裝載介面](hosting-interfaces.md)
- [應用程式域資源監視](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [裝載](index.md)
