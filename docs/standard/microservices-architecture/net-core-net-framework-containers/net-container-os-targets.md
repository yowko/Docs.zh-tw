---
title: 針對 .NET 容器要設為目標的作業系統
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 針對 .NET 容器要設為目標的作業系統
ms.date: 01/07/2019
ms.openlocfilehash: 6f160aeba5257722490788271e6f89359342cc0d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639087"
---
# <a name="what-os-to-target-with-net-containers"></a><span data-ttu-id="e25f9-103">針對 .NET 容器要設為目標的作業系統</span><span class="sxs-lookup"><span data-stu-id="e25f9-103">What OS to target with .NET containers</span></span>

<span data-ttu-id="e25f9-104">考量到 Docker 支援的作業系統多樣性及 .NET Framework 和 .NET Core 之間的不同，建議您根據您使用的架構來瞄準特定 OS 和特定的版本。</span><span class="sxs-lookup"><span data-stu-id="e25f9-104">Given the diversity of operating systems supported by Docker and the differences between .NET Framework and .NET Core, you should target a specific OS and specific versions depending on the framework you are using.</span></span>

<span data-ttu-id="e25f9-105">針對 Windows，您可以使用 Windows Server Core 或 Windows Nano Server。</span><span class="sxs-lookup"><span data-stu-id="e25f9-105">For Windows, you can use Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="e25f9-106">這些 Windows 版本提供了 .NET Framework 或 .NET Core 各自所需的不同特性 (Windows Server 中的 IIS 與 Nano Server 中的自我裝載網頁伺服器，例如 Kestrel)。</span><span class="sxs-lookup"><span data-stu-id="e25f9-106">These Windows versions provide different characteristics (IIS in Windows Server Core versus a self-hosted web server like Kestrel in Nano Server) that might be needed by .NET Framework or .NET Core, respectively.</span></span>

<span data-ttu-id="e25f9-107">針對 Linux，有多個發佈可供使用，且受到正式 .NET Docker 映像的支援 (例如 Debian)。</span><span class="sxs-lookup"><span data-stu-id="e25f9-107">For Linux, multiple distros are available and supported in official .NET Docker images (like Debian).</span></span>

<span data-ttu-id="e25f9-108">在圖 3-1 中，您可以看到根據使用的 .NET Framework，可能使用的 OS 版本。</span><span class="sxs-lookup"><span data-stu-id="e25f9-108">In Figure 3-1 you can see the possible OS version depending on the .NET framework used.</span></span>

![在部署舊版 .NET Framework 應用程式時，您必須以相容於舊版應用程式和 IIS、且具有較大映像的 Windows Server Core 為目標。](./media/image1.png)

<span data-ttu-id="e25f9-113">**圖 3-1**</span><span class="sxs-lookup"><span data-stu-id="e25f9-113">**Figure 3-1.**</span></span> <span data-ttu-id="e25f9-114">根據 .NET Framework 版本決定要設為目標的作業系統</span><span class="sxs-lookup"><span data-stu-id="e25f9-114">Operating systems to target depending on versions of the .NET framework</span></span>

<span data-ttu-id="e25f9-115">若您想要使用不同的 Linux 發佈或 Microsoft 未支援的版本，您也可以建立您自己的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="e25f9-115">You can also create your own Docker image in cases where you want to use a different Linux distro or where you want an image with versions not provided by Microsoft.</span></span> <span data-ttu-id="e25f9-116">例如，您可以建立讓 ASP.NET Core 在傳統式 .NET Framework 及 Windows Server Core 上執行的映像 (並非 Docker 的常見案例)。</span><span class="sxs-lookup"><span data-stu-id="e25f9-116">For example, you might create an image with ASP.NET Core running on the traditional .NET Framework and Windows Server Core, which is a not-so-common scenario for Docker.</span></span>

<span data-ttu-id="e25f9-117">當您將映像名稱新增至您的 Dockerfile 檔案時，您可以根據使用的標籤選取作業系統及版本，如下列範例中所示：</span><span class="sxs-lookup"><span data-stu-id="e25f9-117">When you add the image name to your Dockerfile file, you can select the operating system and version depending on the tag you use, as in the following examples:</span></span>

<table>
<thead>
<tr class="header">
<th><span data-ttu-id="e25f9-118">Image</span><span class="sxs-lookup"><span data-stu-id="e25f9-118">Image</span></span></th>
<th><span data-ttu-id="e25f9-119">註解</span><span class="sxs-lookup"><span data-stu-id="e25f9-119">Comments</span></span></th>
</tr>
</thead>
<tbody>
<tr>
<td><span data-ttu-id="e25f9-120">mcr.microsoft.com/dotnet/core/runtime:2.2</span><span class="sxs-lookup"><span data-stu-id="e25f9-120">mcr.microsoft.com/dotnet/core/runtime:2.2</span></span></td>
<td><span data-ttu-id="e25f9-121">.NET Core 2.2 多重架構：支援 Linux 和 Windows Nano Server，視 Docker 主機而定。</span><span class="sxs-lookup"><span data-stu-id="e25f9-121">.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e25f9-122">mcr.microsoft.com/dotnet/core/aspnet:2.2</span><span class="sxs-lookup"><span data-stu-id="e25f9-122">mcr.microsoft.com/dotnet/core/aspnet:2.2</span></span></td>
<td><p><span data-ttu-id="e25f9-123">ASP.NET Core 2.2 多重架構：支援 Linux 和 Windows Nano Server，視 Docker 主機而定。</span><span class="sxs-lookup"><span data-stu-id="e25f9-123">ASP.NET Core 2.2 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.</span></span></p>
<p><span data-ttu-id="e25f9-124">aspnetcore 映像有幾項針對 ASP.NET Core 所做的最佳化。</span><span class="sxs-lookup"><span data-stu-id="e25f9-124">The aspnetcore image has a few optimizations for ASP.NET Core.</span></span></p></td>
</tr>
<tr class="even">
<td><span data-ttu-id="e25f9-125">mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</span><span class="sxs-lookup"><span data-stu-id="e25f9-125">mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine</span></span></td>
<td><span data-ttu-id="e25f9-126">.NET Core 2.2 執行階段 - 僅限於 Linux Alpine 發行版本上</span><span class="sxs-lookup"><span data-stu-id="e25f9-126">.NET Core 2.2 runtime-only on Linux Alpine distro</span></span></td>
</tr>
<tr class="odd">
<td><span data-ttu-id="e25f9-127">mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</span><span class="sxs-lookup"><span data-stu-id="e25f9-127">mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803</span></span></td>
<td><span data-ttu-id="e25f9-128">.NET Core 2.2 執行階段 - 僅限於 Windows Nano Server (Windows Server 1803 版) 上</span><span class="sxs-lookup"><span data-stu-id="e25f9-128">.NET Core 2.2 runtime-only on Windows Nano Server (Windows Server version 1803)</span></span></td>
</tr>
</tbody>
</table>

> [!div class="step-by-step"]
> <span data-ttu-id="e25f9-129">[上一頁](container-framework-choice-factors.md)
> [下一頁](official-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="e25f9-129">[Previous](container-framework-choice-factors.md)
[Next](official-net-docker-images.md)</span></span>
