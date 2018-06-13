---
title: Docker 應用程式的開發程序
description: 容器化 .NET 應用程式的 .NET 微服務架構 | Docker 應用程式的開發程序
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 881817f4f1007edad85eefb9002d56764cbf2a02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574780"
---
# <a name="development-process-for-docker-based-applications"></a><span data-ttu-id="f6db2-103">Docker 應用程式的開發程序</span><span class="sxs-lookup"><span data-stu-id="f6db2-103">Development Process for Docker-Based Applications</span></span>

<span data-ttu-id="f6db2-104">*依您喜歡的方式來開發容器化 .NET 應用程式，可以是 Visual Studio 和 Visual Studio Tools for Docker 導向的 IDE，或是 Docker CLI 和 Visual Studio Code 導向的 CLI/編輯器。*</span><span class="sxs-lookup"><span data-stu-id="f6db2-104">*Develop containerized .NET applications the way you like, either IDE focused with Visual Studio and Visual Studio tools for Docker or CLI/Editor focused with Docker CLI and Visual Studio Code.*</span></span>

## <a name="development-environment-for-docker-apps"></a><span data-ttu-id="f6db2-105">Docker 應用程式的開發環境</span><span class="sxs-lookup"><span data-stu-id="f6db2-105">Development environment for Docker apps</span></span>

### <a name="development-tool-choices-ide-or-editor"></a><span data-ttu-id="f6db2-106">開發工具選擇：IDE 或編輯器</span><span class="sxs-lookup"><span data-stu-id="f6db2-106">Development tool choices: IDE or editor</span></span>

<span data-ttu-id="f6db2-107">不論您偏好使用完整且強大的 IDE，還是輕量型的敏捷式編輯器，Microsoft 都有相關工具可供您用來開發 Docker 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6db2-107">Whether you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has tools that you can use for developing Docker applications.</span></span>

<span data-ttu-id="f6db2-108">**Visual Studio (適用於 Windows)**.</span><span class="sxs-lookup"><span data-stu-id="f6db2-108">**Visual Studio (for Windows)**.</span></span> <span data-ttu-id="f6db2-109">若要開發以 Docker 為基礎的應用程式，請使用隨附已內建 Docker 工具的 Visual Studio 2017 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="f6db2-109">To develop Docker-based applications, use Visual Studio 2017 or later versions that comes with tools for Docker already built-in.</span></span> <span data-ttu-id="f6db2-110">Docker 工具可讓您直接在目標 Docker 環境中開發、執行和驗證應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6db2-110">The tools for Docker let you develop, run, and validate your applications directly in the target Docker environment.</span></span> <span data-ttu-id="f6db2-111">您可以按 F5 鍵，直接在 Docker 主機中執行並偵錯您的應用程式 (單一容器或多個容器)，或按 CTRL+F5 來編輯及重新整理您的應用程式，而不需要重建容器。</span><span class="sxs-lookup"><span data-stu-id="f6db2-111">You can press F5 to run and debug your application (single container or multiple containers) directly into a Docker host, or press CTRL+F5 to edit and refresh your application without having to rebuild the container.</span></span> <span data-ttu-id="f6db2-112">這是以 Docker 為基礎之應用程式的最強大開發選擇。</span><span class="sxs-lookup"><span data-stu-id="f6db2-112">This is the most powerful development choice for Docker-based apps.</span></span>

<span data-ttu-id="f6db2-113">**Visual Studio for Mac**.</span><span class="sxs-lookup"><span data-stu-id="f6db2-113">**Visual Studio for Mac**.</span></span> <span data-ttu-id="f6db2-114">它是在 macOS 上執行的 IDE (即 Xamarin Studio 的演進)，並支援以 Docker 為基礎的應用程式開發。</span><span class="sxs-lookup"><span data-stu-id="f6db2-114">It is an IDE, evolution of Xamarin Studio, that runs on macOS and supports Docker-based application development.</span></span> <span data-ttu-id="f6db2-115">針對在 Mac 電腦上工作同時想要使用功能強大之 IDE 的開發人員，這應該是偏好選項。</span><span class="sxs-lookup"><span data-stu-id="f6db2-115">This should be the preferred choice for developers working in Mac machines who also want to use a powerful IDE.</span></span>

<span data-ttu-id="f6db2-116">**Visual Studio Code 和 Docker CLI**。</span><span class="sxs-lookup"><span data-stu-id="f6db2-116">**Visual Studio Code and Docker CLI**.</span></span> <span data-ttu-id="f6db2-117">如果您偏好使用支援任何開發語言之輕量型且跨平台的編輯器，您可以使用 Microsoft Visual Studio Code (VS Code) 和 Docker CLI。</span><span class="sxs-lookup"><span data-stu-id="f6db2-117">If you prefer a lightweight and cross-platform editor that supports any development language, you can use Microsoft Visual Studio Code (VS Code) and the Docker CLI.</span></span> <span data-ttu-id="f6db2-118">這是適用於 Mac、Linux 和 Windows 的跨平台開發方法。</span><span class="sxs-lookup"><span data-stu-id="f6db2-118">This is a cross-platform development approach for Mac, Linux, and Windows.</span></span>

<span data-ttu-id="f6db2-119">藉由安裝 [Docker Community Edition (CE)](https://www.docker.com/community-edition) 工具，您可以使用單一 Docker CLI 來建置 Windows 和 Linux 應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6db2-119">By installing [Docker Community Edition (CE)](https://www.docker.com/community-edition) tools, you can use a single Docker CLI to build apps for both Windows and Linux.</span></span> <span data-ttu-id="f6db2-120">此外，Visual Studio Code 支援 Docker 的延伸模組 (例如適用於 Dockerfile 的 IntelliSense)，以及可從編輯器執行 Docker 命令的捷徑工作。</span><span class="sxs-lookup"><span data-stu-id="f6db2-120">Additionally, Visual Studio Code supports extensions for Docker such as IntelliSense for Dockerfiles and shortcut tasks to run Docker commands from the editor.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="f6db2-121">其他資源</span><span class="sxs-lookup"><span data-stu-id="f6db2-121">Additional resources</span></span>

-   <span data-ttu-id="f6db2-122">**Visual Studio Tools for Docker**
    [*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span><span class="sxs-lookup"><span data-stu-id="f6db2-122">**Visual Studio Tools for Docker**
[*https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker*](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)</span></span>

-   <span data-ttu-id="f6db2-123">**Visual Studio Code**。</span><span class="sxs-lookup"><span data-stu-id="f6db2-123">**Visual Studio Code**.</span></span> <span data-ttu-id="f6db2-124">官方網站。</span><span class="sxs-lookup"><span data-stu-id="f6db2-124">Official site.</span></span>
    [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

-   <span data-ttu-id="f6db2-125">**適用於 Mac 和 Windows 的 Docker Community Edition (CE)**
    [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span><span class="sxs-lookup"><span data-stu-id="f6db2-125">**Docker Community Edition (CE) for Mac and Windows**
[*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)</span></span>

## <a name="net-languages-and-frameworks-for-docker-containers"></a><span data-ttu-id="f6db2-126">Docker 容器的 .NET 語言和 Framework</span><span class="sxs-lookup"><span data-stu-id="f6db2-126">.NET languages and frameworks for Docker containers</span></span>

<span data-ttu-id="f6db2-127">如本指南稍早章節所述，開發 Docker 容器化 .NET 應用程式時，您可以使用 .NET Framework、.NET Core 或開放原始碼 Mono 專案。</span><span class="sxs-lookup"><span data-stu-id="f6db2-127">As mentioned in earlier sections of this guide, you can use .NET Framework, .NET Core, or the open-source Mono project when developing Docker containerized .NET applications.</span></span> <span data-ttu-id="f6db2-128">當目標設為 Linux 或 Windows 容器時，您可以根據所使用的 .NET Framework，以 C\#、F\# 或 Visual Basic 進行開發。</span><span class="sxs-lookup"><span data-stu-id="f6db2-128">You can develop in C\#, F\#, or Visual Basic when targeting Linux or Windows Containers, depending on which .NET framework is in use.</span></span> <span data-ttu-id="f6db2-129">如需 .NET 語言的詳細資訊，請參閱部落格文章 [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/) (.NET 語言策略)。</span><span class="sxs-lookup"><span data-stu-id="f6db2-129">For more details about.NET languages, see the blog post [The .NET Language Strategy](https://blogs.msdn.microsoft.com/dotnet/2017/02/01/the-net-language-strategy/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="f6db2-130">[上一個] (../architect-microservice-container-applications/using-azure-service-fabric.md) [下一個] (docker-app-development-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f6db2-130">[Previous] (../architect-microservice-container-applications/using-azure-service-fabric.md) [Next] (docker-app-development-workflow.md)</span></span>
