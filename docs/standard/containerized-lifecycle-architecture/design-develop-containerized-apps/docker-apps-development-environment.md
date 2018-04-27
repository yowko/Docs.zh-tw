---
title: Docker 應用程式的開發環境
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ddd1006c8c6728d4d315442f409f8fa33e54f9a3
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="d1eeb-103">Docker 應用程式的開發環境</span><span class="sxs-lookup"><span data-stu-id="d1eeb-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="d1eeb-104">開發工具選擇：IDE 或編輯器</span><span class="sxs-lookup"><span data-stu-id="d1eeb-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="d1eeb-105">不論您偏好使用完整且功能強大的 IDE 或是套輕量型且敏捷式軟體開發編輯器中，如果 Microsoft 有您涵蓋談到開發 Docker 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d1eeb-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="d1eeb-106">Visual Studio 程式碼和 Docker CLI （如 Mac、 Linux 及 Windows 的跨平台工具）</span><span class="sxs-lookup"><span data-stu-id="d1eeb-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="d1eeb-107">如果您想支援任何開發語言的輕量型、 跨平台編輯器，您可以使用 Visual Studio 程式碼和 Docker CLI。</span><span class="sxs-lookup"><span data-stu-id="d1eeb-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="d1eeb-108">這些產品，提供簡單但強大體驗，這相當重要的開發人員工作流程可簡化程序。</span><span class="sxs-lookup"><span data-stu-id="d1eeb-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="d1eeb-109">藉由安裝"Docker for Mac"或"Docker for Windows"（開發環境），Docker 開發人員可以使用單一的 Docker CLI 建置應用程式的 Windows 或 Linux （執行階段環境）。</span><span class="sxs-lookup"><span data-stu-id="d1eeb-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="d1eeb-110">此外，Visual Studio 程式碼支援對具有 IntelliSense 的 Dockerfiles 和快顯工作從編輯器執行 Docker 命令的 Docker 擴充功能。</span><span class="sxs-lookup"><span data-stu-id="d1eeb-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="d1eeb-111">若要下載 Visual Studio 程式碼，請移至<https://code.visualstudio.com/download>。</span><span class="sxs-lookup"><span data-stu-id="d1eeb-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>

<span data-ttu-id="d1eeb-112">若要下載 Mac 和 Windows Docker，請移至<http://www.docker.com/products/docker>。</span><span class="sxs-lookup"><span data-stu-id="d1eeb-112">To download Docker for Mac and Windows, go to <http://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools"></a><span data-ttu-id="d1eeb-113">Visual Studio 和 Docker 工具</span><span class="sxs-lookup"><span data-stu-id="d1eeb-113">Visual Studio with Docker Tools</span></span>

<span data-ttu-id="d1eeb-114">當您使用 Visual Studio 2015，您就可以安裝附加元件工具 [Visual Studio 的 Docker 工具]。</span><span class="sxs-lookup"><span data-stu-id="d1eeb-114">When you're using Visual Studio 2015 you can install the add-on tools "Docker Tools for Visual Studio."</span></span> <span data-ttu-id="d1eeb-115">針對 Visual Studio 2017，Docker 工具來自內建的已。</span><span class="sxs-lookup"><span data-stu-id="d1eeb-115">For Visual Studio 2017, Docker Tools come built in already.</span></span> <span data-ttu-id="d1eeb-116">在這兩種情況下，您可以開發、 執行和驗證您的應用程式，直接在所選的 Docker 環境中。</span><span class="sxs-lookup"><span data-stu-id="d1eeb-116">In both cases you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="d1eeb-117">F5 應用程式 （單一容器或多個容器） 直接在 Docker 主機並偵錯，或按 Ctrl + F5 鍵來編輯和重新整理您的應用程式，而不必重建容器。</span><span class="sxs-lookup"><span data-stu-id="d1eeb-117">F5 your application (single container or multiple containers) directly into a Docker host with debugging, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="d1eeb-118">這是 Windows 開發人員建立 Docker 容器的 Linux 或 Windows 的最簡單且功能更強大的選擇。</span><span class="sxs-lookup"><span data-stu-id="d1eeb-118">This is the simplest and more powerful choice for Windows developers creating Docker containers for Linux or Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="d1eeb-119">若要下載 Visual Studio 的 Docker 工具，請移至<https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>。</span><span class="sxs-lookup"><span data-stu-id="d1eeb-119">To download Docker Tools for Visual Studio, go to <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="d1eeb-120">語言和架構選項</span><span class="sxs-lookup"><span data-stu-id="d1eeb-120">Language and framework choices</span></span>

<span data-ttu-id="d1eeb-121">您可以開發 Docker 應用程式和與大多數最新型的程式設計語言的 Microsoft 工具。</span><span class="sxs-lookup"><span data-stu-id="d1eeb-121">You can develop Docker applications and Microsoft tools with most modern languages.</span></span> <span data-ttu-id="d1eeb-122">以下是初始的清單，但不是限於它：</span><span class="sxs-lookup"><span data-stu-id="d1eeb-122">The following is an initial list, but you are not limited to it:</span></span>

-   <span data-ttu-id="d1eeb-123">.NET core 與 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d1eeb-123">.NET Core and ASP.NET Core</span></span>

-   <span data-ttu-id="d1eeb-124">Node.js</span><span class="sxs-lookup"><span data-stu-id="d1eeb-124">Node.js</span></span>

-   <span data-ttu-id="d1eeb-125">Golang</span><span class="sxs-lookup"><span data-stu-id="d1eeb-125">Golang</span></span>

-   <span data-ttu-id="d1eeb-126">Java</span><span class="sxs-lookup"><span data-stu-id="d1eeb-126">Java</span></span>

-   <span data-ttu-id="d1eeb-127">Ruby</span><span class="sxs-lookup"><span data-stu-id="d1eeb-127">Ruby</span></span>

-   <span data-ttu-id="d1eeb-128">Python</span><span class="sxs-lookup"><span data-stu-id="d1eeb-128">Python</span></span>

<span data-ttu-id="d1eeb-129">基本上，您可以使用現代 Docker 的 Linux 或 Windows 所支援的語言。</span><span class="sxs-lookup"><span data-stu-id="d1eeb-129">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="d1eeb-130">[上一個] (協調-高的延展性-availability.md) [下一步] (docker-應用程式-內部-迴圈-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d1eeb-130">[Previous] (orchestrate-high-scalability-availability.md) [Next] (docker-apps-inner-loop-workflow.md)</span></span>
