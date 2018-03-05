---
title: ".NET 架構元件"
description: "描述 .NET 架構元件，例如 .NET Standard、.NET 實作、.NET 執行階段和工具。"
author: cartermp
ms.author: mairaw
ms.date: 08/23/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8a17d4c36d9c1942166b9ad889103a7942f1813d
ms.sourcegitcommit: 96cc82cac4650adfb65ba351506d8a8fbcd17b5c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2018
---
# <a name="net-architectural-components"></a>.NET 架構元件

.NET 應用程式是針對一或多個「.NET 實作」所開發並在其中執行。  .NET 實作包括 .NET Framework、.NET Core 和 Mono。 所有 .NET 實作有一個通用的 API 規格，稱為 .NET Standard。 本文提供上述每個概念的簡介。

## <a name="net-standard"></a>.NET Standard

.NET Standard 是由 .NET 實作的基底類別庫所實作的一組 API。 更正式的說法是，它是一個 .NET API 的規格，其構成了一組您據以編譯程式碼的制式協定。 每個 .NET 實作中都會實作這些協定。 這會跨不同的 .NET 實作啟用可攜性，以有效地讓您的程式碼在任何地方執行。

.NET Standard 也是[目標 Framework](glossary.md#target-framework)。 如果您的程式碼以某個 .NET Standard 版本為目標，就可以在支援該版 .NET Standard 的任何 .NET 實作上執行。

若要了解 .NET Standard 及如何將其設為目標，請參閱 [.NET Standard](net-standard.md) 主題。

## <a name="net-implementations"></a>.NET 實作

.NET 的每項實作包括下列元件：

- 一或多個執行階段。 範例：適用於 .NET Framework 的 CLR、適用於 .NET Core 的 CoreCLR 和 CoreRT。
- 實作 .NET Standard 並可能實作其他 API 的類別庫。 範例：.NET Framework 基底類別庫、.NET Core 基底類別庫。
- (選擇性) 一或多個應用程式架構。 範例：[ASP.NET](https://www.asp.net/)、[Windows Forms](../framework/winforms/windows-forms-overview.md) 和 [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) 會包含在 .NET Framework 中。
- (選擇性) 開發工具。 某些開發工具可在多個實作之間共用。

Microsoft 會主動開發和維護的主要 .NET 實作有四個︰.NET Core、.NET Framework、Mono 和 UWP。

### <a name="net-core"></a>.NET 核心

.NET Core 是 .NET 的跨平台實作，目的是處理大規模的伺服器與雲端工作負載。 可在 Windows、macOS 及 Linux 執行。 它會實作 .NET Standard，讓以 .NET Standard 為目標的程式碼可以在 .NET Core 上執行。 ASP.NET Core 會在 .NET Core 上執行。 

若要深入了解 .NET Core，請參閱 [.NET Core 指南](../core/index.md)及[為伺服器應用程式選擇 .NET Core 或 .NET Framework](choosing-core-framework-server.md)。

### <a name="net-framework"></a>.NET Framework

.NET Framework 是自 2002年以來已存在的原始 .NET 實作。 它就是現有 .NET 開發人員一律會使用的同一個 .NET Framework。 4.5 和更新版本會實作 .NET Standard，讓以 .NET Standard 為目標的程式碼可以在這些 .NET Framework 版本上執行。 它包含其他 Windows 特定的 API，例如，使用 Windows Form 和 WPF 進行適用於 Windows 桌面開發的 API。 .NET Framework 最適合用來建置 Windows 傳統型應用程式。

若要深入了解 .NET Framework，請參閱 [.NET Framework 指南](../framework/index.md)。

### <a name="mono"></a>Mono

Mono 是需要小型執行階段時主要使用的 .NET 實作。 它是支援 Android、Mac、iOS、tvOS 和 watchOS 版 Xamarin 應用程式的執行階段，主要著重於較小的使用量。 Mono 也支援使用 Unity 引擎所建置的遊戲。

它支援目前發行的所有 .NET Standard 版本。

在過去，Mono 實作較大型的 .NET Framework API，並模擬 UNIX 上最熱門的其中一些功能。 它有時可用來執行依賴這些 UNIX 功能的 .NET 應用程式。

Mono 通常可搭配 Just-In-Time 編譯器使用，但也提供適用於 iOS 等平台的完整靜態編譯器 (預先編譯)。

若要深入了解 Mono，請參閱 [Mono 文件](http://www.mono-project.com/docs/)。

### <a name="universal-windows-platform-uwp"></a>通用 Windows 平台 (UWP)

UWP 是用於建置適用於物聯網 (IoT) 之現代化觸控式 Windows 應用程式和軟體的 .NET 實作。 其設計目的是為了整合您可能想要設為目標的不同裝置類型，包括電腦、平板電腦、平板手機、手機，甚至是 Xbox。 UWP 提供許多服務 (例如集中式應用程式存放區)、一個執行環境 (AppContainer)，以及用來取代 Win32 (WinRT) 的一組 Windows API。 您可以使用 C++、C#、VB.NET 和 JavaScript 來撰寫應用程式。 使用 C# 和 VB.NET 時，.NET API 是由 .NET Core 所提供。

若要深入了解 UWP，請參閱[通用 Windows 平台簡介](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide)。

## <a name="net-runtimes"></a>.NET 執行階段

執行階段是受管理程式的執行環境。 OS 是執行階段環境的一部分，但不是 .NET 執行階段的一部分。 以下是 .NET 執行階段的一些範例：
 
 - 適用於 .NET Framework 的 Common Language Runtime (CLR)
 - 適用於 .NET Core 的 Core Common Language Runtime (CoreCLR)
 - 適用於通用 Windows 平台的 .NET Native 
 - 適用於 Xamarin.iOS、Xamarin.Android、Xamarin.Mac 和 Mono 桌面架構的 Mono 執行階段

## <a name="net-tooling-and-common-infrastructure"></a>.NET 工具和通用基礎結構

您可以存取一組詳盡的工具和基礎結構元件，以搭配各種 .NET 實作使用。 這些包括 (但不限於) 下列項目：

- .NET 語言及其編譯器
- .NET 專案系統 (以 *.csproj*、*.vbproj* 和 *.fsproj* 檔案為基礎)
- [MSBuild](/visualstudio/msbuild/msbuild)，用來建置專案的建置引擎
- [NuGet](/nuget/)，適用於 .NET 的 Microsoft 套件管理員
- 開放原始碼建置協調流程工具，例如 [CAKE](http://cakebuild.net/) 和 [FAKE](https://fake.build/)

## <a name="see-also"></a>另請參閱
[為伺服器應用程式選擇 .NET Core 或 .NET Framework](choosing-core-framework-server.md)   
[.NET Standard](net-standard.md)  
[.NET Core 指南](../core/index.md)  
[.NET Framework 指南](../framework/index.md)  
[C# 指南](../csharp/index.md)  
[F# 指南](../fsharp/index.md)  
[VB.NET 指南](../visual-basic/index.md)  

