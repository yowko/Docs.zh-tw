---
title: 使用 Ocelot 實作 API 閘道
description: 了解如何使用 Ocelot 實作 API 閘道，並了解如何在以容器為基礎的環境中使用 Ocelot。
ms.date: 10/02/2018
ms.openlocfilehash: 1ade05cc6935ce6a1bc74e6d6e4cdd5ef9fc6873
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734604"
---
# <a name="implement-api-gateways-with-ocelot"></a>使用 Ocelot 實作 API 閘道

參考微服務應用程式[eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers)使用[Ocelot](https://github.com/ThreeMammals/Ocelot)，這是一種簡單且輕量的 API 閘道，您可以在任何地方與您的微服務/容器一起部署，例如在 eShopOnContainers 所使用的下列任何環境中：

- 您本機開發電腦、內部部署或雲端中的 Docker 主機。
- 內部部署或受控雲端 (例如 Azure Kubernetes Service (AKS)) 中的 Kubernetes 叢集。
- 內部部署或雲端中的 Service Fabric 叢集。
- 在 Azure 中以 PaaS/無伺服器形式提供的 Service Fabric 網格。

## <a name="architect-and-design-your-api-gateways"></a>架構及設計您的 API 閘道

下列架構圖說明如何在 eShopOnContainers 中使用 Ocelot 實作 API 閘道。

![顯示 eShopOnContainers 架構的圖表。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

**圖 6-28**。 使用 API 閘道的 eShopOnContainers 架構

該圖顯示整個應用程式如何部署到具有 "適用於 Windows 的 Docker" 或 "Docker for Mac" 的單一 Docker 主機或開發電腦。 不過，部署至任何協調器會很類似，但圖表中的任何容器都可以在協調器中相應放大。

此外，基礎結構資產 (例如資料庫、快取和訊息代理程式) 應該從協調器卸載，並部署到基礎結構的高可用性系統，例如 Azure SQL Database、Azure Cosmos DB、Azure Redis、Azure 服務匯流排或任何內部部署 HA 叢集解決方案。

您也可以在圖表中注意到，有數個 API 閘道可讓多個開發小組在開發和部署其微服務以及自己的相關 API 閘道時，自主（在此案例中為行銷功能與購物功能）。

如果您有單一整合型 API 閘道，這會是要由多個開發小組更新的單一點，並可結合所有微服務與應用程式的單一組件。

更進一步設計時，有時也可以根據所選擇的架構，將微調 API 閘道限制為單一商務微服務。 擁有商務或領域所規定的 API 閘道界限，將可協助您取得更好的設計。

例如，API 閘道層中的細微性可能特別適用於根據微服務的更進階複合 UI 應用程式，因為微調 API 閘道概念類似於 UI 組合服務。

我們有在先前的章節[建立以微服務為基礎的複合 UI](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md)中進行更深入的探討。

其重點在於，針對許多中型和大型應用程式，使用自訂建置的 API 閘道產品通常是不錯的方法，但不能作為單一整合型彙總工具或唯一中央自訂 API 閘道，除非該 API 閘道允許數個開發小組透過多個獨立設定區域建立自發微服務。

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a>範例微服務/容器透過 API 閘道重設路徑

例如，eShopOnContainers 大約有六個內部微服務類型必須透過 API 閘道發佈，如下圖所示。

![[服務] 資料夾的螢幕擷取畫面，其中顯示其子資料夾。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

**圖 6-29**。 Visual Studio 之 eShopOnContainers 方案中的微服務資料夾

關於識別服務，其設計是不包含在 API 閘道路由中，因為它是系統中的唯一跨領域考量，但使用 Ocelot 時，還可能包含它作為重設路徑清單的一部分。

上述所有服務目前會實作為 ASP.NET Core Web API 服務，如程式碼所示。 讓我們將焦點放在其中一個微服務，例如目錄微服務程式代碼。

![顯示目錄. API 專案內容方案總管的螢幕擷取畫面。](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

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

關於微服務 URL，當容器部署在您的本機開發電腦（本機 Docker 主機）時，每個微服務的容器一律會在其 dockerfile 中指定內部埠（通常是埠80），如下列 dockerfile 所示：

```Dockerfile
FROM microsoft/aspnetcore:2.0.5 AS base
WORKDIR /app
EXPOSE 80
```

程式碼中顯示的連接埠 80 位於 Docker 主機內部，因此用戶端應用程式無法連線到該連接埠。

用戶端應用程式只能存取使用 `docker-compose` 部署時所發佈的外部連接埠 (如果有的話)。

部署到生產環境時，不應該發佈這些外部連接埠。 這就是為什麼您想要使用 API 閘道來避免用戶端應用程式與微服務之間的直接通訊。

不過，開發時，您想要直接存取微服務/容器，並透過 Swagger 來執行。 這就是為什麼在 eShopOnContainers 中，即使 API 閘道或用戶端應用程式不會使用外部埠，仍然會指定它們。

以下是目錄微服務的 `docker-compose.override.yml` 檔案範例：

```yml
catalog.api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes.
                  # The API Gateway redirects and access through the internal port (80).
```

如您所見，在 docker-compose.override.yml 設定中，目錄容器的內部連接埠是連接埠 80，但外部存取的連接埠是 5101。 但在使用 API 閘道時，應用程式不應該使用此埠，只是用來對目錄微服務進行 debug、run 和測試。

一般來說，您不會使用 docker 撰寫部署到生產環境，因為適用于微服務的正確生產部署環境是協調器，例如 Kubernetes 或 Service Fabric。 當您部署到這些環境時，您會使用不同的設定檔，而您不會直接發行微服務的任何外部埠，而是一律會從 API 閘道使用反向 proxy。

在您的本機 Docker 主機中執行目錄微服務。 請從 Visual Studio 執行完整的 eShopOnContainers 解決方案（它會執行 docker 撰寫檔案中的所有服務），或使用 CMD 或 PowerShell 中的下列 docker 撰寫命令，在放置 `docker-compose.yml` 和 `docker-compose.override.yml` 的資料夾中啟動目錄微服務。

```console
docker-compose run --service-ports catalog.api
```

此命令只會執行 catalog.api 服務容器及 docker-compose.yml 中指定的相依性。 在本例中為 SQL Server 容器和 RabbitMQ 容器。

然後，您可以直接存取目錄微服務，並透過直接透過該「外部」埠存取的 Swagger UI 查看其方法，在此情況下 `http://localhost:5101/swagger`：

![顯示目錄. API REST API 的 Swagger UI 螢幕擷取畫面。](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

**圖 6-31**。 使用其 Swagger UI 測試目錄微服務

此時，您可以在 Visual Studio 的 C# 程式碼中設定中斷點、使用在 Swagger UI 中公開的方法測試微服務，最後使用 `docker-compose down` 命令清除所有內容。

不過，建議您在應用程式中避免微服務的直接存取通訊，在本例中是透過外部連接埠 5101。 您可以設定額外的 API 閘道間接層 (在本例中為 Ocelot) 來避免此問題。 如此一來，用戶端應用程式就不會直接存取微服務。

## <a name="implementing-your-api-gateways-with-ocelot"></a>使用 Ocelot 實作您的 API 閘道

Ocelot 基本上是可依特定順序套用的一組中介軟體。

Ocelot 設計成只能搭配 ASP.NET Core 使用。 它以 netstandard2.0 為目標，因此可用於支援 .NET Standard 2.0 的任何位置，包括 .NET Core 2.0 執行階段以及 .NET Framework 4.6.1 執行階段和更新版本。

您可以從 Visual Studio 透過 [Ocelot 的 NuGet 套件](https://www.nuget.org/packages/Ocelot/)在 ASP.NET Core 專案中安裝 Ocelot 及其相依性。

```powershell
Install-Package Ocelot
```

在 eShopOnContainers 中，其 API 閘道的執行是簡單的 ASP.NET Core WebHost 專案，而 Ocelot 的中介軟體會處理所有 API 閘道功能，如下圖所示：

![顯示 Ocelot API 閘道專案的方案總管螢幕擷取畫面。](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

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

設定分成兩個部分。 重置和 GlobalConfiguration 的陣列。 重置是告訴 Ocelot 如何處理上游要求的物件。 全域設定允許覆寫重新路由的特定設定。 如果您不想要管理大量的重新路由特定設定，這會很有用。

以下是從 eShopOnContainers 的其中一個 API 閘道重新[路由設定檔](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json)案的簡單範例。

```json
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog.api",
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
          "Host": "basket.api",
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

Ocelot API 閘道的主要功能是接受傳入 HTTP 要求並將其轉送到下游服務 (目前為另一個 HTTP 要求)。 Ocelot 的描述會將一個要求路由傳送至另一個，做為重新路由。

例如，讓我們將焦點放在上述的設定中的其中一個重做，這是購物籃微服務的設定。

```json
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
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

但如架構及設計一節所介紹，如果您真的想要有自發微服務，最好將單一整合型 API 閘道分割成多個 API 閘道及/或 BFF (前端的後端)。 基於此目的，讓我們來瞭解如何使用 Docker 容器來執行該方法。

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a>使用單一 Docker 容器映像執行多個不同的 API 閘道/BFF 容器類型

在 eShopOnContainers 中，我們會使用單一 Docker 容器映射搭配 Ocelot API 閘道，但是在執行時間，我們會提供不同的設定 json 檔案，為每一種 API 閘道/BFF 建立不同的服務/容器，方法是使用 Docker 磁片區來存取每個服務的不同電腦資料夾。

![適用于所有 API 閘道的單一 Ocelot 閘道 Docker 映射圖表。](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

**圖 6-33**。 在多個 API 閘道類型之間重複使用單一 Ocelot Docker 映像

在 eShopOnContainers 中，會使用名為 ' OcelotApiGw ' 的專案和 OcelotApiGw 檔案中指定的映射名稱 "eshop/docker-compose.dev.debug.yml" 來建立「一般 Ocelot API 閘道 Docker 映射」。 然後，當部署到 Docker 時，會從該相同的 Docker 映像建立四個 API 閘道容器，如下列 docker-compose.yml 檔案摘錄所示。

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
    - IdentityUrl=http://identity.api
  ports:
    - "5200:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration

mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5201:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5202:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5203:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

基於上述程式碼，而且如下面的 Visual Studio 總管所示，定義每個特定業務/BFF API 閘道所需的唯一檔案只有 configuration.json 檔案，因為這四個 API 閘道是以相同的 Docker 映像為依據。

![螢幕擷取畫面：顯示具有設定 json 檔案的所有 API 閘道。](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

**圖 6-34**。 使用 Ocelot 定義每個 API 閘道/BFF 所需的唯一檔案是設定檔

將 API 閘道分割成多個 API 閘道之後，著重於不同微服務子集的不同開發小組就可以使用獨立的 Ocelot 設定檔來管理自己的 API 閘道。 此外，他們還可以同時重複使用相同的 Ocelot Docker 映像。

現在，如果您使用 API 閘道執行 eShopOnContainers （在開啟 Eshoponcontainers-servicesandwebapps.sln 方案或執行「docker-撰寫」時，VS 中預設包含），將會執行下列範例路由。

例如，瀏覽 webshoppingapigw API 閘道所提供的上游 URL `http://localhost:5202/api/v1/c/catalog/items/2/` 時，您會從 Docker 主機的內部下游 URL `http://catalog.api/api/v1/2` 取得相同結果，如下列瀏覽器所示。

![瀏覽器的螢幕擷取畫面，其中顯示透過 API 閘道的回應。](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

**圖 6-35**。 透過 API 閘道提供的 URL 存取微服務

基於測試或偵錯原因，如果您想要直接存取目錄 Docker 容器 (僅限開發環境) 而不透過 API 閘道傳遞，由於 'catalog.api' 是 Docker 主機內部的 DNS 解析 (由 docker-compose 服務名稱處理的服務探索)，因此直接存取容器的唯一方式是透過 docker-compose.override.yml 中發佈的外部連接埠，這只會提供給開發測試，例如下列瀏覽器中的 `http://localhost:5101/api/v1/Catalog/items/1`。

![瀏覽器的螢幕擷取畫面，其中顯示對目錄的直接回應。](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

**圖 6-36**。 直接存取微服務以進行測試

但已設定應用程式，因此它會透過 API 閘道存取所有微服務，而不是直接埠「快捷方式」。

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a>eShopOnContainers 中的閘道彙總模式

如前所介紹，實作要求彙總的一個彈性方法，就是透過程式碼使用自訂服務。 您也可以使用 [Ocelot 中的 Request Aggregation](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation) (要求彙總) 功能來實作要求彙總，但其彈性可能不符合您的需求。 因此，在 eShopOnContainers 中執行匯總所選取的方式是針對每一個匯總工具使用明確的 ASP.NET Core Web API 服務。

根據該方法，考量到上述簡化全域架構圖中未顯示的彙總工具服務，API 閘道組合圖實際上會涵蓋更大範圍。

在下圖中，您也可以查看彙總工具服務如何搭配其相關 API 閘道使用。

![顯示匯總工具服務的 eShopOnContainers 架構圖表。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

**圖 6-37**。 使用彙總工具服務的 eShopOnContainers 架構

進一步放大，在下圖的「購物」商務區域中，您可以看到在使用 API 閘道中的匯總工具服務時，用戶端應用程式和微服務之間的對話會降低。

![顯示 eShopOnContainers 架構放大的圖表。](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

**圖 6-38**。 放大檢視彙總工具服務

您可以注意到，當圖表顯示來自 API 閘道的可能要求時，可能會變得很複雜。 雖然您可以看到藍色箭號如何簡化，但從用戶端應用程式觀點來看，當使用彙總工具模式時，若能減少通訊中的頻繁交談和延遲，最終特別會大幅改善遠端應用程式 (行動和 SPA 應用程式) 的使用者體驗。

在「行銷」業務領域和微服務的情況下，這是一個簡單的使用案例，因此不需要使用匯總工具，但如果有需要，也可以這麼做。

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a>Ocelot API 閘道中的驗證與授權

在 Ocelot API 閘道中，您可以將驗證服務 (例如使用 [IdentityServer](https://identityserver.io/) 提供驗證權杖的 ASP.NET Core Web API 服務) 放在 API 閘道外部或內部。

由於 eShopOnContainers 使用多個具有依據 BFF 和業務領域之界限的 API 閘道，因此識別/驗證服務不會包含在 API 閘道中 (在下圖中以黃色醒目提示)。

![此圖顯示 API 閘道底下的身分識別微服務。](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

**圖 6-39**。 識別服務在 eShopOnContainers 中的位置

不過，Ocelot 也支援將識別/驗證微服務放在 API 閘道界限內，如下面另一個圖所示。

![此圖顯示 Ocelot API 閘道中的驗證。](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

**圖 6-40**。 Ocelot 的驗證

如上圖所示，當身分識別微服務位於 API 閘道（AG）底下時：1） AG 會向身分識別微服務要求驗證權杖，2） identity 微服務會使用驗證 token，將權杖傳回給 AG，3-4） AG 來自微服務的要求。 由於 eShopOnContainers 應用程式已將 API 閘道分割成多個 BFF (前端的後端) 和業務領域 API 閘道，因此另一個選擇是為跨領域考量建立其他 API 閘道。 該選擇相當適合具有多個跨領域考量微服務的更複雜微服務型架構。 因為在 eShopOnContainers 中只有一個跨領域考慮，所以已決定只是為了簡單起見，只會處理 API 閘道領域的安全性服務。

在任何情況下，如果在 API 閘道層級保護應用程式，當嘗試使用任何受保護的微服務時，會先瀏覽 Ocelot API 閘道的驗證模組。 這會將 HTTP 要求重新導向至身分識別或驗證微服務，以取得存取權杖，讓您可以流覽受保護的服務與 access_token。

您在 API 閘道層級使用驗證保護任何服務的方式，就是在 configuration.json 中設定其相關設定的 AuthenticationProviderKey。

```json
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
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

當 Ocelot 執行時，它會查看重排的 AuthenticationOptions. AuthenticationProviderKey，並檢查是否有向指定金鑰註冊的驗證提供者。 如果沒有，則 Ocelot 將無法啟動。 如果有，則重設路徑將會在執行時使用該提供者。

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

ValidAudiences （例如「購物籃」）會與每個微服務中定義的物件相互關聯，並 `AddJwtBearer()` 在啟動類別的 ConfigureServices （）中，如下列程式碼所示。

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

如果您嘗試存取任何受保護的微服務，例如購物籃微服務，並以 API 閘道（例如 `http://localhost:5202/api/v1/b/basket/1`）為基礎的重新路由 URL，則除非您提供有效的權杖，否則您會收到401未經授權。 相反地，如果重新路由 URL 經過驗證，Ocelot 會叫用與其相關聯的任何下游配置（內部微服務 URL）。

**Ocelot 的重做層級授權。**  Ocelot 支援在驗證後評估宣告式授權。 您可以透過將下列程式行新增至 ReRoute 組態，在路由層級設定授權。

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

在該範例中，當呼叫授權中介軟體時，Ocelot 會查明使用者在權杖中是否有宣告類型 'UserType'，以及該宣告的值是否為 'employee'。 如果不是，則不會授權使用者，而且回應會是403禁止。

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a>使用 Kubernetes 輸入加上 Ocelot API 閘道

使用 Kubernetes (例如 Azure Kubernetes Service 叢集) 時，您通常會透過以 *Nginx* 為基礎的 [Kuberentes 輸入層](https://kubernetes.io/docs/concepts/services-networking/ingress/) \(英文\) 來整合所有 HTTP 要求。

在 Kubernetes 中，如果您未使用任何輸入方法，則您的服務和 pod 只能透過叢集網路路由 Ip。

但如果您使用輸入方法，您就會在網際網路與服務 (包括 API 閘道) 之間有一個中介層作為反向 Proxy。

按照定義，輸入是允許輸入連線到達叢集服務的規則集合。 輸入通常會設定為提供服務可從外部連線的 URL、負載平衡流量、SSL 終止等項目。 使用者透過將輸入資源張貼到 API 伺服器來要求輸入。

在 eShopOnContainers 中，當您在本機開發並只使用您的開發電腦作為 Docker 主機時，您不會使用任何輸入，而只會使用多個 API 閘道。

不過，當目標為以 Kubernetes 為基礎的「生產」環境時，eShopOnContainers 會使用 API 閘道前面的輸入。 如此一來，用戶端仍會呼叫相同的基底 URL，但要求會路由至多個 API 閘道或 BFF。

API 閘道是前端或會外觀) 只呈現服務，而不是通常在其範圍外的 web 應用程式。 此外，API 閘道可能會隱藏特定內部微服務。

不過，輸入只會重新導向 HTTP，而不會嘗試隱藏任何微服務或 Web 應用程式。

在 Web 應用程式前端的 Kubernetes 中有一個輸入 Nginx 層加上數個 Ocelot API 閘道/BFF 是理想的架構，如下圖所示。

![顯示輸入層如何融入 AKS 環境的圖表。](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

**圖 6-41**。 部署至 Kubernetes 時之 eShopOnContainers 中的輸入層

Kubernetes 輸入扮演著所有對應用程式流量的反向 Proxy 角色，其中包括通常不在 API 閘道範圍內的 Web 應用程式。 當您將 eShopOnContainers 部署到 Kubernetes 時，它只會透過「輸入」公開一些服務或端點，基本上包括 URL 上的下列後置詞清單：

- `/` 代表用戶端 SPA Web 應用程式
- `/webmvc` 代表用戶端 MVC Web 應用程式
- `/webstatus` 代表顯示狀態/健康狀態檢查的用戶端 Web 應用程式
- `/webshoppingapigw` 代表 Web BFF 和購物商務程序
- `/webmarketingapigw` 代表 Web BFF 和行銷商務程序
- `/mobileshoppingapigw` 代表行動 BFF 和購物商務程序
- `/mobilemarketingapigw` 代表行動 BFF 和行銷商務程序

部署至 Kubernetes 時，每個 Ocelot API 閘道都會針對每個執行 API 閘道的_pod_使用不同的 "設定. json" 檔案。 這些 "config.xml" 檔案是藉由掛接（原本是使用 deploy 腳本）來提供，並根據名為 ' ocelot ' 的 Kubernetes _config 對應_建立磁片區。 每個容器會將其相關的設定檔掛接到名為 `/app/configuration`的容器檔案夾中。

在 eShopOnContainers 的原始程式碼檔案中，可以在 `k8s/ocelot/` 資料夾內找到原始的 "configuration. json" 檔案。 每個 BFF/APIGateway 都有一個檔案。

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a>Ocelot API 閘道中的其他跨領域功能

使用 Ocelot API 閘道時，還有其他重要的功能可供探索及使用，下列連結將進行說明。

- **在整合 Ocelot 與 Consul 或 Eureka 的用戶端進行服務探索** \
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- **API 閘道層的快取** \
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- **API 閘道層的記錄** \
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- **API 閘道層的服務品質 (重試和斷路器)**  \
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- **速率限制** \
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> [上一頁](background-tasks-with-ihostedservice.md)
> [下一頁](../microservice-ddd-cqrs-patterns/index.md)
