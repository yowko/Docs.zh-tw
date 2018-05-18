---
title: 針對 .NET 容器要設為目標的作業系統
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對 .NET 容器要設為目標的作業系統
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 0b06f64027a736ead148ea5511cf20e900b8b39a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="what-os-to-target-with-net-containers"></a>針對 .NET 容器要設為目標的作業系統

考量到 Docker 支援的作業系統多樣性及 .NET Framework 和 .NET Core 之間的不同，建議您根據您使用的架構來瞄準特定 OS 和特定的版本。 

針對 Windows，您可以使用 Windows Server Core 或 Windows Nano Server。 這些 Windows 版本提供了 .NET Framework 或 .NET Core 各自所需的不同特性 (Windows Server 中的 IIS 與 Nano Server 中的自我裝載網頁伺服器，例如 Kestrel)。 

針對 Linux，有多個發佈可供使用，且受到正式 .NET Docker 映像的支援 (例如 Debian)。

在圖 3-1 中，您可以看到根據使用的 .NET Framework，可能使用的 OS 版本。

![](./media/image1.png)

**圖 3-1** 根據 .NET Framework 版本決定要設為目標的作業系統

若您想要使用不同的 Linux 發佈或 Microsoft 未支援的版本，您也可以建立您自己的 Docker 映像。 例如，您可以建立讓 ASP.NET Core 在傳統式 .NET Framework 及 Windows Server Core 上執行的映像 (並非 Docker 的常見案例)。

當您將映像名稱新增至您的 Dockerfile 檔案時，您可以根據使用的標籤選取作業系統及版本，如下列範例中所示：

-   microsoft/**dotnet:2.0.0-runtime-jessie**

        .NET Core 2.0 runtime-only on Linux

-   microsoft/**dotnet:2.0.0-runtime-nanoserver-1709** 

        .NET Core 2.0 runtime-only on Windows Nano Server (Windows Server 2016 Fall Creators Update version 1709)

-   microsoft/**aspnetcore:2.0**
    
        .NET Core 2.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 





>[!div class="step-by-step"]
[上一頁] (container-framework-choice-factors.md) [下一頁] (official-net-docker-images.md)
