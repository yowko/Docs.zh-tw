---
title: "目標架構 | Microsoft Docs"
description: "以 .NET Core 應用程式和程式庫的目標架構為中心的資訊。"
keywords: ".NET, .NET Core, 架構, TFM"
author: richlander
ms.author: mairaw
ms.date: 04/27/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6ef56a2e-593d-497b-925a-1e25bb6df2e6
ms.translationtype: Machine Translation
ms.sourcegitcommit: 45835eb80642253f80ea630ae9db1ac766b72b9c
ms.openlocfilehash: 11c1f11e4f8354b7573d03e680cf4a8a16fa26d9
ms.contentlocale: zh-tw
ms.lasthandoff: 05/11/2017

---

# 目標 Framework
<a id="target-frameworks" class="xliff"></a>

「架構」定義了您用來建立應用程式和程式庫的物件、方法及工具。 .NET Framework 可用來建立應用程式和程式庫，這些應用程式和程式庫主要用來在執行 Windows 作業系統的系統上執行。 .NET Core 包含一個可讓您建置在各種作業系統上執行之應用程式和程式庫的架構。

「架構」和「平台」這兩個詞有時在措辭中的使用方式會造成混淆。 讓解釋變得更糟的是，「平台」一詞在不同的內容中有不同的意義。 例如，您會看到 ".NET Core" 在建置應用程式和程式庫的內容中被描述成「.NET Core 架構」，而在執行應用程式和程式庫程式碼的內容中則也被描述成「.NET Core 平台」。 「計算平台」描述應用程式的執行「位置與方式」。 由於 .NET Core 會使用 [.NET Core Common Language Runtime (CoreCLR)](https://github.com/dotnet/coreclr) 來執行程式碼，因此它也是一個平台。 .NET Framework 也是如此，具有 [Common Language Runtime (CLR)](clr.md) 來執行使用 .NET Framework 的架構物件、方法及工具開發的應用程式和程式庫程式碼。 經常在文件中出現的「跨平台」一詞，應該解釋為「跨作業系統和跨架構 (x86、x64、arm)」，因為這是作者通常想要傳達的意思。

架構的物件和方法稱為「應用程式開發介面」(API)。 架構 API 是在 [Visual Studio](https://www.visualstudio.com/)、[Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/)、[Visual Studio Code](https://code.visualstudio.com/) 及其他「整合式開發環境」(IDE) 和編輯器中用來提供您一組正確的開發物件和方法。 架構也可供 [NuGet](https://www.nuget.org/) 用來產生和取用 NuGet 套件，以確保您針對在應用程式或程式庫中作為目標的架構，產生及使用正確的套件。

當您「以某個架構為目標」或以數個架構為目標時，即已決定好要使用哪幾組 API 及這些 API 的哪些版本。 參考架構的方式有數種：依產品名稱、依完整或簡短格式架構名稱，以及依系列。

## 參考架構
<a id="referring-to-frameworks" class="xliff"></a>

您可以使用數種方式來參考架構，大多數這些方式都已在 .NET Core 的文件中使用。 以 .NET Framework 4.6.2 為例，會使用下列格式：

**參考產品**

您可以參考 .NET 平台或執行階段。 這兩者同樣有效。

* .NET Framework 4.6.2
* .NET 4.6.2

**參考某個架構**

您可以使用完整格式或簡短形式的 TFM，來參考架構或架構的目標。 這兩者同樣有效。

* `.NETFramework,Version=4.6.2`
* `net462`

**參考一系列的架構**

您可以使用完整格式或簡短形式的架構識別碼，來參考一系列的架構。 這兩者同樣有效。

* `.NETFramework`
* `net`

## 最新架構版本
<a id="latest-framework-versions" class="xliff"></a>

下表定義一組您可以使用的架構、其參考方式，以及它們所實作的 [.NET Standard 程式庫](library.md)版本。 這些架構版本是最新穩定版本。 不顯示發行前版本。

| 架構             | 最新的版本 | Target Framework Moniker (TFM) | Compact Target Framework Moniker (TFM) | .NET Standard 版本 | 中繼套件 |
| :-------------------: | :------------: | :----------------------------: | :------------------------------------: | :-------------------: | :---------: |
| .NET Standard         | 1.6.1          | .NETStandard,Version=1.6       | netstandard1.6                         | N/A                   | [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) |
| .NET Core 應用程式 | 1.1.1          | .NETCoreApp,Version=1.1        | netcoreapp1.1                          | 1.6                   | [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App) |
| .NET Framework        | 4.6.2          | .NETFramework,Version=4.6.2    | net462                                 | 1.5                   | N/A |

## 支援的架構
<a id="supported-frameworks" class="xliff"></a>

架構通常會由簡短的目標架構 Moniker 或 *TFM* 參考。 在 .NET Standard 中，這也會一般化為 *TxM*，以允許對多個架構的單一參考。 NuGet 用戶端支援下列架構。 對等項目會顯示在括號 (`[]`) 內。

| 名稱                       | 縮寫 | TFM/TxM                                    |
| -------------------------- | ------------ | -------------------------------------------- |
| .NET Standard              | netstandard  | netstandard1.0                               |
|                            |              | netstandard1.1                               |
|                            |              | netstandard1.2                               |
|                            |              | netstandard1.3                               |
|                            |              | netstandard1.4                               |
|                            |              | netstandard1.5                               |
|                            |              | netstandard1.6                               |
| .NET 核心                  | netcoreapp   | netcoreapp1.0                                |
|                            |              | netcoreapp1.1                                |
| .NET Framework             | net          | net11                                        |
|                            |              | net20                                        |
|                            |              | net35                                        |
|                            |              | net40                                        |
|                            |              | net403                                       |
|                            |              | net45                                        |
|                            |              | net451                                       |
|                            |              | net452                                       |
|                            |              | net46                                        |
|                            |              | net461                                       |
|                            |              | net462                                       |
| Windows 市集              | netcore      | netcore [netcore45]                          |
|                            |              | netcore45 [win, win8]                        |
|                            |              | netcore451 [win81]                           |
| .NET Micro Framework       | netmf        | netmf                                        |
| Silverlight                | sl           | sl4                                          |
|                            |              | sl5                                          |
| Windows Phone              | wp           | wp [wp7]                                     |
|                            |              | wp7                                          |
|                            |              | wp75                                         |
|                            |              | wp8                                          |
|                            |              | wp81                                         |
|                            |              | wpa81                                        |
| 通用 Windows 平台 | uap          | uap [uap10.0]                                |
|                            |              | uap10.0 [win10] [netcore50]                  |

## 已被取代的架構
<a id="deprecated-frameworks" class="xliff"></a>

下列架構已被取代。 以這些架構為目標的套件應該移轉至所指出的取代項目。

| 已被取代的架構 | Replacement |
| -------------------- | ----------- |
| aspnet50             | netcoreapp  |
| aspnetcore50         |             |
| dnxcore50            |             |
| dnx                  |             |
| dnx45                |             |
| dnx451               |             |
| dnx452               |             |
| dotnet               | netstandard |
| dotnet50             |             |
| dotnet51             |             |
| dotnet52             |             |
| dotnet53             |             |
| dotnet54             |             |
| dotnet55             |             |
| dotnet56             |             |
| netcore50            | uap10.0     |
| win                  | netcore45   |
| win8                 | netcore45   |
| win81                | netcore451  |
| win10                | uap10.0     |
| winrt                | netcore45   |

## 優先順序
<a id="precedence" class="xliff"></a>

有一些架構彼此相關且相容，但未必相等：

| 架構                        | 可使用   |
| -------------------------------- | --------- |
| uap (通用 Windows 平台) | win81     |
|                                  | wpa81     |
|                                  | netcore50 |
| win (Windows 市集)              | winrt     |
|                                  | winrt45   |

## .NET Standard
<a id="net-standard" class="xliff"></a>

[.NET Standard](https://github.com/dotnet/standard) 可簡化二進位相容架構之間的參考，讓單一目標架構參考其他項目的組合。 如需詳細資訊，請參閱 [.NET Standard 程式庫](library.md)主題。

[NuGet 工具的取得最接近的架構工具](http://nugettoolsdev.azurewebsites.net/)會模擬 NuGet 邏輯，此邏輯可用來根據專案的架構從套件中的許多可用架構資產選取一個架構。 若要使用此工具，請輸入一個專案架構和一或多個套件架構。 選取 [送出] 按鈕。 此工具會指出您列出的套件架構是否與您提供的專案架構相容。

## 可攜式類別庫
<a id="portable-class-libraries" class="xliff"></a>

如需有關「可攜式類別庫」的資訊，請參閱 NuGet 文件中＜目標架構＞主題的[可攜式類別庫](https://docs.microsoft.com/nuget/schema/target-frameworks#portable-class-libraries)一節。 Stephen Cleary 已建立一個列出所支援之 PCL 的工具。 如需詳細資訊，請參閱 [.NET 中的架構設定檔 (英文)](http://blog.stephencleary.com/2012/05/framework-profiles-in-net.html)。

