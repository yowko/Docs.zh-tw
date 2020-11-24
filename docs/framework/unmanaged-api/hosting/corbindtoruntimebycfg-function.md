---
title: CorBindToRuntimeByCfg 函式
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeByCfg
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeByCfg
helpviewer_keywords:
- CorBindToRuntimeByCfg function [.NET Framework hosting]
ms.assetid: ded1e492-a782-4185-9c66-709e421c1782
topic_type:
- apiref
ms.openlocfilehash: d319382b577844a804c3e4562676491a15de5f63
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673770"
---
# <a name="corbindtoruntimebycfg-function"></a>CorBindToRuntimeByCfg 函式

使用從 XML 檔案讀取的版本資訊，將 common language runtime (CLR) 載入處理常式。  
  
 此函式已在 .NET Framework 4 中被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CorBindToRuntimeByCfg (  
    [in]  IStream     *pCfgStream,  
    [in]  DWORD        reserved,  
    [in]  DWORD        startupFlags,  
    [in]  REFCLSID     rclsid,  
    [in]  REFIID       riid,
    [out] LPVOID FAR*  ppv  
);  
```  
  
## <a name="parameters"></a>參數  

 `pCfgStream`  
 在 `IStream` 物件的指標，該物件會讀取 XML 檔案。  
  
 `reserved`  
 在保留供日後使用。 使用 0 (零) 作為值。  
  
 `startupFlags`  
 在 [STARTUP_FLAGS](startup-flags-enumeration.md) 列舉值，指定 CLR 的啟動行為。  
  
 `rclsid`  
 在Coclass 的， `CLSID` 可執行 [ICorRuntimeHost](icorruntimehost-interface.md) 或 [ICLRRuntimeHost](iclrruntimehost-interface.md) 介面。 支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。  
  
 `riid`  
 在 `IID` `ICorRuntimeHost` 或 `ICLRRuntimeHost` 介面的。 支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。  
  
 `ppv`  
 擴展傳回之介面的位址指標。  
  
## <a name="remarks"></a>備註  

 XML 檔案的格式是在標準應用程式佈建檔之後進行模型化。 如需 XML 檔案的詳細資訊，請參閱 [設定檔案架構](../../configure-apps/file-schema/index.md)。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CorBindToCurrentRuntime 函式](corbindtocurrentruntime-function.md)
- [CorBindToRuntime 函式](corbindtoruntime-function.md)
- [CorBindToRuntimeEx 函式](corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost 函式](corbindtoruntimehost-function.md)
- [ICorRuntimeHost 介面](icorruntimehost-interface.md)
- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
