---
title: .NET Core 概觀
description: 瞭解 .NET Core 的特性和組合，並將其與其他 .NET 部署進行比較。
ms.date: 03/26/2020
ms.openlocfilehash: e57451968ed8c4d5457acea084d3c6c9f998b8da
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144522"
---
# <a name="net-core-overview"></a>.NET Core 概觀

.NET Core 有以下特性：

- **跨平臺：** 可在 Windows、macOS 及 Linux[作業系統](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)上執行。
- **開放原始碼：**.NET Core 架構是[開放原始](https://github.com/dotnet/core)碼，使用 MIT 和 Apache 2 授權。 .NET core 是 [.NET Foundation](https://dotnetfoundation.org/) 專案。
- **現代化：** 它會實行非同步程式設計、使用結構的無複製模式，以及容器的資源控管等新式範例。
- **效能：** 透過[硬體內建函式](https://devblogs.microsoft.com/dotnet/hardware-intrinsics-in-net-core/)、階層式[編譯](https://github.com/dotnet/coreclr/blob/master/Documentation/design-docs/tiered-compilation.md)和[ \<T> Span](../standard/memory-and-spans/index.md)等功能，提供[高效](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-core-3-0/)能。
- **跨環境一致：** 在多個作業系統和架構（包括 x64、x86 及 ARM）上，以相同的行為執行您的程式碼。
- **命令列工具：** 包含便於使用的命令列工具，可用於本機開發及持續整合。
- **彈性的部署：** 您可以在應用程式中包含 .NET Core，或並存安裝（全使用者或全系統安裝）。 可搭配 [Docker 容器](docker/introduction.md)使用。

## <a name="languages"></a>Languages

[C #](../csharp/index.yml)、 [Visual Basic](../visual-basic/index.yml)和[F #](../fsharp/index.yml)語言可以用來撰寫適用于 .net Core 的應用程式和程式庫。 這些語言可用於您慣用的文字編輯器或整合式開發環境（IDE），包括：

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Visual Studio Code](https://code.visualstudio.com/download)

[OmniSharp](https://www.omnisharp.net/)和[Ionide](https://ionide.io)專案的參與者會在部分提供編輯器整合。

## <a name="apis"></a>API

.NET Core 會公開用來建立任何一種應用程式的架構：

* 具有[ASP.NET Core](/aspnet/core/)的雲端應用程式
* 使用[Xamarin](/xamarin)的行動應用程式
* IoT 應用程式搭配[system.web](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)
* 使用[WPF](../desktop-wpf/overview/index.md)和 Windows Forms 的 Windows 用戶端應用程式
* 機器學習[ML.NET](../machine-learning/index.yml)

包含許多可滿足一般需求的 Api：

- 基本類型，例如 <xref:System.Boolean?displayProperty=nameWithType> 和 <xref:System.Int32?displayProperty=nameWithType> 。
- 集合，例如 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 及 <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>。
- 公用程式類型，例如 <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 及 <xref:System.IO.FileStream?displayProperty=nameWithType>。
- 資料類型，例如 <xref:System.Data.DataSet?displayProperty=nameWithType> 和 <xref:System.Data.Entity.DbSet?displayProperty=nameWithType> 。
- 高效能類型，例如 <xref:System.Span%601?displayProperty=nameWithType> 、 <xref:System.Numerics.Vector?displayProperty=nameWithType> 和[管線](../standard/io/pipelines.md)。

藉由實作 [.NET Standard](../standard/net-standard.md) 規格，.NET Core 可提供與 NET Framework 及 Mono API 的相容性。

## <a name="composition"></a>Composition

.NET Core 由下列部分組成：

- [.Net Core 運行](https://github.com/dotnet/runtime/tree/master/src/coreclr)時間，提供類型系統、元件載入、垃圾收集行程、原生 interop 及其他基本服務。 [.Net Core framework 程式庫](https://github.com/dotnet/runtime/tree/master/src/libraries)提供基本資料類型、應用程式組合類型，以及基礎公用程式。
- [ASP.NET Core 運行](https://github.com/dotnet/aspnetcore)時間，可提供架構來建立現代化、雲端式、網際網路連線的應用程式，例如 web 應用程式、IoT 應用程式和行動後端。
- 可啟用 .NET Core 開發人員體驗的[.NET Core SDK](https://github.com/dotnet/sdk)和語言編譯器（[Roslyn](https://github.com/dotnet/roslyn)和[F #](https://github.com/microsoft/visualfsharp)）。
- [Dotnet 命令](./tools/dotnet.md)，用來啟動 .net Core 應用程式和 CLI 命令。 它會選取並裝載執行時間、提供元件載入原則，以及啟動應用程式和工具。

### <a name="open-source"></a>開放原始碼

[.Net Core](about.md)是一個[開放原始](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)碼的一般用途開發平臺。 您可以針對 x64、x86、ARM32 和 ARM64 處理器，建立適用于 Windows、macOS 和 Linux 的 .NET Core 應用程式。 針對[雲端](/aspnet/core/)、 [IoT](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)、[用戶端 UI](../desktop-wpf/overview/index.md)和[機器學習](../machine-learning/index.yml)服務提供架構和 api。

## <a name="support"></a>支援

Windows、macOS 和 Linux 上[的 Microsoft 都支援](https://dotnet.microsoft.com/platform/support/policy).net Core。 它會定期更新安全性和品質（每月第二個星期二）。

Microsoft 的 .NET Core 二進位散發套件已在 Azure 中的 Microsoft 維護伺服器上建立和測試，並遵循 Microsoft 工程和安全性實務。

[Red Hat 在 Red Hat Enterprise Linux (RHEL) 上支援 .NET Core](https://developers.redhat.com/topics/dotnet/)。 Red Hat 從原始碼建置 .NET Core 並在 [Red Hat 軟體集合](https://developers.redhat.com/products/softwarecollections/overview/)中提供。 Red Hat 與 Microsoft 共同作業以確保 .NET Core 可在 RHEL 上正確運作。

Tizen 在 Tizen 平臺上[支援 .Net Core](https://developer.tizen.org/development/training/.net-application) 。
