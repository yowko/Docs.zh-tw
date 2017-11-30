---
title: "使用 Visual Studio Tools for Docker (在 Windows 上的 Visual Studio)"
description: "Microsoft 平台和工具與 Docker 容器化應用程式生命週期"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: d7a24633f5857bc5b72ebab42020627c645f4302
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2017
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a><span data-ttu-id="5e84d-104">使用 Visual Studio Tools for Docker (在 Windows 上的 Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="5e84d-104">Using Visual Studio Tools for Docker (Visual Studio on Windows)</span></span>

<span data-ttu-id="5e84d-105">開發人員工作流程時使用 Visual Studio Tools for Docker 時，才能與工作流程類似使用 Visual Studio 程式碼和 Docker CLI （事實上，它根據相同的 Docker CLI），但您更輕鬆地開始使用、 可簡化程序，並提供更高組建的產能執行，而且組成的工作。</span><span class="sxs-lookup"><span data-stu-id="5e84d-105">The developer workflow when using Visual Studio Tools for Docker is similar to the workflow when using Visual Studio Code and Docker CLI (in fact, it is based on the same Docker CLI), but it is easier to get started, simplifies the process, and provides greater productivity for the build, run, and compose tasks.</span></span> <span data-ttu-id="5e84d-106">它也會執行並偵錯您的容器，透過簡單的動作，如 F5 和 Ctrl + F5 從 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="5e84d-106">It's also able to execute and debug your containers via simple actions like F5 and Ctrl+F5 from Visual Studio.</span></span> <span data-ttu-id="5e84d-107">更，與 Visual Studio 2017，除了執行和偵錯單一容器中，您也可以執行和偵錯的容器 （整個方案） 的群組同時如果方案層級相同的 docker compose.yml 檔案中定義。</span><span class="sxs-lookup"><span data-stu-id="5e84d-107">Even more, with Visual Studio 2017, in addition to being able to run and debug a single container, you also can run and debug a group of containers (a whole solution) at the same time if they are defined in the same docker-compose.yml file at the solution level.</span></span>

## <a name="configuring-your-local-environment"></a><span data-ttu-id="5e84d-108">設定您的本機環境</span><span class="sxs-lookup"><span data-stu-id="5e84d-108">Configuring your local environment</span></span>

<span data-ttu-id="5e84d-109">Docker for Windows 的最新版本，它就能夠更輕鬆比曾經來開發 Docker 應用程式因為下列參考中所述，很簡單，安裝程式。</span><span class="sxs-lookup"><span data-stu-id="5e84d-109">With the latest versions of Docker for Windows, it is easier than ever to develop Docker applications because the setup is straightforward, as explained in the following references.</span></span>

<span data-ttu-id="5e84d-110">**更多資訊：** 若要了解安裝 Docker for Windows 的詳細資訊，請移至<https://docs.docker.com/docker-for-windows/>。</span><span class="sxs-lookup"><span data-stu-id="5e84d-110">**More info:** To learn more about installing Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>

<span data-ttu-id="5e84d-111">如果您使用 Visual Studio 2015，您必須更新 3 或更新版本以及 Visual Studio Tools for Docker。</span><span class="sxs-lookup"><span data-stu-id="5e84d-111">If you're using Visual Studio 2015, you must have Update 3 or a later version plus the Visual Studio Tools for Docker.</span></span>

<span data-ttu-id="5e84d-112">**更多資訊：** 如需安裝 Visual Studio 的指示，請移至[https://www.visualstudio.com/ \ 產品/vs-2015年-產品-版本](https://www.visualstudio.com/products/vs-2015-product-editions)。</span><span class="sxs-lookup"><span data-stu-id="5e84d-112">**More info:** For instructions on installing Visual Studio, go to [https://www.visualstudio.com/\ products/vs-2015-product-editions](https://www.visualstudio.com/products/vs-2015-product-editions).</span></span>

<span data-ttu-id="5e84d-113">若要查看安裝 Visual Studio Tools for Docker 的詳細資訊，請移至<http://aka.ms/vstoolsfordocker>和<https://docs.microsoft.com/dotnet/articles/core/docker/visual-studio-tools-for-docker>.</span><span class="sxs-lookup"><span data-stu-id="5e84d-113">To see more about installing Visual Studio Tools for Docker, go to <http://aka.ms/vstoolsfordocker> and <https://docs.microsoft.com/dotnet/articles/core/docker/visual-studio-tools-for-docker>.</span></span>

<span data-ttu-id="5e84d-114">如果您使用 Visual Studio 2017，已經包含 Docker 的支援。</span><span class="sxs-lookup"><span data-stu-id="5e84d-114">If you're using Visual Studio 2017, Docker support is already included.</span></span>

## <a name="using-docker-tools-in-visual-studio-2015"></a><span data-ttu-id="5e84d-115">使用 Visual Studio 2015 中的 Docker 工具</span><span class="sxs-lookup"><span data-stu-id="5e84d-115">Using Docker Tools in Visual Studio 2015</span></span>

<span data-ttu-id="5e84d-116">Visual Studio Tools for Docker 會提供一致的方式開發，並在本機驗證 Docker 容器適用於 Linux 的 Linux Docker 主機或 VM 或您直接在 Windows 上的 Windows 容器中。</span><span class="sxs-lookup"><span data-stu-id="5e84d-116">The Visual Studio Tools for Docker provides a consistent way to develop and validate locally your Docker containers for Linux in a Linux Docker host or VM, or your Windows Containers directly on Windows.</span></span>

<span data-ttu-id="5e84d-117">如果您使用單一的容器，您需要開始第一件事就是開啟 Docker 支援到.NET Core 專案。</span><span class="sxs-lookup"><span data-stu-id="5e84d-117">If you're using a single container, the first thing you need to begin is to turn on Docker support into your .NET Core project.</span></span> <span data-ttu-id="5e84d-118">若要這樣做，以滑鼠右鍵按一下專案檔，如圖 4-25 所示。</span><span class="sxs-lookup"><span data-stu-id="5e84d-118">To do this, right-click your project file, as shown in Figure 4-25.</span></span>

![https://i1.visualstudiogallery.msdn.s-msft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4/image/file/205468/1/add-docker-support.png](./media/image31.png)

<span data-ttu-id="5e84d-120">圖 4-25： 開啟 Visual Studio 專案的 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="5e84d-120">Figure 4-25: Turning on Docker support for your Visual Studio project</span></span>

## <a name="using-docker-tools-in-visual-studio-2017"></a><span data-ttu-id="5e84d-121">在 Visual Studio 2017 使用 Docker 工具</span><span class="sxs-lookup"><span data-stu-id="5e84d-121">Using Docker Tools in Visual Studio 2017</span></span>

<span data-ttu-id="5e84d-122">當您將 Docker 的支援加入服務專案方案中 （請參閱圖 4-26），Visual Studio 會不只 DockerFile 檔案加入您的專案，它也服務區段中加入您的方案 docker compose.yml 檔案 （或建立檔案，如果他們未存在）。</span><span class="sxs-lookup"><span data-stu-id="5e84d-122">When you add Docker support to a service project in your solution (see Figure 4-26), Visual Studio is not just adding a DockerFile file to your project, it also is adding a service section in your solution's docker-compose.yml files (or creating the files if they didn't exist).</span></span> <span data-ttu-id="5e84d-123">這是簡單的方法，若要開始撰寫 multicontainer 方案;您可以開啟 docker compose.yml 檔案，然後其他功能用來更新這些。</span><span class="sxs-lookup"><span data-stu-id="5e84d-123">It's an easy way to begin composing your multicontainer solution; you then can open the docker-compose.yml files and update them with additional features.</span></span>

![](./media/image32.png)

<span data-ttu-id="5e84d-124">圖 4-26： 開啟 Docker 方案在 Visual Studio 2017 專案中的支援</span><span class="sxs-lookup"><span data-stu-id="5e84d-124">Figure 4-26: Turning on Docker Solution support in a Visual Studio 2017 project</span></span>

<span data-ttu-id="5e84d-125">這個動作不只會將 DockerFile 至您的專案，它也會將必要的組態程式碼加入方案層級設定全域 docker compose.yml。</span><span class="sxs-lookup"><span data-stu-id="5e84d-125">This action not only adds the DockerFile to your project, it also adds the required configuration lines of code to a global docker-compose.yml set at the solution level.</span></span>

<span data-ttu-id="5e84d-126">您也可以開啟 Docker 支援時建立的 ASP.NET Core 專案在 Visual Studio 2017，如圖 4-27 所示。</span><span class="sxs-lookup"><span data-stu-id="5e84d-126">You also can turn on Docker support when creating an ASP.NET Core project in Visual Studio 2017, as shown in Figure 4-27.</span></span>

![](./media/image33.png)

<span data-ttu-id="5e84d-127">建立專案時，Docker 支援開啟圖 4-27:</span><span class="sxs-lookup"><span data-stu-id="5e84d-127">Figure 4-27: Turning on Docker support when creating a project</span></span>

<span data-ttu-id="5e84d-128">在 Visual Studio 方案中加入 Docker 支援之後，您也會看到新節點樹狀，在 [方案總管] 新增的 docker compose.yml 檔案時，如上圖 4-28。</span><span class="sxs-lookup"><span data-stu-id="5e84d-128">After you add Docker support to your solution in Visual Studio, you also will see a new node tree in Solution Explorer with the added docker-compose.yml files, as depicted in Figure 4-28.</span></span>

![](./media/image34.PNG)

<span data-ttu-id="5e84d-129">圖 4-28: docker compose.yml 檔案現在會顯示在 方案總管</span><span class="sxs-lookup"><span data-stu-id="5e84d-129">Figure 4-28: docker-compose.yml files now display in Solution Explorer</span></span>

<span data-ttu-id="5e84d-130">您可以部署 multicontainer 應用程式使用單一的 docker compose.yml 檔案，當您執行 docker-撰寫組成;不過，Visual Studio 將群組加入項目，因此您可以覆寫值取決於環境 （與實際執行的程式開發） 和執行類型 （與偵錯版本）。</span><span class="sxs-lookup"><span data-stu-id="5e84d-130">You could deploy a multicontainer application by using a single docker-compose.yml file when you run docker-compose up; however, Visual Studio adds a group of them, so you can override values depending on the environment (development versus production) and the execution type (release versus debug).</span></span> <span data-ttu-id="5e84d-131">這項功能將進一步說明，在後續章節。</span><span class="sxs-lookup"><span data-stu-id="5e84d-131">This capability will be better explained in later chapters.</span></span>

<span data-ttu-id="5e84d-132">**更多資訊：** 如需詳細資訊的服務實作和使用 Visual Studio Tools for Docker，請閱讀下列文章：</span><span class="sxs-lookup"><span data-stu-id="5e84d-132">**More info:** For further details on the services implementation and use of Visual Studio Tools for Docker, read the following articles:</span></span>

<span data-ttu-id="5e84d-133">建置、 偵錯、 更新和重新整理本機的 Docker 容器中的應用程式： [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="5e84d-133">Build, debug, update, and refresh apps in a local Docker container: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

<span data-ttu-id="5e84d-134">部署至遠端 Docker 主機 ASP.NET 容器： [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="5e84d-134">Deploy an ASP.NET container to a remote Docker host: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="5e84d-135">[上一個](docker-應用程式-內部-迴圈-workflow.md) [下一步] (set-up-windows-containers-with-powershell.md)</span><span class="sxs-lookup"><span data-stu-id="5e84d-135">[Previous] (docker-apps-inner-loop-workflow.md) [Next] (set-up-windows-containers-with-powershell.md)</span></span>
