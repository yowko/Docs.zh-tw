---
title: .NET Framework 4 和 4.5 中新增的 CLR 裝載介面
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9086502968fb9046237e77b76b4038a9f32f4ef
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407399"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>.NET Framework 4 和 4.5 中新增的 CLR 裝載介面
本節說明 unmanaged 介面主機可用來將 common language runtime (CLR) 整合在[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]， [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]，和在其應用程式的更新版本。 這些介面提供的主機，若要設定及執行階段載入處理序的方法。  
  
 從開始[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]、 所有裝載介面具有下列特性：  
  
-   他們使用生命週期管理 (`AddRef`並`Release`)，封裝 （隱含的內容） 和`QueryInterface`從 com 存取。  
  
-   那里請不要使用 COM 類型這類`BSTR`， `SAFEARRAY`，或`VARIANT`。  
  
-   不沒有使用任何 apartment 模型、 彙總或登錄啟用[CoCreateInstance 函式](https://go.microsoft.com/fwlink/?LinkId=142894)。  
  
## <a name="in-this-section"></a>本節內容  
 [ICLRAppDomainResourceMonitor 介面](../../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 提供方法，檢查應用程式定義域的記憶體和 CPU 使用量。  
  
 [ICLRDomainManager 介面](../../../../docs/framework/unmanaged-api/hosting/iclrdomainmanager-interface.md)  
 可讓主應用程式指定將用來初始化預設的應用程式定義域，並指定初始化屬性的應用程式定義域管理員。  
  
 [ICLRGCManager2 介面](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-interface.md)  
 提供[SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)方法，讓主應用程式來設定記憶體回收集合區段的大小和記憶體回收系統的層代 0 的最大值大於`DWORD`。  
  
 [ICLRMetaHost 介面](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md)  
 提供方法，傳回特定版本的 CLR、 列出所有已安裝的 Clr、 列出所有的同處理序執行階段，傳回啟用介面，並探索用以編譯組件的 CLR 版本。  
  
 [ICLRMetaHostPolicy 介面](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-interface.md)  
 提供[GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)提供 CLR 介面的方法會根據原則準則、 managed 組件、 版本和組態檔。  
  
 [ICLRRuntimeInfo 介面](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md)  
 提供方法，傳回特定的執行階段，包括版本、 目錄和負載狀態的相關資訊。  
  
 [ICLRStrongName 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)  
 提供基本的全域靜態函式簽章以強式名稱的組件。 所有[ICLRStrongName](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)方法會傳回標準的 COM Hresult。  
  
 [ICLRStrongName2 介面](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname2-interface.md)  
 讓您能夠建立使用 sha-2 群組的安全雜湊演算法 （SHA-256、 SHA-384 和 SHA-512） 的強式名稱。  
  
 [ICLRTask2 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask2-interface.md)  
 提供的所有功能[ICLRTask 介面](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md); 此外，都提供方法，可讓執行緒中止延遲在目前的執行緒上。  
  
## <a name="related-sections"></a>相關章節  
 [已被取代的 CLR 裝載介面和 Coclass](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 描述裝載.NET framework 1.0 和 1.1 版所提供的介面。  
  
 [CLR 裝載介面](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 描述裝載以.NET Framework 版本 2.0、 3.0 和 3.5 提供的介面。  
  
 [裝載](../../../../docs/framework/unmanaged-api/hosting/index.md)  
 導入了.NET Framework 中所裝載。
