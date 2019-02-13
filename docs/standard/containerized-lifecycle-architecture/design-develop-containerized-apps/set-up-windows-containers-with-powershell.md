---
title: 在 DockerFile 中使用 Windows PowerShell 命令，來設定 Windows 容器 (Docker 標準為基礎)
description: 了解如何使用 PowerShell，使用 Windows 容器中的 Docker 時
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: df9e98e3f963b6492e1008455251b61a8cb6e771
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219967"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>在 DockerFile 中使用 Windows PowerShell 命令，來設定 Windows 容器 (Docker 標準為基礎)

具有[Windows 容器](/virtualization/windowscontainers/about/index)，您可以轉換現有的 Windows 應用程式到 Docker 映像，並將其部署為 Docker 生態系統的其餘部分相同的工具。

若要使用 Windows 容器，您只需要撰寫 Windows PowerShell 命令，在 DockerFile 中，如下列範例所示：

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

在此情況下，我們使用 Windows PowerShell 來安裝 Windows Server Core 基本映像，以及 IIS。

在類似的方式，您也可以使用 Windows PowerShell 命令來設定額外的元件，例如傳統 ASP.NET 4.x 和.NET 4.6 或任何其他 Windows 軟體，如下所示：

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[上一頁](visual-studio-tools-for-docker.md)
>[下一頁](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
