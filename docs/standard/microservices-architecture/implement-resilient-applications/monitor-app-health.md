---
title: 健康情況監視
description: 瀏覽實作健康情況監視的其中一種方式。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 666b55608ca4e5d18448e1a0b4a1735f3e856474
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362479"
---
# <a name="health-monitoring"></a>健康情況監視

健康情況監視功能可提供近即時的容器和微服務狀態資訊。 健康情況監視功能對微服務運作的各方面來說都非常重要，尤其當協調器要分階段執行部分應用程式升級時更是如此，如稍後所說明。

微服務應用程式通常使用活動訊號或健康情況檢查，使其效能監視器、排程器及協調器可以追蹤許多服務。 如果服務無法視需求或依排程傳送「運作正常」的訊號，當您部署更新時應用程式可能會面臨風險，或可能會太晚偵測到失敗，讓故障一發不可收拾，進而導致全面中斷。

在一般模型中，服務會傳送其狀態報告，而該彙總資訊可提供應用程式健康情況的整體檢視。 如果您是使用協調器，則可以提供健康情況資訊給協調器的叢集，使叢集可以據以採取行動。 如果您為應用程式投入自訂的高品質健康情況報告，即可更輕鬆地偵測執行中的應用程式並修正問題。

## <a name="implement-health-checks-in-aspnet-core-services"></a>在 ASP.NET Core 服務中實作健康情況檢查

開發 ASP.NET Core 微服務或 Web 應用程式時，您可以使用 ASP.NET 小組所提供、名為 *Health Checks* 的實驗性頻外程式庫 (不是 ASP.NETCore 中正式提供的，且現在已被取代)。 您可以在這個 [dotnet 架構 GitHub 存放庫](https://github.com/dotnet-architecture/HealthChecks)中找到它。 不過，正式版本的*健康情況檢查*[將會在 ASP.NET Core 2.2 中發行](https://github.com/aspnet/Announcements/issues/307) (應該會在 2018 年底正式發行)。

這個程式庫不僅簡單易用，還提供功能讓您驗證任何應用程式所需的特定外部資源 (例如 SQL Server 資料庫或遠端 API) 是否正常運作。 使用這個程式庫時，您也可以自行決定何種情況下表示資源狀況良好，如我們稍後所說明。

若要使用這個程式庫，您必須先使用微服務中的程式庫。 接著，您需要可查詢健康情況報告的前端應用程式。 這裡的前端應用程式可能是自訂的報告應用程式，或能根據健康情況採取動作的協調器本身。

### <a name="use-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a>在您的後端 ASP.NET 微服務中使用 HealthChecks 程式庫

您可以看看 eShopOnContainers 範例應用程式如何使用 HealthChecks 程式庫。 首先，您需要為每個微服務定義健康情況良好的構成項目。 在範例應用程式中，如果可以透過 HTTP 存取微服務 API 且其相關 SQL Server 資料庫亦可供存取，即表示微服務健康情況良好。

未來，您將能夠以 NuGet 套件形式安裝 HealthChecks 程式庫。 但在本文撰寫當下，您仍必須下載並編譯程式碼以作為方案的一部分。 複製位於 <https://github.com/dotnet-architecture/HealthChecks> 的程式碼並將下列資料夾複製到您的解決方案：

- src/common
- src/Microsoft.AspNetCore.HealthChecks
- src/Microsoft.Extensions.HealthChecks
- src/Microsoft.Extensions.HealthChecks.SqlServer

您也可以使用適用於 Azure 的額外檢查 (Microsoft.Extensions.HealthChecks.AzureStorage)，但因為這一版的 eShopOnContainers 對 Azure 沒有任何相依性，所以您並不需要。 您也不需要 ASP.NET 健康情況檢查，因為 eShopOnContainers 是以 ASP.NET Core 為基礎。

圖 8-7 顯示 Visual Studio 中的 HealthChecks 程式庫，它已備妥可供任何微服務作為建置組塊。

![顯示三個專案的 HealthChecks 資料夾解決方案總管檢視。](./media/image6.png)

**圖 8-7**。 Visual Studio 方案中的 ASP.NET Core HealthChecks 程式庫原始程式碼

如前所述，您在每個微服務專案中的首要任務就是新增三個 HealthChecks 程式庫的參考。 接著，您即可新增要在該微服務中執行的健康情況檢查動作。 這些動作基本上是相依於其他微服務 (HttpUrlCheck) 或資料庫 (針對 SQL Server 資料庫，目前為 SqlCheck\*)。 接著，在每個 ASP.NET 微服務或 ASP.NET Web 應用程式的啟動類別中新增動作。

若要為每個服務或 Web 應用程式進行設定，請使用一個 AddHealthCheck 方法來新增其所有的 HTTP 或資料庫相依性。 例如，eShopOnContainers 的 MVC Web 應用程式仰賴許多服務，因此會新增數種 AddCheck 方法至健康情況檢查。

例如，您可以在下列 (已簡化) 程式碼中了解目錄微服務如何新增其對 SQL Server 資料庫的相依性。

```csharp
// Startup.cs from Catalog.api microservice
//
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Add framework services
        services.AddHealthChecks(checks =>
        {
            checks.AddSqlCheck("CatalogDb", Configuration["ConnectionString"]);
        });
        // Other services
    }
}
```

不過，eShopOnContainers 的 MVC Web 應用程式對其餘微服務具有多個相依性。 因此，它會為每個微服務呼叫一個 AddUrlCheck 方法，如下列 (已簡化) 範例所示：

```csharp
// Startup.cs from the MVC web app
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
        services.Configure<AppSettings>(Configuration);
        services.AddHealthChecks(checks =>
        {
            checks.AddUrlCheck(Configuration["CatalogUrl"]);
            checks.AddUrlCheck(Configuration["OrderingUrl"]);
            checks.AddUrlCheck(Configuration["BasketUrl"]);
            checks.AddUrlCheck(Configuration["IdentityUrl"]);
        });
    }
}
```

如此一來，微服務會在其所有檢查都是狀況良好時才會提供「狀況良好」狀態。

如果微服務對服務或 SQL Server 沒有相依性，就只需新增 Healthy("Ok") 檢查。 下列程式碼取自 eShopOnContainers `basket.api` 微服務。 (購物籃微服務會使用 Redis 快取，但程式庫並未包含 Redis 健康情況檢查提供者)。

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

若要讓服務或 Web 應用程式公開健康情況檢查端點，就必須啟用 `UseHealthChecks([*url_for_health_checks*])` 擴充方法。 如下列已簡化程式碼所示，這個方法用於 ASP.NET Core 服務或 Web 應用程式 `Program` 類別之主要方法的 `WebHostBuilder` 層級中，並緊接在 <xref:Microsoft.AspNetCore.WebHost.CreateDefaultBuilder> 之後：

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = WebHost.CreateDefaultBuilder(args)
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseStartup<Startup>()
                .Build();

            host.Run();
        }
    }
}
```

程序會以此方式運作：每個微服務都會公開端點 /hc。 HealthChecks 程式庫 ASP.NET Core 中介軟體會建立該端點。 叫用該端點時，它會執行啟動類別之 AddHealthChecks 方法中所設定的所有健康情況檢查。

UseHealthChecks 方法必須使用連接埠或路徑。 該連接埠或路徑是用來檢查服務健康情況的端點。 例如，目錄微服務會使用路徑 /hc。

### <a name="cache-health-check-responses"></a>快取健康情況檢查回應

如果您不想造成服務出現拒絕服務 (DoS) 的問題，或不希望太頻繁的資源檢查會影響服務效能，您可以快取傳回項目，並設定每個健康情況檢查的快取期間。

內部預設的快取期間為 5 分鐘，但您可以變更每個健康情況檢查的快取期間，如下列程式碼所示：

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a>查詢微服務以報告其健康情況

完成此文章中說明的健康情況檢查設定並在 Docker 中開始執行微服務之後，您就可以直接從瀏覽器檢查微服務的健康情況。

您必須在 Docker 主機中發佈容器連接埠，以便透過外部 Docker 主機 IP 或 `localhost` 存取容器，如圖 8-8 所示。

![健康情況檢查所傳回 JSON 回應的瀏覽器檢視](./media/image7.png)

**圖 8-8**。 從瀏覽器檢查單一服務的健康情況

在這個測試中，您可以看到 catalog.api 微服務 (執行於連接埠 5101 上) 健康情況良好，並以 JSON 形式傳回 HTTP 狀態 200 和狀態資訊。 這表示，服務也已內部檢查其 SQL Server 資料庫相依性的健康情況，而該健康情況檢查已自行回報健康情況良好。

## <a name="use-watchdogs"></a>使用監視程式

監視程式是一種可以跨服務監看健康情況和負載的個別服務，它會查詢稍早說明過的 `HealthChecks` 程式庫以回報微服務的健康情況。 這可協助防止從單一服務角度無法偵測出的錯誤。 監視程式也是裝載程式碼的好地方，以針對已知情況執行修復動作，而不需使用者互動。

eShopOnContainers 範例包含顯示範例健康情況檢查報告的網頁，如圖 8-9 所示。 這是一種最簡單的監視程式，因為它只會顯示 eShopOnContainers 中的微服務和 Web 應用程式狀態。 通常監視程式也會在偵測到健康情況不良時採取動作。

![WebStatus 應用程式的瀏覽器檢視，顯示來自 eShopOnContainers 的五個微服務的健康情況狀態](./media/image8.png)

**圖 8-9**。 eShopOnContainers 中的範例健康情況檢查報告

簡單來說，ASP.NET Core HealthChecks 程式庫中的 ASP.NET 中介軟體會針對每個微服務提供單一的健康情況檢查端點。 其會執行端點中定義的所有健康情況檢查，並根據這所有檢查傳回整體健康情況。

HealthChecks 程式庫可透過未來外部資源的新健康情況檢查而進行擴充 。 例如，我們預期未來程式庫必須針對 Redis 快取和其他資料庫進行健康情況檢查。 程式庫可按照多個服務或應用程式相依性來提供健康情況報告，以便您依據這些健康情況檢查採取動作。

## <a name="health-checks-when-using-orchestrators"></a>使用協調器時的健康情況檢查

為了監視您的微服務可用性，Kubernetes 和 Service Fabric 這類協調器會傳送測試微服務的要求，以定期執行健康情況檢查。 當協調器判斷某個服務/容器健康情況不良時，它會停止將要求路由至該執行個體。 它通常也會建立該容器的新執行個體。

例如，大部分協調器可以使用健康情況檢查來管理零停機部署。 只有當服務/容器的狀態變更為健康情況良好時，協調器才會開始將流量路由到服務/容器的執行個體。

當協調器執行應用程式升級時，健康情況監視尤為重要。 某些協調器 (例如 Azure Service Fabric) 會分階段升級服務 — 例如，它們可能會為每個應用程式升級進行五分之一的叢集介面更新。 在相同時間升級的一組節點即為一個「升級網域」。 每個升級網域都已升級並可供使用者使用之後，該升級網域還必須通過健康情況檢查，部署才會移到下一個升級網域。

服務健康情況的另一個重點是服務的報告計量。 這是 Service Fabric 等協調器的一個健康情況模型進階功能。 使用協調器時，計量非常重要，因為其可用來平衡資源使用狀況。 計量也是系統健康情況的指標。 例如，您的應用程式可能有許多微服務，而每個執行個體都會報告每秒要求數 (RPS) 計量。 如果某一個服務比其他服務使用更多資源 (記憶體、處理器等)，協調器可以在叢集中移動服務執行個體，以嘗試維護平均的資源使用率。

請注意，Azure Service Fabric 隨附的[健康情況監視模型](/azure/service-fabric/service-fabric-health-introduction)比簡單的健康情況檢查更進階。

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>進階監視：視覺效果、分析和警示

監視的最後一個部分是視覺化事件資料流、報告服務效能，並在偵測到問題時發出警示。 您可以使用不同解決方案來進行這方面的監視。

您可以使用簡單的自訂應用程式以顯示服務狀態，例如我們在說明 [ASP.NET Core HealthChecks](https://github.com/dotnet-architecture/HealthChecks) 時介紹過的自訂頁面。 或者，您可以使用 Azure Application Insights 這類更進階的工具，以依據事件資料流來發出警示。

最後，如果您已儲存所有事件資料流，即可使用 Microsoft Power BI 或 Kibana 或 Splunk 等其他解決方案來視覺化資料。

## <a name="additional-resources"></a>其他資源

- **ASP.NET Core HealthChecks** (實驗性版本)\
  [*https://github.com/dotnet-architecture/HealthChecks/*](https://github.com/dotnet-architecture/HealthChecks/)

- **Service Fabric 健康情況監視簡介**\
  [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](/azure/service-fabric/service-fabric-health-introduction)

- **Azure Application Insights**\
  [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

- **Microsoft Operations Management Suite**\
  [*https://www.microsoft.com/cloud-platform/operations-management-suite*](https://www.microsoft.com/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
>[上一頁](implement-circuit-breaker-pattern.md)
>[下一頁](../secure-net-microservices-web-applications/index.md)