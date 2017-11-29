---
title: "ICLRRuntimeInfo 介面"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeInfo
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeInfo
helpviewer_keywords: ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 287e5ede-b3a7-4ef8-a756-4fca3f285a82
topic_type: apiref
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 86861ae1742cf520d1a5251c70a112b090ec429e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo 介面
提供方法，傳回特定 common language runtime (CLR) 的相關資訊包括版本、 目錄和負載狀態。 此介面也提供執行階段特有的功能，但沒有初始化執行階段。 其中包括執行階段相對[LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)方法中，執行階段模組專屬[GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)方法，並提供執行階段介面，透過[GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)方法。  
  
## <a name="methods"></a>方法  
  
|方法|說明|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)|將這個執行階段針對舊版 CLR 版本 2 的啟用原則決定所有的繫結。|  
|[GetDefaultStartupFlags 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getdefaultstartupflags-method.md)|取得 CLR 啟動旗標和主機組態檔。|  
|[GetInterface 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)|CLR 載入目前的處理序，並傳回執行階段介面指標，例如[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)， [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)和[IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)。 這個方法會取代所有`CorBindTo*`函式。|  
|[GetProcAddress 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)|取得指定的函式，此介面相關聯的 CLR 從匯出的位址。 這個方法會取代[GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)方法。|  
|[GetRuntimeDirectory 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)|取得此介面相關聯的 clr 安裝目錄。 這個方法會取代[GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)方法。|  
|[GetVersionString 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getversionstring-method.md)|取得 common language runtime (CLR) 版本資訊與相關給定[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面。 這個方法會取代[GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)和[GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)方法。|  
|[IsLoadable 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloadable-method.md)|表示此介面相關聯的執行階段是否可以載入目前的處理序不顧及其他執行階段，可能已經載入處理序。|  
|[IsLoaded 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloaded-method.md)|指出是否在 CLR 與相關聯[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面載入處理序。|  
|[IsStarted 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isstarted-method.md)|指出是否在 CLR 與相關聯[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面已啟動。|  
|[LoadErrorString 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loaderrorstring-method.md)|HRESULT 值轉譯為適當的錯誤訊息指定的文化特性。 這個方法會取代[LoadStringRC](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)和[LoadStringRCEx](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)方法。|  
|[LoadLibrary 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)|從 CLR 所代表的 framework 目錄中載入文件庫[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面。 這個方法會取代[LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)方法。|  
|[SetDefaultStartupFlags 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)|設定 CLR 啟動旗標和主機組態檔。|  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost.h  
  
 **程式庫：**包含做為 MSCorEE.dll 中的資源  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
