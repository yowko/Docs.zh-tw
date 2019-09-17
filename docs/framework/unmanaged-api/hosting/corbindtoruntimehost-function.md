---
title: CorBindToRuntimeHost 函式
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeHost
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeHost
helpviewer_keywords:
- CorBindToRuntimeHost function [.NET Framework hosting]
ms.assetid: 5c826ba3-8258-49bc-a417-78807915fcaf
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e1965917e8a1c5ae07cf119df3664b969a979be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969243"
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost 函式
讓主機將指定版本的 common language runtime （CLR）載入進程中。  
  
 此函式在 .NET Framework 4 中已被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CorBindToRuntimeHost (  
    [in] LPCWSTR       pwszVersion,   
    [in] LPCWSTR       pwszBuildFlavor,   
    [in] LPCWSTR       pwszHostConfigFile,   
    [in] VOID*         pReserved,   
    [in] DWORD         startupFlags,   
    [in] REFCLSID      rclsid,   
    [in] REFIID        riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a>參數  
 `pwszVersion`  
 在描述您要載入之 CLR 版本的字串。  
  
 .NET Framework 中的版本號碼包含四個以句點分隔的部分： [主要]. [*次要. 組建. 修訂*]。 傳遞為`pwszVersion`的字串必須以字元 "v" 開頭，後面接著版本號碼的前三個部分（例如 "v 1.0.1529"）。  
  
 某些 CLR 版本會與原則語句一起安裝，以指定與舊版 CLR 的相容性。 根據預設，啟動填充碼會`pwszVersion`針對原則語句評估，並載入與所要求版本相容的最新執行階段版本。 主機可以強制填充碼略過原則評估，並藉`pwszVersion`由傳遞`startupFlags`參數的 STARTUP_LOADER_SAFEMODE 值來載入所指定的確切版本。  
  
 如果`pwszVersion` 是`null,` ，則方法不會載入任何版本的 CLR。 相反地，它會傳回 CLR_E_SHIM_RUNTIMELOAD，這表示它無法載入執行時間。  
  
 `pwszBuildFlavor`  
 在字串，指定是否要載入伺服器或 CLR 的工作站組建。 有效值為 `svr` 和 `wks`。 伺服器組建已優化，可利用多個處理器進行垃圾收集，而且工作站組建已針對在單處理器機器上執行的用戶端應用程式優化。  
  
 如果`pwszBuildFlavor`設定為 null，則會載入工作站組建。 在單處理器機器上執行時，一律會載入工作站組建，即使設定為`pwszBuildFlavor` `svr`也一樣。 不過，如果`pwszBuildFlavor`設定為`svr` ，且指定了並行垃圾收集（ `startupFlags`請參閱參數的描述），則會載入伺服器組建。  
  
> [!NOTE]
> 在執行 Intel Itanium 架構（先前稱為 IA-64）的64位系統上執行 WOW64 x86 模擬器的應用程式不支援並行垃圾收集。 如需在64位 Windows 系統上使用 WOW64 的詳細資訊，請參閱執行[32 位應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。  
  
 `pwszHostConfigFile`  
 在主機設定檔的名稱，指定要載入的 CLR 版本。 如果檔案名不包含完整路徑，則會假設檔案與進行呼叫的可執行檔位於相同的目錄中。  
  
 `pReserved`  
 在保留以供未來擴充性之用。  
  
 `startupFlags`  
 在一組旗標，可控制並行垃圾收集、網域中性程式碼，以及`pwszVersion`參數的行為。 如果未設定旗標，則預設值為單一網域。 如需支援值的清單，請參閱[STARTUP_FLAGS 列舉](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)。  
  
 `rclsid`  
 在Coclass 的，其會執行 [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) 或 [ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md) 介面。`CLSID` 支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。  
  
 `riid`  
 在您所要求之介面的。 `IID` 支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。  
  
 `ppv`  
 脫銷載入的執行階段版本的介面指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.idl  
  
 **LIBRARY:** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CorBindToCurrentRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
