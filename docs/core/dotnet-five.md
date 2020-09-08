---
title: .NET Core 到 .NET 5 的演進
description: 深入瞭解 .NET 5，這是一個跨平臺和開放原始碼的開發平臺，也就是 .NET Core 的下一次演進。
ms.date: 09/02/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: 5e8ed371173ff8b81909ceb071ed93c6b0e1eea5
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89515840"
---
# <a name="the-evolution-of-net-core-to-net-5"></a>.NET Core 到 .NET 5 的演進

本文將詳細說明 .NET 5 中包含的專案，這是下一個 .NET Core 3.1 版。 版本號碼是5.0，以避免與 .NET Framework 4.x 混淆。 和 "Core" 會從名稱中卸載，因為它是持續進行的 .NET 主要執行。 ASP.NET Core 保留 "Core" 的名稱，以避免與 ASP.NET MVC 5 混淆。 此外，Entity Framework Core 會保留 "Core" 的名稱，以避免與 Entity Framework 5 和6混淆。 .NET 5 支援的應用程式類型和平臺比 .NET Core 或 .NET Framework 更多。

.NET Core 的問世以吸引人的方式發展 .NET 生態系統。 它已在 GitHub 上以開放原始碼專案的形式成熟，並可在一段時間後，慶祝誠懇改進。

.NET Core 有幾個主要特性：

> [!div class="checklist"]
>
> - 跨平台
> - 開放原始碼
> - 並存安裝
> - 小型專案檔案 (SDK 樣式的) 
> - 彈性部署

.NET 5 擴充了這些特性，可進行累加式改善：

- 單一檔案應用程式
- Windows ARM64 和 ARM64 內建函式
- 的效能改進：
  - [垃圾收集 (GC) ](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [System.Text.Json](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [System.Text.RegularExpressions](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [非同步 ValueTask 共用](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [更多區域](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- 容器大小優化
- [應用程式修剪](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- [C # 編譯器增強功能](https://devblogs.microsoft.com/dotnet/automatically-find-latent-bugs-in-your-code-with-net-5)
- 傾印偵錯工具的工具支援
- 平臺是以[可為 null 的參考](../csharp/nullable-references.md)型別標注的80%

### <a name="what-net-5-is-not"></a>什麼是 .NET 5

.NET 5 不是 .NET Framework 的替代方案。 沒有將下列技術從 .NET Framework 移植到 .NET 5 的計畫，但 .NET 5 中包含支援的替代方案：

| 技術                             | 建議                                              |
|----------------------------------------|-------------------------------------------------------------|
| Web Form                              | [ASP.NET Core Blazor](/aspnet/core/blazor)                  |
| Windows Communication Foundation (WCF) | [gRPC](/aspnet/core/grpc)                                   |
| Windows Workflow (WF)                   | [開放原始碼 CoreWF](https://github.com/UiPath-Open/corewf) |

## <a name="net-standard"></a>.NET Standard

新的應用程式開發可以 `net5.0` 針對所有專案類型（包括類別庫）指定目標 framework 標記 (TFM) 。 在 .NET 5 工作負載之間共用程式碼已經過簡化，您只需要 `net5.0` TFM。

`net5.0`TFM 結合和取代 `netcoreapp` 和 `netstandard` 名稱。 這種 TFM 通常只包含可跨平臺運作的技術，例如使用 .NET Standard 完成。 但是，如果您打算在 .NET Framework、.NET Core 和 .NET 5 工作負載之間共用程式碼，您可以藉由指定 TFM 來進行 `netstandard2.0` 。 如需詳細資訊，請參閱 [如何指定目標 framework](../standard/frameworks.md#how-to-specify-target-frameworks)。

## <a name="language-updates"></a>語言更新

使用 .NET 5，.NET 程式設計語言仍會持續改進。

### <a name="c-updates"></a>C # 更新

撰寫 .NET 5 應用程式的開發人員可以存取最新的 c # 版本和功能。 .NET 5 與 c # 9 配對。 C # 9 將許多新功能帶入語言，以下提供一些重點：

- 記錄：行為類似實值型別的不可變引用型別，並且會在語言中引入新的 `with` 關鍵字。
- 關聯式模式比對：將模式比對功能延伸至關聯評估和運算式的關係運算子，包括邏輯模式-新的關鍵字 `and` 、 `or` 和 `not` 。
- 最上層語句：作為加速採用和學習 c # 的方法，您 `Main` 可以省略方法，並將應用程式視為有效，如下所示：

   ```csharp
   System.Console.Write("Hello world!");
   ```

- 函式指標：語言結構會公開下列中繼語言 (IL) 碼碼： `ldftn` 和 `calli` 。

如需可用 c # 9 功能的詳細資訊，請參閱 [c # 9 的新](../csharp/whats-new/csharp-9.md)功能。

#### <a name="source-generators"></a>來源產生器

除了一些醒目提示的新 c # 功能之外，來源產生器也會將其轉換成開發人員專案。 來源產生器可讓在編譯期間執行的程式碼檢查您的程式，並產生與其余程式碼一起編譯的其他檔案。

如需來源產生器的詳細資訊，請參閱 [c # 來源](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) 產生器和 [c # 來源](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples)產生器範例簡介。

### <a name="f-updates"></a>F # 更新

F # 是 .NET 功能性程式設計語言，而在 .NET 5 中，開發人員可以存取 F # 5。 以下是 F # 5 的幾項新功能：

#### <a name="interpolated-strings"></a>插入字串

類似于 c # 中的字串插值，甚至 JavaScript-F # 都支援基本的字串插補。

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

除了基底字元串插補，還有具類型的插補。 使用具類型的插補時，指定的類型必須符合格式規範。

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

這類似于 [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) 根據型別安全輸入來格式化字串的函式。 <!-- For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md). -->

### <a name="visual-basic-updates"></a>Visual Basic 更新

.NET 5 中沒有適用于 Visual Basic 的新語言功能。 不過，在 .NET 5 中，Visual Basic 支援延伸至：

| 描述                            | `dotnet new` 參數 |
|----------------------------------------|------------------------|
| 主控台應用程式                    | `console`              |
| 類別庫                          | `classlib`             |
| WPF 應用程式                        | `wpf`                  |
| WPF 類別庫                      | `wpflib`               |
| WPF 自訂控制項程式庫             | `wpfcustomcontrollib`  |
| WPF 使用者控制項程式庫               | `wpfusercontrollib`    |
| Windows Forms (WinForms) 應用程式   | `winforms`             |
| Windows Forms (WinForms) 類別庫 | `winformslib`          |
| 單元測試專案                      | `mstest`               |
| NUnit 3 測試專案                   | `nunit`                |
| NUnit 3 測試項目                      | `nunit-test`           |
| xUnit 測試專案                     | `xunit`                |

如需 .NET CLI 專案範本的詳細資訊，請參閱 [`dotnet new`](tools/dotnet-new.md) 。

## <a name="net-maui"></a>.NET MAUI

.NET MAUI 是日益普及的 Xamarin 工具組演進，在 GitHub 上的開放原始碼位於 [dotnet/MAUI](https://github.com/dotnet/maui)。 使用 .NET MAUI，可簡化 .NET 開發人員的選擇，提供支援所有新式工作負載的單一堆疊： Android、iOS、macOS 和 Windows。 使用 .NET MAUI，您可以取得以多個平臺和裝置為目標的單一專案開發人員體驗。

> [!IMPORTANT]
> .NET MAUI 是早期預覽版本。 您可以在 [xamarin/net6](https://github.com/xamarin/net6-samples)範例中找到範例原始程式碼。

### <a name="model-view-update-pattern"></a>模型-視圖-更新模式

開發人員喜歡新式開發模式。 「榆樹架構」是一種流暢的 UI 開發方法，它是 [模型視圖-更新](https://elmprogramming.com/model-view-update-part-1.html) 或 MVU 模式。 MVU 可提升資料和狀態管理的單向流程，以及程式碼優先的開發經驗，只要套用必要的變更，就能快速更新 UI。

例如，請考慮使用 MVU 模式，以 .NET MAUI 撰寫的下列計數器：

```csharp
readonly State<int> _count = 0;

[Body]
View body() => new StackLayout
{
    new Label("Welcome to .NET MAUI!"),
    new Button(
        () => $"You clicked {_count} times.",
        () => ++ _count.Value)
    )
};
```

如需詳細資訊，請參閱 [.NET MAUI 藍圖](https://github.com/dotnet/maui/wiki/Roadmap)和 [.net MAUI 簡介](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) 文章。

## <a name="see-also"></a>另請參閱

- [一個 .NET 的旅程](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [.NET 5 的效能改進](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
