---
title: .NET 核心簡介和概述
description: .NET Core 是 .NET 的模組化高性能實現，用於創建 Windows、Linux 和 macOS 應用。 了解 .NET Core 以開始使用。
author: richlander
ms.date: 03/25/2020
ms.custom: updateeachrelease
ms.openlocfilehash: edd3864d3c3c5c0e9fd8c26ee806ffc9e100423d
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80351698"
---
# <a name="introduction-to-net-core"></a>.NET 核心簡介

[.NET Core](about.md)是一個[開源](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)的通用開發平臺，由微軟和[GitHub](https://github.com/dotnet/core)上的 .NET 社區維護。 它可以跨平台支援 Windows、macOS 與 Linux，並可用於建置裝置、雲端與 IoT 應用程式。

## <a name="download-net-core"></a>下載 .NET Core

下載[.NET 核心 SDK，](https://dotnet.microsoft.com/download)在 Windows、macOS 或 Linux 電腦上嘗試 .NET 酷睿。 如果您更喜歡使用 Docker 容器，請訪問[.NET 核心 Docker 集線器 。](https://hub.docker.com/_/microsoft-dotnet-core/)

## <a name="net-core-31"></a>.NET 核心 3.1

最新版本是 .NET 核心 3.1。 3.1 包括對 .NET Core 3.0 的細微改進，但是.NET Core 3.1 是長期[支援的版本](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。 有關 .NET Core 3.1 版本的詳細資訊，請參閱[.NET Core 3.1 中的新增功能](./whats-new/dotnet-core-3-1.md)。

如果您正在尋找 .NET Core 的另一個版本，所有版本都可以在[.NET Core 下載中](https://dotnet.microsoft.com/download/dotnet-core)提供。

## <a name="create-your-first-application"></a>建立您的第一個應用程式

安裝 .NET Core SDK 之後，請開啟命令提示字元。 輸入以下`dotnet`命令以創建和運行 C# 應用程式：

```dotnetcli
dotnet new console
dotnet run
```

您應該會看見下列輸出：

```output
Hello World!
```

## <a name="support"></a>支援

.NET Core 在 Windows、macOS 和 Linux 上[得到微軟的支援](https://dotnet.microsoft.com/platform/support/policy)。 每年都為它推出安全性與品質更新數次，通常是一個月一次。

.NET Core 二進位發行版本是在 Azure 中由 Microsoft 維護的服務上建置及測試，而且享有與任何 Microsoft 產品一樣的支援。

[Red Hat 在 Red Hat Enterprise Linux (RHEL) 上支援 .NET Core](http://redhatloves.net/)。 Red Hat 從原始碼建置 .NET Core 並在 [Red Hat 軟體集合](https://developers.redhat.com/products/softwarecollections/overview/)中提供。 Red Hat 與 Microsoft 共同作業以確保 .NET Core 可在 RHEL 上正確運作。

## <a name="next-steps"></a>後續步驟

> [!div class="nextstepaction"]
> [.NET 核心教程](tutorials/index.md)

> [!div class="nextstepaction"]
> [在瀏覽器中試用 .NET 核心](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
