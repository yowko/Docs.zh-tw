---
title: "CorBindToRuntime 函式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorBindToRuntime
api_location:
- mscoree.dll
- mscoreei.dll
api_type: DLLExport
f1_keywords: CorBindToRuntime
helpviewer_keywords: CorBindToRuntime function [.NET Framework hosting]
ms.assetid: 799740aa-46ec-4532-95da-6444565b4971
topic_type: apiref
caps.latest.revision: "20"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e6ce976961eedaa58ad265a133c15b2f27a8985
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="corbindtoruntime-function"></a>CorBindToRuntime 函式
可讓 unmanaged 的主機將 common language runtime (CLR) 載入處理序。  
  
 此函式中已被取代[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT CorBindToRuntime (  
    [in]  LPCWSTR     pwszVersion,   
    [in]  LPCWSTR     pwszBuildFlavor,   
    [in]  REFCLSID    rclsid,   
    [in]  REFIID      riid,   
    [out] LPVOID FAR  *ppv  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pwszVersion`  
 [in]您要載入描述的 CLR 版本字串。  
  
 在.NET Framework 的版本號碼是由以句號分隔的四個部分所組成： *major.minor.build.revision*。 當做字串傳遞給`pwszVersion`開頭必須是字元"v"後面接著的版本號碼 (例如，"v1.0.1529") 的前三個部分。  
  
 某些版本的 CLR 會以指定與舊版 CLR 相容的原則陳述式安裝。 根據預設，啟動填充碼會評估`pwszVersion`針對原則陳述式和載入執行階段的最新版本，是與所要求的版本相容。 主機可以強制略過原則評估並載入中指定的確切版本填充碼`pwszVersion`依值傳遞`STARTUP_LOADER_SAFEMODE`如`flags`參數，如下所述。  
  
 如果呼叫端指定為 null `pwszVersion`，載入執行階段的最新版本。 將 null 傳遞不提供主應用程式載入的執行階段版本的任何控制項。 雖然在某些情況下可能適合使用這種方法，但強烈建議主應用程式，提供要載入的特定版本。  
  
 `pwszBuildFlavor`  
 [in]字串，指定是否要在伺服器或工作站組建的 clr 載入。 有效值為 `svr` 和 `wks`。 伺服器組建已最佳化，可利用多個處理器的記憶體回收，並工作站組建最適合用於單一處理器電腦上執行的用戶端應用程式。  
  
 如果`pwszBuildFlavor`設為 null，工作站組建已載入。 單一處理器電腦上執行時，會一律載入工作站組建，即使`pwszBuildFlavor`設`svr`。 不過，如果`pwszBuildFlavor`設為`svr`並行記憶體回收是指定 (請參閱描述`flags`參數)，會載入伺服器組建。  
  
 `rclsid`  
 [in]`CLSID`實作的 coclass 的[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面。 支援的值為 CLSID_CorRuntimeHost 或 CLSID_CLRRuntimeHost。  
  
 `riid`  
 [in]`IID`所要求介面從`rclsid`。 支援的值為 IID_ICorRuntimeHost 或 IID_ICLRRuntimeHost。  
  
 `ppv`  
 [out]傳回的介面指標`riid`。  
  
## <a name="remarks"></a>備註  
 如果`pwszVersion`指定不存在，執行階段版本`CorBindToRuntimeEx`傳回 CLR_E_SHIM_RUNTIMELOAD HRESULT 值。  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>執行內容和流程的 Windows 身分識別  
 在 CLR 的第 1 版中<xref:System.Security.Principal.WindowsIdentity>物件不會流動到非同步的點，例如新的執行緒、 執行緒集區或計時器回呼。 在 CLR 2.0 版<xref:System.Threading.ExecutionContext>物件包裝目前執行中執行緒的一些資訊及流向它，跨越任何非同步的點，但不是會跨應用程式定義域界限。 同樣地，<xref:System.Security.Principal.WindowsIdentity>物件也會透過非同步的任何時間點流動。 因此，目前的模擬執行緒，如果有的話，流動。  
  
 您可以修改流程有兩種：  
  
1.  藉由修改<xref:System.Threading.ExecutionContext>設定，以隱藏每個執行緒為基礎的流程 (請參閱<xref:System.Threading.ExecutionContext.SuppressFlow%2A>， <xref:System.Security.SecurityContext.SuppressFlow%2A>，和<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A>方法)。  
  
2.  由處理程序的預設模式變更為 「 第 1 版的相容性模式，其中<xref:System.Security.Principal.WindowsIdentity>物件不會流動跨越任何非同步的點，不論<xref:System.Threading.ExecutionContext>目前執行緒上的設定。 如何變更預設的模式取決於是否載入 CLR 使用 managed 可執行檔或 unmanaged 裝載介面：  
  
    1.  針對受管理的可執行檔，您必須設定`enabled`屬性[ \<legacyImpersonationPolicy >](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)元素`true`。  
  
    2.  Unmanaged 裝載介面，設定`STARTUP_LEGACY_IMPERSONATION`加上旗標`flags`參數呼叫時`CorBindToRuntimeEx`函式。  
  
     第 1 版相容性模式適用於整個程序和程序中的所有應用程式定義域。  
  
## <a name="remarks"></a>備註  
 [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)和`CorBindToRuntime`執行相同的作業，但`CorBindToRuntimeEx`函式可讓您設定旗標來指定 CLR 的行為。  
  
## <a name="requirements"></a>需求  
 **平台：**看到[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標頭：** MSCorEE.h  
  
 **程式庫：** MSCorEE.dll  
  
 **.NET framework 版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>請參閱  
 [CorBindToCurrentRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)  
 [CorBindToRuntimeByCfg 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)  
 [CorBindToRuntimeEx 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [CorBindToRuntimeHost 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)  
 [ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)  
 [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
