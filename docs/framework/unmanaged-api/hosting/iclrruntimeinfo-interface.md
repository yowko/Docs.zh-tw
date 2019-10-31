---
title: ICLRRuntimeInfo 介面
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo
helpviewer_keywords:
- ICLRRuntimeInfo interface [.NET Framework hosting]
ms.assetid: 287e5ede-b3a7-4ef8-a756-4fca3f285a82
topic_type:
- apiref
ms.openlocfilehash: f6608b03df80fa37ebf5049b53bce46da3e155e0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120366"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo 介面
提供方法，傳回特定 common language runtime （CLR）的相關資訊，包括版本、目錄和載入狀態。 這個介面也會提供執行時間特有的功能，而不會初始化執行時間。 它包含執行時間相關的[LoadLibrary](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)方法、執行時間模組特定的[GetProcAddress](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)方法，以及執行時間提供的介面（透過[GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)方法）。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-bindaslegacyv2runtime-method.md)|針對所有舊版 CLR 第2版啟用原則決策系結此執行時間。|  
|[GetDefaultStartupFlags 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getdefaultstartupflags-method.md)|取得 CLR 啟動旗標和主機設定檔。|  
|[GetInterface 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md)|將 CLR 載入目前的進程，並傳回執行時間介面指標，例如[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)、 [ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)和[IMetaDataDispenser](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)。 這個方法會取代所有的 `CorBindTo*` 函數。|  
|[GetProcAddress 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getprocaddress-method.md)|取得指定函式的位址，該函式是從與這個介面相關聯的 CLR 所匯出。 這個方法會取代[GetRealProcAddress](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md)方法。|  
|[GetRuntimeDirectory 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)|取得與這個介面相關聯之 CLR 的安裝目錄。 這個方法會取代[GetCORSystemDirectory](../../../../docs/framework/unmanaged-api/hosting/getcorsystemdirectory-function.md)方法。|  
|[GetVersionString 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getversionstring-method.md)|取得與指定的[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面相關聯的 common language RUNTIME （CLR）版本資訊。 這個方法會取代[GetRequestedRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeinfo-function.md)和[GetRequestedRuntimeVersion](../../../../docs/framework/unmanaged-api/hosting/getrequestedruntimeversion-function.md)方法。|  
|[IsLoadable 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloadable-method.md)|指出與這個介面相關聯的執行時間是否可以載入目前的進程中，並考慮可能已經載入進程的其他執行時間。|  
|[IsLoaded 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isloaded-method.md)|指出與[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面相關聯的 CLR 是否已載入進程中。|  
|[IsStarted 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-isstarted-method.md)|指出是否已啟動與[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面相關聯的 CLR。|  
|[LoadErrorString 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loaderrorstring-method.md)|針對指定的文化特性，將 HRESULT 值轉譯為適當的錯誤訊息。 這個方法會取代[LoadStringRC](../../../../docs/framework/unmanaged-api/hosting/loadstringrc-function.md)和[LoadStringRCEx](../../../../docs/framework/unmanaged-api/hosting/loadstringrcex-function.md)方法。|  
|[LoadLibrary 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-loadlibrary-method.md)|從[ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)介面所代表之 CLR 的架構目錄載入程式庫。 這個方法會取代[LoadLibraryShim](../../../../docs/framework/unmanaged-api/hosting/loadlibraryshim-function.md)方法。|  
|[SetDefaultStartupFlags 方法](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-setdefaultstartupflags-method.md)|設定 CLR 啟動旗標和主機設定檔。|  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [裝載介面](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)
