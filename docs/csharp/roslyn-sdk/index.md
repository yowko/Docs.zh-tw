---
title: .NET Compiler Platform SDK (Roslyn API)
description: 了解如何使用.NET 編譯器平台 SDK (亦稱為 Roslyn API) 來了解 .NET 程式碼、找出錯誤，並修正那些錯誤。
ms.date: 10/10/2017
ms.custom: mvc
---

# <a name="the-net-compiler-platform-sdk"></a>.NET 編譯器平台 SDK

當編譯器驗證應用程式程式碼的語法和語意時，會同時建置該程式碼的詳細模型。 其使用此模型從原始程式碼建置可執行檔輸出。 .NET 編譯器平台 SDK 提供對此模型的存取權。 目前，我們越來越依賴整合式開發環境 (IDE) 功能來提高我們的生產力，例如 IntelliSense、重構、智慧型重新命名、「尋找所有參考」和「移至定義」。 我們依賴程式碼分析工具來改善程式碼品質，並依賴程式碼產生器來協助建構應用程式。 隨著這些工具變得越來越聰明，當它們處理應用程式程式碼時，需要存取越來越多只有編譯器會建立的模型。 這就是 Roslyn API 的核心任務：開啟黑箱並允許工具和使用者共用編譯器所擁有關於程式碼的豐富資訊。
使用 Roslyn 時，編譯器會成為平台，而不是不透明的的輸入原始程式碼、輸出物件程式碼程序：您可以為您的工具與應用程式中之程式碼相關工作使用的 API。

## <a name="net-compiler-platform-sdk-concepts"></a>.NET 編譯器平台 SDK 概念

.NET 編譯器平台 SDK 可大幅降低建立以程式碼為中心之工具和應用程式的入門障礙。 它在多個領域中創造了許多創新的機會，例如中繼程式設計、程式碼產生和轉換、C# 和 VB 語言的交互使用，以及在網域特定語言中內嵌 C# 和 VB。

.NET 編譯器平台 SDK 可讓您建置「分析器」和「程式碼修正」，以尋找並更正程式碼錯誤。 「分析器」了解程式碼的語法和結構，並會偵測應該修正的做法。 「程式碼修正」提供一或多個建議的修正，以解決分析器所發現的程式碼錯誤。 一般而言，分析器和相關聯的程式碼修正會一起封裝在單一專案中。

分析器和程式碼修正會使用靜態分析來了解程式碼。 它們不會執行程式碼或提供其他測試優點。 不過，它們可以指出通常會導致錯誤、無法維護的程式碼，或標準指導方針驗證的做法。

.NET 編譯器平台 SDK 提供一組 API，可讓您檢查並了解 C# 或 Visual Basic 程式碼基底。 因為您可以使用這個單一程式碼基底，所以您可以更輕鬆地撰寫分析器和程式碼修正，方法是使用 .NET 編譯器平台 SDK 所提供的語法和語意分析 API。 擺脫由編譯器完成的大型複寫工作，您可以專注於更需要關注的工作，像是尋找並更正您的專案或程式庫的常見程式碼錯誤。

一個較小的優點是您的分析器和程式碼修正較小，如果您撰寫自己的程式碼基底以了解專案中的程式碼，在 Visual Studio 中載入這些分析器和程式碼修正，會使用比原來更少的記憶體。 透過使用由編譯器和 Visual Studio 所使用的相同類別，您可以建立您自己的靜態分析工具。 這表示您的小組可以使用分析器和程式碼修正，而不會明顯影響 IDE 的效能。

撰寫分析器和程式碼修正有三種主要案例：

1. [*強制執行小組程式碼撰寫標準*](#enforce-team-coding-standards)
1. [*提供程式庫套件指導方針*](#provide-guidance-with-library-packages)
1. [*提供一般指導方針*](#provide-general-guidance)

## <a name="enforce-team-coding-standards"></a>強制執行小組程式碼撰寫標準

許多小組有透過與其他小組成員的程式碼檢閱而強制執行的程式碼撰寫標準。 分析器和程式碼修正可讓此程序更有效率。 當開發人員與小組的其他人共用其工作時，就會發生程式碼檢閱。 在得到任何註解之前，開發人員將會投資所有所需的時間完成一個新功能。 當開發人員加強不符合小組做法的習慣時，可能會經過數週的時間。

分析器執行的方式，就如同開發人員撰寫程式碼。 開發人員會取得立即意見反應，可鼓勵立即遵循指導方針。 當開發人員開始進行原型設計時，就能建立習慣以撰寫符合規範的程式碼。 當功能準備好供人員檢閱時，所有的標準指導方針都已經強制執行。

小組可以建置分析器和程式碼修正，來尋找違反小組程式碼撰寫做法的最常見做法。 這些分析器和程式碼修正可以安裝在每個開發人員的電腦上，以強制執行標準。

## <a name="provide-guidance-with-library-packages"></a>提供程式庫套件指導方針

針對 NuGet 上的 .NET 開發人員，有豐富的程式庫可以使用。
部分的程式庫來自 Microsoft，部分則來自協力廠商，還有一些來自社群成員和志工。 當開發人員成功使用那些程式庫時，這些程式庫就會得到更多的採用與更高的評價。

除了提供文件以外，您還可以提供分析器和程式碼修正，來尋找並更正您的程式庫的常見錯誤用法。 這些立即更正可協助開發人員更快速地成功。

您可以在 NuGet 上將分析器和程式碼修正與您的程式庫一起封裝。 在該案例中，安裝您的 NuGet 套件的每位開發人員也將會安裝分析器套件。 使用您的程式庫的所有開發人員將會以立即錯誤回應與建議的更正的形式，立即收到來自您小組的指導方針。

## <a name="provide-general-guidance"></a>提供一般指導方針

.NET 開發人員社群已經透過運作良好以及最好避免的體驗模式進行探索。 數個社群成員已建立分析器，強制執行那些建議的模式。 隨著我們進一步了解，總有新的想法。

這些分析器可以上傳至 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs) 並讓使用 Visual Studio 的開發人員下載。 不熟悉語言和平台的新手能快速了解可接受的做法，並搶先別人在其 .NET 旅程變得更有生產力。 因為這些做法已廣泛使用，所以社群也加以採用。

## <a name="next-steps"></a>後續步驟

.NET 編譯器平台 SDK 包含了用於程式碼產生、分析和重構的最新語言物件模型。 本節提供 .NET 編譯器平台 SDK 的概念性概觀。 如需詳細資訊，請參閱快速入門、範例和教學課程等節。

您可以在下列五個主題中深入了解 .NET 編譯器平台 SDK 中的概念：

- [利用語法視覺化檢視探索程式碼](syntax-visualizer.md)
- [了解編譯器 API 模型](compiler-api-model.md)
- [使用語法](work-with-syntax.md)
- [使用語意](work-with-semantics.md)
- [使用工作區](work-with-workspace.md)

若要開始使用，您必須安裝 **.NET Compiler Platform SDK**：

[!INCLUDE[interactive-note](~/includes/roslyn-installation.md)]

<!--

Turn this on as more of the conceptual content is in place:
- Try the [Quickstarts](quickstart/index.md) to create your first tutorial.
- Experiment with one of the [Tutorials](tutorials/index.md).
- Explore the [Samples](samples/index.md) to see some simple analyzers.
- Read the [Concepts](concepts/index.md) to understand the ideas behind analyzers and code fixes.

-->
