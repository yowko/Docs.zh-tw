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
ms.openlocfilehash: 4c015d77deb4e6ed3d43074f2903e26b687de84f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493561"
---
# <a name="corbindtocurrentruntime-function"></a>CorBindToCurrentRuntime 函式
使用儲存在 XML 檔案中的版本資訊，將 common language runtime （CLR）載入進程中。 XML 檔案的格式會在標準應用程式佈建檔案之後進行模型化。 如需組態檔的詳細資訊，請參閱[組態檔結構描述](../../configure-apps/file-schema/index.md)。  
  
 此函式在 .NET Framework 4 中已被取代。 請參閱將[Common Language Runtime 載入進程中](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/01918c6x(v=vs.100))。  
  
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
 在應用程式佈建檔的名稱，指定要載入的 CLR 版本。 如果檔案名不是完整名稱，則會假設為與呼叫相同的目錄。  
  
 要載入的執行階段版本，會由設定檔的元素中的 version 屬性描述 [\<requiredRuntime>](../../configure-apps/file-schema/startup/requiredruntime-element.md) 。  
  
 如果未指定任何版本，或找不到該專案，則會 `<requiredRuntime>` 載入電腦上所安裝的最新 CLR 版本。  
  
 `rclsid`  
 在Coclass 的，其 `CLSID` 會執行[ICorRuntimeHost](icorruntimehost-interface.md)或[ICLRRuntimeHost](iclrruntimehost-interface.md)介面。 支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。  
  
 `riid`  
 在`IID`您所要求之介面的。 支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。  
  
 `ppv`  
 脫銷傳回的介面指標。  
  
## <a name="requirements"></a>規格需求  
 **平台：** 請參閱[系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CorBindToRuntime 函式](corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg 函式](corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx 函式](corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost 函式](corbindtoruntimehost-function.md)
- [ICorRuntimeHost 介面](icorruntimehost-interface.md)
- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
