---
title: "定義您的 docker compose.yml 多容器應用程式"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |定義您的 docker compose.yml 多容器應用程式"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c5d4d2c9fb9fbb595f6f6ea195247474f353a32f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="3ec0b-104">定義您的 docker compose.yml 多容器應用程式</span><span class="sxs-lookup"><span data-stu-id="3ec0b-104">Defining your multi-container application with docker-compose.yml</span></span> 

<span data-ttu-id="3ec0b-105">本指南中， [docker compose.yml](https://docs.docker.com/compose/compose-file/)檔案 > 一節中導入[步驟 4。建置多容器 Docker 應用程式時，您的服務定義在 docker compose.yml](#step4_define_svcs_in_docker_compose_yml)。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-105">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](#step4_define_svcs_in_docker_compose_yml).</span></span> <span data-ttu-id="3ec0b-106">不過，有一些使用值得深入瀏覽的 docker-compose 檔案的其他方法。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-106">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="3ec0b-107">例如，您可以明確地描述您要部署多個容器應用程式在 docker compose.yml 檔案中的方式。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-107">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="3ec0b-108">（選擇性） 您也可以描述要如何建立自訂的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-108">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="3ec0b-109">（自訂的 Docker 映像也可以建立使用 Docker CLI。）</span><span class="sxs-lookup"><span data-stu-id="3ec0b-109">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="3ec0b-110">基本上，您會定義每個您想要部署的容器，再加上每個容器部署某些特性。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-110">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="3ec0b-111">一旦您擁有多個容器部署描述檔案，您可以部署整個方案由協調以單一動作[docker 撰寫向上](https://docs.docker.com/compose/overview/)CLI 命令，或者您可以將它部署以透明的方式從 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-111">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="3ec0b-112">否則，您必須使用 Docker CLI 使用 docker run 命令，從命令列部署容器所-容器中的多個步驟。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-112">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the docker run command from the command line.</span></span> <span data-ttu-id="3ec0b-113">因此，必須指定剛好只有一個映像 docker compose.yml 中所定義的每個服務，或建置。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-113">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="3ec0b-114">其他索引鍵為選擇性，且類似於其 docker 執行命令列對應項目。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-114">Other keys are optional, and are analogous to their docker run command-line counterparts.</span></span>

<span data-ttu-id="3ec0b-115">下列 YAML 程式碼是 eShopOnContainers 範例可能全域但單一 docker-compose.yml 檔案的定義。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-115">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="3ec0b-116">這不是從 eShopOnContainers 實際 docker-compose 檔案。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-116">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="3ec0b-117">相反地，它是簡化和合併版本在單一檔案中，這不是最佳的方式來使用 docker-撰寫的檔案，將會稍後所述。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-117">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

```yml
version: '2'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
    ports:
      - "5100:80"
    depends_on:
      - catalog.api
      - ordering.api
      - basket.api

  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  basket.api:
    image: eshop/basket.api
    environment:
      - ConnectionString=sql.data
    ports:
      - "5103:80"
    depends_on:
      - sql.data

  sql.data:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basket.data:
    image: redis
```

<span data-ttu-id="3ec0b-118">在這個檔案的根目錄機碼是服務 」。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-118">The root key in this file is services.</span></span> <span data-ttu-id="3ec0b-119">該機碼下，您定義您想要部署和執行中執行時的服務 docker 撰寫命令，或當您從 Visual Studio 部署使用此 docker compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-119">Under that key you define the services you want to deploy and run when you execute the docker-compose up command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="3ec0b-120">在此情況下，docker compose.yml 檔案會有多個服務定義，如下列清單所述。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-120">In this case, the docker-compose.yml file has multiple services defined, as described in the following list.</span></span>

-   <span data-ttu-id="3ec0b-121">webmvc 包括耗用從伺服器端 C microservices ASP.NET Core MVC 應用程式的容器\#</span><span class="sxs-lookup"><span data-stu-id="3ec0b-121">webmvc Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>

-   <span data-ttu-id="3ec0b-122">catalog.api 包括目錄 ASP.NET Core Web API 的微服務容器</span><span class="sxs-lookup"><span data-stu-id="3ec0b-122">catalog.api Container including the Catalog ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="3ec0b-123">ordering.api 包含排序 ASP.NET Core Web API 的微服務容器</span><span class="sxs-lookup"><span data-stu-id="3ec0b-123">ordering.api Container including the Ordering ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="3ec0b-124">sql.data for Linux，持有 microservices 資料庫執行 SQL Server 的容器</span><span class="sxs-lookup"><span data-stu-id="3ec0b-124">sql.data Container running SQL Server for Linux, holding the microservices databases</span></span>

-   <span data-ttu-id="3ec0b-125">使用購物籃 ASP.NET Core Web API 的微服務 basket.api 容器</span><span class="sxs-lookup"><span data-stu-id="3ec0b-125">basket.api Container with the Basket ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="3ec0b-126">basket.data REDIS 快取服務中，使用購物籃資料庫執行為 REDIS 快取的容器</span><span class="sxs-lookup"><span data-stu-id="3ec0b-126">basket.data Container running the REDIS cache service, with the basket database as a REDIS cache</span></span>

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="3ec0b-127">簡單的 Web 服務 API 容器</span><span class="sxs-lookup"><span data-stu-id="3ec0b-127">A simple Web Service API container</span></span>

<span data-ttu-id="3ec0b-128">將焦點放在單一容器上，catalog.api 容器的微服務有直接的定義：</span><span class="sxs-lookup"><span data-stu-id="3ec0b-128">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

```yml
  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=catalog.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data
```

<span data-ttu-id="3ec0b-129">此容器化的服務具有下列的基本設定：</span><span class="sxs-lookup"><span data-stu-id="3ec0b-129">This containerized service has the following basic configuration:</span></span>

-   <span data-ttu-id="3ec0b-130">它根據自訂 eshop/catalog.api 映像。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-130">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="3ec0b-131">為了簡單起見，沒有任何組建： 金鑰檔中的設定。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-131">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="3ec0b-132">這表示在映像必須已先前建置 （使用 docker 建置），或已從任何 Docker 登錄下載 （與 docker 的提取命令）。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-132">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

-   <span data-ttu-id="3ec0b-133">它會定義名為 ConnectionString 的連接字串，可用於 Entity framework 存取 SQL Server 執行個體，其中包含的目錄資料模型的環境變數。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-133">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="3ec0b-134">在此情況下，相同的 SQL Server 容器所保留的多個資料庫。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-134">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="3ec0b-135">因此，您需要較少的記憶體在開發電腦中的 Docker。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-135">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="3ec0b-136">不過，您也可以部署一個 SQL Server 容器，每個微服務資料庫。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-136">However, you could also deploy one SQL Server container for each microservice database.</span></span>

-   <span data-ttu-id="3ec0b-137">SQL Server 名稱是 sql.data，正在執行 SQL Server 執行個體，適用於 Linux 的容器所使用的相同名稱。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-137">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="3ec0b-138">這是很方便。能夠使用此名稱解析 （內部 Docker 主機） 將會解析網路位址，因此您不需要知道您要從其他容器存取容器的內部 IP。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-138">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="3ec0b-139">因為連接字串環境變數所定義，您可以設定該變數，透過不同的機制，而在不同的時間。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-139">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="3ec0b-140">例如，您可以在部署到生產環境中的最後一個主機，或從您的 CI/CD 管線 VSTS 或您慣用的 DevOps 系統中執行它時，設定不同的連接字串。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-140">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in VSTS or your preferred DevOps system.</span></span>

-   <span data-ttu-id="3ec0b-141">它會公開內部服務的存取權 catalog.api Docker 主機中的連接埠 80。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-141">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="3ec0b-142">該主機目前是 Linux VM，因為它為基礎的 Docker 映像 for Linux，但您可以設定改為執行 Windows 映像上的容器。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-142">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

-   <span data-ttu-id="3ec0b-143">它會將公開連接埠 80 上 Docker 主機電腦 (Linux VM) 的連接埠 5101 容器上的轉送。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-143">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

-   <span data-ttu-id="3ec0b-144">它會連結到 sql.data 服務 （在容器中執行的 Linux 資料庫的 SQL Server 執行個體） 的 web 服務。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-144">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="3ec0b-145">當您指定此相依性時，catalog.api 容器之前不會啟動 sql.data 容器已經啟動。這是很重要，因為 catalog.api 必須最多有 SQL Server 資料庫執行第一次。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-145">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="3ec0b-146">不過，這種容器相依性不是在許多情況下，因為只能在容器層級檢查 Docker。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-146">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="3ec0b-147">有時 （在此案例的 SQL Server) 服務可能仍然不是好時，因此建議您最好在用戶端 microservices 中實作重試邏輯以指數型輪詢。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-147">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="3ec0b-148">這樣一來，如果相依性容器未準備好一段時間，應用程式仍會具有恢復功能。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-148">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

-   <span data-ttu-id="3ec0b-149">它被設定為允許存取外部伺服器： 額外\_主機設定可讓您存取外部的伺服器或機器之外 Docker 主機 （亦即，這是開發 Docker 的 Linux VM 的預設值外裝載），例如本機 SQL在您開發電腦上的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-149">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="3ec0b-150">另外還有其他，我們將討論下列各節中的更多進階的 docker compose.yml 設定。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-150">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="3ec0b-151">使用 docker-撰寫針對多個環境的檔案</span><span class="sxs-lookup"><span data-stu-id="3ec0b-151">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="3ec0b-152">Docker compose.yml 檔案會定義檔案，並可供多個基礎結構，以了解該格式。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-152">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="3ec0b-153">最簡單的工具是 docker-組成命令，但其他工具 (例如，Docker Swarm) orchestrators 也了解該檔案。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-153">The most straightforward tool is the docker-compose command, but other tools like orchestrators (for example, Docker Swarm) also understand that file.</span></span>

<span data-ttu-id="3ec0b-154">因此，藉由 docker 組成您可以以下列主要案例為目標的命令。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-154">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="3ec0b-155">開發環境</span><span class="sxs-lookup"><span data-stu-id="3ec0b-155">Development environments</span></span>

<span data-ttu-id="3ec0b-156">當您開發應用程式時，務必要能夠在隔離式的開發環境中執行的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-156">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="3ec0b-157">您可以使用 docker 撰寫建立該環境，或使用 Visual Studio 會使用 docker-撰寫實際上 CLI 命令。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-157">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="3ec0b-158">Docker compose.yml 檔案可讓您設定及文件的所有應用程式的服務依存性 （其他服務、 快取、 資料庫、 佇列等等）。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-158">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="3ec0b-159">使用 docker 組成 CLI 命令，您可以建立並啟動的每個相依的一個或多個容器，使用單一命令 （docker-撰寫組成）。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-159">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="3ec0b-160">Docker compose.yml 檔案是由 Docker 引擎所解譯的組態檔，但也可當做多容器應用程式的編撰詳細方便的文件檔。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-160">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="3ec0b-161">在測試環境</span><span class="sxs-lookup"><span data-stu-id="3ec0b-161">Testing environments</span></span>

<span data-ttu-id="3ec0b-162">任何連續部署 (CD) 或持續整合 (CI) 程序的重要部分是單元測試和整合測試。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-162">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="3ec0b-163">這些自動化的測試需要隔離的環境，因此不受影響的使用者或應用程式的資料中的任何其他變更。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-163">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="3ec0b-164">透過 Docker Compose 您可以建立和終結該隔離的環境非常輕鬆地中的幾個命令，從命令提示字元或指令碼，如下列命令：</span><span class="sxs-lookup"><span data-stu-id="3ec0b-164">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a><span data-ttu-id="3ec0b-165">生產部署</span><span class="sxs-lookup"><span data-stu-id="3ec0b-165">Production deployments</span></span>

<span data-ttu-id="3ec0b-166">您也可以使用部署至遠端 Docker 引擎的撰寫。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-166">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="3ec0b-167">典型的案例是將部署到單一的 Docker 主機執行個體 (實際執行 VM 或伺服器使用佈建[Docker 機器](https://docs.docker.com/machine/overview/))。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-167">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span> <span data-ttu-id="3ec0b-168">但它也可以是整個[Docker Swarm](https://docs.docker.com/swarm/overview/)叢集化，因為叢集也是 docker compose.yml 檔案相容。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-168">But it could also be an entire [Docker Swarm](https://docs.docker.com/swarm/overview/) cluster, because clusters are also compatible with the docker-compose.yml files.</span></span>

<span data-ttu-id="3ec0b-169">如果您使用任何其他 orchestrator （Azure Service Fabric、 Mesos DC/OS、 Kubernetes 等），您可能需要加入類似在 docker compose.yml，但在其他 orchestrator 所需的格式設定和中繼資料的組態設定。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-169">If you are using any other orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="3ec0b-170">在任何情況下，docker 撰寫雖然實際執行工作流程可能會隨著您使用 orchestrator 是開發、 測試及實際執行的工作流程，方便的工具和中繼資料格式。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-170">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="3ec0b-171">使用多個 docker-撰寫來處理數個環境的檔案</span><span class="sxs-lookup"><span data-stu-id="3ec0b-171">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="3ec0b-172">當目標為不同的環境，您應該使用多個構成的檔案。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-172">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="3ec0b-173">這可讓您建立多個組態變化視環境而定。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-173">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="3ec0b-174">覆寫基底 docker-compose 檔案</span><span class="sxs-lookup"><span data-stu-id="3ec0b-174">Overriding the base docker-compose file</span></span>

<span data-ttu-id="3ec0b-175">您可以使用單一的 docker compose.yml 檔案，如先前各節中所顯示的簡化範例所示。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-175">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="3ec0b-176">不過，不建議對於大部分應用程式。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-176">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="3ec0b-177">根據預設，撰寫讀取兩個檔案、 docker compose.yml 和選擇性的 docker compose.override.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-177">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="3ec0b-178">示在圖 8-11 中，當您使用 Visual Studio，並啟用 Docker 的支援，Visual Studio 也會建立這些檔案，以及用來偵錯某些其他檔案。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-178">As shown in Figure 8-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates those files plus some additional files used for debugging.</span></span>

![](./media/image12.png)

<span data-ttu-id="3ec0b-179">**圖 8-11**。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-179">**Figure 8-11**.</span></span> <span data-ttu-id="3ec0b-180">docker 撰寫 Visual Studio 2017 中的檔案</span><span class="sxs-lookup"><span data-stu-id="3ec0b-180">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="3ec0b-181">您可以使用任何編輯器，例如 Visual Studio 程式碼或適，編輯 docker-compose 檔案，並執行應用程式與 docker 撰寫 up 命令。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-181">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="3ec0b-182">依照慣例，docker compose.yml 檔案會包含基底組態及其他靜態的設定。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-182">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="3ec0b-183">這表示不應該根據您的目標部署環境變更服務組態。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-183">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="3ec0b-184">Docker compose.override.yml 檔案，如其名所示，包含覆寫基底組態，例如取決於部署環境的組態的組態設定。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-184">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="3ec0b-185">您也可以有多個具有不同名稱的覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-185">You can have multiple override files with different names also.</span></span> <span data-ttu-id="3ec0b-186">覆寫檔案通常會包含所需的應用程式但特定環境或部署的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-186">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="3ec0b-187">目標多個環境</span><span class="sxs-lookup"><span data-stu-id="3ec0b-187">Targeting multiple environments</span></span>

<span data-ttu-id="3ec0b-188">典型的使用案例是當您定義多個撰寫檔案讓您可鎖定目標多個環境，例如生產環境中，暫存、 CI 或開發。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-188">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="3ec0b-189">若要支援這些差異，您可以分割成多個檔案，您撰寫的組態所示圖 8-12。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-189">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 8-12.</span></span>

![](./media/image13.png)

<span data-ttu-id="3ec0b-190">**圖 8-12**。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-190">**Figure 8-12**.</span></span> <span data-ttu-id="3ec0b-191">多個 docker 撰寫檔案覆寫基底的 docker compose.yml 檔案中的值</span><span class="sxs-lookup"><span data-stu-id="3ec0b-191">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="3ec0b-192">您可以使用的基底的 docker compose.yml 啟動。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-192">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="3ec0b-193">此基底的檔案必須包含基底或靜態的組態設定不會變更視環境而定。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-193">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="3ec0b-194">比方說，eShopOnContainers 與基底的檔案具有下列 docker compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-194">For example, the eShopOnContainers has the following docker-compose.yml file as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '2'

services:
  basket.api:
    image: eshop/basket.api
    build:
    context: ./src/Services/Basket/Basket.API
    dockerfile: Dockerfile
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api
    build:
    context: ./src/Services/Catalog/Catalog.API
    dockerfile: Dockerfile
    depends_on:
      - sql.data
      - rabbitmq

  identity.api:
    image: eshop/identity.api
    build:
    context: ./src/Services/Identity/Identity.API
    dockerfile: Dockerfile
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    build:
    context: ./src/Services/Ordering/Ordering.API
    dockerfile: Dockerfile
    depends_on:
      - sql.data
      - rabbitmq

  webspa:
    image: eshop/webspa
    build:
    context: ./src/Web/WebSPA
    dockerfile: Dockerfile
    depends_on:
      - identity.api
      - basket.api

  webmvc:
    image: eshop/webmvc
    build:
    context: ./src/Web/WebMVC
    dockerfile: Dockerfile
    depends_on:
      - catalog.api
      - ordering.api
      - identity.api
      - basket.api

  sql.data:
    image: microsoft/mssql-server-linux
    basket.data:
    image: redis
    expose:
      - "6379"
    rabbitmq:
    image: rabbitmq
    ports:
      - "5672:5672"

  webstatus:
    image: eshop/webstatus
    build:
    context: ./src/Web/WebStatus
    dockerfile: Dockerfile
```

<span data-ttu-id="3ec0b-195">由於不同的目標部署環境，不應該變更基底的 docker compose.yml 檔案中的值。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-195">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="3ec0b-196">如果您專注於 webmvc 服務定義，比方說，您就可以查看該資訊的方式無論何種環境，您可能會將目標設為大致相同。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-196">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="3ec0b-197">您擁有下列資訊：</span><span class="sxs-lookup"><span data-stu-id="3ec0b-197">You have the following information:</span></span>

-   <span data-ttu-id="3ec0b-198">服務名稱： webmvc。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-198">The service name: webmvc.</span></span>

-   <span data-ttu-id="3ec0b-199">容器的自訂映像： 資格/webmvc。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-199">The container’s custom image: eshop/webmvc.</span></span>

-   <span data-ttu-id="3ec0b-200">若要建置自訂的 Docker 映像，指出要使用哪些 Dockerfile 指令。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-200">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

-   <span data-ttu-id="3ec0b-201">相依於其他服務，所以此容器會等到其他相依性容器已經啟動。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-201">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="3ec0b-202">您可以有額外的設定，但是重點是在基底的 docker compose.yml 檔案中，您只想要設定環境之間是共通的資訊。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-202">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="3ec0b-203">然後在 docker compose.override.yml 或類似檔案生產或預備環境中，您應該將針對每個環境的設定。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-203">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="3ec0b-204">通常，docker compose.override.yml 會使用您的開發環境，如下列範例從 eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="3ec0b-204">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '2'

services:
# Simplified number of services here:
  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:5101
      - ConnectionString=Server=sql.data; Database=Microsoft.eShopOnContainers.Services.CatalogDb; User Id=sa;Password=Pass@word
      - ExternalCatalogBaseUrl=http://localhost:5101
    ports:
      - "5101:5101"

  identity.api:
    environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:5105
    - SpaClient=http://localhost:5104
    - ConnectionStrings__DefaultConnection = Server=sql.data;Database=Microsoft.eShopOnContainers.Service.IdentityDb;User Id=sa;Password=Pass@word
    - MvcClient=http://localhost:5100
    ports:
      - "5105:5105"

  webspa:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:5104
      - CatalogUrl=http://localhost:5101
      - OrderingUrl=http://localhost:5102
      - IdentityUrl=http://localhost:5105
      - BasketUrl=http:// localhost:5103
    ports:
      - "5104:5104"

  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

<span data-ttu-id="3ec0b-205">在此範例中，開發覆寫組態公開 （expose） 至主機的某些連接埠，定義環境變數，以重新導向 Url，並指定連接字串以供開發環境。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-205">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="3ec0b-206">這些設定只是在開發環境。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-206">These settings are all just for the development environment.</span></span>

<span data-ttu-id="3ec0b-207">當您執行 docker 撰寫向上 （或從 Visual Studio 啟動它），此命令會讀取覆寫自動如同它已合併這兩個檔案。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-207">When you run docker-compose up (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="3ec0b-208">假設您想用於實際執行環境，具有不同的組態值的另一個撰寫檔案。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-208">Suppose that you want another Compose file for the production environment, with different configuration values.</span></span> <span data-ttu-id="3ec0b-209">您可以建立另一個覆寫檔案，如下所示。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-209">You can create another override file, like the following.</span></span> <span data-ttu-id="3ec0b-210">（這個檔案可能會儲存在不同的 Git 儲存機制或受管理和保護不同的小組。）</span><span class="sxs-lookup"><span data-stu-id="3ec0b-210">(This file might be stored in a different Git repo or managed and secured by a different team.)</span></span>

```yml
#docker-compose.prod.yml (Extended config for PRODUCTION env.)
version: '2'

services:
  # Simplified number of services here:
  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Production
      - ASPNETCORE_URLS=http://0.0.0.0:5101
      - ConnectionString=Server=sql.data; Database = Microsoft.eShopOnContainers.Services.CatalogDb; User Id=sa;Password=Prod@Pass
      - ExternalCatalogBaseUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5101
    ports:
      - "5101:5101"

  identity.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Production
      - ASPNETCORE_URLS=http://0.0.0.0:5105
      - SpaClient=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5104
      - ConnectionStrings__DefaultConnection = Server=sql.data;Database=Microsoft.eShopOnContainers.Service.IdentityDb;User Id=sa;Password=Pass@word
      - MvcClient=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5100
    ports:
      - "5105:5105"

  webspa:
    environment:
      - ASPNETCORE_ENVIRONMENT= Production
      - ASPNETCORE_URLS=http://0.0.0.0:5104
      - CatalogUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5101
      - OrderingUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5102
      - IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
      - BasketUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5103
    ports:
      - "5104:5104"

  sql.data:
    environment:
      - SA_PASSWORD=Prod@Pass
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="3ec0b-211">如何部署與特定覆寫檔案</span><span class="sxs-lookup"><span data-stu-id="3ec0b-211">How to deploy with a specific override file</span></span>

<span data-ttu-id="3ec0b-212">若要使用不同的名稱中使用多個覆寫檔案或覆寫檔案，您可以使用-f 選項與 docker 組成命令並指定的檔案。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-212">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="3ec0b-213">撰寫命令列指定的順序中的合併檔案。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-213">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="3ec0b-214">下列範例會示範如何使用覆寫檔案進行部署。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-214">The following example shows how to deploy with override files.</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="3ec0b-215">使用環境變數的 docker-撰寫檔案</span><span class="sxs-lookup"><span data-stu-id="3ec0b-215">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="3ec0b-216">很方便，尤其是在生產環境中，若要能夠從環境變數取得組態資訊，我們有在先前的範例所示。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-216">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="3ec0b-217">您使用語法 docker-compose 檔案中參考的環境變數\${MY\_VAR}。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-217">You reference an environment variable in your docker-compose files using the syntax \${MY\_VAR}.</span></span> <span data-ttu-id="3ec0b-218">Docker compose.prod.yml 檔案下列行示範如何參考環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-218">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="3ec0b-219">環境變數會建立並初始化在不同的方式，根據您的主機環境中 (Linux、 Windows、 雲端叢集等。)。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-219">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="3ec0b-220">不過，便利的方式是使用.env 檔案。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-220">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="3ec0b-221">Docker-compose 檔案支援宣告.env 檔案中的預設環境變數。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-221">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="3ec0b-222">這些環境變數的值是預設值。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-222">These values for the environment variables are the default values.</span></span> <span data-ttu-id="3ec0b-223">但您可能已經定義在每個環境 （主機作業系統或從您的叢集環境變數） 中的值覆寫。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-223">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="3ec0b-224">您將此.env 檔案放在資料夾位置 docker 撰寫從執行命令。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-224">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="3ec0b-225">下列範例顯示類似.env 檔案[.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) eShopOnContainers 應用程式檔案。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-225">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="3ec0b-226">Docker 撰寫預期.env 檔案格式中的每一行&lt;變數&gt;=&lt;值&gt;。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-226">Docker-compose expects each line in an .env file to be in the format &lt;variable&gt;=&lt;value&gt;.</span></span>

<span data-ttu-id="3ec0b-227">請注意，一律在執行階段環境中設定的值會覆寫.env 檔案內所定義的值。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-227">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="3ec0b-228">類似的方式，透過命令列命令引數傳遞的值也會覆寫.env 檔案中設定的預設值。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-228">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="3ec0b-229">其他資源</span><span class="sxs-lookup"><span data-stu-id="3ec0b-229">Additional resources</span></span>

-   <span data-ttu-id="3ec0b-230">**Docker 概觀撰寫**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span><span class="sxs-lookup"><span data-stu-id="3ec0b-230">**Overview of Docker Compose**
[*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span></span>

-   <span data-ttu-id="3ec0b-231">**多個撰寫檔案**
    [*https://docs.docker.com/compose/extends/\#多撰寫檔案*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span><span class="sxs-lookup"><span data-stu-id="3ec0b-231">**Multiple Compose files**
[*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span></span>

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="3ec0b-232">建置最佳化的 ASP.NET Core Docker 映像</span><span class="sxs-lookup"><span data-stu-id="3ec0b-232">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="3ec0b-233">如果您瀏覽 Docker 和.NET 核心上的網際網路來源，您會發現示範簡化建立 Docker 映像，藉由將您的來源複製到容器的 Dockerfiles。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-233">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="3ec0b-234">這些範例建議，藉由使用簡單的設定，您可以擁有的 Docker 映像會與您的應用程式一起封裝的環境。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-234">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="3ec0b-235">下列範例會顯示簡易的 Dockerfile 中此動作。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-235">The following example shows a simple Dockerfile in this vein.</span></span>

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="3ec0b-236">像這樣的 Dockerfile 會運作。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-236">A Dockerfile like this will work.</span></span> <span data-ttu-id="3ec0b-237">不過，您可以大幅最佳化您的映像，特別是您實際執行的映像。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-237">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="3ec0b-238">在容器和 microservices 模型中，您會不斷地啟動容器。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-238">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="3ec0b-239">因為容器是可處置，使用容器的一般方式不會重新啟動的睡眠中的容器。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-239">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="3ec0b-240">（例如 Docker Swarm、 Kubernetes、 DCOS 或 Azure Service Fabric） orchestrators 直接建立映像的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-240">Orchestrators (like Docker Swarm, Kubernetes, DCOS or Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="3ec0b-241">這就表示您需要讓具現化程序將會更快建置時，先行編譯應用程式最佳化。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-241">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="3ec0b-242">啟動容器時，它應該準備好執行。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-242">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="3ec0b-243">您不應該還原，並在執行階段編譯、 使用 dotnet 還原和 dotnet 建置 dotnet CLI 命令，許多有關.NET Core 及 Docker 的部落格文章中所示。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-243">You should not restore and compile at run time, using dotnet restore and dotnet build commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="3ec0b-244">.NET 小組已執行重要的工作，讓.NET Core 與 ASP.NET Core 容器最佳化的架構。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-244">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="3ec0b-245">不只是一個輕量型架構與較小的記憶體耗用量;.NET Core小組已將焦點放在 啟動效能和產生某些最佳化的 Docker 映像，例如[microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)映像可在[Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/)，相較於一般[microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/)或[microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile)映像。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-245">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on startup performance and produced some optimized Docker images, like the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image available at [Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), in comparison to the regular [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) or [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) images.</span></span> <span data-ttu-id="3ec0b-246">[Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)映像提供自動設定的 aspnetcore\_url 以連接埠 80 和前 ngend 快取的組件; 這兩個選項會導致更快速啟動。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-246">The [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image provides automatic setting of aspnetcore\_urls to port 80 and the pre-ngend cache of assemblies; both of these settings result in faster startup.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="3ec0b-247">其他資源</span><span class="sxs-lookup"><span data-stu-id="3ec0b-247">Additional resources</span></span>

-   <span data-ttu-id="3ec0b-248">**建置最佳化與 ASP.NET Core Docker Images**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span><span class="sxs-lookup"><span data-stu-id="3ec0b-248">**Building Optimized Docker Images with ASP.NET Core**
[*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span></span>

### <a name="building-the-application-from-a-build-ci-container"></a><span data-ttu-id="3ec0b-249">建置應用程式從組建 (CI) 容器</span><span class="sxs-lookup"><span data-stu-id="3ec0b-249">Building the application from a build (CI) container</span></span>

<span data-ttu-id="3ec0b-250">Docker 的另一個優點是您可以建置您的應用程式，從預先設定的容器，為顯示在圖 8-13，因此您不需要建立組建電腦或 VM 來建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-250">Another benefit of Docker is that you can build your application from a preconfigured container, as shown in Figure 8-13, so you do not need to create a build machine or VM to build your application.</span></span> <span data-ttu-id="3ec0b-251">您可以使用或執行您的開發電腦上，以測試該組建容器。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-251">You can use or test that build container by running it at your development machine.</span></span> <span data-ttu-id="3ec0b-252">但更有趣的是，您可以使用相同的組建容器從 CI （連續整合） 管線。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-252">But what is even more interesting is that you can use the same build container from your CI (Continuous Integration) pipeline.</span></span>

![](./media/image14.png)

<span data-ttu-id="3ec0b-253">**圖 8-13**。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-253">**Figure 8-13**.</span></span> <span data-ttu-id="3ec0b-254">建立.NET 從容器的位元的元件</span><span class="sxs-lookup"><span data-stu-id="3ec0b-254">Components building .NET bits from a container</span></span>

<span data-ttu-id="3ec0b-255">針對此案例中，我們提供[microsoft/aspnetcore 建置](https://hub.docker.com/r/microsoft/aspnetcore-build/)映像，您可以使用編譯和建置您的 ASP.NET 核心應用程式。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-255">For this scenario, we provide the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image, which you can use to compile and build your ASP.NET Core apps.</span></span> <span data-ttu-id="3ec0b-256">將輸出放在基礎映像[microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)映像，執行階段最佳化映像，如先前所述。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-256">The output is placed in an image based on the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image, which is an optimized runtime image, as previously noted.</span></span>

<span data-ttu-id="3ec0b-257">Aspnetcore 建置映像包含所需的所有以編譯 ASP.NET Core 應用程式，包括.NET Core、 ASP.NET SDK、 npm Bower、 Gulp、 等等。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-257">The aspnetcore-build image contains everything you need in order to compile an ASP.NET Core application, including .NET Core, the ASP.NET SDK, npm, Bower, Gulp, etc.</span></span>

<span data-ttu-id="3ec0b-258">在建置階段，我們就會需要這些相依性。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-258">We need these dependencies at build time.</span></span> <span data-ttu-id="3ec0b-259">但我們不想要執行這些應用程式在執行階段，因為它會使映像不必要地大。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-259">But we do not want to carry these with the application at runtime, because it would make the image unnecessarily large.</span></span> <span data-ttu-id="3ec0b-260">在 eShopOnContainers 應用程式中，您可以建置應用程式從只執行容器下 docker-撰寫命令。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-260">In the eShopOnContainers application, you can build the application from a container by just running the following docker-compose command.</span></span>

```
  docker-compose -f docker-compose.ci.build.yml up
```

<span data-ttu-id="3ec0b-261">圖 8-14 顯示在命令列執行此命令。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-261">Figure 8-14 shows this command running at the command line.</span></span>

![](./media/image15.png)

<span data-ttu-id="3ec0b-262">**圖 8-14 版。**</span><span class="sxs-lookup"><span data-stu-id="3ec0b-262">**Figure 8-14.**</span></span> <span data-ttu-id="3ec0b-263">建置您的.NET 應用程式，從容器</span><span class="sxs-lookup"><span data-stu-id="3ec0b-263">Building your .NET application from a container</span></span>

<span data-ttu-id="3ec0b-264">如您所見，正在執行的容器是 ci 組建\_1 的容器。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-264">As you can see, the container that is running is the ci-build\_1 container.</span></span> <span data-ttu-id="3ec0b-265">這根據 aspnetcore 建置映像，使它可以編譯和建置整個應用程式而不是該容器內，從您的電腦。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-265">This is based on the aspnetcore-build image so that it can compile and build your whole application from within that container instead of from your PC.</span></span> <span data-ttu-id="3ec0b-266">也就是為什麼實際上它會建置和編譯.NET Core 專案，在 Linux 中的，因為該容器預設 Docker 的 Linux 主機上執行。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-266">That is why in reality it is building and compiling the .NET Core projects in Linux—because that container is running on the default Docker Linux host.</span></span>

<span data-ttu-id="3ec0b-267">[Docker compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml)該映像 （eShopOnContainers 的一部份） 包含下列程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-267">The [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) file for that image (part of eShopOnContainers) contains the following code.</span></span> <span data-ttu-id="3ec0b-268">您可以看到它啟動組建的容器使用[microsoft/aspnetcore 建置](https://hub.docker.com/r/microsoft/aspnetcore-build/)映像。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-268">You can see that it starts a build container using the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image.</span></span>

```yml
version: '2'
  services:
    ci-build:
      image: microsoft/aspnetcore-build:1.0-1.1
      volumes:
        - .:/src
      working_dir: /src
      command: /bin/bash -c "pushd ./src/Web/WebSPA && npm rebuild node-sass && pushd ./../../.. && dotnet restore ./eShopOnContainers-ServicesAndWebApps.sln && dotnet publish ./eShopOnContainers-ServicesAndWebApps.sln -c Release -o ./obj/Docker/publish"
```

* <span data-ttu-id="3ec0b-269">從開始**.NET Core 2.0**，`dotnet restore`會自動執行命令時`dotnet publish`執行命令。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-269">Starting with **.NET Core 2.0**, `dotnet restore` command executes automatically when the `dotnet publish` command is executed.</span></span>

<span data-ttu-id="3ec0b-270">一旦組建容器已啟動並執行，這會執行.NET SDK dotnet 還原，而且 dotnet 發行方案中針對所有專案的命令，以編譯的.NET 位元。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-270">Once the build container is up and running, it runs the .NET SDK dotnet restore and dotnet publish commands against all the projects in the solution in order to compile the .NET bits.</span></span> <span data-ttu-id="3ec0b-271">在此情況下，因為 eShopOnContainers 也有 SPA TypeScript 和 Angular 根據用戶端程式碼，也必須檢查 npm 與 JavaScript 相依性，但動作不相關的.NET 位元。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-271">In this case, because eShopOnContainers also has an SPA based on TypeScript and Angular for the client code, it also needs to check JavaScript dependencies with npm, but that action is not related to the .NET bits.</span></span>

<span data-ttu-id="3ec0b-272">Dotnet 發行命令組建和發行的每個專案的資料夾內的已編譯的輸出.../obj/Docker/publish 資料夾，如圖 8-15 所示。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-272">The dotnet publish command builds and publishes the compiled output within each project’s folder to the ../obj/Docker/publish folder, as shown in Figure 8-15.</span></span>

![](./media/image16.png)

<span data-ttu-id="3ec0b-273">**圖 8-15。**</span><span class="sxs-lookup"><span data-stu-id="3ec0b-273">**Figure 8-15.**</span></span> <span data-ttu-id="3ec0b-274">Dotnet 所產生的二進位檔案發行命令</span><span class="sxs-lookup"><span data-stu-id="3ec0b-274">Binary files generated by the dotnet publish command</span></span>

#### <a name="creating-the-docker-images-from-the-cli"></a><span data-ttu-id="3ec0b-275">從 CLI 建立 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="3ec0b-275">Creating the Docker images from the CLI</span></span>

<span data-ttu-id="3ec0b-276">一旦應用程式輸出發行至相關的資料夾 （在每一個專案中） 時下, 一個步驟是實際建置 Docker images。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-276">Once the application output is published to the related folders (within each project), the next step is to actually build the Docker images.</span></span> <span data-ttu-id="3ec0b-277">若要這樣做，您可以使用 docker-compose 組建並 docker-撰寫向上命令，如圖 8-16 中所示。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-277">To do this, you use the docker-compose build and docker-compose up commands, as shown in Figure 8-16.</span></span>

![](./media/image17.png)

<span data-ttu-id="3ec0b-278">**圖 8-16。**</span><span class="sxs-lookup"><span data-stu-id="3ec0b-278">**Figure 8-16.**</span></span> <span data-ttu-id="3ec0b-279">建立 Docker 映像和執行容器</span><span class="sxs-lookup"><span data-stu-id="3ec0b-279">Building Docker images and running the containers</span></span>

<span data-ttu-id="3ec0b-280">在圖 8-17，您可以看到 docker-compose 如何建置執行命令。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-280">In Figure 8-17, you can see how the docker-compose build command runs.</span></span>

![](./media/image18.png)

<span data-ttu-id="3ec0b-281">**圖 8-17**。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-281">**Figure 8-17**.</span></span> <span data-ttu-id="3ec0b-282">使用 docker 建置 Docker images-撰寫建置命令</span><span class="sxs-lookup"><span data-stu-id="3ec0b-282">Building the Docker images with the docker-compose build command</span></span>

<span data-ttu-id="3ec0b-283">建置 docker-compose 之間的差異，並向上 docker 撰寫命令是 docker 撰寫組建和啟動映像。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-283">The difference between the docker-compose build and docker-compose up commands is that docker-compose up both builds and starts the images.</span></span>

<span data-ttu-id="3ec0b-284">當您使用 Visual Studio 時，在幕後執行所有這些步驟。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-284">When you use Visual Studio, all these steps are performed under the covers.</span></span> <span data-ttu-id="3ec0b-285">Visual Studio 編譯的.NET 應用程式、 建立 Docker 映像中，並將容器部署至 Docker 主機。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-285">Visual Studio compiles your .NET application, creates the Docker images, and deploys the containers into the Docker host.</span></span> <span data-ttu-id="3ec0b-286">Visual Studio 會提供額外的功能，例如您在 Docker 執行直接從 Visual Studio 的容器的偵錯功能。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-286">Visual Studio offers additional features, like the ability to debug your containers running in Docker, directly from Visual Studio.</span></span>

<span data-ttu-id="3ec0b-287">整體的 takeway 是，您可以建置您的應用程式相同的方式，應該建立該 CI/CD 管線 — 從容器而不是從本機電腦。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-287">The overall takeway here is that you are able to build your application the same way your CI/CD pipeline should build it—from a container instead of from a local machine.</span></span> <span data-ttu-id="3ec0b-288">之後建立的映像，則您只需要執行的 Docker 映像使用 docker-撰寫 up 命令。</span><span class="sxs-lookup"><span data-stu-id="3ec0b-288">After having the images created, then you just need to run the Docker images using the docker-compose up command.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="3ec0b-289">其他資源</span><span class="sxs-lookup"><span data-stu-id="3ec0b-289">Additional resources</span></span>

-   <span data-ttu-id="3ec0b-290">**建立從容器的位元： Windows CLI 環境 (dotnet CLI，Docker CLI 和 VS Code) 中設定 eShopOnContainers 方案**
    [*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span><span class="sxs-lookup"><span data-stu-id="3ec0b-290">**Building bits from a container: Setting the eShopOnContainers solution up in a Windows CLI environment (dotnet CLI, Docker CLI and VS Code)**
[*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="3ec0b-291">[上一個](資料-驅動-crud-microservice.md) [下一步] (資料庫的伺服器-container.md)</span><span class="sxs-lookup"><span data-stu-id="3ec0b-291">[Previous] (data-driven-crud-microservice.md) [Next] (database-server-container.md)</span></span>
