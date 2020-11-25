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
ms.openlocfilehash: eba9caece91e369cd46aed652b559ace49c77725
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95704899"
---
# <a name="iclrappdomainresourcemonitorgetcurrentsurvived-method"></a>ICLRAppDomainResourceMonitor::GetCurrentSurvived 方法

取得最後一次完整、封鎖垃圾收集和目前應用程式域所參考的位元組數目。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT STDMETHODCALLTYPE GetCurrentSurvived(  
             [in]  DWORD dwAppDomainId,  
             [out] ULONGLONG *pAppDomainBytesSurvived,  
             [out] ULONGLONG *pTotalBytesSurvived);  
```  
  
## <a name="parameters"></a>參數  

 `dwAppDomainId`  
 在要求之應用程式域的識別碼。  
  
 `pAppDomainBytesSurvived`  
 擴展此應用程式域所持有之最後一次垃圾收集之後存活的位元組數目指標。 在完整集合之後，這個數位就是正確且完整的。 暫時收集之後，此數位可能不完整。 這個參數可以是 `null`。  
  
 `pRuntimeBytesSurvived`  
 擴展從上次垃圾收集中存活的總位元組數的指標。 在完整集合之後，此數位代表 managed 堆積中保留的位元組數目。 在暫時集合之後，此數位代表暫時層代中存留的位元組數目。 這個參數可以是 `null`。  
  
## <a name="return-value"></a>傳回值  

 這個方法會傳回下列特定的 HRESULT，以及表示方法失敗的 HRESULT 錯誤。  
  
|HRESULT|描述|  
|-------------|-----------------|  
|S_OK|已成功完成命令。|  
|COR_E_APPDOMAINUNLOADED|應用程式域已卸載或不存在。|  
  
## <a name="remarks"></a>備註  

 只有在完整、封鎖的垃圾收集之後，才會更新統計資料。亦即，包含所有層代的集合，以及在收集時停止應用程式的集合。 例如，方法多載會 <xref:System.GC.Collect?displayProperty=nameWithType> 執行完整的封鎖集合。 並行垃圾收集會在背景進行，而且不會封鎖應用程式。  
  
 `GetCurrentSurvived`方法是 managed 屬性的非受控對等專案 <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> 。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [ICLRAppDomainResourceMonitor 介面](iclrappdomainresourcemonitor-interface.md)
- [應用程式域資源監視](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [裝載介面](hosting-interfaces.md)
- [裝載](index.md)
