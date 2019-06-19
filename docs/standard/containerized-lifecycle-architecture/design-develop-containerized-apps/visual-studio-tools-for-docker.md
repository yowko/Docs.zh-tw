---
title: Windows 上的 Visual Studio Tools for Docker
description: 了解 Visual Studio 2017 15.7 版和更新版本中可用的 Docker 工具。
ms.date: 02/15/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 2b6fdc33f9cf850cf9e52fca4a1a9754cd412567
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644668"
---
# <a name="use-docker-tools-in-visual-studio-2017-on-windows"></a><span data-ttu-id="718a6-103">在 Windows 上使用 Visual Studio 2017 中的 Docker 工具</span><span class="sxs-lookup"><span data-stu-id="718a6-103">Use Docker Tools in Visual Studio 2017 on Windows</span></span>

<span data-ttu-id="718a6-104">使用 Docker 工具時包含在 Visual Studio 2017 15.7 版和更新版本中的開發人員工作流程，類似於使用 Visual Studio Code 和 Docker CLI (事實上，它是以相同的 Docker CLI 為基礎)，但它可以更輕鬆地開始使用、簡化此處理序，以及針對建置、執行和撰寫工作提供更高的生產力。</span><span class="sxs-lookup"><span data-stu-id="718a6-104">The developer workflow when using the Docker Tools included in Visual Studio 2017 version 15.7 and later, is similar to using Visual Studio Code and Docker CLI (in fact, it's based on the same Docker CLI), but it's easier to get started, simplifies the process, and provides greater productivity for the build, run, and compose tasks.</span></span> <span data-ttu-id="718a6-105">它也可以從 Visual Studio 透過常用的 `F5` 和 `Ctrl+F5` 按鍵執行容器並對其進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="718a6-105">It can also run and debug your containers via the usual `F5` and `Ctrl+F5` keys from Visual Studio.</span></span> <span data-ttu-id="718a6-106">如果其容器是在解決方案層級的同一個 `docker-compose.yml` 檔案中定義，您甚至可以對整個解決方案進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="718a6-106">You can even debug a whole solution if its containers are defined in the same `docker-compose.yml` file at the solution level.</span></span>

## <a name="configure-your-local-environment"></a><span data-ttu-id="718a6-107">設定您的本機環境</span><span class="sxs-lookup"><span data-stu-id="718a6-107">Configure your local environment</span></span>

<span data-ttu-id="718a6-108">使用適用於 Windows 的最新版本 Docker 時，因為設定非常簡單，所以開發 Docker 應用程式比以往更加容易，如下列參考中所述。</span><span class="sxs-lookup"><span data-stu-id="718a6-108">With the latest versions of Docker for Windows, it's easier than ever to develop Docker applications because the setup is straightforward, as explained in the following references.</span></span>

> [!TIP]
> <span data-ttu-id="718a6-109">若要深入了解如何安裝適用於 Windows 的 Docker，請前往 (<https://docs.docker.com/docker-for-windows/>)。</span><span class="sxs-lookup"><span data-stu-id="718a6-109">To learn more about installing Docker for Windows, go to (<https://docs.docker.com/docker-for-windows/>).</span></span>

## <a name="docker-support-in-visual-studio-2017"></a><span data-ttu-id="718a6-110">Visual Studio 2017 中的 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="718a6-110">Docker support in Visual Studio 2017</span></span>

<span data-ttu-id="718a6-111">您可以將兩種 Docker 支援層級新增至專案。</span><span class="sxs-lookup"><span data-stu-id="718a6-111">There are two levels of Docker support you can add to a project.</span></span> <span data-ttu-id="718a6-112">在 ASP.NET Core 專案中，您可以啟用 Docker 支援，只將 `Dockerfile` 檔案新增至專案。</span><span class="sxs-lookup"><span data-stu-id="718a6-112">In ASP.NET Core projects, you can just add a `Dockerfile` file to the project by enabling Docker support.</span></span> <span data-ttu-id="718a6-113">下一個層級是容器協調流程支援，這會將 `Dockerfile` 新增至專案 (如果它尚未存在) 和解決方案層級的 `docker-compose.yml` 檔案。</span><span class="sxs-lookup"><span data-stu-id="718a6-113">The next level is container orchestration support, which adds a `Dockerfile` to the project (if it doesn't already exist) and a `docker-compose.yml` file at the solution level.</span></span> <span data-ttu-id="718a6-114">預設會透過 Docker Compose 在 Visual Studio 2017 15.0 版至 15.7 版中新增容器協調流程支援。</span><span class="sxs-lookup"><span data-stu-id="718a6-114">Container orchestration support, via Docker Compose, is added by default in Visual Studio 2017 versions 15.0 to 15.7.</span></span> <span data-ttu-id="718a6-115">容器協調流程支援是 Visual Studio 2017 15.8 版或更新版本中的選擇性功能。</span><span class="sxs-lookup"><span data-stu-id="718a6-115">Container orchestration support is an opt-in feature in Visual Studio 2017 versions 15.8 or later.</span></span> <span data-ttu-id="718a6-116">15.8 版和更新版本支援 Docker Compose 與 Service Fabric。</span><span class="sxs-lookup"><span data-stu-id="718a6-116">Version 15.8 an later support Docker Compose and Service Fabric.</span></span>

<span data-ttu-id="718a6-117">[新增] > [Docker 支援]  和 [新增] > [容器協調器支援]  命令位於 [方案總管]  中 ASP.NET Core 專案的專案節點右鍵功能表 (或操作功能表) 上，如圖 4-31 所示：</span><span class="sxs-lookup"><span data-stu-id="718a6-117">The **Add > Docker Support** and **Add > Container Orchestrator Support** commands are located on the right-click menu (or context menu) of the project node for an ASP.NET Core project in **Solution Explorer**, as shown in Figure 4-31:</span></span>

![Visual Studio 中的 [新增 Docker 支援] 功能表選項](./media/add-docker-support-menu.png)

<span data-ttu-id="718a6-119">**圖 4-31**。</span><span class="sxs-lookup"><span data-stu-id="718a6-119">**Figure 4-31**.</span></span> <span data-ttu-id="718a6-120">將 Docker 支援新增至 Visual Studio 2017 專案</span><span class="sxs-lookup"><span data-stu-id="718a6-120">Adding Docker support to a Visual Studio 2017 project</span></span>

### <a name="add-docker-support"></a><span data-ttu-id="718a6-121">新增 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="718a6-121">Add Docker support</span></span>

<span data-ttu-id="718a6-122">您可以透過在 [方案總管]  中選取 [新增]   > [Docker 支援]  ，為現有的 ASP.NET Core 專案新增 Docker 支援。</span><span class="sxs-lookup"><span data-stu-id="718a6-122">You can add Docker support to an existing ASP.NET Core project by selecting **Add** > **Docker Support** in **Solution Explorer**.</span></span> <span data-ttu-id="718a6-123">您也可以在專案建立期間啟用 Docker 支援，方法是在按一下 [新增專案]  對話方塊的 [確定]  之後開啟的 [新增 ASP.NET Core Web 應用程式]  對話方塊中選取 [啟用 Docker 支援]  ，如圖 4-32 所示。</span><span class="sxs-lookup"><span data-stu-id="718a6-123">You can also enable Docker support during project creation by selecting **Enable Docker Support** in the **New ASP.NET Core Web Application** dialog box that opens after you click **OK** in the **New Project** dialog box, as shown in Figure 4-32.</span></span>

![在 Visual Studio 中為新的 ASP.NET Core Web 應用程式啟用 Docker 支援](./media/enable-docker-support-visual-studio.png)

<span data-ttu-id="718a6-125">**圖 4-32**。</span><span class="sxs-lookup"><span data-stu-id="718a6-125">**Figure 4-32**.</span></span> <span data-ttu-id="718a6-126">在 Visual Studio 2017 中於專案建立期間啟用 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="718a6-126">Enable Docker support during project creation in Visual Studio 2017</span></span>

<span data-ttu-id="718a6-127">當您新增或啟用 Docker 支援時，Visual Studio 會將 *Dockerfile* 檔案新增至專案中。</span><span class="sxs-lookup"><span data-stu-id="718a6-127">When you add or enable Docker support, Visual Studio adds a *Dockerfile* file to the project.</span></span>

> [!NOTE]
> <span data-ttu-id="718a6-128">在專案建立期間為 ASP.NET 專案 (.NET Framework，而不是 .NET Core 專案) 啟用 Docker Compose 支援時，也會新增容器協調流程支援，如圖 4-33 所示。</span><span class="sxs-lookup"><span data-stu-id="718a6-128">When you enable Docker Compose support during project creation for a ASP.NET project (.NET Framework, not a .NET Core project) as shown in Figure 4-33, container orchestration support is also added.</span></span>

![針對 ASP.NET 專案啟用 Docker Compose 支援](media/enable-docker-compose-support.png)

<span data-ttu-id="718a6-130">**圖 4-33**。</span><span class="sxs-lookup"><span data-stu-id="718a6-130">**Figure 4-33**.</span></span> <span data-ttu-id="718a6-131">在 Visual Studio 2017 中針對 ASP.NET 專案啟用 Docker Compose 支援</span><span class="sxs-lookup"><span data-stu-id="718a6-131">Enabling Docker Compose support for an ASP.NET project in Visual Studio 2017</span></span>

### <a name="add-container-orchestration-support"></a><span data-ttu-id="718a6-132">新增容器協調流程支援</span><span class="sxs-lookup"><span data-stu-id="718a6-132">Add container orchestration support</span></span>

<span data-ttu-id="718a6-133">若要撰寫多容器解決方案，請將容器協調流程支援新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="718a6-133">When you want to compose a multi-container solution, add container orchestration support to your projects.</span></span> <span data-ttu-id="718a6-134">如果它們在同一個 *docker-compose.yml* 文件中定義，則允許您同時執行一組容器 (整個解決方案) 並對其進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="718a6-134">This lets you run and debug a group of containers (a whole solution) at the same time if they're defined in the same *docker-compose.yml* file.</span></span>

<span data-ttu-id="718a6-135">若要新增容器協調流程支援，請以滑鼠右鍵按一下 [方案總管]  中的解決方案或專案節點，然後選擇 [新增] > [容器協調流程支援]  。</span><span class="sxs-lookup"><span data-stu-id="718a6-135">To add container orchestration support, right-click on the solution or project node in **Solution Explorer**, and choose **Add > Container Orchestration Support**.</span></span> <span data-ttu-id="718a6-136">然後選擇 [Docker Compose]  或 [Service Fabric]  來管理容器。</span><span class="sxs-lookup"><span data-stu-id="718a6-136">Then choose **Docker Compose** or **Service Fabric** to manage the containers.</span></span>

<span data-ttu-id="718a6-137">向專案新增容器協調流程支援後，您會看到專案中新增了 Dockerfile，且 [方案總管]  中的解決方案新增了 **docker-compose** 資料夾，如圖 4-34 所示：</span><span class="sxs-lookup"><span data-stu-id="718a6-137">After you add container orchestration support to your project, you see a Dockerfile added to the project and a **docker-compose** folder added to the solution in **Solution Explorer**, as shown in Figure 4-34:</span></span>

![Visual Studio 中 [方案總管] 中的 Docker 檔案](media/docker-support-solution-explorer.png)

<span data-ttu-id="718a6-139">**圖 4-34**.</span><span class="sxs-lookup"><span data-stu-id="718a6-139">**Figure 4-34**.</span></span> <span data-ttu-id="718a6-140">Visual Studio 2017 [方案總管] 中的 Docker 檔案</span><span class="sxs-lookup"><span data-stu-id="718a6-140">Docker files in Solution Explorer in Visual Studio 2017</span></span>

<span data-ttu-id="718a6-141">如果 *docker-compose.yml* 已存在，則 Visual Studio 只會向其新增所需的組態程式碼行。</span><span class="sxs-lookup"><span data-stu-id="718a6-141">If *docker-compose.yml* already exists, Visual Studio just adds the required lines of configuration code to it.</span></span>

## <a name="configure-docker-tools"></a><span data-ttu-id="718a6-142">設定 Docker 工具</span><span class="sxs-lookup"><span data-stu-id="718a6-142">Configure Docker tools</span></span>

<span data-ttu-id="718a6-143">從主功能表中，選擇 [工具] > [選項]  ，並展開 [容器工具] > [設定]  。</span><span class="sxs-lookup"><span data-stu-id="718a6-143">From the main menu, choose **Tools > Options**, and expand **Container Tools > Settings**.</span></span> <span data-ttu-id="718a6-144">容器工具設定隨即出現。</span><span class="sxs-lookup"><span data-stu-id="718a6-144">The container tools settings appear.</span></span>

![Visual Studio Docker 工具選項，其中顯示：自動在專案載入時提取所需的 Docker 映像、自動在背景中啟動容器、自動在解決方案關閉時終止容器，以及不要提示信任 SSL 憑證。](./media/visual-studio-docker-tools-options.png)

<span data-ttu-id="718a6-146">**圖 4-35**.</span><span class="sxs-lookup"><span data-stu-id="718a6-146">**Figure 4-35**.</span></span> <span data-ttu-id="718a6-147">Docker 工具選項</span><span class="sxs-lookup"><span data-stu-id="718a6-147">Docker Tools Options</span></span>

<span data-ttu-id="718a6-148">下表可協助您決定如何設定這些選項。</span><span class="sxs-lookup"><span data-stu-id="718a6-148">The following table might help you decide how to set these options.</span></span>

| <span data-ttu-id="718a6-149">名稱</span><span class="sxs-lookup"><span data-stu-id="718a6-149">Name</span></span> | <span data-ttu-id="718a6-150">預設設定</span><span class="sxs-lookup"><span data-stu-id="718a6-150">Default Setting</span></span> | <span data-ttu-id="718a6-151">適用於</span><span class="sxs-lookup"><span data-stu-id="718a6-151">Applies To</span></span> | <span data-ttu-id="718a6-152">說明</span><span class="sxs-lookup"><span data-stu-id="718a6-152">Description</span></span> |
| -----|:---------------:|:----------:| ----------- |
| <span data-ttu-id="718a6-153">自動在專案載入時提取所需的 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="718a6-153">Automatically pull required Docker images on project load</span></span> | <span data-ttu-id="718a6-154">開啟</span><span class="sxs-lookup"><span data-stu-id="718a6-154">On</span></span> | <span data-ttu-id="718a6-155">Docker Compose</span><span class="sxs-lookup"><span data-stu-id="718a6-155">Docker Compose</span></span> | <span data-ttu-id="718a6-156">為了提高載入專案時的效能，Visual Studio 會在背景中啟動 Docker 提取作業，因此當您準備好要執行程式碼時，映像已下載或正在下載中。</span><span class="sxs-lookup"><span data-stu-id="718a6-156">For increased performance when loading projects, Visual Studio will start a Docker pull operation in the background so that when you're ready to run your code, the image is already downloaded or in the process of downloading.</span></span> <span data-ttu-id="718a6-157">如果您只要載入專案並瀏覽程式碼，則可以關閉這項功能，避免下載您不需要的容器映像。</span><span class="sxs-lookup"><span data-stu-id="718a6-157">If you're just loading projects and browsing code, you can turn this off to avoid downloading container images you don't need.</span></span> |
| <span data-ttu-id="718a6-158">自動在背景中啟動容器</span><span class="sxs-lookup"><span data-stu-id="718a6-158">Automatically start containers in background</span></span> | <span data-ttu-id="718a6-159">開啟</span><span class="sxs-lookup"><span data-stu-id="718a6-159">On</span></span> | <span data-ttu-id="718a6-160">Docker Compose</span><span class="sxs-lookup"><span data-stu-id="718a6-160">Docker Compose</span></span> | <span data-ttu-id="718a6-161">同樣為了提高效能，Visual Studio 會在您建置並執行容器時建立一個容器，內含準備好可供使用的磁碟區裝載。</span><span class="sxs-lookup"><span data-stu-id="718a6-161">Again for increased performance, Visual Studio creates a container with volume mounts ready for when you build and run your container.</span></span> <span data-ttu-id="718a6-162">如果您想要控制何時建立容器，請關閉這項功能。</span><span class="sxs-lookup"><span data-stu-id="718a6-162">If you want to control when your container is created, turn this off.</span></span> |
| <span data-ttu-id="718a6-163">自動在解決方案關閉時終止容器</span><span class="sxs-lookup"><span data-stu-id="718a6-163">Automatically kill containers on solution close</span></span> | <span data-ttu-id="718a6-164">開啟</span><span class="sxs-lookup"><span data-stu-id="718a6-164">On</span></span> | <span data-ttu-id="718a6-165">Docker Compose</span><span class="sxs-lookup"><span data-stu-id="718a6-165">Docker Compose</span></span> | <span data-ttu-id="718a6-166">如果您希望解決方案的容器在關閉解決方案或關閉 Visual Studio 之後繼續執行，請關閉這項功能。</span><span class="sxs-lookup"><span data-stu-id="718a6-166">Turn this off if you would like containers for your solution to continue to run after closing the solution or closing Visual Studio.</span></span> |
| <span data-ttu-id="718a6-167">不要提示信任 localhost SSL 憑證</span><span class="sxs-lookup"><span data-stu-id="718a6-167">Do not prompt for trusting localhost SSL certificate</span></span> | <span data-ttu-id="718a6-168">Off</span><span class="sxs-lookup"><span data-stu-id="718a6-168">Off</span></span> | <span data-ttu-id="718a6-169">ASP.NET Core 2.2 專案</span><span class="sxs-lookup"><span data-stu-id="718a6-169">ASP.NET Core 2.2 projects</span></span> | <span data-ttu-id="718a6-170">如果 localhost SSL 憑證不受信任，則除非核取此核取方塊，否則每次執行專案時 Visual Studio 都會提示。</span><span class="sxs-lookup"><span data-stu-id="718a6-170">If the localhost SSL certificate is not trusted, Visual Studio will prompt every time you run your project, unless this checkbox is checked.</span></span> |

> [!WARNING]
> <span data-ttu-id="718a6-171">如果 localhost SSL 憑證不受信任，且您核取隱藏提示的方塊，則 HTTPS Web 要求可能會在應用程式或服務的執行階段失敗。</span><span class="sxs-lookup"><span data-stu-id="718a6-171">If the localhost SSL certificate is not trusted, and you check the box to suppress prompting, then HTTPS web requests might fail at runtime in your app or service.</span></span> <span data-ttu-id="718a6-172">在此情況下，請取消核取 [不要提示]  核取方塊，執行您的專案，並在提示時表示信任。</span><span class="sxs-lookup"><span data-stu-id="718a6-172">In that case, uncheck the **Do not prompt** checkbox, run your project, and indicate trust at the prompt.</span></span>

> [!TIP]
> <span data-ttu-id="718a6-173">如需服務實作和使用 Visual Studio Tools for Docker 的進一步詳細資料，請閱讀下列文章：</span><span class="sxs-lookup"><span data-stu-id="718a6-173">For further details on the services implementation and use of Visual Studio Tools for Docker, read the following articles:</span></span>
>
><span data-ttu-id="718a6-174">對本機 Docker 容器中的應用程式進行偵錯：<https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh></span><span class="sxs-lookup"><span data-stu-id="718a6-174">Debugging apps in a local Docker container: <https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh></span></span>
>
><span data-ttu-id="718a6-175">使用 Visual Studio 將 ASP.NET 容器部署到容器登錄：<https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker></span><span class="sxs-lookup"><span data-stu-id="718a6-175">Deploy an ASP.NET container to a container registry using Visual Studio: <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker></span></span>

>[!div class="step-by-step"]
><span data-ttu-id="718a6-176">[上一頁](docker-apps-inner-loop-workflow.md)
>[下一頁](set-up-windows-containers-with-powershell.md)</span><span class="sxs-lookup"><span data-stu-id="718a6-176">[Previous](docker-apps-inner-loop-workflow.md)
[Next](set-up-windows-containers-with-powershell.md)</span></span>
