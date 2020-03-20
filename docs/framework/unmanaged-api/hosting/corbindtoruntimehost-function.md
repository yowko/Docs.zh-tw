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
ms.openlocfilehash: 6566adc442034763e0209869404b60b5afa63866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176483"
---
# <a name="corbindtoruntimehost-function"></a>CorBindToRuntimeHost 函式
使主機能夠將指定版本的通用語言運行時 （CLR） 載入到進程中。  
  
 此功能已在 .NET 框架 4 中棄用。  
  
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
 [在]描述要載入的 CLR 版本的字串。  
  
 .NET 框架中的版本號由四個部分組成，由句點分隔：*主要.minor.build.revision*. 傳遞的`pwszVersion`字串必須以字元"v"開頭，後跟版本號的前三個部分（例如，"v1.0.1529"）。  
  
 CLR 的某些版本都安裝了策略語句，該語句指定與 CLR 的早期版本的相容性。 預設情況下，啟動希姆`pwszVersion`根據策略語句進行評估，並載入與所請求版本相容的最新版本的運行時。 主機可以通過傳遞`startupFlags`參數的STARTUP_LOADER_SAFEMODE值來強制 him 跳過策略評估並載入指定`pwszVersion`的確切版本。  
  
 如果`pwszVersion`是`null,`，該方法不會載入 CLR 的任何版本。 相反，它將返回CLR_E_SHIM_RUNTIMELOAD，這表明它無法載入運行時。  
  
 `pwszBuildFlavor`  
 [在]指定是載入 CLR 的伺服器還是工作站構建的字串。 有效值為 `svr` 和 `wks`。 伺服器生成經過優化，以利用多個處理器進行垃圾回收，工作站生成針對在單處理器電腦上運行的用戶端應用程式進行了優化。  
  
 如果`pwszBuildFlavor`設置為 null，則載入工作站生成。 在單處理器電腦上運行時，工作站生成始終載入，即使`pwszBuildFlavor`設置為`svr`。 但是，如果`pwszBuildFlavor`設置為`svr`並指定了併發垃圾回收（請參閱`startupFlags`參數的說明），則載入伺服器生成。  
  
> [!NOTE]
> 在 64 位系統上運行 WOW64 x86 模擬器的應用程式不支援併發垃圾回收，這些系統實現了英特爾 Itanium 架構（以前稱為 IA-64）。 有關在 64 位 Windows 系統上使用 WOW64 的詳細資訊，請參閱[運行 32 位應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。  
  
 `pwszHostConfigFile`  
 [在]指定要載入的 CLR 版本的主機設定檔的名稱。 如果檔案名不包含完全限定的路徑，則假定該檔與進行調用的可執行檔位於同一目錄中。  
  
 `pReserved`  
 [在]保留以供將來擴展。  
  
 `startupFlags`  
 [在]控制併發垃圾回收、域中立代碼和`pwszVersion`參數行為的標誌集。 如果未設置標誌，則預設值為單個域。 有關受支援值的清單，請參閱[STARTUP_FLAGS枚舉](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)。  
  
 `rclsid`  
 [在]`CLSID`實現[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面的共類。 支援的值CLSID_CorRuntimeHost或CLSID_CLRRuntimeHost。  
  
 `riid`  
 [在]您`IID`請求的介面的。 支援的值IID_ICorRuntimeHost或IID_ICLRRuntimeHost。  
  
 `ppv`  
 [出]指向載入的執行階段版本的介面指標。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.idl  
  
 **庫：** MSCorEE.dll  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CorBindToCurrentRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
