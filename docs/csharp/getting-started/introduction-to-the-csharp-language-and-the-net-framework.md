---
title: 'C # 語言和 .NET 簡介'
description: 了解 C# 與 .NET 的基本概念。 取得 C# 語言與 .NET 生態系統的概觀。
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: 9e84726a8f6056c5beeedae9081a68980150efdd
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465165"
---
# <a name="introduction-to-the-c-language-and-net"></a>C # 語言和 .NET 簡介

C # 是一種簡潔且型別安全的物件導向語言，可讓開發人員建立可在 .NET 生態系統中執行的各種安全且穩固的應用程式。 .NET 生態系統是由 .NET 的所有實作為所組成，其中包括但不限於 [.Net Core](../../core/introduction.md)，以及 [.NET Framework](../../framework/index.yml)。 本文著重于 .NET Framework。 您可以使用 C# 建立 Windows 用戶端應用程式、XML Web 服務、分散式元件、主從應用程式、資料庫應用程式，而且還不僅止於此。

> [!NOTE]
> Visual C# 文件假設您了解基本程式設計概念。 如果您是新手，可能會想要瀏覽網站上提供的 Visual C# Express。 您也可以利用 C# 的相關書籍和 Web 資源來了解實用的程式設計技能。

## <a name="c-language"></a>C# 語言

C# 語法的表達能力相當高，同時也很簡單且易於了解。 任何熟悉 C、c + + 或 JAVA 的人，都能立即辨識出 c # 的大括弧語法。 知道這些語言的程式開發人員通常可以在短時間內開始有效率地使用 c #。 C # 語法簡化了 c + + 的許多複雜性，並提供可為 null 的類型、列舉、委派、lambda 運算式和直接記憶體存取等強大功能。 C# 支援泛型方法和型別，提供更高的型別安全和效能。C# 也支援迭代器，讓集合類別的實作者定義自訂的反覆項目表現方式，使得用戶端程式碼可以容易地使用。  (LINQ) 運算式的語言整合式查詢，讓強型別查詢成為第一級的語言結構。

C# 為物件導向語言，支援封裝、繼承和多型的概念。 包括應用程式的進入點 `Main` 方法在內，所有變數和方法都會封裝在類別定義內。 類別可直接繼承自一個父類別，但可以實作數目不拘的介面。 覆寫父類別中虛擬方法的方法需要利用 `override` 關鍵字，避免意外重複定義。 在 C# 中，結構就像輕量型的類別。它是堆疊配置型別，可以實作介面，但不支援繼承。

除了這些基本物件導向準則，C# 可讓您透過許多創新的語言建構，輕鬆地開發軟體元件，包括下列各項︰

- 稱為「委派」** 的封裝方法簽章，可啟用型別安全事件通知。
- 屬性，可做為私用成員變數的存取子。
- 屬性，可在執行階段提供有關型別的宣告式中繼資料。
- 內嵌 XML 文件註解。
-  (LINQ) 的語言整合式查詢，可跨各種資料來源提供內建的查詢功能。

如果您必須與 COM 物件或原生 Win32 DLL 等其他 Windows 軟體互動，您可以在 C# 中透過稱為 "Interop" 的處理序來達到此目的。 Interop 幾乎可讓 C# 程式執行大部分原生 C++ 應用程式的功能。 C # 甚至還支援指標和「unsafe」程式碼的概念，在這些情況下，直接記憶體存取是很重要的。

相較於 C 和 C++，C# 建置流程相當簡單，也比 Java 更有彈性。 沒有個別標頭檔，也不需要以特定順序宣告方法和型別。 C# 原始程式檔可以定義數目不拘的類別、結構、介面及事件。

下列是一些其他 C# 資源：

- 如需此語言的一般簡介，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的第 1 章。
- 如需有關 C# 語言特定層面的詳細資訊，請參閱 [C# 參考](../language-reference/index.md)。
- 如需 LINQ 的詳細資訊，請參閱 [linq (語言整合查詢) ](../programming-guide/concepts/linq/index.md)。

## <a name="net-platform-architecture"></a>.NET 平臺架構

C # 程式是在 .NET 上執行，這是 Windows 的整陣列件，其中包括稱為 common language runtime (CLR) 的虛擬執行系統，以及一組整合的類別庫。 CLR 是由 Microsoft 通用語言基礎結構 (CLI) 的商業實作，此國際標準是建立各種語言和程式庫都能一起順暢執行和開發環境的基礎。

以 c # 撰寫的原始程式碼會編譯成符合 CLI 規格 [ (IL) 的中繼語言 ](../../standard/managed-code.md) 。 IL 程式碼和像是點陣圖和字串的資源，會以稱為組件的可執行檔儲存在磁碟上，副檔名通常為 .exe 或 .dll。 組件包含的資訊清單提供有關組件的型別、版本、文化特性及安全性需求資訊。

C# 程式執行時，組件會載入至 CLR，根據資訊清單中的資訊執行各種不同動作。 然後，如果符合安全性需求，CLR 會執行即時 (JIT) 編譯，以將 IL 程式碼轉換成原生電腦指令。 CLR 也提供有關自動記憶體回收、例外狀況處理和資源管理的其他服務。 CLR 所執行的程式碼有時稱為「managed 程式碼」，相較于「非受控碼」，它會編譯成以特定系統為目標的原生電腦語言。 下圖說明 c # 原始程式碼檔、.NET 類別庫、元件和 CLR 的編譯時期和執行時間關聯性。

![從 C# 原始程式碼到電腦執行](./media/introduction-to-the-csharp-language-and-the-net-framework/net-architecture-relationships.png)

語言互通性是 .NET 的一項重要功能。 由於 C# 編譯器所產生的 IL 程式碼符合通用型別規格 (CTS)，所以從 C# 產生的 IL 程式碼可以和從 Visual Basic、Visual C++ 的 .NET 版本所產生的程式碼互動，或和 20 種以上的任何其他 CTS 相容語言互動。 單一元件可能包含多個以不同 .NET 語言撰寫的模組，而類型可以彼此參考，如同以相同語言撰寫的一樣。

除了執行時間服務以外，.NET 還包含多個分類為命名空間的4000類別程式庫，提供各種有用的功能，從檔案輸入和輸出到字串操作到 XML 剖析，到 Windows Forms 控制項都有。 一般 c # 應用程式會廣泛使用 .NET 類別庫來處理常見的「配管」工作。

如需 .NET Framework 的詳細資訊，請參閱 [Microsoft.NET Framework 概觀 (英文)](../../framework/get-started/overview.md)。

## <a name="see-also"></a>另請參閱

- [Visual C# 使用者入門](/visualstudio/ide/quickstart-csharp-console)
