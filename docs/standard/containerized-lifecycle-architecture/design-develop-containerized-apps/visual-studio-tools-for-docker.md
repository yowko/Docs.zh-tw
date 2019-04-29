---
title: Visual Studio Tools for Windows 上的 Docker
description: 了解 Visual Studio 2017 15.7 版及更新版本中可用的 Docker 工具。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 431a0f34ba913c18c35e28ca45660495403bf688
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795538"
---
# <a name="use-docker-tools-in-visual-studio-2017-on-windows"></a><span data-ttu-id="c06ae-103">在 Windows 上的 Visual Studio 2017 中使用 Docker 工具</span><span class="sxs-lookup"><span data-stu-id="c06ae-103">Use Docker Tools in Visual Studio 2017 on Windows</span></span>

<span data-ttu-id="c06ae-104">使用 Docker 工具包含在 Visual Studio 2017 15.7 版及更新版本時，開發人員工作流程，類似於使用 Visual Studio Code 和 Docker CLI （事實上，它根據相同的 Docker CLI），但它可以更輕鬆地開始使用，可簡化此程序，以及提供更高的生產力組建、 執行和撰寫工作。</span><span class="sxs-lookup"><span data-stu-id="c06ae-104">The developer workflow when using the Docker Tools included in Visual Studio 2017 version 15.7 and later, is similar to using Visual Studio Code and Docker CLI (in fact, it's based on the same Docker CLI), but it's easier to get started, simplifies the process, and provides greater productivity for the build, run, and compose tasks.</span></span> <span data-ttu-id="c06ae-105">它也可以執行和偵錯您的容器，透過一般`F5`和`Ctrl+F5`從 Visual Studio 的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="c06ae-105">It can also run and debug your containers via the usual `F5` and `Ctrl+F5` keys from Visual Studio.</span></span> <span data-ttu-id="c06ae-106">可以在同一個定義其容器如果甚至偵錯整個解決方案`docker-compose.yml`方案層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="c06ae-106">You can even debug a whole solution if its containers are defined in the same `docker-compose.yml` file at the solution level.</span></span>

## <a name="configure-your-local-environment"></a><span data-ttu-id="c06ae-107">設定您的本機環境</span><span class="sxs-lookup"><span data-stu-id="c06ae-107">Configure your local environment</span></span>

<span data-ttu-id="c06ae-108">使用 Docker for Windows 的最新版本，就比以往若要開發 Docker 應用程式因為下列參考中所述，安裝程式很簡單，更容易。</span><span class="sxs-lookup"><span data-stu-id="c06ae-108">With the latest versions of Docker for Windows, it's easier than ever to develop Docker applications because the setup is straightforward, as explained in the following references.</span></span>

> [!TIP]
> <span data-ttu-id="c06ae-109">若要深入了解安裝 Docker for Windows，請移至 (<https://docs.docker.com/docker-for-windows/>)。</span><span class="sxs-lookup"><span data-stu-id="c06ae-109">To learn more about installing Docker for Windows, go to (<https://docs.docker.com/docker-for-windows/>).</span></span>

## <a name="docker-support-in-visual-studio-2017"></a><span data-ttu-id="c06ae-110">Visual Studio 2017 中的 docker 支援</span><span class="sxs-lookup"><span data-stu-id="c06ae-110">Docker support in Visual Studio 2017</span></span>

<span data-ttu-id="c06ae-111">有兩種您可以新增至專案的 Docker 支援層級。</span><span class="sxs-lookup"><span data-stu-id="c06ae-111">There are two levels of Docker support you can add to a project.</span></span> <span data-ttu-id="c06ae-112">在 ASP.NET Core 專案中，您就可以新增`Dockerfile`專案啟用 Docker 支援的檔案。</span><span class="sxs-lookup"><span data-stu-id="c06ae-112">In ASP.NET Core projects, you can just add a `Dockerfile` file to the project by enabling Docker support.</span></span> <span data-ttu-id="c06ae-113">下一個層級是容器協調流程支援，這會新增`Dockerfile`至專案 （如果它尚未存在） 和`docker-compose.yml`方案層級的檔案。</span><span class="sxs-lookup"><span data-stu-id="c06ae-113">The next level is container orchestration support, which adds a `Dockerfile` to the project (if it doesn't already exist) and a `docker-compose.yml` file at the solution level.</span></span> <span data-ttu-id="c06ae-114">預設會在 Visual Studio 2017 版本 15.0 到 15.7 新增容器協調流程的支援，透過 Docker Compose。</span><span class="sxs-lookup"><span data-stu-id="c06ae-114">Container orchestration support, via Docker Compose, is added by default in Visual Studio 2017 versions 15.0 to 15.7.</span></span> <span data-ttu-id="c06ae-115">容器協調流程的支援是選擇性功能 15.8 或更新版本的 Visual Studio 2017 版本中。</span><span class="sxs-lookup"><span data-stu-id="c06ae-115">Container orchestration support is an opt-in feature in Visual Studio 2017 versions 15.8 or later.</span></span> <span data-ttu-id="c06ae-116">更新版本的版本 15.8 支援 Docker Compose 與 Service Fabric。</span><span class="sxs-lookup"><span data-stu-id="c06ae-116">Version 15.8 an later support Docker Compose and Service Fabric.</span></span>

<span data-ttu-id="c06ae-117">**新增 > Docker 支援**並**新增 > 容器協調器支援**命令位於 ASP.NET Core 專案的專案節點的右鍵操作功能表 （或操作功能表） 中**方案總管] 中**，如 [圖 4-31 的所示：</span><span class="sxs-lookup"><span data-stu-id="c06ae-117">The **Add > Docker Support** and **Add > Container Orchestrator Support** commands are located on the right-click menu (or context menu) of the project node for an ASP.NET Core project in **Solution Explorer**, as shown in Figure 4-31:</span></span>

![Visual Studio 中的 [新增 Docker 支援] 功能表選項](./media/add-docker-support-menu.png)

<span data-ttu-id="c06ae-119">**圖 4-31**。</span><span class="sxs-lookup"><span data-stu-id="c06ae-119">**Figure 4-31**.</span></span> <span data-ttu-id="c06ae-120">將 Docker 支援新增至 Visual Studio 2017 的專案</span><span class="sxs-lookup"><span data-stu-id="c06ae-120">Adding Docker support to a Visual Studio 2017 project</span></span>

### <a name="add-docker-support"></a><span data-ttu-id="c06ae-121">新增 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="c06ae-121">Add Docker support</span></span>

<span data-ttu-id="c06ae-122">您也可以選取現有的 ASP.NET Core 專案新增 Docker 支援**新增** > **Docker 支援**中**方案總管 中**。</span><span class="sxs-lookup"><span data-stu-id="c06ae-122">You can add Docker support to an existing ASP.NET Core project by selecting **Add** > **Docker Support** in **Solution Explorer**.</span></span> <span data-ttu-id="c06ae-123">您也可以啟用 Docker 支援在專案建立期間選取**啟用 Docker 支援**中**新的 ASP.NET Core Web 應用程式**按一下之後開啟的對話方塊**確定**中**新的專案**對話方塊中，顯示 圖 4-32。</span><span class="sxs-lookup"><span data-stu-id="c06ae-123">You can also enable Docker support during project creation by selecting **Enable Docker Support** in the **New ASP.NET Core Web Application** dialog box that opens after you click **OK** in the **New Project** dialog box, as shown in Figure 4-32.</span></span>

![在 Visual Studio 中為新的 ASP.NET Core Web 應用程式啟用 Docker 支援](./media/enable-docker-support-visual-studio.png)

<span data-ttu-id="c06ae-125">**圖 4-32**。</span><span class="sxs-lookup"><span data-stu-id="c06ae-125">**Figure 4-32**.</span></span> <span data-ttu-id="c06ae-126">在 Visual Studio 2017 中的專案建立期間啟用 Docker 支援</span><span class="sxs-lookup"><span data-stu-id="c06ae-126">Enable Docker support during project creation in Visual Studio 2017</span></span>

<span data-ttu-id="c06ae-127">當您新增或啟用 Docker 支援時，Visual Studio 會加入*Dockerfile*檔案加入專案。</span><span class="sxs-lookup"><span data-stu-id="c06ae-127">When you add or enable Docker support, Visual Studio adds a *Dockerfile* file to the project.</span></span>

> [!NOTE]
> <span data-ttu-id="c06ae-128">圖 4-33 示，您可以啟用 ASP.NET 專案 (.NET Framework，.NET Core 專案) 的專案建立期間的 Docker Compose 的支援，也會加入容器協調流程支援。</span><span class="sxs-lookup"><span data-stu-id="c06ae-128">When you enable Docker Compose support during project creation for a ASP.NET project (.NET Framework, not a .NET Core project) as shown in Figure 4-33, container orchestration support is also added.</span></span>

![針對 ASP.NET 專案啟用 Docker Compose 支援](media/enable-docker-compose-support.png)

<span data-ttu-id="c06ae-130">**圖 4-33**。</span><span class="sxs-lookup"><span data-stu-id="c06ae-130">**Figure 4-33**.</span></span> <span data-ttu-id="c06ae-131">啟用 Docker Compose 的 ASP.NET 專案中 Visual Studio 2017 的支援</span><span class="sxs-lookup"><span data-stu-id="c06ae-131">Enabling Docker Compose support for an ASP.NET project in Visual Studio 2017</span></span>

### <a name="add-container-orchestration-support"></a><span data-ttu-id="c06ae-132">新增容器協調流程的支援</span><span class="sxs-lookup"><span data-stu-id="c06ae-132">Add container orchestration support</span></span>

<span data-ttu-id="c06ae-133">當您想要撰寫多容器解決方案時，將容器協調流程支援新增至您的專案。</span><span class="sxs-lookup"><span data-stu-id="c06ae-133">When you want to compose a multi-container solution, add container orchestration support to your projects.</span></span> <span data-ttu-id="c06ae-134">這可讓您執行，並同時在偵錯容器 （整個解決方案） 的群組，如果它們定義在相同*docker compose.yml*檔案。</span><span class="sxs-lookup"><span data-stu-id="c06ae-134">This lets you run and debug a group of containers (a whole solution) at the same time if they're defined in the same *docker-compose.yml* file.</span></span>

<span data-ttu-id="c06ae-135">若要新增容器協調流程的支援，請以滑鼠右鍵按一下的方案或專案節點上**方案總管 中**，然後選擇**新增 > 容器協調流程支援**。</span><span class="sxs-lookup"><span data-stu-id="c06ae-135">To add container orchestration support, right-click on the solution or project node in **Solution Explorer**, and choose **Add > Container Orchestration Support**.</span></span> <span data-ttu-id="c06ae-136">然後選擇**Docker Compose**或是**Service Fabric**管理容器。</span><span class="sxs-lookup"><span data-stu-id="c06ae-136">Then choose **Docker Compose** or **Service Fabric** to manage the containers.</span></span>

<span data-ttu-id="c06ae-137">協調流程的容器支援新增至您的專案之後，您會看到加入至專案的 Dockerfile 並**docker compose**加入至方案中的資料夾**方案總管] 中**所示，[圖 4-34:</span><span class="sxs-lookup"><span data-stu-id="c06ae-137">After you add container orchestration support to your project, you see a Dockerfile added to the project and a **docker-compose** folder added to the solution in **Solution Explorer**, as shown in Figure 4-34:</span></span>

![Visual Studio 中 [方案總管] 中的 Docker 檔案](media/docker-support-solution-explorer.png)

<span data-ttu-id="c06ae-139">**圖 4-34**。</span><span class="sxs-lookup"><span data-stu-id="c06ae-139">**Figure 4-34**.</span></span> <span data-ttu-id="c06ae-140">Visual Studio 2017 中的 [方案總管] 中的 docker 檔案</span><span class="sxs-lookup"><span data-stu-id="c06ae-140">Docker files in Solution Explorer in Visual Studio 2017</span></span>

<span data-ttu-id="c06ae-141">如果 *docker-compose.yml* 已存在，則 Visual Studio 只會向其新增所需的組態程式碼行。</span><span class="sxs-lookup"><span data-stu-id="c06ae-141">If *docker-compose.yml* already exists, Visual Studio just adds the required lines of configuration code to it.</span></span>

## <a name="configure-docker-tools"></a><span data-ttu-id="c06ae-142">設定 Docker 工具</span><span class="sxs-lookup"><span data-stu-id="c06ae-142">Configure Docker tools</span></span>

<span data-ttu-id="c06ae-143">從主功能表中，選擇**工具 > 選項**，展開**容器工具 > 設定**。</span><span class="sxs-lookup"><span data-stu-id="c06ae-143">From the main menu, choose **Tools > Options**, and expand **Container Tools > Settings**.</span></span> <span data-ttu-id="c06ae-144">容器的 [工具] 設定會出現。</span><span class="sxs-lookup"><span data-stu-id="c06ae-144">The container tools settings appear.</span></span>

![Visual Studio Docker 工具選項，顯示：自動在專案載入提取所需的 Docker 映像、 自動在背景中啟動容器、 自動終止容器關閉、 解決方案和不要提示信任 SSL 憑證。](./media/visual-studio-docker-tools-options.png)

<span data-ttu-id="c06ae-146">**圖 4-35**。</span><span class="sxs-lookup"><span data-stu-id="c06ae-146">**Figure 4-35**.</span></span> <span data-ttu-id="c06ae-147">Docker 工具選項</span><span class="sxs-lookup"><span data-stu-id="c06ae-147">Docker Tools Options</span></span>

<span data-ttu-id="c06ae-148">下表可協助您決定如何設定這些選項。</span><span class="sxs-lookup"><span data-stu-id="c06ae-148">The following table might help you decide how to set these options.</span></span>

| <span data-ttu-id="c06ae-149">名稱</span><span class="sxs-lookup"><span data-stu-id="c06ae-149">Name</span></span> | <span data-ttu-id="c06ae-150">預設設定</span><span class="sxs-lookup"><span data-stu-id="c06ae-150">Default Setting</span></span> | <span data-ttu-id="c06ae-151">適用於</span><span class="sxs-lookup"><span data-stu-id="c06ae-151">Applies To</span></span> | <span data-ttu-id="c06ae-152">描述</span><span class="sxs-lookup"><span data-stu-id="c06ae-152">Description</span></span> |
| -----|:---------------:|:----------:| ----------- |
| <span data-ttu-id="c06ae-153">自動在專案載入提取所需的 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="c06ae-153">Automatically pull required Docker images on project load</span></span> | <span data-ttu-id="c06ae-154">開啟</span><span class="sxs-lookup"><span data-stu-id="c06ae-154">On</span></span> | <span data-ttu-id="c06ae-155">Docker Compose</span><span class="sxs-lookup"><span data-stu-id="c06ae-155">Docker Compose</span></span> | <span data-ttu-id="c06ae-156">為了提高效能載入專案時，Visual Studio 會啟動 Docker 提取作業在背景中，因此當您準備好要執行您的程式碼，將映像已下載，或是正在下載。</span><span class="sxs-lookup"><span data-stu-id="c06ae-156">For increased performance when loading projects, Visual Studio will start a Docker pull operation in the background so that when you're ready to run your code, the image is already downloaded or in the process of downloading.</span></span> <span data-ttu-id="c06ae-157">如果您只會載入專案，並瀏覽程式碼，您可以避免下載容器映像，您不需要將此關閉。</span><span class="sxs-lookup"><span data-stu-id="c06ae-157">If you're just loading projects and browsing code, you can turn this off to avoid downloading container images you don't need.</span></span> |
| <span data-ttu-id="c06ae-158">自動在背景中啟動容器</span><span class="sxs-lookup"><span data-stu-id="c06ae-158">Automatically start containers in background</span></span> | <span data-ttu-id="c06ae-159">開啟</span><span class="sxs-lookup"><span data-stu-id="c06ae-159">On</span></span> | <span data-ttu-id="c06ae-160">Docker Compose</span><span class="sxs-lookup"><span data-stu-id="c06ae-160">Docker Compose</span></span> | <span data-ttu-id="c06ae-161">再次為了提高效能，Visual Studio 會建立一個容器與磁碟區掛接供當您建置並執行您的容器。</span><span class="sxs-lookup"><span data-stu-id="c06ae-161">Again for increased performance, Visual Studio creates a container with volume mounts ready for when you build and run your container.</span></span> <span data-ttu-id="c06ae-162">如果您想要控制您的容器建立時，請關閉這個功能。</span><span class="sxs-lookup"><span data-stu-id="c06ae-162">If you want to control when your container is created, turn this off.</span></span> |
| <span data-ttu-id="c06ae-163">自動終止容器解決方案關閉</span><span class="sxs-lookup"><span data-stu-id="c06ae-163">Automatically kill containers on solution close</span></span> | <span data-ttu-id="c06ae-164">開啟</span><span class="sxs-lookup"><span data-stu-id="c06ae-164">On</span></span> | <span data-ttu-id="c06ae-165">Docker Compose</span><span class="sxs-lookup"><span data-stu-id="c06ae-165">Docker Compose</span></span> | <span data-ttu-id="c06ae-166">如果您想要繼續執行之後關閉解決方案，或關閉 Visual Studio 方案的容器，請開啟此功能。</span><span class="sxs-lookup"><span data-stu-id="c06ae-166">Turn this off if you would like containers for your solution to continue to run after closing the solution or closing Visual Studio.</span></span> |
| <span data-ttu-id="c06ae-167">不要提示信任 localhost SSL 憑證</span><span class="sxs-lookup"><span data-stu-id="c06ae-167">Do not prompt for trusting localhost SSL certificate</span></span> | <span data-ttu-id="c06ae-168">Off</span><span class="sxs-lookup"><span data-stu-id="c06ae-168">Off</span></span> | <span data-ttu-id="c06ae-169">ASP.NET Core 2.1 專案</span><span class="sxs-lookup"><span data-stu-id="c06ae-169">ASP.NET Core 2.1 projects</span></span> | <span data-ttu-id="c06ae-170">如果 localhost SSL 憑證不受信任，Visual Studio 在除非已選取此核取方塊，會先提示每次您執行您的專案。</span><span class="sxs-lookup"><span data-stu-id="c06ae-170">If the localhost SSL certificate is not trusted, Visual Studio will prompt every time you run your project, unless this checkbox is checked.</span></span> |

> [!WARNING]
> <span data-ttu-id="c06ae-171">如果 localhost SSL 憑證不受信任，而且您核取方塊來隱藏提示，則 HTTPS web 要求可能會在您的應用程式或服務執行階段失敗。</span><span class="sxs-lookup"><span data-stu-id="c06ae-171">If the localhost SSL certificate is not trusted, and you check the box to suppress prompting, then HTTPS web requests might fail at runtime in your app or service.</span></span> <span data-ttu-id="c06ae-172">在此情況下，取消核取**不要提示**核取方塊，執行您的專案，並指出在提示字元中的信任。</span><span class="sxs-lookup"><span data-stu-id="c06ae-172">In that case, uncheck the **Do not prompt** checkbox, run your project, and indicate trust at the prompt.</span></span>

> [!TIP]
> <span data-ttu-id="c06ae-173">如需詳細的服務實作和使用 Visual Studio Tools for Docker，閱讀下列文章：</span><span class="sxs-lookup"><span data-stu-id="c06ae-173">For further details on the services implementation and use of Visual Studio Tools for Docker, read the following articles:</span></span>
>
><span data-ttu-id="c06ae-174">偵錯本機 Docker 容器中的應用程式： <https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh></span><span class="sxs-lookup"><span data-stu-id="c06ae-174">Debugging apps in a local Docker container: <https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh></span></span>
>
><span data-ttu-id="c06ae-175">將 ASP.NET 容器部署到使用 Visual Studio 的容器登錄： <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker></span><span class="sxs-lookup"><span data-stu-id="c06ae-175">Deploy an ASP.NET container to a container registry using Visual Studio: <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker></span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c06ae-176">[上一頁](docker-apps-inner-loop-workflow.md)
>[下一頁](set-up-windows-containers-with-powershell.md)</span><span class="sxs-lookup"><span data-stu-id="c06ae-176">[Previous](docker-apps-inner-loop-workflow.md)
[Next](set-up-windows-containers-with-powershell.md)</span></span>
