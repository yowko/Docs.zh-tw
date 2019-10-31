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
ms.openlocfilehash: 3802354bf52cd2aab2a4149d565993b9965e8312
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138292"
---
# <a name="corbindtoruntimebycfg-function"></a>CorBindToRuntimeByCfg 函式
使用從 XML 檔案讀取的版本資訊，將 common language runtime （CLR）載入進程中。  
  
 此函式在 .NET Framework 4 中已被取代。  
  
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
 在讀取 XML 檔案之 `IStream` 物件的指標。  
  
 `reserved`  
 在保留供日後使用。 使用0（零）作為值。  
  
 `startupFlags`  
 在[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列舉的值，指定 CLR 的啟動行為。  
  
 `rclsid`  
 在執行[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面之 coclass 的 `CLSID`。 支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。  
  
 `riid`  
 在`ICorRuntimeHost` 或 `ICLRRuntimeHost` 介面的 `IID`。 支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。  
  
 `ppv`  
 脫銷傳回之介面位址的指標。  
  
## <a name="remarks"></a>備註  
 XML 檔案的格式會在標準應用程式佈建檔案之後進行模型化。 如需 XML 檔案的詳細資訊，請參閱[設定檔案架構](../../../../docs/framework/configure-apps/file-schema/index.md)。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [CorBindToCurrentRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeEx 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
