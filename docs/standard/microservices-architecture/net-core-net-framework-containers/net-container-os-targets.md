---
title: "目標.NET 容器具有何種作業系統"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |目標.NET 容器具有何種作業系統"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 828ccb5e7a76f9419e80793b6cb3a6ba24f358cf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="what-os-to-target-with-net-containers"></a>目標.NET 容器具有何種作業系統

提供多樣化的 Docker 和.NET Framework 和.NET Core 之間的差異所支援的作業系統，您應將目標設在特定的作業系統，根據您使用的架構特定的版本。 

對於 Windows，您可以使用 Windows Server Core 或 Windows Nano Server。 這些 Windows 版本提供不同的特性 (中 Windows Server Core 與 Nano server Kestrel 自我裝載的 web 伺服器 IIS) 可能會分別需要的.NET Framework 或.NET 核心。 

適用於 Linux，多個散發版本會提供及支援 （例如，Debian) 的正式.NET Docker 映像。

圖 3-1，您可以查看根據.NET framework 使用可能的 OS 版本。

![](./media/image1.png)

**圖 3-1。** 若要根據.NET framework 版本為目標的作業系統

您也可以建立自己的 Docker 映像中的情況下您要使用不同的 Linux distro 或您想映像使用並非由 Microsoft 提供的版本。 例如，您可能會與傳統.NET Framework 和 Windows Server Core 是 Docker 不常見的案例上執行的 ASP.NET Core 建立映像。

當您將映像名稱加入您 Dockerfile 的檔案時，您可以選取的作業系統和版本根據標記使用，如下列範例所示：

-   microsoft /**dotnet:2.0.0-執行階段-潔**

        .NET Core 2.0 runtime-only on Linux

-   microsoft /**dotnet:2.0.0-執行階段-nanoserver-1709年** 

        .NET Core 2.0 runtime-only on Windows Nano Server (Windows Server 2016 Fall Creators Update version 1709)

-   microsoft /**aspnetcore:2.0**
    
        .NET Core 2.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 





>[!div class="step-by-step"]
[上一個](容器-架構-選擇-factors.md) [下一步] (官方-網路-docker-images.md)
