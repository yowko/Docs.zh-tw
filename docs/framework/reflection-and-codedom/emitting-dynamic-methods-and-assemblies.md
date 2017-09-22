---
title: "發出動態方法和組件"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.assetid: 8e8e2631-62fd-40e7-a8ee-0039b06749bc
caps.latest.revision: 18
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c28a5b71a93ea5159adc73316771d490dbe0db87
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 發出動態方法和組件
本節說明 <xref:System.Reflection.Emit> 命名空間中的一組 Managed 類型，它可讓編譯器或工具在執行階段發出中繼資料和 Microsoft 中繼語言 \(MSIL\)，以及選擇性地在磁碟上產生可攜式執行檔 \(PE\)。  指令碼引擎和編譯器是此命名空間的主要使用者。  在本節中，<xref:System.Reflection.Emit> 命名空間所提供的功能稱為反映發出。  
  
 反映發出提供下列功能：  
  
-   使用 <xref:System.Reflection.Emit.DynamicMethod> 類別，在執行階段定義輕量型全域方法，並使用委派加以執行。  
  
-   在執行階段定義組件，然後加以執行，並\/或儲存至磁碟。  
  
-   在執行階段定義組件、加以執行，然後將其卸載，並允許記憶體回收，以回收其資源。  
  
-   在執行階段定義新組件中的模組，然後加以執行，並\/或儲存至磁碟。  
  
-   在執行階段定義模組中的類型、建立這些類型的執行個體，並叫用其方法。  
  
-   針對已定義的模組，定義可供工具 \(例如偵錯工具和程式碼分析工具\) 使用的符號資訊。  
  
 除了 <xref:System.Reflection.Emit> 命名空間中的 Managed 類型，還有[中繼資料介面](../../../ocs/framework/unmanaged-api/metadata/metadata-interfaces.md)參考文件中說明的 Unmanaged 中繼資料介面。  相較於 Unmanaged 中繼資料介面，Managed 反映發出提供較強的語意錯誤檢查，以及抽象層級較高的中繼資料。  
  
 另一項適用於中繼資料和 MSIL 的有用資源，是通用語言基礎結構 \(CLI\) 文件，尤其是＜第二部分：中繼資料定義和語意＞以及＜第三部分：CIL 指令集＞。  您可以在 [MSDN](http://go.microsoft.com/fwlink/?LinkID=65555) 和 [Ecma 網站](http://go.microsoft.com/fwlink/?LinkId=116487)上，線上取得該文件。  
  
## 在本節中  
 [反映發出中的安全性問題](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
 說明有關使用反映發出來建立動態組件的安全性問題。  
  
## 參考  
 <xref:System.Reflection.Emit.OpCodes>  
 將可用來建置方法主體的 MSIL 指令碼編製目錄。  
  
 <xref:System.Reflection.Emit>  
 包含用來發出動態方法、組件和類型的 Managed 類別。  
  
 <xref:System.Type>  
 說明 <xref:System.Type> 類別，其代表 Managed 反映和反映發出中的類型，且其為使用這些技術的關鍵。  
  
 <xref:System.Reflection>  
 包含用來探索中繼資料和 Managed 程式碼的 Managed 類別。  
  
## 相關章節  
 [反映](../../../docs/framework/reflection-and-codedom/reflection.md)  
 說明如何探索中繼資料和 Managed 程式碼。  
  
 [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 提供 .NET Framework 中的組件概觀。

