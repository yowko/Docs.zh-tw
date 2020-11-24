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
ms.openlocfilehash: 55fbf0c37861029940422a10bd62f5ecfebf2b9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673731"
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx 函式

讓非受控主機將 common language runtime (CLR) 載入至進程。 [CorBindToRuntime](corbindtoruntime-function.md)和 `CorBindToRuntimeEx` 函數會執行相同的作業，但 `CorBindToRuntimeEx` 函數可讓您設定旗標來指定 CLR 的行為。  
  
 此函式已在 .NET Framework 4 中被取代。  
  
 此函式會採用一組允許主機執行下列動作的參數：  
  
- 指定將載入的執行階段版本。  
  
- 指出是否應該載入伺服器或工作站組建。  
  
- 控制並行垃圾收集或非並行垃圾收集是否已完成。  
  
> [!NOTE]
> 在64位系統上執行 WOW64 x86 模擬器的應用程式不支援並行垃圾收集，這些系統會執行先前稱為 IA-64) 的 Intel Itanium 架構 (。 如需在64位 Windows 系統上使用 WOW64 的詳細資訊，請參閱執行 [32 位應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。  
  
- 控制是否將元件載入為網域中性。  
  
- 取得 [ICorRuntimeHost](icorruntimehost-interface.md) 的介面指標，可用來設定啟動 CLR 實例之前，設定其他選項。  
  
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
 在字串，描述您想要載入的 CLR 版本。  
  
 .NET Framework 中的版本號碼包含四個以句號分隔的部分： *主要.*...............。 傳遞的字串 `pwszVersion` 必須以字元 "v" 開頭，後面接著第三個版本號碼部分 (例如 "v 1.0.1529" ) 。  
  
 某些版本的 CLR 會與指定 CLR 舊版相容性的原則語句一起安裝。 根據預設，啟動填充碼 `pwszVersion` 會針對原則語句進行評估，並載入與所要求版本相容的最新執行階段版本。 主機可以強制填充碼略過原則評估，並藉由傳遞參數的值來載入指定的確切版本 `pwszVersion`  `STARTUP_LOADER_SAFEMODE` `startupFlags` ，如下所述。  
  
 如果呼叫端為指定 null `pwszVersion` ，則 `CorBindToRuntimeEx` 會識別其版本號碼低於 .NET Framework 4 執行時間的已安裝執行時間集，並從該集合載入最新版本的執行時間。 它不會載入 .NET Framework 4 或更新版本，如果未安裝舊版，則會失敗。 請注意，傳遞 null 可讓主機無法控制載入的執行階段版本。 雖然此方法可能適用于某些情況，但強烈建議主機提供要載入的特定版本。  
  
 `pwszBuildFlavor`  
 在字串，指定是否要載入伺服器或 CLR 的工作站組建。 有效值為 `svr` 和 `wks`。 伺服器組建經過優化，可利用多個處理器進行垃圾收集，而且工作站組建已針對在單處理器電腦上執行的用戶端應用程式優化。  
  
 如果 `pwszBuildFlavor` 設定為 null，就會載入工作站組建。 在單處理器電腦上執行時，一律會載入工作站組建，即使 `pwszBuildFlavor` 設定為 `svr` 。 但是，如果 `pwszBuildFlavor` 設定為 `svr` ，而且指定了並行垃圾收集 (請參閱 `startupFlags`) 的參數描述，就會載入伺服器組建。  
  
 `startupFlags`  
 在 [STARTUP_FLAGS](startup-flags-enumeration.md) 列舉值的組合。 這些旗標控制並行垃圾收集、網域中立的程式碼，以及參數的行為 `pwszVersion` 。 如果未設定任何旗標，則預設為單一網域。 下列是有效值：  
  
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
  
 如需這些旗標的說明，請參閱 [STARTUP_FLAGS](startup-flags-enumeration.md) 列舉。  
  
 `rclsid`  
 在Coclass 的， `CLSID` 可執行 [ICorRuntimeHost](icorruntimehost-interface.md) 或 [ICLRRuntimeHost](iclrruntimehost-interface.md) 介面。 支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。  
  
 `riid`  
 在所 `IID` 要求介面的 `rclsid` 。 支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。  
  
 `ppv`  
 擴展傳回的介面指標 `riid` 。  
  
## <a name="remarks"></a>備註  

 如果 `pwszVersion` 指定不存在的執行階段版本，則會傳回 `CorBindToRuntimeEx` CLR_E_SHIM_RUNTIMELOAD 的 HRESULT 值。  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>執行內容和 Windows 身分識別的流程  

 在 CLR 的第1版中， <xref:System.Security.Principal.WindowsIdentity> 物件不會在非同步點（例如新執行緒、執行緒集區或計時器回呼）之間流動。 在 CLR 的2.0 版中， <xref:System.Threading.ExecutionContext> 物件會包裝有關目前執行中線程的一些資訊，並將其流經任何非同步點，而不是跨應用程式域界限。 同樣地，此 <xref:System.Security.Principal.WindowsIdentity> 物件也會在任何非同步點之間流動。 因此，執行緒上目前的模擬（如果有的話）也會流程。  
  
 您可以透過兩種方式來變更流程：  
  
1. 藉由修改 <xref:System.Threading.ExecutionContext> 設定以針對每個執行緒隱藏流程 (查看 <xref:System.Threading.ExecutionContext.SuppressFlow%2A> 、 <xref:System.Security.SecurityContext.SuppressFlow%2A> 和 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A> 方法) 。  
  
2. 藉由將進程預設模式變更為第1版的相容性模式，其中 <xref:System.Security.Principal.WindowsIdentity> 物件不會流經任何非同步點，而不論 <xref:System.Threading.ExecutionContext> 目前線程上的設定為何。 變更預設模式的方式取決於您是使用 managed 可執行檔或非受控裝載介面載入 CLR：  
  
    1. 針對 managed 可執行檔，您必須將 `enabled` 元素的屬性設定 [\<legacyImpersonationPolicy>](../../configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md) 為 `true` 。  
  
    2. 若為非受控裝載介面，請在呼叫函式時，于 `STARTUP_LEGACY_IMPERSONATION` 參數中設定旗標 `startupFlags` `CorBindToRuntimeEx` 。  
  
     第1版的相容性模式會套用至整個進程，以及處理常式中的所有應用程式域。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CorBindToCurrentRuntime 函式](corbindtocurrentruntime-function.md)
- [CorBindToRuntime 函式](corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg 函式](corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeHost 函式](corbindtoruntimehost-function.md)
- [ICorRuntimeHost 介面](icorruntimehost-interface.md)
- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
