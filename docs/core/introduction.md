---
title: .NET 核心簡介和概述
description: .NET Core 是 .NET 的模組化高性能實現，用於創建 Windows、Linux 和 macOS 應用。 了解 .NET Core 以開始使用。
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: a20cdda5cbd366d04e7ee9e8df3d1b15d10c1f4a
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391157"
---
# <a name="introduction-to-net-core"></a>.NET Core 簡介

[.NET Core](about.md)是一個[開源](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)的通用開發平臺。 您可以使用多種程式設計語言為 X64、x86、ARM32 和 ARM64 處理器創建 .NET 核心應用。 為[雲](/aspnet/core/)、[物聯網](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)、[用戶端 UI](/dotnet/desktop-wpf/overview/index)和[機器學習](/dotnet/machine-learning/)提供了框架和 API。

[下載 .NET 核心 SDK，](https://dotnet.microsoft.com/download)在電腦上嘗試 .NET Core。 最新版本是[.NET 核心 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)。

## <a name="download-net-core"></a>下載 .NET Core

您可以通過以下方式獲取 .NET Core：

* [適用于 Windows 和 macOS 的安裝程式](https://dotnet.microsoft.com/download)
* [Linux 套件](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [Docker 容器](https://hub.docker.com/_/microsoft-dotnet-core/)
* [拉鍊和焦油球](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [安裝腳本](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [版本資訊](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a>建立您的第一個應用程式

安裝 .NET Core SDK 之後，請開啟命令提示字元。 使用以下命令創建和運行應用程式：

```dotnetcli
dotnet new console
dotnet run
```

您應該會看見下列輸出：

```output
Hello World!
```

## <a name="contribute"></a>參與

.NET 核心是一個開放的平臺。 歡迎大家參加。

* 在[開發人員社區](https://developercommunity.visualstudio.com/spaces/61/index.html)中歸檔產品問題和問題。
* 應在其中一個專案存儲庫上進行產品貢獻，例如[dotnet/運行時](https://github.com/dotnet/runtime)、[點網/sdk、dotnet/rosyln](https://github.com/dotnet/sdk)或[aspnetcore](https://github.com/dotnet/aspnetcore)。 [dotnet/rosyln](https://github.com/dotnet/roslyn) 有關詳細資訊，請參閱[.NET 核心存儲庫](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md)。

## <a name="support"></a>支援

.NET Core 在 Windows、macOS 和 Linux 上得到 Microsoft 的支援，紅帽企業 Linux 上支援紅帽。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [.NET 核心教程](tutorials/index.md)

> [!div class="nextstepaction"]
> [在瀏覽器中試用 .NET 核心](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
