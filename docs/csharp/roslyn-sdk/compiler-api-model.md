---
title: ".NET Compiler Platform SDK 概念和物件模型"
description: "這個概觀提供有效率地使用 .NET 編譯器 SDK 所需的背景。 您將學習 API 層、所含的主要類型和整體物件模型。"
author: billwagner
ms.author: wiwagn
ms.date: 10/10/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 65a4695c6f4e5268582d83452246ed8262d6fe2f
ms.sourcegitcommit: d095094e942eedf09530ea5636fbaf9029853027
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2017
---
# <a name="understand-the-net-compiler-platform-sdk-model"></a>了解 .NET Compiler Platform SDK 模型

編譯器會處理您遵循結構化規則所撰寫的程式碼，而結構化規則通常與人們閱讀和了解程式碼的方式不同。 編譯器所使用模型的基本了解務必了解您在建置 Roslyn 工具時所使用的 API。 

## <a name="compiler-pipeline-functional-areas"></a>編譯器管線功能區域

.NET Compiler Platform SDK 透過提供可鏡像傳統編譯器管線的 API 層，以將 C# 和 Visual Basic 編譯器的程式碼分析公開為取用者。

![編譯器管線將原始程式碼處理為物件程式碼的步驟](media/compiler-pipeline.png)

此管線的每個階段都是個別元件。 首先，剖析階段會權杖化，並將原始程式文字剖析為遵循語言文法的語法。 其次，宣告階段會分析來源和已匯入的中繼資料來形成具名符號。 接下來，繫結階段會比對程式碼中的識別碼與符號。 最後，發出階段會發出具有編譯器所建置之所有資訊的組件。

![編譯器管線 API 可存取屬於編譯器管線一部分的每個步驟](media/compiler-pipeline-api.png)

對應至所有這些階段，.NET Compiler Platform SDK 會公開物件模型，以允許存取該階段的資訊。 剖析階段會公開語法樹狀結構、宣告階段會公開階層式符號表、繫結階段會公開編譯器語意分析的結果，而發出階段是產生 IL 位元組碼的 API。

![編譯器管線各步驟可從編譯器 API 使用的語言服務](media/compiler-pipeline-lang-svc.png)

每個編譯器都會將這些元件一起合併為單一端對端整體。

這些 API 是與 Visual Studio 所使用的相同。 例如，概述和格式化功能的程式碼會使用語法樹狀結構、物件瀏覽器和導覽功能會使用符號表、重構和 [移至定義] 使用語意模型，而 [編輯後繼續] 會使用所有這些項目 (包含發出 API)。 

## <a name="api-layers"></a>API 層

.NET 編譯器 SDK 包含兩個主要 API 層：編譯器 API 和工作區 API。

![編譯器管線 API 所代表的 API 層](media/api-layers.png)

### <a name="compiler-apis"></a>編譯器 API

編譯器層所包含的物件模型對應至編譯器管線的每個階段所公開的資訊 (語法和語意)。 編譯器層也包含單一編譯器叫用的不可變快照集，包含組件參考、編譯器選項和原始程式碼檔。 有兩個不同的 API 代表 C# 語言和 Visual Basic 語言。 這兩個 API 與圖形類似，但進行調整以取得所有個別語言的高畫質。 此層沒有與 Visual Studio 元件的相依性。

### <a name="diagnostic-apis"></a>診斷 API

進行分析時，編譯器可能會產生一組診斷，其涵蓋語法、語意和明確指派錯誤的所有項目，以及各種警告和參考性診斷。 編譯器 API 層會透過將使用者定義分析器插入編譯程序的可延伸 API 來公開診斷。 它可以產生使用者定義診斷 (例如 StyleCop 或 FxCop 這類工具所產生的診斷) 和編譯器定義診斷。 使用這種方式產生診斷的優點是自然與 MSBuild 和 Visual Studio 這類工具整合，而這些工具取決於下列這類體驗的診斷：根據原則來終止組建，以及在編輯器中顯示即時波浪線並建議程式碼修正。

### <a name="scripting-apis"></a>指令碼 API

裝載和指令碼 API 是編譯器層的一部分。 您可以使用它們來執行程式碼片段以及累積執行階段執行內容。
C# 互動 REPL (「讀取、求值、輸出」迴圈) 會使用這些 API。 REPL 可讓您使用 C# 作為指令碼語言，並在撰寫時以互動方式執行程式碼。

### <a name="workspaces-apis"></a>工作區 API

[工作區] 層會包含工作區 API，這是執行程式碼分析以及重構整個方案的起點。 它可協助您將方案中的所有專案資訊都組織成單一物件模型，以讓您直接存取編譯器層物件模型，而不需要剖析檔案、設定選項，或管理專案對專案相依性。

此外，工作區層具有實作程式碼分析以及重構工具時所使用的一組 API，而這些工具在 Visual Studio IDE 這類主機環境內運作。 範例包含 [尋找所有參考]、[格式] 和 [程式碼產生 API]。

此層沒有與 Visual Studio 元件的相依性。
