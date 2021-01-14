---
title: 以 Docker 為基礎之應用程式的開發流程
description: 取得開發以 Docker 為基礎之應用程式的選項高階總覽。 使用您選擇的 Windows、Visual Studio for Mac 或 Visual Studio Code 的 Visual Studio， (Windows、macOS 和 Linux) 的多平臺支援。
ms.date: 01/13/2021
ms.openlocfilehash: 3a4f4078e745c52e8eca46473668e3319917bfd2
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188292"
---
# <a name="development-process-for-docker-based-applications"></a><span data-ttu-id="f9b65-104">以 Docker 為基礎之應用程式的開發流程</span><span class="sxs-lookup"><span data-stu-id="f9b65-104">Development process for Docker-based applications</span></span>

<span data-ttu-id="f9b65-105">*以您喜歡的方式開發容器化 .NET 應用程式，整合式開發環境 (IDE) 著重于 Docker 的 Visual Studio 和 Visual Studio 工具，或是以 Docker CLI 和 Visual Studio Code 為焦點的 CLI/編輯器。*</span><span class="sxs-lookup"><span data-stu-id="f9b65-105">*Develop containerized .NET applications the way you like, either Integrated Development Environment (IDE) focused with Visual Studio and Visual Studio tools for Docker or CLI/Editor focused with Docker CLI and Visual Studio Code.*</span></span>

## <a name="development-environment-for-docker-apps"></a><span data-ttu-id="f9b65-106">Docker 應用程式的開發環境</span><span class="sxs-lookup"><span data-stu-id="f9b65-106">Development environment for Docker apps</span></span>

### <a name="development-tool-choices-ide-or-editor"></a><span data-ttu-id="f9b65-107">開發工具選擇：IDE 或編輯器</span><span class="sxs-lookup"><span data-stu-id="f9b65-107">Development tool choices: IDE or editor</span></span>

<span data-ttu-id="f9b65-108">不論您偏好使用完整且強大的 IDE，還是輕量型的敏捷式編輯器，Microsoft 都有相關工具可供您用來開發 Docker 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f9b65-108">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has tools that you can use for developing Docker applications.</span></span>

<span data-ttu-id="f9b65-109">**Visual Studio (適用於 Windows)。**</span><span class="sxs-lookup"><span data-stu-id="f9b65-109">**Visual Studio (for Windows).**</span></span> <span data-ttu-id="f9b65-110">以 Docker 為基礎的 .NET 5 應用程式開發 Visual Studio 需要 Visual Studio 2019 16.4 版或更新版本。</span><span class="sxs-lookup"><span data-stu-id="f9b65-110">Docker-based .NET 5 application development with Visual Studio requires Visual Studio 2019 version 16.4 or later.</span></span> <span data-ttu-id="f9b65-111">Visual Studio 2019 隨附的 Docker 工具已內建。</span><span class="sxs-lookup"><span data-stu-id="f9b65-111">Visual Studio 2019 comes with tools for Docker already built in.</span></span> <span data-ttu-id="f9b65-112">Docker 工具可讓您直接在目標 Docker 環境中開發、執行和驗證應用程式。</span><span class="sxs-lookup"><span data-stu-id="f9b65-112">The tools for Docker let you develop, run, and validate your applications directly in the target Docker environment.</span></span> <span data-ttu-id="f9b65-113">您可以按 F5 鍵，直接在 Docker 主機中執行並偵錯您的應用程式 (單一容器或多個容器)，或按 CTRL+F5 來編輯及重新整理您的應用程式，而不需要重建容器。</span><span class="sxs-lookup"><span data-stu-id="f9b65-113">You can press F5 to run and debug your application (single container or multiple containers) directly into a Docker host, or press CTRL+F5 to edit and refresh your application without having to rebuild the container.</span></span> <span data-ttu-id="f9b65-114">此 IDE 是以 Docker 為基礎之應用程式的最強大開發選擇。</span><span class="sxs-lookup"><span data-stu-id="f9b65-114">This IDE is the most powerful development choice for Docker-based apps.</span></span>

<span data-ttu-id="f9b65-115">**Visual Studio for Mac。**</span><span class="sxs-lookup"><span data-stu-id="f9b65-115">**Visual Studio for Mac.**</span></span> <span data-ttu-id="f9b65-116">它是在 macOS 中執行的 IDE Xamarin Studio 演進。</span><span class="sxs-lookup"><span data-stu-id="f9b65-116">It's an IDE, evolution of Xamarin Studio, running in macOS.</span></span> <span data-ttu-id="f9b65-117">針對 .NET 5 開發，它需要版本8.4 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="f9b65-117">For .NET 5 development, it requires version 8.4 or later.</span></span> <span data-ttu-id="f9b65-118">如果開發人員想要使用強大的 IDE，這項工具應該是在 macOS 電腦上工作的開發人員偏好的選擇。</span><span class="sxs-lookup"><span data-stu-id="f9b65-118">This tool should be the preferred choice for developers working in macOS machines who also want to use a powerful IDE.</span></span>

<span data-ttu-id="f9b65-119">**Visual Studio Code 和 Docker CLI**。</span><span class="sxs-lookup"><span data-stu-id="f9b65-119">**Visual Studio Code and Docker CLI**.</span></span> <span data-ttu-id="f9b65-120">如果您偏好使用支援任何開發語言的輕量和跨平臺編輯器，則可以使用 Visual Studio Code 和 Docker CLI。</span><span class="sxs-lookup"><span data-stu-id="f9b65-120">If you prefer a lightweight and cross-platform editor that supports any development language, you can use Visual Studio Code and the Docker CLI.</span></span> <span data-ttu-id="f9b65-121">此 IDE 是適用于 macOS、Linux 和 Windows 的跨平臺開發方法。</span><span class="sxs-lookup"><span data-stu-id="f9b65-121">This IDE is a cross-platform development approach for macOS, Linux, and Windows.</span></span> <span data-ttu-id="f9b65-122">此外，Visual Studio Code 支援 Docker 的延伸模組 (例如適用於 Dockerfile 的 IntelliSense)，以及可從編輯器執行 Docker 命令的捷徑工作。</span><span class="sxs-lookup"><span data-stu-id="f9b65-122">Additionally, Visual Studio Code supports extensions for Docker such as IntelliSense for Dockerfiles and shortcut tasks to run Docker commands from the editor.</span></span>

<span data-ttu-id="f9b65-123">透過安裝 [Docker Desktop Community Edition (CE)](https://hub.docker.com/search/?type=edition&offering=community)，您可以使用單一 Docker CLI 來建置 Windows 和 Linux 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f9b65-123">By installing [Docker Desktop Community Edition (CE)](https://hub.docker.com/search/?type=edition&offering=community), you can use a single Docker CLI to build apps for both Windows and Linux.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f9b65-124">其他資源</span><span class="sxs-lookup"><span data-stu-id="f9b65-124">Additional resources</span></span>

- <span data-ttu-id="f9b65-125">**Visual Studio**。</span><span class="sxs-lookup"><span data-stu-id="f9b65-125">**Visual Studio**.</span></span> <span data-ttu-id="f9b65-126">官方網站。</span><span class="sxs-lookup"><span data-stu-id="f9b65-126">Official site.</span></span> \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- <span data-ttu-id="f9b65-127">**Visual Studio Code** \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="f9b65-127">**Visual Studio Code**.</span></span> <span data-ttu-id="f9b65-128">官方網站。</span><span class="sxs-lookup"><span data-stu-id="f9b65-128">Official site.</span></span> \
  <https://code.visualstudio.com/download>

- <span data-ttu-id="f9b65-129">**適用于 Windows 社群版的 Docker Desktop (CE)** </span><span class="sxs-lookup"><span data-stu-id="f9b65-129">**Docker Desktop for Windows Community Edition (CE)** </span></span>\
  [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

- <span data-ttu-id="f9b65-130">**Docker Desktop for Mac 社區版 (CE)** </span><span class="sxs-lookup"><span data-stu-id="f9b65-130">**Docker Desktop for Mac Community Edition (CE)** </span></span>\
  [https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

## <a name="net-languages-and-frameworks-for-docker-containers"></a><span data-ttu-id="f9b65-131">Docker 容器的 .NET 語言和 Framework</span><span class="sxs-lookup"><span data-stu-id="f9b65-131">.NET languages and frameworks for Docker containers</span></span>

<span data-ttu-id="f9b65-132">如本指南稍早章節所述，您可以在開發 Docker 容器化 .NET 應用程式時，使用 .NET Framework、.NET 5 或開放原始碼 Mono 專案。</span><span class="sxs-lookup"><span data-stu-id="f9b65-132">As mentioned in earlier sections of this guide, you can use .NET Framework, .NET 5, or the open-source Mono project when developing Docker containerized .NET applications.</span></span> <span data-ttu-id="f9b65-133">當目標設為 Linux 或 Windows 容器時，您可以根據所使用的 .NET Framework，以 C\#、F\# 或 Visual Basic 進行開發。</span><span class="sxs-lookup"><span data-stu-id="f9b65-133">You can develop in C\#, F\#, or Visual Basic when targeting Linux or Windows Containers, depending on which .NET framework is in use.</span></span> <span data-ttu-id="f9b65-134">如需 .NET 語言的詳細資訊，請參閱部落格文章 [The .NET Language Strategy](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/) (.NET 語言策略)。</span><span class="sxs-lookup"><span data-stu-id="f9b65-134">For more details about.NET languages, see the blog post [The .NET Language Strategy](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f9b65-135">[上一個](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md) 
>[下一步](docker-app-development-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f9b65-135">[Previous](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
[Next](docker-app-development-workflow.md)</span></span>
