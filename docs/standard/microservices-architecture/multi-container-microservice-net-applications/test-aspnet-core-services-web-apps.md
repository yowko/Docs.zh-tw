---
title: 測試 ASP.NET Core 服務和 Web 應用程式
description: .NET 微服務：容器化 .NET 應用程式的架構 | 探索在容器中用於測試 ASP.NET Core 服務和 Web 應用程式的架構。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 0f4b9a8461b4d14cd5b468a50af1783a340392e2
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362154"
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>測試 ASP.NET Core 服務和 Web 應用程式

控制器是任何 ASP.NET Core API 和 ASP.NET MVC Web 應用程式的核心部分。 因此，您應該確信其行為符合應用程式的預期。 自動化的測試可建立您這方面的信心，並可在錯誤到達生產環境之前就偵測到錯誤。

您需要測試控制器根據有效或無效輸入的運作方式，以及測試根據所執行商務作業結果的控制器回應。 不過，您的微服務應該有這些類型的測試：

-   單元測試。 這些可確保應用程式的個別元件會如預期般運作。 判斷提示測試元件 API。

-   整合測試。 這些可確保針對外部成品 (如資料庫) 的元件互動會如預期般運作。 判斷提示可以測試元件 API、UI 或資料庫 I/O、記錄之類的動作副作用。

-   每個微服務的功能測試。 這些可確保應用程式從使用者的觀點來看如預期般運作。

-   服務測試。 這些可確保會測試端對端的服務使用案例，包括在相同的時間測試多個服務。 針對這種測試，您需要先準備環境。 在此情況下，這表示啟動服務 (例如，使用 docker-compose up)。

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>實作 ASP.NET Core Web API 的單元測試

單元測試包括將應用程式的一部分與其基礎結構和相依性隔離測試。 對控制器邏輯進行單元測試時，只會測試單一動作或方法的內容，而不會測試其相依性或架構本身的行為。 單元測試不會偵測元件之間的互動問題，這需要使用整合測試。

當您對控制器動作進行單元測試時，請務必只著重於其行為。 控制器單元測試會避免像是篩選器、路由，或模型繫結 (將要求資料對應到 ViewModel 或 DTO) 等項目。 由於測試的焦點只有一個，因此單元測試通常很容易撰寫，而且執行速度很快。 一組編寫完善的單元測試可以經常執行，而不會造成太多額外負荷。

單元測試是根據測試架構而實作，例如 xUnit.net、MSTest、Moq 或使用 NUnit。 針對 eShopOnContainers 範例應用程式，我們使用 xUnit。

當您為 Web API 控制器撰寫單元測試時，您會直接使用 C\# 中的新關鍵字具現化控制器類別，以便盡快執行測試。 下列範例示範在使用 [xUnit](https://xunit.github.io/) 作為測試架構時如何執行這項操作。

```csharp
[Fact]
public async Task Get_order_detail_success()
{
    //Arrange
    var fakeOrderId = "12";
    var fakeOrder = GetFakeOrder();
 
    //...

    //Act
    var orderController = new OrderController(
        _orderServiceMock.Object, 
        _basketServiceMock.Object, 
        _identityParserMock.Object);

    orderController.ControllerContext.HttpContext = _contextMock.Object;
    var actionResult = await orderController.Detail(fakeOrderId);
 
    //Assert
    var viewResult = Assert.IsType<ViewResult>(actionResult);
    Assert.IsAssignableFrom<Order>(viewResult.ViewData.Model);
}
```

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>為每個微服務實作整合和功能測試

如前所述，整合測試和功能測試有不同用途和目標。 不過，測試 ASP.NET Core 控制器時兩者的實作方式很類似，因此在這一節讓我們專注於整合測試。

整合測試可確保應用程式的元件在組合時可正確運作。 ASP.NET Core 支援使用單元測試架構和內建測試 Web 主機來進行整合測試，此 Web 主機可以用來處理要求而不會有網路額外負荷。

不像單元測試，整合測試經常牽涉到應用程式基礎結構考量，例如資料庫、檔案系統、網路資源或 Web 要求和回應。 單元測試使用虛假或模擬物件來取代這些考量。 但是，整合測試的目的是要確認系統搭配這些系統時如預期般運作，因此進行整合測試時，請勿使用虛假或模擬物件。 相反地，您要包含基礎結構，例如資料庫存取或從其他服務進行的服務引動過程。

因為整合測試會執行比單元測試大的程式碼區段，且整合測試會依賴基礎結構項目，所以它們的速度通常和單元測試相比，會呈數量級地變慢。 因此，最好限制您撰寫和執行多少整合測試。

ASP.NET Core 包括內建測試 Web 主機，它可以用來處理 HTTP 要求而不會有網路額外負荷，這表示，您執行這些測試的速度可以比使用真實 Web 主機時更快。 測試 Web 主機 (TestServer) 可透過 Microsoft.AspNetCore.TestHost NuGet 元件取得。 它可以新增至整合測試專案，並用於裝載 ASP.NET Core 應用程式。

您可以在下列程式碼中看到，當您建立 ASP.NET Core 控制器的整合測試時，您會透過測試主機將控制器具現化。 這相當於 HTTP 要求，但執行速度較快。

```csharp
public class PrimeWebDefaultRequestShould
{
    private readonly TestServer _server;
    private readonly HttpClient _client;

    public PrimeWebDefaultRequestShould()
    {
        // Arrange
        _server = new TestServer(new WebHostBuilder()
           .UseStartup<Startup>());
           _client = _server.CreateClient();
    }

    [Fact]
    public async Task ReturnHelloWorld()
    {
        // Act
        var response = await _client.GetAsync("/");
        response.EnsureSuccessStatusCode();
        var responseString = await response.Content.ReadAsStringAsync();
        // Assert
        Assert.Equal("Hello World!", responseString);
    }
}
```

#### <a name="additional-resources"></a>其他資源

-   **Steve Smith.測試控制器** (ASP.NET Core) <br/>
    [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)

-   **Steve Smith.整合測試** (ASP.NET Core) <br/>
    [*https://docs.microsoft.com/aspnet/core/test/integration-tests*](https://docs.microsoft.com/aspnet/core/test/integration-tests)

-   **使用 dotnet test 的 .NET Core 單元測試** <br/>
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](~/docs/core/testing/unit-testing-with-dotnet-test.md)

-   **xUnit.net**. 官方網站。 <br/>
    [*https://xunit.github.io/*](https://xunit.github.io/)

-   **單元測試基本概念。** <br/>
    [*https://msdn.microsoft.com/library/hh694602.aspx*](https://msdn.microsoft.com/library/hh694602.aspx)

-   **Moq**. GitHub 存放庫。 <br/>
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

-   **NUnit**. 官方網站。 <br/>
    [*https://www.nunit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a>實作多重容器應用程式上的服務測試 

如前文所述，當您測試多重容器應用程式時，所有微服務都需要在 Docker 主機或容器叢集內執行。 端對端服務測試包含牽涉到數個微服務的多個作業，需要您在 Docker 主機中執行 docker-compose up (如果您使用協調器則是類似的機制) 部署和啟動整個應用程式。 一旦整個應用程式及其所有服務執行之後，您便可以執行端對端整合和功能測試。

有一些方法可供您使用。 在您用來部署應用程式的 docker-compose.yml 檔案中，您可以在解決方案層級展開進入點，以使用 [dotnet test](https://docs.microsoft.com/dotnet/articles/core/tools/dotnet-test)。 您也可以使用另一個 compose 檔案，在您目標的映像中執行測試。 藉由針對包含您容器上之微服務和資料庫的整合測試使用另一個 compose 檔案，您可以確保相關的資料永遠重設為其原始狀態，然後才執行測試。

compose 應用程式啟動且執行之後，如果您正在執行 Visual Studio，則可以利用中斷點和例外狀況。 或者，您可以在 Azure DevOps Services 中的 CI 管線，或其他支援 Docker 容器的任何 CI/CD 系統中，自動執行整合測試。

## <a name="testing-in-eshoponcontainers"></a>在 eShopOnContainers 中進行測試

最近已重組參考應用程式 (eShopOnContainers) 測試，現在有四個類別：

1.  **單元**測試，只是單純的舊版一般單元測試，包含在 **{MicroserviceName}.UnitTests** 專案中

2.  **微服務功能/整合測試**，其中測試案例涉及每個微服務的基礎結構，但會與其他項目隔離，且包含在 **{MicroserviceName}.FunctionalTests** 專案中。

3.  **應用程式功能/整合測試**，著重在微服務整合，其中測試案例會使用數個微服務。 這些測試位於 **Application.FunctionalTests** 專案中。

4.  **負載測試**，著重在每個微服務的回應時間。 這些測試位於 **LoadTest** 專案中，且需要 Visual Studio 2017 Enterprise Edition。

每個微服務的單元測試和整合測試都包含在每個微服務和應用程式中測試資料夾中。負載測試則包含在解決方案資料夾中的測試資料夾中，如圖 6-25 所示。

![eShopOnContainers 中的測試結構：每個服務都有一個 "test" 資料夾，包含單元和功能測試。 應用程式全範圍的功能測試和負載測試，則位於解決方案 "test" 資料夾下。](./media/image42.png)

**圖 6-25**。 eShopOnContainers 中的測試資料夾結構

微服務和應用程式功能/整合測試會使用一般測試執行器從 Visual Studio 執行，但您必須先透過一組包含在解決方案測試資料夾中的 docker-compose 檔案，來啟動必要的基礎結構服務：

**docker-compose-test.yml**

```yml
version: '3.4'

services:
  redis.data:
    image: redis:alpine
  rabbitmq:
    image: rabbitmq:3-management-alpine
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
  nosql.data:
    image: mongo
```

**docker-compose-test.override.yml**

```yml
version: '3.4'

services:
  redis.data:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672" 
  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosql.data:
    ports:
      - "27017:27017"
```

因此，若要執行功能/整合測試，您必須先從解決方案測試資料夾執行此命令：

``` console
docker-compose -f docker-compose-test.yml -f docker-compose-test.override.yml up
```

如您所見，這些 docker-compose 檔案只會啟動 Redis、RabitMQ、SQLServer 和 MongoDB 微服務。

### <a name="additionl-resources"></a>其他資源

-   GitHub 上 eShopOnContainers 存放庫上的**測試讀我檔案** <br/>
    [*https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test*](https://github.com/dotnet-architecture/eShopOnContainers/tree/dev/test)

-   GitHub 上 eShopOnContainers 存放庫上的**負載測試讀我檔案** <br/>
    [*https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/*](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/test/ServicesTests/LoadTest/)

>[!div class="step-by-step"]
>[上一頁](subscribe-events.md)
>[下一頁](background-tasks-with-ihostedservice.md)