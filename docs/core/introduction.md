---
title: .NET Core 簡介和總覽
description: .NET Core 是適用于建立 Windows、Linux 和 macOS 應用程式之 .NET 的模組化高效能執行。 了解 .NET Core 以開始使用。
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 350fd50bee3403a05d1c19c9a692535613b17498
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538272"
---
# <a name="introduction-to-net-core"></a>.NET Core 簡介

[.Net Core](about.md) 是一個 [開放原始](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)碼的一般用途開發平臺。 您可以使用多種程式設計語言，為 x64、x86、ARM32 和 ARM64 處理器建立適用于 Windows、macOS 和 Linux 的 .NET Core 應用程式。 提供適用于 [雲端](/aspnet/core/)、 [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)、 [用戶端 UI](../desktop-wpf/overview/index.md)和 [機器學習](../machine-learning/index.yml)的架構和 api。

[下載 .NET Core SDK](https://dotnet.microsoft.com/download) ，以在您的電腦上嘗試 .net Core。 最新版本是 [.Net Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)。

## <a name="download-net-core"></a>下載 .NET Core

您可以透過下列方式取得 .NET Core：

* [適用于 Windows 和 macOS 的安裝程式](https://dotnet.microsoft.com/download)
* [Linux 套件](./install/linux.md)
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

.NET Core 是開放式平臺。 大家都歡迎參與。

* 在 [開發人員社群](https://developercommunity.visualstudio.com/spaces/61/index.html)提出產品問題和問題。
* 您應該在其中一個專案存放庫（例如 [dotnet/runtime](https://github.com/dotnet/runtime)、 [dotnet/sdk](https://github.com/dotnet/sdk)、 [dotnet/rosyln](https://github.com/dotnet/roslyn)或 [aspnetcore](https://github.com/dotnet/aspnetcore)）上進行產品貢獻。 如需詳細資訊，請參閱 [.Net Core 存放庫](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md)。

## <a name="support"></a>支援

Microsoft 在 Windows、macOS 和 Linux 上以及 Red Hat Enterprise Linux 上的 Red Hat 都支援 .NET Core。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [.NET Core 教學課程](tutorials/index.md)

> [!div class="nextstepaction"]
> [在您的瀏覽器中嘗試 .NET Core](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
