---
title: IAppDomainSetup 介面
ms.date: 03/30/2017
api_name:
- IAppDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IAppDomainSetup
helpviewer_keywords:
- IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type:
- apiref
ms.openlocfilehash: d504101747995557ba526c88de451ebab7b3c556
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698549"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup 介面

提供屬性，可讓主機在 <xref:System.AppDomain?displayProperty=nameWithType> 呼叫 [ICorRuntimeHost：： CreateDomainEx](icorruntimehost-createdomainex-method.md) 方法來建立類型之前，先設定類型。  
  
## <a name="properties"></a>屬性  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|取得或設定包含應用程式的目錄名稱。|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|取得或設定應用程式的名稱。|  
|<xref:System.AppDomainSetup.CachePath%2A>|取得或設定應用程式特定區域的名稱，其中檔案會以陰影複製。|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|取得或設定應用程式的設定檔名稱。|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|取得或設定用來儲存和存取動態產生之檔案的目錄名稱。|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|取得或設定與此網域相關聯之授權檔案的路徑。|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|取得或設定目錄的清單，這些目錄會與 <xref:System.AppDomainSetup.ApplicationBase%2A> 要探查私用元件的目錄合併。|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|取得或設定字串值，這個值會在 <xref:System.AppDomainSetup.ApplicationBase%2A> 應用程式的搜尋路徑中加入或排除。|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|取得或設定包含要陰影複製之元件的目錄名稱。|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|取得或設定字串，這個字串表示是否開啟或關閉陰影複製。 有效的值為 "true" 或 "false"。|  
  
## <a name="remarks"></a>備註  

 `IAppDomainSetup`介面會對應至型別所實的 managed <xref:System.IAppDomainSetup> 介面 <xref:System.AppDomainSetup> 。 <xref:System.IAppDomainSetup?displayProperty=nameWithType>如需其屬性的詳細描述，請參閱。  
  
 `IAppDomainSetup` 表示元件系結資訊，可以 <xref:System.AppDomain> 在實例建立之前將其加入至實例。 例如，主機可以設定 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性來建立根目錄，而 common language runtime (CLR) 探查 managed 元件。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [裝載介面](hosting-interfaces.md)
