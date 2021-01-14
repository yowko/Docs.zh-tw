---
title: 針對 .NET 容器要設為目標的作業系統
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對 .NET 容器要設為目標的作業系統
ms.date: 01/13/2021
ms.openlocfilehash: 1b914d9afca9ade37f13e639f73001b91f338d26
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98187975"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="25680-103">針對 .NET 容器要設為目標的作業系統</span><span class="sxs-lookup"><span data-stu-id="25680-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="25680-104">由於 Docker 支援的作業系統多樣性以及 .NET Framework 與 .NET 5 之間的差異，您應該根據您所使用的架構，將目標設為特定的 OS 和特定版本。</span><span class="sxs-lookup"><span data-stu-id="25680-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET 5, you should target a specific OS and specific versions depending on the framework you are using.</span></span>

<span data-ttu-id="25680-105">針對 Windows，您可以使用 Windows Server Core 或 Windows Nano Server。</span><span class="sxs-lookup"><span data-stu-id="25680-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="25680-106">這些 Windows 版本在 Windows Server Core (的 IIS 與自我裝載的 web 伺服器（例如 Nano) Server 中的 Kestrel）（例如，.NET Framework 或 .NET 5 可能需要的）之間提供不同的特性。</span><span class="sxs-lookup"><span data-stu-id="25680-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET 5, respectively.</span></span>

<span data-ttu-id="25680-107">針對 Linux，有多個發佈可供使用，且受到正式 .NET Docker 映像的支援 (例如 Debian)。</span><span class="sxs-lookup"><span data-stu-id="25680-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="25680-108">在圖3-1 中，您可以根據所使用的 .NET framework，查看可能的作業系統版本。</span><span class="sxs-lookup"><span data-stu-id="25680-108">In Figure 3-1, you can see the possible OS version depending on the .NET framework used.</span></span>

![顯示哪些作業系統與 .NET 容器搭配使用的圖表。](./media/net-container-os-targets/targeting-operating-systems.png)

<span data-ttu-id="25680-110">**圖3-1。**</span><span class="sxs-lookup"><span data-stu-id="25680-110">**Figure 3-1.**</span></span> <span data-ttu-id="25680-111">根據 .NET Framework 版本決定要設為目標的作業系統</span><span class="sxs-lookup"><span data-stu-id="25680-111">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="25680-112">當您部署舊版 .NET Framework 應用程式時，您必須以 Windows Server Core 為目標，與繼承應用程式和 IIS 相容，但它有較大的影像。</span><span class="sxs-lookup"><span data-stu-id="25680-112">When deploying legacy .NET Framework applications you have to target Windows Server Core, compatible with legacy apps and IIS, but it has a larger image.</span></span> <span data-ttu-id="25680-113">部署 .NET 5 應用程式時，您可以將目標設為雲端優化的 Windows Nano Server，使用 Kestrel 且較小且更快速地啟動。</span><span class="sxs-lookup"><span data-stu-id="25680-113">When deploying .NET 5 applications, you can target Windows Nano Server, which is cloud optimized, uses Kestrel and is smaller and starts faster.</span></span> <span data-ttu-id="25680-114">您也可以以 Linux 為目標，支援 Debian、Alpine 和其他專案。</span><span class="sxs-lookup"><span data-stu-id="25680-114">You can also target Linux, supporting Debian, Alpine, and others.</span></span> <span data-ttu-id="25680-115">也會使用 Kestrel、較小且更快速地啟動。</span><span class="sxs-lookup"><span data-stu-id="25680-115">Also uses Kestrel, is smaller, and starts faster.</span></span>

<span data-ttu-id="25680-116">若您想要使用不同的 Linux 發佈或 Microsoft 未支援的版本，您也可以建立您自己的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="25680-116">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="25680-117">例如，您可以建立讓 ASP.NET Core 在傳統式 .NET Framework 及 Windows Server Core 上執行的映像 (並非 Docker 的常見案例)。</span><span class="sxs-lookup"><span data-stu-id="25680-117">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="25680-118">當您使用 Windows Server Core 映射時，可能會發現某些 Dll 遺失，相較于完整的 Windows 映像。</span><span class="sxs-lookup"><span data-stu-id="25680-118">When using Windows Server Core images, you might find that some DLLs are missing, when compared to full Windows images.</span></span> <span data-ttu-id="25680-119">您可以藉由建立自訂 Server Core 映射，在映射建立時新增遺失的檔案，如此 [GitHub 批註](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448)中所述，您可以解決此問題。</span><span class="sxs-lookup"><span data-stu-id="25680-119">You might be able to solve this problem by creating a custom Server Core image, adding the missing files at image build time, as mentioned in this [GitHub comment](https://github.com/microsoft/dotnet-framework-docker/issues/299#issuecomment-511537448).</span></span>

<span data-ttu-id="25680-120">當您將映像名稱新增至您的 Dockerfile 檔案時，您可以根據使用的標籤選取作業系統及版本，如下列範例中所示：</span><span class="sxs-lookup"><span data-stu-id="25680-120">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

| <span data-ttu-id="25680-121">映像</span><span class="sxs-lookup"><span data-stu-id="25680-121">Image</span></span> | <span data-ttu-id="25680-122">註解</span><span class="sxs-lookup"><span data-stu-id="25680-122">Comments</span></span> |
|-------|----------|
| <span data-ttu-id="25680-123">mcr.microsoft.com/dotnet/runtime:5.0</span><span class="sxs-lookup"><span data-stu-id="25680-123">mcr.microsoft.com/dotnet/runtime:5.0</span></span> | <span data-ttu-id="25680-124">.NET 5 多重架構：支援 Linux 和 Windows Nano Server，視 Docker 主機而定。</span><span class="sxs-lookup"><span data-stu-id="25680-124">.NET 5 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span> |
| <span data-ttu-id="25680-125">mcr.microsoft.com/dotnet/aspnet:5.0</span><span class="sxs-lookup"><span data-stu-id="25680-125">mcr.microsoft.com/dotnet/aspnet:5.0</span></span> | <span data-ttu-id="25680-126">ASP.NET Core 5.0 多架構：支援 Linux 和 Windows Nano Server，視 Docker 主機而定。</span><span class="sxs-lookup"><span data-stu-id="25680-126">ASP.NET Core 5.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span> <br/> <span data-ttu-id="25680-127">aspnetcore 映像有幾項針對 ASP.NET Core 所做的最佳化。</span><span class="sxs-lookup"><span data-stu-id="25680-127">The aspnetcore image has a few optimizations for ASP.NET Core.</span></span> |
| <span data-ttu-id="25680-128">mcr.microsoft.com/dotnet/aspnet:5.0-buster-slim</span><span class="sxs-lookup"><span data-stu-id="25680-128">mcr.microsoft.com/dotnet/aspnet:5.0-buster-slim</span></span> | <span data-ttu-id="25680-129">.NET 5 執行時間-僅適用于 Linux Debian 發行版本</span><span class="sxs-lookup"><span data-stu-id="25680-129">.NET 5 runtime-only on Linux Debian distro</span></span> |
| <span data-ttu-id="25680-130">mcr.microsoft.com/dotnet/aspnet:5.0-nanoserver-1809</span><span class="sxs-lookup"><span data-stu-id="25680-130">mcr.microsoft.com/dotnet/aspnet:5.0-nanoserver-1809</span></span> | <span data-ttu-id="25680-131">僅限 .NET 5 執行時間-僅限 Windows Nano Server (Windows Server 1809 版) </span><span class="sxs-lookup"><span data-stu-id="25680-131">.NET 5 runtime-only on Windows Nano Server (Windows Server version 1809)</span></span> |

## <a name="additional-resources"></a><span data-ttu-id="25680-132">其他資源</span><span class="sxs-lookup"><span data-stu-id="25680-132">Additional resources</span></span>

- <span data-ttu-id="25680-133">**BitmapDecoder 失敗，因為 GitHub 問題缺少 WindowsCodecsExt.dll ()**</span><span class="sxs-lookup"><span data-stu-id="25680-133">**BitmapDecoder fails due to missing WindowsCodecsExt.dll (GitHub issue)**</span></span>  
  <https://github.com/microsoft/dotnet-framework-docker/issues/299>

> [!div class="step-by-step"]
> <span data-ttu-id="25680-134">[上一個](container-framework-choice-factors.md) 
> [下一步](official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="25680-134">[Previous](container-framework-choice-factors.md)
[Next](official-net-docker-images.md)</span></span>
