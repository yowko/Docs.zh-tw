---
title: "健全狀況監視"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |健全狀況監視"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: cbbad72f06bcaa882bc50083d9103b0872f51754
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="health-monitoring"></a>健全狀況監視

健全狀況監視，可允許接近即時的容器和 microservices 狀態的資訊。 健全狀況監視，請務必使用多個層面的作業系統 microservices 和時尤其重要 orchestrators 部分應用程式升級中執行階段，如稍後所說明。

Microservices 為基礎的應用程式通常使用的活動訊號或健全狀況檢查，讓追蹤的許多的服務其效能監視器、 排程器及 orchestrators。 如果服務無法傳送某種 「 我運作 」 的訊號，視需要或依排程，您的應用程式可能會面臨風險，當您部署更新，或它可能只是偵測失敗太晚，而且無法停止收下的全面中斷的階層式失敗。

在一般模型中，服務傳送的報告及其狀態，而該資訊彙總提供您的應用程式的健全狀況狀態的整體檢視。 如果您使用 orchestrator，您可以提供健全狀況資訊發給 orchestrator 的叢集，使叢集可以據此採取行動。 如果您進行投資高品質的健康情況報告，自訂您的應用程式，您可以偵測並執行應用程式中更輕鬆地修正問題。

## <a name="implementing-health-checks-in-aspnet-core-services"></a>ASP.NET 核心服務中實作健全狀況檢查

在開發 ASP.NET Core 微服務或 web 應用程式時，您可以使用 HealthChecks 中名為 ASP.NET 小組的程式庫。 （可能 2017 年最早的版本是可在 GitHub 上取得）。

此文件庫不僅簡單易用，並提供功能，可讓您驗證任何特定的外部資源所需的應用程式 （例如 SQL Server 資料庫或遠端的應用程式開發介面中） 正常運作。 當您使用此程式庫時，您也可以決定其代表資源處於狀況良好，因為我們稍後說明。

若要使用此程式庫，您必須先使用您 microservices 中的程式庫。 其次，您需要查詢的前端應用程式的健康情況報告。 前端應用程式可能是自訂的報告應用程式，或可能的協調者本身可以據以採取動作的健全狀況狀態。

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a>使用在您的後端 ASP.NET microservices HealthChecks 程式庫

您可以看到 eShopOnContainers 範例應用程式中使用 HealthChecks 程式庫的方式。 若要開始，您需要定義構成每個微服務狀況良好狀態的項目。 範例應用程式、 microservices 是狀況良好，如果微服務應用程式開發介面透過 HTTP 和其相關的 SQL Server 資料庫是否也可存取。

未來，您將能夠以 NuGet 套件安裝 HealthChecks 程式庫。 但是在撰寫本文時，您必須下載並編譯程式碼做為方案的一部分。 複製位於 https://github.com/aspnet/HealthChecks 程式碼，並將下列資料夾複製到您的方案。

  - src/一般
  - src/Microsoft.AspNetCore.HealthChecks
  - src/Microsoft.Extensions.HealthChecks
  - src/Microsoft.Extensions.HealthChecks.SqlServer

您也可以使用額外的檢查像 azure (Microsoft.Extensions.HealthChecks.AzureStorage)，但因為這一版的 eShopOnContainers 在 Azure 上沒有任何相依性，您不需要它。 因為 eShopOnContainers 以 ASP.NET Core 上不需要 ASP.NET 健康狀態檢查。

圖 10-6 會顯示在 Visual Studio 中，準備好可作為建置組塊供任何 microservices HealthChecks 程式庫。

![](./media/image6.png)

**圖 10-6**。 ASP.NET Core HealthChecks 程式庫原始程式碼的 Visual Studio 方案中

推出之前，若要在每個微服務專案中的第一件事就是加入三個 HealthChecks 文件庫的參考。 之後，您可以新增您想要執行的微服務中的健全狀況檢查動作。 這些動作基本上是在其他 microservices (HttpUrlCheck) 或資料庫上的相依性 (目前 SqlCheck\*的 SQL Server 資料庫)。 您新增的每個 ASP.NET 微服務 」 或 「 ASP.NET web 應用程式啟動類別中的動作。

每個服務或 web 應用程式應該設定為一個 AddHealthCheck 方法將所有資料庫或 HTTP 的相依性。 例如，MVC web 應用程式，從 eShopOnContainers 取決於許多服務，因此會有數種 AddCheck 方法加入至健全狀況檢查。

比方說，下列程式碼中您可以查看目錄微服務在 SQL Server 資料庫上加入相依性的方式。

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

不過，eShopOnContainers 的 MVC web 應用程式有多個相依性上 microservices 的其餘部分。 因此，它會呼叫其中一種 AddUrlCheck 方法的每個微服務，如下列範例所示：

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

因此，微服務不會提供 「 良好 」 狀態，直到其所有的檢查也是狀況良好。

如果微服務並沒有相依性，在服務上，或 SQL Server 上，您只應新增 Healthy("Ok") 核取。 下列程式碼取自 eShopOnContainers basket.api 微服務。 （購物籃微服務使用 Redis 快取，但文件庫尚未包含 Redis 健全狀況檢查提供者）。

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

公開健全狀況檢查端點是服務或 web 應用程式，它有啟用 UseHealthChecks (\[*url\_如\_健全狀況\_檢查*\]) 擴充功能方法。 這個方法會在 WebHostBuilder 層級中的 ASP.NET Core 服務或 web 應用程式，如下列程式碼所示的 UseKestrel 之後 Program 類別的主要方法。

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = new WebHostBuilder()
                .UseKestrel()
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseIISIntegration()
                .UseStartup<Startup>()
                .Build();
            host.Run();
        }
    }
}
```

處理程序的運作方式如下： 每個微服務會公開端點 /hc。 HealthChecks 程式庫 ASP.NET Core 中介軟體會建立該端點。 叫用該端點時，它會執行 AddHealthChecks 中的方法啟動類別中所設定的所有健康情況檢查。

UseHealthChecks 方法預期的連接埠或路徑。 該連接埠或路徑是用來檢查服務的健全狀況狀態的端點。 例如，類別目錄的微服務會使用路徑 /hc。

### <a name="caching-health-check-responses"></a>快取的健康情況檢查回應

因為您不希望您的服務，會造成阻絕服務 (DoS) 或只是不想要藉由檢查資源會影響服務效能頻率太高，您可以快取傳回，設定每個健全狀況檢查的快取持續時間。

根據預設，快取持續時間在內部設定為 5 分鐘，但您可以變更該快取持續時間，在每個健全狀況檢查，如下列程式碼所示：

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a>查詢您 microservices 要報告其健全狀況狀態

當您完成設定健康情況檢查，如下所述，在 Docker 中開始執行的微服務之後時，您直接可以檢查，從瀏覽器是否狀況良好。 （這需要，您要發行超出 Docker 主機時，容器連接埠，以便透過 localhost 或外部的 Docker 主機 IP，您可以存取容器。）圖 10-7 會顯示在瀏覽器和對應的回應中的要求。

![](./media/image7.png)

**圖 10-7**。 正在檢查從瀏覽器的單一服務的健全狀況狀態

在測試，您可以看到 （連接埠 5101 上執行） catalog.api 微服務狀況良好，在 JSON 中傳回 HTTP 狀態 200 和狀態資訊。 這也表示，在內部服務也檢查其 SQL Server 資料庫相依性的健全狀況和健全狀況檢查已回報本身為狀況良好。

## <a name="using-watchdogs"></a>使用 watchdogs

監視是不同的服務，可以觀看健全狀況，並藉由查詢早導入的 HealthChecks 程式庫載入跨服務，以及有關 microservices 回報健全狀況。 這可協助防止將不會偵測根據檢視的單一服務的錯誤。 Watchdogs 也都可以執行修復動作的已知的情況，而不需使用者互動的裝載程式碼的好地方。

EShopOnContainers 範例包含會顯示範例健全狀況檢查報表，如圖 10-8 所示的網頁。 這是最簡單的監視，您可以擁有，因為它已顯示 eShopOnContainers microservices 和 web 應用程式的狀態。 通常監視也會採取動作時偵測到的狀況不良狀態。

![](./media/image8.png)

**圖 10-8**。 在 eShopOnContainers 範例健全狀況檢查報告

在 [摘要] ASP.NET Core HealthChecks 程式庫中的 ASP.NET 中介軟體會針對每個微服務提供單一的健全狀況檢查端點。 這將會執行在其中定義的所有健康情況檢查，並傳回根據所有這些檢查的整體健全狀況狀態。

可透過新的健全狀況檢查的未來外部的資源延伸 HealthChecks 程式庫。 例如，我們預期時，在未來的程式庫必須 Redis 快取和其他資料庫的健全狀況檢查。 程式庫可讓報表功能的多個服務或應用程式相依性的健全狀況，您可以接著依據採取動作的健康情況檢查。

## <a name="health-checks-when-using-orchestrators"></a>使用 orchestrators 時的健全狀況檢查

若要監視您 microservices 的可用性，如 Docker Swarm、 Kubernetes，以及 Service Fabric orchestrators 定期藉由傳送要求以測試 microservices 執行健全狀況檢查。 當 orchestrator 決定服務/容器會處於狀況不良，它會停止要求路由傳送到該執行個體。 它通常也會建立該容器的新執行個體。

比方說，大部分 orchestrators 可以管理零停機時間部署使用健康情況檢查。 將服務/容器變更為狀況良好狀態時，才 orchestrator 會開始將流量傳送到服務/容器的執行個體。

當 orchestrator 執行應用程式升級時，健全狀況監視是特別重要。 某些 orchestrators （例如 Azure Service Fabric) 更新服務中的階段 — 比方說，他們可能會更新每個應用程式升級叢集介面的其中一個第五。 在相同的時間升級的節點集指*升級網域*。 每個升級網域已升級，並提供給使用者之後，該升級網域必須通過健全狀況檢查，之後再部署移到下一個升級網域。

服務健全狀況的另一個層面會報告從服務的度量資訊。 這是一項進階的功能的某些 orchestrators，例如服務網狀架構健全狀況模型。 度量資訊是很重要，因為它們用來平衡資源使用狀況，請使用 orchestrator 時。 度量也可以是系統健全狀況的指標。 比方說，您可能有許多 microservices，應用程式，每個執行個體報告每秒的要求 (RP) 度量資訊。 如果一項服務使用比其他服務的更多資源 （記憶體、 處理器等），orchestrator 無法服務執行個體中移動叢集，以嘗試維護甚至資源使用率。

請注意，是否您使用 Azure Service Fabric，它會提供它自己[監視健全狀況模型](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)，也就是更進階比簡單的健康情況檢查。

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>進階監視： 視覺效果、 分析和警示

監視的最後一個部分視覺化報表服務效能，並在偵測到的問題時發出警示的事件資料流。 您可以使用不同的解決方案，這方面的監視。

您可以使用簡單顯示您的服務狀態的自訂應用程式，像是自訂頁面介紹當我們解釋[ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks)。 或者，您可以使用更進階的工具，像是 Azure Application Insights 和 Operations Management Suite 引發事件的資料流為基礎的警示。

最後，如果您已儲存的事件資料流，您可以使用 Microsoft Power BI 或類似 Kibana 或 Splunk 協力廠商解決方案來視覺化資料。

## <a name="additional-resources"></a>其他資源

-   **ASP.NET Core HealthChecks** （最早版本） [ *https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)

-   **服務網狀架構健全狀況監視簡介**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)

-   **Azure 的 Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

-   **Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
[上一個](實作-循環-分隔-pattern.md) [下一步] (.../secure-net-microservices-web-applications/index.md)
