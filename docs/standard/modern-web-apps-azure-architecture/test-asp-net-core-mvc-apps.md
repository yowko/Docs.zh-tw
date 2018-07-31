---
title: 測試 ASP.NET Core MVC 應用程式
description: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 | 測試 ASP.NET Core MVC 應用程式
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: b6c881a445f5848829ab5ccc6ce8547a390d89f3
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404615"
---
# <a name="test-aspnet-core-mvc-apps"></a>測試 ASP.NET Core MVC 應用程式

> *「如果您不喜歡為您的產品進行單元測試，您的客戶多半也不會喜歡測試它。」*
 > \_- 匿名-

軟體複雜與否，都可能以意想不到的方式回應變更而失敗。 因此，除了最不重要的 (或最不關鍵的) 應用程式之外，對所有應用程式進行變更後都需要進行測試。 手動測試是最慢、最不可靠且最昂貴的測試軟體方式。 不幸的是，如果應用程式設計為不可測試，則手動可能是唯一可用的手段。 遵循第 X 章規定之架構原則所撰寫的應用程式，應可進行單元測試，ASP.NET Core 應用程式也支援自動化整合和功能測試。

## <a name="kinds-of-automated-tests"></a>自動化測試的種類

軟體應用程式自動化測試有許多種類的。 最簡單且最低層級的測試為單元測試。 在稍高層級有整合測試與功能測試。 其他種類的測試如 UI 測試、負載測試、壓力測試和煙霧測試，則不在本文件討論範圍內。

### <a name="unit-tests"></a>單元測試

單元測試會測試應用程式邏輯的單一組件。 可透過列舉一些不具有的事物來對其進一步描述。 單元測試不會測試程式碼如何與相依性或基礎結構同運作，那會在整合測試中進行。 單元測試不會測試撰寫程式碼所採用的架構，您應假設該架構可正常運行；如果您發現並非如此，請提交 Bug 並撰寫因應措施。 單元測試完全在記憶體和處理序中執行。 不會與文件系統、網路或資料庫進行通訊。 單元測試應純粹只測試您的程式碼。

由於單元測試只測試程式碼的一個單元且不含外部相依性，所以應該執行得非常迅速。 因此，您應該能夠在幾秒鐘內執行數百個單元測試的測試套件。 請經常執行，理想情況下在每次推送至共用原始檔控制儲存機制前都先執行，且當然是以組建伺服器上的每個自動化組建來執行。

### <a name="integration-tests"></a>整合測試

雖然封裝與資料庫和檔案系統等基礎結構互動的程式碼是不錯的想法，但您仍將會持有其中某些程式碼且可能需要對其進行測試。 此外，您應該驗證當應用程式相依性在完全解析時，程式碼層的互動是否與預期一致。 這是整合測試的職責。 整合測試通常比單元測試慢且更難設定，因為通常依賴於外部相依性與基礎結構。 因此，您應該避免在整合測試中進行可使用單元測試進行的測試。 如果您可以用單元測試來測試一個指定的案例，您應該用單元測試來進行測試。 如果不能，則考慮使用整合測試。

整合測試通常會有比單元測試更複雜的設定與清除程序。 例如，針對實際資料庫的整合測試，需要一種能在每次測試之前將資料庫傳回已知狀態的方法。 隨著新測試的新增和資料庫結構描述發展出的生產，這些測試指令碼的大小和複雜程度都會增加。 在許多大型系統中，簽入共用原始檔控制的變更之前，在開發人員工作站上執行完整的整合測試套件並不切實際。 在這些情況下，整合測試可能會在組建伺服器上執行。

LocalFileImageService 實作類別，會實作從指定識別碼之特定文件夾中擷取和傳回影像檔位元數的邏輯：

```csharp
public class LocalFileImageService : IImageService
{
    private readonly IHostingEnvironment _env;
    public LocalFileImageService(IHostingEnvironment env)
    {
        _env = env;
    }
    public byte[] GetImageBytesById(int id)
    {
        try
        {
            var contentRoot = _env.ContentRootPath + "//Pics";
            var path = Path.Combine(contentRoot, id + ".png");
            return File.ReadAllBytes(path);
        }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

### <a name="functional-tests"></a>功能測試

整合測試是從開發人員的角度撰寫，以驗證系統的某些元件是否能夠正確地一起運作。 功能測試是從使用者的角度撰寫，並根據其要求來驗證系統的正確性。 相較於單元測試，下列摘錄提供有用的比喻來說明如何思考功能測試：

> 「很多時候，系統的開發就像是建造房屋。 雖然這個比喻不太正確，但我們可以將其延伸以便理解單元測試和功能測試之間的差異。 單元測試類似於造訪房屋建築工地的建築檢查員。 檢查員會專注於房屋的各種內部系統：地基、結構、電力、配管系統等等。 其會確保 (測試) 房屋的各部分都能正確且安全地運作，也就是符合建築規範。 在此案例中，功能測試類似於屋主造訪同一個建築工地。 屋主會假設內部系統能運作正常，因為建築檢查員正在執行工作。 屋主會著重於住在這個房子裡會是什麼樣子。 他會關心房子的外觀：房間大小是否舒適、房子是否符合家庭的需要、窗戶是否位於能迎接早晨陽光的位置。 這即為屋主對房屋進行功能測試。 他以使用者的角度來觀看。 而建築檢查員是對房屋進行單元測試。 其以建築者的角度來觀看。」

來源：[Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html) (單元測試與功能測試)

我喜歡說：「身為開發人員，我們有兩種失敗方式：以錯誤的方式建置東西，或建置錯誤的東西。」 單元測試確保您以正確的方式建置東西，而功能測試確保您建置正確的東西。

由於功能測試在系統層級上操作，因此可能需要一定程度的 UI 自動化。 與整合測試一樣，功能測試通常也會使用某種類的測試基礎結構。 這使其比單元和整合測試更慢且較不可靠。 功能測試的次數，只要足以確保系統會按照使用者的期望運作即可。

### <a name="testing-pyramid"></a>測試金字塔圖

Martin Fowler 撰寫了測試金字塔相關事項，其中的一個範例如圖 9-1 所示。

![](./media/image9-1.png)

圖 9-1 測試金字塔圖

金字塔的不同圖層及其相對大小代表了不同類型的測試，以及您應該為應用程式撰寫的測試數量。 如您所見，建議以大型的單元測試作為基礎，由較小的整合測試層來支援，再加上一個更小的功能測試層。 理想情況下，每個圖層的測試只應能在該層中進行，而不能在較低層中充分進行。 在您嘗試決定需要在特定案例中使用哪種測試類型時，請記得測試金字塔。

### <a name="what-to-test"></a>測試的內容

對於沒有撰寫自動化測試經驗的開發人員來說，常見問題就是測試的內容。 測試條件式邏輯是很好的起點。 如您有任何能根據條件陳述式 (if-else、switch 等等) 而變更行為的方法，您就應該至少能進行一些測試，以確認某些情況下的正確行為。 如果您的程式碼有錯誤狀況，可透過程式碼撰寫至少一個「開心路徑」 (即沒有錯誤) 的測試，且至少一個「悲傷路徑」 (含有錯誤或非典型結果) 的測試，來確認您的應用程式在出現錯誤時的行為如預期。 最後，嘗試專注於測試可能失敗的事項，而不是專注於程式碼涵蓋範圍等指標。 一般來說，程式碼涵蓋範圍是多優於少。 但是，多一些以非常複雜且業務關鍵方法撰寫的程式碼，通常比僅僅為了改善測試程式碼涵蓋範圍指標而撰寫測試的自動屬性，還更具時間效益。

## <a name="organizing-test-projects"></a>組織測試專案

可以使用最適合您的方式來組織測試專案。 依照類型 (單元測試、整合測試) 和測試內容 (依照專案、命名空間) 來分隔測試是不錯的做法。 此分隔該由單一測試專案中的資料夾組成，或是由多個測試專案組成，是設計上的決策。 單一專案是最簡單的，但針對有大量測試的大型專案，或為了能更容易執行不同的測試集，您可能需要有幾個不同的測試專案。 許多小組根據正在測試的專案來組織測試專案；對於具有許多專案的應用程式，這可能會導致大量測試專案，尤其是如果您仍然根據每個專案中的測試種類來分隔測試專案。 折衷方法是讓每個應用程式的每種測試都有一個專案，在測試專案中包含資料夾以指出正在測試的專案 (和類別)。

常用的方法是在 'src' 資料夾下組織應用程式專案，並在平行的 ‘tests' 資料夾下組織應用程式測試專案。 如果您覺得這樣的組織很有用，您可以在 Visual Studio 中建立相符的解決方案資料夾。

![](./media/image9-2.png)

圖 9-2 解決方案中的測試組織

您可以使用您偏好的任何測試架構。 xUnit 架構運作良好，且用來寫入所有的 ASP.NET Core 和 EF Core 測試。 您可以使用圖 9-3 中的範本，或使用 dotnet new xunit 的 CLI，在 Visual Studio 中新增 xUnit 測試專案。

![](./media/image9-3.png)

圖 9-3 在 Visual Studio 中新增 xUnit 測試專案

### <a name="test-naming"></a>命名測試

您應該以統一的方式來為測試命名，並以名稱來指出每項測試的用途。 取得巨大成功的一種方法，是根據其正在測試的類別和方法來命名測試類別。 這會導致許多小測試類別，但可以非常清楚劃分每項測試的職責。 藉由設定測試類別名稱來識別要測試的類別和方法，測試方法名稱可用於指定要測試的行為。 這應該包含預期的行為，以及任何應該產生這種行為的輸入或假設。 測試名稱的一些範例：

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

此方法的變體，會結束每個含有 "Should" 的測試類別名稱，並稍微修改時態：

- `CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`

- `CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`

有些小組會認為第二種命名方法更清楚，只是略為冗長。 無論如何，請嘗試使用能深入了解測試行為的命名慣例；如此，當一或多項測試失敗時，從其名稱即可明顯看出是哪些案例失敗。 請避免含糊不清地命名您的測試，例如 ControllerTests.Test1，因為在測試結果中看到時並不會提供任何價值。

如果您遵循如上所述會產生許多小型測試類別的命名慣例，建議使用資料夾和命名空間來進一步組織測試。 圖 9-4 顯示在幾個測試專案中按資料夾組織測試的一種方法。

![](./media/image9-4.png)

**圖 9-4。** 根據正在測試的類別，按資料夾來組織測試類別。

當然，如果一個特定的應用程式類別中有很多方法正在進行測試 (且因此有許多測試類別)，將其放在與應用程式類別相對應的資料夾中，是有意義的。 這個組織與您如何將檔案組織到別處的資料夾中沒有區別。 如果在包含許多其他檔案的資料夾中有三或四個以上相關檔案，將其移到其本身的子資料夾通常會很有幫助。

## <a name="unit-testing-aspnet-core-apps"></a>對 ASP.NET Core 應用程式進行單元測試

在設計良好的 ASP.NET Core 應用程式中，大部分的複雜性和商務邏輯都會封裝在商務實體與各種服務中。 ASP.NET Core MVC 應用程式本身及其控制器、篩選器、檢視模型和檢視，應只需要很少量的單元測試。 指定動作的許多功能，大多在動作方法本身之外。 使用單元測試無法有效測試路由或全域錯誤處理是否運作正常。 同樣地，任何篩選器 (包含模型驗證和授權，以及授權篩選條件) 都不能進行單元測試。 如果沒有這些行為來源，大多數行動方法應十分微小，會將其大部分工作委派給可獨立於使用它們的控制器來進行測試之服務。

有時您需要重構程式碼才能進行單元測試。 通常這包括識別抽象概念與使用相依性插入來存取您想要測試的程式碼中之抽象概念，而不是直接針對基礎結構進行編碼。 例如，請考慮這個簡單的動作方法，來顯示影像：

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

對此方法進行單元測試很困難，因為它直接相依於 System.IO.File，用來從檔案系統中進行讀取。 您可以測試此行為以確保其按預期運作，但對實際檔案執行此操作的是整合測試。 值得注意的是，您無法測試此方法的路由，但您很快就會了解如何透過功能測試來執行此作業。

如果您不能直接對檔案系統行為進行單元測試，且無法測試路由，那麼需要測試哪些內容？ 在重構使單元測試成為可能之後，您可能會發現一些測試案例和遺失的行為，例如錯誤處理。 找不到檔案時，該方法會執行什麼操作？ 它應該做什麼？ 在此範例中，重構的方法如下所示：

```csharp
[HttpGet("[controller]/pic/{id}")\]
public IActionResult GetImage(int id)
{
    byte[] imageBytes;
    try
    {
        imageBytes = _imageService.GetImageBytesById(id);
    }
    catch (CatalogImageMissingException ex)
    {
        _logger.LogWarning($"No image found for id: {id}");
        return NotFound();
    }
    return File(imageBytes, "image/png");
}
```

\_記錄器和 \_imageService 會同時插入作為相依性。 現在您可以測試將傳遞給操作方法的相同識別碼傳遞給 \_imageService，且產生之位元組會作為 FileResult 的一部分傳回。 您也可以測試錯誤記錄是否按預期進行；假設這是重要的應用程式行為 (意即，不僅僅是開發人員用於診斷問題的臨時程式碼)，如果影像遺失，則傳回 NotFound 結果。 實際的檔案邏輯已移至另一個實作服務中，並且已擴大為針對遺失檔案情況來傳回應用程式特定的例外狀況。 您可以使用整合測試來獨立測試此實作。

## <a name="integration-testing-aspnet-core-apps"></a>對 ASP.NET Core 應用程式進行整合測試

若要對 LocalFileImageService 使用整合測試確認 是否正常運作，您需要建立一個已知的測試影像檔，並驗證該服務會在指定特定輸入的情況下將其傳回。 請注意不要在您實際想要測試的行為上使用模擬物件 (在此情況下，從檔案系統讀取)。 但是，模擬物件可能仍然有助於設定整合測試。 在此情況下，您可以模擬 IHostingEnvironment，使其 ContentRootPath 指向您要用於測試影像的資料夾。 完整運作的整合測試類別如下所示：

```csharp
public class LocalFileImageServiceGetImageBytesById
{
    private byte[] _testBytes = new byte[] { 0x01, 0x02, 0x03 };
    private readonly Mock<IHostingEnvironment> _mockEnvironment = new Mock<IHostingEnvironment>();
    private int _testImageId = 123;
    private string _testFileName = "123.png";

    public LocalFileImageServiceGetImageBytesById()
    {
        // create folder if necessary
        Directory.CreateDirectory(Path.Combine(GetFileDirectory(), "Pics"));
        string filePath = GetFilePath(_testFileName);
        System.IO.File.WriteAllBytes(filePath, _testBytes);
        _mockEnvironment.SetupGet<string>(m => m.ContentRootPath).Returns(GetFileDirectory());
    }

    private string GetFilePath(string fileName)
    {
        return Path.Combine(GetFileDirectory(), "Pics", fileName);
        }
            private string GetFileDirectory()
        {
        var location = System.Reflection.Assembly.GetEntryAssembly().Location;
        return Path.GetDirectoryName(location);
    }

    [Fact]
    public void ReturnsFileContentResultGivenValidId()
    {
        var fileService = new LocalFileImageService(_mockEnvironment.Object);
        var result = fileService.GetImageBytesById(_testImageId);
        Assert.Equal(_testBytes, result);
    }
}
```

> [!NOTE]
> 測試本身非常簡單，大部分程式碼對設定系統和建立測試基礎結構 (在此案例中，從磁碟讀取實際檔案) 是必需的。 這對整合測試來說很常見，通常需要比單元測試更複雜的設定工作。

## <a name="functional-testing-aspnet-core-apps"></a>對 ASP.NET Core 應用程式進行功能測試

對於 ASP.NET Core 應用程式，TestServer 類別可使功能測試很容易撰寫。 直接使用 WebHostBuilder 設定 TestServer (就像您平常設定應用程式一樣)，或使用 WebApplicationFactory 類型 (2.1 中有提供)。 您應該盡可能讓測試主機幾乎與生產主機完全一樣，如此一來，測試的執行行為會與應用程式實際在生產環境中的執行行為類似。 WebApplicationFactory 類別有助於設定 TestServer 的 ContentRoot，ASP.NET Core 用它來找到靜態資源 (如 Views)。

建立簡單功能測試的方法是，建立實作 IClassFixture < WebApplicationFactory<TEntry>> 的測試類別，其中 TEntry 是 Web 應用程式的啟動類別。 準備好測試類別之後，測試固件可以使用處理站的 CreateClient 方法來建立用戶端：

```cs
public class BasicWebTests : IClassFixture<WebApplicationFactory<Startup>>
{
    protected readonly HttpClient _client;

    public BaseWebTest(WebApplicationFactory<Startup> factory)
    {
        _client = factory.CreateClient();
    }

    // write tests that use _client
}
```

通常在每次測試執行之前，您會想要對網站執行一些額外的設定，例如，設定應用程式使用記憶體內資料存放區，然後將測試資料植入應用程式。 若要這樣做，您應該建立自己的 WebApplicationFactory<TEntry> 子類別並覆寫其 ConfigureWebHost 方法。 下列範例取自 eShopOnWeb FunctionalTests 專案，並做為主要 Web 應用程式測試的一部分。

```cs
using Infrastructure.Data;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.eShopWeb;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;
using Microsoft.EntityFrameworkCore;
using Infrastructure.Identity;

namespace FunctionalTests.WebRazorPages
{
    public class CustomWebRazorPagesApplicationFactory<TStartup>
    : WebApplicationFactory<Startup>
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            builder.ConfigureServices(services =>
            {
                // Create a new service provider.
                var serviceProvider = new ServiceCollection()
                    .AddEntityFrameworkInMemoryDatabase()
                    .BuildServiceProvider();

                // Add a database context (ApplicationDbContext) using an in-memory
                // database for testing.
                services.AddDbContext<CatalogContext>(options =>
                {
                    options.UseInMemoryDatabase("InMemoryDbForTesting");
                    options.UseInternalServiceProvider(serviceProvider);
                });

                services.AddDbContext<AppIdentityDbContext>(options =>
                {
                    options.UseInMemoryDatabase("Identity");
                    options.UseInternalServiceProvider(serviceProvider);
                });

                // Build the service provider.
                var sp = services.BuildServiceProvider();

                // Create a scope to obtain a reference to the database
                // context (ApplicationDbContext).
                using (var scope = sp.CreateScope())
                {
                    var scopedServices = scope.ServiceProvider;
                    var db = scopedServices.GetRequiredService<CatalogContext>();
                    var loggerFactory = scopedServices.GetRequiredService<ILoggerFactory>();

                    var logger = scopedServices
                        .GetRequiredService<ILogger<CustomWebRazorPagesApplicationFactory<TStartup>>>();

                    // Ensure the database is created.
                    db.Database.EnsureCreated();

                    try
                    {
                        // Seed the database with test data.
                        CatalogContextSeed.SeedAsync(db, loggerFactory).Wait();
                    }
                    catch (Exception ex)
                    {
                        logger.LogError(ex, $"An error occurred seeding the " +
                            "database with test messages. Error: {ex.Message}");
                    }
                }
            });
        }
    }
}
```

測試可以利用這個自訂的 WebApplicationFactory，使用它來建立用戶端，然後再使用此用戶端執行個體對應用程式提出要求。 應用程式內將會有植入的資料，測試的判斷提示會用到這些資料。 此測試會驗證 eShopOnWeb Razor Pages 應用程式的首頁已正確載入，而且其中包含做為植入資料新增到應用程式的產品清單。

```cs
using Microsoft.eShopWeb.RazorPages;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace FunctionalTests.WebRazorPages
{
    public class HomePageOnGet : IClassFixture<CustomWebRazorPagesApplicationFactory<Startup>>
    {
        public HomePageOnGet(CustomWebRazorPagesApplicationFactory<Startup> factory)
        {
            Client = factory.CreateClient();
        }

        public HttpClient Client { get; }

        [Fact]
        public async Task ReturnsHomePageWithProductListing()
        {
            // Arrange & Act
            var response = await Client.GetAsync("/");
            response.EnsureSuccessStatusCode();
            var stringResponse = await response.Content.ReadAsStringAsync();

            // Assert
            Assert.Contains(".NET Bot Black Sweatshirt", stringResponse); // from seed data
        }
    }
}
```

此功能測試將執行完整的 ASP.NET Core MVC / Razor Pages 應用程式堆疊，包括可能存在的所有中介軟體、篩選器、繫結器等等。 它會確認指定的路由 ("/") 會傳回預期的成功狀態碼和 HTML 輸出。 因並未設定真實的網頁伺服器，所以避免了使用真實的網頁伺服器進行測試之脆弱度 (例如防火牆設定的問題)。 針對 TestServer 執行的功能測試通常比整合與單元測試要慢，但比在網路上執行測試之網頁伺服器的測試要快得多。 您應該使用功能測試以確保應用程式的前端堆疊可如預期運作。 當您在控制器或頁面中找到重複項目並透過新增篩選器來處理這些項目時，這些測試會特別有用。 在理想情況下，這種重構並不會變更應用程式的行為，而一整套功能測試將驗證這種情況。

>[!div class="step-by-step"]
[上一頁](work-with-data-in-asp-net-core-apps.md)
[下一頁](development-process-for-azure.md)
