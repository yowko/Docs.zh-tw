---
title: 在 Linux 或 Windows Nano Server 主機上部署單一容器 .NET Core Web 應用程式
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 在 Linux 或 Windows Nano Server 主機上部署單一容器 .NET Core Web 應用程式
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/27/2018
ms.openlocfilehash: 45be99a86a52ed450b795ca5f91c01ab82c7da47
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197351"
---
# <a name="deploying-single-container-based-net-core-web-applications-on-linux-or-windows-nano-server-hosts"></a><span data-ttu-id="33d02-103">在 Linux 或 Windows Nano Server 主機上部署單一容器 .NET Core Web 應用程式</span><span class="sxs-lookup"><span data-stu-id="33d02-103">Deploying Single-Container-Based .NET Core Web Applications on Linux or Windows Nano Server Hosts</span></span>

<span data-ttu-id="33d02-104">您可以使用 Docker 容器進行更簡單 Web 應用程式的整合型部署。_如此可改善持續整合與持續部署管線，並協助完成部署到生產的過程。不再產生「它可在我的電腦中運作，但為何無法在生產環境中運作？」的疑問_</span><span class="sxs-lookup"><span data-stu-id="33d02-104">_You can use Docker containers for monolithic deployment of simpler web applications. This improves continuous integration and continuous deployment pipelines and helps achieve deployment-to-production success. No more “It works in my machine, why does it not work in production?”_</span></span>

<span data-ttu-id="33d02-105">微服務架構有許多好處，但這些好處的代價是複雜度會增加。</span><span class="sxs-lookup"><span data-stu-id="33d02-105">A microservices-based architecture has many benefits, but those benefits come at a cost of increased complexity.</span></span> <span data-ttu-id="33d02-106">在某些情況下，這些代價會遠大於好處，因此您最好在單一容器或幾個容器中執行整合型部署應用程式。</span><span class="sxs-lookup"><span data-stu-id="33d02-106">In some cases, the costs outweigh the benefits and a monolithic deployment application running in one or a few containers is a better option.</span></span>

<span data-ttu-id="33d02-107">整合型應用程式可能不容易分解成多個適當分離的微服務。</span><span class="sxs-lookup"><span data-stu-id="33d02-107">A monolithic application might not be easily decomposable into well-separated microservices.</span></span> <span data-ttu-id="33d02-108">您已了解這些微服務應該透過函式來分割：其應該彼此獨立運作，才能提供復原能力更高的應用程式。</span><span class="sxs-lookup"><span data-stu-id="33d02-108">You've learned that these microservices should be partitioned by function: they should work independently of each other to provide a more resilient application.</span></span> <span data-ttu-id="33d02-109">如果您無法切割應用程式的功能，將它分離只會增加複雜度。</span><span class="sxs-lookup"><span data-stu-id="33d02-109">If you can't deliver feature slices of the application, separating it only adds complexity.</span></span>

<span data-ttu-id="33d02-110">應用程式可能還不需要獨立擴充功能。</span><span class="sxs-lookup"><span data-stu-id="33d02-110">An application might not yet need to scale features independently.</span></span> <span data-ttu-id="33d02-111">假設在 `eShopOnContainers` 參考應用程式的初期，流量並不需要將個別功能對應到不同的微服務。</span><span class="sxs-lookup"><span data-stu-id="33d02-111">Let’s suppose that in the early stages of the `eShopOnContainers` reference application, the traffic didn't justify separating features into different microservices.</span></span> <span data-ttu-id="33d02-112">流量很小，因此將資源新增至一個服務通常相當於將資源新增至所有服務。</span><span class="sxs-lookup"><span data-stu-id="33d02-112">Traffic was small enough that adding resources to one service typically meant adding resources to all services.</span></span> <span data-ttu-id="33d02-113">執行額外工作以將應用程式分成不同服務的好處有限。</span><span class="sxs-lookup"><span data-stu-id="33d02-113">The additional work to separate the application into discrete services provided minimal benefit.</span></span>

<span data-ttu-id="33d02-114">此外，在開發應用程式初期，您可能不清楚自然功能邊界止於何處。</span><span class="sxs-lookup"><span data-stu-id="33d02-114">Also, early in the development of an application you might not have a clear idea where the natural functional boundaries are.</span></span> <span data-ttu-id="33d02-115">當您開發最低可行性產品 (Minimum Viable Product) 時，自然分離的情況可能尚不明顯。</span><span class="sxs-lookup"><span data-stu-id="33d02-115">As you develop a minimum viable product, the natural separation might not yet have emerged.</span></span>

<span data-ttu-id="33d02-116">有些情況可能是暫時性的。</span><span class="sxs-lookup"><span data-stu-id="33d02-116">Some of these conditions might be temporary.</span></span> <span data-ttu-id="33d02-117">您可以先建立一個整合型應用程式，稍後再將某些功能分成微服務來開發和部署。</span><span class="sxs-lookup"><span data-stu-id="33d02-117">You might start by creating a monolithic application, and later separate some features to be developed and deployed as microservices.</span></span> <span data-ttu-id="33d02-118">其他情況可能對應用程式的問題空間很重要，這表示應用程式可能永遠不會分成多個微服務。</span><span class="sxs-lookup"><span data-stu-id="33d02-118">Other conditions might be essential to the application’s problem space, meaning that the application might never be broken into multiple microservices.</span></span>

<span data-ttu-id="33d02-119">將應用程式分成許多不同的處理序也會引進額外負荷。</span><span class="sxs-lookup"><span data-stu-id="33d02-119">Separating an application into many discrete processes also introduces overhead.</span></span> <span data-ttu-id="33d02-120">將功能分成不同處理序的複雜度更高。</span><span class="sxs-lookup"><span data-stu-id="33d02-120">There's more complexity in separating features into different processes.</span></span> <span data-ttu-id="33d02-121">通訊協定變得更複雜。</span><span class="sxs-lookup"><span data-stu-id="33d02-121">The communication protocols become more complex.</span></span> <span data-ttu-id="33d02-122">您必須在服務之間使用非同步通訊，而不是方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="33d02-122">Instead of method calls, you must use asynchronous communications between services.</span></span> <span data-ttu-id="33d02-123">當您移至微服務架構時，您需要新增在 `eShopOnContainers` 應用程式的微服務版本中實作的許多建置組塊：事件匯流排處理、訊息復原與重試、最終一致性等等。</span><span class="sxs-lookup"><span data-stu-id="33d02-123">As you move to a microservices architecture, you need to add many of the building blocks implemented in the microservices version of the `eShopOnContainers` application: event bus handling, message resiliency and retries, eventual consistency, and more.</span></span>

<span data-ttu-id="33d02-124">eShopOnContainers 的大幅簡化版本 (名為 [eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) 並包含在相同的 GitHub 存放庫中) 會作為整合型 MVC 應用程式執行。</span><span class="sxs-lookup"><span data-stu-id="33d02-124">A much-simplified version of eShopOnContainers (named [eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) and included in the same GitHub repository) runs as a monolithic MVC application.</span></span> <span data-ttu-id="33d02-125">如說明指出，該設計選擇也具有優點。</span><span class="sxs-lookup"><span data-stu-id="33d02-125">As described, there are advantages offered by that design choice.</span></span> <span data-ttu-id="33d02-126">您可以從 GitHub 下載此應用程式的來源並在本機執行。</span><span class="sxs-lookup"><span data-stu-id="33d02-126">You can download the source for this application from GitHub and run it locally.</span></span> <span data-ttu-id="33d02-127">即使是此整合型應用程式也可以透過部署至容器環境獲利。</span><span class="sxs-lookup"><span data-stu-id="33d02-127">Even this monolithic application benefits from being deployed in a container environment.</span></span>

<span data-ttu-id="33d02-128">其中一個優點是，容器化部署表示每個應用程式執行個體都會在相同的環境中執行。</span><span class="sxs-lookup"><span data-stu-id="33d02-128">For one, the containerized deployment means that every instance of the application runs in the same environment.</span></span> <span data-ttu-id="33d02-129">這包括進行早期測試和開發的開發人員環境。</span><span class="sxs-lookup"><span data-stu-id="33d02-129">This includes the developer environment where early testing and development take place.</span></span> <span data-ttu-id="33d02-130">開發小組可以在與生產環境相符的容器化環境中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="33d02-130">The development team can run the application in a containerized environment that matches the production environment.</span></span>

<span data-ttu-id="33d02-131">另外，容器化應用程式會以較低成本相應放大。</span><span class="sxs-lookup"><span data-stu-id="33d02-131">Also, containerized applications scale out at lower cost.</span></span> <span data-ttu-id="33d02-132">如稍早所見，容器環境可共用的資源比傳統 VM 環境更多。</span><span class="sxs-lookup"><span data-stu-id="33d02-132">As you saw earlier, the container environment enables greater resource sharing than traditional VM environments.</span></span>

<span data-ttu-id="33d02-133">最後，容器化應用程式會強制分離商務邏輯與存放區伺服器。</span><span class="sxs-lookup"><span data-stu-id="33d02-133">Finally, containerizing the application forces a separation between the business logic and the storage server.</span></span> <span data-ttu-id="33d02-134">當應用程式相應放大時，各種容器都會依賴單一實體儲存體媒體。</span><span class="sxs-lookup"><span data-stu-id="33d02-134">As the application scales out, the various containers will all rely on a single physical storage medium.</span></span> <span data-ttu-id="33d02-135">此儲存體通常會是執行 SQL Server 資料庫的高可用性伺服器。</span><span class="sxs-lookup"><span data-stu-id="33d02-135">This storage would typically be a high-availability server running a SQL Server database.</span></span>

## <a name="application-tour"></a><span data-ttu-id="33d02-136">應用程式導覽</span><span class="sxs-lookup"><span data-stu-id="33d02-136">Application tour</span></span>

<span data-ttu-id="33d02-137">[eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) 應用程式代表作為整合型應用程式執行的某些 eShopOnContainers 應用程式，也就是在 .NET Core 上執行的 ASP.NET Core MVC 應用程式。</span><span class="sxs-lookup"><span data-stu-id="33d02-137">The [eShopWeb](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebMonolithic) application represents some of the eShopOnContainers application running as a monolithic application — an ASP.NET Core MVC-based application running on .NET Core.</span></span> <span data-ttu-id="33d02-138">它主要提供前面章節中所述的目錄瀏覽功能。</span><span class="sxs-lookup"><span data-stu-id="33d02-138">It mainly provides the catalog browsing capabilities as described in earlier sections.</span></span>

<span data-ttu-id="33d02-139">該應用程式使用 SQL Server 資料庫來存放目錄。</span><span class="sxs-lookup"><span data-stu-id="33d02-139">The application uses a SQL Server database for the catalog storage.</span></span> <span data-ttu-id="33d02-140">在容器部署中，此整合型應用程式可以存取與微服務應用程式相同的資料存放區。</span><span class="sxs-lookup"><span data-stu-id="33d02-140">In container-based deployments, this monolithic application can access the same data store as the microservices-based application.</span></span> <span data-ttu-id="33d02-141">該應用程式會在整合型應用程式所在的容器中執行 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="33d02-141">The application is configured to run SQL Server in a container alongside the monolithic application.</span></span> <span data-ttu-id="33d02-142">在生產環境中，SQL Server 會在 Docker 主機外部的高可用性電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="33d02-142">In a production environment, SQL Server would run on a high-availability machine, outside of the Docker host.</span></span> <span data-ttu-id="33d02-143">為了開發或測試環境方便起見，建議在專屬的容器中執行 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="33d02-143">For convenience, in a development or test environment, running SQL Server in its own container is recommended.</span></span>

<span data-ttu-id="33d02-144">初始功能集只會啟用目錄瀏覽。</span><span class="sxs-lookup"><span data-stu-id="33d02-144">The initial feature set only enables browsing the catalog.</span></span> <span data-ttu-id="33d02-145">更新後即會啟用容器化應用程式的完整功能集。</span><span class="sxs-lookup"><span data-stu-id="33d02-145">Updates would enable the full feature set of the containerized application.</span></span> <span data-ttu-id="33d02-146">如需深入了解整合型 Web 應用程式架構，請參閱 [ASP.NET Web 應用程式架構做法](https://aka.ms/webappebook)電子書和相關的 [eShopOnWeb 範例應用程式](https://aka.ms/WebAppArchitecture)。</span><span class="sxs-lookup"><span data-stu-id="33d02-146">A more advanced monolithic web application architecture is described in the [ASP.NET Web Application architecture practices](https://aka.ms/webappebook) e-book and related [eShopOnWeb sample application](https://aka.ms/WebAppArchitecture).</span></span>

## <a name="docker-support"></a><span data-ttu-id="33d02-147">Docker 支援</span><span class="sxs-lookup"><span data-stu-id="33d02-147">Docker support</span></span>

<span data-ttu-id="33d02-148">eShopOnWeb 專案是在 .NET Core 上執行。</span><span class="sxs-lookup"><span data-stu-id="33d02-148">The eShopOnWeb project runs on .NET Core.</span></span> <span data-ttu-id="33d02-149">這表示它可以在 Linux 或 Windows 容器中執行。</span><span class="sxs-lookup"><span data-stu-id="33d02-149">That means it can run in either Linux-based or Windows-based containers.</span></span> <span data-ttu-id="33d02-150">請注意，若是 Docker 部署，您想要針對 SQL Server 使用相同的主機類型。</span><span class="sxs-lookup"><span data-stu-id="33d02-150">Note that for Docker deployment, you want to use the same host type for SQL Server.</span></span> <span data-ttu-id="33d02-151">Linux 容器允許較小的使用量，而且是偏好選項。</span><span class="sxs-lookup"><span data-stu-id="33d02-151">Linux-based containers allow a smaller footprint and are preferred.</span></span>

<span data-ttu-id="33d02-152">Visual Studio 提供專案範本，以將 Docker 支援新增至方案。</span><span class="sxs-lookup"><span data-stu-id="33d02-152">Visual Studio provides a project template that adds support for Docker to a solution.</span></span> <span data-ttu-id="33d02-153">以滑鼠右鍵按一下專案，然後依序按一下 [新增] 和 [Docker 支援]。</span><span class="sxs-lookup"><span data-stu-id="33d02-153">You right-click the project, click **Add** followed by **Docker Support**.</span></span> <span data-ttu-id="33d02-154">此範本會將 Dockerfile 新增至您的專案，以及新增提供 *docker-compose.yml* 檔案入門的 **docker-compose** 專案。</span><span class="sxs-lookup"><span data-stu-id="33d02-154">The template adds a Dockerfile to your project, and a new **docker-compose** project that provides a starter *docker-compose.yml* file.</span></span> <span data-ttu-id="33d02-155">此步驟在從 GitHub 下載的 eShopOnWeb 專案中已完成。</span><span class="sxs-lookup"><span data-stu-id="33d02-155">This step has already been done in the eShopOnWeb project downloaded from GitHub.</span></span> <span data-ttu-id="33d02-156">您可看到此解決方案包含 **eShopOnWeb** 專案和 **docker-compose** 專案，如圖 6-1 所示。</span><span class="sxs-lookup"><span data-stu-id="33d02-156">You can see that the solution contains the **eShopOnWeb** project and the **docker-compose** project as shown in Figure 6-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="33d02-157">**圖 6-1**.</span><span class="sxs-lookup"><span data-stu-id="33d02-157">**Figure 6-1**.</span></span> <span data-ttu-id="33d02-158">單一容器 Web 應用程式中的 **docker-compose** 專案</span><span class="sxs-lookup"><span data-stu-id="33d02-158">The **docker-compose** project in a single-container web application</span></span>

<span data-ttu-id="33d02-159">這些檔案是標準 docker-compose 檔案，與任何 Docker 專案一致。</span><span class="sxs-lookup"><span data-stu-id="33d02-159">These files are standard docker-compose files, consistent with any Docker project.</span></span> <span data-ttu-id="33d02-160">您可以透過 Visual Studio 或從命令列使用這些檔案。</span><span class="sxs-lookup"><span data-stu-id="33d02-160">You can use them with Visual Studio or from the command line.</span></span> <span data-ttu-id="33d02-161">此應用程式會在 .NET Core 上執行，並使用 Linux 容器。</span><span class="sxs-lookup"><span data-stu-id="33d02-161">This application runs on .NET Core and uses Linux containers.</span></span> <span data-ttu-id="33d02-162">因此，您也可以在 Mac 或 Linux 電腦上加以撰寫程式碼、建置及執行。</span><span class="sxs-lookup"><span data-stu-id="33d02-162">So, you can also code, build, and run it on a Mac or on a Linux machine.</span></span>

<span data-ttu-id="33d02-163">*docker-compose.yml* 檔案包含要建置哪些映像及要啟動哪些容器的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="33d02-163">The *docker-compose.yml* file contains information about what images to build and what containers to launch.</span></span> <span data-ttu-id="33d02-164">該範本會指定如何建置 `eshopweb` 映像及啟動應用程式的容器。</span><span class="sxs-lookup"><span data-stu-id="33d02-164">The templates specify how to build the `eshopweb` image and launch the application’s containers.</span></span> <span data-ttu-id="33d02-165">您需要在 SQL Server 上藉由加入其映像 (例如 `mssql-server-linux`) 來新增相依性，並新增 sql.data 映像的服務，Docker 才能建置及啟動該容器。</span><span class="sxs-lookup"><span data-stu-id="33d02-165">You need to add the dependency on SQL Server by including an image for it (for example, `mssql-server-linux`), and a service for the sql.data image for Docker to build and launch that container.</span></span> <span data-ttu-id="33d02-166">下列範例將顯示這些設定：</span><span class="sxs-lookup"><span data-stu-id="33d02-166">These settings are shown in the following example:</span></span>

```yml
version: '2'

services:
  eshopweb:
    image: eshop/web
    build:
    context: ./eShopWeb
    dockerfile: Dockerfile
    depends_on:
      - sql.data

  sql.data:
    image: microsoft/mssql-server-linux
```

<span data-ttu-id="33d02-167">`depends_on` 指示詞會告訴 Docker eShopWeb 映像相依於 sql.data 映像。</span><span class="sxs-lookup"><span data-stu-id="33d02-167">The `depends_on` directive tells Docker that the eShopWeb image depends on the sql.data image.</span></span> <span data-ttu-id="33d02-168">`depends_on` 下的程式行是使用 `microsoft/mssql-server-linux` 映像建置標記 `sql.data` 之映像的指示。</span><span class="sxs-lookup"><span data-stu-id="33d02-168">The lines below `depends_on` are the instructions to build an image tagged `sql.data` using the `microsoft/mssql-server-linux` image.</span></span>

<span data-ttu-id="33d02-169">**docker-compose** 專案會在主要 *docker-compose.yml* 節點下顯示其他 docker-compose 檔案，以提供與這些檔案相關的視覺化提示。</span><span class="sxs-lookup"><span data-stu-id="33d02-169">The **docker-compose** project displays the other docker-compose files under the main *docker-compose.yml* node to provide a visual indication that these files are related.</span></span> <span data-ttu-id="33d02-170">*docker-compose-override.yml* 檔案包含這兩項服務的設定，例如連接字串和其他應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="33d02-170">The *docker-compose-override.yml* file contains settings for both services, such as connection strings and other application settings.</span></span>

<span data-ttu-id="33d02-171">下列範例會顯示 *docker-compose.vs.debug.yml* 檔案，內含用來在 Visual Studio 中偵錯的設定。</span><span class="sxs-lookup"><span data-stu-id="33d02-171">The following example shows the *docker-compose.vs.debug.yml* file, which contains settings used for debugging in Visual Studio.</span></span> <span data-ttu-id="33d02-172">在該檔案中，eshopweb 映像前面會加上 dev 標記。</span><span class="sxs-lookup"><span data-stu-id="33d02-172">In that file, the eshopweb image has the dev tag appended to it.</span></span> <span data-ttu-id="33d02-173">這有助於將偵錯與發行映像分開，您才不會意外將偵錯資訊部署至生產環境：</span><span class="sxs-lookup"><span data-stu-id="33d02-173">That helps separate debug from release images so that you don't accidentally deploy the debug information to a production environment:</span></span>

```yml
version: '2'

services:
  eshopweb:
    image: eshop/web:dev
    build:
    args:
    source: ${DOCKER_BUILD_SOURCE}
    environment:
      - DOTNET_USE_POLLING_FILE_WATCHER=1
    volumes:
      - ./eShopWeb:/app
      - ~/.nuget/packages:/root/.nuget/packages:ro
      - ~/clrdbg:/clrdbg:ro
    entrypoint: tail -f /dev/null
    labels:
      - "com.microsoft.visualstudio.targetoperatingsystem=linux"
```

<span data-ttu-id="33d02-174">最後一個新增的檔案是 *docker-compose.ci.build.yml*。</span><span class="sxs-lookup"><span data-stu-id="33d02-174">The last file added is *docker-compose.ci.build.yml*.</span></span> <span data-ttu-id="33d02-175">您可以從命令列使用此檔案，以從 CI 伺服器建置專案。</span><span class="sxs-lookup"><span data-stu-id="33d02-175">This file would be used from the command line to build the project from a CI server.</span></span> <span data-ttu-id="33d02-176">此 Compose 檔案會啟動 Docker 容器，以建置應用程式所需的映像。</span><span class="sxs-lookup"><span data-stu-id="33d02-176">This compose file starts a Docker container that builds the images needed for your application.</span></span> <span data-ttu-id="33d02-177">下列範例會示範 *docker-compose.ci.build.yml* 檔案的內容：</span><span class="sxs-lookup"><span data-stu-id="33d02-177">The following example shows the contents of the *docker-compose.ci.build.yml* file:</span></span>

```yml
version: '2'

services:
  ci-build:
    image: microsoft/aspnetcore-build:latest
    volumes:
      - .:/src
    working_dir: /src
  command: /bin/bash -c "dotnet restore ./eShopWeb.sln && dotnet publish  ./eShopWeb.sln -c Release -o ./obj/Docker/publish"
```

> [!NOTE]
> <span data-ttu-id="33d02-178">從 .NET Core SDK 2.0 開始，在執行 [dotnet publish](../../../core/tools/dotnet-publish.md) 時，[dotnet restore](../../../core/tools/dotnet-restore.md) 命令會自動執行。</span><span class="sxs-lookup"><span data-stu-id="33d02-178">Starting with .NET Core SDK 2.0, the [dotnet restore](../../../core/tools/dotnet-restore.md) command executes automatically when [dotnet publish](../../../core/tools/dotnet-publish.md) is executed.</span></span>

<span data-ttu-id="33d02-179">請注意，此映像是 ASP.NET Core 組建映像。</span><span class="sxs-lookup"><span data-stu-id="33d02-179">Notice that the image is an ASP.NET Core build image.</span></span> <span data-ttu-id="33d02-180">該映像包含 SDK 和建置工具，可建置您的應用程式並建立所需的映像。</span><span class="sxs-lookup"><span data-stu-id="33d02-180">That image includes the SDK and build tools to build your application and create the required images.</span></span> <span data-ttu-id="33d02-181">使用此檔案執行 **docker-compose** 專案會從映像啟動組建容器，然後在該容器中建置應用程式的映像。</span><span class="sxs-lookup"><span data-stu-id="33d02-181">Running the **docker-compose** project using this file starts the build container from the image, then builds your application’s image in that container.</span></span> <span data-ttu-id="33d02-182">您可以將 *docker-compose* 檔案指定為命令列的一部分，以在 Docker 容器中建置您的應用程式，然後將它啟動。</span><span class="sxs-lookup"><span data-stu-id="33d02-182">You specify that *docker-compose* file as part of the command line to build your application in a Docker container, then launch it.</span></span>

<span data-ttu-id="33d02-183">在 Visual Studio 中，您可以選取 **docker-compose** 專案作為啟始專案，然後按 Ctrl+F5 (F5 以偵錯)，以便在 Docker 容器中執行您的應用程式，就像是任何其他應用程式一樣。</span><span class="sxs-lookup"><span data-stu-id="33d02-183">In Visual Studio, you can run your application in Docker containers by selecting the **docker-compose** project as the startup project, and then pressing Ctrl+F5 (F5 to debug), as you can with any other application.</span></span> <span data-ttu-id="33d02-184">當您啟動 **docker-compose** 專案時，Visual Studio 會使用 *docker-compose.yml* 檔案、*docker-compose.override.yml* 檔案及其中一個 docker-compose.vs.\* 檔案來執行 **docker-compose**。</span><span class="sxs-lookup"><span data-stu-id="33d02-184">When you start the **docker-compose** project, Visual Studio runs **docker-compose** using the *docker-compose.yml* file, the *docker-compose.override.yml* file, and one of the docker-compose.vs.\* files.</span></span> <span data-ttu-id="33d02-185">一旦啟動應用程式，Visual Studio 會為您啟動瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="33d02-185">Once the application has started, Visual Studio launches the browser for you.</span></span>

<span data-ttu-id="33d02-186">如果您在偵錯工具中啟動應用程式，Visual Studio 將會附加至在 Docker 中執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="33d02-186">If you launch the application in the debugger, Visual Studio attaches to the running application in Docker.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="33d02-187">疑難排解</span><span class="sxs-lookup"><span data-stu-id="33d02-187">Troubleshooting</span></span>

<span data-ttu-id="33d02-188">本節描述當您在本機執行容器時可能發生的一些問題，並建議一些修正。</span><span class="sxs-lookup"><span data-stu-id="33d02-188">This section describes a few issues that might arise when your run containers locally and suggests some fixes.</span></span>

### <a name="stop-docker-containers"></a><span data-ttu-id="33d02-189">停止 Docker 容器</span><span class="sxs-lookup"><span data-stu-id="33d02-189">Stop Docker containers</span></span>

<span data-ttu-id="33d02-190">啟動容器化應用程式之後，容器會繼續執行，即使在停止偵錯之後亦然。</span><span class="sxs-lookup"><span data-stu-id="33d02-190">After you launch the containerized application, the containers continue to run, even after you have stopped debugging.</span></span> <span data-ttu-id="33d02-191">您可以從命令列執行 `docker ps` 命令，以查看哪些容器正在執行。</span><span class="sxs-lookup"><span data-stu-id="33d02-191">You can run the `docker ps` command from the command line to see which containers are running.</span></span> <span data-ttu-id="33d02-192">`docker stop` 命令會停止執行中的容器，如圖 6-2 所示。</span><span class="sxs-lookup"><span data-stu-id="33d02-192">The `docker stop` command stops a running container, as shown in Figure 6-2.</span></span>

![](./media/image2.png)

<span data-ttu-id="33d02-193">**圖 6-2**.</span><span class="sxs-lookup"><span data-stu-id="33d02-193">**Figure 6-2**.</span></span> <span data-ttu-id="33d02-194">使用 docker ps 和 docker stop CLI 命令來列出及停止容器</span><span class="sxs-lookup"><span data-stu-id="33d02-194">Listing and stopping containers with the docker ps and docker stop CLI commands</span></span>

<span data-ttu-id="33d02-195">當您在不同的設定之間切換時，您可能需要停止執行中的處理序。</span><span class="sxs-lookup"><span data-stu-id="33d02-195">You might need to stop running processes when you switch between different configurations.</span></span> <span data-ttu-id="33d02-196">否則，執行 Web 應用程式的容器會使用適用於您應用程式的連接埠 (在此範例中為 5106)。</span><span class="sxs-lookup"><span data-stu-id="33d02-196">Otherwise, the container that is running the web application is using the port for your application (5106 in this example).</span></span>

### <a name="add-docker-to-your-projects"></a><span data-ttu-id="33d02-197">將 Docker 新增至您的專案</span><span class="sxs-lookup"><span data-stu-id="33d02-197">Add Docker to your projects</span></span>

<span data-ttu-id="33d02-198">新增 Docker 支援的精靈會與執行中的 Docker 處理序通訊。</span><span class="sxs-lookup"><span data-stu-id="33d02-198">The wizard that adds Docker support communicates with the running Docker process.</span></span> <span data-ttu-id="33d02-199">當您啟動精靈時，如果 Docker 未執行，精靈將無法正確執行。</span><span class="sxs-lookup"><span data-stu-id="33d02-199">If Docker isn't running when you start the wizard, the wizard won't run correctly.</span></span> <span data-ttu-id="33d02-200">精靈會檢查您目前的容器選擇，以新增正確的 Docker 支援。</span><span class="sxs-lookup"><span data-stu-id="33d02-200">The wizard examines your current container choice to add the correct Docker support.</span></span> <span data-ttu-id="33d02-201">若要新增 Windows 容器的支援，您需要在有執行中 Docker 並已設定 Windows 容器的同時執行精靈。</span><span class="sxs-lookup"><span data-stu-id="33d02-201">To add support for Windows Containers, run the wizard while you have Docker running with Windows Containers configured.</span></span> <span data-ttu-id="33d02-202">若要新增 Linux 容器的支援，您需要在有執行中 Docker 並已設定 Linux 容器的同時執行精靈。</span><span class="sxs-lookup"><span data-stu-id="33d02-202">To add support for Linux containers, run the wizard while you have Docker running with Linux containers configured.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="33d02-203">[上一頁](../docker-application-development-process/docker-app-development-workflow.md)
[下一頁](../containerize-net-framework-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="33d02-203">[Previous](../docker-application-development-process/docker-app-development-workflow.md)
[Next](../containerize-net-framework-applications/index.md)</span></span>
