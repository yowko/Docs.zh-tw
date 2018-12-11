---
title: Docker 應用程式的開發環境
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 471b52fd577e5560bd93e6da50f2032d63eb2e6f
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152406"
---
# <a name="development-environment-for-docker-apps"></a><span data-ttu-id="5e0d4-103">Docker 應用程式的開發環境</span><span class="sxs-lookup"><span data-stu-id="5e0d4-103">Development environment for Docker apps</span></span>

## <a name="development-tools-choices-ide-or-editor"></a><span data-ttu-id="5e0d4-104">開發工具選項：IDE 或編輯器</span><span class="sxs-lookup"><span data-stu-id="5e0d4-104">Development tools choices: IDE or editor</span></span>

<span data-ttu-id="5e0d4-105">不論您偏好使用完整且功能強大的 IDE，還是輕量型的敏捷式編輯器中，如果 Microsoft 擁有您分憂解勞談到開發 Docker 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5e0d4-105">No matter if you prefer a full and powerful IDE or a lightweight and agile editor, Microsoft has you covered when it comes to developing Docker applications.</span></span>

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a><span data-ttu-id="5e0d4-106">Visual Studio Code 和 Docker CLI （適用於 Mac、 Linux 和 Windows 的跨平台工具）</span><span class="sxs-lookup"><span data-stu-id="5e0d4-106">Visual Studio Code and Docker CLI (cross-platform tools for Mac, Linux, and Windows)</span></span>

<span data-ttu-id="5e0d4-107">如果您想支援任何開發語言的輕量型、 跨平台編輯器時，您可以使用 Visual Studio Code 和 Docker CLI。</span><span class="sxs-lookup"><span data-stu-id="5e0d4-107">If you prefer a lightweight, cross-platform editor supporting any development language, you can use Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="5e0d4-108">這些產品提供簡單但強大的體驗，也就是很重要的簡化開發人員工作流程。</span><span class="sxs-lookup"><span data-stu-id="5e0d4-108">These products provide a simple yet robust experience, which is critical for streamlining the developer workflow.</span></span> <span data-ttu-id="5e0d4-109">藉由安裝 「 Docker for Mac"或"Docker for Windows 」 （開發環境），Docker 開發人員可以使用單一 Docker CLI，來建置 Windows 或 Linux （執行階段環境） 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5e0d4-109">By installing "Docker for Mac" or "Docker for Windows" (development environment), Docker developers can use a single Docker CLI to build apps for both Windows or Linux (runtime environment).</span></span> <span data-ttu-id="5e0d4-110">此外，Visual Studio Code 支援 Docker 具有 IntelliSense 的 Dockerfiles 和捷徑工作從編輯器執行 Docker 命令延伸模組。</span><span class="sxs-lookup"><span data-stu-id="5e0d4-110">Plus, Visual Studio Code supports extensions for Docker with IntelliSense for Dockerfiles and shortcut-tasks to run Docker commands from the editor.</span></span>

> [!NOTE]
> <span data-ttu-id="5e0d4-111">若要下載 Visual Studio Code，請移至<https://code.visualstudio.com/download>。</span><span class="sxs-lookup"><span data-stu-id="5e0d4-111">To download Visual Studio Code, go to <https://code.visualstudio.com/download>.</span></span>

<span data-ttu-id="5e0d4-112">若要下載適用於 Mac 和 Windows 的 Docker，請移至<https://www.docker.com/products/docker>。</span><span class="sxs-lookup"><span data-stu-id="5e0d4-112">To download Docker for Mac and Windows, go to <https://www.docker.com/products/docker>.</span></span>

### <a name="visual-studio-with-docker-tools"></a><span data-ttu-id="5e0d4-113">Visual Studio 中使用 Docker 工具</span><span class="sxs-lookup"><span data-stu-id="5e0d4-113">Visual Studio with Docker Tools</span></span>

<span data-ttu-id="5e0d4-114">當您使用 Visual Studio 2015，您就可以安裝附加元件工具 [Docker Tools for Visual Studio]。</span><span class="sxs-lookup"><span data-stu-id="5e0d4-114">When you're using Visual Studio 2015 you can install the add-on tools "Docker Tools for Visual Studio."</span></span> <span data-ttu-id="5e0d4-115">Visual Studio 2017，Docker 工具有內建的已。</span><span class="sxs-lookup"><span data-stu-id="5e0d4-115">For Visual Studio 2017, Docker Tools come built in already.</span></span> <span data-ttu-id="5e0d4-116">在這兩種情況下，您可以開發、 執行及驗證您的應用程式，直接在所選的 Docker 環境中。</span><span class="sxs-lookup"><span data-stu-id="5e0d4-116">In both cases you can develop, run, and validate your applications directly in the chosen Docker environment.</span></span> <span data-ttu-id="5e0d4-117">F5 應用程式 （單一容器或多個容器） 直接在 Docker 主機並偵錯，或按 Ctrl + F5 編輯和重新整理您的應用程式，而不需要重建容器。</span><span class="sxs-lookup"><span data-stu-id="5e0d4-117">F5 your application (single container or multiple containers) directly into a Docker host with debugging, or press Ctrl+F5 to edit and refresh your app without having to rebuild the container.</span></span> <span data-ttu-id="5e0d4-118">這是 Windows 開發人員建立 Linux 或 Windows 的 Docker 容器的最簡單且功能更強大的選擇。</span><span class="sxs-lookup"><span data-stu-id="5e0d4-118">This is the simplest and more powerful choice for Windows developers creating Docker containers for Linux or Windows.</span></span>

> [!NOTE]
> <span data-ttu-id="5e0d4-119">若要下載 Visual Studio Docker 工具，請移至<https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>。</span><span class="sxs-lookup"><span data-stu-id="5e0d4-119">To download Docker Tools for Visual Studio, go to <https://visualstudiogallery.msdn.microsoft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4>.</span></span>

## <a name="language-and-framework-choices"></a><span data-ttu-id="5e0d4-120">語言和架構選項</span><span class="sxs-lookup"><span data-stu-id="5e0d4-120">Language and framework choices</span></span>

<span data-ttu-id="5e0d4-121">您可以開發 Docker 應用程式及現今大部分語言的 Microsoft 工具。</span><span class="sxs-lookup"><span data-stu-id="5e0d4-121">You can develop Docker applications and Microsoft tools with most modern languages.</span></span> <span data-ttu-id="5e0d4-122">以下是初始的清單，但不是限於它：</span><span class="sxs-lookup"><span data-stu-id="5e0d4-122">The following is an initial list, but you are not limited to it:</span></span>

-   <span data-ttu-id="5e0d4-123">.NET Core 與 ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5e0d4-123">.NET Core and ASP.NET Core</span></span>
-   <span data-ttu-id="5e0d4-124">Node.js</span><span class="sxs-lookup"><span data-stu-id="5e0d4-124">Node.js</span></span>
-   <span data-ttu-id="5e0d4-125">Golang</span><span class="sxs-lookup"><span data-stu-id="5e0d4-125">Golang</span></span>
-   <span data-ttu-id="5e0d4-126">Java</span><span class="sxs-lookup"><span data-stu-id="5e0d4-126">Java</span></span>
-   <span data-ttu-id="5e0d4-127">Ruby</span><span class="sxs-lookup"><span data-stu-id="5e0d4-127">Ruby</span></span>
-   <span data-ttu-id="5e0d4-128">Python</span><span class="sxs-lookup"><span data-stu-id="5e0d4-128">Python</span></span>

<span data-ttu-id="5e0d4-129">基本上，您可以使用現代的語言支援在 Linux 或 Windows 的 Docker。</span><span class="sxs-lookup"><span data-stu-id="5e0d4-129">Basically, you can use any modern language supported by Docker in Linux or Windows.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5e0d4-130">[上一頁](orchestrate-high-scalability-availability.md)
>[下一頁](docker-apps-inner-loop-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="5e0d4-130">[Previous](orchestrate-high-scalability-availability.md)
[Next](docker-apps-inner-loop-workflow.md)</span></span>