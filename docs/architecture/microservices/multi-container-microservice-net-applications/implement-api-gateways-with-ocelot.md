---
title: 使用 Ocelot 實作 API 閘道
description: 了解如何使用 Ocelot 實作 API 閘道，並了解如何在以容器為基礎的環境中使用 Ocelot。
ms.date: 03/02/2020
ms.openlocfilehash: 28b9ca22d232baf3545d71b876cecf72fea05c92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846942"
---
# <a name="implement-api-gateways-with-ocelot"></a>使用 Ocelot 實作 API 閘道

> [!IMPORTANT]
> 參考微服務應用程式[eShopOn容器](https://github.com/dotnet-architecture/eShopOnContainers)目前使用[特使](https://www.envoyproxy.io/)提供的功能來實現API閘道，而不是前面引用[的Ocelot。](https://github.com/ThreeMammals/Ocelot)
> 我們之所以做出此設計選擇，是因為特使對 WebSocket 協定的內置支援，這是 eShopOnContainers 中實現的新 gRPC 服務間通信所要求的。
> 但是，我們在指南中保留了此部分，因此您可以將 Ocelot 視為一種簡單、強大且羽量級的 API 閘道，適用于生產級方案。

## <a name="architect-and-design-your-api-gateways"></a>架構及設計您的 API 閘道

下面的體系結構圖顯示了如何在 eShopOn 容器中使用 Ocelot 實現 API 閘道。

![顯示 eShopOn 容器體系結構的圖表。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

**圖 6-28**。 使用 API 閘道的 eShopOnContainers 架構

該圖顯示了如何將整個應用程式部署到具有"為 Windows 的 Docker"或"Mac 的 Docker"的單個 Docker 主機或開發 PC 中。 但是，部署到任何協調器都類似，但關係圖中的任何容器都可以在協調器中展開。

此外，基礎結構資產 (例如資料庫、快取和訊息代理程式) 應該從協調器卸載，並部署到基礎結構的高可用性系統，例如 Azure SQL Database、Azure Cosmos DB、Azure Redis、Azure 服務匯流排或任何內部部署 HA 叢集解決方案。

正如您在關係圖中也可以注意到的，在開發和部署其微服務以及自己的相關 API 閘道時，擁有多個 API 閘道允許多個開發團隊具有自主性（在本例中，行銷功能與購物功能）。

如果您有單一整合型 API 閘道，這會是要由多個開發小組更新的單一點，並可結合所有微服務與應用程式的單一組件。

更進一步設計時，有時也可以根據所選擇的架構，將微調 API 閘道限制為單一商務微服務。 讓 API 閘道的邊界由業務或域決定，將説明您獲得更好的設計。

例如，API 閘道層中的細微性可能特別適用於根據微服務的更進階複合 UI 應用程式，因為微調 API 閘道概念類似於 UI 組合服務。

我們有在先前的章節[建立以微服務為基礎的複合 UI](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md)中進行更深入的探討。

其重點在於，針對許多中型和大型應用程式，使用自訂建置的 API 閘道產品通常是不錯的方法，但不能作為單一整合型彙總工具或唯一中央自訂 API 閘道，除非該 API 閘道允許數個開發小組透過多個獨立設定區域建立自發微服務。

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a>範例微服務/容器透過 API 閘道重設路徑

例如，eShopOnContainers 大約有六個內部微服務類型必須透過 API 閘道發佈，如下圖所示。

![顯示其子資料夾的服務資料夾的螢幕截圖。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

**圖 6-29**。 Visual Studio 之 eShopOnContainers 方案中的微服務資料夾

關於識別服務，其設計是不包含在 API 閘道路由中，因為它是系統中的唯一跨領域考量，但使用 Ocelot 時，還可能包含它作為重設路徑清單的一部分。

上述所有服務目前會實作為 ASP.NET Core Web API 服務，如程式碼所示。 讓我們關注一個微服務，如目錄微服務代碼。

![顯示目錄.API 專案內容的解決方案資源管理器螢幕截圖。](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

**圖 6-30**。 範例 Web API 微服務 (目錄微服務)

如您所見，目錄微服務是一般 ASP.NET Core Web API 專案，其中包含數個控制器和方法，如下列程式碼所示。

```csharp
[HttpGet]
[Route("items/{id:int}")]
[ProducesResponseType((int)HttpStatusCode.BadRequest)]
[ProducesResponseType((int)HttpStatusCode.NotFound)]
[ProducesResponseType(typeof(CatalogItem),(int)HttpStatusCode.OK)]
public async Task<IActionResult> GetItemById(int id)
{
    if (id <= 0)
    {
        return BadRequest();
    }
    var item = await _catalogContext.CatalogItems.
                                          SingleOrDefaultAsync(ci => ci.Id == id);
    //…

    if (item != null)
    {
        return Ok(item);
    }
    return NotFound();
}
```

HTTP 要求最終會執行該類型的 C# 程式碼來存取微服務資料庫，並執行任何其他必要動作。

關於微服務 URL，當容器部署在本地開發 PC（本地 Docker 主機）中時，每個微服務的容器始終具有在其 dockerfile 中指定的內部埠（通常是埠 80），如以下 dockerfile 中：

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
```

程式碼中顯示的連接埠 80 位於 Docker 主機內部，因此用戶端應用程式無法連線到該連接埠。

用戶端應用程式只能存取使用 `docker-compose` 部署時所發佈的外部連接埠 (如果有的話)。

部署到生產環境時，不應該發佈這些外部連接埠。 這就是為什麼您想要使用 API 閘道來避免用戶端應用程式與微服務之間的直接通訊。

不過，開發時，您想要直接存取微服務/容器，並透過 Swagger 來執行。 這就是為什麼在 eShopOn 容器中，即使 API 閘道或用戶端應用不會使用它們，也會指定外部埠。

下面是目錄微服務`docker-compose.override.yml`的檔示例：

```yml
catalog-api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes.
                  # The API Gateway redirects and access through the internal port (80).
```

如您所見，在 docker-compose.override.yml 設定中，目錄容器的內部連接埠是連接埠 80，但外部存取的連接埠是 5101。 但是，應用程式在使用 API 閘道時不應使用此埠，而只能調試、運行和測試目錄微服務。

通常，您不會使用 Docker-compose 部署到生產環境中，因為微服務的正確生產部署環境是像 Kubernetes 或服務結構這樣的協調器。 部署到這些環境時，您使用不同的設定檔，在這些設定檔中，不會直接發佈微服務的任何外部埠，但始終使用 API 閘道的反向代理。

在本地 Docker 主機中運行目錄微服務。 要麼從 Visual Studio 運行完整的 eShopOnContainers 解決方案（它運行 Docker-compose 檔中的所有服務），要麼在 CMD 或 PowerShell 中使用以下 docker 組合命令啟動目錄微服務`docker-compose.yml`，`docker-compose.override.yml`該命令位於 放置 和 的資料夾中。

```console
docker-compose run --service-ports catalog-api
```

此命令僅運行在 docker-compose.yml 中指定的目錄 api 服務容器以及依賴項。 在本例中為 SQL Server 容器和 RabbitMQ 容器。

然後，您可以直接存取目錄微服務，並通過 Swagger UI 直接通過該"外部"埠訪問其方法，在這種情況下`http://localhost:5101/swagger`：

![顯示目錄.API REST API 的斯瓦格 UI 的螢幕截圖。](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

**圖 6-31**。 使用其 Swagger UI 測試目錄微服務

此時，您可以在 Visual Studio 的 C# 程式碼中設定中斷點、使用在 Swagger UI 中公開的方法測試微服務，最後使用 `docker-compose down` 命令清除所有內容。

不過，建議您在應用程式中避免微服務的直接存取通訊，在本例中是透過外部連接埠 5101。 您可以設定額外的 API 閘道間接層 (在本例中為 Ocelot) 來避免此問題。 這樣，用戶端應用將不會直接存取微服務。

## <a name="implementing-your-api-gateways-with-ocelot"></a>使用 Ocelot 實作您的 API 閘道

Ocelot 基本上是可依特定順序套用的一組中介軟體。

Ocelot 設計成只能搭配 ASP.NET Core 使用。 包的最新版本面向目標`.NETCoreApp 3.1`，因此不適合 .NET 框架應用程式。

您可以從 Visual Studio 透過 [Ocelot 的 NuGet 套件](https://www.nuget.org/packages/Ocelot/)在 ASP.NET Core 專案中安裝 Ocelot 及其相依性。

```powershell
Install-Package Ocelot
```

在 eShopOn容器中，其 API 閘道實現是一個簡單的ASP.NET核心 WebHost 專案，Ocelot 的中介軟體處理所有 API 閘道功能，如下圖所示：

![顯示 Ocelot API 閘道專案的解決方案資源管理器螢幕截圖。](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

**圖 6-32**。 eShopOnContainers 中的 OcelotApiGw 基底專案

此 ASP.NET Core WebHost 專案基本上由兩個簡單的檔案所組成：`Program.cs` 和 `Startup.cs`。

Program.cs 只需要建立及設定一般 ASP.NET Core BuildWebHost。

```csharp
namespace OcelotApiGw
{
    public class Program
    {
        public static void Main(string[] args)
        {
            BuildWebHost(args).Run();
        }

        public static IWebHost BuildWebHost(string[] args)
        {
            var builder = WebHost.CreateDefaultBuilder(args);

            builder.ConfigureServices(s => s.AddSingleton(builder))
                    .ConfigureAppConfiguration(
                          ic => ic.AddJsonFile(Path.Combine("configuration",
                                                            "configuration.json")))
                    .UseStartup<Startup>();
            var host = builder.Build();
            return host;
        }
    }
}
```

對於 Ocelot 而言，此處的重點是您必須透過 `AddJsonFile()` 方法提供給產生器的 `configuration.json` 檔案。 該 `configuration.json` 是您指定所有 API 閘道重設路徑的位置，表示具有特定連接埠的外部端點及相互關聯的內部端點 (通常使用不同的連接埠)。

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

設定分成兩個部分。 重新路由和全域配置的陣列。 ReRoutes 是告訴 Ocelot 如何處理上游請求的物件。 全域配置允許重寫特定設置。 如果您不想管理大量重新路由特定設置，則此功能非常有用。

下面是從 eShopOn 容器的 API 閘道之一[重新路由設定檔](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json)的簡化示例。

```json
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/c/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ]
    },
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }

  ],
    "GlobalConfiguration": {
      "RequestIdKey": "OcRequestId",
      "AdministrationPath": "/administration"
    }
  }
```

Ocelot API 閘道的主要功能是接受傳入 HTTP 要求並將其轉送到下游服務 (目前為另一個 HTTP 要求)。 Ocelot 將一個請求路由到另一個請求描述為"重新路由"。

例如，讓我們關注配置中的 ReRoutes 之一，即"購物籃"微服務的配置。

```json
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
}
```

DownstreamPathTemplate、Scheme 和 DownstreamHostAndPorts 會建立此要求將轉送的內部微服務 URL。

連接埠是服務所使用的內部連接埠。 使用容器時，連接埠是在其 dockerfile 中指定。

`Host` 是相依於您使用之服務名稱解析的服務名稱。 使用 docker-compose 時，服務名稱是由 Docker 主機提供，也就是使用 docker-compose 檔案所提供的服務名稱。 如果使用 Kubernetes 或 Service Fabric 等協調器，該名稱應該透過 DNS 或每個協調器提供的名稱解析來解析。

DownstreamHostAndPorts 是包含您想要轉送要求的任何下游服務之主機和連接埠的陣列。 這通常只會包含一個項目，但有時您可能想要將要求負載平衡至您的下游服務，而 Ocelot 可讓您新增多個項目，然後選取負載平衡器。 但如果使用 Azure 及任何協調器，最好透過雲端和協調器基礎結構進行負載平衡。

UpstreamPathTemplate 是 URL，可供 Ocelot 用來識別針對用戶端中的指定要求使用哪個 DownstreamPathTemplate。 最後，使用 UpstreamHttpMethod，讓 Ocelot 可以區別傳送至相同 URL 的不同要求 (GET、POST、PUT)。

此時，您可能會有使用一或[多個合併 configuration.json 檔案](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files)的單一 Ocelot API 閘道 (ASP.NET Core WebHost)，您也可以[在 Consul KV 存放區中儲存設定](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul)。

但如架構及設計一節所介紹，如果您真的想要有自發微服務，最好將單一整合型 API 閘道分割成多個 API 閘道及/或 BFF (前端的後端)。 為此，讓我們看看如何使用 Docker 容器實現該方法。

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a>使用單一 Docker 容器映像執行多個不同的 API 閘道/BFF 容器類型

在 eShopOn容器中，我們使用 Ocelot API 閘道的單個 Docker 容器映射，但在運行時，我們通過提供不同的配置.json 檔，使用 Docker 卷訪問每個服務的不同 PC 資料夾，為每種類型 API 閘道/BFF 創建不同的服務/容器。

![所有 API 閘道的單個 Ocelot 閘道 Docker 映射圖。](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

**圖 6-33**。 在多個 API 閘道類型之間重複使用單一 Ocelot Docker 映像

在 eShopOn 容器中，使用名為"OcelotApiGw"的專案和在 docker-compose.yml 檔中指定的映射名稱"eshop/ocelotapigw"創建"通用 Ocelot API 閘道 Docker 映射"。 然後，當部署到 Docker 時，會從該相同的 Docker 映像建立四個 API 閘道容器，如下列 docker-compose.yml 檔案摘錄所示。

```yml
  mobileshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  mobilemarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webmarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile
```

此外，如您在以下 docker-compose.override.yml 檔案中所見，這些 API 閘道容器之間的唯一差異是 Ocelot 設定檔，每個服務容器會有不同的檔案，而且該檔案會在執行階段透過 Docker 磁碟區指定。

```yml
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5200:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration

mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5201:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5202:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5203:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

基於上述程式碼，而且如下面的 Visual Studio 總管所示，定義每個特定業務/BFF API 閘道所需的唯一檔案只有 configuration.json 檔案，因為這四個 API 閘道是以相同的 Docker 映像為依據。

![顯示所有具有配置.json 檔的 API 閘道的螢幕截圖。](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

**圖 6-34**。 使用 Ocelot 定義每個 API 閘道/BFF 所需的唯一檔案是設定檔

將 API 閘道分割成多個 API 閘道之後，著重於不同微服務子集的不同開發小組就可以使用獨立的 Ocelot 設定檔來管理自己的 API 閘道。 此外，他們還可以同時重複使用相同的 Ocelot Docker 映像。

現在，如果您使用 API 閘道運行 eShopOn 容器（在打開 eShopOnContainers-ServicesAndWebApps.sln 解決方案時預設包含在 VS 中，或者如果運行"docker-compose-up"），將執行以下示例路由。

例如，瀏覽 webshoppingapigw API 閘道所提供的上游 URL `http://localhost:5202/api/v1/c/catalog/items/2/` 時，您會從 Docker 主機的內部下游 URL `http://catalog-api/api/v1/2` 取得相同結果，如下列瀏覽器所示。

![顯示通過 API 閘道的回應的瀏覽器螢幕截圖。](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

**圖 6-35**。 透過 API 閘道提供的 URL 存取微服務

由於測試或調試的原因，如果要直接存取目錄 Docker 容器（僅在開發環境中），而無需通過 API 閘道，因為"目錄 api"是 Docker 主機內部的 DNS 解析（由 Docker-compose 服務名稱處理的服務發現），直接存取該容器的唯一方法是通過 Docker-compose.override.yml 中發佈的外部埠，該容器僅提供用於開發測試，例如`http://localhost:5101/api/v1/Catalog/items/1`在以下瀏覽器中。

![顯示對目錄的直接回應的瀏覽器螢幕截圖。](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

**圖 6-36**。 直接存取微服務以進行測試

但是，應用程式被配置，所以它通過 API 閘道訪問所有微服務，而不是通過直接埠"快捷方式"。

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a>eShopOnContainers 中的閘道彙總模式

如前所介紹，實作要求彙總的一個彈性方法，就是透過程式碼使用自訂服務。 您也可以使用 [Ocelot 中的 Request Aggregation](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation) (要求彙總) 功能來實作要求彙總，但其彈性可能不符合您的需求。 因此，在 eShopOn容器中實現聚合的選定方法是為每個聚合器提供顯式ASP.NET核心 Web API 服務。

根據該方法，考量到上述簡化全域架構圖中未顯示的彙總工具服務，API 閘道組合圖實際上會涵蓋更大範圍。

在下圖中，您也可以查看彙總工具服務如何搭配其相關 API 閘道使用。

![顯示聚合器服務的 eShopOn 容器體系結構圖。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

**圖 6-37**。 使用彙總工具服務的 eShopOnContainers 架構

在下圖中的"購物"業務區域上進一步放大，您可以看到，在 API 閘道中使用聚合器服務時，用戶端應用和微服務之間的聊天量會減少。

![顯示 eShopOn 容器體系結構放大的圖表。](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

**圖 6-38**。 放大檢視彙總工具服務

您可以注意到當關係圖顯示來自 API 閘道的可能請求時，它可能會變得複雜。 雖然您可以看到藍色箭號如何簡化，但從用戶端應用程式觀點來看，當使用彙總工具模式時，若能減少通訊中的頻繁交談和延遲，最終特別會大幅改善遠端應用程式 (行動和 SPA 應用程式) 的使用者體驗。

對於"行銷"業務領域和微服務，這是一個簡單的用例，因此無需使用聚合器，但如果需要，也可以使用聚合器。

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a>Ocelot API 閘道中的驗證與授權

在 Ocelot API 閘道中，您可以將驗證服務 (例如使用 [IdentityServer](https://identityserver.io/) 提供驗證權杖的 ASP.NET Core Web API 服務) 放在 API 閘道外部或內部。

由於 eShopOnContainers 使用多個具有依據 BFF 和業務領域之界限的 API 閘道，因此識別/驗證服務不會包含在 API 閘道中 (在下圖中以黃色醒目提示)。

![顯示 API 閘道下方的標識微服務圖。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

**圖 6-39**。 識別服務在 eShopOnContainers 中的位置

不過，Ocelot 也支援將識別/驗證微服務放在 API 閘道界限內，如下面另一個圖所示。

![顯示 Ocelot API 閘道中身份驗證的圖表。](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

**圖 6-40**。 Ocelot 的驗證

如上圖所示，當標識微服務位於 API 閘道 （AG） 下方時：1） AG 從標識微服務請求身份驗證權杖時，2） 標識微服務使用身份驗證權杖將權杖返回 AG，3-4） 使用 auth 權杖從微服務請求。 由於 eShopOn 容器應用程式將 API 閘道拆分為多個 BFF（前端後端）和業務區域 API 閘道，因此另一個選項是創建一個額外的 API 閘道，以便解決跨領域問題。 該選擇相當適合具有多個跨領域考量微服務的更複雜微服務型架構。 由於 eShopOnContainers 中只有一個貫穿各領域的問題，因此出於簡單起見，決定只處理 API 閘道領域之外的安全服務。

在任何情況下，如果在 API 閘道層級保護應用程式，當嘗試使用任何受保護的微服務時，會先瀏覽 Ocelot API 閘道的驗證模組。 這重定向了 HTTP 要求以訪問標識或身份驗證微服務以獲取訪問權杖，以便您可以使用access_token訪問受保護的服務。

您在 API 閘道層級使用驗證保護任何服務的方式，就是在 configuration.json 中設定其相關設定的 AuthenticationProviderKey。

```json
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }
```

當 Ocelot 運行時，它將查看重新路由身份驗證選項.身份檢查器提供者金鑰，並檢查是否有使用給定金鑰註冊的身份檢查器提供者。 如果沒有，則 Ocelot 將無法啟動。 如果有，則重設路徑將會在執行時使用該提供者。

由於 Ocelot WebHost 是使用 `authenticationProviderKey = "IdentityApiKey"` 設定，因此只要服務有任何要求沒有任何驗證權杖，就需要驗證。

```csharp
namespace OcelotApiGw
{
    public class Startup
    {
        private readonly IConfiguration _cfg;

        public Startup(IConfiguration configuration) => _cfg = configuration;

        public void ConfigureServices(IServiceCollection services)
        {
            var identityUrl = _cfg.GetValue<string>("IdentityUrl");
            var authenticationProviderKey = "IdentityApiKey";
                         //…
            services.AddAuthentication()
                .AddJwtBearer(authenticationProviderKey, x =>
                {
                    x.Authority = identityUrl;
                    x.RequireHttpsMetadata = false;
                    x.TokenValidationParameters = new Microsoft.IdentityModel.Tokens.TokenValidationParameters()
                    {
                        ValidAudiences = new[] { "orders", "basket", "locations", "marketing", "mobileshoppingagg", "webshoppingagg" }
                    };
                });
            //...
        }
    }
}
```

然後，您也需要在任何要存取的資源 (例如微服務) 上透過 [Authorize] 屬性設定授權，例如在下列購物籃微服務控制器中。

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class BasketController : Controller
    {
      //...
    }
}
```

"購物籃"等有效訪問群體與"啟動"類的"佈建服務（）"`AddJwtBearer()`中在每個微服務中定義的訪問群體相關，如下面的代碼。

```csharp
// prevent from mapping "sub" claim to nameidentifier.
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();

var identityUrl = Configuration.GetValue<string>("IdentityUrl");

services.AddAuthentication(options =>
{
    options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
    options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

}).AddJwtBearer(options =>
{
    options.Authority = identityUrl;
    options.RequireHttpsMetadata = false;
    options.Audience = "basket";
});
```

如果您嘗試訪問任何安全的微服務，如基於 API 閘道的`http://localhost:5202/api/v1/b/basket/1`ReRoute URL 的購物籃微服務，則除非提供有效的權杖，否則您將獲得 401 未經授權的服務。 另一方面，如果 ReRoute URL 已過身份驗證，Ocelot 將調用與其關聯的任何下游方案（內部微服務 URL）。

**在 Ocelot 的 ReRoutes 層授權。**  Ocelot 支援在驗證後評估宣告式授權。 您可以透過將下列程式行新增至 ReRoute 組態，在路由層級設定授權。

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

在該範例中，當呼叫授權中介軟體時，Ocelot 會查明使用者在權杖中是否有宣告類型 'UserType'，以及該宣告的值是否為 'employee'。 如果不是，則使用者將不獲得授權，並且將禁止回應 403。

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a>使用 Kubernetes 輸入加上 Ocelot API 閘道

使用庫伯奈斯（如在 Azure 庫伯內斯服務群集中）時，通常基於*Nginx*通過[庫貝內斯入口層](https://kubernetes.io/docs/concepts/services-networking/ingress/)統一所有 HTTP 要求。

在 Kubernetes 中，如果不使用任何入口方法，則服務和窗格的 IP 只能由群集網路路由。

但如果您使用輸入方法，您就會在網際網路與服務 (包括 API 閘道) 之間有一個中介層作為反向 Proxy。

按照定義，輸入是允許輸入連線到達叢集服務的規則集合。 輸入通常會設定為提供服務可從外部連線的 URL、負載平衡流量、SSL 終止等項目。 使用者透過將輸入資源張貼到 API 伺服器來要求輸入。

在 eShopOnContainers 中，當您在本機開發並只使用您的開發電腦作為 Docker 主機時，您不會使用任何輸入，而只會使用多個 API 閘道。

但是，當針對基於 Kubernetes 的"生產"環境時，eShopOnContainers 正在 API 閘道前使用入口。 如此一來，用戶端仍會呼叫相同的基底 URL，但要求會路由至多個 API 閘道或 BFF。

API 閘道是前端或立面，僅顯示服務，而不是通常不在其範圍範圍內的 Web 應用程式。 此外，API 閘道可能會隱藏特定內部微服務。

不過，輸入只會重新導向 HTTP，而不會嘗試隱藏任何微服務或 Web 應用程式。

在 Web 應用程式前端的 Kubernetes 中有一個輸入 Nginx 層加上數個 Ocelot API 閘道/BFF 是理想的架構，如下圖所示。

![顯示入口層如何適應 AKS 環境的圖表。](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

**圖 6-41**。 部署至 Kubernetes 時之 eShopOnContainers 中的輸入層

Kubernetes 輸入扮演著所有對應用程式流量的反向 Proxy 角色，其中包括通常不在 API 閘道範圍內的 Web 應用程式。 當您將 eShopOnContainers 部署到 Kubernetes 時，它只會透過「輸入」__ 公開一些服務或端點，基本上包括 URL 上的下列後置詞清單：

- `/` 代表用戶端 SPA Web 應用程式
- `/webmvc` 代表用戶端 MVC Web 應用程式
- `/webstatus` 代表顯示狀態/健康狀態檢查的用戶端 Web 應用程式
- `/webshoppingapigw` 代表 Web BFF 和購物商務程序
- `/webmarketingapigw` 代表 Web BFF 和行銷商務程序
- `/mobileshoppingapigw` 代表行動 BFF 和購物商務程序
- `/mobilemarketingapigw` 代表行動 BFF 和行銷商務程序

部署到 Kubernetes 時，每個 Ocelot API 閘道對運行 API 閘道的每個_Pod_使用不同的"配置.json"檔。 這些"配置.json"檔是通過安裝（最初使用 Deploy.ps1 腳本）基於名為"ocelot"的 Kubernetes_配置映射_創建的卷來提供的。 每個容器都將其相關設定檔裝載到名為`/app/configuration`的容器檔案夾中。

在 eShopOnContainers 的原始程式碼檔中，可以在`k8s/ocelot/`資料夾中找到原始的"配置.json"檔。 每個 BFF/APIGateway 都有一個檔。

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a>Ocelot API 閘道中的其他跨領域功能

使用 Ocelot API 閘道時，還有其他重要的功能可供探索及使用，下列連結將進行說明。

- **客戶方的服務發現 將 Ocelot 與領事或尤里卡整合** \
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- **在 API 閘道層緩存** \
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- **在 API 閘道層登錄** \
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- **API 閘道層的服務品質（重試和斷路器）** \
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- **速率限制** \
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> [上一個](background-tasks-with-ihostedservice.md)
> [下一個](../microservice-ddd-cqrs-patterns/index.md)
