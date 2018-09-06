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
ms.openlocfilehash: 1952121a6c0c735926944c839c3c7e8a8db5fb53
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723190"
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost 函式
可讓主機以指定的 common language runtime (CLR) 版本載入處理序。  
  
 此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
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
  
#### <a name="parameters"></a>參數  
 `pwszVersion`  
 [in]字串，描述您想要載入的 clr 版本。  
  
 在.NET Framework 的版本號碼是由以句點分隔的四個部分所組成： *major.minor.build.revision*。 將字串傳遞為`pwszVersion`不可使用字元"v"後面接著的版本號碼 (例如，"v1.0.1529 」) 的前三個部分。  
  
 某些版本的 CLR 會以指定與舊版的 clr 相容的原則陳述式安裝。 根據預設，啟動填充碼會評估`pwszVersion`針對原則陳述式並載入最新版本的執行階段，是與所要求的版本相容。 主機可以強制填充碼略過原則評估，並載入指定的確切版本`pwszVersion`藉由傳遞值的 STARTUP_LOADER_SAFEMODE`startupFlags`參數。  
  
 如果`pwszVersion`是`null,`方法不會載入任何版本的 CLR。 相反地，它會傳回 CLR_E_SHIM_RUNTIMELOAD，表示它無法載入執行階段。  
  
 `pwszBuildFlavor`  
 [in]字串，指定是否要載入的伺服器或工作站組建的 clr。 有效值為 `svr` 和 `wks`。 伺服器組建已最佳化，可利用多個處理器的記憶體回收，以及工作站建置適用於單一處理器電腦上執行的用戶端應用程式。  
  
 如果`pwszBuildFlavor`設為 null，工作站組建已載入。 單一處理器電腦上執行時，會一律載入工作站組建，即使`pwszBuildFlavor`設為`svr`。 不過，如果`pwszBuildFlavor`設為`svr`以及指定並行記憶體回收 (請參閱說明，`startupFlags`參數)，會載入伺服器組建。  
  
> [!NOTE]
>  執行 WOW64 的應用程式中不支援並行記憶體回收 x86 實作 Intel Itanium 架構 （先前稱為 IA-64） 的 64 位元系統上的模擬器。 如需在 64 位元 Windows 系統上使用 WOW64 的詳細資訊，請參閱[執行的 32 位元應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。  
  
 `pwszHostConfigFile`  
 [in]指定要載入的 clr 版本的主機組態檔的名稱。 如果檔案名稱不包含完整的路徑，則會假設檔案是與正在進行呼叫之可執行檔相同的目錄中。  
  
 `pReserved`  
 [in]保留供未來擴充。  
  
 `startupFlags`  
 [in]一組控制並行記憶體回收、 定義域中性程式碼和行為的旗標`pwszVersion`參數。 如果沒有旗標設定，則預設會為單一網域。 如需支援的值，請參閱[STARTUP_FLAGS 列舉](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)。  
  
 `rclsid`  
 [in]`CLSID`的實作的 coclass [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面。 支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。  
  
 `riid`  
 [in]`IID`您所要求的介面。 支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。  
  
 `ppv`  
 [out]已載入的執行階段版本介面指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.idl  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [CorBindToCurrentRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [CorBindToRuntimeByCfg 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [CorBindToRuntimeEx 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
