---
title: 發出動態方法和組件
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
ms.openlocfilehash: fda5a20eb7798086ec10415889454b4a8beba5f3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180533"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>發出動態方法和組件

本節說明 <xref:System.Reflection.Emit> 命名空間中的一組 Managed 類型，它可讓編譯器或工具在執行階段發出中繼資料和 Microsoft 中繼語言 (MSIL)，以及選擇性地在磁碟上產生可攜式執行檔 (PE)。 指令碼引擎和編譯器是此命名空間的主要使用者。 在本節中，<xref:System.Reflection.Emit> 命名空間所提供的功能稱為反映發出。  
  
反映發出提供下列功能：  
  
- 使用 <xref:System.Reflection.Emit.DynamicMethod> 類別，在執行階段定義輕量型全域方法，並使用委派加以執行。  
  
- 在執行階段定義組件，然後加以執行，並/或儲存至磁碟。  
  
- 在執行階段定義組件、加以執行，然後將其卸載，並允許記憶體回收，以回收其資源。  
  
- 在執行階段定義新組件中的模組，然後加以執行，並/或儲存至磁碟。  
  
- 在執行階段定義模組中的類型、建立這些類型的執行個體，並叫用其方法。  
  
- 針對已定義的模組，定義可供工具 (例如偵錯工具和程式碼分析工具) 使用的符號資訊。  
  
除了 <xref:System.Reflection.Emit> 命名空間中的 Managed 類型，還有[中繼資料介面](../unmanaged-api/metadata/metadata-interfaces.md)參考文件中說明的 Unmanaged 中繼資料介面。 相較於 Unmanaged 中繼資料介面，Managed 反映發出提供較強的語意錯誤檢查，以及抽象層級較高的中繼資料。  
  
另一項適用於中繼資料和 MSIL 的有用資源，是通用語言基礎結構 (CLI) 文件，尤其是＜第二部分：中繼資料定義和語意＞以及＜第三部分：CIL 指令集＞。 這些檔可在[Ecma網站上](https://www.ecma-international.org/publications/standards/Ecma-335.htm)線上查閱。  
  
## <a name="in-this-section"></a>本節內容
  
[反射中的安全問題發出](security-issues-in-reflection-emit.md)  
說明有關使用反映發出來建立動態組件的安全性問題。  

[如何：定義和執行動態方法](how-to-define-and-execute-dynamic-methods.md)演示如何執行一個簡單的動態方法和綁定到類實例的動態方法。

[如何：定義具有反射發出的泛型型別](how-to-define-a-generic-type-with-reflection-emit.md)演示如何使用兩個類型參數創建簡單的泛型型別，如何對類型參數應用類、介面和特殊約束，以及如何創建使用類的類型參數作為參數類型和返回類型的成員。

[如何：定義具有反射發出的泛型方法](how-to-define-a-generic-method-with-reflection-emit.md)演示如何創建、發出和調用簡單的泛型方法。

[動態類型生成可收集程式集](collectible-assemblies.md)引入可收集程式集，它們是動態程式集，無需卸載創建它們的應用程式域即可卸載。
  
## <a name="reference"></a>參考  

<xref:System.Reflection.Emit.OpCodes>  
將可用來建置方法主體的 MSIL 指令碼編製目錄。  
  
<xref:System.Reflection.Emit>  
包含用來發出動態方法、組件和類型的 Managed 類別。  
  
<xref:System.Type>  
說明 <xref:System.Type> 類別，其代表 Managed 反映和反映發出中的類型，且其為使用這些技術的關鍵。  
  
<xref:System.Reflection>  
包含用來探索中繼資料和 Managed 程式碼的 Managed 類別。  
  
## <a name="related-sections"></a>相關章節  

[反射](reflection.md)  
說明如何探索中繼資料和 Managed 程式碼。  
  
[.NET 中的組件](../../standard/assembly/index.md)  
提供 .NET 實作中組件的概觀。
