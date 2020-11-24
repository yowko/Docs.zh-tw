---
title: ICLRAppDomainResourceMonitor 介面
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor
helpviewer_keywords:
- ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type:
- apiref
ms.openlocfilehash: 84c53f0666d0e04b898e28c1d8e146eab566ca1b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674693"
---
# <a name="iclrappdomainresourcemonitor-interface"></a>ICLRAppDomainResourceMonitor 介面

提供可檢查應用程式域的記憶體和 CPU 使用量的方法。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[GetCurrentAllocated 方法](iclrappdomainresourcemonitor-getcurrentallocated-method.md)|取得應用程式域自從建立之後所做的所有記憶體配置大小總計（以位元組為單位），而不會減去已進行垃圾收集的記憶體。|  
|[GetCurrentSurvived 方法](iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|取得最後一次完整、封鎖垃圾收集和目前應用程式域所參考的位元組數目。|  
|[GetCurrentCpuTime 方法](iclrappdomainresourcemonitor-getcurrentcputime-method.md)|取得在目前的應用程式域中執行時，在目前的應用程式域中執行之所有線程所使用的總處理器時間，因為已建立應用程式域。|  
  
## <a name="remarks"></a>備註  

 `ICLRAppDomainResourceMonitor`介面提供的功能類似下列受控屬性：  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [\<appDomainResourceMonitoring> 元素](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [應用程式域資源監視](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [裝載介面](hosting-interfaces.md)
- [裝載](index.md)
