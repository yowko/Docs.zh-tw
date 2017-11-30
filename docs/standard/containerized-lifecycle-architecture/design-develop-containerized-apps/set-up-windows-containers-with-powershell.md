---
title: "在 DockerFile 中使用 Windows PowerShell 命令來設定 Windows 容器 (Docker 標準基礎)"
description: "Microsoft 平台和工具與 Docker 容器化應用程式生命週期"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: f7e92b0f1c749e2c00e3afc4ffcfc2fc88d7628f
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2017
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="a8405-104">在 DockerFile 中使用 Windows PowerShell 命令來設定 Windows 容器 (Docker 標準基礎)</span><span class="sxs-lookup"><span data-stu-id="a8405-104">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="a8405-105">與[Windows 容器](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview)，您可以將轉換的 Docker 映像您現有的 Windows 應用程式，並將其部署在 Docker 生態系統的其他部分相同的工具。</span><span class="sxs-lookup"><span data-stu-id="a8405-105">With [Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="a8405-106">若要使用 Windows 容器，您只需要撰寫 Windows PowerShell 命令在 DockerFile 中，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="a8405-106">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="a8405-107">在此情況下，我們會使用 Windows PowerShell 來安裝 Windows Server Core 基本映像，以及 IIS。</span><span class="sxs-lookup"><span data-stu-id="a8405-107">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="a8405-108">在類似的方式，您也可以使用 Windows PowerShell 命令來設定其他元件，類似傳統的 ASP.NET 4.x 和.NET 4.6 或任何其他 Windows 軟體，如下所示：</span><span class="sxs-lookup"><span data-stu-id="a8405-108">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET 4.6 or any other Windows software, as shown here:</span></span>

```
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
<span data-ttu-id="a8405-109">[上一個](視覺層 studio-工具-如-docker.md) [下一步] (.../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="a8405-109">[Previous] (visual-studio-tools-for-docker.md) [Next] (../docker-devops-workflow/index.md)</span></span>
