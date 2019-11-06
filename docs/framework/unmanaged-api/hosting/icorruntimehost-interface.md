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
ms.openlocfilehash: e66e1468a864ec85d88f759c481c7a9707d37f7e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139542"
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost 介面
提供的方法可讓主機明確啟動和停止 common language runtime （CLR）、建立和設定應用程式域、存取預設網域，以及列舉在進程中執行的所有網域。  
  
 在 .NET Framework 版本2.0 中，此介面已由[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)所取代。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[CloseEnum 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-closeenum-method.md)|將網域列舉值重設回定義域清單的開頭。|  
|[CreateDomain 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)|建立應用程式域。 呼叫端會接收類型的介面指標，<xref:System._AppDomain> 類型 <xref:System.AppDomain?displayProperty=nameWithType>的實例。|  
|[CreateDomainEx 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)|建立應用程式域。 這個方法可讓呼叫端傳遞 IAppDomainSetup 實例，以設定所傳回 <xref:System._AppDomain> 實例的其他功能。|  
|[CreateDomainSetup 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md)|取得 <xref:System.AppDomainSetup> 實例 `IAppDomainSetup` 類型的介面指標。 `IAppDomainSetup` 提供方法，在應用程式域建立之前設定其層面。|  
|[CreateEvidence 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md)|取得類型 <xref:System.Security.Principal.IIdentity>的介面指標，可讓主機建立要傳遞至[CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)或[CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md)的安全性辨識項。|  
|[CreateLogicalThreadState 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createlogicalthreadstate-method.md)|請勿使用。|  
|[CurrentDomain 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-currentdomain-method.md)|取得類型 <xref:System._AppDomain> 的介面指標，表示在目前線程上載入的網域。|  
|[DeleteLogicalThreadState 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-deletelogicalthreadstate-method.md)|請勿使用。|  
|[EnumDomains 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md)|取得目前進程中之定義域的列舉值。|  
|[GetConfiguration 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getconfiguration-method.md)|取得物件，讓主機指定 CLR 的回呼設定。|  
|[GetDefaultDomain 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-getdefaultdomain-method.md)|取得類型 <xref:System._AppDomain> 的介面指標，表示目前進程的預設網域。|  
|[LocksHeldByLogicalThread 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-locksheldbylogicalthread-method.md)|請勿使用。|  
|[MapFile 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-mapfile-method.md)|將指定的檔案對應到記憶體中。 這個方法已過時。|  
|[NextDomain 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-nextdomain-method.md)|取得列舉中下一個網域的介面指標。|  
|[Start 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-start-method.md)|啟動 CLR。|  
|[Stop 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-stop-method.md)|在執行時間中停止執行目前進程的程式碼。|  
|[SwitchInLogicalThreadState 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchinlogicalthreadstate-method.md)|請勿使用。|  
|[SwitchOutLogicalThreadState 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-switchoutlogicalthreadstate-method.md)|請勿使用。|  
|[UnloadDomain 方法](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-unloaddomain-method.md)|從目前的進程中卸載指定的應用程式域。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：** 1.0、1。1  
  
## <a name="see-also"></a>請參閱

- <xref:System.AppDomain>
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
- [ICLRRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [執行階段主應用程式](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
