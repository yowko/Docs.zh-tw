---
title: .NET Core 指南
description: .NET Core 是適用于建立 Windows、Linux 和 macOS 應用程式的模組化、高效能的 .NET 執行。 了解 .NET Core 以開始使用。
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 80a3b12972e24c3022ac2aa14406aa60635815a3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75341359"
---
# <a name="net-core-guide"></a>.NET Core 指南

[.NET Core](about.md) 是[開放原始碼](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT)的一般用途開發平台，由 Microsoft 與 [GitHub](https://github.com/dotnet/core) 上的 .NET 社群共同維護。 它可以跨平台支援 Windows、macOS 與 Linux，並可用於建置裝置、雲端與 IoT 應用程式。

請參閱[關於 .NET Core](about.md)以深入了解 .NET Core，包括其特性、支援的語言與架構，亦即主要 API。

查看 [.NET Core 教學課程](tutorials/index.md) 以了解如何建立簡單的 .NET Core 應用程式。 只需要幾分鐘，您就可以啟動並執行您的第一個應用程式。 若要在您的瀏覽器中嘗試 .NET Core，請查看 [C# 中的數字](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)線上教學課程。

## <a name="download-net-core"></a>下載 .NET Core

下載[.NET Core SDK](https://www.microsoft.com/net/download) ，在您的 Windows、MacOS 或 Linux 電腦上嘗試 .net Core。 如果您想要使用 Docker 容器，請造訪[.Net Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/)。

若您要尋找另一個 .NET Core 版本，所有 .NET Core 版本都可以在 [.NET Core 下載 ](https://dotnet.microsoft.com/download/dotnet-core)找到。

## <a name="net-core-31"></a>.NET Core 3.1

最新版本是 .NET Core 3.1。 3.1 包含 .NET Core 3.0 的次要改良功能，但是 .NET Core 3.1 是[長期支援的版本](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。 如需 .NET Core 3.1 版本的詳細資訊，請參閱[.Net core 3.1 的新功能](./whats-new/dotnet-core-3-1.md)。

## <a name="create-your-first-application"></a>建立您的第一個應用程式

安裝 .NET Core SDK 之後，請開啟命令提示字元。 輸入下列 `dotnet` 命令來建立和執行C#應用程式：

```dotnetcli
dotnet new console
dotnet run
```

您應該會看到下列輸出：

```output
Hello World!
```

## <a name="support"></a>支援

Microsoft、Windows、macOS 和 Linux 上都[支援](https://dotnet.microsoft.com/platform/support/policy).net Core。 每年都為它推出安全性與品質更新數次，通常是一個月一次。

.NET Core 二進位發行版本是在 Azure 中由 Microsoft 維護的服務上建置及測試，而且享有與任何 Microsoft 產品一樣的支援。

[Red Hat 在 Red Hat Enterprise Linux (RHEL) 上支援 .NET Core](http://redhatloves.net/)。 Red Hat 從原始碼建置 .NET Core 並在 [Red Hat 軟體集合](https://developers.redhat.com/products/softwarecollections/overview/)中提供。 Red Hat 與 Microsoft 共同作業以確保 .NET Core 可在 RHEL 上正確運作。
