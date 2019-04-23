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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbde873481aea9de94862117a99079301965f33c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59220067"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup 介面
提供可讓主應用程式設定的屬性<xref:System.AppDomain?displayProperty=nameWithType>型別之前呼叫[icorruntimehost:: Createdomainex](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)方法用來建立它。  
  
## <a name="properties"></a>屬性  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|取得或設定包含應用程式目錄的名稱。|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|取得或設定應用程式的名稱。|  
|<xref:System.AppDomainSetup.CachePath%2A>|取得或設定其中的檔案已陰影複製的應用程式特定區域的名稱。|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|取得或設定應用程式的組態檔的名稱。|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|取得或設定儲存及存取動態產生的檔案的目錄名稱。|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|取得或設定與此網域相關聯的授權檔案的路徑。|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|取得或設定結合的目錄清單<xref:System.AppDomainSetup.ApplicationBase%2A>探查私用組件的目錄。|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|取得或設定字串值，包含或排除<xref:System.AppDomainSetup.ApplicationBase%2A>從應用程式的搜尋路徑。|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|取得或設定包含要陰影複製組件目錄的名稱。|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|取得或設定字串，表示陰影複製開啟或關閉。 有效值為"true"或"false"。|  
  
## <a name="remarks"></a>備註  
 `IAppDomainSetup`介面會對應至 managed<xref:System.IAppDomainSetup>介面，其中<xref:System.AppDomainSetup>型別會實作。 請參閱<xref:System.IAppDomainSetup?displayProperty=nameWithType>如其屬性的詳細描述。  
  
 `IAppDomainSetup` 表示可以加入的組件繫結資訊<xref:System.AppDomain>之前建立的執行個體。 例如，主機可以設定<xref:System.AppDomainSetup.ApplicationBase%2A>屬性，以建立根目錄，common language runtime (CLR) 探查 managed 組件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
