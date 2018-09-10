---
title: 發出動態方法和組件
ms.date: 08/30/2017
helpviewer_keywords:
- reflection emit
- dynamic assemblies
- metadata, emit interfaces
- reflection emit, overview
- assemblies [.NET Framework], emitting dynamic assemblies
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a0ed1d02fd40a94d4ae63deea3c09b04bfc9bd8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44183128"
---
# <a name="emitting-dynamic-methods-and-assemblies"></a>發出動態方法和組件
本節說明 <xref:System.Reflection.Emit> 命名空間中的一組 Managed 類型，它可讓編譯器或工具在執行階段發出中繼資料和 Microsoft 中繼語言 (MSIL)，以及選擇性地在磁碟上產生可攜式執行檔 (PE)。 指令碼引擎和編譯器是此命名空間的主要使用者。 在本節中，<xref:System.Reflection.Emit> 命名空間所提供的功能稱為反映發出。  
  
 反映發出提供下列功能：  
  
-   使用 <xref:System.Reflection.Emit.DynamicMethod> 類別，在執行階段定義輕量型全域方法，並使用委派加以執行。  
  
-   在執行階段定義組件，然後加以執行，並/或儲存至磁碟。  
  
-   在執行階段定義組件、加以執行，然後將其卸載，並允許記憶體回收，以回收其資源。  
  
-   在執行階段定義新組件中的模組，然後加以執行，並/或儲存至磁碟。  
  
-   在執行階段定義模組中的類型、建立這些類型的執行個體，並叫用其方法。  
  
-   針對已定義的模組，定義可供工具 (例如偵錯工具和程式碼分析工具) 使用的符號資訊。  
  
 除了 <xref:System.Reflection.Emit> 命名空間中的 Managed 類型，還有[中繼資料介面](../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)參考文件中說明的 Unmanaged 中繼資料介面。 相較於 Unmanaged 中繼資料介面，Managed 反映發出提供較強的語意錯誤檢查，以及抽象層級較高的中繼資料。  
  
 另一項適用於中繼資料和 MSIL 的有用資源，是通用語言基礎結構 (CLI) 文件，尤其是＜第二部分：中繼資料定義和語意＞以及＜第三部分：CIL 指令集＞。 您可以在 [MSDN](https://go.microsoft.com/fwlink/?LinkID=65555) 以及 [Ecma 網站](https://go.microsoft.com/fwlink/?LinkId=116487)上，線上取得這份文件。  
  
## <a name="in-this-section"></a>本節內容
  
[反映發出中的安全性問題](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
說明有關使用反映發出來建立動態組件的安全性問題。  

[如何：定義和執行動態方法](how-to-define-and-execute-dynamic-methods.md)   
顯示如何執行簡單的動態方法以及繫結至類別執行個體的動態方法。

[如何：使用反映發出定義泛型型別](how-to-define-a-generic-type-with-reflection-emit.md)   
顯示如何建立具有兩個型別參數的簡單泛型型別、如何將類別、介面和特殊條件約束套用至型別參數，以及如何建立成員，以使用類別的型別參數作為參數類型及傳回型別。

[如何：使用反映發出定義泛型方法](how-to-define-a-generic-method-with-reflection-emit.md)   
顯示如何建立、發出和叫用簡單泛型方法。

[動態類型產生的可回收組件](collectible-assemblies.md)   
引進可回收組件，即動態組件，不需要卸載其建立所在的應用程式定義域即可予以卸載。
  
## <a name="reference"></a>參考資料  
 <xref:System.Reflection.Emit.OpCodes>  
 將可用來建置方法主體的 MSIL 指令碼編製目錄。  
  
 <xref:System.Reflection.Emit>  
 包含用來發出動態方法、組件和類型的 Managed 類別。  
  
 <xref:System.Type>  
 說明 <xref:System.Type> 類別，其代表 Managed 反映和反映發出中的類型，且其為使用這些技術的關鍵。  
  
 <xref:System.Reflection>  
 包含用來探索中繼資料和 Managed 程式碼的 Managed 類別。  
  
## <a name="related-sections"></a>相關章節  
 [反映](../../../docs/framework/reflection-and-codedom/reflection.md)  
 說明如何探索中繼資料和 Managed 程式碼。  
  
 [Common Language Runtime 中的組件](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 提供 .NET 實作中組件的概觀。
