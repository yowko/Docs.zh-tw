---
title: 針對 .NET 容器要設為目標的作業系統
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對 .NET 容器要設為目標的作業系統
ms.date: 01/30/2020
ms.openlocfilehash: a09e3981ece478a9795c0f27acc98d604864cdd5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501855"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="82c6c-103">針對 .NET 容器要設為目標的作業系統</span><span class="sxs-lookup"><span data-stu-id="82c6c-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="82c6c-104">考量到 Docker 支援的作業系統多樣性及 .NET Framework 和 .NET Core 之間的不同，建議您根據您使用的架構來瞄準特定 OS 和特定的版本。</span><span class="sxs-lookup"><span data-stu-id="82c6c-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span>

<span data-ttu-id="82c6c-105">針對 Windows，您可以使用 Windows Server Core 或 Windows Nano Server。</span><span class="sxs-lookup"><span data-stu-id="82c6c-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="82c6c-106">這些 Windows 版本提供了 .NET Framework 或 .NET Core 各自所需的不同特性 (Windows Server 中的 IIS 與 Nano Server 中的自我裝載網頁伺服器，例如 Kestrel)。</span><span class="sxs-lookup"><span data-stu-id="82c6c-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span>

<span data-ttu-id="82c6c-107">針對 Linux，有多個發佈可供使用，且受到正式 .NET Docker 映像的支援 (例如 Debian)。</span><span class="sxs-lookup"><span data-stu-id="82c6c-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="82c6c-108">在圖 3-1 中，您可以看到根據使用的 .NET Framework，可能使用的 OS 版本。</span><span class="sxs-lookup"><span data-stu-id="82c6c-108">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![顯示要與哪個 .NET 容器使用哪些作業系統的圖表。](./media/net-container-os-targets/targeting-operating-systems.png)

<span data-ttu-id="82c6c-110">**圖 3-1。**</span><span class="sxs-lookup"><span data-stu-id="82c6c-110">**Figure 3-1.**</span></span> <span data-ttu-id="82c6c-111">根據 .NET Framework 版本決定要設為目標的作業系統</span><span class="sxs-lookup"><span data-stu-id="82c6c-111">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="82c6c-112">部署舊版 .NET 框架應用程式時，必須針對 Windows 伺服器核心，與舊應用和 IIS 相容，但它具有更大的映射。</span><span class="sxs-lookup"><span data-stu-id="82c6c-112">When deploying legacy .NET Framework applications you have to target Windows Server Core, compatible with legacy apps and IIS, but it has a larger image.</span></span> <span data-ttu-id="82c6c-113">在部署 .NET Core 應用程式時，您能夠以 Windows Nano Server 為目標，因為它已經過雲端最佳化、使用 Kestrel，且較為輕巧而啟動速度較快。</span><span class="sxs-lookup"><span data-stu-id="82c6c-113">When deploying .NET Core applications, you can target Windows Nano Server, which is cloud optimized, uses Kestrel and is smaller and starts faster.</span></span> <span data-ttu-id="82c6c-114">此外，支援 Debian、Alpine 和其他項目的 Linux 也可作為目標。</span><span class="sxs-lookup"><span data-stu-id="82c6c-114">You can also target Linux, supporting Debian, Alpine and others.</span></span> <span data-ttu-id="82c6c-115">也使用Kestrel，更小，啟動更快。</span><span class="sxs-lookup"><span data-stu-id="82c6c-115">Also uses Kestrel, is smaller, and starts faster.</span></span>

<span data-ttu-id="82c6c-116">若您想要使用不同的 Linux 發佈或 Microsoft 未支援的版本，您也可以建立您自己的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="82c6c-116">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="82c6c-117">例如，您可以建立讓 ASP.NET Core 在傳統式 .NET Framework 及 Windows Server Core 上執行的映像 (並非 Docker 的常見案例)。</span><span class="sxs-lookup"><span data-stu-id="82c6c-117">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="82c6c-118">使用 Windows 伺服器核心映射時，您可能會發現與完整的 Windows 映像相比，某些 DLL 缺失。</span><span class="sxs-lookup"><span data-stu-id="82c6c-118">When using Windows Server Core images, you might find that some DLLs are missing, when compared to full Windows images.</span></span> <span data-ttu-id="82c6c-119">您可能可以通過創建自訂伺服器核心映射、在映射生成時添加缺少的檔來解決此問題，如此[GitHub 注釋](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448)中所述。</span><span class="sxs-lookup"><span data-stu-id="82c6c-119">You might be able to solve this problem by creating a custom Server Core image, adding the missing files at image build time, as mentioned in this [GitHub comment](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448).</span></span>

<span data-ttu-id="82c6c-120">當您將映像名稱新增至您的 Dockerfile 檔案時，您可以根據使用的標籤選取作業系統及版本，如下列範例中所示：</span><span class="sxs-lookup"><span data-stu-id="82c6c-120">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

| <span data-ttu-id="82c6c-121">映像</span><span class="sxs-lookup"><span data-stu-id="82c6c-121">Image</span></span> | <span data-ttu-id="82c6c-122">註解</span><span class="sxs-lookup"><span data-stu-id="82c6c-122">Comments</span></span> |
|-------|----------|
| <span data-ttu-id="82c6c-123">mcr.microsoft.com/dotnet/core/runtime:3.1</span><span class="sxs-lookup"><span data-stu-id="82c6c-123">mcr.microsoft.com/dotnet/core/runtime:3.1</span></span> | <span data-ttu-id="82c6c-124">.NET Core 3.1 多體系結構：支援 Linux 和 Windows Nano 伺服器，具體取決於 Docker 主機。</span><span class="sxs-lookup"><span data-stu-id="82c6c-124">.NET Core 3.1 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span> |
| <span data-ttu-id="82c6c-125">mcr.microsoft.com/dotnet/core/aspnet:3.1</span><span class="sxs-lookup"><span data-stu-id="82c6c-125">mcr.microsoft.com/dotnet/core/aspnet:3.1</span></span> | <span data-ttu-id="82c6c-126">ASP.NET核心 3.1 多體系結構：支援 Linux 和 Windows Nano 伺服器，具體取決於 Docker 主機。</span><span class="sxs-lookup"><span data-stu-id="82c6c-126">ASP.NET Core 3.1 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span> <br/> <span data-ttu-id="82c6c-127">aspnetcore 映像有幾項針對 ASP.NET Core 所做的最佳化。</span><span class="sxs-lookup"><span data-stu-id="82c6c-127">The aspnetcore image has a few optimizations for ASP.NET Core.</span></span> |
| <span data-ttu-id="82c6c-128">mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim</span><span class="sxs-lookup"><span data-stu-id="82c6c-128">mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim</span></span> | <span data-ttu-id="82c6c-129">.NET 核心 3.1 僅在 Linux Debian 發行版本上運行時</span><span class="sxs-lookup"><span data-stu-id="82c6c-129">.NET Core 3.1 runtime-only on Linux Debian distro</span></span> |
| <span data-ttu-id="82c6c-130">mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1809</span><span class="sxs-lookup"><span data-stu-id="82c6c-130">mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1809</span></span> | <span data-ttu-id="82c6c-131">.NET 核心 3.1 僅在 Windows Nano 伺服器上運行時（Windows 伺服器版本 1809）</span><span class="sxs-lookup"><span data-stu-id="82c6c-131">.NET Core 3.1 runtime-only on Windows Nano Server (Windows Server version 1809)</span></span> |

## <a name="additional-resources"></a><span data-ttu-id="82c6c-132">其他資源</span><span class="sxs-lookup"><span data-stu-id="82c6c-132">Additional resources</span></span>

- <span data-ttu-id="82c6c-133">**由於缺少 WindowsCodecsExt.dll（GitHub 問題），位映射解碼器失敗**</span><span class="sxs-lookup"><span data-stu-id="82c6c-133">**BitmapDecoder fails due to missing WindowsCodecsExt.dll (GitHub issue)**</span></span>  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> <span data-ttu-id="82c6c-134">[上一個](container-framework-choice-factors.md)
> [下一個](official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="82c6c-134">[Previous](container-framework-choice-factors.md)
[Next](official-net-docker-images.md)</span></span>
