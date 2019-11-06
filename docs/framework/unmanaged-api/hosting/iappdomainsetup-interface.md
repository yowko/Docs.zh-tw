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
ms.openlocfilehash: 0fab64c31d4a73995c16d21767f4569f21c7df9a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126865"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup 介面
提供可讓主機設定 <xref:System.AppDomain?displayProperty=nameWithType> 類型的屬性，然後再呼叫[ICorRuntimeHost：： CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)方法來建立它。  
  
## <a name="properties"></a>內容  
  
|屬性|描述|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|取得或設定包含應用程式的目錄名稱。|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|取得或設定應用程式的名稱。|  
|<xref:System.AppDomainSetup.CachePath%2A>|取得或設定應用程式特定的區功能變數名稱稱，其中會遮蔽檔案的陰影複製位置。|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|取得或設定應用程式的設定檔案名稱。|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|取得或設定用來儲存和存取動態產生的檔案之目錄的名稱。|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|取得或設定與此網域相關聯之授權檔案的路徑。|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|取得或設定與 <xref:System.AppDomainSetup.ApplicationBase%2A> 目錄結合的目錄清單，以探查私用元件。|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|取得或設定字串值，其中包含或排除來自應用程式搜尋路徑的 <xref:System.AppDomainSetup.ApplicationBase%2A>。|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|取得或設定包含要陰影複製之元件的目錄名稱。|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|取得或設定字串，指出陰影複製是否開啟或關閉。 有效的值為 "true" 或 "false"。|  
  
## <a name="remarks"></a>備註  
 `IAppDomainSetup` 介面會對應到 <xref:System.AppDomainSetup> 類型所執行的 managed <xref:System.IAppDomainSetup> 介面。 如需其屬性的詳細說明，請參閱 <xref:System.IAppDomainSetup?displayProperty=nameWithType>。  
  
 `IAppDomainSetup` 代表元件系結資訊，可以在建立之前加入至 <xref:System.AppDomain> 實例。 例如，主控制項可以設定 <xref:System.AppDomainSetup.ApplicationBase%2A> 屬性，以建立根目錄，而 common language runtime （CLR）會探查 managed 元件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
