---
title: .NET Core 概觀
description: 深入瞭解 .NET Core 的特性和組合，並將其與其他 .NET 的實現進行比較。
ms.date: 03/26/2020
ms.openlocfilehash: e99939cf85cc441fd473e4d033e22b1a5d053638
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539004"
---
# <a name="net-core-overview"></a>.NET Core 概觀

> [!div class="button"]
> [下載 .NET Core](https://dotnet.microsoft.com/download)

.NET Core 有以下特性：

- **跨平臺：** 可在 Windows、macOS 和 Linux [作業系統](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)上執行。
- **開放原始碼：** .NET Core framework 是 [開放原始](https://github.com/dotnet/core)碼，使用 MIT 和 Apache 2 授權。 .NET core 是 [.NET Foundation](https://dotnetfoundation.org/) 專案。
- **新式：** 它會實作為非同步程式設計的新式架構、使用結構的無複製模式，以及容器的資源管理。
- **效能：** 透過[硬體內建函式](https://devblogs.microsoft.com/dotnet/hardware-intrinsics-in-net-core/)、階層式[編譯](https://github.com/dotnet/coreclr/blob/master/Documentation/design-docs/tiered-compilation.md)和[ \<T> 範圍](../standard/memory-and-spans/index.md)等功能，提供[高效](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-core-3-0/)能。
- **跨環境一致：** 使用多個作業系統和架構（包括 x64、x86 和 ARM）的相同行為來執行程式碼。
- **命令列工具：**  包含便於使用的命令列工具，可用於本機開發及持續整合。
- **彈性部署：** 您可以在應用程式中包含 .NET Core，或並存安裝 (全使用者或全系統安裝) 。 可搭配 [Docker 容器](docker/introduction.md)使用。

## <a name="languages"></a>語言

[C #](../csharp/index.yml)、 [Visual Basic](../visual-basic/index.yml)和[F #](../fsharp/index.yml)語言可用來撰寫適用于 .net Core 的應用程式和程式庫。 這些語言可用於您慣用的文字編輯器或整合式開發環境 (IDE) ，包括：

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Visual Studio Code](https://code.visualstudio.com/download)

[OmniSharp](https://www.omnisharp.net/)和[Ionide](https://ionide.io)專案的參與者也會提供編輯器整合。

## <a name="apis"></a>API

.NET Core 公開架構來建立任何類型的應用程式：

* 具有[ASP.NET Core](/aspnet/core/)的雲端應用程式
* 使用[Xamarin](/xamarin)的行動應用程式
* [使用 system.servicemodel 的 IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)應用程式
* 使用 [WPF](../desktop-wpf/overview/index.md) 和 Windows Forms 的 Windows 用戶端應用程式
* Machine learning [ML.NET](../machine-learning/index.yml)

包含許多 Api 來滿足常見需求：

- 基本類型，例如 <xref:System.Boolean?displayProperty=nameWithType> 和 <xref:System.Int32?displayProperty=nameWithType> 。
- 集合，例如 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 及 <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>。
- 公用程式類型，例如 <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 及 <xref:System.IO.FileStream?displayProperty=nameWithType>。
- 資料類型，例如 <xref:System.Data.DataSet?displayProperty=nameWithType> 和 <xref:System.Data.Entity.DbSet?displayProperty=nameWithType> 。
- 高效能類型，例如 <xref:System.Span%601?displayProperty=nameWithType> 、 <xref:System.Numerics.Vector?displayProperty=nameWithType> 和 [管線](../standard/io/pipelines.md)。

藉由實作 [.NET Standard](../standard/net-standard.md) 規格，.NET Core 可提供與 NET Framework 及 Mono API 的相容性。

## <a name="composition"></a>Composition

.NET Core 由下列部分組成：

- [.Net Core 運行](https://github.com/dotnet/runtime/tree/master/src/coreclr)時間，可提供類型系統、元件載入、垃圾收集行程、原生 interop 及其他基本服務。 [.Net Core framework 程式庫](https://github.com/dotnet/runtime/tree/master/src/libraries) 提供基本資料類型、應用程式組合類型及基本公用程式。
- [ASP.NET Core 運行](https://github.com/dotnet/aspnetcore)時間，其提供架構來建立新式、雲端式、網際網路連線的應用程式，例如 web 應用程式、IoT 應用程式和行動後端。
- [.NET Core SDK](https://github.com/dotnet/sdk)和語言編譯器 ([Roslyn](https://github.com/dotnet/roslyn)和[F #](https://github.com/microsoft/visualfsharp)) ，可啟用 .net Core 開發人員體驗。
- [Dotnet 命令](./tools/dotnet.md)，用來啟動 .net Core 應用程式和 CLI 命令。 它會選取和裝載執行時間、提供元件載入原則，以及啟動應用程式和工具。

### <a name="open-source"></a>開放原始碼

[.Net Core](about.md) 是一個 [開放原始](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)碼的一般用途開發平臺。 您可以針對 x64、x86、ARM32 和 ARM64 處理器建立適用于 Windows、macOS 和 Linux 的 .NET Core 應用程式。 提供適用于 [雲端](/aspnet/core/)、 [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)、 [用戶端 UI](../desktop-wpf/overview/index.md)和 [機器學習](../machine-learning/index.yml)的架構和 api。

## <a name="support"></a>支援

Microsoft 在 Windows、macOS 和 Linux 上 [支援](https://dotnet.microsoft.com/platform/support/policy) .net Core。 它會定期更新 (每個月的第二個星期二) 的安全性和品質。

Microsoft 的 .NET Core 二進位散發套件是在 Azure 中 Microsoft 維護的伺服器上建立和測試，並遵循 Microsoft 工程和安全性實務。

[Red Hat 在 Red Hat Enterprise Linux (RHEL) 上支援 .NET Core](https://developers.redhat.com/topics/dotnet/)。 Red Hat 從原始碼建置 .NET Core 並在 [Red Hat 軟體集合](https://developers.redhat.com/products/softwarecollections/overview/)中提供。 Red Hat 與 Microsoft 共同作業以確保 .NET Core 可在 RHEL 上正確運作。

[Tizen 支援](https://developer.tizen.org/development/training/.net-application) Tizen 平臺上的 .net Core。
