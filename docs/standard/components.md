---
title: .NET 架構元件
description: 描述 .NET 架構元件，例如 .NET Standard、.NET 實作、.NET 執行階段和工具。
author: cartermp
ms.date: 08/23/2017
ms.technology: dotnet-standard
ms.openlocfilehash: fc34cf35e82e3a401f32561aa239996c7697aa03
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547671"
---
# <a name="net-architectural-components"></a>.NET 架構元件

.NET 應用程式是針對一或多個「.NET 實作」** 所開發並在其中執行。  .NET 實作包括 .NET Framework、.NET Core 和 Mono。 所有 .NET 實作有一個通用的 API 規格，稱為 .NET Standard。 本文提供上述每個概念的簡介。

## <a name="net-standard"></a>.NET Standard

.NET Standard 是由 .NET 實作為基類庫所執行的一組 Api。 正式地說，它是構成制式協定的 .NET API 規格，讓您據以編譯程式碼。 各個 .NET 實作中都會實作這些協定。 這會跨不同的 .NET 實作啟用可攜性，以有效地讓您的程式碼在任何地方執行。

.NET Standard 也是 [目標 framework](glossary.md#target-framework)。 如果您的程式碼以某個 .NET Standard 版本為目標，則可以在任何支援該版本 .NET Standard 的 .NET 執行上執行。

若要深入瞭解 .NET Standard 以及如何將其設為目標，請參閱 [.NET Standard](net-standard.md)。

## <a name="net-implementations"></a>.NET 實作

.NET 的每項實作包括下列元件：

- 一或多個執行階段。 範例：適用於 .NET Framework 的 CLR、適用於 .NET Core 的 CoreCLR 和 CoreRT。
- 實作 .NET Standard 並可能實作其他 API 的類別庫。 範例：.NET Framework 基底類別庫、.NET Core 基底類別庫。
- (選擇性) 一或多個應用程式架構。 範例： [ASP.NET](https://www.asp.net/)、 [Windows Forms](/dotnet/desktop/winforms/windows-forms-overview)和 [Windows Presentation Foundation (WPF) ](/dotnet/desktop/wpf/) 包含在 .NET Framework 和 .net Core 中。
- (選擇性) 開發工具。 某些開發工具可在多個實作之間共用。

Microsoft 會主動開發和維護的主要 .NET 實作有四個︰.NET Core、.NET Framework、Mono 和 UWP。

### <a name="net-core"></a>.NET Core

.NET Core 是 .NET 的跨平台實作，目的是處理大規模的伺服器與雲端工作負載。 它會在 Windows、macOS 和 Linux 上執行。 它會實作 .NET Standard，讓以 .NET Standard 為目標的程式碼可以在 .NET Core 上執行。 [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core)、[Windows Forms](/dotnet/desktop/winforms/windows-forms-overview) 和 [Windows Presentation Foundation (WPF)](/dotnet/desktop/wpf/) 都是在 .NET Core 上執行。

若要深入瞭解 .NET Core，請參閱 .net core [簡介](../core/introduction.md) ，以及 [針對伺服器應用程式在 .net core 和 .NET Framework 之間進行選擇](choosing-core-framework-server.md)。

### <a name="net-framework"></a>.NET Framework

.NET Framework 是自2002起已存在的原始 .NET 執行。 4.5 版和更新版本會執行 .NET Standard，因此以 .NET Standard 為目標的程式碼可以在這些 .NET Framework 版本上執行。 它包含其他 Windows 特定的 API，例如，使用 Windows Form 和 WPF 進行適用於 Windows 桌面開發的 API。 .NET Framework 最適合用來建置 Windows 傳統型應用程式。

若要深入瞭解 .NET Framework，請參閱 [.NET Framework 指南](../framework/index.yml)。

### <a name="mono"></a>Mono

Mono 是需要小型執行階段時主要使用的 .NET 實作。 它是在 Android、macOS、iOS、tvOS 和 watchOS 上提供 Xamarin 應用程式的執行時間，主要著重于較小的使用量。 Mono 也支援使用 Unity 引擎所建置的遊戲。

它支援目前發行的所有 .NET Standard 版本。

在過去，Mono 實作較大型的 .NET Framework API，並模擬 UNIX 上最熱門的其中一些功能。 它有時可用來執行依賴這些 UNIX 功能的 .NET 應用程式。

Mono 通常可搭配 Just-In-Time 編譯器使用，但也提供適用於 iOS 等平台的完整靜態編譯器 (預先編譯)。

若要深入了解 Mono，請參閱 [Mono 文件](https://www.mono-project.com/docs/)。

### <a name="universal-windows-platform-uwp"></a>通用 Windows 平台 (UWP)

UWP 是用於建置適用於物聯網 (IoT) 之現代化觸控式 Windows 應用程式和軟體的 .NET 實作。 它是設計來統一您可能想要鎖定的不同裝置類型，包括電腦、平板電腦、手機，甚至是 Xbox。 UWP 提供許多服務 (例如集中式應用程式存放區)、一個執行環境 (AppContainer)，以及用來取代 Win32 (WinRT) 的一組 Windows API。 您可以用 c + +、c #、Visual Basic 和 JavaScript 來撰寫應用程式。 使用 c # 和 Visual Basic 時，.net Core 會提供 .NET Api。

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
- [MSBuild](/visualstudio/msbuild/msbuild)，用來建立專案的組建引擎
- [NuGet](/nuget/)，適用于 .Net 的 Microsoft 套件管理員
- 開放原始碼建置協調流程工具，例如 [CAKE](https://cakebuild.net/) 和 [FAKE](https://fake.build/)

## <a name="applicable-standards"></a>適用標準

C # 語言和 Common Language 基礎結構 (CLI) 規格會透過[ECMA International &reg; ](https://www.ecma-international.org/)標準化。 這些標準的第一版是在2001年12月發行的 Ecma。

標準的後續修訂已由 TC49-TG2 (c # ) 和 TC49-TG3 (CLI) 在程式設計語言中的工作群組 ([TC49](https://www.ecma-international.org/memento/tc49.htm)) ，然後由 Ecma 一般元件所採用，之後透過 ISO/IEC JTC 1 透過 Iso 快速追蹤程式來採用。

### <a name="latest-standards"></a>最新標準

下列官方 Ecma 檔適用于 [c #](http://www.ecma-international.org/publications/standards/Ecma-334.htm) 和 [CLI](http://www.ecma-international.org/publications/standards/Ecma-335.htm) ([TR-84](http://www.ecma-international.org/publications/techreports/E-TR-084.htm)) ：

- **C # 語言標準 (5.0 版) **： [ECMA-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)
- **通用語言基礎結構**：適用于 [pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.pdf) 表單和 [zip](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.zip) 格式。
- **衍生自資料分割 IV XML 檔案的資訊**： [pdf](https://www.ecma-international.org/publications/files/ECMA-TR/ECMA%20TR-084.pdf) 和 [zip](https://www.ecma-international.org/publications/files/ECMA-TR/TR-084.zip) 格式提供。

ISO/IEC [公開可用的標準](https://standards.iso.org/ittf/PubliclyAvailableStandards/) 頁面提供官方的 ISO/iec 檔。 這些連結會直接來自該頁面：

- **資訊技術-程式設計語言-c #**： [ISO/IEC 23270:2018](https://standards.iso.org/ittf/PubliclyAvailableStandards/c075178_ISO_IEC_23270_2018.zip)
- **資訊技術-通用語言基礎結構 (CLI) 資料分割 I 到 VI**： [ISO/IEC 23271:2012](https://standards.iso.org/ittf/PubliclyAvailableStandards/c058046_ISO_IEC_23271_2012(E).zip)
- **資訊技術（通用語言基礎結構 (CLI) ）從資料分割 IV XML 檔案衍生的資訊技術報告**： [ISO/IEC TR 23272:2011](https://standards.iso.org/ittf/PubliclyAvailableStandards/c057955_ISO_IEC_TR_23272_2011.zip)

## <a name="see-also"></a>另請參閱

- [針對伺服器應用程式在 .NET Core 和 .NET Framework 之間進行選擇](choosing-core-framework-server.md)
- [.NET Standard 簡介](net-standard.md)
- [.NET Core 簡介](../core/introduction.md)
- [.NET Framework 指南](../framework/index.yml)
- [C# 指南](../csharp/index.yml)
- [F# 指南](../fsharp/index.yml)
- [Visual Basic 指南](../visual-basic/index.yml)
