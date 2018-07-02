---
title: 測試 ASP.NET Core MVC 應用程式
description: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 | 測試 ASP.NET Core MVC 應用程式
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.openlocfilehash: b22e0e109144b4abd04cd4199cfdec244d8fa7af
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106498"
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="49605-103">測試 ASP.NET Core MVC 應用程式</span><span class="sxs-lookup"><span data-stu-id="49605-103">Test ASP.NET Core MVC Apps</span></span>

> <span data-ttu-id="49605-104">_「如果您不喜歡為您的產品進行單元測試，您的客戶多半也不會喜歡測試它。」_
>  _- 匿名 -_</span><span class="sxs-lookup"><span data-stu-id="49605-104">_"If you don't like unit testing your product, most likely your customers won't like to test it, either."_
 _- Anonymous-_</span></span>

## <a name="summary"></a><span data-ttu-id="49605-105">總結</span><span class="sxs-lookup"><span data-stu-id="49605-105">Summary</span></span>

<span data-ttu-id="49605-106">軟體複雜與否，都可能以意想不到的方式回應變更而失敗。</span><span class="sxs-lookup"><span data-stu-id="49605-106">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="49605-107">因此，除了最不重要的 (或最不關鍵的) 應用程式之外，對所有應用程式進行變更後都需要進行測試。</span><span class="sxs-lookup"><span data-stu-id="49605-107">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="49605-108">手動測試是最慢、最不可靠且最昂貴的測試軟體方式。</span><span class="sxs-lookup"><span data-stu-id="49605-108">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="49605-109">不幸的是，如果應用程式設計為不可測試，則手動可能是唯一可用的手段。</span><span class="sxs-lookup"><span data-stu-id="49605-109">Unfortunately, if applications are not designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="49605-110">遵循第 X 章規定之架構原則所撰寫的應用程式，應可進行單元測試，ASP.NET Core 應用程式也支援自動化整合和功能測試。</span><span class="sxs-lookup"><span data-stu-id="49605-110">Applications written following the architectural principles laid out in chapter X should be unit testable, and ASP.NET Core applications support automated integration and functional testing as well.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="49605-111">自動化測試的種類</span><span class="sxs-lookup"><span data-stu-id="49605-111">Kinds of Automated Tests</span></span>

<span data-ttu-id="49605-112">軟體應用程式自動化測試有許多種類的。</span><span class="sxs-lookup"><span data-stu-id="49605-112">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="49605-113">最簡單且最低層級的測試為單元測試。</span><span class="sxs-lookup"><span data-stu-id="49605-113">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="49605-114">在稍高層級有整合測試與功能測試。</span><span class="sxs-lookup"><span data-stu-id="49605-114">At a slightly higher level there are integration tests and functional tests.</span></span> <span data-ttu-id="49605-115">其他種類的測試如 UI 測試、負載測試、壓力測試和煙霧測試，則不在本文件討論範圍內。</span><span class="sxs-lookup"><span data-stu-id="49605-115">Other kinds of tests, like UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="49605-116">單元測試</span><span class="sxs-lookup"><span data-stu-id="49605-116">Unit Tests</span></span>

<span data-ttu-id="49605-117">單元測試會測試應用程式邏輯的單一組件。</span><span class="sxs-lookup"><span data-stu-id="49605-117">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="49605-118">可透過列舉一些不具有的事物來對其進一步描述。</span><span class="sxs-lookup"><span data-stu-id="49605-118">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="49605-119">單元測試不會測試程式碼如何與相依性或基礎結構同運作，那會在整合測試中進行。</span><span class="sxs-lookup"><span data-stu-id="49605-119">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="49605-120">單元測試不會測試撰寫程式碼所採用的架構，您應假設該架構可正常運行；如果您發現並非如此，請提交 Bug 並撰寫因應措施。</span><span class="sxs-lookup"><span data-stu-id="49605-120">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="49605-121">單元測試完全在記憶體和處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="49605-121">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="49605-122">不會與文件系統、網路或資料庫進行通訊。</span><span class="sxs-lookup"><span data-stu-id="49605-122">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="49605-123">單元測試應純粹只測試您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="49605-123">Unit tests should only test your code.</span></span>

<span data-ttu-id="49605-124">由於單元測試只測試程式碼的一個單元且不含外部相依性，所以應該執行得非常迅速。</span><span class="sxs-lookup"><span data-stu-id="49605-124">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely quickly.</span></span> <span data-ttu-id="49605-125">因此，您應該能夠在幾秒鐘內執行數百個單元測試的測試套件。</span><span class="sxs-lookup"><span data-stu-id="49605-125">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="49605-126">請經常執行，理想情況下在每次推送至共用原始檔控制儲存機制前都先執行，且當然是以組建伺服器上的每個自動化組建來執行。</span><span class="sxs-lookup"><span data-stu-id="49605-126">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="49605-127">整合測試</span><span class="sxs-lookup"><span data-stu-id="49605-127">Integration Tests</span></span>

<span data-ttu-id="49605-128">雖然封裝與資料庫和檔案系統等基礎結構互動的程式碼是不錯的想法，但您仍將會持有其中某些程式碼且可能需要對其進行測試。</span><span class="sxs-lookup"><span data-stu-id="49605-128">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="49605-129">此外，您應該驗證當應用程式相依性在完全解析時，程式碼層的互動是否與預期一致。</span><span class="sxs-lookup"><span data-stu-id="49605-129">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="49605-130">這是整合測試的職責。</span><span class="sxs-lookup"><span data-stu-id="49605-130">This is the responsibility of integration tests.</span></span> <span data-ttu-id="49605-131">整合測試通常比單元測試慢且更難設定，因為通常依賴於外部相依性與基礎結構。</span><span class="sxs-lookup"><span data-stu-id="49605-131">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="49605-132">因此，您應該避免在整合測試中進行可使用單元測試進行的測試。</span><span class="sxs-lookup"><span data-stu-id="49605-132">Thus, you should avoid testing things that could be tests with unit tests in integration tests.</span></span> <span data-ttu-id="49605-133">如果您可以用單元測試來測試一個指定的案例，您應該用單元測試來進行測試。</span><span class="sxs-lookup"><span data-stu-id="49605-133">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="49605-134">如果不能，則考慮使用整合測試。</span><span class="sxs-lookup"><span data-stu-id="49605-134">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="49605-135">整合測試通常會有比單元測試更複雜的設定與清除程序。</span><span class="sxs-lookup"><span data-stu-id="49605-135">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="49605-136">例如，針對實際資料庫的整合測試，需要一種能在每次測試之前將資料庫傳回已知狀態的方法。</span><span class="sxs-lookup"><span data-stu-id="49605-136">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="49605-137">隨著新測試的新增和資料庫結構描述發展出的生產，這些測試指令碼的大小和複雜程度都會增加。</span><span class="sxs-lookup"><span data-stu-id="49605-137">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="49605-138">在許多大型系統中，簽入共用原始檔控制的變更之前，在開發人員工作站上執行完整的整合測試套件並不切實際。</span><span class="sxs-lookup"><span data-stu-id="49605-138">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="49605-139">在這些情況下，整合測試可能會在組建伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="49605-139">In these cases, integration tests may be run on a build server.</span></span>

<span data-ttu-id="49605-140">LocalFileImageService 實作類別，會實作從指定識別碼之特定文件夾中擷取和傳回影像檔位元數的邏輯：</span><span class="sxs-lookup"><span data-stu-id="49605-140">The LocalFileImageService implementation class implements the logic for fetching and returning the bytes of an image file from a particular folder given an id:</span></span>

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

### <a name="functional-tests"></a><span data-ttu-id="49605-141">功能測試</span><span class="sxs-lookup"><span data-stu-id="49605-141">Functional Tests</span></span>

<span data-ttu-id="49605-142">整合測試是從開發人員的角度撰寫，以驗證系統的某些元件是否能夠正確地一起運作。</span><span class="sxs-lookup"><span data-stu-id="49605-142">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="49605-143">功能測試是從使用者的角度撰寫，並根據其要求來驗證系統的正確性。</span><span class="sxs-lookup"><span data-stu-id="49605-143">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="49605-144">相較於單元測試，下列摘錄提供有用的比喻來說明如何思考功能測試：</span><span class="sxs-lookup"><span data-stu-id="49605-144">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="49605-145">「很多時候，系統的開發就像是建造房屋。</span><span class="sxs-lookup"><span data-stu-id="49605-145">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="49605-146">雖然這個比喻不太正確，但我們可以將其延伸以便理解單元測試和功能測試之間的差異。</span><span class="sxs-lookup"><span data-stu-id="49605-146">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="49605-147">單元測試類似於造訪房屋建築工地的建築檢查員。</span><span class="sxs-lookup"><span data-stu-id="49605-147">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="49605-148">檢查員會專注於房屋的各種內部系統：地基、結構、電力、配管系統等等。</span><span class="sxs-lookup"><span data-stu-id="49605-148">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="49605-149">其會確保 (測試) 房屋的各部分都能正確且安全地運作，也就是符合建築規範。</span><span class="sxs-lookup"><span data-stu-id="49605-149">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="49605-150">在此案例中，功能測試類似於屋主造訪同一個建築工地。</span><span class="sxs-lookup"><span data-stu-id="49605-150">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="49605-151">屋主會假設內部系統能運作正常，因為建築檢查員正在執行工作。</span><span class="sxs-lookup"><span data-stu-id="49605-151">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="49605-152">屋主會著重於住在這個房子裡會是什麼樣子。</span><span class="sxs-lookup"><span data-stu-id="49605-152">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="49605-153">他會關心房子的外觀：房間大小是否舒適、房子是否符合家庭的需要、窗戶是否位於能迎接早晨陽光的位置。</span><span class="sxs-lookup"><span data-stu-id="49605-153">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="49605-154">這即為屋主對房屋進行功能測試。</span><span class="sxs-lookup"><span data-stu-id="49605-154">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="49605-155">他以使用者的角度來觀看。</span><span class="sxs-lookup"><span data-stu-id="49605-155">He has the user's perspective.</span></span> <span data-ttu-id="49605-156">而建築檢查員是對房屋進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="49605-156">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="49605-157">其以建築者的角度來觀看。」</span><span class="sxs-lookup"><span data-stu-id="49605-157">He has the builder's perspective."</span></span>

<span data-ttu-id="49605-158">來源：[Unit Testing versus Functional Tests](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html) (單元測試與功能測試)</span><span class="sxs-lookup"><span data-stu-id="49605-158">Source: [Unit Testing versus Functional Tests](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="49605-159">我喜歡說：「身為開發人員，我們有兩種失敗方式：以錯誤的方式建置東西，或建置錯誤的東西。」</span><span class="sxs-lookup"><span data-stu-id="49605-159">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="49605-160">單元測試確保您以正確的方式建置東西，而功能測試確保您建置正確的東西。</span><span class="sxs-lookup"><span data-stu-id="49605-160">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="49605-161">由於功能測試在系統層級上操作，因此可能需要一定程度的 UI 自動化。</span><span class="sxs-lookup"><span data-stu-id="49605-161">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="49605-162">與整合測試一樣，功能測試通常也會使用某種類的測試基礎結構。</span><span class="sxs-lookup"><span data-stu-id="49605-162">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="49605-163">這使其比單元和整合測試更慢且較不可靠。</span><span class="sxs-lookup"><span data-stu-id="49605-163">This makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="49605-164">功能測試的次數，只要足以確保系統會按照使用者的期望運作即可。</span><span class="sxs-lookup"><span data-stu-id="49605-164">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="49605-165">測試金字塔圖</span><span class="sxs-lookup"><span data-stu-id="49605-165">Testing Pyramid</span></span>

<span data-ttu-id="49605-166">Martin Fowler 撰寫了測試金字塔相關事項，其中的一個範例如圖 9-1 所示。</span><span class="sxs-lookup"><span data-stu-id="49605-166">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![](./media/image9-1.png)

<span data-ttu-id="49605-167">圖 9-1 測試金字塔圖</span><span class="sxs-lookup"><span data-stu-id="49605-167">Figure 9-1 Testing Pyramid</span></span>

<span data-ttu-id="49605-168">金字塔的不同圖層及其相對大小代表了不同類型的測試，以及您應該為應用程式撰寫的測試數量。</span><span class="sxs-lookup"><span data-stu-id="49605-168">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="49605-169">如您所見，建議以大型的單元測試作為基礎，由較小的整合測試層來支援，再加上一個更小的功能測試層。</span><span class="sxs-lookup"><span data-stu-id="49605-169">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="49605-170">理想情況下，每個圖層的測試只應能在該層中進行，而不能在較低層中充分進行。</span><span class="sxs-lookup"><span data-stu-id="49605-170">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="49605-171">在您嘗試決定需要在特定案例中使用哪種測試類型時，請記得測試金字塔。</span><span class="sxs-lookup"><span data-stu-id="49605-171">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="49605-172">測試的內容</span><span class="sxs-lookup"><span data-stu-id="49605-172">What to Test</span></span>

<span data-ttu-id="49605-173">對於沒有撰寫自動化測試經驗的開發人員來說，常見問題就是測試的內容。</span><span class="sxs-lookup"><span data-stu-id="49605-173">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="49605-174">測試條件式邏輯是很好的起點。</span><span class="sxs-lookup"><span data-stu-id="49605-174">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="49605-175">如您有任何能根據條件陳述式 (if-else、switch 等等) 而變更行為的方法，您就應該至少能進行一些測試，以確認某些情況下的正確行為。</span><span class="sxs-lookup"><span data-stu-id="49605-175">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, etc.), you should be able to come up at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="49605-176">如果您的程式碼有錯誤狀況，可透過程式碼撰寫至少一個「開心路徑」 (即沒有錯誤) 的測試，且至少一個「悲傷路徑」 (含有錯誤或非典型結果) 的測試，來確認您的應用程式在出現錯誤時的行為如預期。</span><span class="sxs-lookup"><span data-stu-id="49605-176">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="49605-177">最後，嘗試專注於測試可能失敗的事項，而不是專注於程式碼涵蓋範圍等指標。</span><span class="sxs-lookup"><span data-stu-id="49605-177">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="49605-178">一般來說，程式碼涵蓋範圍是多優於少。</span><span class="sxs-lookup"><span data-stu-id="49605-178">More code coverage is better than less, generally.</span></span> <span data-ttu-id="49605-179">但是，多一些以非常複雜且業務關鍵方法撰寫的程式碼，通常比僅僅為了改善測試程式碼涵蓋範圍指標而撰寫測試的自動屬性，還更具時間效益。</span><span class="sxs-lookup"><span data-stu-id="49605-179">However, writing a few more tests of a very complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="49605-180">組織測試專案</span><span class="sxs-lookup"><span data-stu-id="49605-180">Organizing Test Projects</span></span>

<span data-ttu-id="49605-181">可以使用最適合您的方式來組織測試專案。</span><span class="sxs-lookup"><span data-stu-id="49605-181">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="49605-182">依照類型 (單元測試、整合測試) 和測試內容 (依照專案、命名空間) 來分隔測試是不錯的做法。</span><span class="sxs-lookup"><span data-stu-id="49605-182">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="49605-183">此分隔該由單一測試專案中的資料夾組成，或是由多個測試專案組成，是設計上的決策。</span><span class="sxs-lookup"><span data-stu-id="49605-183">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="49605-184">單一專案是最簡單的，但針對有大量測試的大型專案，或為了能更容易執行不同的測試集，您可能需要有幾個不同的測試專案。</span><span class="sxs-lookup"><span data-stu-id="49605-184">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="49605-185">許多小組根據正在測試的專案來組織測試專案；對於具有許多專案的應用程式，這可能會導致大量測試專案，尤其是如果您仍然根據每個專案中的測試種類來分隔測試專案。</span><span class="sxs-lookup"><span data-stu-id="49605-185">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="49605-186">折衷方法是讓每個應用程式的每種測試都有一個專案，在測試專案中包含資料夾以指出正在測試的專案 (和類別)。</span><span class="sxs-lookup"><span data-stu-id="49605-186">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="49605-187">常用的方法是在 'src' 資料夾下組織應用程式專案，並在平行的 ‘tests' 資料夾下組織應用程式測試專案。</span><span class="sxs-lookup"><span data-stu-id="49605-187">A common approach is to organize the application projects under a ‘src' folder, and the application's test projects under a parallel ‘tests' folder.</span></span> <span data-ttu-id="49605-188">如果您覺得這樣的組織很有用，您可以在 Visual Studio 中建立相符的解決方案資料夾。</span><span class="sxs-lookup"><span data-stu-id="49605-188">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![](./media/image9-2.png)

<span data-ttu-id="49605-189">圖 9-2 解決方案中的測試組織</span><span class="sxs-lookup"><span data-stu-id="49605-189">Figure 9-2 Test organization in your solution</span></span>

<span data-ttu-id="49605-190">您可以使用您偏好的任何測試架構。</span><span class="sxs-lookup"><span data-stu-id="49605-190">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="49605-191">xUnit 架構運作良好，且用來寫入所有的 ASP.NET Core 和 EF Core 測試。</span><span class="sxs-lookup"><span data-stu-id="49605-191">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="49605-192">您可以使用圖 9-3 中的範本，或使用 dotnet new xunit 的 CLI，在 Visual Studio 中新增 xUnit 測試專案。</span><span class="sxs-lookup"><span data-stu-id="49605-192">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using dotnet new xunit.</span></span>

![](./media/image9-3.png)

<span data-ttu-id="49605-193">圖 9-3 在 Visual Studio 中新增 xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="49605-193">Figure 9-3 Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="49605-194">命名測試</span><span class="sxs-lookup"><span data-stu-id="49605-194">Test Naming</span></span>

<span data-ttu-id="49605-195">您應該以統一的方式來為測試命名，並以名稱來指出每項測試的用途。</span><span class="sxs-lookup"><span data-stu-id="49605-195">You should name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="49605-196">取得巨大成功的一種方法，是根據其正在測試的類別和方法來命名測試類別。</span><span class="sxs-lookup"><span data-stu-id="49605-196">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="49605-197">這會導致許多小測試類別，但可以非常清楚劃分每項測試的職責。</span><span class="sxs-lookup"><span data-stu-id="49605-197">This results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="49605-198">藉由設定測試類別名稱來識別要測試的類別和方法，測試方法名稱可用於指定要測試的行為。</span><span class="sxs-lookup"><span data-stu-id="49605-198">With the test class name set up to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="49605-199">這應該包含預期的行為，以及任何應該產生這種行為的輸入或假設。</span><span class="sxs-lookup"><span data-stu-id="49605-199">This should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="49605-200">測試名稱的一些範例：</span><span class="sxs-lookup"><span data-stu-id="49605-200">Some example test names:</span></span>

- <span data-ttu-id="49605-201">CatalogControllerGetImage.CallsImageServiceWithId</span><span class="sxs-lookup"><span data-stu-id="49605-201">CatalogControllerGetImage.CallsImageServiceWithId</span></span>

- <span data-ttu-id="49605-202">CatalogControllerGetImage.LogsWarningGivenImageMissingException</span><span class="sxs-lookup"><span data-stu-id="49605-202">CatalogControllerGetImage.LogsWarningGivenImageMissingException</span></span>

- <span data-ttu-id="49605-203">CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess</span><span class="sxs-lookup"><span data-stu-id="49605-203">CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess</span></span>

- <span data-ttu-id="49605-204">CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException</span><span class="sxs-lookup"><span data-stu-id="49605-204">CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException</span></span>

<span data-ttu-id="49605-205">此方法的變體，會結束每個含有 "Should" 的測試類別名稱，並稍微修改時態：</span><span class="sxs-lookup"><span data-stu-id="49605-205">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

- <span data-ttu-id="49605-206">CatalogControllerGetImage**Should**.**Call**ImageServiceWithId</span><span class="sxs-lookup"><span data-stu-id="49605-206">CatalogControllerGetImage**Should**.**Call**ImageServiceWithId</span></span>

- <span data-ttu-id="49605-207">CatalogControllerGetImage**Should**.**Log**WarningGivenImageMissingException</span><span class="sxs-lookup"><span data-stu-id="49605-207">CatalogControllerGetImage**Should**.**Log**WarningGivenImageMissingException</span></span>

<span data-ttu-id="49605-208">有些小組會認為第二種命名方法更清楚，只是略為冗長。</span><span class="sxs-lookup"><span data-stu-id="49605-208">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="49605-209">無論如何，請嘗試使用能深入了解測試行為的命名慣例；如此，當一或多項測試失敗時，從其名稱即可明顯看出是哪些案例失敗。</span><span class="sxs-lookup"><span data-stu-id="49605-209">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="49605-210">請避免含糊不清地命名您的測試，例如 ControllerTests.Test1，因為在測試結果中看到時並不會提供任何價值。</span><span class="sxs-lookup"><span data-stu-id="49605-210">Avoid naming you tests vaguely, such as ControllerTests.Test1, as these offer no value when you see them in test results.</span></span>

<span data-ttu-id="49605-211">如果您遵循如上所述會產生許多小型測試類別的命名慣例，建議使用資料夾和命名空間來進一步組織測試。</span><span class="sxs-lookup"><span data-stu-id="49605-211">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="49605-212">圖 9-4 顯示在幾個測試專案中按資料夾組織測試的一種方法。</span><span class="sxs-lookup"><span data-stu-id="49605-212">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![](./media/image9-4.png)

<span data-ttu-id="49605-213">**圖 9-4。**</span><span class="sxs-lookup"><span data-stu-id="49605-213">**Figure 9-4.**</span></span> <span data-ttu-id="49605-214">根據正在測試的類別，按資料夾來組織測試類別。</span><span class="sxs-lookup"><span data-stu-id="49605-214">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="49605-215">當然，如果一個特定的應用程式類別中有很多方法正在進行測試 (且因此有許多測試類別)，將其放在與應用程式類別相對應的資料夾中，是有意義的。</span><span class="sxs-lookup"><span data-stu-id="49605-215">Of course, if a particular application class has many methods being tested (and thus many test classes), it may make sense to place these in a folder corresponding to the application class.</span></span> <span data-ttu-id="49605-216">這個組織與您如何將檔案組織到別處的資料夾中沒有區別。</span><span class="sxs-lookup"><span data-stu-id="49605-216">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="49605-217">如果在包含許多其他檔案的資料夾中有三或四個以上相關檔案，將其移到其本身的子資料夾通常會很有幫助。</span><span class="sxs-lookup"><span data-stu-id="49605-217">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="49605-218">對 ASP.NET Core 應用程式進行單元測試</span><span class="sxs-lookup"><span data-stu-id="49605-218">Unit Testing ASP.NET Core Apps</span></span>

<span data-ttu-id="49605-219">在設計良好的 ASP.NET Core 應用程式中，大部分的複雜性和商務邏輯都會封裝在商務實體與各種服務中。</span><span class="sxs-lookup"><span data-stu-id="49605-219">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="49605-220">ASP.NET Core MVC 應用程式本身及其控制器、篩選器、檢視模型和檢視，應只需要很少量的單元測試。</span><span class="sxs-lookup"><span data-stu-id="49605-220">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require very few unit tests.</span></span> <span data-ttu-id="49605-221">指定動作的許多功能，大多在動作方法本身之外。</span><span class="sxs-lookup"><span data-stu-id="49605-221">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="49605-222">使用單元測試無法有效測試路由或全域錯誤處理是否運作正常。</span><span class="sxs-lookup"><span data-stu-id="49605-222">Testing whether routing works correctly, or global error handling, cannot be done effectively with a unit test.</span></span> <span data-ttu-id="49605-223">同樣地，任何篩選器 (包含模型驗證和授權，以及授權篩選條件) 都不能進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="49605-223">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested.</span></span> <span data-ttu-id="49605-224">如果沒有這些行為來源，大多數行動方法應十分微小，會將其大部分工作委派給可獨立於使用它們的控制器來進行測試之服務。</span><span class="sxs-lookup"><span data-stu-id="49605-224">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="49605-225">有時您需要重構程式碼才能進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="49605-225">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="49605-226">通常這包括識別抽象概念與使用相依性插入來存取您想要測試的程式碼中之抽象概念，而不是直接針對基礎結構進行編碼。</span><span class="sxs-lookup"><span data-stu-id="49605-226">Frequently this involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="49605-227">例如，請考慮這個簡單的動作方法，來顯示影像：</span><span class="sxs-lookup"><span data-stu-id="49605-227">For example, consider this simple action method for displaying images:</span></span>

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

<span data-ttu-id="49605-228">對此方法進行單元測試很困難，因為它直接相依於 System.IO.File，用來從檔案系統中進行讀取。</span><span class="sxs-lookup"><span data-stu-id="49605-228">Unit testing this method is made difficult by its direct dependency on System.IO.File, which it uses to read from the file system.</span></span> <span data-ttu-id="49605-229">您可以測試此行為以確保其按預期運作，但對實際檔案執行此操作的是整合測試。</span><span class="sxs-lookup"><span data-stu-id="49605-229">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="49605-230">值得注意的是，您無法測試此方法的路由，但您很快就會了解如何透過功能測試來執行此作業。</span><span class="sxs-lookup"><span data-stu-id="49605-230">It's worth noting you can't test this method's route – you'll see how to do this with a functional test shortly.</span></span>

<span data-ttu-id="49605-231">如果您不能直接對檔案系統行為進行單元測試，且無法測試路由，那麼需要測試哪些內容？</span><span class="sxs-lookup"><span data-stu-id="49605-231">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="49605-232">在重構使單元測試成為可能之後，您可能會發現一些測試案例和遺失的行為，例如錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="49605-232">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="49605-233">找不到檔案時，該方法會執行什麼操作？</span><span class="sxs-lookup"><span data-stu-id="49605-233">What does the method do when a file isn't found?</span></span> <span data-ttu-id="49605-234">它應該做什麼？</span><span class="sxs-lookup"><span data-stu-id="49605-234">What should it do?</span></span> <span data-ttu-id="49605-235">在此範例中，重構的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="49605-235">In this example, the refactored method looks like this:</span></span>

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

<span data-ttu-id="49605-236">\_記錄器和 \_imageService 會同時插入作為相依性。</span><span class="sxs-lookup"><span data-stu-id="49605-236">The \_logger and \_imageService are both injected as dependencies.</span></span> <span data-ttu-id="49605-237">現在您可以測試將傳遞給操作方法的相同識別碼傳遞給 \_imageService，且產生之位元組會作為 FileResult 的一部分傳回。</span><span class="sxs-lookup"><span data-stu-id="49605-237">Now you can test that the same id that is passed to the action method is passed to the \_imageService, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="49605-238">您也可以測試錯誤記錄是否按預期進行；假設這是重要的應用程式行為 (意即，不僅僅是開發人員用於診斷問題的臨時程式碼)，如果影像遺失，則傳回 NotFound 結果。</span><span class="sxs-lookup"><span data-stu-id="49605-238">You can also test that error logging is happening as expected, and that a NotFound result is returned if the image is missing, assuming this is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="49605-239">實際的檔案邏輯已移至另一個實作服務中，並且已擴大為針對遺失檔案情況來傳回應用程式特定的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="49605-239">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="49605-240">您可以使用整合測試來獨立測試此實作。</span><span class="sxs-lookup"><span data-stu-id="49605-240">You can test this implementation independently, using an integration test.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="49605-241">對 ASP.NET Core 應用程式進行單元測試</span><span class="sxs-lookup"><span data-stu-id="49605-241">Integration Testing ASP.NET Core Apps</span></span>

<span data-ttu-id="49605-242">此服務使用 IHostingEnvironment，就像 CatalogController 程式碼在重構為個別的服務之前一樣。</span><span class="sxs-lookup"><span data-stu-id="49605-242">This service uses the IHostingEnvironment, just as the CatalogController code did before it was refactored into a separate service.</span></span> <span data-ttu-id="49605-243">由於這是使用 IHostingEnvironment 之控制器中唯一的程式碼，因此已從 CatalogController 的建構函式中移除該相依性。</span><span class="sxs-lookup"><span data-stu-id="49605-243">Since this was the only code in the controller that used IHostingEnvironment, that dependency was removed from CatalogController's constructor.</span></span>

<span data-ttu-id="49605-244">若要測試此服務是否正常運作，您需要建立一個已知的測試影像檔，並驗證該服務會在指定特定輸入的情況下將其傳回。</span><span class="sxs-lookup"><span data-stu-id="49605-244">To test that this service works correctly, you need to create a known test image file and verify that the service returns it given a specific input.</span></span> <span data-ttu-id="49605-245">請注意不要在您實際想要測試的行為上使用模擬物件 (在此情況下，從檔案系統讀取)。</span><span class="sxs-lookup"><span data-stu-id="49605-245">You should take care not to use mock objects on the behavior you actually want to test (in this case, reading from the file system).</span></span> <span data-ttu-id="49605-246">但是，模擬物件可能仍然有助於設定整合測試。</span><span class="sxs-lookup"><span data-stu-id="49605-246">However, mock objects may still be useful to set up integration tests.</span></span> <span data-ttu-id="49605-247">在此情況下，您可以模擬 IHostingEnvironment，使其 ContentRootPath 指向您要用於測試影像的資料夾。</span><span class="sxs-lookup"><span data-stu-id="49605-247">In this case, you can mock IHostingEnvironment so that its ContentRootPath points to the folder you're going to use for your test image.</span></span> <span data-ttu-id="49605-248">完整運作的整合測試類別如下所示：</span><span class="sxs-lookup"><span data-stu-id="49605-248">The complete working integration test class is shown here:</span></span>

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
> <span data-ttu-id="49605-249">測試本身非常簡單，大部分程式碼對設定系統和建立測試基礎結構 (在此案例中，從磁碟讀取實際檔案) 是必需的。</span><span class="sxs-lookup"><span data-stu-id="49605-249">that the test itself is very simple – the bulk of the code is necessary to configure the system and create the testing infrastructure (in this case, an actual file to be read from disk).</span></span> <span data-ttu-id="49605-250">這對整合測試來說很常見，通常需要比單元測試更複雜的設定工作。</span><span class="sxs-lookup"><span data-stu-id="49605-250">This is typical for integration tests, which often require more complex setup work than unit tests.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="49605-251">對 ASP.NET Core 應用程式進行功能測試</span><span class="sxs-lookup"><span data-stu-id="49605-251">Functional Testing ASP.NET Core Apps</span></span>

<span data-ttu-id="49605-252">對於 ASP.NET Core 應用程式，TestServer 類別可使功能測試很容易撰寫。</span><span class="sxs-lookup"><span data-stu-id="49605-252">For ASP.NET Core applications, the TestServer class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="49605-253">就像您通常為應用程式所做的一樣，可使用 WebHostBuilder 來設定 TestServer。</span><span class="sxs-lookup"><span data-stu-id="49605-253">You configure a TestServer using a WebHostBuilder, just as you normally do for your application.</span></span> <span data-ttu-id="49605-254">這個 WebHostBuilder 應該像應用程式的真實主機一樣設定，但是您可以修改其任何層面以使測試更為容易。</span><span class="sxs-lookup"><span data-stu-id="49605-254">This WebHostBuilder should be configured just like your application's real host, but you can modify any aspects of it that make testing easier.</span></span> <span data-ttu-id="49605-255">大多數情況下，您會在很多測試案例中重複使用相同的 TestServer，因此您可以將其封裝在可重複使用的方法中 (也許在基底類別)：</span><span class="sxs-lookup"><span data-stu-id="49605-255">Most of the time, you'll reuse the same TestServer for many test cases, so you can encapsulate it in a reusable method (perhaps in a base class):</span></span>

```csharp
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
        .UseStartup<Startup>();
        var server = new TestServer(builder);
        var client = server.CreateClient();
        return client;
    }
}
```

<span data-ttu-id="49605-256">GetProjectPath 方法只會將實體路徑傳回至 Web 專案 (下載解決方案範例)。</span><span class="sxs-lookup"><span data-stu-id="49605-256">The GetProjectPath method simply returns the physical path to the web project (download sample solution).</span></span> <span data-ttu-id="49605-257">在此情況下，WebHostBuilder 僅會指定 Web 應用程式的內容根目錄，並參考真實 Web 應用程式使用的相同啟動類別。</span><span class="sxs-lookup"><span data-stu-id="49605-257">The WebHostBuilder in this case simply specifies where the content root for the web application is, and references the same Startup class the real web application uses.</span></span> <span data-ttu-id="49605-258">若要使用 TestServer，請使用標準的 System.Net.HttpClient 類型對其發出要求。</span><span class="sxs-lookup"><span data-stu-id="49605-258">To work with the TestServer, you use the standard System.Net.HttpClient type to make requests to it.</span></span> <span data-ttu-id="49605-259">TestServer 會公開一個有用的 CreateClient 方法，該方法提供了一個預先設定的用戶端，而該用戶端已準備好向在 TestServer 上執行的應用程式發出要求。</span><span class="sxs-lookup"><span data-stu-id="49605-259">TestServer exposes a helpful CreateClient method that provides a pre-configured client that is ready to make requests to the application running on the TestServer.</span></span> <span data-ttu-id="49605-260">在為您的 ASP.NET Core 應用程式撰寫功能測試時，您可以使用此用戶端 (在上述的基本測試中設定為受保護的\_用戶端成員）：</span><span class="sxs-lookup"><span data-stu-id="49605-260">You use this client (set to the protected \_client member on the base test above) when writing functional tests for your ASP.NET Core application:</span></span>

```csharp
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

<span data-ttu-id="49605-261">此功能測試將執行完整的 ASP.NET Core MVC 應用程式堆疊，包括可能存在的所有中介軟體、篩選器、繫結器等等。</span><span class="sxs-lookup"><span data-stu-id="49605-261">This functional test exercises the full ASP.NET Core MVC application stack, including all middleware, filters, binders, etc. that may be in place.</span></span> <span data-ttu-id="49605-262">會驗證指定路由 ("/catalog/pic/1") 傳回已知位置檔案預期的位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="49605-262">It verifies that a given route ("/catalog/pic/1") returns the expected byte array for a file in a known location.</span></span> <span data-ttu-id="49605-263">因並未設定真實的網頁伺服器，所以避免了使用真實的網頁伺服器進行測試之脆弱度 (例如防火牆設定的問題)。</span><span class="sxs-lookup"><span data-stu-id="49605-263">It does so without setting up a real web server, and so avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="49605-264">針對 TestServer 執行的功能測試通常比整合與單元測試要慢，但比在網路上執行測試之網頁伺服器的測試要快得多。</span><span class="sxs-lookup"><span data-stu-id="49605-264">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="49605-265">[上一頁](work-with-data-in-asp-net-core-apps.md)
[下一頁](development-process-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="49605-265">[Previous](work-with-data-in-asp-net-core-apps.md)
[Next](development-process-for-azure.md)</span></span>
