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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03972ac38a5259443f43a4f91002bf8dc717509f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/06/2019
ms.locfileid: "57466293"
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx 函式
可讓 unmanaged 主應用程式將 common language runtime (CLR) 載入程序。 [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)並`CorBindToRuntimeEx`函式會執行相同的作業，但`CorBindToRuntimeEx`函式可讓您設定旗標指定 CLR 的行為。  
  
 此函式中的過時[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
 此函數會採用一組參數，可讓主應用程式執行下列作業：  
  
-   指定將載入的執行階段版本。  
  
-   指出是否應該載入的伺服器或工作站的組建。  
  
-   控制是否進行並行記憶體回收或非並行記憶體回收。  
  
> [!NOTE]
>  執行 WOW64 的應用程式中不支援並行記憶體回收 x86 實作 Intel Itanium 架構 （先前稱為 IA-64） 的 64 位元系統上的模擬器。 如需在 64 位元 Windows 系統上使用 WOW64 的詳細資訊，請參閱[執行的 32 位元應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。  
  
-   控制是否以定義域中性方式載入組件。  
  
-   取得的介面指標[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) ，可以用來設定其他選項來啟動之前設定的 CLR 執行個體。  
  
## <a name="syntax"></a>語法  
  
```  
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
 [in]想要載入的字串，描述的 CLR 版本。  
  
 在.NET Framework 的版本號碼是由以句點分隔的四個部分所組成： *major.minor.build.revision*。 將字串傳遞為`pwszVersion`不可使用字元"v"後面接著的版本號碼 (例如，"v1.0.1529 」) 的前三個部分。  
  
 某些版本的 CLR 會以指定與舊版的 clr 相容的原則陳述式安裝。 根據預設，啟動填充碼會評估`pwszVersion`針對原則陳述式並載入最新版本的執行階段，是與所要求的版本相容。 主機可以強制填充碼略過原則評估，並載入指定的確切版本`pwszVersion`傳遞的值，藉以`STARTUP_LOADER_SAFEMODE`如`startupFlags`參數，如下所述。  
  
 如果呼叫端指定為 null `pwszVersion`，`CorBindToRuntimeEx`識別已安裝執行階段，其版本號碼低於.NET Framework 4 執行階段，並從該集合載入執行階段的最新版本的集合。 如果安裝沒有較早的版本，它就不會載入.NET Framework 4 或更新版本，並會失敗。 請注意，將 null 傳遞提供主機載入執行階段版本的任何控制項。 雖然這種方法可能適用於某些情況下，強烈建議主應用程式，提供要載入的特定版本。  
  
 `pwszBuildFlavor`  
 [in]字串，指定是否要載入的伺服器或工作站組建的 clr。 有效值為 `svr` 和 `wks`。 伺服器組建已最佳化，可利用多個處理器的記憶體回收，以及工作站建置適用於單一處理器電腦上執行的用戶端應用程式。  
  
 如果`pwszBuildFlavor`設為 null，工作站組建已載入。 單一處理器電腦上執行時，會一律載入工作站組建，即使`pwszBuildFlavor`設為`svr`。 不過，如果`pwszBuildFlavor`設為`svr`以及指定並行記憶體回收 (請參閱說明，`startupFlags`參數)，會載入伺服器組建。  
  
 `startupFlags`  
 [in]值的組合[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列舉型別。 這些旗標控制並行記憶體回收、 定義域中性程式碼，以及行為`pwszVersion`參數。 如果沒有旗標設定，則預設會為單一網域。 下列是有效值：  
  
-   `STARTUP_CONCURRENT_GC`  
  
-   `STARTUP_LOADER_OPTIMIZATION_SINGLE_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN`  
  
-   `STARTUP_LOADER_OPTIMIZATION_MULTI_DOMAIN_HOST`  
  
-   `STARTUP_LOADER_SAFEMODE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_LOADER_SETPREFERENCE`  
  
-   `STARTUP_SERVER_GC`  
  
-   `STARTUP_HOARD_GC_VM`  
  
-   `STARTUP_SINGLE_VERSION_HOSTING_INTERFACE`  
  
-   `STARTUP_LEGACY_IMPERSONATION`  
  
-   `STARTUP_DISABLE_COMMITTHREADSTACK`  
  
-   `STARTUP_ALWAYSFLOW_IMPERSONATION`  
  
 如需這些旗標的描述，請參閱 < [STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)列舉型別。  
  
 `rclsid`  
 [in]`CLSID`的實作的 coclass [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面。 支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。  
  
 `riid`  
 [in]`IID`的要求的介面，從`rclsid`。 支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。  
  
 `ppv`  
 [out]若要傳回的介面指標`riid`。  
  
## <a name="remarks"></a>備註  
 如果`pwszVersion`指定不存在，執行階段版本`CorBindToRuntimeEx`傳回 CLR_E_SHIM_RUNTIMELOAD HRESULT 值。  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>執行內容和流程的 Windows 身分識別  
 在第 1 版的 clr，<xref:System.Security.Principal.WindowsIdentity>物件不會流經非同步點，例如新的執行緒、 執行緒集區或計時器回呼。 在 2.0 版中的 clr，<xref:System.Threading.ExecutionContext>物件包裝目前執行中執行緒的一些資訊，並跨任何非同步點，但不是會在應用程式定義域界限之間流動它。 同樣地，<xref:System.Security.Principal.WindowsIdentity>物件也會流過任何非同步點。 因此，目前的模擬執行緒，如果有的話，會流動。  
  
 您可以變更流程有兩種：  
  
1.  藉由修改<xref:System.Threading.ExecutionContext>若要隱藏個別的執行緒上的流程的設定 (請參閱 < <xref:System.Threading.ExecutionContext.SuppressFlow%2A>， <xref:System.Security.SecurityContext.SuppressFlow%2A>，和<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A>方法)。  
  
2.  藉由處理程序的預設模式變更為 「 第 1 版相容性模式中，其中<xref:System.Security.Principal.WindowsIdentity>物件不會流經任何非同步點，無論<xref:System.Threading.ExecutionContext>目前執行緒上的設定。 您要如何變更預設的模式取決於您是使用 managed 可執行檔或未受管理的裝載介面載入 CLR:  
  
    1.  受管理的可執行檔，您必須設定`enabled`的屬性[ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)項目`true`。  
  
    2.  Unmanaged 裝載介面，設定`STARTUP_LEGACY_IMPERSONATION`中的旗標`startupFlags`參數呼叫時`CorBindToRuntimeEx`函式。  
  
     第 1 版相容性模式適用於整個程序和程序中的所有應用程式定義域。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱
- [CorBindToCurrentRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeHost 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
