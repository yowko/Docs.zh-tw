---
title: "測試 ASP.NET Core services 和 web 應用程式"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |測試 ASP.NET Core services 和 web 應用程式"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f756a679befee676db2bf6d402fd7e34b1621b9d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>測試 ASP.NET Core services 和 web 應用程式

任何 ASP.NET Core API 服務和 ASP.NET MVC Web 應用程式的中央部分的控制站。 因此，您應該有的信心它們的行為如預期般應用程式。 自動化的測試可以提供您進行此部署，並在到達生產環境之前，可以偵測錯誤。

您需要測試控制器的運作方式根據有效或無效的輸入，測試控制器回應根據它所執行的商務作業的結果。 不過，您應該有這些類型的測試程式 microservices:

-   單元測試。 這樣可確保應用程式的個別元件會在如預期般運作。 判斷提示測試元件 API。

-   整合測試。 這樣可確保元件互動工作如預期般對外部的成品，如資料庫。 API 元件、 UI 或資料庫 I/O 之類的動作記錄等產生的副作用，就可以測試判斷提示。

-   功能測試每個微服務。 這樣可確保應用程式的運作，如預期般從使用者的觀點來看。

-   測試服務。 這樣可確保端對端服務的使用案例，包括在相同的時間，測試多個服務都會進行測試。 這種測試方法，您需要先準備環境。 在此情況下，這表示正在啟動服務 （例如，使用 docker-撰寫組成）。

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>實作 ASP.NET Core Web 應用程式開發介面的單元測試

單元測試包括從其基礎結構和相依性隔離測試應用程式的一部分。 當您的單元測試控制器邏輯，以單一動作的內容，或測試方法時，不是行為架構本身或其相依性。 單元測試不會偵測問題元件之間的互動中 — 也就是整合測試的目的。

為您的單元測試控制器動作，請確定您只著重於其行為。 控制器單元測試可避免之類的篩選條件、 路由或模型繫結。 其焦點在於測試只是一件事，因為單元測試通常是容易撰寫且快速地執行。 編寫完善的組的單元測試可以經常執行，不多的負荷。

單元測試會實作根據測試架構，例如 xUnit.net、 MSTest、 Moq 或使用 NUnit。 EShopOnContainers 範例應用程式中，我們使用 XUnit。

當您為此 Web API 控制器會撰寫單元測試時，您具現化控制器類別直接在 C 中使用新的關鍵字\#，以便盡快執行測試。 下列範例示範如何執行這項操作，當使用[XUnit](https://xunit.github.io/)做測試架構。

```csharp
[Fact]
public void Add_new_Order_raises_new_event()
{
    // Arrange
    var street = " FakeStreet ";
    var city = "FakeCity";
    // Other variables omitted for brevity ...
    // Act
    var fakeOrder = new Order(new Address(street, city, state, country, zipcode),
        cardTypeId, cardNumber,
        cardSecurityNumber, cardHolderName,
        cardExpiration);
    // Assert
    Assert.Equal(fakeOrder.DomainEvents.Count, expectedResult);
}
```

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>實作整合和每個微服務的功能測試

如前所述，整合測試和功能測試有不同用途和目標。 不過，您同時實作測試 ASP.NET Core 控制站時的方式是類似，讓我們專注於整合測試這一節。

整合測試，可確保應用程式的元件正確運作時組合。 ASP.NET Core 支援整合測試使用單元測試架構和內建測試 web 主機，可以用來處理要求網路額外負荷。

與不同的單元測試，是整合測試通常牽涉到的應用程式基礎結構考量，例如資料庫、 檔案系統、 網路資源或 web 要求和回應。 單元測試使用 fakes 或模擬物件來取代這些考量。 但是，整合測試的目的是要確認系統運作正常搭配這些系統，因此為整合測試，您不要使用 fakes 或模擬物件。 相反地，您可以包含基礎結構，例如資料庫存取或服務引動過程與其他服務。

整合測試會執行較大的程式碼區段比單元測試，因為整合測試會依賴基礎結構項目，它們通常是依據重要順序低於單元測試。 因此，最好限制多少整合測試，您撰寫和執行。

ASP.NET Core 包括內建測試 web 主機可以用來處理 HTTP 要求不含網路額外負荷，這表示，您可以執行這些測試速度時使用真實的 web 主機。 測試 web 主機有 NuGet 元件為 Microsoft.AspNetCore.TestHost。 它可以加入至整合測試專案，並用於主機 ASP.NET Core 應用程式。

您可以看到下列程式碼中，當您建立整合測試的 ASP.NET Core 控制站，您具現化的測試主機控制站。 這相當於 HTTP 要求，但執行速度較快。

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

-   **Steve Smith。測試控制器**(ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)

-   **Steve Smith。整合測試**(ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/testing/integration-testing*](https://docs.microsoft.com/aspnet/core/testing/integration-testing)

-   **單元測試中使用 dotnet 測試.NET Core**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)

-   **xUnit.net**。 官方網站。
    [*https://xunit.github.io/*](https://xunit.github.io/)

-   **單元測試基本概念。** 
     [ *https://msdn.microsoft.com/en-us/library/hh694602.aspx*](https://msdn.microsoft.com/en-us/library/hh694602.aspx)

-   **Moq**。 GitHub 儲存機制。
    [*https://github.com/moq/moq*](https://github.com/moq/moq)

-   **NUnit**。 官方網站。
    [*https://www.nunit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a>實作多重容器應用程式上的服務測試 

如前文所述，當您測試多個容器應用程式時，所有 microservices 都需要 Docker 主機或容器叢集內執行。 端對端服務的測試包含多個作業牽涉到數個 microservices 需要您部署和啟動 Docker 主機中的整個應用程式執行 docker-撰寫向上 （或如果您使用 orchestrator 比較機制）。 一旦整個應用程式及其所有服務正常執行，您可以執行端對端整合和功能測試。

有幾個方法，您可以使用。 您用來部署應用程式 （或類似的項目，例如 docker compose.ci.build.yml） docker compose.yml 檔案中，您也可以在方案層級展開進入點，以使用[dotnet 測試](https://docs.microsoft.com/dotnet/core/tools/dotnet-test)。 您也可以使用另一個會在您的目標的映像中執行測試的撰寫檔案。 使用另一個編輯檔案的整合測試，其中包含您 microservices 和容器上的資料庫，您可以確保，相關的資料永遠重設為其原始狀態再執行測試。

撰寫應用程式啟動且正在執行時，您可以要善用中斷點和例外狀況，如果您正在 Visual Studio。 或者，您可以在 Visual Studio Team Services 或其他支援 Docker 容器的 CI/CD 系統 CI 管線中，自動執行整合測試。

>[!div class="step-by-step"]
[上一個](訂閱-events.md) [下一步] (.../microservice-ddd-cqrs-patterns/index.md)
