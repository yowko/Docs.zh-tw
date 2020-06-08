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
ms.openlocfilehash: 71e2c7f6790f29872c051bb5cea50755068057e9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504039"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo 介面
提供方法，傳回特定 common language runtime （CLR）的相關資訊，包括版本、目錄和載入狀態。 這個介面也會提供執行時間特有的功能，而不會初始化執行時間。 它包含執行時間相關的[LoadLibrary](iclrruntimeinfo-loadlibrary-method.md)方法、執行時間模組特定的[GetProcAddress](iclrruntimeinfo-getprocaddress-method.md)方法，以及執行時間提供的介面（透過[GetInterface](iclrruntimeinfo-getinterface-method.md)方法）。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime 方法](iclrruntimeinfo-bindaslegacyv2runtime-method.md)|針對所有舊版 CLR 第2版啟用原則決策系結此執行時間。|  
|[GetDefaultStartupFlags 方法](iclrruntimeinfo-getdefaultstartupflags-method.md)|取得 CLR 啟動旗標和主機設定檔。|  
|[GetInterface 方法](iclrruntimeinfo-getinterface-method.md)|將 CLR 載入目前的進程，並傳回執行時間介面指標，例如[ICLRRuntimeHost](iclrruntimehost-interface.md)、 [ICLRStrongName](iclrstrongname-interface.md)和[IMetaDataDispenser](../metadata/imetadatadispenser-interface.md)。 這個方法會取代所有 `CorBindTo*` 函數。|  
|[GetProcAddress 方法](iclrruntimeinfo-getprocaddress-method.md)|取得指定函式的位址，該函式是從與這個介面相關聯的 CLR 所匯出。 這個方法會取代[GetRealProcAddress](getrealprocaddress-function.md)方法。|  
|[GetRuntimeDirectory 方法](iclrruntimeinfo-getruntimedirectory-method.md)|取得與這個介面相關聯之 CLR 的安裝目錄。 這個方法會取代[GetCORSystemDirectory](getcorsystemdirectory-function.md)方法。|  
|[GetVersionString 方法](iclrruntimeinfo-getversionstring-method.md)|取得與指定的[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)介面相關聯的 common language RUNTIME （CLR）版本資訊。 這個方法會取代[GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md)和[GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md)方法。|  
|[IsLoadable 方法](iclrruntimeinfo-isloadable-method.md)|指出與這個介面相關聯的執行時間是否可以載入目前的進程中，並考慮可能已經載入進程的其他執行時間。|  
|[IsLoaded 方法](iclrruntimeinfo-isloaded-method.md)|指出與[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)介面相關聯的 CLR 是否已載入進程中。|  
|[IsStarted 方法](iclrruntimeinfo-isstarted-method.md)|指出是否已啟動與[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)介面相關聯的 CLR。|  
|[LoadErrorString 方法](iclrruntimeinfo-loaderrorstring-method.md)|針對指定的文化特性，將 HRESULT 值轉譯為適當的錯誤訊息。 這個方法會取代[LoadStringRC](loadstringrc-function.md)和[LoadStringRCEx](loadstringrcex-function.md)方法。|  
|[LoadLibrary 方法](iclrruntimeinfo-loadlibrary-method.md)|從[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)介面所代表之 CLR 的架構目錄載入程式庫。 這個方法會取代[LoadLibraryShim](loadlibraryshim-function.md)方法。|  
|[SetDefaultStartupFlags 方法](iclrruntimeinfo-setdefaultstartupflags-method.md)|設定 CLR 啟動旗標和主機設定檔。|  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結**庫：** 包含為 Mscoree.dll 中的資源  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](hosting-interfaces.md)
- [Hosting](index.md)
