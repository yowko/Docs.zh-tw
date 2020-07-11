---
title: .NET Core 簡介和總覽
description: .NET Core 是適用于建立 Windows、Linux 和 macOS 應用程式的模組化、高效能的 .NET 執行。 了解 .NET Core 以開始使用。
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: b28ad965e54680e2e1134c389266741ade28084f
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226578"
---
# <a name="introduction-to-net-core"></a>.NET Core 簡介

[.Net Core](about.md)是一個[開放原始](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)碼的一般用途開發平臺。 您可以使用多種程式設計語言，為 x64、x86、ARM32 和 ARM64 處理器建立適用于 Windows、macOS 和 Linux 的 .NET Core 應用程式。 針對[雲端](/aspnet/core/)、 [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)、[用戶端 UI](../desktop-wpf/overview/index.md)和[機器學習](/dotnet/machine-learning/)服務提供架構和 api。

[下載 .NET Core SDK](https://dotnet.microsoft.com/download)以在您的電腦上試用 .net Core。 最新版本是[.Net Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)。

## <a name="download-net-core"></a>下載 .NET Core

您可以透過下列方式取得 .NET Core：

* [Windows 和 macOS 的安裝程式](https://dotnet.microsoft.com/download)
* [Linux 套件](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [Docker 容器](https://hub.docker.com/_/microsoft-dotnet-core/)
* [Zips 和留下 tarball](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [安裝腳本](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [版本資訊](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a>建立您的第一個應用程式

安裝 .NET Core SDK 之後，請開啟命令提示字元。 使用下列命令來建立和執行應用程式：

```dotnetcli
dotnet new console
dotnet run
```

您應該會看見下列輸出：

```output
Hello World!
```

## <a name="contribute"></a>參與

.NET Core 是一個開放式平臺。 大家都歡迎參加。

* 在[開發人員的社區](https://developercommunity.visualstudio.com/spaces/61/index.html)提出產品問題和問題。
* 產品貢獻應在其中一個專案存放庫上進行，例如[dotnet/runtime](https://github.com/dotnet/runtime)、 [dotnet/sdk](https://github.com/dotnet/sdk)、 [dotnet/rosyln](https://github.com/dotnet/roslyn)或[aspnetcore](https://github.com/dotnet/aspnetcore)。 如需詳細資訊，請參閱[.Net Core 存放庫](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md)。

## <a name="support"></a>支援

Windows、macOS 和 Linux 上的 Microsoft 以及 Red Hat Enterprise Linux 上的 Red Hat 都支援 .NET Core。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [.NET Core 教學課程](tutorials/index.md)

> [!div class="nextstepaction"]
> [在您的瀏覽器中嘗試 .NET Core](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
