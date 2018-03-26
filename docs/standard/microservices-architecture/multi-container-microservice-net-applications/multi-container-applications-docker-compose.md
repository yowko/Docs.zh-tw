---
title: 使用 docker-compose.yml 定義多容器應用程式
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 使用 docker-compose.yml 定義多容器應用程式
keywords: Docker, 微服務, ASP.NET, 容器
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c4fed5c7ba5c2048d103f22bd2b463c143013280
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/26/2018
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="7b264-104">使用 docker-compose.yml 定義多容器應用程式</span><span class="sxs-lookup"><span data-stu-id="7b264-104">Defining your multi-container application with docker-compose.yml</span></span> 

<span data-ttu-id="7b264-105">在本指南中，[docker-compose.yml](https://docs.docker.com/compose/compose-file/) 檔案是在下列這節中介紹：[步驟 4.建置多容器 Docker 應用程式時，在 docker-compose.yml 中定義您的服務](#step4_define_svcs_in_docker_compose_yml)。</span><span class="sxs-lookup"><span data-stu-id="7b264-105">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](#step4_define_svcs_in_docker_compose_yml).</span></span> <span data-ttu-id="7b264-106">不過，有一些其他方法可以使用值得深入探索的 docker-compose 檔案。</span><span class="sxs-lookup"><span data-stu-id="7b264-106">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="7b264-107">例如，您可以明確地描述要如何在 docker-compose.yml 檔案中部署多容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="7b264-107">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="7b264-108">您也可以選擇性地描述要如何建置自訂 Docker 映像 </span><span class="sxs-lookup"><span data-stu-id="7b264-108">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="7b264-109">(也可以使用 Docker CLI 來建置自訂 Docker 映像)。</span><span class="sxs-lookup"><span data-stu-id="7b264-109">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="7b264-110">基本上，您會定義您想要部署的每個容器，以及每個容器部署的特定特性。</span><span class="sxs-lookup"><span data-stu-id="7b264-110">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="7b264-111">具有多容器部署描述檔案之後，即可使用單一動作部署 [docker-compose up](https://docs.docker.com/compose/overview/) CLI 命令所協調的整個解決方案，或可從 Visual Studio 透明地進行部署。</span><span class="sxs-lookup"><span data-stu-id="7b264-111">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="7b264-112">否則，您必須使用 Docker CLI，從命令列使用 docker run 命令，透過多個步驟逐一部署容器。</span><span class="sxs-lookup"><span data-stu-id="7b264-112">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the docker run command from the command line.</span></span> <span data-ttu-id="7b264-113">因此，docker-compose.yml 中所定義的每個服務都只能指定一個映像或組建。</span><span class="sxs-lookup"><span data-stu-id="7b264-113">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="7b264-114">其他金鑰是選擇性的，而且類似其 docker run 命令列對應項目。</span><span class="sxs-lookup"><span data-stu-id="7b264-114">Other keys are optional, and are analogous to their docker run command-line counterparts.</span></span>

<span data-ttu-id="7b264-115">下列 YAML 程式碼是 eShopOnContainers 範例之可能全域但單一 docker-compose.yml 檔案的定義。</span><span class="sxs-lookup"><span data-stu-id="7b264-115">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="7b264-116">這不是 eShopOnContainers 中的實際 docker-compose 檔案。</span><span class="sxs-lookup"><span data-stu-id="7b264-116">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="7b264-117">相反地，它是單一檔案中的簡化和合併版本，但這不是使用 docker-compose 檔案的最佳方式，我們將會在稍後進行說明。</span><span class="sxs-lookup"><span data-stu-id="7b264-117">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

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

<span data-ttu-id="7b264-118">此檔案中的根金鑰就是服務。</span><span class="sxs-lookup"><span data-stu-id="7b264-118">The root key in this file is services.</span></span> <span data-ttu-id="7b264-119">在該金鑰下，您定義想要在執行 docker-compose up 命令或是使用此 docker-compose.yml 檔案從 Visual Studio 部署時所部署和執行的服務。</span><span class="sxs-lookup"><span data-stu-id="7b264-119">Under that key you define the services you want to deploy and run when you execute the docker-compose up command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="7b264-120">在此情況下，docker-compose.yml 檔案已定義多個服務，如下列清單所述。</span><span class="sxs-lookup"><span data-stu-id="7b264-120">In this case, the docker-compose.yml file has multiple services defined, as described in the following list.</span></span>

-   <span data-ttu-id="7b264-121">webmvc 容器，包括使用伺服器端 C\# 之微服務的 ASP.NET Core MVC 應用程式</span><span class="sxs-lookup"><span data-stu-id="7b264-121">webmvc Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>

-   <span data-ttu-id="7b264-122">catalog.api 容器，包括 Catalog ASP.NET Core Web API 微服務</span><span class="sxs-lookup"><span data-stu-id="7b264-122">catalog.api Container including the Catalog ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="7b264-123">ordering.api 容器，包括 Ordering ASP.NET Core Web API 微服務</span><span class="sxs-lookup"><span data-stu-id="7b264-123">ordering.api Container including the Ordering ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="7b264-124">執行 SQL Server for Linux 的 sql.data 容器，保留微服務資料庫</span><span class="sxs-lookup"><span data-stu-id="7b264-124">sql.data Container running SQL Server for Linux, holding the microservices databases</span></span>

-   <span data-ttu-id="7b264-125">具有 Basket ASP.NET Core Web API 微服務的 basket.api 容器</span><span class="sxs-lookup"><span data-stu-id="7b264-125">basket.api Container with the Basket ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="7b264-126">執行 REDIS 快取服務的 basket.data 容器，其將購物籃資料庫作為 REDIS 快取</span><span class="sxs-lookup"><span data-stu-id="7b264-126">basket.data Container running the REDIS cache service, with the basket database as a REDIS cache</span></span>

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="7b264-127">簡單 Web 服務 API 容器</span><span class="sxs-lookup"><span data-stu-id="7b264-127">A simple Web Service API container</span></span>

<span data-ttu-id="7b264-128">catalog.api container-microservice 聚焦於單一容器，因此具有簡單易懂的定義：</span><span class="sxs-lookup"><span data-stu-id="7b264-128">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

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

<span data-ttu-id="7b264-129">此容器化服務具有下列基本組態：</span><span class="sxs-lookup"><span data-stu-id="7b264-129">This containerized service has the following basic configuration:</span></span>

-   <span data-ttu-id="7b264-130">它是根據自訂 eshop/catalog.api 映像。</span><span class="sxs-lookup"><span data-stu-id="7b264-130">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="7b264-131">為求簡化，檔案中沒有 build: 金鑰設定。</span><span class="sxs-lookup"><span data-stu-id="7b264-131">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="7b264-132">這表示必須先前已建置映像 (使用 docker build) 或已從任何 Docker 登錄下載映像 (使用 docker pull 命令)。</span><span class="sxs-lookup"><span data-stu-id="7b264-132">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

-   <span data-ttu-id="7b264-133">它會使用 Entity Framework 用來存取包含目錄資料模型之 SQL Server 執行個體的連接字串，來定義名為 ConnectionString 的環境變數。</span><span class="sxs-lookup"><span data-stu-id="7b264-133">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="7b264-134">在此情況下，相同的 SQL Server 容器會保留多個資料庫。</span><span class="sxs-lookup"><span data-stu-id="7b264-134">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="7b264-135">因此，您需要 Docker 的開發電腦中有較少的記憶體。</span><span class="sxs-lookup"><span data-stu-id="7b264-135">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="7b264-136">不過，您也可以為每個微服務資料庫部署一個 SQL Server 容器。</span><span class="sxs-lookup"><span data-stu-id="7b264-136">However, you could also deploy one SQL Server container for each microservice database.</span></span>

-   <span data-ttu-id="7b264-137">SQL Server 名稱是 sql.data，而這個相同名稱用於執行適用於 Linux 之 SQL Server 執行個體的容器。</span><span class="sxs-lookup"><span data-stu-id="7b264-137">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="7b264-138">這樣十分方便；可使用此名稱解析 (Docker 主機內部) 將會解析網路位址，因此您不需要知道從其他容器存取之容器的內部 IP。</span><span class="sxs-lookup"><span data-stu-id="7b264-138">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="7b264-139">因為連接字串是透過環境變數所定義，所以您可以透過不同的機制並在不同的時間來設定該變數。</span><span class="sxs-lookup"><span data-stu-id="7b264-139">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="7b264-140">例如，在最終主機中部署至生產環境時，您可以設定不同的連接字串，或是從 VSTS 或偏好 DevOps 系統中的 CI/CD 管道進行。</span><span class="sxs-lookup"><span data-stu-id="7b264-140">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in VSTS or your preferred DevOps system.</span></span>

-   <span data-ttu-id="7b264-141">它會公開連接埠 80，以對 Docker 主機內的 catalog.api 服務進行內部存取。</span><span class="sxs-lookup"><span data-stu-id="7b264-141">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="7b264-142">該主機目前是 Linux VM，因為它是根據適用於 Linux 的 Docker 映像，但您可以改為設定在 Windows 映像上執行容器。</span><span class="sxs-lookup"><span data-stu-id="7b264-142">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

-   <span data-ttu-id="7b264-143">它會將容器上的公開連接埠 80 轉送至 Docker 主機 (Linux VM) 上的連接埠 5101。</span><span class="sxs-lookup"><span data-stu-id="7b264-143">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

-   <span data-ttu-id="7b264-144">它會將 Web 服務連結至 sql.data 服務 (適用於容器中所執行 Linux 資料庫的 SQL Server 執行個體)。</span><span class="sxs-lookup"><span data-stu-id="7b264-144">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="7b264-145">當您指定此相依性時，除非已啟動 sql.data 容器，否則不會啟動 catalog.api 容器；這十分重要，因為 catalog.api 需要先啟動並執行 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="7b264-145">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="7b264-146">不過，在許多情況下，這種容器相依性不足，因為 Docker 只會在容器層級進行檢查。</span><span class="sxs-lookup"><span data-stu-id="7b264-146">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="7b264-147">服務 (在此情況下是 SQL Server) 有時可能仍然未準備就緒，因此建議您在用戶端微服務中實作含指數輪詢的重試邏輯。</span><span class="sxs-lookup"><span data-stu-id="7b264-147">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="7b264-148">這樣一來，如果相依性容器短時間內無法準備好，則應用程式仍會具有恢復功能。</span><span class="sxs-lookup"><span data-stu-id="7b264-148">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

-   <span data-ttu-id="7b264-149">它是設定為允許存取外部伺服器：extra\_hosts 設定可讓您存取外部伺服器或 Docker 主機外部的電腦 (亦即，本身為開發 Docker 本機的預設 Linux VM 外部)，例如開發電腦上的本機 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b264-149">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="7b264-150">另外還有其他更進階的 docker-compose.yml 設定，我們將在下列各節進行討論。</span><span class="sxs-lookup"><span data-stu-id="7b264-150">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="7b264-151">使用 docker-compose 檔案以多個環境為目標</span><span class="sxs-lookup"><span data-stu-id="7b264-151">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="7b264-152">docker-compose.yml 檔案是定義檔，而且可以供了解該格式的多個基礎結構使用。</span><span class="sxs-lookup"><span data-stu-id="7b264-152">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="7b264-153">最簡單的工具是 docker-compose 命令，但協調器這類其他工具 (例如，Docker Swarm) 也了解該檔案。</span><span class="sxs-lookup"><span data-stu-id="7b264-153">The most straightforward tool is the docker-compose command, but other tools like orchestrators (for example, Docker Swarm) also understand that file.</span></span>

<span data-ttu-id="7b264-154">因此，使用 docker-compose 命令，即可將目標設為下列主要案例。</span><span class="sxs-lookup"><span data-stu-id="7b264-154">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="7b264-155">開發環境</span><span class="sxs-lookup"><span data-stu-id="7b264-155">Development environments</span></span>

<span data-ttu-id="7b264-156">當您開發應用程式時，務必要能夠在隔離開發環境中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="7b264-156">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="7b264-157">您可以使用 docker-compose CLI 命令來建立該環境，或使用在幕後使用 docker-compose 的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="7b264-157">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="7b264-158">docker-compose.yml 檔案可讓您設定和記載所有應用程式的服務相依性 (其他服務、快取、資料庫、佇列等等)。</span><span class="sxs-lookup"><span data-stu-id="7b264-158">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="7b264-159">使用 docker-compose CLI 命令，您可以使用單一命令 (docker-compose up) 來建立和啟動每個相依性的一或多個容器。</span><span class="sxs-lookup"><span data-stu-id="7b264-159">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="7b264-160">docker-compose.yml 檔案不只是 Docker 引擎所解譯的組態檔，也是組合多容器應用程式的便利文件檔案。</span><span class="sxs-lookup"><span data-stu-id="7b264-160">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="7b264-161">測試環境</span><span class="sxs-lookup"><span data-stu-id="7b264-161">Testing environments</span></span>

<span data-ttu-id="7b264-162">任何持續部署 (CD) 或持續整合 (CI) 程序的重要部分都是單元測試和整合測試。</span><span class="sxs-lookup"><span data-stu-id="7b264-162">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="7b264-163">這些自動化測試需要隔離環境，因此它們不受使用者或應用程式資料中的任何其他變更所影響。</span><span class="sxs-lookup"><span data-stu-id="7b264-163">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="7b264-164">使用 Docker Compose，您可以從命令提示字元或指令碼，使用幾個命令非常輕鬆地建立和終結該隔離環境，例如下列命令：</span><span class="sxs-lookup"><span data-stu-id="7b264-164">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a><span data-ttu-id="7b264-165">生產部署</span><span class="sxs-lookup"><span data-stu-id="7b264-165">Production deployments</span></span>

<span data-ttu-id="7b264-166">您也可以使用 Compose 部署至遠端 Docker 引擎。</span><span class="sxs-lookup"><span data-stu-id="7b264-166">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="7b264-167">典型案例是部署至單一 Docker 主機執行個體 (例如，使用 [Docker 電腦](https://docs.docker.com/machine/overview/)所佈建的生產 VM 或伺服器)。</span><span class="sxs-lookup"><span data-stu-id="7b264-167">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span> <span data-ttu-id="7b264-168">但它也可以是整個 [Docker Swarm](https://docs.docker.com/swarm/overview/) 叢集，因為叢集也與 docker-compose.yml 檔案相容。</span><span class="sxs-lookup"><span data-stu-id="7b264-168">But it could also be an entire [Docker Swarm](https://docs.docker.com/swarm/overview/) cluster, because clusters are also compatible with the docker-compose.yml files.</span></span>

<span data-ttu-id="7b264-169">如果您使用任何其他協調器 (Azure Service Fabric、Mesos DC/OS、Kubernetes 等等)，則可能需要新增 docker-compose.yml 中的設定和中繼資料組態設定，但為其他協調器所需的格式。</span><span class="sxs-lookup"><span data-stu-id="7b264-169">If you are using any other orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="7b264-170">在任何情況下，雖然生產工作流程可能會隨著您使用的協調器而不同，但是 docker-compose 是開發、測試和生產工作流程的便利工具和中繼資料格式。</span><span class="sxs-lookup"><span data-stu-id="7b264-170">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="7b264-171">使用多個 docker-compose 檔案來處理數個環境</span><span class="sxs-lookup"><span data-stu-id="7b264-171">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="7b264-172">以不同環境為目標時，您應該使用多個 Compose 檔案。</span><span class="sxs-lookup"><span data-stu-id="7b264-172">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="7b264-173">根據環境，這可讓您建立多個組態變化。</span><span class="sxs-lookup"><span data-stu-id="7b264-173">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="7b264-174">覆寫基底 docker-compose 檔案</span><span class="sxs-lookup"><span data-stu-id="7b264-174">Overriding the base docker-compose file</span></span>

<span data-ttu-id="7b264-175">您可以使用單一 docker-compose.yml 檔案，如先前各節中所顯示的簡化範例所示。</span><span class="sxs-lookup"><span data-stu-id="7b264-175">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="7b264-176">不過，不建議用於大部分應用程式。</span><span class="sxs-lookup"><span data-stu-id="7b264-176">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="7b264-177">Compose 預設會讀取兩個檔案、docker-compose.yml 和選擇性 docker-compose.override.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="7b264-177">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="7b264-178">如圖 8-11 所示，當您要使用 Visual Studio 並啟用 Docker 支援時，Visual Studio 也會建立其他 docker-compose.ci.build.yml 檔案，以供您從 CI/CD 管道 (例如在 VSTS 中) 使用。</span><span class="sxs-lookup"><span data-stu-id="7b264-178">As shown in Figure 8-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.ci.build,yml file for you to use from your CI/CD pipelines like in VSTS.</span></span>

![](./media/image12.png)

<span data-ttu-id="7b264-179">**圖 8-11**.</span><span class="sxs-lookup"><span data-stu-id="7b264-179">**Figure 8-11**.</span></span> <span data-ttu-id="7b264-180">Visual Studio 2017 中的 docker-compose 檔案</span><span class="sxs-lookup"><span data-stu-id="7b264-180">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="7b264-181">您可以使用任何編輯器 (如 Visual Studio Code 或 Sublime) 來編輯 docker-compose 檔案，並使用 docker-compose up 命令來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="7b264-181">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="7b264-182">依照慣例，docker compose.yml 檔案會包含基底組態和其他靜態設定。</span><span class="sxs-lookup"><span data-stu-id="7b264-182">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="7b264-183">這表示根據您設為目標的部署環境，服務組態不應該變更。</span><span class="sxs-lookup"><span data-stu-id="7b264-183">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="7b264-184">docker-compose.override.yml 檔案，如其名所示，包含可覆寫基底組態的組態設定，例如取決於部署環境的組態。</span><span class="sxs-lookup"><span data-stu-id="7b264-184">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="7b264-185">您也可以有多個具有不同名稱的覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="7b264-185">You can have multiple override files with different names also.</span></span> <span data-ttu-id="7b264-186">覆寫檔案通常會包含應用程式所需要但為環境或部署特有的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="7b264-186">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="7b264-187">以多個環境為目標</span><span class="sxs-lookup"><span data-stu-id="7b264-187">Targeting multiple environments</span></span>

<span data-ttu-id="7b264-188">典型使用案例是定義多個 Compose 檔案，讓您可以將目標設為多個環境，例如生產環境、暫存環境、CI 或開發。</span><span class="sxs-lookup"><span data-stu-id="7b264-188">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="7b264-189">若要支援這些差異，您可以將 Compose 組態分割成多個檔案，如圖 8-12 所示。</span><span class="sxs-lookup"><span data-stu-id="7b264-189">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 8-12.</span></span>

![](./media/image13.png)

<span data-ttu-id="7b264-190">**圖 8-12**.</span><span class="sxs-lookup"><span data-stu-id="7b264-190">**Figure 8-12**.</span></span> <span data-ttu-id="7b264-191">覆寫基底 docker-compose.yml 檔案中值的多個 docker-compose 檔案</span><span class="sxs-lookup"><span data-stu-id="7b264-191">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="7b264-192">您可以開始使用基底 docker-compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="7b264-192">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="7b264-193">此基底檔案必須包含不會根據環境而變更的基底或靜態組態設定。</span><span class="sxs-lookup"><span data-stu-id="7b264-193">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="7b264-194">例如，eShopOnContainers 具有下列與基底檔案相同的 docker-compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="7b264-194">For example, the eShopOnContainers has the following docker-compose.yml file as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '3'
services:
  basket.api:
    image: eshop/basket.api:${TAG:-latest}
    build:
      context: ./src/Services/Basket/Basket.API
      dockerfile: Dockerfile    
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api:${TAG:-latest}
    build:
      context: ./src/Services/Catalog/Catalog.API
      dockerfile: Dockerfile    
    depends_on:
      - sql.data
      - rabbitmq

  marketing.api:
    image: eshop/marketing.api:${TAG:-latest}
    build:
      context: ./src/Services/Marketing/Marketing.API
      dockerfile: Dockerfile    
    depends_on:
      - sql.data
      - nosql.data
      - identity.api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: ./src/Web/WebMVC
      dockerfile: Dockerfile    
    depends_on:
      - catalog.api
      - ordering.api
      - identity.api
      - basket.api
      - marketing.api

  sql.data:
    image: microsoft/mssql-server-linux:2017-latest

  nosql.data:
    image: mongo

  basket.data:
    image: redis
      
  rabbitmq:
    image: rabbitmq:3-management

```

<span data-ttu-id="7b264-195">因為目標部署環境不同，所以基底 docker-compose.yml 檔案中的值不應該變更。</span><span class="sxs-lookup"><span data-stu-id="7b264-195">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="7b264-196">例如，如果您專注於 webmvc 服務定義，就可以看到該資訊大致相同，不論您將哪種環境設為目標。</span><span class="sxs-lookup"><span data-stu-id="7b264-196">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="7b264-197">您具有下列資訊：</span><span class="sxs-lookup"><span data-stu-id="7b264-197">You have the following information:</span></span>

-   <span data-ttu-id="7b264-198">服務名稱：webmvc。</span><span class="sxs-lookup"><span data-stu-id="7b264-198">The service name: webmvc.</span></span>

-   <span data-ttu-id="7b264-199">容器的自訂映像：eshop/webmvc。</span><span class="sxs-lookup"><span data-stu-id="7b264-199">The container’s custom image: eshop/webmvc.</span></span>

-   <span data-ttu-id="7b264-200">建置自訂 Docker 映像的命令，指出要使用的 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="7b264-200">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

-   <span data-ttu-id="7b264-201">與其他服務的相依性，因此，除非已啟動其他相依性容器，否則不會啟動此容器。</span><span class="sxs-lookup"><span data-stu-id="7b264-201">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="7b264-202">您可以有額外組態，但重點是在基底 docker-compose.yml 檔案中，您只想要設定環境之間通用的資訊。</span><span class="sxs-lookup"><span data-stu-id="7b264-202">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="7b264-203">然後在 docker-compose.override.yml 或是生產或預備環境的類似檔案中，您應該放置每個環境特有的組態。</span><span class="sxs-lookup"><span data-stu-id="7b264-203">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="7b264-204">通常，docker-compose.override.yml 會用於您的開發環境，如 eShopOnContainers 中的下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="7b264-204">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3'

services: 
# Simplified number of services here: 
      
  basket.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basket.data}
      - identityUrl=http://identity.api              
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}      
      - AzureServiceBusEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}

    ports:
      - "5103:80"

  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5101/api/v1/catalog/items/[0]/pic/}   
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}         
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_CATALOG_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_CATALOG_KEY}
      - UseCustomizationData=True
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
    ports:
      - "5101:80"

  marketing.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=Pass@word}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}          
      - identityUrl=http://identity.api              
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - CampaignDetailFunctionUri=${ESHOP_AZUREFUNC_CAMPAIGN_DETAILS_URI}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_MARKETING_URL:-http://localhost:5110/api/v1/campaigns/[0]/pic/}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_MARKETING_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_MARKETING_KEY}
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5110:80"

  webmvc:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
      - LocationsUrl=http://locations.api
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://marketing.api                                                    
      - CatalogUrlHC=http://catalog.api/hc
      - OrderingUrlHC=http://ordering.api/hc
      - IdentityUrlHC=http://identity.api/hc     
      - BasketUrlHC=http://basket.api/hc
      - MarketingUrlHC=http://marketing.api/hc
      - PaymentUrlHC=http://payment.api/hc
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sql.data:
    environment:
      - MSSQL_SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
      - MSSQL_PID=Developer
    ports:
      - "5433:1433"
  nosql.data:
    ports:
      - "27017:27017"
  basket.data:
    ports:
      - "6379:6379"      
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

<span data-ttu-id="7b264-205">在此範例中，開發覆寫組態會向主機公開一些連接埠、使用重新導向 URL 來定義環境變數，並指定用於開發環境的連接字串。</span><span class="sxs-lookup"><span data-stu-id="7b264-205">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="7b264-206">這些設定全部都只適用於開發環境。</span><span class="sxs-lookup"><span data-stu-id="7b264-206">These settings are all just for the development environment.</span></span>

<span data-ttu-id="7b264-207">當您執行 `docker-compose up` (或從 Visual Studio 啟動它) 時，此命令會自動讀取覆寫，就像它要合併兩個檔案一樣。</span><span class="sxs-lookup"><span data-stu-id="7b264-207">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="7b264-208">假設您想要將另一個 Compose 檔案用於生產環境，但具有不同的組態值、連接埠或連接字串。</span><span class="sxs-lookup"><span data-stu-id="7b264-208">Suppose that you want another Compose file for the production environment, with different configuration values, ports or connection strings.</span></span> <span data-ttu-id="7b264-209">您可以建立另一個覆寫檔案，例如名為 `docker-compose.prod.yml` 且具有不同設定和環境變數的檔案。</span><span class="sxs-lookup"><span data-stu-id="7b264-209">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span>  <span data-ttu-id="7b264-210">該檔案可能儲存在不同的 Git 存放庫中，或是由不同的小組進行管理和保護。</span><span class="sxs-lookup"><span data-stu-id="7b264-210">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="7b264-211">如何使用特定覆寫檔案進行部署</span><span class="sxs-lookup"><span data-stu-id="7b264-211">How to deploy with a specific override file</span></span>

<span data-ttu-id="7b264-212">若要使用多個覆寫檔案，或具有不同名稱的覆寫檔案，您可以搭配使用 -f 選項與 docker-compose 命令，並指定檔案。</span><span class="sxs-lookup"><span data-stu-id="7b264-212">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="7b264-213">Compose 會依在命令列上指定檔案的順序來合併檔案。</span><span class="sxs-lookup"><span data-stu-id="7b264-213">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="7b264-214">下列範例示範如何使用覆寫方法進行部署。</span><span class="sxs-lookup"><span data-stu-id="7b264-214">The following example shows how to deploy with override files.</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="7b264-215">在 docker-compose 檔案中使用環境變數</span><span class="sxs-lookup"><span data-stu-id="7b264-215">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="7b264-216">這十分方便 (尤其是在生產環境中)，可以從環境變數取得組態資訊，如先前範例所示。</span><span class="sxs-lookup"><span data-stu-id="7b264-216">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="7b264-217">您使用語法 \${MY\_VAR} 來參考 docker-compose 檔案中的環境變數。</span><span class="sxs-lookup"><span data-stu-id="7b264-217">You reference an environment variable in your docker-compose files using the syntax \${MY\_VAR}.</span></span> <span data-ttu-id="7b264-218">docker-compose.prod.yml 檔案中的下行示範如何參考環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="7b264-218">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="7b264-219">根據主機環境 (Linux、Windows、Cloud 叢集等等)，會使用不同的方式來建立並初始化環境變數。</span><span class="sxs-lookup"><span data-stu-id="7b264-219">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="7b264-220">不過，便利的方式是使用 .env 檔案。</span><span class="sxs-lookup"><span data-stu-id="7b264-220">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="7b264-221">docker-compose 檔案支援在 .env 檔案中宣告預設環境變數。</span><span class="sxs-lookup"><span data-stu-id="7b264-221">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="7b264-222">這些環境變數值是預設值。</span><span class="sxs-lookup"><span data-stu-id="7b264-222">These values for the environment variables are the default values.</span></span> <span data-ttu-id="7b264-223">但它們可能會覆寫為您在每個環境中所定義的值 (主機 OS 或您叢集中的環境變數)。</span><span class="sxs-lookup"><span data-stu-id="7b264-223">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="7b264-224">您將此 .env 檔案放在從中執行 docker-compose 命令的資料夾。</span><span class="sxs-lookup"><span data-stu-id="7b264-224">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="7b264-225">下列範例示範 .env 檔案 (例如 eShopOnContainers 應用程式的 [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) 檔案)。</span><span class="sxs-lookup"><span data-stu-id="7b264-225">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="7b264-226">Docker-compose 預期 .env 檔案中每行的格式都是 &lt;變數&gt;=&lt;值&gt;。</span><span class="sxs-lookup"><span data-stu-id="7b264-226">Docker-compose expects each line in an .env file to be in the format &lt;variable&gt;=&lt;value&gt;.</span></span>

<span data-ttu-id="7b264-227">請注意，在執行階段環境中所設定的值會一律會覆寫 .env 檔案內所定義的值。</span><span class="sxs-lookup"><span data-stu-id="7b264-227">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="7b264-228">使用類似的方式，透過命令列命令引數所傳遞的值也會覆寫 .env 檔案中所設定的預設值。</span><span class="sxs-lookup"><span data-stu-id="7b264-228">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="7b264-229">其他資源</span><span class="sxs-lookup"><span data-stu-id="7b264-229">Additional resources</span></span>

-   <span data-ttu-id="7b264-230">**撰寫 Docker 的概觀**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span><span class="sxs-lookup"><span data-stu-id="7b264-230">**Overview of Docker Compose**
[*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span></span>

-   <span data-ttu-id="7b264-231">**多個撰寫檔案**
    [*https://docs.docker.com/compose/extends/\#多撰寫檔案*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span><span class="sxs-lookup"><span data-stu-id="7b264-231">**Multiple Compose files**
[*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span></span>

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="7b264-232">建置最佳化 ASP.NET Core Docker 映像</span><span class="sxs-lookup"><span data-stu-id="7b264-232">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="7b264-233">如果您要在網際網路上探索來源上的 Docker 和 .NET Core，則會發現 Dockerfiles，以將您的來源複製至容器來示範建置 Docker 映像的簡單性。</span><span class="sxs-lookup"><span data-stu-id="7b264-233">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="7b264-234">這些範例建議透過使用簡單組態，您可以擁有具有與您應用程式一起封裝之環境的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="7b264-234">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="7b264-235">下列範例示範類似的簡單 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="7b264-235">The following example shows a simple Dockerfile in this vein.</span></span>

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="7b264-236">這類 Dockerfile 將會運作。</span><span class="sxs-lookup"><span data-stu-id="7b264-236">A Dockerfile like this will work.</span></span> <span data-ttu-id="7b264-237">不過，您可以持續最佳化映像，特別是生產映像。</span><span class="sxs-lookup"><span data-stu-id="7b264-237">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="7b264-238">在容器和微服務模型中，您將會不斷地啟動容器。</span><span class="sxs-lookup"><span data-stu-id="7b264-238">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="7b264-239">因為容器是可處置的，所以容器的一般使用方式不會重新啟動睡眠中容器。</span><span class="sxs-lookup"><span data-stu-id="7b264-239">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="7b264-240">協調器 (例如 Docker Swarm、Kubernetes、DCOS 或 Azure Service Fabric) 只會建立映像的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="7b264-240">Orchestrators (like Docker Swarm, Kubernetes, DCOS or Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="7b264-241">這表示您需要在建置應用程式時對其先行編譯來進行最佳化，讓具現化程序更為快速。</span><span class="sxs-lookup"><span data-stu-id="7b264-241">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="7b264-242">容器在啟動時，應該就已準備好執行。</span><span class="sxs-lookup"><span data-stu-id="7b264-242">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="7b264-243">您不應該在執行階段從 dotnet CLI 使用 dotnet restore 和 dotnet build 命令進行還原並編譯，如許多 .NET Core 和 Docker 部落格文章中所見。</span><span class="sxs-lookup"><span data-stu-id="7b264-243">You should not restore and compile at run time, using dotnet restore and dotnet build commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="7b264-244">.NET 小組已執行重要工作，讓 .NET Core 和 ASP.NET Core 成為容器最佳化架構。</span><span class="sxs-lookup"><span data-stu-id="7b264-244">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="7b264-245">.NET Core 不只是具有小型記憶體耗用量的輕量型架構；小組已將焦點放在啟動效能以及產生某些最佳化 Docker 映像 (例如 [Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/) 上提供的 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) 映像)，與一般 [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) 或 [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) 映像相較之下。</span><span class="sxs-lookup"><span data-stu-id="7b264-245">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on startup performance and produced some optimized Docker images, like the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image available at [Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), in comparison to the regular [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) or [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) images.</span></span> <span data-ttu-id="7b264-246">[microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) 映像會將 aspnetcore\_urls 自動設為連接埠 80，並且預先 ngend 快取組件；這兩個選項會導致更快速地啟動。</span><span class="sxs-lookup"><span data-stu-id="7b264-246">The [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image provides automatic setting of aspnetcore\_urls to port 80 and the pre-ngend cache of assemblies; both of these settings result in faster startup.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="7b264-247">其他資源</span><span class="sxs-lookup"><span data-stu-id="7b264-247">Additional resources</span></span>

-   <span data-ttu-id="7b264-248">**建置最佳化 ASP.NET Core 的 Docker 映像**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span><span class="sxs-lookup"><span data-stu-id="7b264-248">**Building Optimized Docker Images with ASP.NET Core**
[*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span></span>

### <a name="building-the-application-from-a-build-ci-container"></a><span data-ttu-id="7b264-249">從 build (CI) 容器建置應用程式</span><span class="sxs-lookup"><span data-stu-id="7b264-249">Building the application from a build (CI) container</span></span>

<span data-ttu-id="7b264-250">Docker 的另一個優點是您可以從預先設定的容器來建置應用程式，如圖 8-13 所示，因此您不需要建立組建電腦或 VM 來建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="7b264-250">Another benefit of Docker is that you can build your application from a preconfigured container, as shown in Figure 8-13, so you do not need to create a build machine or VM to build your application.</span></span> <span data-ttu-id="7b264-251">您可以在開發電腦上執行該組建容器，以使用或測試該組建容器。</span><span class="sxs-lookup"><span data-stu-id="7b264-251">You can use or test that build container by running it at your development machine.</span></span> <span data-ttu-id="7b264-252">但更有趣的是，您可以從 CI (持續整合) 管道使用相同的組建容器。</span><span class="sxs-lookup"><span data-stu-id="7b264-252">But what is even more interesting is that you can use the same build container from your CI (Continuous Integration) pipeline.</span></span>

![](./media/image14.png)

<span data-ttu-id="7b264-253">**圖 8-13**.</span><span class="sxs-lookup"><span data-stu-id="7b264-253">**Figure 8-13**.</span></span> <span data-ttu-id="7b264-254">編譯 .NET 二進位檔的 Docker build-container</span><span class="sxs-lookup"><span data-stu-id="7b264-254">Docker build-container compiling your .NET binaries</span></span> 

<span data-ttu-id="7b264-255">在此情況下，我們提供 [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) 映像，以用來編譯和建置 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="7b264-255">For this scenario, we provide the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image, which you can use to compile and build your ASP.NET Core apps.</span></span> <span data-ttu-id="7b264-256">輸出會放在根據可最佳化執行階段映像之 [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) 映像的映像中，如前所述。</span><span class="sxs-lookup"><span data-stu-id="7b264-256">The output is placed in an image based on the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image, which is an optimized runtime image, as previously noted.</span></span>

<span data-ttu-id="7b264-257">aspnetcore-build 映像包含編譯 ASP.NET Core 應用程式所需的所有項目，包含 .NET Core、ASP.NET SDK、npm、Bower、Gulp 等等。</span><span class="sxs-lookup"><span data-stu-id="7b264-257">The aspnetcore-build image contains everything you need in order to compile an ASP.NET Core application, including .NET Core, the ASP.NET SDK, npm, Bower, Gulp, etc.</span></span>

<span data-ttu-id="7b264-258">在建置階段，我們需要這些相依性。</span><span class="sxs-lookup"><span data-stu-id="7b264-258">We need these dependencies at build time.</span></span> <span data-ttu-id="7b264-259">但我們不想要在執行階段讓應用程式具有這些項目，因為它會讓映像不必要地變大。</span><span class="sxs-lookup"><span data-stu-id="7b264-259">But we do not want to carry these with the application at runtime, because it would make the image unnecessarily large.</span></span> <span data-ttu-id="7b264-260">在 eShopOnContainers 應用程式中，只要執行下列 docker-compose 命令，即可從容器中建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="7b264-260">In the eShopOnContainers application, you can build the application from a container by just running the following docker-compose command.</span></span>

```
  docker-compose -f docker-compose.ci.build.yml up
```

<span data-ttu-id="7b264-261">圖 8-14 顯示在命令列執行的這個命令。</span><span class="sxs-lookup"><span data-stu-id="7b264-261">Figure 8-14 shows this command running at the command line.</span></span>

![](./media/image15.png)

<span data-ttu-id="7b264-262">**圖 8-14**</span><span class="sxs-lookup"><span data-stu-id="7b264-262">**Figure 8-14.**</span></span> <span data-ttu-id="7b264-263">從容器中建置 .NET 應用程式</span><span class="sxs-lookup"><span data-stu-id="7b264-263">Building your .NET application from a container</span></span>

<span data-ttu-id="7b264-264">如您所見，正在執行的容器是 ci-build\_1 容器。</span><span class="sxs-lookup"><span data-stu-id="7b264-264">As you can see, the container that is running is the ci-build\_1 container.</span></span> <span data-ttu-id="7b264-265">這是根據 aspnetcore-build 映像，因此它可以在該容器內編譯和建置整個應用程式，而不是從您的電腦。</span><span class="sxs-lookup"><span data-stu-id="7b264-265">This is based on the aspnetcore-build image so that it can compile and build your whole application from within that container instead of from your PC.</span></span> <span data-ttu-id="7b264-266">這是它在 Linux 中建置和編譯 .NET Core 專案的實際原因，因為該容器將在預設 Docker Linux 主機上執行。</span><span class="sxs-lookup"><span data-stu-id="7b264-266">That is why in reality it is building and compiling the .NET Core projects in Linux—because that container is running on the default Docker Linux host.</span></span>

<span data-ttu-id="7b264-267">該映像的 [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) 檔案 (eShopOnContainers 的一部分) 包含下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="7b264-267">The [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) file for that image (part of eShopOnContainers) contains the following code.</span></span> <span data-ttu-id="7b264-268">您可以看到它使用 [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) 映像來啟動組建容器。</span><span class="sxs-lookup"><span data-stu-id="7b264-268">You can see that it starts a build container using the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image.</span></span>

```yml
version: '3'

services:

  ci-build:

    image: microsoft/aspnetcore-build:2.0

    volumes:
      - .:/src

    working_dir: /src

    command: /bin/bash -c "pushd ./src/Web/WebSPA && npm rebuild node-sass && popd && dotnet restore ./eShopOnContainers-ServicesAndWebApps.sln && dotnet publish ./eShopOnContainers-ServicesAndWebApps.sln -c Release -o ./obj/Docker/publish"

```

* <span data-ttu-id="7b264-269">從 **.NET Core 2.0** 開始，執行 `dotnet publish` 命令時，會自動執行 `dotnet restore` 命令。</span><span class="sxs-lookup"><span data-stu-id="7b264-269">Starting with **.NET Core 2.0**, `dotnet restore` command executes automatically when the `dotnet publish` command is executed.</span></span>

<span data-ttu-id="7b264-270">建置容器在啟動並執行之後，會對解決方案中的所有專案執行 .NET SDK dotnet restore 和 dotnet publish 命令，以編譯 .NET 位元。</span><span class="sxs-lookup"><span data-stu-id="7b264-270">Once the build container is up and running, it runs the .NET SDK dotnet restore and dotnet publish commands against all the projects in the solution in order to compile the .NET bits.</span></span> <span data-ttu-id="7b264-271">在此情況下，因為 eShopOnContainers 也有根據用戶端程式碼之 TypeScript 和 Angular 的 SPA，所以也需要檢查 JavaScript 與 npm 的相依性，但該動作與 .NET 位元無關。</span><span class="sxs-lookup"><span data-stu-id="7b264-271">In this case, because eShopOnContainers also has an SPA based on TypeScript and Angular for the client code, it also needs to check JavaScript dependencies with npm, but that action is not related to the .NET bits.</span></span>

<span data-ttu-id="7b264-272">dotnet publish 命令會在每個專案的資料夾內建置已編譯的輸出，並將其發行至 ../obj/Docker/publish 資料夾，如圖 8-15 所示。</span><span class="sxs-lookup"><span data-stu-id="7b264-272">The dotnet publish command builds and publishes the compiled output within each project’s folder to the ../obj/Docker/publish folder, as shown in Figure 8-15.</span></span>

![](./media/image16.png)

<span data-ttu-id="7b264-273">**圖 8-15**.</span><span class="sxs-lookup"><span data-stu-id="7b264-273">**Figure 8-15.**</span></span> <span data-ttu-id="7b264-274">dotnet publish 命令所產生的二進位檔</span><span class="sxs-lookup"><span data-stu-id="7b264-274">Binary files generated by the dotnet publish command</span></span>

#### <a name="creating-the-docker-images-from-the-cli"></a><span data-ttu-id="7b264-275">從 CLI 建立 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="7b264-275">Creating the Docker images from the CLI</span></span>

<span data-ttu-id="7b264-276">將應用程式輸出發行至相關資料夾 (在每個專案內) 之後，下一步是實際建置 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="7b264-276">Once the application output is published to the related folders (within each project), the next step is to actually build the Docker images.</span></span> <span data-ttu-id="7b264-277">若要這樣做，您可以使用 docker-compose build 和 docker-compose up 命令，如圖 8-16 所示。</span><span class="sxs-lookup"><span data-stu-id="7b264-277">To do this, you use the docker-compose build and docker-compose up commands, as shown in Figure 8-16.</span></span>

![](./media/image17.png)

<span data-ttu-id="7b264-278">**圖 8-16**</span><span class="sxs-lookup"><span data-stu-id="7b264-278">**Figure 8-16.**</span></span> <span data-ttu-id="7b264-279">建置 Docker 映像並執行容器</span><span class="sxs-lookup"><span data-stu-id="7b264-279">Building Docker images and running the containers</span></span>

<span data-ttu-id="7b264-280">在圖 8-17 中，您可以看到 docker-compose build 命令執行方式。</span><span class="sxs-lookup"><span data-stu-id="7b264-280">In Figure 8-17, you can see how the docker-compose build command runs.</span></span>

![](./media/image18.png)

<span data-ttu-id="7b264-281">**圖 8-17**.</span><span class="sxs-lookup"><span data-stu-id="7b264-281">**Figure 8-17**.</span></span> <span data-ttu-id="7b264-282">使用 docker-compose build 命令建置 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="7b264-282">Building the Docker images with the docker-compose build command</span></span>

<span data-ttu-id="7b264-283">docker-compose build 與 docker-compose up 命令之間的差異在於 docker-compose up 會同時建置並啟動映像。</span><span class="sxs-lookup"><span data-stu-id="7b264-283">The difference between the docker-compose build and docker-compose up commands is that docker-compose up both builds and starts the images.</span></span>

<span data-ttu-id="7b264-284">當您使用 Visual Studio 時，所有這些步驟都是在幕後執行。</span><span class="sxs-lookup"><span data-stu-id="7b264-284">When you use Visual Studio, all these steps are performed under the covers.</span></span> <span data-ttu-id="7b264-285">Visual Studio 會編譯 .NET 應用程式、建立 Docker 映像，並將容器部署至 Docker 主機。</span><span class="sxs-lookup"><span data-stu-id="7b264-285">Visual Studio compiles your .NET application, creates the Docker images, and deploys the containers into the Docker host.</span></span> <span data-ttu-id="7b264-286">Visual Studio 提供額外功能，例如，直接從 Visual Studio 偵錯在 Docker 中執行之容器的能力。</span><span class="sxs-lookup"><span data-stu-id="7b264-286">Visual Studio offers additional features, like the ability to debug your containers running in Docker, directly from Visual Studio.</span></span>

<span data-ttu-id="7b264-287">這裡的整體心得是您可以使用 CI/CD 管道建置應用程式的相同方式來建置應用程式：從容器，而不是從本機電腦。</span><span class="sxs-lookup"><span data-stu-id="7b264-287">The overall takeway here is that you are able to build your application the same way your CI/CD pipeline should build it—from a container instead of from a local machine.</span></span> <span data-ttu-id="7b264-288">建立映像之後，您只需要使用 docker-compose up 命令來執行 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="7b264-288">After having the images created, then you just need to run the Docker images using the docker-compose up command.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="7b264-289">其他資源</span><span class="sxs-lookup"><span data-stu-id="7b264-289">Additional resources</span></span>

-   <span data-ttu-id="7b264-290">**建立從容器的位元： Windows CLI 環境 (dotnet CLI，Docker CLI 和 VS Code) 中設定 eShopOnContainers 方案**
    [*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI，-Docker-CLI-和-VS-程式碼)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span><span class="sxs-lookup"><span data-stu-id="7b264-290">**Building bits from a container: Setting the eShopOnContainers solution up in a Windows CLI environment (dotnet CLI, Docker CLI and VS Code)**
[*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="7b264-291">[上一個] (data-driven-crud-microservice.md) [下一個] (database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="7b264-291">[Previous] (data-driven-crud-microservice.md) [Next] (database-server-container.md)</span></span>
