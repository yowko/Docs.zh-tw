---
title: ICLRRuntimeHost 介面
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed32fe643a7722eaf1af38e6079096194690e950
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771887"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost 介面
提供的功能類似於[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) .NET Framework 第 1 版，以下列變更所提供的介面：  
  
- 新增[SetHostControl](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)來設定主應用程式控制項介面的方法。  
  
- 略過其中所提供的一些方法`ICorRuntimeHost`。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ExecuteApplication 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|用於以指定要啟動新的網域中的應用程式的資訊清單為基礎的 ClickOnce 部署案例。|  
|[ExecuteInAppDomain 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|指定<xref:System.AppDomain>要執行指定的 managed 程式碼。|  
|[ExecuteInDefaultAppDomain 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|叫用指定的型別，指定的組件中的指定的方法。|  
|[GetCLRControl 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|取得類型的介面指標[ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)主機可用於自訂的 common language runtime (CLR) 的層面。|  
|[GetCurrentAppDomainId 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|取得的數值識別碼<xref:System.AppDomain>，目前正在執行。|  
|[SetHostControl 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|設定主控件控制介面。 您必須呼叫`SetHostControl`再呼叫`Start`。|  
|[Start 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|初始化 CLR 程序。|  
|[Stop 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|執行階段中停止執行程式碼。|  
|[UnloadAppDomain 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|卸載<xref:System.AppDomain>，其對應於指定的數值識別碼。|  
  
## <a name="remarks"></a>備註  
 開頭[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]，使用[ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)介面，以取得的指標[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面，並接著呼叫[iclrruntimeinfo:: Getinterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)方法來取得變數的指標， `ICLRRuntimeHost`。 在舊版的.NET Framework 中，主應用程式取得的指標`ICLRRuntimeHost`藉由呼叫的執行個體[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或是[CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)。 若要提供的任何.NET Framework 2.0 版中提供的技術實作，您必須使用`ICLRRuntimeHost`而不是`ICorRuntimeHost`。  
  
> [!IMPORTANT]
>  請勿呼叫[開始](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法，再呼叫[ExecuteApplication](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)方法，以啟用資訊清單為基礎的應用程式。 如果`Start`首先，呼叫方法`ExecuteApplication`方法呼叫將會失敗。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CorBindToCurrentRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeEx 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICLRControl 介面](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CLRRuntimeHost Coclass](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
