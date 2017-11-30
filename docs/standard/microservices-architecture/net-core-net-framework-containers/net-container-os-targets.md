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
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="fe92b-104">目標.NET 容器具有何種作業系統</span><span class="sxs-lookup"><span data-stu-id="fe92b-104">What OS to target with .NET containers</span></span>

<span data-ttu-id="fe92b-105">提供多樣化的 Docker 和.NET Framework 和.NET Core 之間的差異所支援的作業系統，您應將目標設在特定的作業系統，根據您使用的架構特定的版本。</span><span class="sxs-lookup"><span data-stu-id="fe92b-105">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span> 

<span data-ttu-id="fe92b-106">對於 Windows，您可以使用 Windows Server Core 或 Windows Nano Server。</span><span class="sxs-lookup"><span data-stu-id="fe92b-106">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="fe92b-107">這些 Windows 版本提供不同的特性 (中 Windows Server Core 與 Nano server Kestrel 自我裝載的 web 伺服器 IIS) 可能會分別需要的.NET Framework 或.NET 核心。</span><span class="sxs-lookup"><span data-stu-id="fe92b-107">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span> 

<span data-ttu-id="fe92b-108">適用於 Linux，多個散發版本會提供及支援 （例如，Debian) 的正式.NET Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="fe92b-108">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="fe92b-109">圖 3-1，您可以查看根據.NET framework 使用可能的 OS 版本。</span><span class="sxs-lookup"><span data-stu-id="fe92b-109">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![](./media/image1.png)

<span data-ttu-id="fe92b-110">**圖 3-1。**</span><span class="sxs-lookup"><span data-stu-id="fe92b-110">**Figure 3-1.**</span></span> <span data-ttu-id="fe92b-111">若要根據.NET framework 版本為目標的作業系統</span><span class="sxs-lookup"><span data-stu-id="fe92b-111">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="fe92b-112">您也可以建立自己的 Docker 映像中的情況下您要使用不同的 Linux distro 或您想映像使用並非由 Microsoft 提供的版本。</span><span class="sxs-lookup"><span data-stu-id="fe92b-112">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="fe92b-113">例如，您可能會與傳統.NET Framework 和 Windows Server Core 是 Docker 不常見的案例上執行的 ASP.NET Core 建立映像。</span><span class="sxs-lookup"><span data-stu-id="fe92b-113">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="fe92b-114">當您將映像名稱加入您 Dockerfile 的檔案時，您可以選取的作業系統和版本根據標記使用，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="fe92b-114">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

-   <span data-ttu-id="fe92b-115">microsoft /**dotnet:2.0.0-執行階段-潔**</span><span class="sxs-lookup"><span data-stu-id="fe92b-115">microsoft/**dotnet:2.0.0-runtime-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux

-   <span data-ttu-id="fe92b-116">microsoft /**dotnet:2.0.0-執行階段-nanoserver-1709年**</span><span class="sxs-lookup"><span data-stu-id="fe92b-116">microsoft/**dotnet:2.0.0-runtime-nanoserver-1709**</span></span> 

        .NET Core 2.0 runtime-only on Windows Nano Server (Windows Server 2016 Fall Creators Update version 1709)

-   <span data-ttu-id="fe92b-117">microsoft /**aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="fe92b-117">microsoft/**aspnetcore:2.0**</span></span>
    
        .NET Core 2.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 





>[!div class="step-by-step"]
<span data-ttu-id="fe92b-118">[上一個](容器-架構-選擇-factors.md) [下一步] (官方-網路-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="fe92b-118">[Previous] (container-framework-choice-factors.md) [Next] (official-net-docker-images.md)</span></span>
