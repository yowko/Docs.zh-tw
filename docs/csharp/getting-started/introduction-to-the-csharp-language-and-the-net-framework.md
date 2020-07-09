---
title: C# 語言和 .NET Framework 簡介
description: 了解 C# 與 .NET 的基本概念。 取得 C# 語言與 .NET 生態系統的概觀。
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, about C# language
- Visual C#, about
ms.assetid: 0a2dff4e-cd84-42ff-8141-e89889b24081
ms.openlocfilehash: 55b90d10a1d8ac8534ba98e1cc5af906d69822a6
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100830"
---
# <a name="introduction-to-the-c-language-and-the-net-framework"></a>C # 語言和 .NET Framework 簡介

C # 是一種簡潔且型別安全的物件導向語言，可讓開發人員建立可在 .NET 生態系統中執行的各種安全且強大的應用程式。 .NET 生態系統是由 .NET 的所有實體系組成，包括但不限於[.Net Core](../../core/index.yml)和[.NET Framework](../../framework/index.yml)。 本文著重于 .NET Framework。 您可以使用 C# 建立 Windows 用戶端應用程式、XML Web 服務、分散式元件、主從應用程式、資料庫應用程式，而且還不僅止於此。

> [!NOTE]
> Visual C# 文件假設您了解基本程式設計概念。 如果您是新手，可能會想要瀏覽網站上提供的 Visual C# Express。 您也可以利用 C# 的相關書籍和 Web 資源來了解實用的程式設計技能。

## <a name="c-language"></a>C# 語言

C# 語法的表達能力相當高，同時也很簡單且易於了解。 C # 的大括弧語法會立即可供任何熟悉 C、c + + 或 JAVA 的人辨識。 瞭解這些語言的開發人員通常可以在短時間內開始有效率地在 c # 中工作。 C # 語法簡化了 c + + 的許多複雜性，並提供強大的功能，例如可為 null 的型別、列舉、委派、lambda 運算式，以及直接記憶體存取。 C# 支援泛型方法和型別，提供更高的型別安全和效能。C# 也支援迭代器，讓集合類別的實作者定義自訂的反覆項目表現方式，使得用戶端程式碼可以容易地使用。 語言整合式查詢（LINQ）運算式會將強型別查詢設為第一類語言結構。

C# 為物件導向語言，支援封裝、繼承和多型的概念。 包括應用程式的進入點 `Main` 方法在內，所有變數和方法都會封裝在類別定義內。 類別可直接繼承自一個父類別，但可以實作數目不拘的介面。 覆寫父類別中虛擬方法的方法需要利用 `override` 關鍵字，避免意外重複定義。 在 C# 中，結構就像輕量型的類別。它是堆疊配置型別，可以實作介面，但不支援繼承。

除了這些基本物件導向準則，C# 可讓您透過許多創新的語言建構，輕鬆地開發軟體元件，包括下列各項︰

- 稱為「委派」** 的封裝方法簽章，可啟用型別安全事件通知。
- 屬性，可做為私用成員變數的存取子。
- 屬性，可在執行階段提供有關型別的宣告式中繼資料。
- 內嵌 XML 文件註解。
- 語言整合式查詢（LINQ），可在各種不同的資料來源中提供內建的查詢功能。

如果您必須與 COM 物件或原生 Win32 DLL 等其他 Windows 軟體互動，您可以在 C# 中透過稱為 "Interop" 的處理序來達到此目的。 Interop 幾乎可讓 C# 程式執行大部分原生 C++ 應用程式的功能。 C # 甚至支援指標和「unsafe」程式碼的概念，適用于直接記憶體存取非常重要的情況。

相較於 C 和 C++，C# 建置流程相當簡單，也比 Java 更有彈性。 沒有個別標頭檔，也不需要以特定順序宣告方法和型別。 C# 原始程式檔可以定義數目不拘的類別、結構、介面及事件。

下列是一些其他 C# 資源：

- 如需此語言的一般簡介，請參閱 [C# 語言規格](/dotnet/csharp/language-reference/language-specification/introduction)的第 1 章。
- 如需有關 C# 語言特定層面的詳細資訊，請參閱 [C# 參考](../language-reference/index.md)。
- 如需 LINQ 的詳細資訊，請參閱[linq （語言整合式查詢）](../programming-guide/concepts/linq/index.md)。

## <a name="net-framework-platform-architecture"></a>.NET Framework 平台架構

C# 程式在 .NET Framework 上執行，其為 Windows 不可或缺的元件，包括稱為通用語言執行平台 (CLR) 的虛擬執行系統和一組已整合類別庫。 CLR 是由 Microsoft 通用語言基礎結構 (CLI) 的商業實作，此國際標準是建立各種語言和程式庫都能一起順暢執行和開發環境的基礎。

以 c # 撰寫的原始程式碼會編譯成符合 CLI 規格的[中繼語言（IL）](../../standard/managed-code.md) 。 IL 程式碼和像是點陣圖和字串的資源，會以稱為組件的可執行檔儲存在磁碟上，副檔名通常為 .exe 或 .dll。 組件包含的資訊清單提供有關組件的型別、版本、文化特性及安全性需求資訊。

C# 程式執行時，組件會載入至 CLR，根據資訊清單中的資訊執行各種不同動作。 然後，如果符合安全性需求，CLR 會執行即時（JIT）編譯，將 IL 程式碼轉換成原生機器指令。 CLR 也提供有關自動記憶體回收、例外狀況處理和資源管理的其他服務。 CLR 執行的程式碼有時稱為「managed 程式碼」，與「非受控碼」相反，它會編譯成以特定系統為目標的原生電腦語言。 下圖說明 C# 原始程式碼檔、.NET Framework 類別庫、組件及 CLR 的編譯時期和執行階段關聯性。

![從 C# 原始程式碼到電腦執行](./media/introduction-to-the-csharp-language-and-the-net-framework/net-architecture-relationships.png)

語言互通性是 .NET Framework 的一項重要功能。 由於 C# 編譯器所產生的 IL 程式碼符合通用型別規格 (CTS)，所以從 C# 產生的 IL 程式碼可以和從 Visual Basic、Visual C++ 的 .NET 版本所產生的程式碼互動，或和 20 種以上的任何其他 CTS 相容語言互動。 單一元件可能包含多個以不同 .NET 語言撰寫的模組，而且這些類型可以彼此參考，就好像它們是以相同的語言撰寫。

除了執行階段服務以外，.NET Framework 也包含超過 4000 種依據命名空間分類的大量類別庫，提供各式各樣的實用功能，從檔案輸入和輸出的字串操作乃至 XML 剖析，到 Windows Form 控制項的一切。 一般 C# 應用程式廣泛使用 .NET Framework 類別庫處理常見的「配管」例行工作。

如需 .NET Framework 的詳細資訊，請參閱 [Microsoft.NET Framework 概觀 (英文)](../../framework/get-started/overview.md)。

## <a name="see-also"></a>另請參閱

- [Visual C# 使用者入門](/visualstudio/ide/quickstart-csharp-console)
