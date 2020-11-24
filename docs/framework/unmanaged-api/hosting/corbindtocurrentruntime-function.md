---
title: CorBindToCurrentRuntime 函式
ms.date: 03/30/2017
api_name:
- CorBindToCurrentRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- HeaderDef
f1_keywords:
- CorBindToCurrentRuntime
helpviewer_keywords:
- CorBindToCurrentRuntime function [.NET Framework hosting]
ms.assetid: 6105c13e-d9cd-44d2-a95a-924e042830c7
topic_type:
- apiref
ms.openlocfilehash: 4a8ab6e1aeedef5b821fc977387b8039f54edd64
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95682493"
---
# <a name="corbindtocurrentruntime-function"></a>CorBindToCurrentRuntime 函式

使用儲存在 XML 檔案中的版本資訊，將 common language runtime (CLR) 載入至進程。 XML 檔案的格式是在標準應用程式佈建檔之後進行模型化。 如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../configure-apps/file-schema/index.md)。  
  
 此函式已在 .NET Framework 4 中被取代。 請參閱將 [Common Language Runtime 載入至進程](/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100))。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CorBindToCurrentRuntime (  
    [in]  LPCWSTR   pwszFileName,  
    [in]  REFCLSID  rclsid,  
    [in]  REFIID    riid,  
    [out] LPVOID    *ppv  
);  
```  
  
## <a name="parameters"></a>參數  

 `pwszFileName`  
 在應用程式佈建檔的名稱，指定要載入的 CLR 版本。 如果檔案名不是完整名稱，則會假設該名稱與可執行檔的可執行檔位於相同的目錄中。  
  
 設定檔元素中的 version 屬性會描述要載入的執行階段版本 [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) 。  
  
 如果未指定任何版本，或如果找不到專案，則會 `<requiredRuntime>` 載入電腦上所安裝之最新版本的 CLR。  
  
 `rclsid`  
 在Coclass 的， `CLSID` 可執行 [ICorRuntimeHost](icorruntimehost-interface.md) 或 [ICLRRuntimeHost](iclrruntimehost-interface.md) 介面。 支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。  
  
 `riid`  
 在 `IID` 您所要求之介面的。 支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。  
  
 `ppv`  
 擴展傳回的介面指標。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CorBindToRuntime 函式](corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg 函式](corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx 函式](corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost 函式](corbindtoruntimehost-function.md)
- [ICorRuntimeHost 介面](icorruntimehost-interface.md)
- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
