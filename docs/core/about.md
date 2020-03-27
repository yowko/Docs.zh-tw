---
title: .NET Core 概觀
description: 瞭解 .NET Core 的特徵和組成，並將其與其他 .NET 實現進行比較。
ms.date: 09/17/2019
ms.openlocfilehash: f2f97fe6a5f822266582c443fd916c270cb0cb6a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345207"
---
# <a name="net-core-overview"></a>.NET Core 概觀

.NET Core 有以下特性：

- **跨平臺：** 在 Windows、macOS 和 Linux[作業系統](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)上運行。
- **在各架構間皆保持一致：** 在多個架構上 (包括 x64、x86 及 ARM) 可使用相同的行為執行程式碼。
- **命令列工具：** 包含易用的命令列工具，可用於本機開發及持續整合案例。
- **靈活部署：** 可以包含在應用中或並排安裝（使用者範圍或系統範圍安裝）。 可搭配 [Docker 容器](docker/introduction.md)使用。
- **相容：** .NET Core 通過[.NET 標準](../standard/net-standard.md)與 .NET 框架、Xamarin 和 Mono 實現相容。
- **開放原始碼︰**.NET Core 平台是開放原始碼，使用 MIT 和 Apache 2 授權。 .NET core 是 [.NET Foundation](https://dotnetfoundation.org/) 專案。
- **微軟支援：** .NET Core[得到微軟的支援](https://dotnet.microsoft.com/platform/support/policy)。

## <a name="languages"></a>Languages

C#、Visual Basic 和 F# 語言可以用來撰寫 .NET Core 應用程式和程式庫。 這些語言可用於您最喜愛的文字編輯器或整合式開發環境 （IDE），包括：

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [視覺工作室代碼](https://code.visualstudio.com/download)
- Sublime Text
- Vim

編輯器集成部分由[OmniSharp](https://www.omnisharp.net/)和[Ionide](http://ionide.io)專案的貢獻者提供。

## <a name="apis"></a>API

包括許多滿足常見需求的 API，例如：

- 基元類型，如<xref:System.Boolean?displayProperty=nameWithType><xref:System.Int32?displayProperty=nameWithType>和 。
- 集合，例如 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 及 <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>。
- 公用程式類型，例如 <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 及 <xref:System.IO.FileStream?displayProperty=nameWithType>。
- 資料類型，例如 <xref:System.Data.DataSet?displayProperty=nameWithType> 及 [DbSet](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/)。
- 高性能類型，如<xref:System.Numerics.Vector?displayProperty=nameWithType>和[管道](../standard/io/pipelines.md)。

藉由實作 [.NET Standard](../standard/net-standard.md) 規格，.NET Core 可提供與 NET Framework 及 Mono API 的相容性。

## <a name="frameworks"></a>架構

在 .NET Core 之上構建了多個框架，包括：

- [ASP.NET Core](/aspnet/core/)
- [通用 Windows 平台 (UWP)](/windows/uwp/)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>撰寫

.NET Core 由下列部分組成：

- [.NET Core 運行時](https://github.com/dotnet/runtime/tree/master/src/coreclr)， 提供類型系統、 程式集載入、 垃圾回收器、 本機交互操作和其他基本服務. [.NET Core 框架庫](https://github.com/dotnet/runtime/tree/master/src/libraries)提供原始資料類型、應用組合類型和基本實用程式。
- [ASP.NET核心運行時](https://github.com/dotnet/aspnetcore)，它提供了一個框架，用於構建現代的基於雲的互聯網連接應用程式，如 Web 應用、IoT 應用和移動後端。
- [.NET 核心 SDK](https://github.com/dotnet/sdk)和語言編譯器[（Roslyn](https://github.com/dotnet/roslyn)和[F#），](https://github.com/microsoft/visualfsharp)支援 .NET Core 開發人員體驗。
- [點網命令](./tools/dotnet.md)， 用於啟動 .NET 核心應用和 CLI 命令. 它選擇並承載運行時，提供程式集載入策略，並啟動應用和工具。

這些元件的散發方式如下：

- [.NET Core 執行階段](https://dotnet.microsoft.com/download) -- 包括 .NET Core 執行階段及架構程式庫。
- [ASP.NET核心運行時](https://dotnet.microsoft.com/download)-- 包括ASP.NET核心和 .NET 核心運行時和框架庫。
- [.NET 核心 SDK](https://dotnet.microsoft.com/download) -- 包括 .NET 核心 CLI、ASP.NET核心運行時和 .NET 核心運行時和框架。

### <a name="open-source"></a>開放原始碼

[.NET Core](https://github.com/dotnet/core)是開源 （[MIT 許可證](https://github.com/dotnet/core/blob/master/LICENSE.TXT)）， 2014 年被微軟為[.NET 基金會](https://dotnetfoundation.org)捐款. 它現在是最活躍的 .NET 基礎專案之一。 它可以被個人和公司使用，包括用於個人、學術或商業目的。 多家公司使用 .NET Core 作為應用、工具、新平臺和託管服務的一部分。 這些公司有些在 GitHub 上對 .NET Core 貢獻良多，為產品方向提供指引，成為 [.NET Foundation Technical Steering Group](https://dotnetfoundation.org/blog/tsg-welcome) 的一部分。

### <a name="designed-for-adaptability"></a>可適性設計

.NET Core 是與其他 .NET 產品相比，是一種相似但獨特的產品。 它旨在實現對新平臺和工作負載的廣泛適應性，並且有多個可用的作業系統和 CPU 埠（並且可能會移植到更多）。

該產品分成幾個部分，讓不同的部分可在不同時間適用於新的平台。 執行階段和特定平台基本程式庫必須移轉為一個單位。 無特定平台程式庫在所有平台都應該按建構照原樣運作。 專案傾向于減少特定于平臺的實現以提高開發人員效率，喜歡在演算法或 API 可以以這種方式全部或部分實現時使用平臺中立的 C# 代碼。

人們常問如何實作 .NET Core 以支援多個作業系統。 他們通常會問是否有不同的實作，或是否使用[條件式編譯](https://en.wikipedia.org/wiki/Conditional_compilation)。 都有，是強式偏差趨向條件式編譯。

在下圖中可以看到，絕大多數[.NET Core 庫](https://github.com/dotnet/runtime/tree/master/src/libraries)都是從跨所有平臺共用的平臺中立代碼編譯的。 平臺中立代碼可以作為單個可移植程式集實現，該程式集用於所有平臺。

![CoreFX︰每個平台各有程式碼行](../images/corefx-platforms-loc.png)

Windows 和 Unix 實現的大小相似。 Windows 實現包含一些僅限 Windows 的功能，如[Microsoft.Win32.Registry](https://github.com/dotnet/runtime/tree/master/src/libraries/Microsoft.Win32.Registry)，但尚未實現許多僅 Unix 的概念。 許多 Linux 和 macOS 實現在 Unix 實現之間共用。 特定于 Linux 和 macOS 的實現在大小上相似。

.NET Core 中混合了特定于平臺的庫和平臺中立的庫。 您可以在幾個範例中看到模式︰

- [CoreCLR](https://github.com/dotnet/runtime/tree/master/src/coreclr) 是特定平台型的。 它建置於 OS 子系統上，像是記憶體管理員和執行緒排程器。
- [System.IO](https://github.com/dotnet/runtime/tree/master/src/libraries/System.IO) 及 [System.Security.Cryptography.Algorithms](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Security.Cryptography.Algorithms) 會具有平台專屬性，每個 OS 上的儲存體和加密 API 都不一樣。
- [System.Collections](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Collections) 和 [System.Linq](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Linq) 是非關平台型，設它們在資料結構上建立與操作。

## <a name="comparisons-to-other-net-implementations"></a>與其他 .NET 實作的比較

為了瞭解 .NET Core 的大小和形狀，以下各節將其與現有的 .NET 實現進行比較。

### <a name="net-core-vs-net-framework"></a>.NET 核心 vs. .NET 框架

.NET 于 2000 年由微軟首次發佈，並從那裡發展而來。 .NET 框架是微軟在近二十年間生成的主要 .NET 實現。

.NET 核心和 .NET 框架之間的主要區別是：

- **應用模型**-- . NET Core 不支援所有 .NET 框架應用模型。 尤其不支援 ASP.NET Web Forms 和 ASP.NET MVC，但支援 ASP.NET Core MVC。 從 .NET Core 3.0 開始，.NET Core 還僅支援 Windows 上的 WPF 和 Windows 表單。
- **API** -- .NET Core 包含大型的 .NET Framework 基底類別庫，但構成方式不同 (組件名稱不同；於類型上公開的成員在重要案例中也不同)。 在某些情況下，這些差異需要將埠源更改為 .NET Core。 有關詳細資訊，請參閱[.NET 可攜性分析器](../standard/analyzers/portability-analyzer.md)。 .NET Core 會實作 [.NET Standard](../standard/net-standard.md) API 規格。
- **子系統**-- .NET Core 在 .NET Framework 中實現子系統的子集，目標是更簡單的實現和程式設計模型。 例如，不支援代碼訪問安全性 （CAS），而支援反射。
- **平臺**-- .NET框架支援Windows和Windows伺服器，而.NET核心也支援macOS和Linux。
- **開源**-- .NET Core是開源的，而[.NET 框架的唯讀子集](https://github.com/microsoft/referencesource)是開源。

雖然 .NET Core 是唯一的，並且與 .NET 框架和其他 .NET 實現有顯著差異，但使用這些實現之間使用原始程式碼或二進位共用技術共用代碼非常簡單。

由於 .NET Core 支援並行安裝，並且其運行時完全獨立于 .NET Framework，因此可以在安裝了 .NET Framework的電腦上安裝，沒有任何問題。

### <a name="net-core-vs-mono"></a>.NET 核心 vs. 單聲道

[單聲道](https://www.mono-project.com/)是 .NET 的原始跨平臺實現。 它最初是 .NET Framework[的開源](https://github.com/mono/mono)替代方案，隨著 iOS 和 Android 設備的普及，它過渡到面向行動裝置。 它可以被看作是 .NET 框架的社區克隆。 為了提供相容的實現，Mono 專案團隊依賴于 Microsoft 發佈的開放[.NET 標準](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md)（特別是 ECMA 335）。

.NET 核心和單聲道之間的主要區別是：

- **應用模型**-- Mono 支援 .NET Framework 應用模型（例如 Windows 表單）的子集，以及通過 Xamarin 產品進行移動開發的其他模型（例如[Xamarin.iOS）](https://www.xamarin.com/platform)的子集。 .NET 核心不支援 Xamarin。
- **API**：Mono 使用相同的組件名稱及分解，支援 .NET Framework API 的[大型子集](http://docs.go-mono.com/?link=root%3a%2fclasslib)。
- **平台**：Mono支援許多平台和 CPU。
- **開放原始碼**：Mono 與 .NET Core 都使用 MIT 授權且都是 .NET Foundation 專案。
- **重心** -- Mono 近年來主要著重於行動平台，而 .NET Core 則著重在雲端和桌面工作負載。

## <a name="support"></a>支援

.NET Core 在 Windows、macOS 和 Linux 上[得到微軟的支援](https://dotnet.microsoft.com/platform/support/policy)。 它定期更新安全性和品質（每月的第二個星期二）。

來自 Microsoft 的 .NET Core 二進位分發在 Azure 中的 Microsoft 維護伺服器上構建和測試，並遵循 Microsoft 工程和安全實踐。

[Red Hat 在 Red Hat Enterprise Linux (RHEL) 上支援 .NET Core](http://redhatloves.net/)。 Red Hat 從原始碼建置 .NET Core 並在 [Red Hat 軟體集合](https://developers.redhat.com/products/softwarecollections/overview/)中提供。 Red Hat 與 Microsoft 共同作業以確保 .NET Core 可在 RHEL 上正確運作。

Tizen 在 Tizen 平臺上[支援 .NET Core。](https://developer.tizen.org/development/training/.net-application)
