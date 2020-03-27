---
title: .NET 架構元件
description: 描述 .NET 架構元件，例如 .NET Standard、.NET 實作、.NET 執行階段和工具。
author: cartermp
ms.date: 08/23/2017
ms.technology: dotnet-standard
ms.openlocfilehash: 027fdb4cec47550f88f6930a4bbdff4ab5cdfb36
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344156"
---
# <a name="net-architectural-components"></a>.NET 架構元件

.NET 應用程式是針對一或多個「.NET 實作」** 所開發並在其中執行。  .NET 實作包括 .NET Framework、.NET Core 和 Mono。 所有 .NET 實作有一個通用的 API 規格，稱為 .NET Standard。 本文提供上述每個概念的簡介。

## <a name="net-standard"></a>.NET Standard

.NET 標準是由 .NET 實現的基類庫實現的一組 API。 正式地說，它是構成制式協定的 .NET API 規格，讓您據以編譯程式碼。 各個 .NET 實作中都會實作這些協定。 這會跨不同的 .NET 實作啟用可攜性，以有效地讓您的程式碼在任何地方執行。

.NET 標準也是[一個目標框架](glossary.md#target-framework)。 如果代碼面向 .NET 標準版本，則可以在支援 .NET 標準版本的任何 .NET 實現上運行。

要瞭解有關 .NET 標準以及如何定位它的更多，請參閱[.NET 標準](net-standard.md)。

## <a name="net-implementations"></a>.NET 實作

.NET 的每項實作包括下列元件：

- 一或多個執行階段。 範例：適用於 .NET Framework 的 CLR、適用於 .NET Core 的 CoreCLR 和 CoreRT。
- 實作 .NET Standard 並可能實作其他 API 的類別庫。 範例：.NET Framework 基底類別庫、.NET Core 基底類別庫。
- (選擇性) 一或多個應用程式架構。 示例[：ASP.NET、Windows](https://www.asp.net/)[表單](../framework/winforms/windows-forms-overview.md)和[Windows 演示文稿基礎 （WPF）](../framework/wpf/index.md)包含在 .NET 框架和 .NET 核心中。
- (選擇性) 開發工具。 某些開發工具可在多個實作之間共用。

Microsoft 會主動開發和維護的主要 .NET 實作有四個︰.NET Core、.NET Framework、Mono 和 UWP。

### <a name="net-core"></a>.NET Core

.NET Core 是 .NET 的跨平台實作，目的是處理大規模的伺服器與雲端工作負載。 它在 Windows、macOS 和 Linux 上運行。 它會實作 .NET Standard，讓以 .NET Standard 為目標的程式碼可以在 .NET Core 上執行。 [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core)、[Windows Forms](../framework/winforms/windows-forms-overview.md) 和 [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) 都是在 .NET Core 上執行。

若要深入了解 .NET Core，請參閱 [.NET Core 指南](../core/index.yml)及[為伺服器應用程式選擇 .NET Core 或 .NET Framework](choosing-core-framework-server.md)。

### <a name="net-framework"></a>.NET Framework

.NET 框架是自 2002 年以來存在的原始 .NET 實現。 版本 4.5 和更高版本實現 .NET 標準，因此目標 .NET 標準的代碼可以在 .NET 框架的這些版本上運行。 它包含其他 Windows 特定的 API，例如，使用 Windows Form 和 WPF 進行適用於 Windows 桌面開發的 API。 .NET Framework 最適合用來建置 Windows 傳統型應用程式。

要瞭解有關 .NET 框架的更多內容，請參閱[.NET 框架指南](../framework/index.yml)。

### <a name="mono"></a>Mono

Mono 是需要小型執行階段時主要使用的 .NET 實作。 它是為 Android、macOS、iOS、tvOS 和 watchOS 上的 Xamarin 應用程式提供支援的運行時，主要側重于佔用空間小。 Mono 也支援使用 Unity 引擎所建置的遊戲。

它支援目前發行的所有 .NET Standard 版本。

在過去，Mono 實作較大型的 .NET Framework API，並模擬 UNIX 上最熱門的其中一些功能。 它有時可用來執行依賴這些 UNIX 功能的 .NET 應用程式。

Mono 通常可搭配 Just-In-Time 編譯器使用，但也提供適用於 iOS 等平台的完整靜態編譯器 (預先編譯)。

若要深入了解 Mono，請參閱 [Mono 文件](https://www.mono-project.com/docs/)。

### <a name="universal-windows-platform-uwp"></a>通用 Windows 平台 (UWP)

UWP 是用於建置適用於物聯網 (IoT) 之現代化觸控式 Windows 應用程式和軟體的 .NET 實作。 它旨在統一您可能想要定位的不同類型的設備，包括 PC、平板電腦、手機，甚至 Xbox。 UWP 提供許多服務 (例如集中式應用程式存放區)、一個執行環境 (AppContainer)，以及用來取代 Win32 (WinRT) 的一組 Windows API。 應用可以用C++、C#、可視基本版和 JavaScript 編寫。 使用 C# 和視覺化基本時，.NET API 由 .NET Core 提供。

若要深入了解 UWP，請參閱[通用 Windows 平台簡介](/windows/uwp/get-started/universal-application-platform-guide)。

## <a name="net-runtimes"></a>.NET 執行階段

執行階段是受管理程式的執行環境。 OS 是執行階段環境的一部分，但不是 .NET 執行階段的一部分。 以下是 .NET 執行階段的一些範例：

- 適用於 .NET Framework 的 Common Language Runtime (CLR)
- 適用於 .NET Core 的 Core Common Language Runtime (CoreCLR)
- 適用於通用 Windows 平台的 .NET Native
- 適用於 Xamarin.iOS、Xamarin.Android、Xamarin.Mac 和 Mono 桌面架構的 Mono 執行階段

## <a name="net-tooling-and-common-infrastructure"></a>.NET 工具和通用基礎結構

您可以存取一組詳盡的工具和基礎結構元件，以搭配各種 .NET 實作使用。 這些工具和元件包括：

- .NET 語言及其編譯器
- .NET 專案系統 (以 *.csproj*、*.vbproj* 和 *.fsproj* 檔案為基礎)
- [MSBuild，](/visualstudio/msbuild/msbuild)用於生成專案的構建引擎
- [NuGet，](/nuget/)微軟的套裝軟體管理器.NET
- 開放原始碼建置協調流程工具，例如 [CAKE](https://cakebuild.net/) 和 [FAKE](https://fake.build/)

## <a name="applicable-standards"></a>適用標準

C# 語言和通用語言基礎設施 （CLI） 規範通過[Ecma 國際&reg;](https://www.ecma-international.org/)標準化。 Ema于2001年12月出版了這些標準的第一版。

隨後對標準的修訂由TC49-TG2（C#）和TC49-TG3（CLI）工作組在程式設計語言技術委員會[（TC49）](https://www.ecma-international.org/memento/tc49.htm)內制定，並經歐共體大會通過，隨後由ISO/IEC JTC 1通過ISO快速跟蹤進程。

### <a name="latest-standards"></a>最新標準

以下官方 Ecma 檔可用於[C#](http://www.ecma-international.org/publications/standards/Ecma-334.htm)和[CLI](http://www.ecma-international.org/publications/standards/Ecma-335.htm) （[TR-84](http://www.ecma-international.org/publications/techreports/E-TR-084.htm)）：

- **C# 語言標準（版本 5.0）：** [ECMA-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)
- **通用語言基礎結構**：提供[pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.pdf)格式和[zip](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.zip)形式。
- **從分區 IV XML 檔派生的資訊**：提供[pdf](https://www.ecma-international.org/publications/files/ECMA-TR/ECMA%20TR-084.pdf)和[zip](https://www.ecma-international.org/publications/files/ECMA-TR/TR-084.zip)格式。

ISO/IEC 官方檔可從 ISO/IEC[公開版標準頁面獲得](https://standards.iso.org/ittf/PubliclyAvailableStandards/)。 這些連結是直接從該頁面：

- **資訊技術 - 程式設計語言 - C#**： [ISO/IEC 23270：2018](https://standards.iso.org/ittf/PubliclyAvailableStandards/c075178_ISO_IEC_23270_2018.zip)
- **資訊技術 – 通用語言基礎設施 （CLI） 分區 I 到 VI**： [ISO/IEC 23271：2012](https://standards.iso.org/ittf/PubliclyAvailableStandards/c058046_ISO_IEC_23271_2012(E).zip)
- **資訊技術 • 通用語言基礎結構 （CLI） • 從分區 IV XML 檔派生的資訊技術報告**： [ISO/IEC TR 23272：2011](https://standards.iso.org/ittf/PubliclyAvailableStandards/c057955_ISO_IEC_TR_23272_2011.zip)

## <a name="see-also"></a>另請參閱

- [針對伺服器應用程式在 .NET Core 和 .NET Framework 之間進行選擇](choosing-core-framework-server.md)
- [.NET Standard](net-standard.md)
- [.NET 核心指南](../core/index.yml)
- [.NET 框架指南](../framework/index.yml)
- [C# 指南](../csharp/index.yml)
- [F# 指南](../fsharp/index.yml)
- [視覺基本指南](../visual-basic/index.yml)
