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
ms.openlocfilehash: 426e95281b648217642ca06f04dfbd9ec991221e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733772"
---
# <a name="corbindtoruntime-function"></a>CorBindToRuntime 函式

讓非受控主機將 common language runtime (CLR) 載入至進程。  
  
 此函式已在 .NET Framework 4 中被取代。  
  
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
 在字串，描述您想要載入的 CLR 版本。  
  
 .NET Framework 中的版本號碼包含四個以句號分隔的部分： *主要.*...............。 傳遞的字串 `pwszVersion` 必須以字元 "v" 開頭，後面接著第三個版本號碼部分 (例如 "v 1.0.1529" ) 。  
  
 某些版本的 CLR 會與指定 CLR 舊版相容性的原則語句一起安裝。 根據預設，啟動填充碼 `pwszVersion` 會針對原則語句進行評估，並載入與所要求版本相容的最新執行階段版本。 主機可以強制填充碼略過原則評估，並藉由傳遞參數的值來載入指定的確切版本 `pwszVersion`  `STARTUP_LOADER_SAFEMODE` `flags` ，如下所述。  
  
 如果呼叫端對指定 null `pwszVersion` ，則會載入執行時間的最新版本。 傳遞 null 可讓主機無法控制載入的執行階段版本。 雖然此方法可能適用于某些情況，但強烈建議主機提供要載入的特定版本。  
  
 `pwszBuildFlavor`  
 在字串，指定是否要載入伺服器或 CLR 的工作站組建。 有效值為 `svr` 和 `wks`。 伺服器組建經過優化，可利用多個處理器進行垃圾收集，而且工作站組建已針對在單處理器電腦上執行的用戶端應用程式優化。  
  
 如果 `pwszBuildFlavor` 設定為 null，就會載入工作站組建。 在單處理器電腦上執行時，一律會載入工作站組建，即使 `pwszBuildFlavor` 設定為 `svr` 。 但是，如果 `pwszBuildFlavor` 設定為 `svr` ，而且指定了並行垃圾收集 (請參閱 `flags`) 的參數描述，就會載入伺服器組建。  
  
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
  
    2. 若為非受控裝載介面，請在呼叫函式時，于 `STARTUP_LEGACY_IMPERSONATION` 參數中設定旗標 `flags` `CorBindToRuntimeEx` 。  
  
     第1版的相容性模式會套用至整個進程，以及處理常式中的所有應用程式域。  
  
## <a name="remarks"></a>備註  

 [CorBindToRuntimeEx](corbindtoruntimeex-function.md) 和 `CorBindToRuntime` 執行相同的作業，但 `CorBindToRuntimeEx` 函數可讓您設定旗標來指定 CLR 的行為。  
  
## <a name="requirements"></a>需求  

 **平台：** 請參閱 [系統需求](../../get-started/system-requirements.md)。  
  
 **標頭：** Mscoree.dll  
  
 連結 **庫：** MSCorEE.dll  
  
 **.NET Framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CorBindToCurrentRuntime 函式](corbindtocurrentruntime-function.md)
- [CorBindToRuntimeByCfg 函式](corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeEx 函式](corbindtoruntimeex-function.md)
- [CorBindToRuntimeHost 函式](corbindtoruntimehost-function.md)
- [ICorRuntimeHost 介面](icorruntimehost-interface.md)
- [已被取代的 CLR 裝載函式](deprecated-clr-hosting-functions.md)
