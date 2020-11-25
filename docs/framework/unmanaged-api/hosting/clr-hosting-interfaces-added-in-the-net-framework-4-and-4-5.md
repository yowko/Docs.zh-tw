---
title: .NET Framework 4 和 4.5 中新增的 CLR 裝載介面
ms.date: 03/30/2017
helpviewer_keywords:
- hosting interfaces [.NET Framework], version 4
- .NET Framework 4, hosting interfaces
- interfaces [.NET Framework hosting], version 4
ms.assetid: f6af6116-f5b0-4bda-a276-fffdba70893d
ms.openlocfilehash: 6ee3b8cdf348a5eade3903e2d26b4f9b93886305
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706810"
---
# <a name="clr-hosting-interfaces-added-in-the-net-framework-4-and-45"></a>.NET Framework 4 和 4.5 中新增的 CLR 裝載介面

本節描述非受控主機可用來將 .NET Framework 4、.NET Framework 4.5 和更新版本中的 common language runtime (CLR) 整合至其應用程式的介面。 這些介面會提供方法，讓主機在進程中設定和載入執行時間。  
  
 從 .NET Framework 4 開始，所有裝載介面都有下列特性：  
  
- 它們使用存留期管理 (`AddRef` 和 `Release`) ，封裝 (隱含內容) 和 `QueryInterface` COM。  
  
- 它們不會使用、或等 COM `BSTR` 類型 `SAFEARRAY` `VARIANT` 。  
  
- 沒有使用 [CoCreateInstance 函數](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)的單元模型、匯總或登錄啟用。  
  
## <a name="in-this-section"></a>本節內容  

 [ICLRAppDomainResourceMonitor 介面](iclrappdomainresourcemonitor-interface.md)  
 提供可檢查應用程式域的記憶體和 CPU 使用量的方法。  
  
 [ICLRDomainManager 介面](iclrdomainmanager-interface.md)  
 讓主機指定將用來初始化預設應用程式域的應用程式域管理員，以及指定初始化屬性。  
  
 [ICLRGCManager2 介面](iclrgcmanager2-interface.md)  
 提供 [SetGCStartupLimitsEx](iclrgcmanager2-setgcstartuplimitsex-method.md) 方法，此方法可讓主控制項將垃圾收集區段的大小以及垃圾收集系統層代0的大小上限設定為大於 `DWORD` 的值。  
  
 [ICLRMetaHost 介面](iclrmetahost-interface.md)  
 提供方法來傳回特定版本的 CLR、列出所有已安裝的 Clr、列出所有同進程執行時間、傳回啟用介面，以及探索用來編譯元件的 CLR 版本。  
  
 [ICLRMetaHostPolicy 介面](iclrmetahostpolicy-interface.md)  
 提供 [GetRequestedRuntime](iclrmetahostpolicy-getrequestedruntime-method.md) 方法，此方法會根據原則準則、managed 元件、版本和設定檔提供 CLR 介面。  
  
 [ICLRRuntimeInfo 介面](iclrruntimeinfo-interface.md)  
 提供方法來傳回特定執行時間的相關資訊，包括版本、目錄和載入狀態。  
  
 [ICLRStrongName 介面](iclrstrongname-interface.md)  
 提供基本的全域靜態函式來簽署具有強式名稱的元件。 所有 [ICLRStrongName](iclrstrongname-interface.md) 方法都會傳回標準 COM hresult。  
  
 [ICLRStrongName2 介面](iclrstrongname2-interface.md)  
 提供使用安全雜湊演算法的 SHA-1 群組來建立強式名稱的功能， (SHA-256、SHA-384 和 SHA-512) 。  
  
 [ICLRTask2 介面](iclrtask2-interface.md)  
 提供 [ICLRTask 介面](iclrtask-interface.md)的所有功能;此外，還提供可讓執行緒中止在目前線程上延遲的方法。  
  
## <a name="related-sections"></a>相關章節  

 [已被取代的 CLR 裝載介面和 Coclass](deprecated-clr-hosting-interfaces-and-coclasses.md)  
 描述 .NET Framework 版本1.0 和1.1 提供的裝載介面。  
  
 [CLR 裝載介面](clr-hosting-interfaces.md)  
 描述 .NET Framework 版本2.0、3.0 和3.5 所提供的裝載介面。  
  
 [裝載](index.md)  
 介紹 .NET Framework 中的裝載。
