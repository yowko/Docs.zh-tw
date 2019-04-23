---
title: 使用 docker-compose.yml 定義多容器應用程式
description: 如何使用 docker-compose.yml 指定多容器應用程式的微服務組合。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: f40559ef7c41febb5e17d583ef2d0eb64addc0a8
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613183"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a>使用 docker-compose.yml 定義多容器應用程式

在本指南中，[docker-compose.yml](https://docs.docker.com/compose/compose-file/) 檔案是在下列這節中介紹：[步驟 4.建置多容器 Docker 應用程式時，在 docker-compose.yml 中定義您的服務](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application)。 不過，有一些其他方法可以使用值得深入探索的 docker-compose 檔案。

例如，您可以明確地描述要如何在 docker-compose.yml 檔案中部署多容器應用程式。 您也可以選擇性地描述要如何建置自訂 Docker 映像  (也可以使用 Docker CLI 來建置自訂 Docker 映像)。

基本上，您會定義您想要部署的每個容器，以及每個容器部署的特定特性。 具有多容器部署描述檔案之後，即可使用單一動作部署 [docker-compose up](https://docs.docker.com/compose/overview/) CLI 命令所協調的整個解決方案，或可從 Visual Studio 透明地進行部署。 否則，您必須使用 Docker CLI，從命令列使用 `docker run` 命令，透過多個步驟逐一部署容器。 因此，docker-compose.yml 中所定義的每個服務都只能指定一個映像或組建。 其他金鑰是選擇性的，而且類似其 `docker run` 命令列對應項目。

下列 YAML 程式碼是 eShopOnContainers 範例之可能全域但單一 docker-compose.yml 檔案的定義。 這不是 eShopOnContainers 中的實際 docker-compose 檔案。 相反地，它是單一檔案中的簡化和合併版本，但這不是使用 docker-compose 檔案的最佳方式，我們將會在稍後進行說明。

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

此檔案中的根金鑰就是服務。 在該金鑰下，您定義想要在執行 `docker-compose up` 命令或是使用此 docker-compose.yml 檔案從 Visual Studio 部署時所部署和執行的服務。 在此情況下，docker-compose.yml 檔案已定義多個服務，如下表所述。

| 服務名稱 | 說明 |
|--------------|-------------|
| webmvc       | 容器，包括使用伺服器端 C\# 之微服務的 ASP.NET Core MVC 應用程式|
| catalog.api  | 容器，包括 Catalog ASP.NET Core Web API 微服務 |
| ordering.api | 容器，包括 Ordering ASP.NET Core Web API 微服務 |
| sql.data     | 執行 SQL Server for Linux 的容器，保留微服務資料庫 |
| basket.api   | 容器，具有 Basket ASP.NET Core Web API 微服務 |
| basket.data  | 執行 REDIS 快取服務的容器，其將 basket 資料庫作為 REDIS 快取 |

### <a name="a-simple-web-service-api-container"></a>簡單 Web 服務 API 容器

catalog.api container-microservice 聚焦於單一容器，因此具有簡單易懂的定義：

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

此容器化服務具有下列基本組態：

- 它是根據自訂 eshop/catalog.api 映像。 為求簡化，檔案中沒有 build: 金鑰設定。 這表示必須先前已建置映像 (使用 docker build) 或已從任何 Docker 登錄下載映像 (使用 docker pull 命令)。

- 它會使用 Entity Framework 用來存取包含目錄資料模型之 SQL Server 執行個體的連接字串，來定義名為 ConnectionString 的環境變數。 在此情況下，相同的 SQL Server 容器會保留多個資料庫。 因此，您需要 Docker 的開發電腦中有較少的記憶體。 不過，您也可以為每個微服務資料庫部署一個 SQL Server 容器。

- SQL Server 名稱是 sql.data，而這個相同名稱用於執行適用於 Linux 之 SQL Server 執行個體的容器。 這樣十分方便；可使用此名稱解析 (Docker 主機內部) 將會解析網路位址，因此您不需要知道從其他容器存取之容器的內部 IP。

因為連接字串是透過環境變數所定義，所以您可以透過不同的機制並在不同的時間來設定該變數。 例如，在最終主機中部署至生產環境時，您可以設定不同的連接字串，或是從 Azure DevOps Services 或偏好 DevOps 系統中的 CI/CD 管道進行。

- 它會公開連接埠 80，以對 Docker 主機內的 catalog.api 服務進行內部存取。 該主機目前是 Linux VM，因為它是根據適用於 Linux 的 Docker 映像，但您可以改為設定在 Windows 映像上執行容器。

- 它會將容器上的公開連接埠 80 轉送至 Docker 主機 (Linux VM) 上的連接埠 5101。

- 它會將 Web 服務連結至 sql.data 服務 (適用於容器中所執行 Linux 資料庫的 SQL Server 執行個體)。 當您指定此相依性時，除非已啟動 sql.data 容器，否則不會啟動 catalog.api 容器；這十分重要，因為 catalog.api 需要先啟動並執行 SQL Server 資料庫。 不過，在許多情況下，這種容器相依性不足，因為 Docker 只會在容器層級進行檢查。 服務 (在此情況下是 SQL Server) 有時可能仍然未準備就緒，因此建議您在用戶端微服務中實作含指數輪詢的重試邏輯。 這樣一來，如果相依性容器短時間內無法準備好，則應用程式仍會具有恢復功能。

- 它是設定為允許存取外部伺服器：extra\_hosts 設定可讓您存取外部伺服器或 Docker 主機外部的電腦 (亦即，本身為開發 Docker 本機的預設 Linux VM 外部)，例如開發電腦上的本機 SQL Server 執行個體。

另外還有其他更進階的 docker-compose.yml 設定，我們將在下列各節進行討論。

### <a name="using-docker-compose-files-to-target-multiple-environments"></a>使用 docker-compose 檔案以多個環境為目標

docker-compose.yml 檔案是定義檔，而且可以供了解該格式的多個基礎結構使用。 最簡單的工具是 docker-compose 命令。

因此，使用 docker-compose 命令，即可將目標設為下列主要案例。

#### <a name="development-environments"></a>開發環境

當您開發應用程式時，務必要能夠在隔離開發環境中執行應用程式。 您可以使用 docker-compose CLI 命令來建立該環境，或使用在幕後使用 docker-compose 的 Visual Studio。

docker-compose.yml 檔案可讓您設定和記載所有應用程式的服務相依性 (其他服務、快取、資料庫、佇列等等)。 使用 docker-compose CLI 命令，您可以使用單一命令 (docker-compose up) 來建立和啟動每個相依性的一或多個容器。

docker-compose.yml 檔案不只是 Docker 引擎所解譯的組態檔，也是組合多容器應用程式的便利文件檔案。

#### <a name="testing-environments"></a>測試環境

任何持續部署 (CD) 或持續整合 (CI) 程序的重要部分都是單元測試和整合測試。 這些自動化測試需要隔離環境，因此它們不受使用者或應用程式資料中的任何其他變更所影響。

使用 Docker Compose，您可以從命令提示字元或指令碼，使用幾個命令非常輕鬆地建立和終結該隔離環境，例如下列命令：

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a>生產部署

您也可以使用 Compose 部署至遠端 Docker 引擎。 典型案例是部署至單一 Docker 主機執行個體 (例如，使用 [Docker 電腦](https://docs.docker.com/machine/overview/)所佈建的生產 VM 或伺服器)。

如果您使用任何其他協調器 (Azure Service Fabric Kubernetes 等)，則可能需要新增 docker-compose.yml 中的設定和中繼資料組態設定，但為其他協調器所需的格式。

在任何情況下，雖然生產工作流程可能會隨著您使用的協調器而不同，但是 docker-compose 是開發、測試和生產工作流程的便利工具和中繼資料格式。

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a>使用多個 docker-compose 檔案來處理數個環境

以不同環境為目標時，您應該使用多個 Compose 檔案。 根據環境，這可讓您建立多個組態變化。

#### <a name="overriding-the-base-docker-compose-file"></a>覆寫基底 docker-compose 檔案

您可以使用單一 docker-compose.yml 檔案，如先前各節中所顯示的簡化範例所示。 不過，不建議用於大部分應用程式。

Compose 預設會讀取兩個檔案、docker-compose.yml 和選擇性 docker-compose.override.yml 檔案。 如圖 6-11 中所示，當您在使用 Visual Studio 並啟用 Docker 支援時，Visual Studio 也會另外建立 docker-compose.vs.debug.g.yml 檔案以供偵錯應用程式，您可以在主要解決方案資料夾中的資料夾 obj\\Docker\\查看此檔案。

![docker-compose 專案檔結構：.dockerignore > 用於忽略檔案；docker-compose.yml > 用於結合微服務；docker-compose.override.yml > 用於設定微服務環境。](./media/image12.png)

**圖 6-11**。 Visual Studio 2017 中的 docker-compose 檔案

您可以使用任何編輯器 (如 Visual Studio Code 或 Sublime) 來編輯 docker-compose 檔案，並使用 docker-compose-up 命令來執行應用程式。

依照慣例，docker compose.yml 檔案會包含基底組態和其他靜態設定。 這表示根據您設為目標的部署環境，服務組態不應該變更。

docker-compose.override.yml 檔案，如其名所示，包含可覆寫基底組態的組態設定，例如取決於部署環境的組態。 您也可以有多個具有不同名稱的覆寫檔案。 覆寫檔案通常會包含應用程式所需要但為環境或部署特有的其他資訊。

#### <a name="targeting-multiple-environments"></a>以多個環境為目標

典型使用案例是定義多個 Compose 檔案，讓您可以將目標設為多個環境，例如生產環境、暫存環境、CI 或開發。 若要支援這些差異，您可以將 Compose 組態分割成多個檔案，如圖 6-12 所示。

![您可以合併多個 docker-compose*.fml 檔案來處理不同環境。](./media/image13.png)

**圖 6-12**。 覆寫基底 docker-compose.yml 檔案中值的多個 docker-compose 檔案

您可以開始使用基底 docker-compose.yml 檔案。 此基底檔案必須包含不會根據環境而變更的基底或靜態組態設定。 例如，eShopOnContainers 具有下列與基底檔案相同的 docker-compose.yml (簡化為具有較少服務) 檔案。

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

因為目標部署環境不同，所以基底 docker-compose.yml 檔案中的值不應該變更。

例如，如果您專注於 webmvc 服務定義，就可以看到該資訊大致相同，不論您將哪種環境設為目標。 您具有下列資訊：

- 服務名稱：webmvc。

- 容器的自訂映像：eshop/webmvc。

- 建置自訂 Docker 映像的命令，指出要使用的 Dockerfile。

- 與其他服務的相依性，因此，除非已啟動其他相依性容器，否則不會啟動此容器。

您可以有額外組態，但重點是在基底 docker-compose.yml 檔案中，您只想要設定環境之間通用的資訊。 然後在 docker-compose.override.yml 或是生產或預備環境的類似檔案中，您應該放置每個環境特有的組態。

通常，docker-compose.override.yml 會用於您的開發環境，如 eShopOnContainers 中的下列範例所示：

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

在此範例中，開發覆寫組態會向主機公開一些連接埠、使用重新導向 URL 來定義環境變數，並指定用於開發環境的連接字串。 這些設定全部都只適用於開發環境。

當您執行 `docker-compose up` (或從 Visual Studio 啟動它) 時，此命令會自動讀取覆寫，就像它要合併兩個檔案一樣。

假設您想要將另一個 Compose 檔案用於生產環境，但具有不同的組態值、連接埠或連接字串。 您可以建立另一個覆寫檔案，例如名為 `docker-compose.prod.yml` 且具有不同設定和環境變數的檔案。 該檔案可能儲存在不同的 Git 存放庫中，或是由不同的小組進行管理和保護。

#### <a name="how-to-deploy-with-a-specific-override-file"></a>如何使用特定覆寫檔案進行部署

若要使用多個覆寫檔案，或具有不同名稱的覆寫檔案，您可以搭配使用 -f 選項與 docker-compose 命令，並指定檔案。 Compose 會依在命令列上指定檔案的順序來合併檔案。 下列範例示範如何使用覆寫方法進行部署。

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a>在 docker-compose 檔案中使用環境變數

這十分方便 (尤其是在生產環境中)，可以從環境變數取得組態資訊，如先前範例所示。 您可以使用語法 ${MY\_VAR} 來參考 docker-compose 檔案中的環境變數。 docker-compose.prod.yml 檔案中的下行示範如何參考環境變數的值。

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

根據主機環境 (Linux、Windows、Cloud 叢集等等)，會使用不同的方式來建立並初始化環境變數。 不過，便利的方式是使用 .env 檔案。 docker-compose 檔案支援在 .env 檔案中宣告預設環境變數。 這些環境變數值是預設值。 但它們可能會覆寫為您在每個環境中所定義的值 (主機 OS 或您叢集中的環境變數)。 您將此 .env 檔案放在從中執行 docker-compose 命令的資料夾。

下列範例示範 .env 檔案 (例如 eShopOnContainers 應用程式的 [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) 檔案)。

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

Docker-compose 預期 .env 檔案中每行的格式都是 \<變數\>=\<值\>。

請注意，在執行階段環境中所設定的值會一律會覆寫 .env 檔案內所定義的值。 使用類似的方式，透過命令列命令引數所傳遞的值也會覆寫 .env 檔案中所設定的預設值。

#### <a name="additional-resources"></a>其他資源

- **Docker Compose 的概觀** \
    <https://docs.docker.com/compose/overview/>

- **多個 Compose 檔案** \
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a>建置最佳化 ASP.NET Core Docker 映像

如果您要在網際網路上探索來源上的 Docker 和 .NET Core，則會發現 Dockerfiles，以將您的來源複製至容器來示範建置 Docker 映像的簡單性。 這些範例建議透過使用簡單組態，您可以擁有具有與您應用程式一起封裝之環境的 Docker 映像。 下列範例示範類似的簡單 Dockerfile。

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:2.2
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

這類 Dockerfile 將會運作。 不過，您可以持續最佳化映像，特別是生產映像。

在容器和微服務模型中，您將會不斷地啟動容器。 因為容器是可處置的，所以容器的一般使用方式不會重新啟動睡眠中容器。 協調器 (例如 Kubernetes 和 Azure Service Fabric) 只會建立映像的新執行個體。 這表示您需要在建置應用程式時對其先行編譯來進行最佳化，讓具現化程序更為快速。 容器在啟動時，應該就已準備好執行。 您不應該在執行階段從 dotnet CLI 使用 `dotnet restore` 和 `dotnet build` 命令進行還原和編譯，如許多 .NET Core 和 Docker 部落格文章中所見。

.NET 小組已執行重要工作，讓 .NET Core 和 ASP.NET Core 成為容器最佳化架構。 .NET Core 不僅已是磁碟使用量低的輕量型架構，從 2.1 版起，小組還將重點放在針對三大情境將 Docker 映像最佳化，以便於 *dotnet/core*的 Docker Hub 登錄中加以發佈：

1. **開發**：最優先事項是能夠快速進行整合，及對變更進行偵錯，而大小則次之。

2. **組建**：最優先事項是編譯應用程式，以及包含二進位檔和其他相依性來將二進位檔最佳化。

3. **生產**：因為重點在於快速地部署和啟動容器，所以這些映像只限於二進位檔及執行應用程式所需的內容。

為達到這項目標，.NET 小組目前在 [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (Docker Hub) 提供 四種基本變體：

1. **sdk**：適用於開發與建置環節
1. **aspnet**：ASP.NET 生產環境案例
1. **aspnet**：.NET 生產環境案例
1. **runtime-deps**：適用於[獨立式應用程式](../../../core/deploying/index.md#self-contained-deployments-scd)的生產環節。

為了啟動更快，執行階段映像也會將 spnetcore\_urls 自動設定為連接埠 80，並使用 Ngen 建立組件的原生映像快取。

#### <a name="additional-resources"></a>其他資源

- **使用 ASP.NET Core 建置最佳化 Docker 映像** \
    <https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/>

- **建置 .NET Core 應用程式的 Docker 映像** \
    [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](../../../core/docker/building-net-docker-images.md)

> [!div class="step-by-step"]
> [上一頁](data-driven-crud-microservice.md)
> [下一頁](database-server-container.md)
