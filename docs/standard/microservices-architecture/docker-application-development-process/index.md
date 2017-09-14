---
title: "Docker 應用程式的開發程序"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | Docker 應用程式的開發程序"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.translationtype: HT
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: f4c241f463ff1270037c7d66ba39409ca5d9e728
ms.contentlocale: zh-tw
ms.lasthandoff: 09/05/2017

---
# <a name="development-process-for-docker-based-applications"></a><span data-ttu-id="7eaf6-104">Docker 應用程式的開發程序</span><span class="sxs-lookup"><span data-stu-id="7eaf6-104">Development Process for Docker-Based Applications</span></span>

<span data-ttu-id="7eaf6-105">*依您喜歡的方式來開發容器化 .NET 應用程式，可以是 Visual Studio 和 Visual Studio Tools for Docker 導向的 IDE，或是 Docker CLI 和 Visual Studio Code 導向的 CLI/編輯器。*</span><span class="sxs-lookup"><span data-stu-id="7eaf6-105">*Develop containerized .NET applications the way you like, either IDE focused with Visual Studio and Visual Studio tools for Docker or CLI/Editor focused with Docker CLI and Visual Studio Code.*</span></span>

## <a name="development-environment-for-docker-apps"></a><span data-ttu-id="7eaf6-106">Docker 應用程式的開發環境</span><span class="sxs-lookup"><span data-stu-id="7eaf6-106">Development environment for Docker apps</span></span>

### <a name="development-tool-choices-ide-or-editor"></a><span data-ttu-id="7eaf6-107">開發工具選擇：IDE 或編輯器</span><span class="sxs-lookup"><span data-stu-id="7eaf6-107">Development tool choices: IDE or editor</span></span>

<span data-ttu-id="7eaf6-108">不論您偏好使用完整且強大的 IDE，還是輕量型的敏捷式編輯器，Microsoft 都有相關工具可供您用來開發 Docker 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-108">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has tools that you can use for developing Docker applications.</span></span>

<span data-ttu-id="7eaf6-109">**Visual Studio Tools for Docker**。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-109">**Visual Studio with Tools for Docker**.</span></span> <span data-ttu-id="7eaf6-110">如果您使用 Visual Studio 2015，您可以安裝 [Visual Studio Tools for Docker](https://marketplace.visualstudio.com/items?itemName=MicrosoftCloudExplorer.VisualStudioToolsforDocker-Preview) 增益集。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-110">If you are using Visual Studio 2015, you can install the [Visual Studio Tools for Docker](https://marketplace.visualstudio.com/items?itemName=MicrosoftCloudExplorer.VisualStudioToolsforDocker-Preview) add-in.</span></span> <span data-ttu-id="7eaf6-111">如果您使用 Visual Studio 2017，則已內建 Docker 工具。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-111">If you are using Visual Studio 2017, tools for Docker are already built-in.</span></span> <span data-ttu-id="7eaf6-112">不論是哪種情況，Docker 工具都可讓您直接在目標 Docker 環境中開發、執行及驗證應用程式。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-112">In either case, the tools for Docker let you develop, run, and validate your applications directly in the target Docker environment.</span></span> <span data-ttu-id="7eaf6-113">您可以按 F5 鍵，直接在 Docker 主機中執行並偵錯您的應用程式 (單一容器或多個容器)，或按 CTRL+F5 來編輯及重新整理您的應用程式，而不需要重建容器。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-113">You can press F5 to run and debug your application (single container or multiple containers) directly into a Docker host, or press CTRL+F5 to edit and refresh your application without having to rebuild the container.</span></span> <span data-ttu-id="7eaf6-114">這是適用於 Windows 開發人員並以 Linux 或 Windows 之 Docker 容器為目標的最簡單且最強大的選擇。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-114">This is the simplest and most powerful choice for Windows developers targeting Docker containers for Linux or Windows.</span></span>

<span data-ttu-id="7eaf6-115">**Visual Studio Code 和 Docker CLI**。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-115">**Visual Studio Code and Docker CLI**.</span></span> <span data-ttu-id="7eaf6-116">如果您偏好使用支援任何開發語言之輕量型且跨平台的編輯器，您可以使用 Microsoft Visual Studio Code (VS Code) 和 Docker CLI。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-116">If you prefer a lightweight and cross-platform editor that supports any development language, you can use Microsoft Visual Studio Code (VS Code) and the Docker CLI.</span></span> <span data-ttu-id="7eaf6-117">這是適用於 Mac、Linux 和 Windows 的跨平台開發方法。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-117">This is a cross-platform development approach for Mac, Linux, and Windows.</span></span>

<span data-ttu-id="7eaf6-118">這些產品提供簡單但強大的體驗，可簡化開發人員工作流程。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-118">These products provide a simple but robust experience that streamlines the developer workflow.</span></span> <span data-ttu-id="7eaf6-119">藉由安裝 [Docker Community Edition (CE)](https://www.docker.com/community-edition) 工具，您可以使用單一 Docker CLI 來建置 Windows 和 Linux 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-119">By installing [Docker Community Edition (CE)](https://www.docker.com/community-edition) tools, you can use a single Docker CLI to build apps for both Windows and Linux.</span></span> <span data-ttu-id="7eaf6-120">此外，Visual Studio Code 支援 Docker 的延伸模組 (例如適用於 Dockerfile 的 IntelliSense)，以及可從編輯器執行 Docker 命令的捷徑工作。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-120">Additionally, Visual Studio Code supports extensions for Docker such as IntelliSense for Dockerfiles and shortcut tasks to run Docker commands from the editor.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7eaf6-121">其他資源</span><span class="sxs-lookup"><span data-stu-id="7eaf6-121">Additional resources</span></span>

-   <span data-ttu-id="7eaf6-122">**Visual Studio Tools for Docker**
    [*https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4*](https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4)</span><span class="sxs-lookup"><span data-stu-id="7eaf6-122">**Visual Studio Tools for Docker**
[*https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4*](https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4)</span></span>

-   <span data-ttu-id="7eaf6-123">**Visual Studio Code**。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-123">**Visual Studio Code**.</span></span> <span data-ttu-id="7eaf6-124">官方網站。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-124">Official site.</span></span>
    [<span data-ttu-id="7eaf6-125">*https://code.visualstudio.com/download*</span><span class="sxs-lookup"><span data-stu-id="7eaf6-125">*https://code.visualstudio.com/download*</span></span>](https://code.visualstudio.com/download)

-   <span data-ttu-id="7eaf6-126">**適用於 Mac 和 Windows 的 Docker Community Edition (CE)**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span><span class="sxs-lookup"><span data-stu-id="7eaf6-126">**Docker Community Edition (CE) for Mac and Windows**
[*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span></span>

## <a name="net-languages-and-frameworks-for-docker-containers"></a><span data-ttu-id="7eaf6-127">Docker 容器的 .NET 語言和 Framework</span><span class="sxs-lookup"><span data-stu-id="7eaf6-127">.NET languages and frameworks for Docker containers</span></span>

<span data-ttu-id="7eaf6-128">如本指南稍早章節所述，開發 Docker 容器化 .NET 應用程式時，您可以使用 .NET Framework、.NET Core 或開放原始碼 Mono 專案。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-128">As mentioned in earlier sections of this guide, you can use .NET Framework, .NET Core, or the open-source Mono project when developing Docker containerized .NET applications.</span></span> <span data-ttu-id="7eaf6-129">當目標設為 Linux 或 Windows 容器時，您可以根據所使用的 .NET Framework，以 C\#、F\# 或 Visual Basic 進行開發。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-129">You can develop in C\#, F\#, or Visual Basic when targeting Linux or Windows Containers, depending on which .NET framework is in use.</span></span> <span data-ttu-id="7eaf6-130">如需 .NET 語言的詳細資訊，請參閱部落格文章 [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/) (.NET 語言策略)。</span><span class="sxs-lookup"><span data-stu-id="7eaf6-130">For more details about.NET languages, see the blog post [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="7eaf6-131">[上一個] (../architect-microservice-container-applications/using-azure-service-fabric.md) [下一個] (docker-app-development-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7eaf6-131">[Previous] (../architect-microservice-container-applications/using-azure-service-fabric.md) [Next] (docker-app-development-workflow.md)</span></span>

