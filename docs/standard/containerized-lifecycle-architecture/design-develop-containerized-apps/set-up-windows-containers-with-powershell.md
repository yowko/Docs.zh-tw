---
title: 在 DockerFile 中使用 Windows PowerShell 命令，來設定 Windows 容器 (Docker 標準為基礎)
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: 5e85beea0efbee6a2b6594e3a49d705505a36e1c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149389"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="f00c6-103">在 DockerFile 中使用 Windows PowerShell 命令，來設定 Windows 容器 (Docker 標準為基礎)</span><span class="sxs-lookup"><span data-stu-id="f00c6-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="f00c6-104">具有[Windows 容器](/virtualization/windowscontainers/about/index)，您可以轉換現有的 Windows 應用程式到 Docker 映像，並將其部署為 Docker 生態系統的其餘部分相同的工具。</span><span class="sxs-lookup"><span data-stu-id="f00c6-104">With [Windows Containers](/virtualization/windowscontainers/about/index), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="f00c6-105">若要使用 Windows 容器，您只需要撰寫 Windows PowerShell 命令，在 DockerFile 中，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="f00c6-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="f00c6-106">在此情況下，我們使用 Windows PowerShell 來安裝 Windows Server Core 基本映像，以及 IIS。</span><span class="sxs-lookup"><span data-stu-id="f00c6-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="f00c6-107">在類似的方式，您也可以使用 Windows PowerShell 命令來設定額外的元件，例如傳統 ASP.NET 4.x 和.NET 4.6 或任何其他 Windows 軟體，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f00c6-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
><span data-ttu-id="f00c6-108">[上一頁](visual-studio-tools-for-docker.md)
>[下一頁](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="f00c6-108">[Previous](visual-studio-tools-for-docker.md)
[Next](../docker-devops-workflow/index.md)</span></span>
