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
ms.openlocfilehash: 7ba35823ccb670ad0201d1950687dc83cc9ba64a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673732"
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost 函式

讓主機將指定版本的 common language runtime (CLR) 載入至進程。  
  
 此函式已在 .NET Framework 4 中被取代。  
  
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
 在字串，描述您想要載入的 CLR 版本。  
  
 .NET Framework 中的版本號碼包含四個以句號分隔的部分： *主要.*...............。 傳遞的字串 `pwszVersion` 必須以字元 "v" 開頭，後面接著第三個版本號碼部分 (例如 "v 1.0.1529" ) 。  
  
 某些版本的 CLR 會與指定 CLR 舊版相容性的原則語句一起安裝。 根據預設，啟動填充碼 `pwszVersion` 會針對原則語句進行評估，並載入與所要求版本相容的最新執行階段版本。 主機可以強制填充碼略過原則評估，並藉 `pwszVersion` 由傳遞參數的 STARTUP_LOADER_SAFEMODE 值來載入指定的精確版本 `startupFlags` 。  
  
 如果 `pwszVersion` 為， `null,` 則方法不會載入任何版本的 CLR。 相反地，它會傳回 CLR_E_SHIM_RUNTIMELOAD，這表示它無法載入執行時間。  
  
 `pwszBuildFlavor`  
 在字串，指定是否要載入伺服器或 CLR 的工作站組建。 有效值為 `svr` 和 `wks`。 伺服器組建經過優化，可利用多個處理器進行垃圾收集，而且工作站組建已針對在單處理器電腦上執行的用戶端應用程式優化。  
  
 如果 `pwszBuildFlavor` 設定為 null，就會載入工作站組建。 在單處理器電腦上執行時，一律會載入工作站組建，即使 `pwszBuildFlavor` 設定為 `svr` 。 但是，如果 `pwszBuildFlavor` 設定為 `svr` ，而且指定了並行垃圾收集 (請參閱 `startupFlags`) 的參數描述，就會載入伺服器組建。  
  
> [!NOTE]
> 在64位系統上執行 WOW64 x86 模擬器的應用程式不支援並行垃圾收集，這些系統會執行先前稱為 IA-64) 的 Intel Itanium 架構 (。 如需在64位 Windows 系統上使用 WOW64 的詳細資訊，請參閱執行 [32 位應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。  
  
 `pwszHostConfigFile`  
 在主機設定檔的名稱，指定要載入的 CLR 版本。 如果檔案名不包含完整路徑，則會假設檔案與進行呼叫的可執行檔位於相同的目錄中。  
  
 `pReserved`  
 在保留供未來擴充性之用。  
  
 `startupFlags`  
 在一組旗標，可控制並行垃圾收集、定義域中性程式碼，以及參數的行為 `pwszVersion` 。 如果未設定任何旗標，則預設為單一網域。 如需支援值的清單，請參閱 [STARTUP_FLAGS 列舉](startup-flags-enumeration.md)。  
  
 `rclsid`  
 在Coclass 的， `CLSID` 可執行 [ICorRuntimeHost](icorruntimehost-interface.md) 或 [ICLRRuntimeHost](iclrruntimehost-interface.md) 介面。 支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。  
  
 `riid`  
 在 `IID` 您所要求之介面的。 支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。  
  
 `ppv`  
 擴展載入之執行時間版本的介面指標。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CorBindToCurrentRuntime 函式](corbindtocurrentruntime-function.md)
- [CorBindToRuntime 函式](corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg 函式](corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx 函式](corbindtoruntimeex-function.md)
- [ICorRuntimeHost 介面](icorruntimehost-interface.md)
- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
