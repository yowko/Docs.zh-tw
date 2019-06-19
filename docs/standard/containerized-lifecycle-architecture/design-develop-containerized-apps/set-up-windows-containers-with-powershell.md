---
title: 在 DockerFile 中使用 Windows PowerShell 命令來設定 Windows 容器 (以 Docker 標準為基礎)
description: 了解如何在 Windows 容器中使用 Docker 時利用 PowerShell
ms.date: 02/15/2019
ms.openlocfilehash: e91d278aef1365a111e8d67ff04092dfc6a44185
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "65641590"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>在 DockerFile 中使用 Windows PowerShell 命令來設定 Windows 容器 (以 Docker 標準為基礎)

透過 [Windows 容器](/virtualization/windowscontainers/about/index)，您可以將現有的 Windows 應用程式轉換成 Docker 映像，並使用相同工具將它們部署為 Docker 生態系統的其餘部分。

若要使用 Windows 容器，您只需要在 Dockerfile 中撰寫 Windows PowerShell 命令，如下列範例所示：

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

在此案例中，我們會使用 Windows PowerShell 來安裝 Windows Server Core 基本映像以及 IIS。

使用類似的方式，您也可以使用 Windows PowerShell 命令來安裝其他元件，例如傳統的 ASP.NET 4.x 和 .NET 4.6 或任何其他 Windows 軟體，如下所示：

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[上一頁](visual-studio-tools-for-docker.md)
>[下一頁](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
