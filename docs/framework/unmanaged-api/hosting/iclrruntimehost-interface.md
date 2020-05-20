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
ms.openlocfilehash: dd1aa4089a981d82ae1403189343694a065a701d
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703659"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost 介面
提供的功能類似于 .NET Framework 第1版所提供的[ICorRuntimeHost](icorruntimehost-interface.md)介面，但有下列變更：  
  
- 新增[SetHostControl](iclrruntimehost-sethostcontrol-method.md)方法以設定主控制項介面。  
  
- 省略所提供的一些方法 `ICorRuntimeHost` 。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[ExecuteApplication 方法](iclrruntimehost-executeapplication-method.md)|在以資訊清單為基礎的 ClickOnce 部署案例中使用，以指定要在新的網域中啟動的應用程式。|  
|[ExecuteInAppDomain 方法](iclrruntimehost-executeinappdomain-method.md)|指定 <xref:System.AppDomain> 要在其中執行指定 managed 程式碼的。|  
|[ExecuteInDefaultAppDomain 方法](iclrruntimehost-executeindefaultappdomain-method.md)|在指定的元件中，叫用指定之類型的指定方法。|  
|[GetCLRControl 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|取得類型[ICLRControl](iclrcontrol-interface.md)的介面指標，可供裝載用來自訂 common language RUNTIME （CLR）的各個層面。|  
|[GetCurrentAppDomainId 方法](iclrruntimehost-getcurrentappdomainid-method.md)|取得目前正在執行之的數值識別碼 <xref:System.AppDomain> 。|  
|[SetHostControl 方法](iclrruntimehost-sethostcontrol-method.md)|設定主控制項介面。 呼叫之前，您必須 `SetHostControl` 先呼叫 `Start` 。|  
|[Start 方法](iclrruntimehost-start-method.md)|將 CLR 初始化為進程。|  
|[Stop 方法](iclrruntimehost-stop-method.md)|停止執行時間的程式碼執行。|  
|[UnloadAppDomain 方法](iclrruntimehost-unloadappdomain-method.md)|卸載 <xref:System.AppDomain> 對應于指定之數位識別碼的。|  
  
## <a name="remarks"></a>備註  
 從 .NET Framework 4 開始，請使用[ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)介面來取得[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面的指標，然後呼叫[ICLRRuntimeInfo：： GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)方法來取得的指標 `ICLRRuntimeHost` 。 在舊版的 .NET Framework 中，主機會藉 `ICLRRuntimeHost` 由呼叫[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)或[CorBindToCurrentRuntime](corbindtocurrentruntime-function.md)取得實例的指標。 若要提供 .NET Framework 版本2.0 中所提供的任何技術的執行，您必須使用， `ICLRRuntimeHost` 而不是 `ICorRuntimeHost` 。  
  
> [!IMPORTANT]
> 在呼叫[ExecuteApplication](iclrruntimehost-executeapplication-method.md)方法來啟動以資訊清單為基礎的應用程式之前，請不要呼叫[Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)方法。 如果 `Start` 先呼叫方法， `ExecuteApplication` 方法呼叫將會失敗。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CorBindToCurrentRuntime 函式](corbindtocurrentruntime-function.md)
- [CorBindToRuntimeEx 函式](corbindtoruntimeex-function.md)
- [ICLRControl 介面](iclrcontrol-interface.md)
- [ICorRuntimeHost 介面](icorruntimehost-interface.md)
- [裝載介面](hosting-interfaces.md)
- [CLRRuntimeHost Coclass](clrruntimehost-coclass.md)
