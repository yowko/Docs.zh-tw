---
title: "C# 語言和 .NET Framework 簡介"
description: "了解 C# 與 .NET 的基本概念。 取得 C# 語言與 .NET 生態系統的概觀。"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: get-started-article
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: b2ffb641f436a41c97a94a6ec117f6087851d482
ms.sourcegitcommit: 8bde7a3432f30fc771079744955c75c58c4eb393
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/20/2018
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>C# 語言和 .NET Framework 簡介
C# 是型別安全的優質物件導向語言，可讓開發人員建置各種在 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 上執行且兼俱安全性與穩定性的應用程式。 您可以使用 C# 建立 Windows 用戶端應用程式、XML Web 服務、分散式元件、主從應用程式、資料庫應用程式，而且還不僅止於此。 Visual C# 提供進階的程式碼編輯器、使用方便的使用者介面設計工具、整合式偵錯工具及許多其他工具，以根據 C# 語言和 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 輕鬆地開發應用程式。  
  
> [!NOTE]
> [!INCLUDE[csprcs](~/includes/csprcs-md.md)] 文件假設您了解基本程式設計概念。 如果您是新手，可能會想要瀏覽網站上的 [!INCLUDE[csprcsxpr](~/includes/csprcsxpr-md.md)]。 您也可以利用 C# 的相關書籍和 Web 資源來了解實用的程式設計技能。  
  
## <a name="c-language"></a>C# 語言  
 C# 語法的表達能力相當高，同時也很簡單且易於了解。 熟悉 C、C++ 或 Java 的任何人都能立即辨識出 C# 的大括號語法。 了解上述任何一種語言的開發人員一般都能在極短時間內開始用 C# 有效率地工作。 C# 語法可大幅簡化 C++ 的複雜性，並提供強大的功能，例如可為 Null 的實值型別、列舉、委派、lambda 運算式，還有 Java 中所沒有的直接記憶體存取。 C# 支援泛型方法和型別，提供更高的型別安全和效能。C# 也支援迭代器，讓集合類別的實作者定義自訂的反覆項目表現方式，使得用戶端程式碼可以容易地使用。 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] 運算式可讓強型別查詢成為優先使用的語言建構。  
  
 C# 為物件導向語言，支援封裝、繼承和多型的概念。 包括應用程式的進入點 `Main` 方法在內，所有變數和方法都會封裝在類別定義內。 類別可直接繼承自一個父類別，但可以實作數目不拘的介面。 覆寫父類別中虛擬方法的方法需要利用 `override` 關鍵字，避免意外重複定義。 在 C# 中，結構就像輕量型的類別。它是堆疊配置型別，可以實作介面，但不支援繼承。  
  
 除了這些基本物件導向準則，C# 可讓您透過許多創新的語言建構，輕鬆地開發軟體元件，包括下列各項︰  
  
-   稱為「委派」的封裝方法簽章，可啟用型別安全事件通知。  
  
-   屬性，可做為私用成員變數的存取子。  
  
-   屬性，可在執行階段提供有關型別的宣告式中繼資料。  
  
-   內嵌 XML 文件註解。  
  
-   [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] 可跨各種資料來源提供內建查詢功能。  
  
 如果您必須和 COM 物件或原生 Win32 DLL 等其他 Windows 軟體互動，您可以透過稱為 "Interop" 的處理序來達到此目的。 Interop 幾乎可讓 C# 程式執行大部分原生 C++ 應用程式的功能。 對於直接記憶體存取是絕對必要的情況，C# 甚至支援指標和「不安全」的程式碼概念。  
  
 相較於 C 和 C++，C# 建置流程相當簡單，也比 Java 更有彈性。 沒有個別標頭檔，也不需要以特定順序宣告方法和型別。 C# 原始程式檔可以定義數目不拘的類別、結構、介面及事件。  
  
 下列是一些其他 C# 資源：  
  
-   如需此語言的一般簡介，請參閱 [C# 語言規格](../../csharp/language-reference/language-specification/index.md)的第 1 章。  
  
-   如需有關 C# 語言特定層面的詳細資訊，請參閱 [C# 參考](../../csharp/language-reference/index.md)。  
  
-   如需 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 的詳細資訊，請參閱 [LINQ (Language-Integrated Query)](../programming-guide/concepts/linq/index.md)。  

## <a name="net-framework-platform-architecture"></a>.NET Framework 平台架構  
 C# 程式在 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 上執行，其為 Windows 不可或缺的元件，包括稱為通用語言執行平台 (CLR) 的虛擬執行系統和整合的一組類別庫。 CLR 是由 Microsoft 通用語言基礎結構 (CLI) 的商業實作，此國際標準是建立各種語言和程式庫都能一起順暢執行和開發環境的基礎。  
  
 以 C# 撰寫的原始程式碼會編譯成符合 CLI 規格的中繼語言 (IL) 。 IL 程式碼和像是點陣圖和字串的資源，會以稱為組件的可執行檔儲存在磁碟上，副檔名通常為 .exe 或 .dll。 組件包含的資訊清單提供有關組件的型別、版本、文化特性及安全性需求資訊。  
  
 C# 程式執行時，組件會載入至 CLR，根據資訊清單中的資訊執行各種不同動作。 然後，如果符合安全性需求，CLR 就會執行 Just-In-Time (JIT) 編譯以將 IL 程式碼轉換成原生機器指令。 CLR 也提供有關自動記憶體回收、例外狀況處理和資源管理的其他服務。 由 CLR 執行的程式碼有時稱為「Managed 程式碼 」，相對於會以特定系統為目標編譯成原生機器語言的「Unmanaged 程式碼 」。 下圖說明 C# 原始程式碼檔、.NET Framework 類別庫、組件及 CLR 的編譯時期和執行階段關聯性。  
  
 ![從 C&#35; 原始程式碼到機器執行](../../csharp/getting-started/media/netarchitecture.png "NETarchitecture")  
  
 語言互通性是 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 的一項重要功能。 由於 C# 編譯器所產生的 IL 程式碼符合通用型別規格 (CTS)，所以從 C# 產生的 IL 程式碼可以和從 Visual Basic、Visual C++ 的 .NET 版本所產生的程式碼互動，或和 20 種以上的任何其他 CTS 相容語言互動。 單一組件可包含以不同的 .NET 語言撰寫的多個模組，而且型別可以彼此參考，如同它們都以相同的語言撰寫一般。  
  
 除了執行階段服務以外，[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 也包含超過 4000 種依據命名空間分類的大量類別庫，提供各式各樣的實用功能，從檔案輸入和輸出的字串操作乃至 XML 剖析，到 Windows Form 控制項的一切。 一般 C# 應用程式會使用廣泛用來處理常見「配管」例行工作的 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 類別庫。  
  
 如需 .NET Framework 的詳細資訊，請參閱 [Microsoft.NET Framework 概觀 (英文)](../../framework/get-started/overview.md)。  
  
## <a name="see-also"></a>請參閱  
 [C#](../../csharp/index.md) [Visual C# 與 Visual Basic 使用者入門](/visualstudio/ide/getting-started-with-visual-csharp-and-visual-basic)
