---
title: ".NET Core 指南"
description: ".NET Core 是 .NET 的模組化、高效能實作，可用於建立 Windows、Linux 和 Mac 應用程式。 了解 .NET Core 以開始使用。"
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: f2b312cb-f80c-4b0d-9101-93908f06a6fa
ms.translationtype: HT
ms.sourcegitcommit: 9f2128080d34e78733cec926e59ee5dbe9b98a0d
ms.openlocfilehash: 14e72dad71b8d99cea947e14f2ac77aedcfb5672
ms.contentlocale: zh-tw
ms.lasthandoff: 08/07/2017

---

# <a name="net-core-guide"></a>.NET Core 指南

> 簽出[「入門」教學課程](get-started.md)以了解如何建立簡單的 .NET Core 應用程式。 只需要幾分鐘，您就可以啟動並執行您的第一個應用程式。

.NET Core 是一般用途的開發平台，由 Microsoft 和 [GitHub](https://github.com/dotnet/core) 上的 .NET 社群共同維護。 它可以跨平台支援 Windows、macOS 及 Linux，並可用於裝置、雲端和內嵌/IoT 案例。 

下列特性最能定義 .NET Core：

- **彈性的部署︰**可以包含在應用程式內，或任何人、任何機器都可並行安裝。
- **跨平台︰**Windows、macOS 及 Linux 上都可執行，也可以移轉到其他作業系統。 Microsoft、其他公司及個人提供的[支援的作業系統 (OS)](https://github.com/dotnet/core/blob/master/roadmap.md)、Cpu 和應用程式案例，會隨著時間成長。
- **命令列工具︰**所有產品案例都可以在命令列操作。 
- **相容︰**.NET Core 透過 [.NET Standard Library](../standard/library.md) (.NET 標準程式庫) 與 .NET Framework、Xamarin 及 Mono 相容。
- **開放原始碼︰**.NET Core 平台是開放原始碼，使用 MIT 和 Apache 2 授權。 請在 [CC-BY](https://creativecommons.org/licenses/by/4.0/) 下取得文件授權。 .NET core 是 [.NET Foundation](https://dotnetfoundation.org/) 專案。
- **受 Microsoft 支援︰**.NET Core 依照 [.NET Core 支援](https://www.microsoft.com/net/core/support/) 受 Microsoft 支援。

## <a name="composition"></a>組合

.NET Core 由下列部分組成：

- 一個 [.NET 執行階段](https://github.com/dotnet/coreclr)，提供類型系統、組件載入、記憶體回收行程、原生 Interop 及其他基本服務。 
- 一組 [Framework 程式庫](https://github.com/dotnet/corefx)，提供基本資料類型、應用程式組合類型及基本的公用程式。 
- [SDK 工具組](https://github.com/dotnet/cli)及[語言編譯器](https://github.com/dotnet/roslyn)，提供基本的開發人員體驗，可在 [.NET Core SDK](sdk.md) 中取得。
- 'Dotnet' 應用程式主機，用來啟動 .NET Core 應用程式。 它會選取執行階段及裝載執行階段、提供組件載入原則，然後啟動應用程式。 您也可以差不多的方式用相同的主機啟動 SDK 工具。

### <a name="languages"></a>語言

C# 和 F# 語言 (Visual Basic 即將加入) 可用來撰寫 .NET Core 應用程式和程式庫。 在 .NET Core 上執行的編譯器，讓您在可以執行 .NET Core 的任何地方進行開發。 一般情況下，您不會直接使用編譯器，而是使用 SDK 工具間接使用它。

C# 和 F# 編譯器和 .NET Core 工具已或可以整合至數個文字編輯器和 IDE 中，包括 Visual Studio、[Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)、Sublime Text 和 Vim，讓 .NET Core 開發成為您最愛的編碼環境和作業系統的選項。 這項整合有部分是由 [OmniSharp 專案](http://www.omnisharp.net/)的熱心人士提供。

### <a name="net-apis-and-compatibility"></a>.NET API 和相容性

.NET Core 可以視為 .NET Framework 基底類別庫 (BCL) 層的 .NET Framework 跨平台版本。 它會實作 [.NET 標準程式庫](../standard/library.md) 規格。 .NET Core 提供可在 .NET Framework 或 Mono/Xamarin 中取得的 API 子集。 在某些情況下不會實作全部類型 (某些成員不提供或已搬遷)。

若要深入了解 .NET Core API 藍圖，請參閱 [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md)。

### <a name="relationship-to-net-standard"></a>.NET Standard 的關聯性

[.NET Standard](../standard/net-standard.md) 是一種 API 規格，描述開發人員在每個 .NET 實作中預期出現的一組一致的 .NET API。 .NET 實作必須實作此規格，才會被視為符合 .NET Standard 規範，可以支援以 .NET Standard 為目標的程式庫。 

.NET Core 實作 .NET Standard，因此支援 .NET Standard 程式庫。

### <a name="workloads"></a>工作負載

.NET Core 本身就包含單一的應用程式模型：主控台應用程式，對工具、本機服務和文字型遊戲都極有幫助。 其他應用程式模型早已建置在 .NET Core 以擴充其功能，例如︰

- [ASP.NET Core](/aspnet/core/)
- [Windows 10 通用 Windows 平台 (UWP)](https://developer.microsoft.com/windows)
- [Xamarin.Forms](https://www.xamarin.com/forms)

### <a name="open-source"></a>開啟原始檔

[.NET Core](https://github.com/dotnet/core) 是開放原始碼 (MIT 授權)，Microsoft 已於 2014 年提供給 [.NET Foundation](https://dotnetfoundation.org)。 它現在是最常使用的 .NET Foundation 專案之一。 可供個人和公司行號自由運用於個人、學術或商業用途。 很多公司將 .NET Core 用為應用程式、工具、新平台及裝載服務的一部分。 這些公司有些在 GitHub 上對 .NET Core 貢獻良多，為產品方向提供指引，成為 [.NET Foundation Technical Steering Group](https://dotnetfoundation.org/blog/tsg-welcome) 的一部分。

## <a name="acquisition"></a>擷取

.NET Core 有兩大散發方式，一種是 NuGet.org 的封裝，一種是獨立散發。

### <a name="distributions"></a>分佈

您可以在 [.NET Core 快速入門](https://www.microsoft.com/net/core)頁面下載 .NET Core。

- *Microsoft .NET Core* 散發包含 CoreCLR 執行階段、相關程式庫、主控台應用程式主機和 `dotnet` 應用程式啟動程式。 它是由 [`Microsoft.NETCore.App`](https://www.nuget.org/packages/Microsoft.NETCore.App) 中繼套件所描述。
- *Microsoft .NET Core SDK* 散發包含 .NET Core 和一組還原 NuGet 封裝及編譯與建置應用程式的工具。 

通常您會先安裝 .NET Core SDK 開始使用 .NET Core 開發。 您可以選擇安裝其他的 .NET Core (或許是發行前版本) 組建。

### <a name="packages"></a>封裝

- [.NET Core 封裝](packages.md)包含 .NET Core 執行階段和程式庫 (參考組件和實作)。 例如，[System.Net.Http](https://www.nuget.org/packages/System.Net.Http/)。
- [.NET Core 中繼套件](packages.md)藉由參考適當的建立版本的程式庫封裝集合，描述各種層級和應用程式模型。

## <a name="architecture"></a>架構

.NET Core 是跨平台的 .NET 實作。 .NET Core 唯一的主要架構考量，是關於為支援的平台提供特定平台的實作。

### <a name="environments"></a>環境

Microsoft 在 Windows、macOS 及 Linux 上都支援 .NET Core。 在 Linux 上，Microsoft 主要支援 .NET Core 在running on Red Hat Enterprise Linux (RHEL) 及 Debian 散發系列上執行。

.NET Core 目前支援 X64 CPU。 Windows 上也支援 X86。 ARM64 和 ARM32 正在進行中。

[.NET Core Roadmap](https://github.com/dotnet/core/blob/master/roadmap.md) 提供更詳盡的工作負載及作業系統和 CPU 環境支援與方案資訊。

其他公司或群組可能支援其他應用程式類型和環境的 .NET Core。

### <a name="designed-for-adaptability"></a>可適性設計

.NET Core 近似其他 .NET 產品，但保有獨特性。 它的設計使它具有最大的可適性，能夠適應新的平台、新的工作負載和新的編譯器工具鏈。 目前正在建構數個作業系統和 CPU 連接埠，可能會移轉更多。 [LLILC](https://github.com/dotnet/llilc) 專案即為一例，這是透過 [LLVM](http://llvm.org/) 編譯器的 .NET Core 原生編譯早期原型。

產品分成幾個部分，讓不同的部分適用於新平台的不同排程。 執行階段和特定平台基本程式庫必須移轉為一個單位。 無特定平台程式庫在所有平台都應該按建構照原樣運作。 減少特定平台實作的專案偏差會提高開發人員的效率，只要能全部或部分以該方式實作演算法或 API，就偏好非平台相關的 C# 程式碼。

人們常問如何實作 .NET Core 以支援多個作業系統。 他們通常會問是否有不同的實作，或是否使用[條件式編譯](https://en.wikipedia.org/wiki/Conditional_compilation)。 都有，是強式偏差趨向條件式編譯。

如以下圖表所示，[CoreFX](https://github.com/dotnet/corefx) 絕大部分是跨所有平台共用的非平台相關程式碼。 非平台相關程式碼可以實作為單一的可攜式組件，用在所有平台上。

![CoreFX︰每個平台各有程式碼行](../images/corefx-platforms-loc.png)

Windows 與 Unix 實作大小相近。 Windows 實作較大，因為 CoreFX 會實作一些 Windows 專用功能，例如 [Microsoft.Win32.Registry](https://github.com/dotnet/corefx/tree/master/src/Microsoft.Win32.Registry)，但尚未實作任何 Unix 專有的概念。 您也會看到大多數的 Linux 和 macOS 實作會跨 Unix 實作共用，因此 Linux 和 macOS 特定實作的大小差相彷彿。


.NET Core 混用特定平台和非平台相關程式庫。 您可以在幾個範例中看到模式︰

- [CoreCLR](https://github.com/dotnet/coreclr) 是特定平台型的。 它以 C/C++ 建置，所以依建構而言是特定平台。
- [System.IO](https://github.com/dotnet/corefx/tree/master/src/System.IO) 和 [System.Security.Cryptography.Algorithms](https://github.com/dotnet/corefx/tree/master/src/System.Security.Cryptography.Algorithms) 是特定平台型，設儲存體和密碼編譯 API 在每個作業系統上有巨大差異。 
- [System.Collections](https://github.com/dotnet/corefx/tree/master/src/System.Collections) 和 [System.Linq](https://github.com/dotnet/corefx/tree/master/src/System.Linq) 是非關平台型，設它們在資料結構上建立與操作。

## <a name="comparisons-to-other-net-implementations"></a>與其他 .NET 實作的比較

比較 .NET Core 和現有的 .NET 實作，可能最容易了解 .NET Core 的大小和形態。 

### <a name="comparison-with-net-framework"></a>與 .NET Framework 的比較

.NET 最早由 Microsoft 於 2000 年發表，從此不斷演進。 .NET Framework 在超過 15 年來始終是 Microsoft 生產的主要 .NET 實作。 

.NET Core 和 .NET Framework 的主要差異︰ 

- **應用程式模型**：.NET Core 不支援所有的 .NET Framework 應用程式模型，部分是因為其中大部分是建置在 Windows 技術上，例如 WPF (以 DirectX 為建置基礎)。 .NET Core 和 .NET Framework 都支援主控台和 ASP.NET Core 應用程式模型。 
- **API**：.NET Core 包含許多和 .NET Framework 相同但較少的 API，且有不同的分解 (組件名稱不同，重要案例的類型圖案不同)。 這些差異目前通常需要變更 .NET Core 的移轉來源。 .NET Core 實作 [.NET 標準程式庫](../standard/library.md) API，隨著時間會成長到能包含更多的 .NET Framework BCL API。
- **子系統**：.NET Core 在 .NET Framework 中實作子系統的子集，目標是更簡單的實作和程式設計模型。 例如，不支援程式碼存取安全性 (CAS)，但支援反映。
- **平台**：.NET Framework 支援 Windows 和 Windows Server，但 .NET Core 也支援 macOS 及 Linux。
- **開放原始碼**：.NET Core 是開放原始碼，同時[唯讀的 .NET Framework 子集](https://github.com/microsoft/referencesource)也是開放原始碼。

雖然 .NET Core 很獨特，與 .NET Framework 及其他 .NET 實作有顯著差異，卻可以使用原始碼或二進位共用技術，直接共用程式碼。 

### <a name="comparison-with-mono"></a>與 Mono 的比較

[Mono](http://www.mono-project.com/) 是原始的跨平台和[開放原始碼](https://github.com/mono/mono) .NET 實作，首次發送為 2004 年。 它可以視為 .NET Framework 的社群複製體。 Mono 專案小組依賴 Microsoft 為提供相容實作而發行的開放 [.NET 標準](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) (特別是 ECMA 335)。

.NET Core 和 Mono 的主要差異︰

- **應用程式模型**：單聲道透過 Xamarin 產品支援 .NET Framework 應用程式模型的子集 (例如，Windows Forms) 和一些其他子集 (例如，[Xamarin.iOS](https://www.xamarin.com/platform))。 .NET Core 不支援這些。
- **API**：Mono 使用相同的組件名稱及分解，支援 .NET Framework API 的[大型子集](http://docs.go-mono.com/?link=root%3a%2fclasslib)。
- **平台**：Mono支援許多平台和 CPU。
- **開放原始碼**：Mono 與 .NET Core 都使用 MIT 授權且都是 .NET Foundation 專案。
- **焦點**：Mono 近年來的主要焦點是行動平台，而 .NET Core 則著重於雲端工作負載。

