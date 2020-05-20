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
ms.openlocfilehash: 1726f8929404e0dde979972d7830a6951dd71891
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617057"
---
# <a name="iappdomainsetup-interface"></a>IAppDomainSetup 介面
提供的屬性可讓主機在 <xref:System.AppDomain?displayProperty=nameWithType> 呼叫[ICorRuntimeHost：： CreateDomainEx](icorruntimehost-createdomainex-method.md)方法來建立類型之前，先設定型別。  
  
## <a name="properties"></a>屬性  
  
|屬性|說明|  
|--------------|-----------------|  
|<xref:System.AppDomainSetup.ApplicationBase%2A>|取得或設定包含應用程式的目錄名稱。|  
|<xref:System.AppDomainSetup.ApplicationName%2A>|取得或設定應用程式的名稱。|  
|<xref:System.AppDomainSetup.CachePath%2A>|取得或設定應用程式特定的區功能變數名稱稱，其中會遮蔽檔案的陰影複製位置。|  
|<xref:System.AppDomainSetup.ConfigurationFile%2A>|取得或設定應用程式的設定檔案名稱。|  
|<xref:System.AppDomainSetup.DynamicBase%2A>|取得或設定用來儲存和存取動態產生的檔案之目錄的名稱。|  
|<xref:System.AppDomainSetup.LicenseFile%2A>|取得或設定與此網域相關聯之授權檔案的路徑。|  
|<xref:System.AppDomainSetup.PrivateBinPath%2A>|取得或設定目錄的清單，並結合 <xref:System.AppDomainSetup.ApplicationBase%2A> 目錄來探查私用元件。|  
|<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>|取得或設定字串值，其中包含或排除 <xref:System.AppDomainSetup.ApplicationBase%2A> 應用程式的搜尋路徑。|  
|<xref:System.AppDomainSetup.ShadowCopyDirectories%2A>|取得或設定包含要陰影複製之元件的目錄名稱。|  
|<xref:System.AppDomainSetup.ShadowCopyFiles%2A>|取得或設定字串，指出陰影複製是否開啟或關閉。 有效的值為 "true" 或 "false"。|  
  
## <a name="remarks"></a>備註  
 `IAppDomainSetup`介面會對應到類型所執行的 managed <xref:System.IAppDomainSetup> 介面 <xref:System.AppDomainSetup> 。 <xref:System.IAppDomainSetup?displayProperty=nameWithType>如需其屬性的詳細說明，請參閱。  
  
 `IAppDomainSetup`表示元件系結資訊，可以在 <xref:System.AppDomain> 建立之前加入至實例。 例如，主控制項可以設定屬性， <xref:System.AppDomainSetup.ApplicationBase%2A> 以建立根目錄，而通用語言執行時間（CLR）會探查 managed 元件。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup>
- [裝載介面](hosting-interfaces.md)
