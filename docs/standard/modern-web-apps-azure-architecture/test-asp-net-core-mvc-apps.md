---
title: "測試 ASP.NET Core MVC 應用程式"
description: "使用 ASP.NET Core 和 Azure 的現代化 Web 應用程式架構設計人員 |測試 ASP.NET Core MVC 應用程式"
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d23d0accc33fb8335dff602d6e1d6c8689972906
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="3b87a-103">測試 ASP.NET Core MVC 應用程式</span><span class="sxs-lookup"><span data-stu-id="3b87a-103">Test ASP.NET Core MVC Apps</span></span>

> <span data-ttu-id="3b87a-104">_"如果您不喜歡單元測試您的產品，最有可能您的客戶不會想要予以測試，請。 」_</span><span class="sxs-lookup"><span data-stu-id="3b87a-104">_"If you don't like unit testing your product, most likely your customers won't like to test it, either."_</span></span>
> <span data-ttu-id="3b87a-105">_-匿名-</span><span class="sxs-lookup"><span data-stu-id="3b87a-105">_- Anonymous-</span></span>

## <a name="summary"></a><span data-ttu-id="3b87a-106">總結</span><span class="sxs-lookup"><span data-stu-id="3b87a-106">Summary</span></span>

<span data-ttu-id="3b87a-107">任何複雜度的軟體可能會非預期的方式，以回應變更失敗。</span><span class="sxs-lookup"><span data-stu-id="3b87a-107">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="3b87a-108">因此，測試進行變更之後，才能幾乎連最簡單的 （或最不重要的） 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3b87a-108">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="3b87a-109">手動測試是最慢的作業，最可靠且成本最高的方式測試軟體。</span><span class="sxs-lookup"><span data-stu-id="3b87a-109">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="3b87a-110">不幸的是，如果應用程式都不可測試的設計，它可以是唯一可用的方法。</span><span class="sxs-lookup"><span data-stu-id="3b87a-110">Unfortunately, if applications are not designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="3b87a-111">撰寫架構原則配置的下列章節 X 中的應用程式應該是單元測試和 ASP.NET Core 應用程式支援自動化的整合和功能測試以及。</span><span class="sxs-lookup"><span data-stu-id="3b87a-111">Applications written following the architectural principles laid out in chapter X should be unit testable, and ASP.NET Core applications support automated integration and functional testing as well.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="3b87a-112">類型的自動化測試</span><span class="sxs-lookup"><span data-stu-id="3b87a-112">Kinds of Automated Tests</span></span>

<span data-ttu-id="3b87a-113">有許多種類的軟體應用程式的自動化測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-113">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="3b87a-114">最簡單的最低層級的測試是單元測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-114">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="3b87a-115">在稍高等級有整合測試與功能測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-115">At a slightly higher level there are integration tests and functional tests.</span></span> <span data-ttu-id="3b87a-116">其他種類的測試，例如 UI 測試、 負載測試、 壓力測試和煙霧測試中，已超出本文的範圍。</span><span class="sxs-lookup"><span data-stu-id="3b87a-116">Other kinds of tests, like UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="3b87a-117">單元測試</span><span class="sxs-lookup"><span data-stu-id="3b87a-117">Unit Tests</span></span>

<span data-ttu-id="3b87a-118">單元測試中測試您的應用程式邏輯的單一組件。</span><span class="sxs-lookup"><span data-stu-id="3b87a-118">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="3b87a-119">其中一個可以進一步說明藉由列出的一些作業，它不是。</span><span class="sxs-lookup"><span data-stu-id="3b87a-119">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="3b87a-120">單元測試不會測試的相依性或基礎結構-何種整合測試的程式碼正常運作的方式。</span><span class="sxs-lookup"><span data-stu-id="3b87a-120">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="3b87a-121">單元測試不會測試您的程式碼也會在寫入架構，您應該假設它的運作或，如果您覺得不、 提報 bug 和程式碼因應措施。</span><span class="sxs-lookup"><span data-stu-id="3b87a-121">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="3b87a-122">在記憶體和處理序中，會完全執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-122">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="3b87a-123">它不會與檔案系統、 網路或資料庫進行通訊。</span><span class="sxs-lookup"><span data-stu-id="3b87a-123">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="3b87a-124">單元測試應該只測試您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3b87a-124">Unit tests should only test your code.</span></span>

<span data-ttu-id="3b87a-125">單元測試，其會測試您的程式碼，不含外部相依性，將單一單位的事實必定應執行速度非常快。</span><span class="sxs-lookup"><span data-stu-id="3b87a-125">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely quickly.</span></span> <span data-ttu-id="3b87a-126">因此，您應該能夠在幾秒鐘的時間執行的數百個單元測試的測試套件。</span><span class="sxs-lookup"><span data-stu-id="3b87a-126">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="3b87a-127">它們經常執行，在理想情況下再每個推送至共用原始檔控制儲存機制中，並確實與每個自動化建置您的組建伺服器上。</span><span class="sxs-lookup"><span data-stu-id="3b87a-127">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="3b87a-128">整合測試</span><span class="sxs-lookup"><span data-stu-id="3b87a-128">Integration Tests</span></span>

<span data-ttu-id="3b87a-129">雖然它是個不錯的主意，封裝會與基礎結構，例如資料庫和檔案系統互動的程式碼，您仍會有部分的程式碼，您可能會想要測試它。</span><span class="sxs-lookup"><span data-stu-id="3b87a-129">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="3b87a-130">此外，您應該確認您的程式碼層級互動如預期般完全解析您的應用程式相依性時。</span><span class="sxs-lookup"><span data-stu-id="3b87a-130">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="3b87a-131">這是整合測試的責任。</span><span class="sxs-lookup"><span data-stu-id="3b87a-131">This is the responsibility of integration tests.</span></span> <span data-ttu-id="3b87a-132">整合測試通常速度較慢且更難以設定比單元測試，因為它們通常取決於外部相依性和基礎結構。</span><span class="sxs-lookup"><span data-stu-id="3b87a-132">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="3b87a-133">因此，您應該避免測試可能是整合測試中的單元測試的測試中的項目。</span><span class="sxs-lookup"><span data-stu-id="3b87a-133">Thus, you should avoid testing things that could be tests with unit tests in integration tests.</span></span> <span data-ttu-id="3b87a-134">如果您可以測試特定的案例與單元測試，您應該測試它與單元測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-134">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="3b87a-135">如果無法處理，請考慮使用整合測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-135">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="3b87a-136">整合測試時，通常會有更複雜的設定和清除程序比單元測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-136">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="3b87a-137">例如，整合測試，會針對實際的資料庫會需要能夠讓資料庫返回已知的狀態，每個測試回合之前。</span><span class="sxs-lookup"><span data-stu-id="3b87a-137">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="3b87a-138">加入新的測試和實際執行資料庫結構描述的發展，這些測試指令碼通常會成長的大小和複雜度。</span><span class="sxs-lookup"><span data-stu-id="3b87a-138">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="3b87a-139">在許多大型系統，很適合簽入變更到共用的原始檔控制之前，開發人員工作站上執行完整的整合測試套件。</span><span class="sxs-lookup"><span data-stu-id="3b87a-139">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="3b87a-140">在這些情況下，可能會在組建伺服器上執行整合測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-140">In these cases, integration tests may be run on a build server.</span></span>

<span data-ttu-id="3b87a-141">LocalFileImageService 實作類別會實作用於擷取和傳回的映像檔的位元組數從指定的 id 的特定資料夾的邏輯：</span><span class="sxs-lookup"><span data-stu-id="3b87a-141">The LocalFileImageService implementation class implements the logic for fetching and returning the bytes of an image file from a particular folder given an id:</span></span>

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

### <a name="functional-tests"></a><span data-ttu-id="3b87a-142">功能測試</span><span class="sxs-lookup"><span data-stu-id="3b87a-142">Functional Tests</span></span>

<span data-ttu-id="3b87a-143">整合測試的開發人員，以驗證系統的某些元件可正確地同時角度從寫入。</span><span class="sxs-lookup"><span data-stu-id="3b87a-143">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="3b87a-144">功能測試會寫入從使用者的觀點來看，並確認系統根據其需求的正確性。</span><span class="sxs-lookup"><span data-stu-id="3b87a-144">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="3b87a-145">下列摘錄中提供比喻如何思考功能測試，相較於單元測試：</span><span class="sxs-lookup"><span data-stu-id="3b87a-145">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="3b87a-146">「 系統的開發多次被比擬為一棟房子的建置。</span><span class="sxs-lookup"><span data-stu-id="3b87a-146">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="3b87a-147">雖然這項類比帶並不是相當正確，我們可以延伸該架構基於的了解單元測試和功能的測試之間的差異。</span><span class="sxs-lookup"><span data-stu-id="3b87a-147">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="3b87a-148">類似於瀏覽一棟房子建構網站建置 inspector 單元測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-148">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="3b87a-149">他會著重於各種內部房屋、 框架、 電力、 配管，等等的基礎的系統。</span><span class="sxs-lookup"><span data-stu-id="3b87a-149">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="3b87a-150">他可確保房屋的組件會正確運作，並安全地，也就是符合建置程式碼 （測試）。</span><span class="sxs-lookup"><span data-stu-id="3b87a-150">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="3b87a-151">在此案例中的功能測試會類似於瀏覽這個相同的建構網站家長。</span><span class="sxs-lookup"><span data-stu-id="3b87a-151">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="3b87a-152">他會假設內部系統將會適當地運作，建置偵測器正在執行他的工作。</span><span class="sxs-lookup"><span data-stu-id="3b87a-152">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="3b87a-153">家長著重於以及它進行像是存在於此房子。</span><span class="sxs-lookup"><span data-stu-id="3b87a-153">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="3b87a-154">他關心房子的外觀、 各種聊天室舒適的大小、 房子是否符合需求的系列，都適合攔截早上 sun 中的視窗。</span><span class="sxs-lookup"><span data-stu-id="3b87a-154">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="3b87a-155">家長房子上執行功能測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-155">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="3b87a-156">他有使用者的觀點來看。</span><span class="sxs-lookup"><span data-stu-id="3b87a-156">He has the user's perspective.</span></span> <span data-ttu-id="3b87a-157">建置偵測器房子上執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-157">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="3b87a-158">他有產生器 」 的檢視方塊 」。</span><span class="sxs-lookup"><span data-stu-id="3b87a-158">He has the builder's perspective."</span></span>

<span data-ttu-id="3b87a-159">來源：[單元測試與功能測試](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span><span class="sxs-lookup"><span data-stu-id="3b87a-159">Source: [Unit Testing versus Functional Tests](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="3b87a-160">我喜歡說 「 身為開發人員，我們在兩種方式會失敗： 我們建置的項目不正確，或我們建置錯誤的項目。 」</span><span class="sxs-lookup"><span data-stu-id="3b87a-160">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="3b87a-161">單元測試，確保您要建置的項目權限;功能測試，請確定您在建立正確的事。</span><span class="sxs-lookup"><span data-stu-id="3b87a-161">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="3b87a-162">功能測試是在系統層級上操作，因為它們可能會需要某種程度的 UI 自動化。</span><span class="sxs-lookup"><span data-stu-id="3b87a-162">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="3b87a-163">整合測試，例如它們通常會使用某種類型的測試基礎結構。</span><span class="sxs-lookup"><span data-stu-id="3b87a-163">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="3b87a-164">這讓它們更慢，而且比單元和整合測試更不可靠。</span><span class="sxs-lookup"><span data-stu-id="3b87a-164">This makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="3b87a-165">您應該僅具有許多功能測試，因為您必須確定系統如預期的使用者行為。</span><span class="sxs-lookup"><span data-stu-id="3b87a-165">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="3b87a-166">測試金字塔圖</span><span class="sxs-lookup"><span data-stu-id="3b87a-166">Testing Pyramid</span></span>

<span data-ttu-id="3b87a-167">Martin Fowler 寫入有關測試金字塔圖，顯示的範例圖 9-1。</span><span class="sxs-lookup"><span data-stu-id="3b87a-167">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![](./media/image9-1.png)

<span data-ttu-id="3b87a-168">圖 9 1 測試金字塔圖</span><span class="sxs-lookup"><span data-stu-id="3b87a-168">Figure 9-1 Testing Pyramid</span></span>

<span data-ttu-id="3b87a-169">金字塔圖和其相對的大小不同的圖層代表不同種類的測試和多少您應該撰寫應用程式。</span><span class="sxs-lookup"><span data-stu-id="3b87a-169">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="3b87a-170">如您所見，建議是讓單元測試，更小的圖層的功能測試較小的整合測試，圖層所支援的大型基底。</span><span class="sxs-lookup"><span data-stu-id="3b87a-170">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="3b87a-171">每個圖層應該在理想情況下只有測試中的低層級無法充分執行。</span><span class="sxs-lookup"><span data-stu-id="3b87a-171">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="3b87a-172">當您嘗試決定您需要在特定案例的測試類型時，請記住測試的金字塔。</span><span class="sxs-lookup"><span data-stu-id="3b87a-172">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="3b87a-173">要測試的項目</span><span class="sxs-lookup"><span data-stu-id="3b87a-173">What to Test</span></span>

<span data-ttu-id="3b87a-174">接下來的開發人員會熟悉撰寫自動化的測試的常見的問題與要測試的項目。</span><span class="sxs-lookup"><span data-stu-id="3b87a-174">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="3b87a-175">若要測試的條件式邏輯是很好的起點。</span><span class="sxs-lookup"><span data-stu-id="3b87a-175">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="3b87a-176">您有任何變更會根據條件陳述式的行為的方法如果 else，切換 (等），您應該能夠出現至少有幾個確認特定條件的正確行為的測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-176">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, etc.), you should be able to come up at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="3b87a-177">如果您的程式碼有錯誤狀況，最好確認應用程式的行為如預期般遇到錯誤時寫入至少一個測試執行程式碼 」 高興路徑 」 （未出現任何錯誤），以及至少一個測試，「 悲傷路徑 」 （具有錯誤或非典型的結果）。</span><span class="sxs-lookup"><span data-stu-id="3b87a-177">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="3b87a-178">最後，請嘗試將焦點放在測試，可能會失敗的項目，而不是將焦點放在計量，例如程式碼涵蓋範圍。</span><span class="sxs-lookup"><span data-stu-id="3b87a-178">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="3b87a-179">多個程式碼涵蓋範圍通常是優於少。</span><span class="sxs-lookup"><span data-stu-id="3b87a-179">More code coverage is better than less, generally.</span></span> <span data-ttu-id="3b87a-180">不過，撰寫非常複雜，而且業務關鍵方法的一些詳細測試通常是利用時間比撰寫測試的 auto 屬性只是為了改善測試程式碼涵蓋範圍的度量。</span><span class="sxs-lookup"><span data-stu-id="3b87a-180">However, writing a few more tests of a very complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="3b87a-181">組織測試專案</span><span class="sxs-lookup"><span data-stu-id="3b87a-181">Organizing Test Projects</span></span>

<span data-ttu-id="3b87a-182">可以組織測試專案，不過您最佳的運作方式。</span><span class="sxs-lookup"><span data-stu-id="3b87a-182">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="3b87a-183">最好分隔測試類型 （整合測試中的 單元測試），以及藉由測試 （藉由命名空間的專案）。</span><span class="sxs-lookup"><span data-stu-id="3b87a-183">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="3b87a-184">中的單一測試專案或多個測試專案的資料夾是否包含這項分隔是設計的決策。</span><span class="sxs-lookup"><span data-stu-id="3b87a-184">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="3b87a-185">其中一個專案是最簡單，但用於大型專案中使用許多測試，或是為了更輕鬆地執行不同的測試集，您可能想要有數個不同的測試專案。</span><span class="sxs-lookup"><span data-stu-id="3b87a-185">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="3b87a-186">許多小組來組織根據他們所測試，其中有多個專案的應用程式可能會導致大量的測試專案中，特別是如果您仍將分解這些根據種類的測試會在每個專案的專案的測試專案。</span><span class="sxs-lookup"><span data-stu-id="3b87a-186">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="3b87a-187">洩露方法是讓每種測試，每個應用程式，以指出要測試的專案 （和類別） 的測試專案內的資料夾與一個專案。</span><span class="sxs-lookup"><span data-stu-id="3b87a-187">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="3b87a-188">常見的作法是組織 'src' 資料夾下的應用程式專案和平行的測試' 資料夾下的應用程式的測試專案。</span><span class="sxs-lookup"><span data-stu-id="3b87a-188">A common approach is to organize the application projects under a ‘src' folder, and the application's test projects under a parallel ‘tests' folder.</span></span> <span data-ttu-id="3b87a-189">如果您發現此組織很有用，您可以在 Visual Studio 中，建立相符的方案資料夾。</span><span class="sxs-lookup"><span data-stu-id="3b87a-189">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![](./media/image9-2.png)

<span data-ttu-id="3b87a-190">圖 9 2 測試組織方案中</span><span class="sxs-lookup"><span data-stu-id="3b87a-190">Figure 9-2 Test organization in your solution</span></span>

<span data-ttu-id="3b87a-191">您可以使用任何您偏好的測試架構。</span><span class="sxs-lookup"><span data-stu-id="3b87a-191">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="3b87a-192">XUnit 架構可正常運作，就是，已用來撰寫所有 ASP.NET Core 和 EF 核心的測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-192">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="3b87a-193">您可以使用顯示在圖 9-3，或從使用 dotnet 新 xunit CLI 範本的 Visual Studio 中加入 xUnit 測試專案。</span><span class="sxs-lookup"><span data-stu-id="3b87a-193">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using dotnet new xunit.</span></span>

![](./media/image9-3.png)

<span data-ttu-id="3b87a-194">圖 9-3 新增 xUnit Visual Studio 中的測試專案</span><span class="sxs-lookup"><span data-stu-id="3b87a-194">Figure 9-3 Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="3b87a-195">測試命名</span><span class="sxs-lookup"><span data-stu-id="3b87a-195">Test Naming</span></span>

<span data-ttu-id="3b87a-196">您應該指出每項測試用途的名稱與命名一致的方式，測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-196">You should name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="3b87a-197">我有很棒的成功，但的其中一個方法是根據類別和他們所測試的方法名稱測試類別。</span><span class="sxs-lookup"><span data-stu-id="3b87a-197">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="3b87a-198">這會導致許多小型測試類別，但它可以非常清楚什麼每項測試會負責。</span><span class="sxs-lookup"><span data-stu-id="3b87a-198">This results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="3b87a-199">使用測試類別名稱設定以指定的類別和方法，以進行測試，測試方法名稱可用來指定要測試的行為。</span><span class="sxs-lookup"><span data-stu-id="3b87a-199">With the test class name set up to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="3b87a-200">這應該包含預期的行為與任何輸入或應該產生此行為的假設。</span><span class="sxs-lookup"><span data-stu-id="3b87a-200">This should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="3b87a-201">一些範例測試名稱中：</span><span class="sxs-lookup"><span data-stu-id="3b87a-201">Some example test names:</span></span>

-   <span data-ttu-id="3b87a-202">CatalogControllerGetImage.CallsImageServiceWithId</span><span class="sxs-lookup"><span data-stu-id="3b87a-202">CatalogControllerGetImage.CallsImageServiceWithId</span></span>

-   <span data-ttu-id="3b87a-203">CatalogControllerGetImage.LogsWarningGivenImageMissingException</span><span class="sxs-lookup"><span data-stu-id="3b87a-203">CatalogControllerGetImage.LogsWarningGivenImageMissingException</span></span>

-   <span data-ttu-id="3b87a-204">CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess</span><span class="sxs-lookup"><span data-stu-id="3b87a-204">CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess</span></span>

-   <span data-ttu-id="3b87a-205">CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException</span><span class="sxs-lookup"><span data-stu-id="3b87a-205">CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException</span></span>

<span data-ttu-id="3b87a-206">這種方法的變化會結束 「 應該 」 與每個測試類別名稱，並稍微修改時態：</span><span class="sxs-lookup"><span data-stu-id="3b87a-206">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

-   <span data-ttu-id="3b87a-207">CatalogControllerGetImage**Should**.**Call**ImageServiceWithId</span><span class="sxs-lookup"><span data-stu-id="3b87a-207">CatalogControllerGetImage**Should**.**Call**ImageServiceWithId</span></span>

-   <span data-ttu-id="3b87a-208">CatalogControllerGetImage**Should**.**Log**WarningGivenImageMissingException</span><span class="sxs-lookup"><span data-stu-id="3b87a-208">CatalogControllerGetImage**Should**.**Log**WarningGivenImageMissingException</span></span>

<span data-ttu-id="3b87a-209">有些小組尋找第二個的命名方式更清楚，但是稍微更多詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3b87a-209">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="3b87a-210">在任何情況下，嘗試使用提供深入了解測試的行為，使用命名慣例，如此當一或多個測試失敗時，它是明顯來自已失敗何種情況下，其名稱。</span><span class="sxs-lookup"><span data-stu-id="3b87a-210">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="3b87a-211">避免命名您的測試大致，例如 ControllerTests.Test1，這些都會提供任何值，當您在測試結果中看到。</span><span class="sxs-lookup"><span data-stu-id="3b87a-211">Avoid naming you tests vaguely, such as ControllerTests.Test1, as these offer no value when you see them in test results.</span></span>

<span data-ttu-id="3b87a-212">如果您遵循命名慣例，如上述，會產生許多小型測試類別，最好以進一步組織您的測試使用資料夾和命名空間。</span><span class="sxs-lookup"><span data-stu-id="3b87a-212">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="3b87a-213">圖 9-4 顯示組織內數個測試專案的資料夾來測試的其中一個方法。</span><span class="sxs-lookup"><span data-stu-id="3b87a-213">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![](./media/image9-4.png)

<span data-ttu-id="3b87a-214">**圖 9-4。**</span><span class="sxs-lookup"><span data-stu-id="3b87a-214">**Figure 9-4.**</span></span> <span data-ttu-id="3b87a-215">組織測試的類別為基礎的資料夾來測試類別。</span><span class="sxs-lookup"><span data-stu-id="3b87a-215">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="3b87a-216">當然，如果特定應用程式類別有多正在測試的方法 （且因此有許多測試類別），可能會更有意義放置這些資料夾對應至應用程式類別中。</span><span class="sxs-lookup"><span data-stu-id="3b87a-216">Of course, if a particular application class has many methods being tested (and thus many test classes), it may make sense to place these in a folder corresponding to the application class.</span></span> <span data-ttu-id="3b87a-217">此組織並無不同如何組織檔案到其他位置的資料夾。</span><span class="sxs-lookup"><span data-stu-id="3b87a-217">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="3b87a-218">如果您有多個有三個或四個相關的檔案中包含許多其他檔案的資料夾，通常會很有幫助將它們移入本身的子資料夾。</span><span class="sxs-lookup"><span data-stu-id="3b87a-218">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="3b87a-219">單元測試的 ASP.NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="3b87a-219">Unit Testing ASP.NET Core Apps</span></span>

<span data-ttu-id="3b87a-220">設計良好的 ASP.NET Core 應用程式中的複雜性和商務邏輯的大部分都會封裝在商務實體與各種服務。</span><span class="sxs-lookup"><span data-stu-id="3b87a-220">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="3b87a-221">ASP.NET Core MVC 應用程式本身，以控制站、 篩選、 viewmodels 及檢視，應該需要極少數的單元測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-221">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require very few unit tests.</span></span> <span data-ttu-id="3b87a-222">大部分的指定動作的功能之外的動作方法本身。</span><span class="sxs-lookup"><span data-stu-id="3b87a-222">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="3b87a-223">測試是否運作正常，路由或全域錯誤處理，無法執行有效地與單元測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-223">Testing whether routing works correctly, or global error handling, cannot be done effectively with a unit test.</span></span> <span data-ttu-id="3b87a-224">同樣地，任何篩選條件，包括模型驗證和驗證和授權篩選條件，不能進行過單元測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-224">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested.</span></span> <span data-ttu-id="3b87a-225">這些來源，不應該是行為的兩者很小，委派的服務可測試使用它們的控制站的獨立運作大量大部分動作方法。</span><span class="sxs-lookup"><span data-stu-id="3b87a-225">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="3b87a-226">有時候，您必須要重構程式碼中的，以便單元測試它。</span><span class="sxs-lookup"><span data-stu-id="3b87a-226">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="3b87a-227">這經常需要識別的抽象概念和使用相依性插入來存取您想要測試，程式碼中的抽象，而不要直接針對基礎結構程式碼撰寫。</span><span class="sxs-lookup"><span data-stu-id="3b87a-227">Frequently this involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="3b87a-228">例如，請考慮這個簡單的動作方法，來顯示影像：</span><span class="sxs-lookup"><span data-stu-id="3b87a-228">For example, consider this simple action method for displaying images:</span></span>

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

<span data-ttu-id="3b87a-229">單元測試這個方法會由直接相依於 System.IO.File，用來從檔案系統讀取困難。</span><span class="sxs-lookup"><span data-stu-id="3b87a-229">Unit testing this method is made difficult by its direct dependency on System.IO.File, which it uses to read from the file system.</span></span> <span data-ttu-id="3b87a-230">您可以測試此行為以確保運作正常，但實際的檔案與如此做為整合測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-230">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="3b87a-231">值得注意的是您無法測試此方法的路由，您會看到如何短時間內執行此動作與功能的測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-231">It's worth noting you can't test this method's route – you'll see how to do this with a functional test shortly.</span></span>

<span data-ttu-id="3b87a-232">如果您不能單元測試的檔案系統行為直接，而且您不能測試路由，還有什麼測試呢？</span><span class="sxs-lookup"><span data-stu-id="3b87a-232">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="3b87a-233">嗯之後讓單元測試的重構作業，, 您可能會發現一些測試案例和遺失的行為，例如錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="3b87a-233">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="3b87a-234">方法的作用為何時找不到檔案？</span><span class="sxs-lookup"><span data-stu-id="3b87a-234">What does the method do when a file isn't found?</span></span> <span data-ttu-id="3b87a-235">它是該怎麼辦？</span><span class="sxs-lookup"><span data-stu-id="3b87a-235">What should it do?</span></span> <span data-ttu-id="3b87a-236">在此範例中，重構的方法看起來像這樣：</span><span class="sxs-lookup"><span data-stu-id="3b87a-236">In this example, the refactored method looks like this:</span></span>

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

<span data-ttu-id="3b87a-237">\_記錄器和\_imageService 同時插入做為相依性。</span><span class="sxs-lookup"><span data-stu-id="3b87a-237">The \_logger and \_imageService are both injected as dependencies.</span></span> <span data-ttu-id="3b87a-238">現在您可以測試會傳遞至動作方法的相同識別碼會傳遞至\_imageService，及一部分 FileResult 傳回結果的位元組。</span><span class="sxs-lookup"><span data-stu-id="3b87a-238">Now you can test that the same id that is passed to the action method is passed to the \_imageService, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="3b87a-239">您也可以測試會發生錯誤記錄，不如預期，並會傳回找不到結果，如果映像已遺失，假設這重要的應用程式行為 （亦即，不只暫存程式碼加入至診斷問題的開發人員）。</span><span class="sxs-lookup"><span data-stu-id="3b87a-239">You can also test that error logging is happening as expected, and that a NotFound result is returned if the image is missing, assuming this is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="3b87a-240">實際的檔案邏輯已移至另一個實作服務時，並具有已予以增加以傳回遺失檔案的大小寫的應用程式特定例外狀況。</span><span class="sxs-lookup"><span data-stu-id="3b87a-240">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="3b87a-241">您可以測試此實作中獨立作業，使用整合測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-241">You can test this implementation independently, using an integration test.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="3b87a-242">整合測試 ASP.NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="3b87a-242">Integration Testing ASP.NET Core Apps</span></span>

```cs
    }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

<span data-ttu-id="3b87a-243">此服務會 IHostingEnvironment，程式碼未重構到個別的服務前 CatalogController 一樣。</span><span class="sxs-lookup"><span data-stu-id="3b87a-243">This service uses the IHostingEnvironment, just as the CatalogController code did before it was refactored into a separate service.</span></span> <span data-ttu-id="3b87a-244">因為這是唯一的程式碼中使用 IHostingEnvironment 控制器，該相依性已從 CatalogController 的建構函式中移除。</span><span class="sxs-lookup"><span data-stu-id="3b87a-244">Since this was the only code in the controller that used IHostingEnvironment, that dependency was removed from CatalogController's constructor.</span></span>

<span data-ttu-id="3b87a-245">若要測試此服務能夠正常運作，您需要建立已知的測試映像檔，並確認服務傳回其提供特定的輸入。</span><span class="sxs-lookup"><span data-stu-id="3b87a-245">To test that this service works correctly, you need to create a known test image file and verify that the service returns it given a specific input.</span></span> <span data-ttu-id="3b87a-246">您應該注意不要使用模擬物件在您實際想要測試 （在此情況下，從檔案系統讀取） 的行為。</span><span class="sxs-lookup"><span data-stu-id="3b87a-246">You should take care not to use mock objects on the behavior you actually want to test (in this case, reading from the file system).</span></span> <span data-ttu-id="3b87a-247">不過，模擬物件可能仍會很有用，若要設定整合測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-247">However, mock objects may still be useful to set up integration tests.</span></span> <span data-ttu-id="3b87a-248">在此情況下，您可以模擬 IHostingEnvironment，使其 ContentRootPath 指向您要用於測試影像的資料夾。</span><span class="sxs-lookup"><span data-stu-id="3b87a-248">In this case, you can mock IHostingEnvironment so that its ContentRootPath points to the folder you're going to use for your test image.</span></span> <span data-ttu-id="3b87a-249">完成的工作整合測試類別如下所示：</span><span class="sxs-lookup"><span data-stu-id="3b87a-249">The complete working integration test class is shown here:</span></span>

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
> <span data-ttu-id="3b87a-250">測試本身是很簡單 – 大量的程式碼就必須設定系統，並建立測試的基礎結構 （在此案例中的實際檔案從磁碟讀取）。</span><span class="sxs-lookup"><span data-stu-id="3b87a-250">that the test itself is very simple – the bulk of the code is necessary to configure the system and create the testing infrastructure (in this case, an actual file to be read from disk).</span></span> <span data-ttu-id="3b87a-251">這是常見的整合測試，通常需要更複雜的安裝程式工作與單元測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-251">This is typical for integration tests, which often require more complex setup work than unit tests.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="3b87a-252">功能測試的 ASP.NET Core 應用程式</span><span class="sxs-lookup"><span data-stu-id="3b87a-252">Functional Testing ASP.NET Core Apps</span></span>

<span data-ttu-id="3b87a-253">對於 ASP.NET Core 應用程式，此 TestServer 類別可讓功能測試很容易撰寫。</span><span class="sxs-lookup"><span data-stu-id="3b87a-253">For ASP.NET Core applications, the TestServer class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="3b87a-254">就像平常您的應用程式，您可以設定使用 WebHostBuilder，TestServer。</span><span class="sxs-lookup"><span data-stu-id="3b87a-254">You configure a TestServer using a WebHostBuilder, just as you normally do for your application.</span></span> <span data-ttu-id="3b87a-255">應該設定這個 WebHostBuilder，就像您的應用程式的實際主機，但您可以修改它的任何層面，讓測試更為容易。</span><span class="sxs-lookup"><span data-stu-id="3b87a-255">This WebHostBuilder should be configured just like your application's real host, but you can modify any aspects of it that make testing easier.</span></span> <span data-ttu-id="3b87a-256">大部分的情況下，因此您可以將它封裝的可重複使用的方法 （也許在基底類別） 中，您將重複使用相同的 TestServer 許多測試案例：</span><span class="sxs-lookup"><span data-stu-id="3b87a-256">Most of the time, you'll reuse the same TestServer for many test cases, so you can encapsulate it in a reusable method (perhaps in a base class):</span></span>

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

<span data-ttu-id="3b87a-257">GetProjectPath 方法只會傳回至 web 專案 （下載範例方案） 的實體路徑。</span><span class="sxs-lookup"><span data-stu-id="3b87a-257">The GetProjectPath method simply returns the physical path to the web project (download sample solution).</span></span> <span data-ttu-id="3b87a-258">WebHostBuilder 在此情況下只指定其中內容的根 web 應用程式，以及參考真實的 web 應用程式使用的相同啟動類別。</span><span class="sxs-lookup"><span data-stu-id="3b87a-258">The WebHostBuilder in this case simply specifies where the content root for the web application is, and references the same Startup class the real web application uses.</span></span> <span data-ttu-id="3b87a-259">若要使用 TestServer，您可以使用標準 System.Net.HttpClient 類型提出要求，它。</span><span class="sxs-lookup"><span data-stu-id="3b87a-259">To work with the TestServer, you use the standard System.Net.HttpClient type to make requests to it.</span></span> <span data-ttu-id="3b87a-260">TestServer 公開提供的預先設定的用戶端準備好要提出 TestServer 上執行的應用程式，很有幫助 CreateClient 方法。</span><span class="sxs-lookup"><span data-stu-id="3b87a-260">TestServer exposes a helpful CreateClient method that provides a pre-configured client that is ready to make requests to the application running on the TestServer.</span></span> <span data-ttu-id="3b87a-261">使用此用戶端 (設定為受保護\_上述的基本測試上的用戶端成員) 撰寫 ASP.NET Core 應用程式的功能測試時：</span><span class="sxs-lookup"><span data-stu-id="3b87a-261">You use this client (set to the protected \_client member on the base test above) when writing functional tests for your ASP.NET Core application:</span></span>

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

<span data-ttu-id="3b87a-262">此功能的測試執行完整的 ASP.NET Core MVC 應用程式堆疊，包括所有中介軟體、 篩選器、 繫結器等，可能會先準備就緒。</span><span class="sxs-lookup"><span data-stu-id="3b87a-262">This functional test exercises the full ASP.NET Core MVC application stack, including all middleware, filters, binders, etc. that may be in place.</span></span> <span data-ttu-id="3b87a-263">它會確認指定的路由 （「 / 目錄/pic 1 」） 會傳回預期的位元組陣列，檔案至已知位置。</span><span class="sxs-lookup"><span data-stu-id="3b87a-263">It verifies that a given route ("/catalog/pic/1") returns the expected byte array for a file in a known location.</span></span> <span data-ttu-id="3b87a-264">它會這樣做，而不需設定實際的網頁伺服器，並因此可避免大部分的損毀，使用真實的 web 伺服器以進行測試可能會遇到 （例如，防火牆設定的問題）。</span><span class="sxs-lookup"><span data-stu-id="3b87a-264">It does so without setting up a real web server, and so avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="3b87a-265">針對 TestServer 執行功能測試通常低於整合和單元測試，但速度比測試 web 伺服器會在網路上執行的測試。</span><span class="sxs-lookup"><span data-stu-id="3b87a-265">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="3b87a-266">[上一個](work-with-data-in-asp-net-core-apps.md) [下一步] (開發的程序-如-azure.md)</span><span class="sxs-lookup"><span data-stu-id="3b87a-266">[Previous] (work-with-data-in-asp-net-core-apps.md) [Next] (development-process-for-azure.md)</span></span>
