---
title: .NET Core 指南
description: .NET Core 是 .NET 的模組化、高效能實作，可用於建立 Windows、Linux 和 Mac 應用程式。 了解 .NET Core 以開始使用。
author: richlander
ms.author: mairaw
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: 448edabf624f04311695e8b8c224f653b9939966
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199457"
---
# <a name="net-core-guide"></a>.NET Core 指南

[.NET Core](about.md) 是[開放原始碼](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT)的一般用途開發平台，由 Microsoft 與 [GitHub](https://github.com/dotnet/core) 上的 .NET 社群共同維護。 它可以跨平台支援 Windows、macOS 與 Linux，並可用於建置裝置、雲端與 IoT 應用程式。

請參閱[關於 .NET Core](about.md)以深入了解 .NET Core，包括其特性、支援的語言與架構，亦即主要 API。

查看 [.NET Core 教學課程](tutorials/index.md) 以了解如何建立簡單的 .NET Core 應用程式。 只需要幾分鐘，您就可以啟動並執行您的第一個應用程式。 若要在您的瀏覽器中嘗試 .NET Core，請查看 [C# 中的數字](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)線上教學課程。

## <a name="download-net-core-21"></a>下載 .NET Core 2.1

下載 [.NET Core  2.1 SDK](https://www.microsoft.com/net/download) 以在您的 Windows、macOS 或 Linux 電腦上嘗試 .NET Core。 若偏好使用 Docker 容器，請瀏覽 [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/)。

若您要尋找另一個 .NET Core 版本，所有 .NET Core 版本都可以在 [.NET Core 下載 ](https://www.microsoft.com/net/download/archives)找到。

## <a name="net-core-21"></a>.NET Core 2.1

最新版本是 [.NET Core 2.1](whats-new/dotnet-core-2-1.md)。 新功能包括：全域工具、高效能 API (例如 <xref:System.Span%601?displayProperty=nameWithType>)、分層式 JIT 編譯、[建置](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/)與[執行階段效能改進](https://blogs.msdn.microsoft.com/dotnet/2018/04/18/performance-improvements-in-net-core-2-1/)，以及對 Alpine 與 ARM32 的支援。

## <a name="create-your-first-application"></a>建立您的第一個應用程式

安裝 .NET Core SDK 之後，請開啟命令提示字元。 鍵入下列 `dotnet` 命令以建立並執行 C# 應用程式。

```console
dotnet new console
dotnet run
```

您應該會看到下列輸出：

```console
Hello World!
```

## <a name="support"></a>支援

[Microsoft 在 Windows、macOS 與 Linux上](https://www.microsoft.com/net/support/policy) 都支援 .NET Core。 每年都為它推出安全性與品質更新數次，通常是一個月一次。

.NET Core 二進位發行版本是在 Azure 中由 Microsoft 維護的服務上建置及測試，而且享有與任何 Microsoft 產品一樣的支援。

[Red Hat 在 Red Hat Enterprise Linux (RHEL) 上支援 .NET Core](http://redhatloves.net/)。 Red Hat 從原始碼建置 .NET Core 並在 [Red Hat 軟體集合](https://developers.redhat.com/products/softwarecollections/overview/)中提供。 Red Hat 與 Microsoft 共同作業以確保 .NET Core 可在 RHEL 上正確運作。
