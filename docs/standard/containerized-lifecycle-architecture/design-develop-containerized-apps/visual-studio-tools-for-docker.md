---
title: Visual Studio Tools for Windows 上的 Docker
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: 7daac744238feb38358e4cc0ab185e90257aa98d
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48027451"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a><span data-ttu-id="1b0b9-103">使用 Visual Studio Tools for Docker (Windows 上的 Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="1b0b9-103">Using Visual Studio Tools for Docker (Visual Studio on Windows)</span></span>

<span data-ttu-id="1b0b9-104">使用 Visual Studio Code 和 Docker CLI 時，工作流程類似 Visual Studio Tools for Docker 開發工作流程。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-104">The Visual Studio Tools for Docker development workflow is similar to the workflow when using Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="1b0b9-105">事實上，它根據相同的 Docker CLI，但您更輕鬆地開始使用、 簡化程序，並提供更高的生產力組建、 執行和撰寫工作。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-105">In fact, it's based on the same Docker CLI, but it's easier to get started, simplifies the process, and provides greater productivity for the build, run, and compose tasks.</span></span> <span data-ttu-id="1b0b9-106">執行和偵錯您的容器，透過簡單的動作，例如**F5**並**Ctrl**+**F5**。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-106">Execute and debug your containers via simple actions like **F5** and **Ctrl**+**F5**.</span></span> <span data-ttu-id="1b0b9-107">選擇性的容器協調流程的支援，除了能夠執行和偵錯單一容器中，您可以執行，並同時在偵錯容器 （整個解決方案） 的群組。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-107">With the optional container orchestration support, in addition to being able to run and debug a single container, you can run and debug a group of containers (a whole solution) at the same time.</span></span>

> [!NOTE]
> <span data-ttu-id="1b0b9-108">本文適用於 Visual Studio 在 Windows，而非 Visual Studio for mac。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-108">This article applies to Visual Studio on Windows, and not Visual Studio for Mac.</span></span>

## <a name="configure-your-local-environment"></a><span data-ttu-id="1b0b9-109">設定您的本機環境</span><span class="sxs-lookup"><span data-stu-id="1b0b9-109">Configure your local environment</span></span>

<span data-ttu-id="1b0b9-110">使用 Docker for Windows 的最新版本 ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/))，簡單的安裝程式可讓您輕鬆地開發 Docker 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-110">With the latest versions of Docker for Windows ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)), the straightforward setup makes it easy to develop Docker applications.</span></span>

<span data-ttu-id="1b0b9-111">在 Visual Studio 2017 包含 docker 支援。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-111">Docker support is included in Visual Studio 2017.</span></span> <span data-ttu-id="1b0b9-112">從這裡下載 Visual Studio 2017: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span><span class="sxs-lookup"><span data-stu-id="1b0b9-112">Download Visual Studio 2017 here: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span></span>

## <a name="use-docker-tools-in-visual-studio-2017"></a><span data-ttu-id="1b0b9-113">Visual Studio 2017 中使用 Docker 工具</span><span class="sxs-lookup"><span data-stu-id="1b0b9-113">Use Docker Tools in Visual Studio 2017</span></span>

<span data-ttu-id="1b0b9-114">有兩種您可以新增至專案的 Docker 支援層級。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-114">There are two levels of Docker support you can add to a project.</span></span> <span data-ttu-id="1b0b9-115">在.NET Core web 應用程式專案中，您就可以新增*Dockerfile*專案啟用 Docker 支援的檔案。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-115">In .NET Core web app projects, you can just add a *Dockerfile* file to the project by enabling Docker support.</span></span> <span data-ttu-id="1b0b9-116">下一個層級是容器協調流程支援，這會新增*Dockerfile*至專案 （如果它尚未存在） 並*docker compose.yml*方案層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-116">The next level is container orchestration support, which adds a *Dockerfile* to the project (if it doesn't already exist) and a *docker-compose.yml* file at the solution level.</span></span> <span data-ttu-id="1b0b9-117">新增容器協調流程支援，透過 Docker Compose，預設會在 Visual Studio 2017 版本 15.7 或更早版本。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-117">Container orchestration support, via Docker Compose, is added by default in Visual Studio 2017 versions 15.7 or earlier.</span></span> <span data-ttu-id="1b0b9-118">容器協調流程的支援是在 Visual Studio 2017 版本 15.8 選擇加入的功能或更新版本中，在此情況下 Docker Compose 與 Service Fabric 支援。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-118">Container orchestration support is an opt-in feature in Visual Studio 2017 versions 15.8 or later, in which case Docker Compose and Service Fabric are supported.</span></span>

<span data-ttu-id="1b0b9-119">**新增** > **Docker 支援**並**新增** > **容器協調流程支援**命令在 web 應用程式專案的專案節點的右鍵操作功能表 （或操作功能表） 位於**方案總管 中**所示，在圖 4-26:</span><span class="sxs-lookup"><span data-stu-id="1b0b9-119">The **Add** > **Docker Support** and **Add** > **Container orchestration Support** commands are located on the right-click menu (or context menu) of the project node for a web app project in **Solution Explorer**, as shown in Figure 4-26:</span></span>

![在 Visual Studio 中新增 Docker 支援 功能表選項](media/add-docker-support-menu.png)

<span data-ttu-id="1b0b9-121">圖 4-26： 新增 Docker 支援新增至 Visual Studio 2017 的專案</span><span class="sxs-lookup"><span data-stu-id="1b0b9-121">Figure 4-26: Adding Docker support to a Visual Studio 2017 project</span></span>

### <a name="add-docker-support"></a><span data-ttu-id="1b0b9-122">新增 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="1b0b9-122">Add Docker support</span></span>

<span data-ttu-id="1b0b9-123">您也可以選取現有的.NET Core web 應用程式專案新增 Docker 支援**新增** > **Docker 支援**中**方案總管 中**。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-123">You can add Docker support to an existing .NET Core web app project by selecting **Add** > **Docker Support** in **Solution Explorer**.</span></span> <span data-ttu-id="1b0b9-124">您也可以啟用 Docker 支援在專案建立期間選取**啟用 Docker 支援**中**新的 ASP.NET Core Web 應用程式**按一下之後開啟的對話方塊 **[確定]** 中**新的專案**對話方塊中，顯示在圖 4-27。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-124">You can also enable Docker support during project creation by selecting **Enable Docker Support** in the **New ASP.NET Core Web Application** dialog box that opens after you click **OK** in the **New Project** dialog box, as shown in Figure 4-27.</span></span>

![Visual Studio 中的新 ASP.NET Core web 應用程式中啟用 Docker 支援](./media/enable-docker-support-visual-studio.png)

<span data-ttu-id="1b0b9-126">圖 4-27： 在 Visual Studio 2017 中的專案建立期間啟用 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="1b0b9-126">Figure 4-27: Enable Docker support during project creation in Visual Studio 2017</span></span>

<span data-ttu-id="1b0b9-127">當您新增或啟用 Docker 支援時，Visual Studio 會加入*Dockerfile*檔案加入專案。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-127">When you add or enable Docker support, Visual Studio adds a *Dockerfile* file to the project.</span></span>

> [!NOTE]
> <span data-ttu-id="1b0b9-128">圖 4-28 示，您可以啟用.NET Framework web 應用程式專案 （非.NET Core web 應用程式專案） 的專案建立期間的 Docker Compose 的支援，也會加入容器協調流程支援。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-128">When you enable Docker Compose support during project creation for a .NET Framework web app project (not a .NET Core web app project) as shown in Figure 4-28, container orchestration support is also added.</span></span>
>
> ![啟用 Docker compose 的.NET Framework web 應用程式專案的支援](media/enable-docker-compose-support.png)

> <span data-ttu-id="1b0b9-130">圖 4-28： 啟用 Visual Studio 2017 中的.NET Framework web 應用程式專案上的 Docker Compose 的支援</span><span class="sxs-lookup"><span data-stu-id="1b0b9-130">Figure 4-28: Enabling Docker Compose support on a .NET Framework web app project in Visual Studio 2017</span></span>

### <a name="add-container-orchestration-support"></a><span data-ttu-id="1b0b9-131">新增容器協調流程的支援</span><span class="sxs-lookup"><span data-stu-id="1b0b9-131">Add container orchestration support</span></span>

<span data-ttu-id="1b0b9-132">當您想要撰寫多容器解決方案時，將容器協調流程支援新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-132">When you want to compose a multicontainer solution, add container orchestration support to your projects.</span></span> <span data-ttu-id="1b0b9-133">這可讓您執行，並同時在偵錯容器 （整個解決方案） 的群組，如果它們定義在相同*docker compose.yml*檔案。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-133">This lets you run and debug a group of containers (a whole solution) at the same time if they're defined in the same *docker-compose.yml* file.</span></span>

<span data-ttu-id="1b0b9-134">若要新增容器協調流程的支援，請以滑鼠右鍵按一下的方案或專案節點上**方案總管 中**，然後選擇**新增** > **容器協調流程支援**.</span><span class="sxs-lookup"><span data-stu-id="1b0b9-134">To add container orchestration support, right-click on the solution or project node in **Solution Explorer**, and choose **Add** > **Container Orchestration Support**.</span></span> <span data-ttu-id="1b0b9-135">然後選擇**Docker Compose**或是**Service Fabric**管理容器。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-135">Then choose **Docker Compose** or **Service Fabric** to manage the containers.</span></span>

<span data-ttu-id="1b0b9-136">容器協調流程的支援加入專案之後，您會看到新增至專案的 Dockerfile 並**docker compose**加入至方案中的資料夾**方案總管 中**所示，在圖 4-29:</span><span class="sxs-lookup"><span data-stu-id="1b0b9-136">After you add container orchestration support to your project, you see a Dockerfile added to the project and a **docker-compose** folder added to the solution in **Solution Explorer**, as shown in Figure 4-29:</span></span>

![在 Visual Studio 中的 [方案總管] 中的 docker 檔案](media/docker-support-solution-explorer.png)

<span data-ttu-id="1b0b9-138">圖 4-29： 在 Visual Studio 2017 中的 [方案總管] 中的 Docker 檔案</span><span class="sxs-lookup"><span data-stu-id="1b0b9-138">Figure 4-29: Docker files in Solution Explorer in Visual Studio 2017</span></span>

<span data-ttu-id="1b0b9-139">如果*docker compose.yml*已經存在，Visual Studio 只會將必要的組態程式碼的行加入至它。</span><span class="sxs-lookup"><span data-stu-id="1b0b9-139">If *docker-compose.yml* already exists, Visual Studio just adds the required lines of configuration code to it.</span></span>

<span data-ttu-id="1b0b9-140">**更多資訊：** 如需詳細的服務實作和使用 Visual Studio Tools for Docker，請閱讀下列文章：</span><span class="sxs-lookup"><span data-stu-id="1b0b9-140">**More information:** For further details on the services implementation and use of Visual Studio Tools for Docker, read the following articles:</span></span>

<span data-ttu-id="1b0b9-141">建置、 偵錯、 更新和重新整理本機 Docker 容器中的應用程式： [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="1b0b9-141">Build, debug, update, and refresh apps in a local Docker container: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

<span data-ttu-id="1b0b9-142">將 ASP.NET Core Docker 容器部署至容器登錄： [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="1b0b9-142">Deploy an ASP.NET Core Docker container to a container registry: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="1b0b9-143">[上一頁](docker-apps-inner-loop-workflow.md)
[下一頁](set-up-windows-containers-with-powershell.md)</span><span class="sxs-lookup"><span data-stu-id="1b0b9-143">[Previous](docker-apps-inner-loop-workflow.md)
[Next](set-up-windows-containers-with-powershell.md)</span></span>