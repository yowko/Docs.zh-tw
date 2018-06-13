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
ms.openlocfilehash: 8c1d83b32402343f3cd2b5403e328698abd6a930
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436211"
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost 函式
可讓主機處理程序中載入指定的 common language runtime (CLR) 版本。  
  
 此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
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
 [in]描述您想要載入的 clr 版本字串。  
  
 在.NET Framework 的版本號碼是由以句號分隔的四個部分所組成： *major.minor.build.revision*。 當做字串傳遞給`pwszVersion`開頭必須是字元"v"後面接著的版本號碼 (例如，"v1.0.1529") 的前三個部分。  
  
 某些版本的 CLR 會以指定與舊版 CLR 相容的原則陳述式安裝。 根據預設，啟動填充碼會評估`pwszVersion`針對原則陳述式和載入執行階段的最新版本，是與所要求的版本相容。 主機可以強制略過原則評估並載入中指定的確切版本填充碼`pwszVersion`藉由傳遞值的 STARTUP_LOADER_SAFEMODE`startupFlags`參數。  
  
 如果`pwszVersion`是`null,`方法不會載入任何版本的 CLR。 相反地，它會傳回 CLR_E_SHIM_RUNTIMELOAD，指出它無法載入執行階段。  
  
 `pwszBuildFlavor`  
 [in]字串，指定是否要在伺服器或工作站組建的 clr 載入。 有效值為 `svr` 和 `wks`。 伺服器組建已最佳化，可利用多個處理器的記憶體回收，並工作站組建最適合用於單一處理器電腦上執行的用戶端應用程式。  
  
 如果`pwszBuildFlavor`設為 null，工作站組建已載入。 單一處理器電腦上執行時，會一律載入工作站組建，即使`pwszBuildFlavor`設`svr`。 不過，如果`pwszBuildFlavor`設為`svr`並行記憶體回收是指定 (請參閱描述`startupFlags`參數)，會載入伺服器組建。  
  
> [!NOTE]
>  執行 WOW64 應用程式中不支援並行記憶體回收 x86 實作 （之前稱為 ia-64） 的 Intel Itanium 架構的 64 位元系統上的模擬器。 如需使用 WOW64 在 64 位元 Windows 系統上的詳細資訊，請參閱[執行 32 位元應用程式](http://msdn.microsoft.com/library/windows/desktop/aa384249.aspx)。  
  
 `pwszHostConfigFile`  
 [in]指定要載入的 clr 版本的主機組態檔的名稱。 如果檔案名稱不包含完整的路徑，則會假設檔案中進行呼叫的可執行檔相同的目錄。  
  
 `pReserved`  
 [in]保留供未來擴充。  
  
 `startupFlags`  
 [in]一組控制並行記憶體回收、 定義域中性程式碼和行為的旗標`pwszVersion`參數。 預設值是單一網域，如果沒有旗標設定。 如需支援的值，請參閱[STARTUP_FLAGS 列舉](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)。  
  
 `rclsid`  
 [in]`CLSID`實作的 coclass 的[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面。 支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。  
  
 `riid`  
 [in]`IID`您要求的介面。 支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。  
  
 `ppv`  
 [out]新版執行階段載入的介面指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.idl  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 [CorBindToCurrentRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)  
 [CorBindToRuntimeByCfg 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [CorBindToRuntimeEx 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
