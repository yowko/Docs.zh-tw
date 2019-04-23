---
title: ICorRuntimeHost 介面
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost
helpviewer_keywords:
- ICorRuntimeHost interface [.NET Framework hosting]
ms.assetid: 4369533d-7834-4497-bc37-bfea0ad737b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec893c898a6cd4abffd525056ed0d0169fcbb288
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59184778"
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost 介面
提供方法，讓主應用程式啟動，並明確地停止 common language runtime (CLR)，來建立及設定應用程式定義域，若要存取預設網域，並列舉處理序中執行的所有網域。  
  
 在.NET Framework 2.0 版中，此介面已被取代[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CloseEnum 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|將網域列舉值重設回網域清單的開頭。|  
|[CreateDomain 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|建立應用程式定義域。 呼叫端會收到類型的介面指標<xref:System._AppDomain>型別的執行個體<xref:System.AppDomain?displayProperty=nameWithType>。|  
|[CreateDomainEx 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|建立應用程式定義域。 這個方法可讓呼叫端傳遞 IAppDomainSetup 執行個體來設定傳回的其他功能<xref:System._AppDomain>執行個體。|  
|[CreateDomainSetup 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|取得類型的介面指標`IAppDomainSetup`至<xref:System.AppDomainSetup>執行個體。 `IAppDomainSetup` 提供方法來設定應用程式定義域的層面，才能建立。|  
|[CreateEvidence 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|取得類型的介面指標<xref:System.Security.Principal.IIdentity>，可讓主應用程式建立安全性辨識項，要傳遞給[CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)或是[CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)。|  
|[CreateLogicalThreadState 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|請勿使用。|  
|[CurrentDomain 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|取得類型的介面指標<xref:System._AppDomain>，代表目前執行緒上所載入的網域。|  
|[DeleteLogicalThreadState 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|請勿使用。|  
|[EnumDomains 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|取得目前的處理序中的網域列舉值。|  
|[GetConfiguration 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|取得物件，可讓主機指定的 clr 的回撥設定。|  
|[GetDefaultDomain 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|取得類型的介面指標<xref:System._AppDomain>，代表為目前的處理序的預設網域。|  
|[LocksHeldByLogicalThread 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|請勿使用。|  
|[MapFile 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|將指定的檔案對應到記憶體中。 這個方法已過時。|  
|[NextDomain 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|取得列舉型別中的下一個網域的介面指標。|  
|[Start 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|啟動 CLR。|  
|[Stop 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|停止目前的處理序的執行階段中的程式碼執行。|  
|[SwitchInLogicalThreadState 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|請勿使用。|  
|[SwitchOutLogicalThreadState 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|請勿使用。|  
|[UnloadDomain 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|卸載指定的應用程式定義域，從目前的處理序。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：** 1.0, 1.1  
  
## <a name="see-also"></a>另請參閱

- <xref:System.AppDomain>
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [執行階段主應用程式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
