---
title: .NET Framework 4 和 4.5 中新增的 CLR 裝載介面
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: aea88430d8f83234a1568bcaf433c2a75492e23a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195918"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>.NET Framework 4 和 4.5 中新增的 CLR 裝載介面
本節說明非受控主機可用來將 .NET Framework 4、.NET Framework 4.5 和更新版本中的 common language runtime （CLR）整合到其應用程式的介面。 這些介面會提供方法，讓主機設定並將執行時間載入進程中。  
  
 從 .NET Framework 4 開始，所有的裝載介面都具有下列特性：  
  
- 它們會使用存留期管理（`AddRef` 和 `Release`）、封裝（隱含內容）和 COM `QueryInterface`。  
  
- 它們不會使用 COM 類型，例如 `BSTR`、`SAFEARRAY`或 `VARIANT`。  
  
- 沒有使用[CoCreateInstance 函數](https://go.microsoft.com/fwlink/?LinkId=142894)的單元模型、匯總或登錄啟用。  
  
## <a name="in-this-section"></a>本章節內容  
 [ICLRAppDomainResourceMonitor 介面](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 提供可檢查應用程式域記憶體和 CPU 使用量的方法。  
  
 [ICLRDomainManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 可讓主機指定將用來初始化預設應用程式域的應用程式網域管理員，以及指定初始化屬性。  
  
 [ICLRGCManager2 介面](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 提供[SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)方法，可讓主機將垃圾收集區段的大小，以及垃圾收集系統層代0的大小上限設定為大於 `DWORD`的值。  
  
 [ICLRMetaHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 提供的方法會傳回 CLR 的特定版本、列出所有已安裝的 CLRs、列出所有內含式執行時間、傳回啟用介面，以及探索用來編譯元件的 CLR 版本。  
  
 [ICLRMetaHostPolicy 介面](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 提供[GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)方法，以根據原則準則、managed 元件、版本和設定檔來提供 CLR 介面。  
  
 [ICLRRuntimeInfo 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 提供傳回特定執行時間相關資訊的方法，包括版本、目錄和載入狀態。  
  
 [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 提供基本的全域靜態函式，以強式名稱簽署元件。 所有的[ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)方法都會傳回標準 COM hresult。  
  
 [ICLRStrongName2 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 提供使用 SHA-2 安全雜湊演算法（SHA-256、SHA-384 和 SHA-512）群組建立強式名稱的功能。  
  
 [ICLRTask2 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 提供[ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)的所有功能;此外，也提供可讓執行緒中止在目前線程上延遲的方法。  
  
## <a name="related-sections"></a>相關章節  
 [已被取代的 CLR 裝載介面和 Coclass](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 描述 .NET Framework 版本1.0 和1.1 所提供的主控介面。  
  
 [CLR 裝載介面](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 描述 .NET Framework 版本2.0、3.0 和3.5 所提供的主控介面。  
  
 [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 引進了 .NET Framework 中的裝載。
