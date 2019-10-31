---
title: CorBindToRuntimeEx 函式
ms.date: 03/30/2017
api_name:
- CorBindToRuntimeEx
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntimeEx
helpviewer_keywords:
- CorBindToRuntimeEx function [.NET Framework hosting]
ms.assetid: aae9fb17-5d01-41da-9773-1b5b5b642d81
topic_type:
- apiref
ms.openlocfilehash: 794a39f1e2c4a93a34ae39641519c79fd4c4e79e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131219"
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx 函式
讓非受控主機將 common language runtime （CLR）載入進程中。 [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)和 `CorBindToRuntimeEx` 函式會執行相同的作業，但 `CorBindToRuntimeEx` 函數可讓您設定旗標來指定 CLR 的行為。  
  
 此函式在 .NET Framework 4 中已被取代。  
  
 此函式會接受一組參數，讓主機能夠執行下列動作：  
  
- 指定將要載入的執行階段版本。  
  
- 指出是否應載入伺服器或工作站組建。  
  
- 控制並行垃圾收集或非並行垃圾收集是否已完成。  
  
> [!NOTE]
> 在執行 Intel Itanium 架構（先前稱為 IA-64）的64位系統上執行 WOW64 x86 模擬器的應用程式不支援並行垃圾收集。 如需在64位 Windows 系統上使用 WOW64 的詳細資訊，請參閱執行[32 位應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。  
  
- 控制是否將元件載入為網域中性。  
  
- 取得[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)的介面指標，其可以用來設定在啟動 CLR 實例之前，用來設定它的其他選項。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CorBindToRuntimeEx (  
    [in]  LPCWSTR      pwszVersion,   
    [in]  LPCWSTR      pwszBuildFlavor,   
    [in]  DWORD        startupFlags,   
    [in]  REFCLSID     rclsid,   
    [in]  REFIID       riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a>參數  
 `pwszVersion`  
 在描述您要載入之 CLR 版本的字串。  
  
 .NET Framework 中的版本號碼包含四個以句點分隔的部分： [主要]. [*次要. 組建. 修訂*]。 當做 `pwszVersion` 傳遞的字串必須以 "v" 字元開頭，後面接著版本號碼的前三個部分（例如 "v 1.0.1529"）。  
  
 某些 CLR 版本會與原則語句一起安裝，以指定與舊版 CLR 的相容性。 根據預設，啟動填充碼會針對原則語句評估 `pwszVersion`，並載入與所要求版本相容的最新執行階段版本。 主機可以強制填充碼略過原則評估，並藉由傳遞 `startupFlags` 參數的 `STARTUP_LOADER_SAFEMODE` 值來載入 `pwszVersion` 中指定的確切版本，如下所述。  
  
 如果呼叫者指定 null 做為 `pwszVersion`，`CorBindToRuntimeEx` 會識別版本號碼低於 .NET Framework 4 執行時間的已安裝執行時間，並從該集合載入最新版本的執行時間。 它不會載入 .NET Framework 4 或更新版本，如果未安裝舊版，則會失敗。 請注意，傳遞 null 可讓主機無法控制載入的執行階段版本。 雖然這種方法可能適用于某些情況，但強烈建議主機提供要載入的特定版本。  
  
 `pwszBuildFlavor`  
 在字串，指定是否要載入伺服器或 CLR 的工作站組建。 有效值為 `svr` 和 `wks`。 伺服器組建已優化，可利用多個處理器進行垃圾收集，而且工作站組建已針對在單處理器機器上執行的用戶端應用程式優化。  
  
 如果 `pwszBuildFlavor` 設定為 null，則會載入工作站組建。 在單處理器電腦上執行時，一律會載入工作站組建，即使 `pwszBuildFlavor` 設定為 `svr`也一樣。 不過，如果 `pwszBuildFlavor` 設定為 `svr` 且同時指定了並行垃圾收集（請參閱 `startupFlags` 參數的描述），則會載入伺服器組建。  
  
 `startupFlags`  
 在[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列舉的值組合。 這些旗標會控制並行垃圾收集、網域中性程式碼，以及 `pwszVersion` 參數的行為。 如果未設定旗標，則預設值為單一網域。 下列是有效值：  
  
- `STARTUP_CONCURRENT_GC`  
  
- `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
- `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
- `STARTUP_LOADER_SAFEMODE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_LOADER_SETPREFERENCE`  
  
- `STARTUP_SERVER_GC`  
  
- `STARTUP_HOARD_GC_VM`  
  
- `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
- `STARTUP_LEGACY_IMPERSONATION`  
  
- `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
- `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 如需這些旗標的說明，請參閱[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列舉。  
  
 `rclsid`  
 在執行[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面之 coclass 的 `CLSID`。 支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。  
  
 `riid`  
 在從 `rclsid`所要求之介面的 `IID`。 支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。  
  
 `ppv`  
 脫銷要 `riid`的傳回介面指標。  
  
## <a name="remarks"></a>備註  
 如果 `pwszVersion` 指定不存在的執行階段版本，`CorBindToRuntimeEx` 會傳回 CLR_E_SHIM_RUNTIMELOAD 的 HRESULT 值。  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>執行內容和 Windows 身分識別流程  
 在 CLR 的第1版中，<xref:System.Security.Principal.WindowsIdentity> 物件不會流經非同步點，例如新執行緒、執行緒集區或計時器回呼。 在版本2.0 的 CLR 中，<xref:System.Threading.ExecutionContext> 物件會包裝有關目前執行中線程的一些資訊，並將其流經任何非同步點，但不會跨越應用程式域界限。 同樣地，<xref:System.Security.Principal.WindowsIdentity> 物件也會跨任何非同步點流動。 因此，執行緒上目前的模擬（如果有的話）也會流動。  
  
 您可以透過兩種方式來改變流程：  
  
1. 藉由修改 <xref:System.Threading.ExecutionContext> 設定，以根據每個執行緒來隱藏流程（請參閱 <xref:System.Threading.ExecutionContext.SuppressFlow%2A>、<xref:System.Security.SecurityContext.SuppressFlow%2A>和 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> 方法）。  
  
2. 藉由將進程預設模式變更為版本1相容性模式，其中 <xref:System.Security.Principal.WindowsIdentity> 物件不會流經任何非同步點，而不論目前線程上的 <xref:System.Threading.ExecutionContext> 設定為何。 您變更預設模式的方式，取決於您使用的是受控可執行檔或非受控裝載介面來載入 CLR：  
  
    1. 對於受控可執行檔，您必須將[\<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)專案的 `enabled` 屬性設定為 [`true`]。  
  
    2. 若為非受控裝載介面，請在呼叫 `CorBindToRuntimeEx` 函式時，在 `startupFlags` 參數中設定 `STARTUP_LEGACY_IMPERSONATION` 旗標。  
  
     版本1相容性模式適用于整個進程和進程中的所有應用程式域。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [CorBindToCurrentRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeHost 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
