---
title: 關於 .NET Core
description: 了解 .NET Core。
ms.date: 09/17/2019
ms.openlocfilehash: 89740b67b294650f78cf36361548c2fe24ac80cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147356"
---
# <a name="about-net-core"></a>關於 .NET Core

.NET Core 有以下特性：

- **跨平臺：** 在 Windows、macOS 和 Linux[作業系統](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)上運行。
- **在各架構間皆保持一致：** 在多個架構上 (包括 x64、x86 及 ARM) 可使用相同的行為執行程式碼。
- **命令列工具：** 包含易用的命令列工具，可用於本機開發及持續整合案例。
- **靈活部署：** 可以包含在應用中或並排安裝（使用者範圍或系統範圍安裝）。 可搭配 [Docker 容器](docker/introduction.md)使用。
- **相容：** .NET 核心通過[.NET 標準](../standard/net-standard.md)與 .NET 框架、Xamarin 和 Mono 相容。
- **開放原始碼︰**.NET Core 平台是開放原始碼，使用 MIT 和 Apache 2 授權。 .NET core 是 [.NET Foundation](https://dotnetfoundation.org/) 專案。
- **受 Microsoft 支援：**.NET Core 根據 [.NET Core 支援](https://dotnet.microsoft.com/platform/support/policy)受 Microsoft 支援。

## <a name="languages"></a>Languages

C#、Visual Basic 及 F# 語言可用於撰寫 .NET Core 應用程式和程式庫。 這些語言可用於您最喜愛的文字編輯器或整合式開發環境 （IDE），包括：

- [Visualstudio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [視覺工作室代碼](https://code.visualstudio.com/download)
- Sublime Text
- Vim

這種集成部分由[OmniSharp](https://www.omnisharp.net/)和[Ionide](http://ionide.io)專案的貢獻者提供。

## <a name="apis"></a>API

.NET Core 公開許多案例的 API，以下是其中幾個：

- 基元類型，如<xref:System.Boolean?displayProperty=nameWithType><xref:System.Int32?displayProperty=nameWithType>和 。
- 集合，例如 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 及 <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>。
- 公用程式類型，例如 <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 及 <xref:System.IO.FileStream?displayProperty=nameWithType>。
- 資料類型，例如 <xref:System.Data.DataSet?displayProperty=nameWithType> 及 [DbSet](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/)。
- 高性能類型，如<xref:System.Numerics.Vector?displayProperty=nameWithType>和[管道](../standard/io/pipelines.md)。

藉由實作 [.NET Standard](../standard/net-standard.md) 規格，.NET Core 可提供與 NET Framework 及 Mono API 的相容性。

## <a name="frameworks"></a>架構

已在 .NET Core 上建置多項架構：

- [ASP.NET Core](/aspnet/core/)
- [Windows 10 通用 Windows 平台 (UWP)](https://developer.microsoft.com/windows)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>撰寫

.NET Core 由下列部分組成：

- [.NET Core 運行時](https://github.com/dotnet/runtime/tree/master/src/coreclr)， 提供類型系統、 程式集載入、 垃圾回收器、 本機交互操作和其他基本服務. [.NET Core 框架庫](https://github.com/dotnet/runtime/tree/master/src/libraries)提供原始資料類型、應用組合類型和基本實用程式。
- [ASP.NET核心運行時](https://github.com/dotnet/aspnetcore)，它提供了一個框架，用於構建現代基於雲的互聯網連接應用程式，如 Web 應用程式、IoT 應用和移動後端。
- [.NET 核心 SDK](https://github.com/dotnet/sdk)和語言編譯器[（Roslyn](https://github.com/dotnet/roslyn)和[F#），](https://github.com/microsoft/visualfsharp)支援 .NET Core 開發人員體驗。
- [點網命令](./tools/dotnet.md)， 用於啟動 .NET 核心應用和 CLI 命令. 它選擇運行時並承載運行時，提供程式集載入策略，並啟動應用和工具。

這些元件的散發方式如下：

- [.NET Core 執行階段](https://dotnet.microsoft.com/download) -- 包括 .NET Core 執行階段及架構程式庫。
- [ASP.NET Core 執行階段](https://dotnet.microsoft.com/download) -- 包括 ASP.NET Core 和 .NET Core 執行階段及架構程式庫。
- [.NET 核心 SDK](https://dotnet.microsoft.com/download) -- 包括 .NET 核心 CLI、ASP.NET核心運行時和 .NET 核心運行時和框架。

### <a name="open-source"></a>開放原始碼

[.NET Core](https://github.com/dotnet/core) 是開放原始碼 ([MIT 授權](https://github.com/dotnet/core/blob/master/LICENSE.TXT))，且 Microsoft 已於 2014 年貢獻給 [.NET Foundation](https://dotnetfoundation.org)。 它現在是最活躍的 .NET 基礎專案之一。 它可以被個人和公司使用，包括用於個人、學術或商業目的。 多家公司使用 .NET Core 作為應用、工具、新平臺和託管服務的一部分。 這些公司有些在 GitHub 上對 .NET Core 貢獻良多，為產品方向提供指引，成為 [.NET Foundation Technical Steering Group](https://dotnetfoundation.org/blog/tsg-welcome) 的一部分。

### <a name="designed-for-adaptability"></a>可適性設計

.NET Core 是與其他 .NET 產品相比，是一種相似但獨特的產品。 它旨在實現對新平臺和工作負載的廣泛適應性，並且有多個可用的作業系統和 CPU 埠（並且可能會移植到更多）。

該產品分成幾個部分，讓不同的部分可在不同時間適用於新的平台。 執行階段和特定平台基本程式庫必須移轉為一個單位。 無特定平台程式庫在所有平台都應該按建構照原樣運作。 專案傾向于減少特定于平臺的實現以提高開發人員效率，喜歡在演算法或 API 可以以這種方式全部或部分實現時使用平臺中立的 C# 代碼。

人們常問如何實作 .NET Core 以支援多個作業系統。 他們通常會問是否有不同的實作，或是否使用[條件式編譯](https://en.wikipedia.org/wiki/Conditional_compilation)。 都有，是強式偏差趨向條件式編譯。

在下圖中可以看到，絕大多數[.NET Core 庫](https://github.com/dotnet/runtime/tree/master/src/libraries)都是跨所有平臺共用的平臺中立代碼。 非平台相關程式碼可以實作為單一的可攜式組件，用在所有平台上。

![CoreFX︰每個平台各有程式碼行](../images/corefx-platforms-loc.png)

Windows 與 Unix 實作大小相近。 由於 .NET Core 庫實現了一些僅限 Windows 的功能（如[Microsoft.Win32.Registry），](https://github.com/dotnet/runtime/tree/master/src/libraries/Microsoft.Win32.Registry)但尚未實現許多僅 Unix 概念，因此 Windows 具有較大的實現。 您還將看到，大多數 Linux 和 macOS 實現都是在 Unix 實現之間共用的，而特定于 Linux 和 macOS 的實現在大小上大致相同。

.NET Core 中混合了特定于平臺的庫和平臺中立的庫。 您可以在幾個範例中看到模式︰

- [CoreCLR](https://github.com/dotnet/runtime/tree/master/src/coreclr) 是特定平台型的。 它建置於 OS 子系統上，像是記憶體管理員和執行緒排程器。
- [System.IO](https://github.com/dotnet/runtime/tree/master/src/libraries/System.IO) 及 [System.Security.Cryptography.Algorithms](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Security.Cryptography.Algorithms) 會具有平台專屬性，每個 OS 上的儲存體和加密 API 都不一樣。
- [System.Collections](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Collections) 和 [System.Linq](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Linq) 是非關平台型，設它們在資料結構上建立與操作。

## <a name="comparisons-to-other-net-implementations"></a>與其他 .NET 實作的比較

通過將 .NET Core 與現有的 .NET 實現進行比較，可能更容易理解 .NET Core 的大小和形狀。

### <a name="comparison-with-net-framework"></a>與 .NET Framework 的比較

.NET 最早由 Microsoft 於 2000 年發表，從此不斷演進。 在將近二十年間，.NET Framework 始終是 Mocrosoft 生產的主要 .NET 實作。

.NET Core 和 .NET Framework 的主要差異︰

- **應用模型**-- . NET Core 不支援所有 .NET 框架應用模型。 尤其不支援 ASP.NET Web Forms 和 ASP.NET MVC，但支援 ASP.NET Core MVC。 從 .NET Core 3.0 開始，.NET Core 還僅支援 Windows 上的 WPF 和 Windows 表單。
- **API** -- .NET Core 包含大型的 .NET Framework 基底類別庫，但構成方式不同 (組件名稱不同；於類型上公開的成員在重要案例中也不同)。 在某些情況下，這些差異需要將埠源更改為 .NET Core。 有關詳細資訊，請參閱[.NET 可攜性分析器](../standard/analyzers/portability-analyzer.md)。 .NET Core 會實作 [.NET Standard](../standard/net-standard.md) API 規格。
- **子系統**：.NET Core 在 .NET Framework 中實作子系統的子集，目標是更簡單的實作和程式設計模型。 例如，不支援代碼訪問安全性 （CAS），而支援反射。
- **平台**：.NET Framework 支援 Windows 和 Windows Server，但 .NET Core 也支援 macOS 及 Linux。
- **開放原始碼**：.NET Core 是開放原始碼，同時[唯讀的 .NET Framework 子集](https://github.com/microsoft/referencesource)也是開放原始碼。

雖然 .NET Core 是唯一的，並且與 .NET 框架和其他 .NET 實現有顯著差異，但使用這些實現之間使用原始程式碼或二進位共用技術共用代碼非常簡單。

由於 .NET Core 支援並行安裝，且其執行階段完全獨立於 .NET Framework，這使您可以在不產生任何問題的情況下，將它安裝到已經安裝 .NET Framework 的電腦上。

### <a name="comparison-with-mono"></a>與 Mono 的比較

[單聲道](https://www.mono-project.com/)是 .NET 的原始跨平臺實現。 它最初是 .NET Framework[的開源](https://github.com/mono/mono)替代方案，隨著 iOS 和 Android 設備的普及，它過渡到面向行動裝置。 它可以視為 .NET Framework 的社群複製體。 Mono 專案團隊依靠 Microsoft 發佈的開放[.NET 標準](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md)（尤其是 ECMA 335）來提供相容的實現。

.NET Core 和 Mono 的主要差異︰

- **應用模型**-- Mono 支援 .NET Framework 應用模型（例如 Windows 表單）的子集，以及通過 Xamarin 產品進行移動開發的其他模型（例如[Xamarin.iOS）](https://www.xamarin.com/platform)的子集。 .NET 核心不支援 Xamarin。
- **API**：Mono 使用相同的組件名稱及分解，支援 .NET Framework API 的[大型子集](http://docs.go-mono.com/?link=root%3a%2fclasslib)。
- **平台**：Mono支援許多平台和 CPU。
- **開放原始碼**：Mono 與 .NET Core 都使用 MIT 授權且都是 .NET Foundation 專案。
- **重心** -- Mono 近年來主要著重於行動平台，而 .NET Core 則著重在雲端和桌面工作負載。

## <a name="the-future"></a>未來

據宣佈，.NET 5將是.NET Core的下一個版本，代表了平臺的統一。 該專案旨在通過以下幾個關鍵方式改進 .NET：

- 生成單個 .NET 運行時和框架，可隨處使用，並且具有統一的運行時行為和開發人員體驗。
- 通過充分利用 .NET 核心、.NET 框架、Xamarin 和 Mono 來擴展 .NET 的功能。
- 從開發人員（Microsoft 和社區）可以協同處理和擴展的單個代碼庫構建該產品，從而改進所有方案。

有關 .NET 5 計畫內容的更多詳細資訊，請參閱介紹[.NET 5](https://devblogs.microsoft.com/dotnet/introducing-net-5/)。
