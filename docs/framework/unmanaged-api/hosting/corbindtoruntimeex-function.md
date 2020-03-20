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
ms.openlocfilehash: 3520af5f55f43183920dce7fbd24b70359c023a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176496"
---
# <a name="corbindtoruntimeex-function"></a>CorBindToRuntimeEx 函式
使非託管主機能夠將通用語言運行時 （CLR） 載入到進程中。 [CorBindToRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)和`CorBindToRuntimeEx`函數執行相同的操作，`CorBindToRuntimeEx`但該函數允許您設置標誌以指定 CLR 的行為。  
  
 此功能已在 .NET 框架 4 中棄用。  
  
 此函數採用一組允許主機執行以下操作的參數：  
  
- 指定將載入的運行時的版本。  
  
- 指示是否應載入伺服器或工作站生成。  
  
- 控制是否完成了併發垃圾回收或非併發垃圾回收。  
  
> [!NOTE]
> 在 64 位系統上運行 WOW64 x86 模擬器的應用程式不支援併發垃圾回收，這些系統實現了英特爾 Itanium 架構（以前稱為 IA-64）。 有關在 64 位 Windows 系統上使用 WOW64 的詳細資訊，請參閱[運行 32 位應用程式](/windows/desktop/WinProg64/running-32-bit-applications)。  
  
- 控制程式集是否載入為域中立。  
  
- 獲取指向[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)的介面指標，該指標可用於在 CLR 啟動之前設置用於配置 CLR 實例的其他選項。  
  
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
 [在]描述要載入的 CLR 版本的字串。  
  
 .NET 框架中的版本號由四個部分組成，由句點分隔：*主要.minor.build.revision*. 傳遞的`pwszVersion`字串必須以字元"v"開頭，後跟版本號的前三個部分（例如，"v1.0.1529"）。  
  
 CLR 的某些版本都安裝了策略語句，該語句指定與 CLR 的早期版本的相容性。 預設情況下，啟動希姆`pwszVersion`根據策略語句進行評估，並載入與所請求版本相容的最新版本的運行時。 主機可以強制 him 跳過策略評估，並通過傳遞`pwszVersion``STARTUP_LOADER_SAFEMODE``startupFlags`參數的值來載入指定的確切版本，如下所述。  
  
 如果調用方為`pwszVersion`指定`CorBindToRuntimeEx`null，則標識其版本號低於 .NET Framework 4 運行時的已安裝運行時集，並從該集載入最新版本的運行時。 它不會載入 .NET 框架 4 或更高版本，如果沒有安裝早期版本，它將失敗。 請注意，傳遞 null 使主機無法控制載入的哪個版本的運行時。 儘管此方法在某些情況下可能適用，但強烈建議主機提供要載入的特定版本。  
  
 `pwszBuildFlavor`  
 [在]指定是載入 CLR 的伺服器還是工作站構建的字串。 有效值為 `svr` 和 `wks`。 伺服器生成經過優化，以利用多個處理器進行垃圾回收，工作站生成針對在單處理器電腦上運行的用戶端應用程式進行了優化。  
  
 如果`pwszBuildFlavor`設置為 null，則載入工作站生成。 在單處理器電腦上運行時，工作站生成始終載入，即使`pwszBuildFlavor`設置為`svr`。 但是，如果`pwszBuildFlavor`設置為`svr`並指定了併發垃圾回收（請參閱`startupFlags`參數的說明），則載入伺服器生成。  
  
 `startupFlags`  
 [在][STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)枚舉的值的組合。 這些標誌控制併發垃圾回收、域中立代碼和`pwszVersion`參數的行為。 如果未設置標誌，則預設值為單個域。 下列是有效值：  
  
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
  
 有關這些標誌的說明，請參閱[STARTUP_FLAGS](../../../../docs/framework/unmanaged-api/hosting/startup-flags-enumeration.md)枚舉。  
  
 `rclsid`  
 [在]`CLSID`實現[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)或[ICLRRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)介面的共類。 支援的值CLSID_CorRuntimeHost或CLSID_CLRRuntimeHost。  
  
 `riid`  
 [在]從`IID`的請求介面的`rclsid`的 支援的值IID_ICorRuntimeHost或IID_ICLRRuntimeHost。  
  
 `ppv`  
 [出]返回的介面指標到`riid`。  
  
## <a name="remarks"></a>備註  
 如果`pwszVersion`指定不存在的執行階段版本，`CorBindToRuntimeEx`則返回 hRESULT 值CLR_E_SHIM_RUNTIMELOAD。  
  
## <a name="execution-context-and-flow-of-windows-identity"></a>執行上下文和 Windows 標識的流  
 在 CLR 的版本 1<xref:System.Security.Principal.WindowsIdentity>中，物件不會跨非同步點（如新執行緒、執行緒池或計時器回檔）流動。 在 CLR 的版本 2.0<xref:System.Threading.ExecutionContext>中，物件會包裝有關當前正在執行的執行緒的一些資訊，並將其流過任何非同步點，但不跨應用程式域邊界。 同樣，<xref:System.Security.Principal.WindowsIdentity>物件也流過任何非同步點。 因此，執行緒上的當前類比（如果有）也會流動。  
  
 您可以通過兩種方式更改流：  
  
1. 通過修改<xref:System.Threading.ExecutionContext>設置以按執行緒禁止流（請參閱 、<xref:System.Threading.ExecutionContext.SuppressFlow%2A><xref:System.Security.SecurityContext.SuppressFlow%2A>和方法）。 <xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A>  
  
2. 通過將進程預設模式更改為版本 1 相容性模式，其中<xref:System.Security.Principal.WindowsIdentity>物件不會流過任何非同步點，而不考慮當前執行緒上的<xref:System.Threading.ExecutionContext>設置。 更改預設模式的方式取決於您是使用託管可執行檔還是非託管託管介面來載入 CLR：  
  
    1. 對於託管可執行檔，必須將`enabled`[\<舊類比策略>](../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)元素的屬性設置為`true`。  
  
    2. 對於非託管託管介面，在`STARTUP_LEGACY_IMPERSONATION`調用`startupFlags``CorBindToRuntimeEx`函數時在參數中設置標誌。  
  
     版本 1 相容性模式適用于整個過程和流程中的所有應用程式域。  
  
## <a name="requirements"></a>需求  
 **平台：** 請參閱[系統需求](../../../../docs/framework/get-started/system-requirements.md)。  
  
 **標題：** MSCorEE.h  
  
 **庫：** MSCorEE.dll  
  
 **.NET 框架版本：**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>另請參閱

- [CorBindToCurrentRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntime 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntime-function.md)
- [CorBindToRuntimeByCfg 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)
- [CorBindToRuntimeHost 函式](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimehost-function.md)
- [ICorRuntimeHost 介面](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [已被取代的 CLR 裝載函式](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
