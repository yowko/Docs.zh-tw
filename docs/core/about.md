---
title: .NET Core 概觀
description: 瞭解 .NET Core 的特徵和組成，並將其與其他 .NET 實現進行比較。
ms.date: 03/26/2020
ms.openlocfilehash: c9a63ddba14cf176be529e9520027c0610cfc087
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391165"
---
# <a name="net-core-overview"></a>.NET Core 概觀

.NET Core 有以下特性：

- **交叉平臺：** 在 Windows、macOS 和 Linux[作業系統](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)上運行。
- **開源：**.NET 核心框架是[開源](https://github.com/dotnet/core)的，使用 MIT 和 Apache 2 許可證。 .NET core 是 [.NET Foundation](https://dotnetfoundation.org/) 專案。
- **現代：** 它實現了現代範例，如非同步程式設計、使用結構的無複製模式以及容器的資源治理。
- **性能：** 提供[高性能](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-core-3-0/)的功能，如[硬體內部](https://devblogs.microsoft.com/dotnet/hardware-intrinsics-in-net-core/)，[分層編譯](https://github.com/dotnet/coreclr/blob/master/Documentation/design-docs/tiered-compilation.md)，和[Span\<T>。](../standard/memory-and-spans/index.md)
- **跨環境一致：** 在多個作業系統和體系結構（包括 x64、x86 和 ARM）上運行具有相同行為的代碼。
- **命令列工具：** 包括便於使用的命令列工具，可用於本地開發和持續集成。
- **靈活部署：** 您可以在應用中包括 .NET Core，也可以並排安裝（使用者範圍或系統範圍安裝）。 可搭配 [Docker 容器](docker/introduction.md)使用。

## <a name="languages"></a>Languages

[C#、](../csharp/index.yml)[可視基本](../visual-basic/index.yml)語言和[F#](../fsharp/index.yml)語言可用於為 .NET Core 編寫應用程式和庫。 這些語言可用於您最喜愛的文字編輯器或整合式開發環境 （IDE），包括：

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [視覺工作室代碼](https://code.visualstudio.com/download)

編輯器集成部分由[OmniSharp](https://www.omnisharp.net/)和[Ionide](http://ionide.io)專案的貢獻者提供。

## <a name="apis"></a>API

.NET Core 公開用於構建任何類型的應用的框架：

* 具有[ASP.NET核心的](/aspnet/core/)雲應用
* 帶有[Xamarin 的](/xamarin)移動應用程式
* 帶[System.Device.GPIO](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)的 IoT 應用
* 具有[WPF](../desktop-wpf/overview/index.md)和 Windows 表單的 Windows 用戶端應用
* 機器學習[ML.NET](../machine-learning/index.yml)

包括許多滿足常見需求的 API：

- 基元類型，如<xref:System.Boolean?displayProperty=nameWithType><xref:System.Int32?displayProperty=nameWithType>和 。
- 集合，例如 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 及 <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>。
- 公用程式類型，例如 <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> 及 <xref:System.IO.FileStream?displayProperty=nameWithType>。
- 資料類型，如<xref:System.Data.DataSet?displayProperty=nameWithType>和<xref:System.Data.Entity.DbSet?displayProperty=nameWithType>。
- 高性能類型，如<xref:System.Span%601?displayProperty=nameWithType>，<xref:System.Numerics.Vector?displayProperty=nameWithType>和[管道](../standard/io/pipelines.md)。

藉由實作 [.NET Standard](../standard/net-standard.md) 規格，.NET Core 可提供與 NET Framework 及 Mono API 的相容性。

## <a name="composition"></a>撰寫

.NET Core 由下列部分組成：

- [.NET Core 運行時](https://github.com/dotnet/runtime/tree/master/src/coreclr)， 提供類型系統、 程式集載入、 垃圾回收器、 本機交互操作和其他基本服務. [.NET Core 框架庫](https://github.com/dotnet/runtime/tree/master/src/libraries)提供原始資料類型、應用組合類型和基本實用程式。
- [ASP.NET核心運行時](https://github.com/dotnet/aspnetcore)，它提供了一個框架，用於構建現代的基於雲的互聯網連接應用程式，如 Web 應用、IoT 應用和移動後端。
- [.NET 核心 SDK](https://github.com/dotnet/sdk)和語言編譯器[（Roslyn](https://github.com/dotnet/roslyn)和[F#），](https://github.com/microsoft/visualfsharp)支援 .NET Core 開發人員體驗。
- [點網命令](./tools/dotnet.md)， 用於啟動 .NET 核心應用和 CLI 命令. 它選擇並承載運行時，提供程式集載入策略，並啟動應用和工具。

### <a name="open-source"></a>開放原始碼

[.NET Core](about.md)是一個[開源](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)的通用開發平臺。 您可以為 X64、x86、ARM32 和 ARM64 處理器創建 .NET 核心應用。 為[雲](/aspnet/core/)、[物聯網](https://docs.microsoft.com/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)、[用戶端 UI](../desktop-wpf/overview/index.md)和[機器學習](../machine-learning/index.yml)提供了框架和 API。

## <a name="support"></a>支援

.NET Core 在 Windows、macOS 和 Linux 上[得到微軟的支援](https://dotnet.microsoft.com/platform/support/policy)。 它定期更新安全性和品質（每月的第二個星期二）。

來自 Microsoft 的 .NET Core 二進位分發在 Azure 中的 Microsoft 維護伺服器上構建和測試，並遵循 Microsoft 工程和安全實踐。

[Red Hat 在 Red Hat Enterprise Linux (RHEL) 上支援 .NET Core](http://redhatloves.net/)。 Red Hat 從原始碼建置 .NET Core 並在 [Red Hat 軟體集合](https://developers.redhat.com/products/softwarecollections/overview/)中提供。 Red Hat 與 Microsoft 共同作業以確保 .NET Core 可在 RHEL 上正確運作。

Tizen 在 Tizen 平臺上[支援 .NET Core。](https://developer.tizen.org/development/training/.net-application)
