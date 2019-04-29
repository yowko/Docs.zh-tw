---
title: 在 DockerFile 中使用 Windows PowerShell 命令，來設定 Windows 容器 (Docker 標準為基礎)
description: 了解如何使用 PowerShell，使用 Windows 容器中的 Docker 時
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: d9c0bc28f62d44eb7471b99c63055ef43da12a69
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644641"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>在 DockerFile 中使用 Windows PowerShell 命令，來設定 Windows 容器 (Docker 標準為基礎)

具有[Windows 容器](/virtualization/windowscontainers/about/index)，您可以轉換現有的 Windows 應用程式到 Docker 映像，並將其部署為 Docker 生態系統的其餘部分相同的工具。

若要使用 Windows 容器，您只需要撰寫 Windows PowerShell 命令，在 DockerFile 中，如下列範例所示：

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

在此情況下，我們使用 Windows PowerShell 來安裝 Windows Server Core 基本映像，以及 IIS。

在類似的方式，您也可以使用 Windows PowerShell 命令來設定額外的元件，例如傳統 ASP.NET 4.x 和.NET 4.6 或任何其他 Windows 軟體，如下所示：

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[上一頁](visual-studio-tools-for-docker.md)
>[下一頁](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
