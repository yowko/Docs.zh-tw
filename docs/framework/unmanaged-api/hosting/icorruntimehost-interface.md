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
ms.openlocfilehash: 420f22a242a20f8bdf5d5b84f47a297a2f503db0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90546017"
---
# <a name="icorruntimehost-interface"></a>ICorRuntimeHost 介面
提供的方法可讓主機明確地啟動及停止 common language runtime (CLR) 、建立和設定應用程式域、存取預設網域，以及列舉在進程中執行的所有網域。  
  
 在 .NET Framework 2.0 版中，此介面會被 [ICLRRuntimeHost](iclrruntimehost-interface.md)取代。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[CloseEnum 方法](icorruntimehost-closeenum-method.md)|將網域列舉值重設回定義域清單的開頭。|  
|[CreateDomain 方法](icorruntimehost-createdomain-method.md)|建立應用程式域。 呼叫端會收到型別實例的型別介面指標 <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> 。|  
|[CreateDomainEx 方法](icorruntimehost-createdomainex-method.md)|建立應用程式域。 這個方法可讓呼叫端傳遞 IAppDomainSetup 實例，以設定所傳回實例的額外功能 <xref:System._AppDomain> 。|  
|[CreateDomainSetup 方法](icorruntimehost-createdomainsetup-method.md)|取得實例的型別介面指標 `IAppDomainSetup` <xref:System.AppDomainSetup> 。 `IAppDomainSetup` 提供方法來設定應用程式域在建立之前的各個層面。|  
|[CreateEvidence 方法](icorruntimehost-createevidence-method.md)|取得型別的介面指標 <xref:System.Security.Principal.IIdentity> ，可讓主機建立安全性辨識項以傳遞至 [CreateDomain](icorruntimehost-createdomain-method.md) 或 [CreateDomainEx](icorruntimehost-createdomainex-method.md)。|  
|[CreateLogicalThreadState 方法](icorruntimehost-createlogicalthreadstate-method.md)|請勿使用。|  
|[CurrentDomain 方法](icorruntimehost-currentdomain-method.md)|取得型別的介面指標 <xref:System._AppDomain> ，代表在目前線程上載入的網域。|  
|[DeleteLogicalThreadState 方法](icorruntimehost-deletelogicalthreadstate-method.md)|請勿使用。|  
|[EnumDomains 方法](icorruntimehost-enumdomains-method.md)|取得目前進程中之定義域的列舉值。|  
|[GetConfiguration 方法](icorruntimehost-getconfiguration-method.md)|取得物件，這個物件可讓主機指定 CLR 的回呼設定。|  
|[GetDefaultDomain 方法](icorruntimehost-getdefaultdomain-method.md)|取得型別的介面指標 <xref:System._AppDomain> ，表示目前進程的預設網域。|  
|[LocksHeldByLogicalThread 方法](icorruntimehost-locksheldbylogicalthread-method.md)|請勿使用。|  
|[MapFile 方法](icorruntimehost-mapfile-method.md)|將指定的檔案對應到記憶體。 這個方法已過時。|  
|[NextDomain 方法](icorruntimehost-nextdomain-method.md)|取得列舉中下一個網域的介面指標。|  
|[Start 方法](icorruntimehost-start-method.md)|啟動 CLR。|  
|[Stop 方法](icorruntimehost-stop-method.md)|停止執行時間中目前進程的程式碼執行。|  
|[SwitchInLogicalThreadState 方法](icorruntimehost-switchinlogicalthreadstate-method.md)|請勿使用。|  
|[SwitchOutLogicalThreadState 方法](icorruntimehost-switchoutlogicalthreadstate-method.md)|請勿使用。|  
|[UnloadDomain 方法](icorruntimehost-unloaddomain-method.md)|從目前的進程卸載指定的應用程式域。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結**庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：** 1.0、1。1  
  
## <a name="see-also"></a>另請參閱

- <xref:System.AppDomain>
- [Hosting](index.md)
- [ICLRRuntimeHost 介面](iclrruntimehost-interface.md)
- [執行階段主應用程式](/previous-versions/dotnet/netframework-4.0/a51xd4ze(v=vs.100))
- [裝載介面](hosting-interfaces.md)
- [CorRuntimeHost Coclass](corruntimehost-coclass.md)
