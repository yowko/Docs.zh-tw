---
title: CorBindToRuntime 函式
ms.date: 03/30/2017
api_name:
- CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- CorBindToRuntime
helpviewer_keywords:
- CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type:
- apiref
ms.openlocfilehash: 9d4b8bb7d5b3da15f665849c8d18c3a10dbe600b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138315"
---
# <a name="corbindtoruntime-function"></a>CorBindToRuntime 函式
讓非受控主機將 common language runtime （CLR）載入進程中。  
  
 此函式在 .NET Framework 4 中已被取代。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
## <a name="parameters"></a>參數  
 `pwszVersion`  
 在描述您要載入之 CLR 版本的字串。  
  
 .NET Framework 中的版本號碼包含四個以句點分隔的部分： [主要]. [*次要. 組建. 修訂*]。 當做 `pwszVersion` 傳遞的字串必須以 "v" 字元開頭，後面接著版本號碼的前三個部分（例如 "v 1.0.1529"）。  
  
 某些 CLR 版本會與原則語句一起安裝，以指定與舊版 CLR 的相容性。 根據預設，啟動填充碼會針對原則語句評估 `pwszVersion`，並載入與所要求版本相容的最新執行階段版本。 主機可以強制填充碼略過原則評估，並藉由傳遞 `flags` 參數的 `STARTUP_LOADER_SAFEMODE` 值來載入 `pwszVersion` 中指定的確切版本，如下所述。  
  
 如果呼叫者為 `pwszVersion`指定 null，則會載入最新版本的執行時間。 傳遞 null 可讓主機無法控制載入的執行階段版本。 雖然這種方法可能適用于某些情況，但強烈建議主機提供要載入的特定版本。  
  
 `pwszBuildFlavor`  
 在字串，指定是否要載入伺服器或 CLR 的工作站組建。 有效值為 `svr` 和 `wks`。 伺服器組建已優化，可利用多個處理器進行垃圾收集，而且工作站組建已針對在單處理器機器上執行的用戶端應用程式優化。  
  
 如果 `pwszBuildFlavor` 設定為 null，則會載入工作站組建。 在單處理器電腦上執行時，一律會載入工作站組建，即使 `pwszBuildFlavor` 設定為 `svr`也一樣。 不過，如果 `pwszBuildFlavor` 設定為 `svr` 且同時指定了並行垃圾收集（請參閱 `flags` 參數的描述），則會載入伺服器組建。  
  
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
  
    2. 若為非受控裝載介面，請在呼叫 `CorBindToRuntimeEx` 函式時，在 `flags` 參數中設定 `STARTUP_LEGACY_IMPERSONATION` 旗標。  
  
     版本1相容性模式適用于整個進程和進程中的所有應用程式域。  
  
## <a name="remarks"></a>備註  
 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)和 `CorBindToRuntime` 會執行相同的作業，但 `CorBindToRuntimeEx` 函數可讓您設定旗標來指定 CLR 的行為。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll. h  
  
 連結**庫：** Mscoree.dll .dll  
  
 **.NET framework 版本：** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱

- [CorBindToCurrentRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeByCfg 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
