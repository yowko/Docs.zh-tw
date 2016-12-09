---
title: "關於 .NET"
description: "了解 .NET 平台。"
keywords: .NET, .NET Core
author: richlander
ms.author: ronpet
ms.date: 10/31/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: bbfe6465-329d-4982-869d-472e7ef85d93
translationtype: Human Translation
ms.sourcegitcommit: 254e89abefd28419bd2f36a047e4df939f7ff8da
ms.openlocfilehash: 8eb9274def2683fae20765cbf701b706293744fc

---

# <a name="net-platform-guide"></a>.NET 平台指南

> [!NOTE]
此文章將會改寫。

> 如需了解如何建立簡單的 .NET Core 應用程式，請參閱[＜.NET Core 使用者入門＞教學課程](../core/getting-started.md)。 只需要幾分鐘，您就可以啟動並執行您的第一個應用程式。

.NET 是一般用途開發平台。 它可用於使用一般用途方案的任何應用程式類型或工作負載。 它包含幾項對許多開發人員而言具吸引力的重要功能，包括自動記憶體管理和現代程式語言，可讓您更輕鬆且有效率地建置高品質應用程式。 .NET 支援具有許多便利功能的高層級程式設計環境，同時提供原生記憶體和 API 的低層級存取。

C#、F# 和 Visual Basic 是依賴 .NET 平台並以其為目標的熱門語言。 .NET 語言以其非同步程式設計模型、Language Integrated Query、泛型型別和型別系統反映等重要功能聞名。 這些語言也提供物件導向和功能性程式設計範例的絕佳選項。

這些語言不僅在原理和語法方面，在共用型別系統所提供的對稱方面也有絕佳的多樣性。 此型別系統是由基礎執行階段環境提供。 .NET 的設計中心概念是「Common Language Runtime」，可支援各種不同語言 (例如動態和靜態型別語言) 的需求，並允許這些語言之間的互通性。 例如，您可以將 `People` 物件集合傳遞給不同的語言，而不會遺失語意或功能。

根據指定平台基礎的開放 [.NET 標準](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md)，您可以使用多種 [.NET 實作和產品](components.md)。 這些實作和產品分別針對不同的應用程式類型 (例如傳統型、行動、遊戲、雲端) 進行最佳化，並支援許多晶片 (例如 x86/x64、ARM) 和作業系統 (例如 Windows、Linux、iOS、Android、macOS)。 開放原始碼也是 .NET 生態系統很重要的一部分，具有多項 .NET 實作，並有許多經 OSI 核准授權的程式庫可用。

- 了解 [C#](../csharp/index.md)
- 了解 [F#](../fsharp/index.md)
- 瀏覽 [.NET API 程式庫](../../api/index.md)
- [Common Language Runtime 簡介](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/intro-to-clr.md)

<a name="fundamentals"></a>Fundamentals
------------

**多國語言** -- .NET 提供定義完善的型別系統、檔案格式、執行階段、架構和工具，可供多種語言使用，不僅可單獨執行，也可與使用相同 .NET 元件作為共用元件的其他語言互通。

**Managed 記憶體** -- .NET 會透過記憶體回收行程自動為您管理記憶體。 它可確保您永遠參考實際物件，並確保您避免難處理的問題，例如緩衝區滿溢和存取違規。 這包括陣列界限檢查。

**型別安全** -- 主要 .NET 模型是以「型別」來表示功能和記憶體。 型別可定義圖形並選擇性定義行為。 此執行階段可確保呼叫程式碼只能根據其定義和成員的指定可見度來操作型別，並提供一致、可靠且安全的結果。

<a name="features"></a>功能
--------

**使用者定義的實值型別** -- 實值型別是有用的型別分類，因為它們與類別一樣，提供「以傳值方式」的語意，而不是「以傳址方式」。 實值型別對於數值資料最有用。 .NET 支援基本型別 (例如整數) 和使用者定義型別的實值型別。

**泛型型別** -- 泛型型別是具有一或多個型別參數的型別，可在每次具現化時加以指定。 這對許多型別都很有用，如未指定，則會將內容公開為物件類型，或需要多個類型定義。 例如，您可以針對人員、GPS 位置或字串，指定集合類型的具現化。

**反映** -- .NET 會定義描述二進位檔內型別的中繼資料格式。 反映子系統會使用此資料來公開 API，以在執行階段讀取及具現化型別。 這項功能非常適合不方便事先知道程式之實際實作的動態情節。

**彈性產生程式碼** -- .NET 並未指定特定方法來將 .NET 二進位檔轉換成機器碼。 您可以使用許多方法來達成，包括解譯、Just-In-Time (JIT) 編譯、支援 JIT 後援的預先 (AOT) 編譯，以及不支援 JIT 後援的 AOT 編譯。 上述每種策略都很有價值，而且有時候會一起使用。

**跨平台** -- .NET 一開始就是為了跨平台使用。 此二進位格式和指令集適用於各種作業系統、CPU 和指標大小。 內建於 2000 版並可在 32 位元 Windows 電腦上執行的指定 .NET 二進位檔，可在 ARM64 iOS 裝置上以 2016 版執行，而不需要任何修改。

<a name="open-source"></a>開啟原始檔
-----------

.NET 的 [.NET Core](https://github.com/dotnet/core) 和 [Mono](https://github.com/mono/mono) 實作是使用 MIT 授權的開放原始碼。 文件使用 [Creative Commons CC-BY](https://creativecommons.org/licenses/by/4.0/) 授權。 .NET Core 和 Mono 是由 Microsoft 贊助，並有許來自該社群的參與者。 

這些一般用途執行階段可作為學術研究、教學/學習或商業產品的基礎。 其開放本質也表示任何人都可以在發生錯誤或需要新功能的情況下，回溯參與上游產品程式碼。

<a name="projects"></a>專案
--------

- [CoreCLR](https://github.com/dotnet/coreclr) - .NET Core 所使用的 .NET 執行階段。
- [Mono](https://github.com/mono/mono) - Xamarin 等所使用的 .NET 執行階段。
- [CoreFX](https://github.com/dotnet/coreclr) - .NET Core 所使用及 Mono 透過來源共用在一定程度上使用的 .NET 類別庫。
- [Roslyn](https://github.com/dotnet/roslyn) - 大多數 .NET 平台和工具所使用的 C# 和 Visual Basic 編譯器。 公開 API 以讀取、撰寫及分析原始程式碼。
- [F#](https://github.com/microsoft/visualfsharp) - F# 編譯器。
- [Xamarin SDK](http://open.xamarin.com) - 在 C# 和 F# 中撰寫 Android、iOS 和 macOS 所需的工具和程式庫。

<a name="standardized"></a>標準化
------------

.NET 是透過開放 [ECMA 標準](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md)所指定，該標準概述其功能，並可用來建立新的實作。 還有其他 .NET 實作，其中 Mono 和 Unity 是除了 Microsoft 以外最熱門的實作。




<!--HONumber=Nov16_HO3-->


