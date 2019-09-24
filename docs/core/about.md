---
title: 關於 .NET Core
description: 了解 .NET Core。
ms.date: 09/17/2019
ms.openlocfilehash: 1baad9d6611a4c4340012b9a467d3499ad9ab834
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181912"
---
# <a name="about-net-core"></a>關於 .NET Core

.NET Core 有以下特性：

- **跨平台：** 可在 Windows、macOS 及 Linux[作業系統](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)上執行。
- **在各架構間皆保持一致：** 在多個架構上 (包括 x64、x86 及 ARM) 可使用相同的行為來執行程式碼。
- **命令列工具：** 包含易用的命令列工具，可用於本機開發及持續整合案例。
- **彈性部署：** 可以包含在應用程式內或並行安裝 (針對所有使用者或所有系統進行安裝)。 可搭配 [Docker 容器](docker/index.md)使用。
- **相容：** .net Core 可透過[.NET Standard](../standard/net-standard.md)與 .NET Framework、Xamarin 和 Mono 相容。
- **開放原始碼：** .NET Core 平台是開放原始碼，使用 MIT 和 Apache 2 授權。 .NET core 是 [.NET Foundation](https://dotnetfoundation.org/) 專案。
- **受 Microsoft 支援：** .NET Core 根據 [.NET Core 支援](https://dotnet.microsoft.com/platform/support/policy)受 Microsoft 支援。

## <a name="languages"></a>語言

C#、Visual Basic 及 F# 語言可用於撰寫 .NET Core 應用程式和程式庫。 這些語言可用於您慣用的文字編輯器或整合式開發環境（IDE），包括：

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)
- Sublime 文字
- vim
 
這是由[OmniSharp](https://www.omnisharp.net/)和[Ionide](http://ionide.io)專案的參與者所提供的整合。

## <a name="apis"></a>API

.NET Core 公開許多案例的 API，以下是其中幾個：

- 基本類型，例如 [bool](../csharp/language-reference/keywords/bool.md) 與 [int](../csharp/language-reference/builtin-types/integral-numeric-types.md)。
- 集合，例如 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 及 <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>。
- 公用程式類型，例如 <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 及 <xref:System.IO.FileStream?displayProperty=nameWithType>。
- 資料類型，例如 <xref:System.Data.DataSet?displayProperty=nameWithType> 與 [DbSet](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/) \(英文\)。
- 高效能類型，例如<xref:System.Numerics.Vector?displayProperty=nameWithType>和[管線](https://devblogs.microsoft.com/dotnet/system-io-pipelines-high-performance-io-in-net/)。

藉由實作 [.NET Standard](../standard/net-standard.md) 規格，.NET Core 可提供與 NET Framework 及 Mono API 的相容性。

## <a name="frameworks"></a>架構

已在 .NET Core 上建置多項架構：

- [ASP.NET Core](/aspnet/core/)
- [Windows 10 通用 Windows 平台 (UWP)](https://developer.microsoft.com/windows)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>組合

.NET Core 由下列部分組成：

- [.Net Core 運行](https://github.com/dotnet/coreclr)時間，提供類型系統、元件載入、垃圾收集行程、原生 interop 及其他基本服務。 [.Net Core framework 程式庫](https://github.com/dotnet/corefx)提供基本資料類型、應用程式組合類型，以及基礎公用程式。
- [ASP.NET 運行](https://github.com/aspnet/home)時間可提供架構，以建立新式雲端式網際網路連線應用程式，例如 web Apps、IoT app 和 mobile 後端。
- [.NET Core CLI 工具](https://github.com/dotnet/cli)及語言編譯器 ([Roslyn](https://github.com/dotnet/roslyn) 和 [F#](https://github.com/microsoft/visualfsharp)) 可提供 .NET Core 開發人員體驗。
- [dotnet 工具](https://github.com/dotnet/core-setup)用於啟動 .NET Core 應用程式和 CLI 工具。 它會選取執行時間並裝載執行時間、提供元件載入原則，以及啟動應用程式和工具。

這些元件的散發方式如下：

- [.NET Core 執行階段](https://dotnet.microsoft.com/download) -- 包括 .NET Core 執行階段及架構程式庫。
- [ASP.NET Core 執行階段](https://dotnet.microsoft.com/download) -- 包括 ASP.NET Core 和 .NET Core 執行階段及架構程式庫。
- [.NET Core SDK](https://dotnet.microsoft.com/download) -- 包括 .NET CLI 工具、ASP.NET Core 執行階段、.NET Core 執行階段和架構。

### <a name="open-source"></a>開啟原始檔

[.NET Core](https://github.com/dotnet/core) 是開放原始碼 ([MIT 授權](https://github.com/dotnet/core/blob/master/LICENSE.TXT))，且 Microsoft 已於 2014 年貢獻給 [.NET Foundation](https://dotnetfoundation.org)。 它現在是其中一個最活躍的 .NET Foundation 專案。 其可供個人和公司使用，包括用於個人、學術或商業用途。 多家公司使用 .NET Core 做為應用程式、工具、新平臺和主機服務的一部分。 這些公司有些在 GitHub 上對 .NET Core 貢獻良多，為產品方向提供指引，成為 [.NET Foundation Technical Steering Group](https://dotnetfoundation.org/blog/tsg-welcome) 的一部分。

### <a name="designed-for-adaptability"></a>可適性設計

相較于其他 .NET 產品，.NET Core 已建立成非常類似但獨特的產品。 其設計目的是要為新平臺和工作負載提供廣泛的適應性，而且有數個可用的 OS 和 CPU 埠（也可能會移植到更多）。

該產品分成幾個部分，讓不同的部分可在不同時間適用於新的平台。 執行階段和特定平台基本程式庫必須移轉為一個單位。 無特定平台程式庫在所有平台都應該按建構照原樣運作。 有個專案的偏差可減少平臺特定的執行，以提高開發人員的效率，並C#在演算法或 API 以該方式完全或部分完成時，偏好平臺中立的程式碼。

人們常問如何實作 .NET Core 以支援多個作業系統。 他們通常會問是否有不同的實作，或是否使用[條件式編譯](https://en.wikipedia.org/wiki/Conditional_compilation)。 都有，是強式偏差趨向條件式編譯。

如以下圖表所示，[CoreFX](https://github.com/dotnet/corefx) \(英文\) 絕大部分是跨所有平台共用的非平台相關程式碼。 非平台相關程式碼可以實作為單一的可攜式組件，用在所有平台上。

![CoreFX：每個平台各有程式碼行](../images/corefx-platforms-loc.png)

Windows 與 Unix 實作大小相近。 Windows 有更大的執行，因為 CoreFX 會執行一些僅限 Windows 的功能，例如[Microsoft Win32](https://github.com/dotnet/corefx/tree/master/src/Microsoft.Win32.Registry) ，但尚未實行許多僅限 Unix 的概念。 您也會看到大部分的 Linux 和 macOS 的執行都是跨 Unix 的方式共用，而 Linux 和 macOS 特定的則是大小大致相似的。

.NET Core 中混合了平臺特定和平臺中立的程式庫。 您可以在幾個範例中看到模式︰

- [CoreCLR](https://github.com/dotnet/coreclr) 是特定平台型的。 它建置於 OS 子系統上，像是記憶體管理員和執行緒排程器。
- [System.IO](https://github.com/dotnet/corefx/tree/master/src/System.IO) 及 [System.Security.Cryptography.Algorithms](https://github.com/dotnet/corefx/tree/master/src/System.Security.Cryptography.Algorithms) 會具有平台專屬性，每個 OS 上的儲存體和加密 API 都不一樣。
- [System.Collections](https://github.com/dotnet/corefx/tree/master/src/System.Collections) 和 [System.Linq](https://github.com/dotnet/corefx/tree/master/src/System.Linq) 是非關平台型，設它們在資料結構上建立與操作。

## <a name="comparisons-to-other-net-implementations"></a>與其他 .NET 實作的比較

藉由比較 .NET Core 與現有 .NET 的實作為，可能更容易瞭解其大小和形狀。

### <a name="comparison-with-net-framework"></a>與 .NET Framework 的比較

.NET 最早由 Microsoft 於 2000 年發表，從此不斷演進。 在將近二十年間，.NET Framework 始終是 Mocrosoft 生產的主要 .NET 實作。

.NET Core 和 .NET Framework 的主要差異︰

- --. NET Core 的**應用程式模型**不支援所有 .NET Framework 的應用程式模型。 尤其不支援 ASP.NET Web Forms 和 ASP.NET MVC，但支援 ASP.NET Core MVC。 從 .NET Core 3.0 開始，.NET Core 也僅支援 Windows 上的 WPF 和 Windows Forms。
- **API** -- .NET Core 包含大型的 .NET Framework 基底類別庫，但構成方式不同 (組件名稱不同；於類型上公開的成員在重要案例中也不同)。 在某些情況下，這些差異需要將埠來源變更為 .NET Core。 如需詳細資訊，請參閱[.net 可攜性分析器](../standard/analyzers/portability-analyzer.md)。 .NET Core 會實作 [.NET Standard](../standard/net-standard.md) API 規格。
- **子系統**：.NET Core 在 .NET Framework 中實作子系統的子集，目標是更簡單的實作和程式設計模型。 例如，不支援代碼啟用安全性（CAS），而支援反射。
- **平台**：.NET Framework 支援 Windows 和 Windows Server，但 .NET Core 也支援 macOS 及 Linux。
- **開放原始碼**：.NET Core 是開放原始碼，同時[唯讀的 .NET Framework 子集](https://github.com/microsoft/referencesource)也是開放原始碼。

雖然 .NET Core 是唯一的，而且與 .NET Framework 和其他 .NET 的執行有顯著的差異，但使用來源或二進位共用技術，可以直接在這些執行之間共用程式碼。

由於 .NET Core 支援並行安裝，且其執行階段完全獨立於 .NET Framework，這使您可以在不產生任何問題的情況下，將它安裝到已經安裝 .NET Framework 的電腦上。

### <a name="comparison-with-mono"></a>與 Mono 的比較

[Mono](https://www.mono-project.com/)是 .net 的原始跨平臺。 它會以[開放原始]([open-source](https://github.com/mono/mono))碼替代方式開始使用 .NET Framework 並轉換成以行動裝置為目標，因為 IOS 和 Android 裝置變得很熱門。 它可以視為 .NET Framework 的社群複製體。 Mono 專案小組依賴 Microsoft 發佈的開放[.net 標準](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md)（尤其是 ECMA 335）來提供相容的執行。

.NET Core 和 Mono 的主要差異︰

- **應用程式模型**--Mono 支援 .NET Framework 應用程式模型（例如 Windows Forms）的子集，以及透過 Xamarin 產品進行行動裝置開發（例如， [Xamarin](https://www.xamarin.com/platform)）的一些額外元件。 .NET Core 不支援 Xamarin。
- **API**：Mono 使用相同的組件名稱及分解，支援 .NET Framework API 的[大型子集](http://docs.go-mono.com/?link=root%3a%2fclasslib)。
- **平台**：Mono支援許多平台和 CPU。
- **開放原始碼**：Mono 與 .NET Core 都使用 MIT 授權且都是 .NET Foundation 專案。
- **重心** -- Mono 近年來主要著重於行動平台，而 .NET Core 則著重在雲端和桌面工作負載。

## <a name="the-future"></a>未來

我們宣佈 .NET 5 將會是下一版的 .NET Core，並代表平臺的統一。 此專案的目的是要透過幾個主要方式來改善 .NET：

- 產生單一 .NET 執行時間和架構，可以在任何地方使用，而且具有一致的執行時間行為和開發人員體驗。
- 充分發揮 .NET Core、.NET Framework、Xamarin 和 Mono 的功能，以擴充 .NET 的功能。
- 從單一程式碼基底建立該產品，讓開發人員（Microsoft 和社區）可以同時處理和擴充，並改善所有案例。

如需 .NET 5 規劃之功能的詳細資訊，請參閱[.net 5 簡介](https://devblogs.microsoft.com/dotnet/introducing-net-5/)。
