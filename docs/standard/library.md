---
title: ".NET 標準程式庫"
description: ".NET 標準程式庫"
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: c044882c-af15-45f2-96d1-534557a5ee9b
translationtype: Human Translation
ms.sourcegitcommit: f9ffbb2e300df2080276096095a7269736260ba1
ms.openlocfilehash: d56ddc264d861081f0b808711cccd489a374c0b8

---

# <a name="net-standard-library"></a>.NET 標準程式庫

.NET 標準程式庫是計劃提供所有 .NET 執行階段使用的 .NET API 正式規格。 標準程式庫背後的動機是在 .NET 生態系統中建立更高的一致性。 [ECMA 335](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) 會繼續建立 .NET 執行階段行為的一致性，但沒有 .NET 程式庫實作之 .NET 基底類別庫 (BCL) 的類似規格。 

.NET 標準程式庫支援下列重要案例： 

- 定義一致的 BCL API 集合，以供所有 .NET 平台實作，而不論工作負載為何。
- 可讓開發人員使用這組相同的 API，產生可跨 .NET 執行階段使用的可攜式程式庫。
- 減少因 .NET API 而必須對共用原始程式碼進行的條件式編譯，並在順利的情況下完全排除，僅適用於 OS API。

不同的 .NET 執行階段會實作特定版本的 .NET 標準程式庫。 每個 .NET 執行階段版本會宣佈它所支援的最高 .NET Standard 版本，此聲明表示它也會支援舊版。 例如，.NET Framework 4.6 會實作 .NET Standard Library 1.3，這表示它會公開 .NET Standard Library 1.0 到 1.3 版中定義的所有 API。 同樣地，.NET Framework 4.6.2 會實作 .NET Standard Library 1.5，而 .NET Core 1.0 會實作 .NET Standard Library 1.6。

## <a name="net-platforms-support"></a>.NET 平台支援

您會看到支援 .NET 標準程式庫的一組完整 .NET 執行階段。

| 平台名稱 | Alias |  |  |  |  |  | | | |
| :---------- | :--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |:--------- |
|.NET Standard | netstandard | 1.0 | 1.1 | 1.2 | 1.3 | 1.4 | 1.5 | 1.6 | 2.0 |
|.NET 核心|netcoreapp|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|1.0|vNext|
|.NET Framework|net|&rarr;|4.5|4.5.1|4.6|4.6.1|4.6.2|vNext|4.6.1|
|Mono/Xamarin 平台||&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|&rarr;|vNext|
|通用 Windows 平台|uap|&rarr;|&rarr;|&rarr;|&rarr;|10.0|&rarr;|&rarr;|vNext|
|Windows|win|&rarr;|8.0|8.1||||||
|Windows Phone|wpa|&rarr;|&rarr;|8.1||||||
|Windows Phone Silverlight|wp|8.0||||||||

## <a name="comparison-to-portable-class-libraries"></a>與可攜式類別庫的比較

.NET 標準程式庫可視為新一代的[可攜式類別庫 (PCL)](https://msdn.microsoft.com/library/gg597391.aspx)。 .NET 標準程式庫藉由組織標準 BCL 並在 .NET 執行階段之間建立更高的一致性結果，來改進建立可攜式程式庫的體驗。 以 .NET 標準程式庫為目標的程式庫是 PCL 或「.NET Standard 型 PCL」。 現有的 PCL 是「設定檔型 PCL」。

.NET 標準程式庫和 PCL 設定檔是為了類似的目的而建立，但也有幾點重要的不同之處。

相似之處：

- 定義可用於二進位字碼共用的 API。

不同之處：

- .NET 標準程式庫是一組經過組織的 API，而 PCL 設定檔則是由現有平台的交集所定義。
- .NET 標準程式庫是以線性方式控制版本，而 PCL 設定檔則不是。
- PCL 設定檔代表 Microsoft 平台，而 .NET 標準程式庫則無從驗證平台。

## <a name="specification"></a>規格

.NET 標準程式庫規格是一組標準化的 API。 此規格是由 .NET 執行階段實作項所維護，特別是 Microsoft (包括.NET Framework、.NET Core 和 Mono) 和 Unity。 建立新的 .NET 標準程式庫版本時會使用公開回饋程序。

### <a name="official-artifacts"></a>正式成品

正式規格是一組定義 API 的 .cs 檔案，這些 API 是標準的一部分。 每個[元件](https://github.com/dotnet/corefx/tree/master/src)的 [ref 目錄](https://github.com/dotnet/corefx/tree/master/src/System.Runtime/ref)會定義 .NET 標準程式庫 API。 雖然參考成品位於 [CoreFX 儲存機制](https://github.com/dotnet/corefx)，但不是 .NET Core 的特定成品。

[NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library) 中繼套件 ([原始程式碼](https://github.com/dotnet/corefx/blob/master/pkg/NETStandard.Library/NETStandard.Library.packages.targets)) 描述定義 (部分) 一個或多個 .NET 標準程式庫版本的程式庫集合。

System.Runtime 等指定元件描述：

- .NET 標準程式庫的組件 (僅限其範圍)。
- 適用於該範圍的多個 .NET 標準程式庫版本。

為了更方便閱讀及支援特定開發人員案例 (例如使用編譯器)，已提供衍生成品。

- Markdown 中的 API 清單 (TBD)
- 以 [NuGet 套件](../core/packages.md)散發並由 [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library/) 中繼套件參考的參考組件。

### <a name="package-representation"></a>封裝表示

.NET 標準程式庫參考組件的主要散發工具是 [NuGet 套件](../core/packages.md)。 您可以根據每個 .NET 執行階段，以各種適當的方式來提供實作。

NuGet 套件是以一個或多個[架構](frameworks.md)為目標。 .NET 標準程式庫套件是以 ".NET Standard" 架構為目標。 您可以使用 `netstandard` [Compact TFM](frameworks.md) (例如 `netstandard1.4`) 將 .NET 標準程式庫設為目標。 要在多個執行階段上執行的程式庫應以此架構為目標。 

`NETStandard.Library` 中繼套件會參考定義 .NET 標準程式庫的一組完整 NuGet 套件。  若要將 `netstandard` 設為目標，最常見方式是參考這個中繼套件。 其中描述大約 40 種 .NET 程式庫和相關聯的 API (以定義 .NET 標準程式庫)，並提供存取權。 您可以參考目標為 `netstandard` 的其他套件，以存取其他 API。 

### <a name="versioning"></a>版本控制

此規格不只一個，而是一組以累加方式擴充並以線性方式控制版本的 API。 此標準的第一個版本會建立一組基準 API。 後續版本會新增 API，並繼承舊版所定義的 API。 沒有任何既定的佈建可從標準中移除 API。

.NET 標準程式庫並不屬於任何一個 .NET 執行階段，也不符合任何執行階段的版本配置。

加入任何執行階段 (例如 .NET Framework、.NET Core 和 Mono) 的 API 都可視為要加入規格的候選項目，尤其是如果本質上要作為基礎的 API。 新的 [.NET 標準程式庫版本](https://github.com/dotnet/corefx/blob/master/Documentation/architecture/net-platform-standard.md#list-of-net-corefx-apis-and-their-associated-net-platform-standard-version)是根據 .NET 執行階段版本所建立，可讓您以 .NET Standard PCL 中的新 API 為目標。 如需版本控制機制的詳細資訊，請參閱 [.NET Core 版本控制](../core/versions/index.md)。

.NET 標準程式庫版本控制對於使用至關重要。 指定 .NET 標準程式庫版本之後，您可以使用以相同版本或更低版本為目標的程式庫。 下列方法描述使用 .NET 標準程式庫 PCL (專屬於 .NET 標準程式庫目標) 的工作流程。

- 選取要用於 PCL 的 .NET 標準程式庫版本。
- 使用相依於相同 .NET 標準程式庫版本或更低版本的程式庫。
- 如果您發現有個程式庫相依於更高版本的 .NET 標準程式庫，您需要採用該相同的版本，或決定不要使用該程式庫。

### <a name="pcl-compatibility"></a>PCL 相容性

.NET 標準程式庫與 PCL 設定檔子集相容。 .NET Standard Library 1.0、1.1 和 1.2 會各自與一組 PCL 設定檔相重疊。 建立此重疊的原因有兩個：

- 可讓 .NET Standard 型 PCL 參考設定檔型 PCL。
- 可將設定檔型 PCL 封裝成 .NET Standard 型 PCL。

[Microsoft.NETCore.Portable.Compatibility](https://www.nuget.org/packages/Microsoft.NETCore.Portable.Compatibility) NuGet 套件提供設定檔型 PCL 相容性。 參考包含設定檔型 PCL 的 NuGet 套件時需要此相依性。

封裝成 `netstandard` 的設定檔型 PCL，會比一般封裝在 project.json 中的設定檔型 PCL 更容易使用。 現有的使用者可以使用 `netstandard` 封裝。

您會看到與 .NET Standard 相容的 PCL 設定檔集合： 

| 設定檔 | .NET 平台標準版本 |
| ---------| --------------- |
| Profile7 .NET 可攜式子集 (.NET Framework 4.5、Windows 8) | 1.1 |
| Profile31 .NET 可攜式子集 (Windows 8.1、Windows Phone Silverlight 8.1)| 1.0 |
| Profile32 .NET 可攜式子集 (Windows 8.1、Windows Phone 8.1) | 1.2 |
| Profile44 .NET 可攜式子集 (.NET Framework 4.5.1、Windows 8.1) | 1.2 |
| Profile49 .NET 可攜式子集 (.NET Framework 4.5、Windows Phone Silverlight 8) | 1.0 |
| Profile78 .NET 可攜式子集 (.NET Framework 4.5、Windows 8、Windows Phone Silverlight 8) | 1.0 |
| Profile84 .NET 可攜式子集 (Windows Phone 8.1、Windows Phone Silverlight 8.1) | 1.0 |
| Profile111 .NET 可攜式子集 (.NET Framework 4.5、Windows 8、Windows Phone 8.1) | 1.1 |
| Profile151 .NET 可攜式子集 (.NET Framework 4.5.1、Windows 8.1、Windows Phone 8.1) | 1.2 |
| Profile157 .NET 可攜式子集 (Windows 8.1、Windows Phone 8.1、Windows Phone Silverlight 8.1) | 1.0 |
| Profile259 .NET 可攜式子集 (.NET Framework 4.5、Windows 8、Windows Phone 8.1、Windows Phone Silverlight 8) | 1.0 |

## <a name="targeting-net-standard-library"></a>以 .NET 標準程式庫為目標

您可以搭配使用 `netstandard` 架構和 NETStandard.Library 中繼套件，來[建置 .NET 標準程式庫](../core/tutorials/libraries.md)。 您可以看到[使用 .NET Core 工具將 .NET 標準程式庫設為目標](../core/packages.md)的範例 。



<!--HONumber=Nov16_HO3-->


