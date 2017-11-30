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
# <a name="testing-aspnet-core-services-and-web-apps"></a><span data-ttu-id="ab61f-104">測試 ASP.NET Core services 和 web 應用程式</span><span class="sxs-lookup"><span data-stu-id="ab61f-104">Testing ASP.NET Core services and web apps</span></span>

<span data-ttu-id="ab61f-105">任何 ASP.NET Core API 服務和 ASP.NET MVC Web 應用程式的中央部分的控制站。</span><span class="sxs-lookup"><span data-stu-id="ab61f-105">Controllers are a central part of any ASP.NET Core API service and ASP.NET MVC Web application.</span></span> <span data-ttu-id="ab61f-106">因此，您應該有的信心它們的行為如預期般應用程式。</span><span class="sxs-lookup"><span data-stu-id="ab61f-106">As such, you should have confidence they behave as intended for your application.</span></span> <span data-ttu-id="ab61f-107">自動化的測試可以提供您進行此部署，並在到達生產環境之前，可以偵測錯誤。</span><span class="sxs-lookup"><span data-stu-id="ab61f-107">Automated tests can provide you with this confidence and can detect errors before they reach production.</span></span>

<span data-ttu-id="ab61f-108">您需要測試控制器的運作方式根據有效或無效的輸入，測試控制器回應根據它所執行的商務作業的結果。</span><span class="sxs-lookup"><span data-stu-id="ab61f-108">You need to test how the controller behaves based on valid or invalid inputs, and test controller responses based on the result of the business operation it performs.</span></span> <span data-ttu-id="ab61f-109">不過，您應該有這些類型的測試程式 microservices:</span><span class="sxs-lookup"><span data-stu-id="ab61f-109">However, you should have these types of tests your microservices:</span></span>

-   <span data-ttu-id="ab61f-110">單元測試。</span><span class="sxs-lookup"><span data-stu-id="ab61f-110">Unit tests.</span></span> <span data-ttu-id="ab61f-111">這樣可確保應用程式的個別元件會在如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="ab61f-111">These ensure that individual components of the application work as expected.</span></span> <span data-ttu-id="ab61f-112">判斷提示測試元件 API。</span><span class="sxs-lookup"><span data-stu-id="ab61f-112">Assertions test the component API.</span></span>

-   <span data-ttu-id="ab61f-113">整合測試。</span><span class="sxs-lookup"><span data-stu-id="ab61f-113">Integration tests.</span></span> <span data-ttu-id="ab61f-114">這樣可確保元件互動工作如預期般對外部的成品，如資料庫。</span><span class="sxs-lookup"><span data-stu-id="ab61f-114">These ensure that component interactions work as expected against external artifacts like databases.</span></span> <span data-ttu-id="ab61f-115">API 元件、 UI 或資料庫 I/O 之類的動作記錄等產生的副作用，就可以測試判斷提示。</span><span class="sxs-lookup"><span data-stu-id="ab61f-115">Assertions can test component API, UI, or the side effects of actions like database I/O, logging, etc.</span></span>

-   <span data-ttu-id="ab61f-116">功能測試每個微服務。</span><span class="sxs-lookup"><span data-stu-id="ab61f-116">Functional tests for each microservice.</span></span> <span data-ttu-id="ab61f-117">這樣可確保應用程式的運作，如預期般從使用者的觀點來看。</span><span class="sxs-lookup"><span data-stu-id="ab61f-117">These ensure that the application works as expected from the user’s perspective.</span></span>

-   <span data-ttu-id="ab61f-118">測試服務。</span><span class="sxs-lookup"><span data-stu-id="ab61f-118">Service tests.</span></span> <span data-ttu-id="ab61f-119">這樣可確保端對端服務的使用案例，包括在相同的時間，測試多個服務都會進行測試。</span><span class="sxs-lookup"><span data-stu-id="ab61f-119">These ensure that end-to-end service use cases, including testing multiple services at the same time, are tested.</span></span> <span data-ttu-id="ab61f-120">這種測試方法，您需要先準備環境。</span><span class="sxs-lookup"><span data-stu-id="ab61f-120">For this type of testing, you need to prepare the environment first.</span></span> <span data-ttu-id="ab61f-121">在此情況下，這表示正在啟動服務 （例如，使用 docker-撰寫組成）。</span><span class="sxs-lookup"><span data-stu-id="ab61f-121">In this case, it means starting the services (for example, by using docker-compose up).</span></span>

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a><span data-ttu-id="ab61f-122">實作 ASP.NET Core Web 應用程式開發介面的單元測試</span><span class="sxs-lookup"><span data-stu-id="ab61f-122">Implementing unit tests for ASP.NET Core Web APIs</span></span>

<span data-ttu-id="ab61f-123">單元測試包括從其基礎結構和相依性隔離測試應用程式的一部分。</span><span class="sxs-lookup"><span data-stu-id="ab61f-123">Unit testing involves testing a part of an application in isolation from its infrastructure and dependencies.</span></span> <span data-ttu-id="ab61f-124">當您的單元測試控制器邏輯，以單一動作的內容，或測試方法時，不是行為架構本身或其相依性。</span><span class="sxs-lookup"><span data-stu-id="ab61f-124">When you unit test controller logic, only the content of a single action or method is tested, not the behavior of its dependencies or of the framework itself.</span></span> <span data-ttu-id="ab61f-125">單元測試不會偵測問題元件之間的互動中 — 也就是整合測試的目的。</span><span class="sxs-lookup"><span data-stu-id="ab61f-125">Unit tests do not detect issues in the interaction between components—that is the purpose of integration testing.</span></span>

<span data-ttu-id="ab61f-126">為您的單元測試控制器動作，請確定您只著重於其行為。</span><span class="sxs-lookup"><span data-stu-id="ab61f-126">As you unit test your controller actions, make sure you focus only on their behavior.</span></span> <span data-ttu-id="ab61f-127">控制器單元測試可避免之類的篩選條件、 路由或模型繫結。</span><span class="sxs-lookup"><span data-stu-id="ab61f-127">A controller unit test avoids things like filters, routing, or model binding.</span></span> <span data-ttu-id="ab61f-128">其焦點在於測試只是一件事，因為單元測試通常是容易撰寫且快速地執行。</span><span class="sxs-lookup"><span data-stu-id="ab61f-128">Because they focus on testing just one thing, unit tests are generally simple to write and quick to run.</span></span> <span data-ttu-id="ab61f-129">編寫完善的組的單元測試可以經常執行，不多的負荷。</span><span class="sxs-lookup"><span data-stu-id="ab61f-129">A well-written set of unit tests can be run frequently without much overhead.</span></span>

<span data-ttu-id="ab61f-130">單元測試會實作根據測試架構，例如 xUnit.net、 MSTest、 Moq 或使用 NUnit。</span><span class="sxs-lookup"><span data-stu-id="ab61f-130">Unit tests are implemented based on test frameworks like xUnit.net, MSTest, Moq, or NUnit.</span></span> <span data-ttu-id="ab61f-131">EShopOnContainers 範例應用程式中，我們使用 XUnit。</span><span class="sxs-lookup"><span data-stu-id="ab61f-131">For the eShopOnContainers sample application, we are using XUnit.</span></span>

<span data-ttu-id="ab61f-132">當您為此 Web API 控制器會撰寫單元測試時，您具現化控制器類別直接在 C 中使用新的關鍵字\#，以便盡快執行測試。</span><span class="sxs-lookup"><span data-stu-id="ab61f-132">When you write a unit test for a Web API controller, you instantiate the controller class directly using the new keyword in C\#, so that the test will run as fast as possible.</span></span> <span data-ttu-id="ab61f-133">下列範例示範如何執行這項操作，當使用[XUnit](https://xunit.github.io/)做測試架構。</span><span class="sxs-lookup"><span data-stu-id="ab61f-133">The following example shows how to do this when using [XUnit](https://xunit.github.io/) as the Test framework.</span></span>

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

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a><span data-ttu-id="ab61f-134">實作整合和每個微服務的功能測試</span><span class="sxs-lookup"><span data-stu-id="ab61f-134">Implementing integration and functional tests for each microservice</span></span>

<span data-ttu-id="ab61f-135">如前所述，整合測試和功能測試有不同用途和目標。</span><span class="sxs-lookup"><span data-stu-id="ab61f-135">As noted, integration tests and functional tests have different purposes and goals.</span></span> <span data-ttu-id="ab61f-136">不過，您同時實作測試 ASP.NET Core 控制站時的方式是類似，讓我們專注於整合測試這一節。</span><span class="sxs-lookup"><span data-stu-id="ab61f-136">However, the way you implement both when testing ASP.NET Core controllers is similar, so in this section we concentrate on integration tests.</span></span>

<span data-ttu-id="ab61f-137">整合測試，可確保應用程式的元件正確運作時組合。</span><span class="sxs-lookup"><span data-stu-id="ab61f-137">Integration testing ensures that an application's components function correctly when assembled.</span></span> <span data-ttu-id="ab61f-138">ASP.NET Core 支援整合測試使用單元測試架構和內建測試 web 主機，可以用來處理要求網路額外負荷。</span><span class="sxs-lookup"><span data-stu-id="ab61f-138">ASP.NET Core supports integration testing using unit test frameworks and a built-in test web host that can be used to handle requests without network overhead.</span></span>

<span data-ttu-id="ab61f-139">與不同的單元測試，是整合測試通常牽涉到的應用程式基礎結構考量，例如資料庫、 檔案系統、 網路資源或 web 要求和回應。</span><span class="sxs-lookup"><span data-stu-id="ab61f-139">Unlike unit testing, integration tests frequently involve application infrastructure concerns, such as a database, file system, network resources, or web requests and responses.</span></span> <span data-ttu-id="ab61f-140">單元測試使用 fakes 或模擬物件來取代這些考量。</span><span class="sxs-lookup"><span data-stu-id="ab61f-140">Unit tests use fakes or mock objects in place of these concerns.</span></span> <span data-ttu-id="ab61f-141">但是，整合測試的目的是要確認系統運作正常搭配這些系統，因此為整合測試，您不要使用 fakes 或模擬物件。</span><span class="sxs-lookup"><span data-stu-id="ab61f-141">But the purpose of integration tests is to confirm that the system works as expected with these systems, so for integration testing you do not use fakes or mock objects.</span></span> <span data-ttu-id="ab61f-142">相反地，您可以包含基礎結構，例如資料庫存取或服務引動過程與其他服務。</span><span class="sxs-lookup"><span data-stu-id="ab61f-142">Instead, you include the infrastructure, like database access or service invocation from other services.</span></span>

<span data-ttu-id="ab61f-143">整合測試會執行較大的程式碼區段比單元測試，因為整合測試會依賴基礎結構項目，它們通常是依據重要順序低於單元測試。</span><span class="sxs-lookup"><span data-stu-id="ab61f-143">Because integration tests exercise larger segments of code than unit tests, and because integration tests rely on infrastructure elements, they tend to be orders of magnitude slower than unit tests.</span></span> <span data-ttu-id="ab61f-144">因此，最好限制多少整合測試，您撰寫和執行。</span><span class="sxs-lookup"><span data-stu-id="ab61f-144">Thus, it is a good idea to limit how many integration tests you write and run.</span></span>

<span data-ttu-id="ab61f-145">ASP.NET Core 包括內建測試 web 主機可以用來處理 HTTP 要求不含網路額外負荷，這表示，您可以執行這些測試速度時使用真實的 web 主機。</span><span class="sxs-lookup"><span data-stu-id="ab61f-145">ASP.NET Core includes a built-in test web host that can be used to handle HTTP requests without network overhead, meaning that you can run those tests faster when using a real web host.</span></span> <span data-ttu-id="ab61f-146">測試 web 主機有 NuGet 元件為 Microsoft.AspNetCore.TestHost。</span><span class="sxs-lookup"><span data-stu-id="ab61f-146">The test web host is available in a NuGet component as Microsoft.AspNetCore.TestHost.</span></span> <span data-ttu-id="ab61f-147">它可以加入至整合測試專案，並用於主機 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ab61f-147">It can be added to integration test projects and used to host ASP.NET Core applications.</span></span>

<span data-ttu-id="ab61f-148">您可以看到下列程式碼中，當您建立整合測試的 ASP.NET Core 控制站，您具現化的測試主機控制站。</span><span class="sxs-lookup"><span data-stu-id="ab61f-148">As you can see in the following code, when you create integration tests for ASP.NET Core controllers, you instantiate the controllers through the test host.</span></span> <span data-ttu-id="ab61f-149">這相當於 HTTP 要求，但執行速度較快。</span><span class="sxs-lookup"><span data-stu-id="ab61f-149">This is comparable to an HTTP request, but it runs faster.</span></span>

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

#### <a name="additional-resources"></a><span data-ttu-id="ab61f-150">其他資源</span><span class="sxs-lookup"><span data-stu-id="ab61f-150">Additional resources</span></span>

-   <span data-ttu-id="ab61f-151">**Steve Smith。測試控制器**(ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)</span><span class="sxs-lookup"><span data-stu-id="ab61f-151">**Steve Smith. Testing controllers** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)</span></span>

-   <span data-ttu-id="ab61f-152">**Steve Smith。整合測試**(ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/testing/integration-testing*](https://docs.microsoft.com/aspnet/core/testing/integration-testing)</span><span class="sxs-lookup"><span data-stu-id="ab61f-152">**Steve Smith. Integration testing** (ASP.NET Core) [*https://docs.microsoft.com/aspnet/core/testing/integration-testing*](https://docs.microsoft.com/aspnet/core/testing/integration-testing)</span></span>

-   <span data-ttu-id="ab61f-153">**單元測試中使用 dotnet 測試.NET Core**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)</span><span class="sxs-lookup"><span data-stu-id="ab61f-153">**Unit testing in .NET Core using dotnet test**
[*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)</span></span>

-   <span data-ttu-id="ab61f-154">**xUnit.net**。</span><span class="sxs-lookup"><span data-stu-id="ab61f-154">**xUnit.net**.</span></span> <span data-ttu-id="ab61f-155">官方網站。</span><span class="sxs-lookup"><span data-stu-id="ab61f-155">Official site.</span></span>
    [<span data-ttu-id="ab61f-156">*https://xunit.github.io/*</span><span class="sxs-lookup"><span data-stu-id="ab61f-156">*https://xunit.github.io/*</span></span>](https://xunit.github.io/)

-   <span data-ttu-id="ab61f-157">**單元測試基本概念。** 
     [ *https://msdn.microsoft.com/en-us/library/hh694602.aspx*](https://msdn.microsoft.com/en-us/library/hh694602.aspx)</span><span class="sxs-lookup"><span data-stu-id="ab61f-157">**Unit Test Basics.**
[*https://msdn.microsoft.com/en-us/library/hh694602.aspx*](https://msdn.microsoft.com/en-us/library/hh694602.aspx)</span></span>

-   <span data-ttu-id="ab61f-158">**Moq**。</span><span class="sxs-lookup"><span data-stu-id="ab61f-158">**Moq**.</span></span> <span data-ttu-id="ab61f-159">GitHub 儲存機制。</span><span class="sxs-lookup"><span data-stu-id="ab61f-159">GitHub repo.</span></span>
    [<span data-ttu-id="ab61f-160">*https://github.com/moq/moq*</span><span class="sxs-lookup"><span data-stu-id="ab61f-160">*https://github.com/moq/moq*</span></span>](https://github.com/moq/moq)

-   <span data-ttu-id="ab61f-161">**NUnit**。</span><span class="sxs-lookup"><span data-stu-id="ab61f-161">**NUnit**.</span></span> <span data-ttu-id="ab61f-162">官方網站。</span><span class="sxs-lookup"><span data-stu-id="ab61f-162">Official site.</span></span>
    [<span data-ttu-id="ab61f-163">*https://www.nunit.org/*</span><span class="sxs-lookup"><span data-stu-id="ab61f-163">*https://www.nunit.org/*</span></span>](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a><span data-ttu-id="ab61f-164">實作多重容器應用程式上的服務測試</span><span class="sxs-lookup"><span data-stu-id="ab61f-164">Implementing service tests on a multi-container application</span></span> 

<span data-ttu-id="ab61f-165">如前文所述，當您測試多個容器應用程式時，所有 microservices 都需要 Docker 主機或容器叢集內執行。</span><span class="sxs-lookup"><span data-stu-id="ab61f-165">As noted earlier, when you test multi-container applications, all the microservices need to be running within the Docker host or container cluster.</span></span> <span data-ttu-id="ab61f-166">端對端服務的測試包含多個作業牽涉到數個 microservices 需要您部署和啟動 Docker 主機中的整個應用程式執行 docker-撰寫向上 （或如果您使用 orchestrator 比較機制）。</span><span class="sxs-lookup"><span data-stu-id="ab61f-166">End-to-end service tests that include multiple operations involving several microservices require you to deploy and start the whole application in the Docker host by running docker-compose up (or a comparable mechanism if you are using an orchestrator).</span></span> <span data-ttu-id="ab61f-167">一旦整個應用程式及其所有服務正常執行，您可以執行端對端整合和功能測試。</span><span class="sxs-lookup"><span data-stu-id="ab61f-167">Once the whole application and all its services is running, you can execute end-to-end integration and functional tests.</span></span>

<span data-ttu-id="ab61f-168">有幾個方法，您可以使用。</span><span class="sxs-lookup"><span data-stu-id="ab61f-168">There are a few approaches you can use.</span></span> <span data-ttu-id="ab61f-169">您用來部署應用程式 （或類似的項目，例如 docker compose.ci.build.yml） docker compose.yml 檔案中，您也可以在方案層級展開進入點，以使用[dotnet 測試](https://docs.microsoft.com/dotnet/core/tools/dotnet-test)。</span><span class="sxs-lookup"><span data-stu-id="ab61f-169">In the docker-compose.yml file that you use to deploy the application (or similar ones, like docker-compose.ci.build.yml), at the solution level you can expand the entry point to use [dotnet test](https://docs.microsoft.com/dotnet/core/tools/dotnet-test).</span></span> <span data-ttu-id="ab61f-170">您也可以使用另一個會在您的目標的映像中執行測試的撰寫檔案。</span><span class="sxs-lookup"><span data-stu-id="ab61f-170">You can also use another compose file that would run your tests in the image you are targeting.</span></span> <span data-ttu-id="ab61f-171">使用另一個編輯檔案的整合測試，其中包含您 microservices 和容器上的資料庫，您可以確保，相關的資料永遠重設為其原始狀態再執行測試。</span><span class="sxs-lookup"><span data-stu-id="ab61f-171">By using another compose file for integration tests that includes your microservices and databases on containers, you can make sure that the related data is always reset to its original state before running the tests.</span></span>

<span data-ttu-id="ab61f-172">撰寫應用程式啟動且正在執行時，您可以要善用中斷點和例外狀況，如果您正在 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="ab61f-172">Once the compose application is up and running, you can take advantage of breakpoints and exceptions if you are running Visual Studio.</span></span> <span data-ttu-id="ab61f-173">或者，您可以在 Visual Studio Team Services 或其他支援 Docker 容器的 CI/CD 系統 CI 管線中，自動執行整合測試。</span><span class="sxs-lookup"><span data-stu-id="ab61f-173">Or you can run the integration tests automatically in your CI pipeline in Visual Studio Team Services or any other CI/CD system that supports Docker containers.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="ab61f-174">[上一個](訂閱-events.md) [下一步] (.../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="ab61f-174">[Previous] (subscribe-events.md) [Next] (../microservice-ddd-cqrs-patterns/index.md)</span></span>
