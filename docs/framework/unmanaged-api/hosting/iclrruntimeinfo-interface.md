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
ms.openlocfilehash: 9f485728ddb050abf815bf8ba26c69be9c909785
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714966"
---
# <a name="iclrruntimeinfo-interface"></a>ICLRRuntimeInfo 介面

提供方法，以傳回特定 common language runtime (CLR) 的相關資訊，包括版本、目錄和載入狀態。 這個介面也提供執行時間專屬的功能，而不需要初始化執行時間。 它包含執行時間相關的 [LoadLibrary](iclrruntimeinfo-loadlibrary-method.md) 方法、執行時間模組特定的 [GetProcAddress](iclrruntimeinfo-getprocaddress-method.md) 方法，以及透過 [GetInterface](iclrruntimeinfo-getinterface-method.md) 方法提供的執行時間介面。  
  
## <a name="methods"></a>方法  
  
|方法|描述|  
|------------|-----------------|  
|[BindAsLegacyV2Runtime 方法](iclrruntimeinfo-bindaslegacyv2runtime-method.md)|將此執行時間系結到所有舊版 CLR 第2版啟用原則決策。|  
|[GetDefaultStartupFlags 方法](iclrruntimeinfo-getdefaultstartupflags-method.md)|取得 CLR 啟動旗標和主機設定檔案。|  
|[GetInterface 方法](iclrruntimeinfo-getinterface-method.md)|將 CLR 載入目前的進程，並傳回執行時間介面指標，例如 [ICLRRuntimeHost](iclrruntimehost-interface.md)、 [ICLRStrongName](iclrstrongname-interface.md) 和 [IMetaDataDispenser](../metadata/imetadatadispenser-interface.md)。 這個方法會取代所有的函式 `CorBindTo*` 。|  
|[GetProcAddress 方法](iclrruntimeinfo-getprocaddress-method.md)|取得從與這個介面相關聯的 CLR 匯出之指定函式的位址。 這個方法會取代 [GetRealProcAddress](getrealprocaddress-function.md) 方法。|  
|[GetRuntimeDirectory 方法](iclrruntimeinfo-getruntimedirectory-method.md)|取得與此介面相關聯之 CLR 的安裝目錄。 這個方法會取代 [GetCORSystemDirectory](getcorsystemdirectory-function.md) 方法。|  
|[GetVersionString 方法](iclrruntimeinfo-getversionstring-method.md)|取得與給定 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面相關聯的 common language RUNTIME (CLR) 版本資訊。 這個方法會取代 [GetRequestedRuntimeInfo](getrequestedruntimeinfo-function.md) 和 [GetRequestedRuntimeVersion](getrequestedruntimeversion-function.md) 方法。|  
|[IsLoadable 方法](iclrruntimeinfo-isloadable-method.md)|指出與這個介面相關聯的執行時間是否可以載入至目前的進程，並將可能已載入至進程的其他執行時間納入考慮。|  
|[IsLoaded 方法](iclrruntimeinfo-isloaded-method.md)|指出與 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面相關聯的 CLR 是否會載入至進程。|  
|[IsStarted 方法](iclrruntimeinfo-isstarted-method.md)|指出與 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面相關聯的 CLR 是否已啟動。|  
|[LoadErrorString 方法](iclrruntimeinfo-loaderrorstring-method.md)|針對指定的文化特性，將 HRESULT 值轉譯為適當的錯誤訊息。 這個方法會取代 [LoadStringRC](loadstringrc-function.md) 和 [LoadStringRCEx](loadstringrcex-function.md) 方法。|  
|[LoadLibrary 方法](iclrruntimeinfo-loadlibrary-method.md)|從 [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) 介面所代表之 CLR 的 framework 目錄載入程式庫。 這個方法會取代 [LoadLibraryShim](loadlibraryshim-function.md) 方法。|  
|[SetDefaultStartupFlags 方法](iclrruntimeinfo-setdefaultstartupflags-method.md)|設定 CLR 啟動旗標和主機設定檔案。|  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** MetaHost。h  
  
 連結 **庫：** 以資源的形式包含在 MSCorEE.dll 中  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [裝載介面](hosting-interfaces.md)
- [裝載](index.md)
