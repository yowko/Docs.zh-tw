---
title: "測試 ASP.NET Core MVC 應用程式"
description: "使用 ASP.NET Core 和 Azure 的現代化 Web 應用程式架構設計人員 |測試 ASP.NET Core MVC 應用程式"
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 4611ffa8334e124946e849306d3281b695830eb1
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2017
---
# <a name="test-aspnet-core-mvc-apps"></a>測試 ASP.NET Core MVC 應用程式

> _"如果您不喜歡單元測試您的產品，最有可能您的客戶不會想要予以測試，請。 」_
> _-匿名-

## <a name="summary"></a>總結

任何複雜度的軟體可能會非預期的方式，以回應變更失敗。 因此，測試進行變更之後，才能幾乎連最簡單的 （或最不重要的） 的應用程式。 手動測試是最慢的作業，最可靠且成本最高的方式測試軟體。 不幸的是，如果應用程式都不可測試的設計，它可以是唯一可用的方法。 撰寫架構原則配置的下列章節 X 中的應用程式應該是單元測試和 ASP.NET Core 應用程式支援自動化的整合和功能測試以及。

## <a name="kinds-of-automated-tests"></a>類型的自動化測試

有許多種類的軟體應用程式的自動化測試。 最簡單的最低層級的測試是單元測試。 在稍高等級有整合測試與功能測試。 其他種類的測試，例如 UI 測試、 負載測試、 壓力測試和煙霧測試中，已超出本文的範圍。

### <a name="unit-tests"></a>單元測試

單元測試中測試您的應用程式邏輯的單一組件。 其中一個可以進一步說明藉由列出的一些作業，它不是。 單元測試不會測試的相依性或基礎結構-何種整合測試的程式碼正常運作的方式。 單元測試不會測試您的程式碼也會在寫入架構，您應該假設它的運作或，如果您覺得不、 提報 bug 和程式碼因應措施。 在記憶體和處理序中，會完全執行單元測試。 它不會與檔案系統、 網路或資料庫進行通訊。 單元測試應該只測試您的程式碼。

單元測試，其會測試您的程式碼，不含外部相依性，將單一單位的事實必定應執行速度非常快。 因此，您應該能夠在幾秒鐘的時間執行的數百個單元測試的測試套件。 它們經常執行，在理想情況下再每個推送至共用原始檔控制儲存機制中，並確實與每個自動化建置您的組建伺服器上。

### <a name="integration-tests"></a>整合測試

雖然它是個不錯的主意，封裝會與基礎結構，例如資料庫和檔案系統互動的程式碼，您仍會有部分的程式碼，您可能會想要測試它。 此外，您應該確認您的程式碼層級互動如預期般完全解析您的應用程式相依性時。 這是整合測試的責任。 整合測試通常速度較慢且更難以設定比單元測試，因為它們通常取決於外部相依性和基礎結構。 因此，您應該避免測試可能是整合測試中的單元測試的測試中的項目。 如果您可以測試特定的案例與單元測試，您應該測試它與單元測試。 如果無法處理，請考慮使用整合測試。

整合測試時，通常會有更複雜的設定和清除程序比單元測試。 例如，整合測試，會針對實際的資料庫會需要能夠讓資料庫返回已知的狀態，每個測試回合之前。 加入新的測試和實際執行資料庫結構描述的發展，這些測試指令碼通常會成長的大小和複雜度。 在許多大型系統，很適合簽入變更到共用的原始檔控制之前，開發人員工作站上執行完整的整合測試套件。 在這些情況下，可能會在組建伺服器上執行整合測試。

LocalFileImageService 實作類別會實作用於擷取和傳回的映像檔的位元組數從指定的 id 的特定資料夾的邏輯：

```cs
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
```

### <a name="functional-tests"></a>功能測試

整合測試的開發人員，以驗證系統的某些元件可正確地同時角度從寫入。 功能測試會寫入從使用者的觀點來看，並確認系統根據其需求的正確性。 下列摘錄中提供比喻如何思考功能測試，相較於單元測試：

> 「 系統的開發多次被比擬為一棟房子的建置。 雖然這項類比帶並不是相當正確，我們可以延伸該架構基於的了解單元測試和功能的測試之間的差異。 類似於瀏覽一棟房子建構網站建置 inspector 單元測試。 他會著重於各種內部房屋、 框架、 電力、 配管，等等的基礎的系統。 他可確保房屋的組件會正確運作，並安全地，也就是符合建置程式碼 （測試）。 在此案例中的功能測試會類似於瀏覽這個相同的建構網站家長。 他會假設內部系統將會適當地運作，建置偵測器正在執行他的工作。 家長著重於以及它進行像是存在於此房子。 他關心房子的外觀、 各種聊天室舒適的大小、 房子是否符合需求的系列，都適合攔截早上 sun 中的視窗。 家長房子上執行功能測試。 他有使用者的觀點來看。 建置偵測器房子上執行單元測試。 他有產生器 」 的檢視方塊 」。

來源：[單元測試與功能測試](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

我喜歡說 「 身為開發人員，我們在兩種方式會失敗： 我們建置的項目不正確，或我們建置錯誤的項目。 」 單元測試，確保您要建置的項目權限;功能測試，請確定您在建立正確的事。

功能測試是在系統層級上操作，因為它們可能會需要某種程度的 UI 自動化。 整合測試，例如它們通常會使用某種類型的測試基礎結構。 這讓它們更慢，而且比單元和整合測試更不可靠。 您應該僅具有許多功能測試，因為您必須確定系統如預期的使用者行為。

### <a name="testing-pyramid"></a>測試金字塔圖

Martin Fowler 寫入有關測試金字塔圖，顯示的範例圖 9-1。

![](./media/image9-1.png)

圖 9 1 測試金字塔圖

金字塔圖和其相對的大小不同的圖層代表不同種類的測試和多少您應該撰寫應用程式。 如您所見，建議是讓單元測試，更小的圖層的功能測試較小的整合測試，圖層所支援的大型基底。 每個圖層應該在理想情況下只有測試中的低層級無法充分執行。 當您嘗試決定您需要在特定案例的測試類型時，請記住測試的金字塔。

### <a name="what-to-test"></a>要測試的項目

接下來的開發人員會熟悉撰寫自動化的測試的常見的問題與要測試的項目。 若要測試的條件式邏輯是很好的起點。 您有任何變更會根據條件陳述式的行為的方法如果 else，切換 (等），您應該能夠出現至少有幾個確認特定條件的正確行為的測試。 如果您的程式碼有錯誤狀況，最好確認應用程式的行為如預期般遇到錯誤時寫入至少一個測試執行程式碼 」 高興路徑 」 （未出現任何錯誤），以及至少一個測試，「 悲傷路徑 」 （具有錯誤或非典型的結果）。 最後，請嘗試將焦點放在測試，可能會失敗的項目，而不是將焦點放在計量，例如程式碼涵蓋範圍。 多個程式碼涵蓋範圍通常是優於少。 不過，撰寫非常複雜，而且業務關鍵方法的一些詳細測試通常是利用時間比撰寫測試的 auto 屬性只是為了改善測試程式碼涵蓋範圍的度量。

## <a name="organizing-test-projects"></a>組織測試專案

可以組織測試專案，不過您最佳的運作方式。 最好分隔測試類型 （整合測試中的 單元測試），以及藉由測試 （藉由命名空間的專案）。 中的單一測試專案或多個測試專案的資料夾是否包含這項分隔是設計的決策。 其中一個專案是最簡單，但用於大型專案中使用許多測試，或是為了更輕鬆地執行不同的測試集，您可能想要有數個不同的測試專案。 許多小組來組織根據他們所測試，其中有多個專案的應用程式可能會導致大量的測試專案中，特別是如果您仍將分解這些根據種類的測試會在每個專案的專案的測試專案。 洩露方法是讓每種測試，每個應用程式，以指出要測試的專案 （和類別） 的測試專案內的資料夾與一個專案。

常見的作法是組織 'src' 資料夾下的應用程式專案和平行的測試' 資料夾下的應用程式的測試專案。 如果您發現此組織很有用，您可以在 Visual Studio 中，建立相符的方案資料夾。

![](./media/image9-2.png)

圖 9 2 測試組織方案中

您可以使用任何您偏好的測試架構。 XUnit 架構可正常運作，就是，已用來撰寫所有 ASP.NET Core 和 EF 核心的測試。 您可以使用顯示在圖 9-3，或從使用 dotnet 新 xunit CLI 範本的 Visual Studio 中加入 xUnit 測試專案。

![](./media/image9-3.png)

圖 9-3 新增 xUnit Visual Studio 中的測試專案

### <a name="test-naming"></a>測試命名

您應該指出每項測試用途的名稱與命名一致的方式，測試。 我有很棒的成功，但的其中一個方法是根據類別和他們所測試的方法名稱測試類別。 這會導致許多小型測試類別，但它可以非常清楚什麼每項測試會負責。 使用測試類別名稱設定以指定的類別和方法，以進行測試，測試方法名稱可用來指定要測試的行為。 這應該包含預期的行為與任何輸入或應該產生此行為的假設。 一些範例測試名稱中：

-   CatalogControllerGetImage.CallsImageServiceWithId

-   CatalogControllerGetImage.LogsWarningGivenImageMissingException

-   CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess

-   CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException

這種方法的變化會結束 「 應該 」 與每個測試類別名稱，並稍微修改時態：

-   CatalogControllerGetImage**應該**。**呼叫**ImageServiceWithId

-   CatalogControllerGetImage**應該**。**記錄**WarningGivenImageMissingException

有些小組尋找第二個的命名方式更清楚，但是稍微更多詳細資料。 在任何情況下，嘗試使用提供深入了解測試的行為，使用命名慣例，如此當一或多個測試失敗時，它是明顯來自已失敗何種情況下，其名稱。 避免命名您的測試大致，例如 ControllerTests.Test1，這些都會提供任何值，當您在測試結果中看到。

如果您遵循命名慣例，如上述，會產生許多小型測試類別，最好以進一步組織您的測試使用資料夾和命名空間。 圖 9-4 顯示組織內數個測試專案的資料夾來測試的其中一個方法。

![](./media/image9-4.png)

**圖 9-4。** 組織測試的類別為基礎的資料夾來測試類別。

當然，如果特定應用程式類別有多正在測試的方法 （且因此有許多測試類別），可能會更有意義放置這些資料夾對應至應用程式類別中。 此組織並無不同如何組織檔案到其他位置的資料夾。 如果您有多個有三個或四個相關的檔案中包含許多其他檔案的資料夾，通常會很有幫助將它們移入本身的子資料夾。

## <a name="unit-testing-aspnet-core-apps"></a>單元測試的 ASP.NET Core 應用程式

設計良好的 ASP.NET Core 應用程式中的複雜性和商務邏輯的大部分都會封裝在商務實體與各種服務。 ASP.NET Core MVC 應用程式本身，以控制站、 篩選、 viewmodels 及檢視，應該需要極少數的單元測試。 大部分的指定動作的功能之外的動作方法本身。 測試是否運作正常，路由或全域錯誤處理，無法執行有效地與單元測試。 同樣地，任何篩選條件，包括模型驗證和驗證和授權篩選條件，不能進行過單元測試。 這些來源，不應該是行為的兩者很小，委派的服務可測試使用它們的控制站的獨立運作大量大部分動作方法。

有時候，您必須要重構程式碼中的，以便單元測試它。 這經常需要識別的抽象概念和使用相依性插入來存取您想要測試，程式碼中的抽象，而不要直接針對基礎結構程式碼撰寫。 例如，請考慮這個簡單的動作方法，來顯示影像：

```cs
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

單元測試這個方法會由直接相依於 System.IO.File，用來從檔案系統讀取困難。 您可以測試此行為以確保運作正常，但實際的檔案與如此做為整合測試。 值得注意的是您無法測試此方法的路由，您會看到如何短時間內執行此動作與功能的測試。

如果您不能單元測試的檔案系統行為直接，而且您不能測試路由，還有什麼測試呢？ 嗯之後讓單元測試的重構作業，, 您可能會發現一些測試案例和遺失的行為，例如錯誤處理。 方法的作用為何時找不到檔案？ 它是該怎麼辦？ 在此範例中，重構的方法看起來像這樣：

```cs
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

\_記錄器和\_imageService 同時插入做為相依性。 現在您可以測試會傳遞至動作方法的相同識別碼會傳遞至\_imageService，及一部分 FileResult 傳回結果的位元組。 您也可以測試會發生錯誤記錄，不如預期，並會傳回找不到結果，如果映像已遺失，假設這重要的應用程式行為 （亦即，不只暫存程式碼加入至診斷問題的開發人員）。 實際的檔案邏輯已移至另一個實作服務時，並具有已予以增加以傳回遺失檔案的大小寫的應用程式特定例外狀況。 您可以測試此實作中獨立作業，使用整合測試。

## <a name="integration-testing-aspnet-core-apps"></a>整合測試 ASP.NET Core 應用程式

```cs
    }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

此服務會 IHostingEnvironment，程式碼未重構到個別的服務前 CatalogController 一樣。 因為這是唯一的程式碼中使用 IHostingEnvironment 控制器，該相依性已從 CatalogController 的建構函式中移除。

若要測試此服務能夠正常運作，您需要建立已知的測試映像檔，並確認服務傳回其提供特定的輸入。 您應該注意不要使用模擬物件在您實際想要測試 （在此情況下，從檔案系統讀取） 的行為。 不過，模擬物件可能仍會很有用，若要設定整合測試。 在此情況下，您可以模擬 IHostingEnvironment，使其 ContentRootPath 指向您要用於測試影像的資料夾。 完成的工作整合測試類別如下所示：

```cs
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
> 測試本身是很簡單 – 大量的程式碼就必須設定系統，並建立測試的基礎結構 （在此案例中的實際檔案從磁碟讀取）。 這是常見的整合測試，通常需要更複雜的安裝程式工作與單元測試。

## <a name="functional-testing-aspnet-core-apps"></a>功能測試的 ASP.NET Core 應用程式

對於 ASP.NET Core 應用程式，此 TestServer 類別可讓功能測試很容易撰寫。 就像平常您的應用程式，您可以設定使用 WebHostBuilder，TestServer。 應該設定這個 WebHostBuilder，就像您的應用程式的實際主機，但您可以修改它的任何層面，讓測試更為容易。 大部分的情況下，因此您可以將它封裝的可重複使用的方法 （也許在基底類別） 中，您將重複使用相同的 TestServer 許多測試案例：

```cs
public abstract class BaseWebTest
{
    protected readonly HttpClient _client;
    protected string _contentRoot;

    public BaseWebTest()
    {
        _client = GetClient();
    }
    
    protected HttpClient GetClient()
    {
        var startupAssembly = typeof(Startup).GetTypeInfo().Assembly;
        _contentRoot = GetProjectPath("src", startupAssembly);
        var builder = new WebHostBuilder()
        .UseContentRoot(_contentRoot)
        .UseStartup&lt;Startup&gt;();
        var server = new TestServer(builder);
        var client = server.CreateClient();
        return client;
    }
}
```

GetProjectPath 方法只會傳回至 web 專案 （下載範例方案） 的實體路徑。 WebHostBuilder 在此情況下只指定其中內容的根 web 應用程式，以及參考真實的 web 應用程式使用的相同啟動類別。 若要使用 TestServer，您可以使用標準 System.Net.HttpClient 類型提出要求，它。 TestServer 公開提供的預先設定的用戶端準備好要提出 TestServer 上執行的應用程式，很有幫助 CreateClient 方法。 使用此用戶端 (設定為受保護\_上述的基本測試上的用戶端成員) 撰寫 ASP.NET Core 應用程式的功能測試時：

```cs
public class CatalogControllerGetImage : BaseWebTest
{
    [Fact]
    public async Task ReturnsFileContentResultGivenValidId()
    {
        var testFilePath = Path.Combine(_contentRoot, "pics//1.png");
        var expectedFileBytes = File.ReadAllBytes(testFilePath);
        var response = await _client.GetAsync("/catalog/pic/1");
        response.EnsureSuccessStatusCode();
        var streamResponse = await response.Content.ReadAsStreamAsync();
        byte[] byteResult;
        using (var ms = new MemoryStream())
        {
            streamResponse.CopyTo(ms);
            byteResult = ms.ToArray();
        }
        Assert.Equal(expectedFileBytes, byteResult);
    }
}
```

此功能的測試執行完整的 ASP.NET Core MVC 應用程式堆疊，包括所有中介軟體、 篩選器、 繫結器等，可能會先準備就緒。 它會確認指定的路由 （「 / 目錄/pic 1 」） 會傳回預期的位元組陣列，檔案至已知位置。 它會這樣做，而不需設定實際的網頁伺服器，並因此可避免大部分的損毀，使用真實的 web 伺服器以進行測試可能會遇到 （例如，防火牆設定的問題）。 針對 TestServer 執行功能測試通常低於整合和單元測試，但速度比測試 web 伺服器會在網路上執行的測試。

>[!div class="step-by-step"]
[上一個](work-with-data-in-asp-net-core-apps.md) [下一步] (開發的程序-如-azure.md)
