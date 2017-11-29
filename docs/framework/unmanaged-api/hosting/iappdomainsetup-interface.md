---
title: "IAppDomainSetup 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IAppDomainSetup
api_location: mscoree.dll
api_type: COM
f1_keywords: IAppDomainSetup
helpviewer_keywords: IAppDomainSetup interface [.NET Framework hosting]
ms.assetid: 1844da85-c031-40bf-bea4-1a3d12a36c8c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e6ed5ea00799fff70626114257efef2d06b505ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup 介面
提供可讓主應用程式設定的屬性<xref:System.AppDomain?displayProperty=nameWithType>型別之前呼叫[icorruntimehost:: Createdomainex](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)方法來建立它。  
  
## <a name="properties"></a>屬性  
  
|屬性|說明|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|取得或設定包含應用程式的目錄名稱。|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|取得或設定應用程式的名稱。|  
|<xref:System.AppDomainSetup.CachePath%2A>|取得或設定檔案已陰影複製的應用程式特定區域的名稱。|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|取得或設定應用程式的組態檔的名稱。|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|取得或設定儲存及存取動態產生的檔案的目錄名稱。|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|取得或設定與這個定義域相關聯的使用權檔案的路徑。|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|取得或設定與結合的目錄清單<xref:System.AppDomainSetup.ApplicationBase%2A>探查私用組件的目錄。|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|取得或設定字串值包含或排除<xref:System.AppDomainSetup.ApplicationBase%2A>應用程式的搜尋路徑中。|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|取得或設定包含要陰影複製組件的目錄名稱。|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|取得或設定指示陰影複製開啟或關閉的字串。 有效值為"true"或"false"。|  
  
## <a name="remarks"></a>備註  
 `IAppDomainSetup`介面對應至 managed<xref:System.IAppDomainSetup>介面，其中<xref:System.AppDomainSetup>型別會實作。 請參閱<xref:System.IAppDomainSetup?displayProperty=nameWithType>如其屬性的詳細描述。  
  
 `IAppDomainSetup`表示可以加入的組件繫結資訊<xref:System.AppDomain>之前建立的執行個體。 例如，主機可以設定<xref:System.AppDomainSetup.ApplicationBase%2A>屬性，以建立根目錄，探查 common language runtime (CLR) managed 組件。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup>  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
