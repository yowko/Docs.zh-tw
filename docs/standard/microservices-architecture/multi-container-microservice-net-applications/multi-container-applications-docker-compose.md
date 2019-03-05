---
title: 使用 docker-compose.yml 定義多容器應用程式
description: 如何使用 docker-compose.yml 指定多容器應用程式的微服務組合。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 908837c470e97e66a6f6b06ef89e87fca80982f2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56973505"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="2bbdd-103">使用 docker-compose.yml 定義多容器應用程式</span><span class="sxs-lookup"><span data-stu-id="2bbdd-103">Defining your multi-container application with docker-compose.yml</span></span> 

<span data-ttu-id="2bbdd-104">在本指南中，[docker-compose.yml](https://docs.docker.com/compose/compose-file/) 檔案是在下列這節中介紹：[步驟 4.建置多容器 Docker 應用程式時，在 docker-compose.yml 中定義您的服務](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application)。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span></span> <span data-ttu-id="2bbdd-105">不過，有一些其他方法可以使用值得深入探索的 docker-compose 檔案。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="2bbdd-106">例如，您可以明確地描述要如何在 docker-compose.yml 檔案中部署多容器應用程式。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="2bbdd-107">您也可以選擇性地描述要如何建置自訂 Docker 映像 </span><span class="sxs-lookup"><span data-stu-id="2bbdd-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="2bbdd-108">(也可以使用 Docker CLI 來建置自訂 Docker 映像)。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="2bbdd-109">基本上，您會定義您想要部署的每個容器，以及每個容器部署的特定特性。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="2bbdd-110">具有多容器部署描述檔案之後，即可使用單一動作部署 [docker-compose up](https://docs.docker.com/compose/overview/) CLI 命令所協調的整個解決方案，或可從 Visual Studio 透明地進行部署。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="2bbdd-111">否則，您必須使用 Docker CLI，從命令列使用 `docker run` 命令，透過多個步驟逐一部署容器。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the `docker run` command from the command line.</span></span> <span data-ttu-id="2bbdd-112">因此，docker-compose.yml 中所定義的每個服務都只能指定一個映像或組建。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="2bbdd-113">其他金鑰是選擇性的，而且類似其 `docker run` 命令列對應項目。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-113">Other keys are optional, and are analogous to their `docker run` command-line counterparts.</span></span>

<span data-ttu-id="2bbdd-114">下列 YAML 程式碼是 eShopOnContainers 範例之可能全域但單一 docker-compose.yml 檔案的定義。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="2bbdd-115">這不是 eShopOnContainers 中的實際 docker-compose 檔案。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="2bbdd-116">相反地，它是單一檔案中的簡化和合併版本，但這不是使用 docker-compose 檔案的最佳方式，我們將會在稍後進行說明。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

```yml
version: '3.4'

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

<span data-ttu-id="2bbdd-117">此檔案中的根金鑰就是服務。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-117">The root key in this file is services.</span></span> <span data-ttu-id="2bbdd-118">在該金鑰下，您定義想要在執行 `docker-compose up` 命令或是使用此 docker-compose.yml 檔案從 Visual Studio 部署時所部署和執行的服務。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-118">Under that key you define the services you want to deploy and run when you execute the `docker-compose up` command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="2bbdd-119">在此情況下，docker-compose.yml 檔案已定義多個服務，如下表所述。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following table.</span></span>

| <span data-ttu-id="2bbdd-120">服務名稱</span><span class="sxs-lookup"><span data-stu-id="2bbdd-120">Service name</span></span> | <span data-ttu-id="2bbdd-121">說明</span><span class="sxs-lookup"><span data-stu-id="2bbdd-121">Description</span></span> |
|--------------|-------------|
| <span data-ttu-id="2bbdd-122">webmvc</span><span class="sxs-lookup"><span data-stu-id="2bbdd-122">webmvc</span></span>       | <span data-ttu-id="2bbdd-123">容器，包括使用伺服器端 C\# 之微服務的 ASP.NET Core MVC 應用程式</span><span class="sxs-lookup"><span data-stu-id="2bbdd-123">Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>|
| <span data-ttu-id="2bbdd-124">catalog.api</span><span class="sxs-lookup"><span data-stu-id="2bbdd-124">catalog.api</span></span>  | <span data-ttu-id="2bbdd-125">容器，包括 Catalog ASP.NET Core Web API 微服務</span><span class="sxs-lookup"><span data-stu-id="2bbdd-125">Container including the Catalog ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="2bbdd-126">ordering.api</span><span class="sxs-lookup"><span data-stu-id="2bbdd-126">ordering.api</span></span> | <span data-ttu-id="2bbdd-127">容器，包括 Ordering ASP.NET Core Web API 微服務</span><span class="sxs-lookup"><span data-stu-id="2bbdd-127">Container including the Ordering ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="2bbdd-128">sql.data</span><span class="sxs-lookup"><span data-stu-id="2bbdd-128">sql.data</span></span>     | <span data-ttu-id="2bbdd-129">執行 SQL Server for Linux 的容器，保留微服務資料庫</span><span class="sxs-lookup"><span data-stu-id="2bbdd-129">Container running SQL Server for Linux, holding the microservices databases</span></span> |
| <span data-ttu-id="2bbdd-130">basket.api</span><span class="sxs-lookup"><span data-stu-id="2bbdd-130">basket.api</span></span>   | <span data-ttu-id="2bbdd-131">容器，具有 Basket ASP.NET Core Web API 微服務</span><span class="sxs-lookup"><span data-stu-id="2bbdd-131">Container with the Basket ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="2bbdd-132">basket.data</span><span class="sxs-lookup"><span data-stu-id="2bbdd-132">basket.data</span></span>  | <span data-ttu-id="2bbdd-133">執行 REDIS 快取服務的容器，其將 basket 資料庫作為 REDIS 快取</span><span class="sxs-lookup"><span data-stu-id="2bbdd-133">Container running the REDIS cache service, with the basket database as a REDIS cache</span></span> |

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="2bbdd-134">簡單 Web 服務 API 容器</span><span class="sxs-lookup"><span data-stu-id="2bbdd-134">A simple Web Service API container</span></span>

<span data-ttu-id="2bbdd-135">catalog.api container-microservice 聚焦於單一容器，因此具有簡單易懂的定義：</span><span class="sxs-lookup"><span data-stu-id="2bbdd-135">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

```yml
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
```

<span data-ttu-id="2bbdd-136">此容器化服務具有下列基本組態：</span><span class="sxs-lookup"><span data-stu-id="2bbdd-136">This containerized service has the following basic configuration:</span></span>

-   <span data-ttu-id="2bbdd-137">它是根據自訂 eshop/catalog.api 映像。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-137">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="2bbdd-138">為求簡化，檔案中沒有 build: 金鑰設定。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-138">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="2bbdd-139">這表示必須先前已建置映像 (使用 docker build) 或已從任何 Docker 登錄下載映像 (使用 docker pull 命令)。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-139">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

-   <span data-ttu-id="2bbdd-140">它會使用 Entity Framework 用來存取包含目錄資料模型之 SQL Server 執行個體的連接字串，來定義名為 ConnectionString 的環境變數。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-140">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="2bbdd-141">在此情況下，相同的 SQL Server 容器會保留多個資料庫。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-141">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="2bbdd-142">因此，您需要 Docker 的開發電腦中有較少的記憶體。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-142">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="2bbdd-143">不過，您也可以為每個微服務資料庫部署一個 SQL Server 容器。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-143">However, you could also deploy one SQL Server container for each microservice database.</span></span>

-   <span data-ttu-id="2bbdd-144">SQL Server 名稱是 sql.data，而這個相同名稱用於執行適用於 Linux 之 SQL Server 執行個體的容器。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-144">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="2bbdd-145">這樣十分方便；可使用此名稱解析 (Docker 主機內部) 將會解析網路位址，因此您不需要知道從其他容器存取之容器的內部 IP。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-145">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="2bbdd-146">因為連接字串是透過環境變數所定義，所以您可以透過不同的機制並在不同的時間來設定該變數。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-146">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="2bbdd-147">例如，在最終主機中部署至生產環境時，您可以設定不同的連接字串，或是從 Azure DevOps Services 或偏好 DevOps 系統中的 CI/CD 管道進行。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-147">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in Azure DevOps Services or your preferred DevOps system.</span></span>

-   <span data-ttu-id="2bbdd-148">它會公開連接埠 80，以對 Docker 主機內的 catalog.api 服務進行內部存取。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-148">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="2bbdd-149">該主機目前是 Linux VM，因為它是根據適用於 Linux 的 Docker 映像，但您可以改為設定在 Windows 映像上執行容器。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-149">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

-   <span data-ttu-id="2bbdd-150">它會將容器上的公開連接埠 80 轉送至 Docker 主機 (Linux VM) 上的連接埠 5101。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-150">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

-   <span data-ttu-id="2bbdd-151">它會將 Web 服務連結至 sql.data 服務 (適用於容器中所執行 Linux 資料庫的 SQL Server 執行個體)。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-151">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="2bbdd-152">當您指定此相依性時，除非已啟動 sql.data 容器，否則不會啟動 catalog.api 容器；這十分重要，因為 catalog.api 需要先啟動並執行 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-152">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="2bbdd-153">不過，在許多情況下，這種容器相依性不足，因為 Docker 只會在容器層級進行檢查。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-153">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="2bbdd-154">服務 (在此情況下是 SQL Server) 有時可能仍然未準備就緒，因此建議您在用戶端微服務中實作含指數輪詢的重試邏輯。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-154">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="2bbdd-155">這樣一來，如果相依性容器短時間內無法準備好，則應用程式仍會具有恢復功能。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-155">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

-   <span data-ttu-id="2bbdd-156">它是設定為允許存取外部伺服器：extra\_hosts 設定可讓您存取外部伺服器或 Docker 主機外部的電腦 (亦即，本身為開發 Docker 本機的預設 Linux VM 外部)，例如開發電腦上的本機 SQL Server 執行個體。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-156">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="2bbdd-157">另外還有其他更進階的 docker-compose.yml 設定，我們將在下列各節進行討論。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-157">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="2bbdd-158">使用 docker-compose 檔案以多個環境為目標</span><span class="sxs-lookup"><span data-stu-id="2bbdd-158">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="2bbdd-159">docker-compose.yml 檔案是定義檔，而且可以供了解該格式的多個基礎結構使用。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-159">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="2bbdd-160">最簡單的工具是 docker-compose 命令。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-160">The most straightforward tool is the docker-compose command.</span></span>

<span data-ttu-id="2bbdd-161">因此，使用 docker-compose 命令，即可將目標設為下列主要案例。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-161">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="2bbdd-162">開發環境</span><span class="sxs-lookup"><span data-stu-id="2bbdd-162">Development environments</span></span>

<span data-ttu-id="2bbdd-163">當您開發應用程式時，務必要能夠在隔離開發環境中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-163">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="2bbdd-164">您可以使用 docker-compose CLI 命令來建立該環境，或使用在幕後使用 docker-compose 的 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-164">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="2bbdd-165">docker-compose.yml 檔案可讓您設定和記載所有應用程式的服務相依性 (其他服務、快取、資料庫、佇列等等)。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-165">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="2bbdd-166">使用 docker-compose CLI 命令，您可以使用單一命令 (docker-compose up) 來建立和啟動每個相依性的一或多個容器。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-166">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="2bbdd-167">docker-compose.yml 檔案不只是 Docker 引擎所解譯的組態檔，也是組合多容器應用程式的便利文件檔案。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-167">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="2bbdd-168">測試環境</span><span class="sxs-lookup"><span data-stu-id="2bbdd-168">Testing environments</span></span>

<span data-ttu-id="2bbdd-169">任何持續部署 (CD) 或持續整合 (CI) 程序的重要部分都是單元測試和整合測試。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-169">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="2bbdd-170">這些自動化測試需要隔離環境，因此它們不受使用者或應用程式資料中的任何其他變更所影響。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-170">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="2bbdd-171">使用 Docker Compose，您可以從命令提示字元或指令碼，使用幾個命令非常輕鬆地建立和終結該隔離環境，例如下列命令：</span><span class="sxs-lookup"><span data-stu-id="2bbdd-171">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a><span data-ttu-id="2bbdd-172">生產部署</span><span class="sxs-lookup"><span data-stu-id="2bbdd-172">Production deployments</span></span>

<span data-ttu-id="2bbdd-173">您也可以使用 Compose 部署至遠端 Docker 引擎。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-173">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="2bbdd-174">典型案例是部署至單一 Docker 主機執行個體 (例如，使用 [Docker 電腦](https://docs.docker.com/machine/overview/)所佈建的生產 VM 或伺服器)。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-174">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span>

<span data-ttu-id="2bbdd-175">如果您使用任何其他協調器 (Azure Service Fabric Kubernetes 等)，則可能需要新增 docker-compose.yml 中的設定和中繼資料組態設定，但為其他協調器所需的格式。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-175">If you are using any other orchestrator (Azure Service Fabric, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="2bbdd-176">在任何情況下，雖然生產工作流程可能會隨著您使用的協調器而不同，但是 docker-compose 是開發、測試和生產工作流程的便利工具和中繼資料格式。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-176">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="2bbdd-177">使用多個 docker-compose 檔案來處理數個環境</span><span class="sxs-lookup"><span data-stu-id="2bbdd-177">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="2bbdd-178">以不同環境為目標時，您應該使用多個 Compose 檔案。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-178">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="2bbdd-179">根據環境，這可讓您建立多個組態變化。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-179">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="2bbdd-180">覆寫基底 docker-compose 檔案</span><span class="sxs-lookup"><span data-stu-id="2bbdd-180">Overriding the base docker-compose file</span></span>

<span data-ttu-id="2bbdd-181">您可以使用單一 docker-compose.yml 檔案，如先前各節中所顯示的簡化範例所示。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-181">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="2bbdd-182">不過，不建議用於大部分應用程式。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-182">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="2bbdd-183">Compose 預設會讀取兩個檔案、docker-compose.yml 和選擇性 docker-compose.override.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-183">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="2bbdd-184">如圖 6-11 中所示，當您在使用 Visual Studio 並啟用 Docker 支援時，Visual Studio 也會另外建立 docker-compose.vs.debug.g.yml 檔案以供偵錯應用程式，您可以在主要解決方案資料夾中的資料夾 obj\\Docker\\查看此檔案。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-184">As shown in Figure 6-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.vs.debug.g.yml file for debugging the application, you can take a look at this file in folder obj\\Docker\\ in the main solution folder.</span></span>

![docker-compose 專案檔結構：.dockerignore > 用於忽略檔案；docker-compose.yml > 用於結合微服務；docker-compose.override.yml > 用於設定微服務環境。](./media/image12.png)

<span data-ttu-id="2bbdd-186">**圖 6-11**。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-186">**Figure 6-11**.</span></span> <span data-ttu-id="2bbdd-187">Visual Studio 2017 中的 docker-compose 檔案</span><span class="sxs-lookup"><span data-stu-id="2bbdd-187">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="2bbdd-188">您可以使用任何編輯器 (如 Visual Studio Code 或 Sublime) 來編輯 docker-compose 檔案，並使用 docker-compose-up 命令來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-188">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="2bbdd-189">依照慣例，docker compose.yml 檔案會包含基底組態和其他靜態設定。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-189">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="2bbdd-190">這表示根據您設為目標的部署環境，服務組態不應該變更。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-190">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="2bbdd-191">docker-compose.override.yml 檔案，如其名所示，包含可覆寫基底組態的組態設定，例如取決於部署環境的組態。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-191">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="2bbdd-192">您也可以有多個具有不同名稱的覆寫檔案。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-192">You can have multiple override files with different names also.</span></span> <span data-ttu-id="2bbdd-193">覆寫檔案通常會包含應用程式所需要但為環境或部署特有的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-193">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="2bbdd-194">以多個環境為目標</span><span class="sxs-lookup"><span data-stu-id="2bbdd-194">Targeting multiple environments</span></span>

<span data-ttu-id="2bbdd-195">典型使用案例是定義多個 Compose 檔案，讓您可以將目標設為多個環境，例如生產環境、暫存環境、CI 或開發。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-195">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="2bbdd-196">若要支援這些差異，您可以將 Compose 組態分割成多個檔案，如圖 6-12 所示。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-196">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 6-12.</span></span>

![您可以合併多個 docker-compose\*.fml 檔案來處理不同環境。](./media/image13.png)

<span data-ttu-id="2bbdd-198">**圖 6-12**。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-198">**Figure 6-12**.</span></span> <span data-ttu-id="2bbdd-199">覆寫基底 docker-compose.yml 檔案中值的多個 docker-compose 檔案</span><span class="sxs-lookup"><span data-stu-id="2bbdd-199">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="2bbdd-200">您可以開始使用基底 docker-compose.yml 檔案。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-200">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="2bbdd-201">此基底檔案必須包含不會根據環境而變更的基底或靜態組態設定。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-201">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="2bbdd-202">例如，eShopOnContainers 具有下列與基底檔案相同的 docker-compose.yml (簡化為具有較少服務) 檔案。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-202">For example, the eShopOnContainers has the following docker-compose.yml file (simplified with less services) as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket.api:
    image: eshop/basket.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile    
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile    
    depends_on:
      - sql.data
      - rabbitmq

  marketing.api:
    image: eshop/marketing.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile    
    depends_on:
      - sql.data
      - nosql.data
      - identity.api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile    
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

<span data-ttu-id="2bbdd-203">因為目標部署環境不同，所以基底 docker-compose.yml 檔案中的值不應該變更。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-203">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="2bbdd-204">例如，如果您專注於 webmvc 服務定義，就可以看到該資訊大致相同，不論您將哪種環境設為目標。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-204">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="2bbdd-205">您具有下列資訊：</span><span class="sxs-lookup"><span data-stu-id="2bbdd-205">You have the following information:</span></span>

-   <span data-ttu-id="2bbdd-206">服務名稱：webmvc。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-206">The service name: webmvc.</span></span>

-   <span data-ttu-id="2bbdd-207">容器的自訂映像：eshop/webmvc。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-207">The container’s custom image: eshop/webmvc.</span></span>

-   <span data-ttu-id="2bbdd-208">建置自訂 Docker 映像的命令，指出要使用的 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-208">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

-   <span data-ttu-id="2bbdd-209">與其他服務的相依性，因此，除非已啟動其他相依性容器，否則不會啟動此容器。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-209">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="2bbdd-210">您可以有額外組態，但重點是在基底 docker-compose.yml 檔案中，您只想要設定環境之間通用的資訊。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-210">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="2bbdd-211">然後在 docker-compose.override.yml 或是生產或預備環境的類似檔案中，您應該放置每個環境特有的組態。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-211">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="2bbdd-212">通常，docker-compose.override.yml 會用於您的開發環境，如 eShopOnContainers 中的下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="2bbdd-212">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

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
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5202/api/v1/catalog/items/[0]/pic/}   
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
      - PurchaseUrl=http://webshoppingapigw
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://webmarketingapigw
      - CatalogUrlHC=http://catalog.api/hc
      - OrderingUrlHC=http://ordering.api/hc
      - IdentityUrlHC=http://identity.api/hc
      - BasketUrlHC=http://basket.api/hc
      - MarketingUrlHC=http://marketing.api/hc
      - PaymentUrlHC=http://payment.api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
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

<span data-ttu-id="2bbdd-213">在此範例中，開發覆寫組態會向主機公開一些連接埠、使用重新導向 URL 來定義環境變數，並指定用於開發環境的連接字串。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-213">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="2bbdd-214">這些設定全部都只適用於開發環境。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-214">These settings are all just for the development environment.</span></span>

<span data-ttu-id="2bbdd-215">當您執行 `docker-compose up` (或從 Visual Studio 啟動它) 時，此命令會自動讀取覆寫，就像它要合併兩個檔案一樣。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-215">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="2bbdd-216">假設您想要將另一個 Compose 檔案用於生產環境，但具有不同的組態值、連接埠或連接字串。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-216">Suppose that you want another Compose file for the production environment, with different configuration values, ports or connection strings.</span></span> <span data-ttu-id="2bbdd-217">您可以建立另一個覆寫檔案，例如名為 `docker-compose.prod.yml` 且具有不同設定和環境變數的檔案。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-217">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span>  <span data-ttu-id="2bbdd-218">該檔案可能儲存在不同的 Git 存放庫中，或是由不同的小組進行管理和保護。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-218">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="2bbdd-219">如何使用特定覆寫檔案進行部署</span><span class="sxs-lookup"><span data-stu-id="2bbdd-219">How to deploy with a specific override file</span></span>

<span data-ttu-id="2bbdd-220">若要使用多個覆寫檔案，或具有不同名稱的覆寫檔案，您可以搭配使用 -f 選項與 docker-compose 命令，並指定檔案。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-220">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="2bbdd-221">Compose 會依在命令列上指定檔案的順序來合併檔案。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-221">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="2bbdd-222">下列範例示範如何使用覆寫方法進行部署。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-222">The following example shows how to deploy with override files.</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="2bbdd-223">在 docker-compose 檔案中使用環境變數</span><span class="sxs-lookup"><span data-stu-id="2bbdd-223">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="2bbdd-224">這十分方便 (尤其是在生產環境中)，可以從環境變數取得組態資訊，如先前範例所示。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-224">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="2bbdd-225">您可以使用語法 ${MY\_VAR} 來參考 docker-compose 檔案中的環境變數。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-225">You can reference an environment variable in your docker-compose files using the syntax ${MY\_VAR}.</span></span> <span data-ttu-id="2bbdd-226">docker-compose.prod.yml 檔案中的下行示範如何參考環境變數的值。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-226">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="2bbdd-227">根據主機環境 (Linux、Windows、Cloud 叢集等等)，會使用不同的方式來建立並初始化環境變數。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-227">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="2bbdd-228">不過，便利的方式是使用 .env 檔案。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-228">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="2bbdd-229">docker-compose 檔案支援在 .env 檔案中宣告預設環境變數。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-229">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="2bbdd-230">這些環境變數值是預設值。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-230">These values for the environment variables are the default values.</span></span> <span data-ttu-id="2bbdd-231">但它們可能會覆寫為您在每個環境中所定義的值 (主機 OS 或您叢集中的環境變數)。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-231">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="2bbdd-232">您將此 .env 檔案放在從中執行 docker-compose 命令的資料夾。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-232">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="2bbdd-233">下列範例示範 .env 檔案 (例如 eShopOnContainers 應用程式的 [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) 檔案)。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-233">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="2bbdd-234">Docker-compose 預期 .env 檔案中每行的格式都是 \<變數\>=\<值\>。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-234">Docker-compose expects each line in an .env file to be in the format \<variable\>=\<value\>.</span></span>

<span data-ttu-id="2bbdd-235">請注意，在執行階段環境中所設定的值會一律會覆寫 .env 檔案內所定義的值。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-235">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="2bbdd-236">使用類似的方式，透過命令列命令引數所傳遞的值也會覆寫 .env 檔案中所設定的預設值。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-236">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="2bbdd-237">其他資源</span><span class="sxs-lookup"><span data-stu-id="2bbdd-237">Additional resources</span></span>

-   <span data-ttu-id="2bbdd-238">**Docker Compose 的概觀**</span><span class="sxs-lookup"><span data-stu-id="2bbdd-238">**Overview of Docker Compose**</span></span> <br/>
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   <span data-ttu-id="2bbdd-239">**多個 Compose 檔案**</span><span class="sxs-lookup"><span data-stu-id="2bbdd-239">**Multiple Compose files**</span></span> <br/>
    [*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="2bbdd-240">建置最佳化 ASP.NET Core Docker 映像</span><span class="sxs-lookup"><span data-stu-id="2bbdd-240">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="2bbdd-241">如果您要在網際網路上探索來源上的 Docker 和 .NET Core，則會發現 Dockerfiles，以將您的來源複製至容器來示範建置 Docker 映像的簡單性。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-241">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="2bbdd-242">這些範例建議透過使用簡單組態，您可以擁有具有與您應用程式一起封裝之環境的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-242">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="2bbdd-243">下列範例示範類似的簡單 Dockerfile。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-243">The following example shows a simple Dockerfile in this vein.</span></span>

```
FROM microsoft/dotnet
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="2bbdd-244">這類 Dockerfile 將會運作。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-244">A Dockerfile like this will work.</span></span> <span data-ttu-id="2bbdd-245">不過，您可以持續最佳化映像，特別是生產映像。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-245">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="2bbdd-246">在容器和微服務模型中，您將會不斷地啟動容器。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-246">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="2bbdd-247">因為容器是可處置的，所以容器的一般使用方式不會重新啟動睡眠中容器。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-247">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="2bbdd-248">協調器 (例如 Kubernetes 和 Azure Service Fabric) 只會建立映像的新執行個體。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-248">Orchestrators (like Kubernetes and Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="2bbdd-249">這表示您需要在建置應用程式時對其先行編譯來進行最佳化，讓具現化程序更為快速。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-249">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="2bbdd-250">容器在啟動時，應該就已準備好執行。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-250">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="2bbdd-251">您不應該在執行階段從 dotnet CLI 使用 `dotnet restore` 和 `dotnet build` 命令進行還原和編譯，如許多 .NET Core 和 Docker 部落格文章中所見。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-251">You should not restore and compile at run time, using `dotnet restore` and `dotnet build` commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="2bbdd-252">.NET 小組已執行重要工作，讓 .NET Core 和 ASP.NET Core 成為容器最佳化架構。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-252">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="2bbdd-253">.NET Core 不僅已是磁碟使用量低的輕量型架構，從 2.1 版起，小組還將重點放在針對三大情境將 Docker 映像最佳化，以便於 <span class="underline">microsoft/dotnet</span>的 Docker Hub 登錄中加以發佈：</span><span class="sxs-lookup"><span data-stu-id="2bbdd-253">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on optimized Docker images for three main scenarios and published them in the Docker Hub registry at <span class="underline">microsoft/dotnet</span>, beginning with version 2.1:</span></span>

1.  <span data-ttu-id="2bbdd-254">**開發**：最優先事項是能夠快速進行整合，及對變更進行偵錯，而大小則次之。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-254">**Development**: Where the priority is the ability to quickly interate and debug changes and size is secondary.</span></span>

2.  <span data-ttu-id="2bbdd-255">**組建**：最優先事項是編譯應用程式，以及包含二進位檔和其他相依性來將二進位檔最佳化。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-255">**Build**: The priority is compiling the application and includes binaries and other dependencies to optimize binaries.</span></span>

3.  <span data-ttu-id="2bbdd-256">**生產**：因為重點在於快速地部署和啟動容器，所以這些映像只限於二進位檔及執行應用程式所需的內容。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-256">**Production**: Where the focus is fast deploying and starting of containers, so these images are limited to the binaries and the content nedded to run the application.</span></span>

<span data-ttu-id="2bbdd-257">為達到這項目標，.NET 小組目前在 [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) (Docker Hub) 提供三種基本變體：</span><span class="sxs-lookup"><span data-stu-id="2bbdd-257">To achieve this, the .NET team is providing three basic variants in [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) (at Docker Hub):</span></span>

1.  <span data-ttu-id="2bbdd-258">**sdk**：適用於開發與建置環節。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-258">**sdk**: for the development and build scenarios.</span></span>
2.  <span data-ttu-id="2bbdd-259">**runtime**：適用於生產環節和</span><span class="sxs-lookup"><span data-stu-id="2bbdd-259">**runtime**: for the production scenario and</span></span>
3.  <span data-ttu-id="2bbdd-260">**runtime-deps**：適用於[獨立式應用程式](../../../core/deploying/index.md#self-contained-deployments-scd)的生產環節。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-260">**runtime-deps**: for the production scenario of [self-contained applications](../../../core/deploying/index.md#self-contained-deployments-scd).</span></span>

<span data-ttu-id="2bbdd-261">執行階段映像也會將 aspnetcore\_urls 自動設為連接埠 80，並且預先 ngend 快取組件讓啟動更快速。</span><span class="sxs-lookup"><span data-stu-id="2bbdd-261">Runtime images also provides automatic setting of aspnetcore\_urls to port 80 and the pre-ngend cache of assemblies; to help in getting faster startup.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="2bbdd-262">其他資源</span><span class="sxs-lookup"><span data-stu-id="2bbdd-262">Additional resources</span></span>

-   <span data-ttu-id="2bbdd-263">**Building Optimized Docker Images with ASP.NET Core** (使用 ASP.NET Core 建置最佳化 Docker 映像)</span><span class="sxs-lookup"><span data-stu-id="2bbdd-263">**Building Optimized Docker Images with ASP.NET Core**</span></span> <br/>
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

-   <span data-ttu-id="2bbdd-264">**建置 .NET Core 應用程式的 Docker 映像**</span><span class="sxs-lookup"><span data-stu-id="2bbdd-264">**Building Docker Images for .NET Core Applications**</span></span> <br/>
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)

>[!div class="step-by-step"]
><span data-ttu-id="2bbdd-265">[上一頁](data-driven-crud-microservice.md)
>[下一頁](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="2bbdd-265">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
