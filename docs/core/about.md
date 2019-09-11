---
title: 關於 .NET Core
description: 了解 .NET Core。
author: richlander
ms.date: 08/01/2018
ms.openlocfilehash: ea9253bacf2bcee63430cd45f2a9ed412ce629e7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849136"
---
# <a name="about-net-core"></a>關於 .NET Core

.NET Core 有以下特性：

- **跨平台：** 可在 Windows、macOS 及 Linux [作業系統](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)上執行。
- **在各架構間皆保持一致：** 在多個架構上 (包括 x64、x86 及 ARM) 可使用相同的行為來執行程式碼。
- **命令列工具：** 包含易用的命令列工具，可用於本機開發及持續整合案例。
- **彈性部署：** 可以包含在應用程式內或並行安裝 (針對所有使用者或所有系統進行安裝)。 可搭配 [Docker 容器](docker/index.md)使用。
- **相容：** .NET Core 可透過 [.NET Standard](../standard/net-standard.md) 與 .NET Framework、Xamarin 及 Mono 相容。
- **開放原始碼：** .NET Core 平台是開放原始碼，使用 MIT 和 Apache 2 授權。 .NET core 是 [.NET Foundation](https://dotnetfoundation.org/) 專案。
- **受 Microsoft 支援：** .NET Core 根據 [.NET Core 支援](https://dotnet.microsoft.com/platform/support/policy)受 Microsoft 支援。

## <a name="languages"></a>語言

C#、Visual Basic 及 F# 語言可用於撰寫 .NET Core 應用程式和程式庫。 這些語言已經或者能夠整合至您最慣用的文字編輯器與 IDE，包括 [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)、[Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)、Sublime Text 和 Vim。 這項整合有部分由 [OmniSharp](https://www.omnisharp.net/) 及 [Ionide](http://ionide.io) 專案的優秀人士提供。

## <a name="apis"></a>API

.NET Core 公開許多案例的 API，以下是其中幾個：

- 基本類型，例如 [bool](../csharp/language-reference/keywords/bool.md) 與 [int](../csharp/language-reference/builtin-types/integral-numeric-types.md)。
- 集合，例如 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 及 <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>。
- 公用程式類型，例如 <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 及 <xref:System.IO.FileStream?displayProperty=nameWithType>。
- 資料類型，例如 <xref:System.Data.DataSet?displayProperty=nameWithType> 與 [DbSet](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/) \(英文\)。
- 高效能類型，例如 <xref:System.Numerics.Vector?displayProperty=nameWithType> 與 [Pipelines](https://devblogs.microsoft.com/dotnet/system-io-pipelines-high-performance-io-in-net/)\(英文\)。

藉由實作 [.NET Standard](../standard/net-standard.md) 規格，.NET Core 可提供與 NET Framework 及 Mono API 的相容性。

## <a name="frameworks"></a>架構

已在 .NET Core 上建置多項架構：

- [ASP.NET Core](/aspnet/core/)
- [Windows 10 通用 Windows 平台 (UWP)](https://developer.microsoft.com/windows)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>組合

.NET Core 由下列部分組成：

- [.NET Core 執行階段](https://github.com/dotnet/coreclr)提供類型系統、組件負載、記憶體回收行程、原始 interop 及其他基本服務。 [.NET Core 架構程式庫](https://github.com/dotnet/corefx)提供基本資料類型、應用程式組合類型及基本公用程式。
- [ASP.NET 執行階段](https://github.com/aspnet/home)提供架構，用以建置與網際網路連線的新式雲端應用程式，如 Web 應用程式、IoT 應用程式及行動後端。
- [.NET Core CLI 工具](https://github.com/dotnet/cli)及語言編譯器 ([Roslyn](https://github.com/dotnet/roslyn) 和 [F#](https://github.com/microsoft/visualfsharp)) 可提供 .NET Core 開發人員體驗。
- [dotnet 工具](https://github.com/dotnet/core-setup)用於啟動 .NET Core 應用程式和 CLI 工具。 它會選取並裝載執行階段，提供組件負載原則，並啟動應用程式和工具。

這些元件的散發方式如下：

- [.NET Core 執行階段](https://dotnet.microsoft.com/download) -- 包括 .NET Core 執行階段及架構程式庫。
- [ASP.NET Core 執行階段](https://dotnet.microsoft.com/download) -- 包括 ASP.NET Core 和 .NET Core 執行階段及架構程式庫。
- [.NET Core SDK](https://dotnet.microsoft.com/download) -- 包括 .NET CLI 工具、ASP.NET Core 執行階段、.NET Core 執行階段和架構。

### <a name="open-source"></a>開啟原始檔

[.NET Core](https://github.com/dotnet/core) 是開放原始碼 ([MIT 授權](https://github.com/dotnet/core/blob/master/LICENSE.TXT))，且 Microsoft 已於 2014 年貢獻給 [.NET Foundation](https://dotnetfoundation.org)。 它現在是最常使用的 .NET Foundation 專案之一。 可供個人和公司行號自由運用於個人、學術或商業用途。 很多公司將 .NET Core 用為應用程式、工具、新平台及裝載服務的一部分。 這些公司有些在 GitHub 上對 .NET Core 貢獻良多，為產品方向提供指引，成為 [.NET Foundation Technical Steering Group](https://dotnetfoundation.org/blog/tsg-welcome) 的一部分。

### <a name="designed-for-adaptability"></a>可適性設計

.NET Core 近似其他 .NET 產品，但保有獨特性。 其設計能夠廣泛地配合新的平台及工作負載。 同時也提供多個 OS 及 CPU 連接埠，並可移植至更多 OS 和 CPU 連接埠。

該產品分成幾個部分，讓不同的部分可在不同時間適用於新的平台。 執行階段和特定平台基本程式庫必須移轉為一個單位。 無特定平台程式庫在所有平台都應該按建構照原樣運作。 減少特定平台實作的專案偏差會提高開發人員的效率，只要能全部或部分以該方式實作演算法或 API，就偏好非平台相關的 C# 程式碼。

人們常問如何實作 .NET Core 以支援多個作業系統。 他們通常會問是否有不同的實作，或是否使用[條件式編譯](https://en.wikipedia.org/wiki/Conditional_compilation)。 都有，是強式偏差趨向條件式編譯。

如以下圖表所示，[CoreFX](https://github.com/dotnet/corefx) \(英文\) 絕大部分是跨所有平台共用的非平台相關程式碼。 非平台相關程式碼可以實作為單一的可攜式組件，用在所有平台上。

![CoreFX：每個平台各有程式碼行](../images/corefx-platforms-loc.png)

Windows 與 Unix 實作大小相近。 因為 CoreFX 實作一些 Windows 專屬的功能，例如 [Microsoft.Win32.Registry](https://github.com/dotnet/corefx/tree/master/src/Microsoft.Win32.Registry)，所以 Windows 的實作較大，但尚未實作很多 Unix 專屬的概念。 您也會看到大多數的 Linux 和 macOS 實作會跨 Unix 實作共用，因此 Linux 和 macOS 特定實作的大小差相彷彿。

.NET Core 混用特定平台和非平台相關程式庫。 您可以在幾個範例中看到模式︰

- [CoreCLR](https://github.com/dotnet/coreclr) 是特定平台型的。 它建置於 OS 子系統上，像是記憶體管理員和執行緒排程器。
- [System.IO](https://github.com/dotnet/corefx/tree/master/src/System.IO) 及 [System.Security.Cryptography.Algorithms](https://github.com/dotnet/corefx/tree/master/src/System.Security.Cryptography.Algorithms) 會具有平台專屬性，每個 OS 上的儲存體和加密 API 都不一樣。
- [System.Collections](https://github.com/dotnet/corefx/tree/master/src/System.Collections) 和 [System.Linq](https://github.com/dotnet/corefx/tree/master/src/System.Linq) 是非關平台型，設它們在資料結構上建立與操作。

## <a name="comparisons-to-other-net-implementations"></a>與其他 .NET 實作的比較

比較 .NET Core 和現有的 .NET 實作，可能最容易了解 .NET Core 的大小和形態。

### <a name="comparison-with-net-framework"></a>與 .NET Framework 的比較

.NET 最早由 Microsoft 於 2000 年發表，從此不斷演進。 在將近二十年間，.NET Framework 始終是 Mocrosoft 生產的主要 .NET 實作。

.NET Core 和 .NET Framework 的主要差異︰

- **應用程式模型** -- .NET Core 並不支援所有的 .NET Framwork 應用程式模型。 尤其不支援 ASP.NET Web Forms 和 ASP.NET MVC，但支援 ASP.NET Core MVC。 已宣布 [.NET Core 3 將會支援 WPF 和 Windows Forms](https://devblogs.microsoft.com/dotnet/net-core-3-and-support-for-windows-desktop-applications/)。
- **API** -- .NET Core 包含大型的 .NET Framework 基底類別庫，但構成方式不同 (組件名稱不同；於類型上公開的成員在重要案例中也不同)。 這些差異在某些情況下需要將連接埠來源變更為 .NET Core (請參閱 [microsoft/dotnet-apiport](https://github.com/microsoft/dotnet-apiport))。 .NET Core 會實作 [.NET Standard](../standard/net-standard.md) API 規格。
- **子系統**：.NET Core 在 .NET Framework 中實作子系統的子集，目標是更簡單的實作和程式設計模型。 例如，不支援程式碼存取安全性 (CAS)，但支援反映。
- **平台**：.NET Framework 支援 Windows 和 Windows Server，但 .NET Core 也支援 macOS 及 Linux。
- **開放原始碼**：.NET Core 是開放原始碼，同時[唯讀的 .NET Framework 子集](https://github.com/microsoft/referencesource)也是開放原始碼。

雖然 .NET Core 很獨特，且與 .NET Framework 及其他 .NET 實作有顯著差異，卻可以直接使用原始程式碼或二進位共用技術在這些實作間共用程式碼。

由於 .NET Core 支援並行安裝，且其執行階段完全獨立於 .NET Framework，這使您可以在不產生任何問題的情況下，將它安裝到已經安裝 .NET Framework 的電腦上。

### <a name="comparison-with-mono"></a>與 Mono 的比較

[Mono](https://www.mono-project.com/) 是原始的跨平台和[開放原始碼](https://github.com/mono/mono) .NET 實作，首次發送為 2004 年。 它可以視為 .NET Framework 的社群複製體。 Mono 專案小組依賴 Microsoft 為提供相容實作而發行的開放 [.NET Standard](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) (特別是 ECMA 335)。

.NET Core 和 Mono 的主要差異︰

- **應用程式模型**：單聲道透過 Xamarin 產品支援 .NET Framework 應用程式模型的子集 (例如，Windows Forms) 和一些其他子集 (例如，[Xamarin.iOS](https://www.xamarin.com/platform))。 .NET Core 不支援這些。
- **API**：Mono 使用相同的組件名稱及分解，支援 .NET Framework API 的[大型子集](http://docs.go-mono.com/?link=root%3a%2fclasslib)。
- **平台**：Mono支援許多平台和 CPU。
- **開放原始碼**：Mono 與 .NET Core 都使用 MIT 授權且都是 .NET Foundation 專案。
- **重心** -- Mono 近年來主要著重於行動平台，而 .NET Core 則著重在雲端和桌面工作負載。
