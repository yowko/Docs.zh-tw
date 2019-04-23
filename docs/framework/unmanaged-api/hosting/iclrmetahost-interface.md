---
title: ICLRMetaHost 介面
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a1b189b79a02f04b7f795ff2524441f12b053cec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143945"
---
# <a name="iclrmetahost-interface"></a>ICLRMetaHost 介面
提供方法，傳回 common language runtime (CLR) 的特定版本，其版本號碼為基礎，列出所有已安裝的 Clr，清單中指定的處理序所載入的所有執行階段中，探索用來編譯組件、 結束處理程序的 CLR 版本與全新的執行階段關閉舊版 API 繫結的查詢。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[EnumerateInstalledRuntimes 方法](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateinstalledruntimes-method.md)|傳回包含有效的列舉[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)每個 CLR 版本安裝在電腦上的介面指標。|  
|[EnumerateLoadedRuntimes 方法](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-enumerateloadedruntimes-method.md)|傳回包含有效的列舉[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)載入指定的處理序中每個 CLR 的介面指標。 這個方法會取代[GetVersionFromProcess](../../../../docs/framework/unmanaged-api/hosting/getversionfromprocess-function.md)。|  
|[ExitProcess 方法](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-exitprocess-method.md)|嘗試先關閉所有已載入的執行階段依正常程序，然後終止處理序。 會取代[CorExitProcess](../../../../docs/framework/unmanaged-api/hosting/corexitprocess-function.md)函式。|  
|[GetRuntime 方法](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getruntime-method.md)|取得[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面會對應到特定的 CLR 版本。 這個方法會取代[CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)搭配使用函式[STARTUP_LOADER_SAFEMODE](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)旗標。|  
|[GetVersionFromFile 方法](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-getversionfromfile-method.md)|取得組件的原始.NET Framework 編譯版本 （儲存於中繼資料），提供其檔案路徑。 這個方法會取代[GetFileVersion](../../../../docs/framework/unmanaged-api/hosting/getfileversion-function.md)。|  
|[QueryLegacyV2RuntimeBinding 方法](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-querylegacyv2runtimebinding-method.md)|傳回代表舊版啟用原則具有已繫結至，例如使用執行階段介面`useLegacyV2RuntimeActivationPolicy`屬性[\<啟動 > 項目](../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)組態檔項目，直接使用舊版啟用的 Api，或藉由呼叫[ICLRRuntimeInfo::BindAsLegacyV2Runtime](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)方法。|  
|[RequestRuntimeLoadedNotification 方法](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-requestruntimeloadednotification-method.md)|第一次載入，但尚未開始的 CLR 版本時，可確保指定的函式指標的回呼。 這個方法會取代[LockClrVersion](../../../../docs/framework/unmanaged-api/hosting/lockclrversion-function.md)|  
  
## <a name="remarks"></a>備註  
 取得這個介面的執行個體的唯一方式是藉由呼叫[CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md)函式，如下所示：  
  
```  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **LIBRARY:** 包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
