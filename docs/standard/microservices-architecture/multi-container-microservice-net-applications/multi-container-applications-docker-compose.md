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
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>定義您的 docker compose.yml 多容器應用程式 

本指南中， [docker compose.yml](https://docs.docker.com/compose/compose-file/)檔案 > 一節中導入[步驟 4。建置多容器 Docker 應用程式時，您的服務定義在 docker compose.yml](#step4_define_svcs_in_docker_compose_yml)。 不過，有一些使用值得深入瀏覽的 docker-compose 檔案的其他方法。

例如，您可以明確地描述您要部署多個容器應用程式在 docker compose.yml 檔案中的方式。 （選擇性） 您也可以描述要如何建立自訂的 Docker 映像。 （自訂的 Docker 映像也可以建立使用 Docker CLI。）

基本上，您會定義每個您想要部署的容器，再加上每個容器部署某些特性。 一旦您擁有多個容器部署描述檔案，您可以部署整個方案由協調以單一動作[docker 撰寫向上](https://docs.docker.com/compose/overview/)CLI 命令，或者您可以將它部署以透明的方式從 Visual Studio。 否則，您必須使用 Docker CLI 使用 docker run 命令，從命令列部署容器所-容器中的多個步驟。 因此，必須指定剛好只有一個映像 docker compose.yml 中所定義的每個服務，或建置。 其他索引鍵為選擇性，且類似於其 docker 執行命令列對應項目。

下列 YAML 程式碼是 eShopOnContainers 範例可能全域但單一 docker-compose.yml 檔案的定義。 這不是從 eShopOnContainers 實際 docker-compose 檔案。 相反地，它是簡化和合併版本在單一檔案中，這不是最佳的方式來使用 docker-撰寫的檔案，將會稍後所述。

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

在這個檔案的根目錄機碼是服務 」。 該機碼下，您定義您想要部署和執行中執行時的服務 docker 撰寫命令，或當您從 Visual Studio 部署使用此 docker compose.yml 檔案。 在此情況下，docker compose.yml 檔案會有多個服務定義，如下列清單所述。

-   webmvc 包括耗用從伺服器端 C microservices ASP.NET Core MVC 應用程式的容器\#

-   catalog.api 包括目錄 ASP.NET Core Web API 的微服務容器

-   ordering.api 包含排序 ASP.NET Core Web API 的微服務容器

-   sql.data for Linux，持有 microservices 資料庫執行 SQL Server 的容器

-   使用購物籃 ASP.NET Core Web API 的微服務 basket.api 容器

-   basket.data REDIS 快取服務中，使用購物籃資料庫執行為 REDIS 快取的容器

### <a name="a-simple-web-service-api-container"></a>簡單的 Web 服務 API 容器

將焦點放在單一容器上，catalog.api 容器的微服務有直接的定義：

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

此容器化的服務具有下列的基本設定：

-   它根據自訂 eshop/catalog.api 映像。 為了簡單起見，沒有任何組建： 金鑰檔中的設定。 這表示在映像必須已先前建置 （使用 docker 建置），或已從任何 Docker 登錄下載 （與 docker 的提取命令）。

-   它會定義名為 ConnectionString 的連接字串，可用於 Entity framework 存取 SQL Server 執行個體，其中包含的目錄資料模型的環境變數。 在此情況下，相同的 SQL Server 容器所保留的多個資料庫。 因此，您需要較少的記憶體在開發電腦中的 Docker。 不過，您也可以部署一個 SQL Server 容器，每個微服務資料庫。

-   SQL Server 名稱是 sql.data，正在執行 SQL Server 執行個體，適用於 Linux 的容器所使用的相同名稱。 這是很方便。能夠使用此名稱解析 （內部 Docker 主機） 將會解析網路位址，因此您不需要知道您要從其他容器存取容器的內部 IP。

因為連接字串環境變數所定義，您可以設定該變數，透過不同的機制，而在不同的時間。 例如，您可以在部署到生產環境中的最後一個主機，或從您的 CI/CD 管線 VSTS 或您慣用的 DevOps 系統中執行它時，設定不同的連接字串。

-   它會公開內部服務的存取權 catalog.api Docker 主機中的連接埠 80。 該主機目前是 Linux VM，因為它為基礎的 Docker 映像 for Linux，但您可以設定改為執行 Windows 映像上的容器。

-   它會將公開連接埠 80 上 Docker 主機電腦 (Linux VM) 的連接埠 5101 容器上的轉送。

-   它會連結到 sql.data 服務 （在容器中執行的 Linux 資料庫的 SQL Server 執行個體） 的 web 服務。 當您指定此相依性時，catalog.api 容器之前不會啟動 sql.data 容器已經啟動。這是很重要，因為 catalog.api 必須最多有 SQL Server 資料庫執行第一次。 不過，這種容器相依性不是在許多情況下，因為只能在容器層級檢查 Docker。 有時 （在此案例的 SQL Server) 服務可能仍然不是好時，因此建議您最好在用戶端 microservices 中實作重試邏輯以指數型輪詢。 這樣一來，如果相依性容器未準備好一段時間，應用程式仍會具有恢復功能。

-   它被設定為允許存取外部伺服器： 額外\_主機設定可讓您存取外部的伺服器或機器之外 Docker 主機 （亦即，這是開發 Docker 的 Linux VM 的預設值外裝載），例如本機 SQL在您開發電腦上的伺服器執行個體。

另外還有其他，我們將討論下列各節中的更多進階的 docker compose.yml 設定。

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>使用 docker-撰寫針對多個環境的檔案

Docker compose.yml 檔案會定義檔案，並可供多個基礎結構，以了解該格式。 最簡單的工具是 docker-組成命令，但其他工具 (例如，Docker Swarm) orchestrators 也了解該檔案。

因此，藉由 docker 組成您可以以下列主要案例為目標的命令。

#### <a name="development-environments"></a>開發環境

當您開發應用程式時，務必要能夠在隔離式的開發環境中執行的應用程式。 您可以使用 docker 撰寫建立該環境，或使用 Visual Studio 會使用 docker-撰寫實際上 CLI 命令。

Docker compose.yml 檔案可讓您設定及文件的所有應用程式的服務依存性 （其他服務、 快取、 資料庫、 佇列等等）。 使用 docker 組成 CLI 命令，您可以建立並啟動的每個相依的一個或多個容器，使用單一命令 （docker-撰寫組成）。

Docker compose.yml 檔案是由 Docker 引擎所解譯的組態檔，但也可當做多容器應用程式的編撰詳細方便的文件檔。

#### <a name="testing-environments"></a>在測試環境

任何連續部署 (CD) 或持續整合 (CI) 程序的重要部分是單元測試和整合測試。 這些自動化的測試需要隔離的環境，因此不受影響的使用者或應用程式的資料中的任何其他變更。

透過 Docker Compose 您可以建立和終結該隔離的環境非常輕鬆地中的幾個命令，從命令提示字元或指令碼，如下列命令：

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a>生產部署

您也可以使用部署至遠端 Docker 引擎的撰寫。 典型的案例是將部署到單一的 Docker 主機執行個體 (實際執行 VM 或伺服器使用佈建[Docker 機器](https://docs.docker.com/machine/overview/))。 但它也可以是整個[Docker Swarm](https://docs.docker.com/swarm/overview/)叢集化，因為叢集也是 docker compose.yml 檔案相容。

如果您使用任何其他 orchestrator （Azure Service Fabric、 Mesos DC/OS、 Kubernetes 等），您可能需要加入類似在 docker compose.yml，但在其他 orchestrator 所需的格式設定和中繼資料的組態設定。

在任何情況下，docker 撰寫雖然實際執行工作流程可能會隨著您使用 orchestrator 是開發、 測試及實際執行的工作流程，方便的工具和中繼資料格式。

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>使用多個 docker-撰寫來處理數個環境的檔案

當目標為不同的環境，您應該使用多個構成的檔案。 這可讓您建立多個組態變化視環境而定。

#### <a name="overriding-the-base-docker-compose-file"></a>覆寫基底 docker-compose 檔案

您可以使用單一的 docker compose.yml 檔案，如先前各節中所顯示的簡化範例所示。 不過，不建議對於大部分應用程式。

根據預設，撰寫讀取兩個檔案、 docker compose.yml 和選擇性的 docker compose.override.yml 檔案。 示在圖 8-11 中，當您使用 Visual Studio，並啟用 Docker 的支援，Visual Studio 也會建立這些檔案，以及用來偵錯某些其他檔案。

![](./media/image12.png)

**圖 8-11**。 docker 撰寫 Visual Studio 2017 中的檔案

您可以使用任何編輯器，例如 Visual Studio 程式碼或適，編輯 docker-compose 檔案，並執行應用程式與 docker 撰寫 up 命令。

依照慣例，docker compose.yml 檔案會包含基底組態及其他靜態的設定。 這表示不應該根據您的目標部署環境變更服務組態。

Docker compose.override.yml 檔案，如其名所示，包含覆寫基底組態，例如取決於部署環境的組態的組態設定。 您也可以有多個具有不同名稱的覆寫檔案。 覆寫檔案通常會包含所需的應用程式但特定環境或部署的其他資訊。

#### <a name="targeting-multiple-environments"></a>目標多個環境

典型的使用案例是當您定義多個撰寫檔案讓您可鎖定目標多個環境，例如生產環境中，暫存、 CI 或開發。 若要支援這些差異，您可以分割成多個檔案，您撰寫的組態所示圖 8-12。

![](./media/image13.png)

**圖 8-12**。 多個 docker 撰寫檔案覆寫基底的 docker compose.yml 檔案中的值

您可以使用的基底的 docker compose.yml 啟動。 此基底的檔案必須包含基底或靜態的組態設定不會變更視環境而定。 比方說，eShopOnContainers 與基底的檔案具有下列 docker compose.yml 檔案。

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

由於不同的目標部署環境，不應該變更基底的 docker compose.yml 檔案中的值。

如果您專注於 webmvc 服務定義，比方說，您就可以查看該資訊的方式無論何種環境，您可能會將目標設為大致相同。 您擁有下列資訊：

-   服務名稱： webmvc。

-   容器的自訂映像： 資格/webmvc。

-   若要建置自訂的 Docker 映像，指出要使用哪些 Dockerfile 指令。

-   相依於其他服務，所以此容器會等到其他相依性容器已經啟動。

您可以有額外的設定，但是重點是在基底的 docker compose.yml 檔案中，您只想要設定環境之間是共通的資訊。 然後在 docker compose.override.yml 或類似檔案生產或預備環境中，您應該將針對每個環境的設定。

通常，docker compose.override.yml 會使用您的開發環境，如下列範例從 eShopOnContainers:

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

在此範例中，開發覆寫組態公開 （expose） 至主機的某些連接埠，定義環境變數，以重新導向 Url，並指定連接字串以供開發環境。 這些設定只是在開發環境。

當您執行 docker 撰寫向上 （或從 Visual Studio 啟動它），此命令會讀取覆寫自動如同它已合併這兩個檔案。

假設您想用於實際執行環境，具有不同的組態值的另一個撰寫檔案。 您可以建立另一個覆寫檔案，如下所示。 （這個檔案可能會儲存在不同的 Git 儲存機制或受管理和保護不同的小組。）

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

#### <a name="how-to-deploy-with-a-specific-override-file"></a>如何部署與特定覆寫檔案

若要使用不同的名稱中使用多個覆寫檔案或覆寫檔案，您可以使用-f 選項與 docker 組成命令並指定的檔案。 撰寫命令列指定的順序中的合併檔案。 下列範例會示範如何使用覆寫檔案進行部署。

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>使用環境變數的 docker-撰寫檔案

很方便，尤其是在生產環境中，若要能夠從環境變數取得組態資訊，我們有在先前的範例所示。 您使用語法 docker-compose 檔案中參考的環境變數\${MY\_VAR}。 Docker compose.prod.yml 檔案下列行示範如何參考環境變數的值。

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

環境變數會建立並初始化在不同的方式，根據您的主機環境中 (Linux、 Windows、 雲端叢集等。)。 不過，便利的方式是使用.env 檔案。 Docker-compose 檔案支援宣告.env 檔案中的預設環境變數。 這些環境變數的值是預設值。 但您可能已經定義在每個環境 （主機作業系統或從您的叢集環境變數） 中的值覆寫。 您將此.env 檔案放在資料夾位置 docker 撰寫從執行命令。

下列範例顯示類似.env 檔案[.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) eShopOnContainers 應用程式檔案。

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Docker 撰寫預期.env 檔案格式中的每一行&lt;變數&gt;=&lt;值&gt;。

請注意，一律在執行階段環境中設定的值會覆寫.env 檔案內所定義的值。 類似的方式，透過命令列命令引數傳遞的值也會覆寫.env 檔案中設定的預設值。

#### <a name="additional-resources"></a>其他資源

-   **Docker 概觀撰寫**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   **多個撰寫檔案**
    [*https://docs.docker.com/compose/extends/\#多撰寫檔案*](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>建置最佳化的 ASP.NET Core Docker 映像

如果您瀏覽 Docker 和.NET 核心上的網際網路來源，您會發現示範簡化建立 Docker 映像，藉由將您的來源複製到容器的 Dockerfiles。 這些範例建議，藉由使用簡單的設定，您可以擁有的 Docker 映像會與您的應用程式一起封裝的環境。 下列範例會顯示簡易的 Dockerfile 中此動作。

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

像這樣的 Dockerfile 會運作。 不過，您可以大幅最佳化您的映像，特別是您實際執行的映像。

在容器和 microservices 模型中，您會不斷地啟動容器。 因為容器是可處置，使用容器的一般方式不會重新啟動的睡眠中的容器。 （例如 Docker Swarm、 Kubernetes、 DCOS 或 Azure Service Fabric） orchestrators 直接建立映像的新執行個體。 這就表示您需要讓具現化程序將會更快建置時，先行編譯應用程式最佳化。 啟動容器時，它應該準備好執行。 您不應該還原，並在執行階段編譯、 使用 dotnet 還原和 dotnet 建置 dotnet CLI 命令，許多有關.NET Core 及 Docker 的部落格文章中所示。

.NET 小組已執行重要的工作，讓.NET Core 與 ASP.NET Core 容器最佳化的架構。 不只是一個輕量型架構與較小的記憶體耗用量;.NET Core小組已將焦點放在 啟動效能和產生某些最佳化的 Docker 映像，例如[microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)映像可在[Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/)，相較於一般[microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/)或[microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile)映像。 [Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)映像提供自動設定的 aspnetcore\_url 以連接埠 80 和前 ngend 快取的組件; 這兩個選項會導致更快速啟動。

#### <a name="additional-resources"></a>其他資源

-   **建置最佳化與 ASP.NET Core Docker Images**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

### <a name="building-the-application-from-a-build-ci-container"></a>建置應用程式從組建 (CI) 容器

Docker 的另一個優點是您可以建置您的應用程式，從預先設定的容器，為顯示在圖 8-13，因此您不需要建立組建電腦或 VM 來建置應用程式。 您可以使用或執行您的開發電腦上，以測試該組建容器。 但更有趣的是，您可以使用相同的組建容器從 CI （連續整合） 管線。

![](./media/image14.png)

**圖 8-13**。 建立.NET 從容器的位元的元件

針對此案例中，我們提供[microsoft/aspnetcore 建置](https://hub.docker.com/r/microsoft/aspnetcore-build/)映像，您可以使用編譯和建置您的 ASP.NET 核心應用程式。 將輸出放在基礎映像[microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/)映像，執行階段最佳化映像，如先前所述。

Aspnetcore 建置映像包含所需的所有以編譯 ASP.NET Core 應用程式，包括.NET Core、 ASP.NET SDK、 npm Bower、 Gulp、 等等。

在建置階段，我們就會需要這些相依性。 但我們不想要執行這些應用程式在執行階段，因為它會使映像不必要地大。 在 eShopOnContainers 應用程式中，您可以建置應用程式從只執行容器下 docker-撰寫命令。

```
  docker-compose -f docker-compose.ci.build.yml up
```

圖 8-14 顯示在命令列執行此命令。

![](./media/image15.png)

**圖 8-14 版。** 建置您的.NET 應用程式，從容器

如您所見，正在執行的容器是 ci 組建\_1 的容器。 這根據 aspnetcore 建置映像，使它可以編譯和建置整個應用程式而不是該容器內，從您的電腦。 也就是為什麼實際上它會建置和編譯.NET Core 專案，在 Linux 中的，因為該容器預設 Docker 的 Linux 主機上執行。

[Docker compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml)該映像 （eShopOnContainers 的一部份） 包含下列程式碼檔案。 您可以看到它啟動組建的容器使用[microsoft/aspnetcore 建置](https://hub.docker.com/r/microsoft/aspnetcore-build/)映像。

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

* 從開始**.NET Core 2.0**，`dotnet restore`會自動執行命令時`dotnet publish`執行命令。

一旦組建容器已啟動並執行，這會執行.NET SDK dotnet 還原，而且 dotnet 發行方案中針對所有專案的命令，以編譯的.NET 位元。 在此情況下，因為 eShopOnContainers 也有 SPA TypeScript 和 Angular 根據用戶端程式碼，也必須檢查 npm 與 JavaScript 相依性，但動作不相關的.NET 位元。

Dotnet 發行命令組建和發行的每個專案的資料夾內的已編譯的輸出.../obj/Docker/publish 資料夾，如圖 8-15 所示。

![](./media/image16.png)

**圖 8-15。** Dotnet 所產生的二進位檔案發行命令

#### <a name="creating-the-docker-images-from-the-cli"></a>從 CLI 建立 Docker 映像

一旦應用程式輸出發行至相關的資料夾 （在每一個專案中） 時下, 一個步驟是實際建置 Docker images。 若要這樣做，您可以使用 docker-compose 組建並 docker-撰寫向上命令，如圖 8-16 中所示。

![](./media/image17.png)

**圖 8-16。** 建立 Docker 映像和執行容器

在圖 8-17，您可以看到 docker-compose 如何建置執行命令。

![](./media/image18.png)

**圖 8-17**。 使用 docker 建置 Docker images-撰寫建置命令

建置 docker-compose 之間的差異，並向上 docker 撰寫命令是 docker 撰寫組建和啟動映像。

當您使用 Visual Studio 時，在幕後執行所有這些步驟。 Visual Studio 編譯的.NET 應用程式、 建立 Docker 映像中，並將容器部署至 Docker 主機。 Visual Studio 會提供額外的功能，例如您在 Docker 執行直接從 Visual Studio 的容器的偵錯功能。

整體的 takeway 是，您可以建置您的應用程式相同的方式，應該建立該 CI/CD 管線 — 從容器而不是從本機電腦。 之後建立的映像，則您只需要執行的 Docker 映像使用 docker-撰寫 up 命令。

#### <a name="additional-resources"></a>其他資源

-   **建立從容器的位元： Windows CLI 環境 (dotnet CLI，Docker CLI 和 VS Code) 中設定 eShopOnContainers 方案**
    [*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))


>[!div class="step-by-step"]
[上一個](資料-驅動-crud-microservice.md) [下一步] (資料庫的伺服器-container.md)
