---
title: 測試 ASP.NET Core MVC 應用程式
description: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 | 測試 ASP.NET Core MVC 應用程式
author: ardalis
ms.author: wiwagn
ms.date: 12/01/2020
ms.openlocfilehash: b253cfb90487cc462b0f3b8a7564c97ad403aa06
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851395"
---
# <a name="test-aspnet-core-mvc-apps"></a><span data-ttu-id="f0738-103">測試 ASP.NET Core MVC 應用程式</span><span class="sxs-lookup"><span data-stu-id="f0738-103">Test ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="f0738-104">*「如果您不喜歡為您的產品進行單元測試，您的客戶多半也不會喜歡測試它。」*</span><span class="sxs-lookup"><span data-stu-id="f0738-104">*"If you don't like unit testing your product, most likely your customers won't like to test it, either."*</span></span>
 > <span data-ttu-id="f0738-105">\_- 匿名-</span><span class="sxs-lookup"><span data-stu-id="f0738-105">\_- Anonymous-</span></span>

<span data-ttu-id="f0738-106">軟體複雜與否，都可能以意想不到的方式回應變更而失敗。</span><span class="sxs-lookup"><span data-stu-id="f0738-106">Software of any complexity can fail in unexpected ways in response to changes.</span></span> <span data-ttu-id="f0738-107">因此，除了最不重要的 (或最不關鍵的) 應用程式之外，對所有應用程式進行變更後都需要進行測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-107">Thus, testing after making changes is required for all but the most trivial (or least critical) applications.</span></span> <span data-ttu-id="f0738-108">手動測試是最慢、最不可靠且最昂貴的測試軟體方式。</span><span class="sxs-lookup"><span data-stu-id="f0738-108">Manual testing is the slowest, least reliable, most expensive way to test software.</span></span> <span data-ttu-id="f0738-109">不幸的是，如果應用程式設計為不可測試，則手動可能是唯一可用的手段。</span><span class="sxs-lookup"><span data-stu-id="f0738-109">Unfortunately, if applications aren't designed to be testable, it can be the only means available.</span></span> <span data-ttu-id="f0738-110">為了遵循 [第4章](architectural-principles.md) 中所述的架構原則而撰寫的應用程式，應可進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-110">Applications written to follow the architectural principles laid out in [chapter 4](architectural-principles.md) should be unit testable.</span></span> <span data-ttu-id="f0738-111">ASP.NET Core 的應用程式支援自動化整合和功能測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-111">ASP.NET Core applications support automated integration and functional testing.</span></span>

## <a name="kinds-of-automated-tests"></a><span data-ttu-id="f0738-112">自動化測試的種類</span><span class="sxs-lookup"><span data-stu-id="f0738-112">Kinds of automated tests</span></span>

<span data-ttu-id="f0738-113">軟體應用程式自動化測試有許多種類的。</span><span class="sxs-lookup"><span data-stu-id="f0738-113">There are many kinds of automated tests for software applications.</span></span> <span data-ttu-id="f0738-114">最簡單且最低層級的測試為單元測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-114">The simplest, lowest level test is the unit test.</span></span> <span data-ttu-id="f0738-115">在較高的層級中，有整合測試和功能測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-115">At a slightly higher level, there are integration tests and functional tests.</span></span> <span data-ttu-id="f0738-116">其他類型的測試（例如 UI 測試、負載測試、壓力測試和冒煙測試）已超出本檔的範圍。</span><span class="sxs-lookup"><span data-stu-id="f0738-116">Other kinds of tests, such as UI tests, load tests, stress tests, and smoke tests, are beyond the scope of this document.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="f0738-117">單元測試</span><span class="sxs-lookup"><span data-stu-id="f0738-117">Unit tests</span></span>

<span data-ttu-id="f0738-118">單元測試會測試應用程式邏輯的單一組件。</span><span class="sxs-lookup"><span data-stu-id="f0738-118">A unit test tests a single part of your application's logic.</span></span> <span data-ttu-id="f0738-119">可透過列舉一些不具有的事物來對其進一步描述。</span><span class="sxs-lookup"><span data-stu-id="f0738-119">One can further describe it by listing some of the things that it isn't.</span></span> <span data-ttu-id="f0738-120">單元測試不會測試程式碼如何與相依性或基礎結構同運作，那會在整合測試中進行。</span><span class="sxs-lookup"><span data-stu-id="f0738-120">A unit test doesn't test how your code works with dependencies or infrastructure – that's what integration tests are for.</span></span> <span data-ttu-id="f0738-121">單元測試不會測試撰寫程式碼所採用的架構，您應假設該架構可正常運行；如果您發現並非如此，請提交 Bug 並撰寫因應措施。</span><span class="sxs-lookup"><span data-stu-id="f0738-121">A unit test doesn't test the framework your code is written on – you should assume it works or, if you find it doesn't, file a bug and code a workaround.</span></span> <span data-ttu-id="f0738-122">單元測試完全在記憶體和處理序中執行。</span><span class="sxs-lookup"><span data-stu-id="f0738-122">A unit test runs completely in memory and in process.</span></span> <span data-ttu-id="f0738-123">不會與文件系統、網路或資料庫進行通訊。</span><span class="sxs-lookup"><span data-stu-id="f0738-123">It doesn't communicate with the file system, the network, or a database.</span></span> <span data-ttu-id="f0738-124">單元測試應純粹只測試您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f0738-124">Unit tests should only test your code.</span></span>

<span data-ttu-id="f0738-125">單元測試是因為它們只會測試程式碼的單一單位（不含外部相依性），因此執行速度非常快。</span><span class="sxs-lookup"><span data-stu-id="f0738-125">Unit tests, by virtue of the fact that they test only a single unit of your code, with no external dependencies, should execute extremely fast.</span></span> <span data-ttu-id="f0738-126">因此，您應該能夠在幾秒鐘內執行數百個單元測試的測試套件。</span><span class="sxs-lookup"><span data-stu-id="f0738-126">Thus, you should be able to run test suites of hundreds of unit tests in a few seconds.</span></span> <span data-ttu-id="f0738-127">請經常執行，理想情況下在每次推送至共用原始檔控制儲存機制前都先執行，且當然是以組建伺服器上的每個自動化組建來執行。</span><span class="sxs-lookup"><span data-stu-id="f0738-127">Run them frequently, ideally before every push to a shared source control repository, and certainly with every automated build on your build server.</span></span>

### <a name="integration-tests"></a><span data-ttu-id="f0738-128">整合測試</span><span class="sxs-lookup"><span data-stu-id="f0738-128">Integration tests</span></span>

<span data-ttu-id="f0738-129">雖然封裝與資料庫和檔案系統等基礎結構互動的程式碼是不錯的想法，但您仍將會持有其中某些程式碼且可能需要對其進行測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-129">Although it's a good idea to encapsulate your code that interacts with infrastructure like databases and file systems, you will still have some of that code, and you will probably want to test it.</span></span> <span data-ttu-id="f0738-130">此外，您應該驗證當應用程式相依性在完全解析時，程式碼層的互動是否與預期一致。</span><span class="sxs-lookup"><span data-stu-id="f0738-130">Additionally, you should verify that your code's layers interact as you expect when your application's dependencies are fully resolved.</span></span> <span data-ttu-id="f0738-131">這項功能是整合測試的責任。</span><span class="sxs-lookup"><span data-stu-id="f0738-131">This functionality is the responsibility of integration tests.</span></span> <span data-ttu-id="f0738-132">整合測試通常比單元測試慢且更難設定，因為通常依賴於外部相依性與基礎結構。</span><span class="sxs-lookup"><span data-stu-id="f0738-132">Integration tests tend to be slower and more difficult to set up than unit tests, because they often depend on external dependencies and infrastructure.</span></span> <span data-ttu-id="f0738-133">因此，您應該避免在整合測試中進行可使用單元測試進行的測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-133">Thus, you should avoid testing things that could be tested with unit tests in integration tests.</span></span> <span data-ttu-id="f0738-134">如果您可以用單元測試來測試一個指定的案例，您應該用單元測試來進行測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-134">If you can test a given scenario with a unit test, you should test it with a unit test.</span></span> <span data-ttu-id="f0738-135">如果不能，則考慮使用整合測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-135">If you can't, then consider using an integration test.</span></span>

<span data-ttu-id="f0738-136">整合測試通常會有比單元測試更複雜的設定與清除程序。</span><span class="sxs-lookup"><span data-stu-id="f0738-136">Integration tests will often have more complex setup and teardown procedures than unit tests.</span></span> <span data-ttu-id="f0738-137">例如，針對實際資料庫的整合測試，需要一種能在每次測試之前將資料庫傳回已知狀態的方法。</span><span class="sxs-lookup"><span data-stu-id="f0738-137">For example, an integration test that goes against an actual database will need a way to return the database to a known state before each test run.</span></span> <span data-ttu-id="f0738-138">隨著新測試的新增和資料庫結構描述發展出的生產，這些測試指令碼的大小和複雜程度都會增加。</span><span class="sxs-lookup"><span data-stu-id="f0738-138">As new tests are added and the production database schema evolves, these test scripts will tend to grow in size and complexity.</span></span> <span data-ttu-id="f0738-139">在許多大型系統中，簽入共用原始檔控制的變更之前，在開發人員工作站上執行完整的整合測試套件並不切實際。</span><span class="sxs-lookup"><span data-stu-id="f0738-139">In many large systems, it is impractical to run full suites of integration tests on developer workstations before checking in changes to shared source control.</span></span> <span data-ttu-id="f0738-140">在這些情況下，整合測試可能會在組建伺服器上執行。</span><span class="sxs-lookup"><span data-stu-id="f0738-140">In these cases, integration tests may be run on a build server.</span></span>

### <a name="functional-tests"></a><span data-ttu-id="f0738-141">功能測試</span><span class="sxs-lookup"><span data-stu-id="f0738-141">Functional tests</span></span>

<span data-ttu-id="f0738-142">整合測試是從開發人員的角度撰寫，以驗證系統的某些元件是否能夠正確地一起運作。</span><span class="sxs-lookup"><span data-stu-id="f0738-142">Integration tests are written from the perspective of the developer, to verify that some components of the system work correctly together.</span></span> <span data-ttu-id="f0738-143">功能測試是從使用者的角度撰寫，並根據其要求來驗證系統的正確性。</span><span class="sxs-lookup"><span data-stu-id="f0738-143">Functional tests are written from the perspective of the user, and verify the correctness of the system based on its requirements.</span></span> <span data-ttu-id="f0738-144">相較於單元測試，下列摘錄提供有用的比喻來說明如何思考功能測試：</span><span class="sxs-lookup"><span data-stu-id="f0738-144">The following excerpt offers a useful analogy for how to think about functional tests, compared to unit tests:</span></span>

> <span data-ttu-id="f0738-145">「很多時候，系統的開發就像是建造房屋。</span><span class="sxs-lookup"><span data-stu-id="f0738-145">"Many times the development of a system is likened to the building of a house.</span></span> <span data-ttu-id="f0738-146">雖然這個比喻不太正確，但我們可以將其延伸以便理解單元測試和功能測試之間的差異。</span><span class="sxs-lookup"><span data-stu-id="f0738-146">While this analogy isn't quite correct, we can extend it for the purposes of understanding the difference between unit and functional tests.</span></span> <span data-ttu-id="f0738-147">單元測試類似於造訪房屋建築工地的建築檢查員。</span><span class="sxs-lookup"><span data-stu-id="f0738-147">Unit testing is analogous to a building inspector visiting a house's construction site.</span></span> <span data-ttu-id="f0738-148">檢查員會專注於房屋的各種內部系統：地基、結構、電力、配管系統等等。</span><span class="sxs-lookup"><span data-stu-id="f0738-148">He is focused on the various internal systems of the house, the foundation, framing, electrical, plumbing, and so on.</span></span> <span data-ttu-id="f0738-149">其會確保 (測試) 房屋的各部分都能正確且安全地運作，也就是符合建築規範。</span><span class="sxs-lookup"><span data-stu-id="f0738-149">He ensures (tests) that the parts of the house will work correctly and safely, that is, meet the building code.</span></span> <span data-ttu-id="f0738-150">在此案例中，功能測試類似於屋主造訪同一個建築工地。</span><span class="sxs-lookup"><span data-stu-id="f0738-150">Functional tests in this scenario are analogous to the homeowner visiting this same construction site.</span></span> <span data-ttu-id="f0738-151">屋主會假設內部系統能運作正常，因為建築檢查員正在執行工作。</span><span class="sxs-lookup"><span data-stu-id="f0738-151">He assumes that the internal systems will behave appropriately, that the building inspector is performing his task.</span></span> <span data-ttu-id="f0738-152">屋主會著重於住在這個房子裡會是什麼樣子。</span><span class="sxs-lookup"><span data-stu-id="f0738-152">The homeowner is focused on what it will be like to live in this house.</span></span> <span data-ttu-id="f0738-153">他會關心房子的外觀：房間大小是否舒適、房子是否符合家庭的需要、窗戶是否位於能迎接早晨陽光的位置。</span><span class="sxs-lookup"><span data-stu-id="f0738-153">He is concerned with how the house looks, are the various rooms a comfortable size, does the house fit the family's needs, are the windows in a good spot to catch the morning sun.</span></span> <span data-ttu-id="f0738-154">這即為屋主對房屋進行功能測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-154">The homeowner is performing functional tests on the house.</span></span> <span data-ttu-id="f0738-155">他以使用者的角度來觀看。</span><span class="sxs-lookup"><span data-stu-id="f0738-155">He has the user's perspective.</span></span> <span data-ttu-id="f0738-156">而建築檢查員是對房屋進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-156">The building inspector is performing unit tests on the house.</span></span> <span data-ttu-id="f0738-157">其以建築者的角度來觀看。」</span><span class="sxs-lookup"><span data-stu-id="f0738-157">He has the builder's perspective."</span></span>

<span data-ttu-id="f0738-158">來源：[Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html) (單元測試與功能測試)</span><span class="sxs-lookup"><span data-stu-id="f0738-158">Source: [Unit Testing versus Functional Tests](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)</span></span>

<span data-ttu-id="f0738-159">我喜歡說：「身為開發人員，我們有兩種失敗方式：以錯誤的方式建置東西，或建置錯誤的東西。」</span><span class="sxs-lookup"><span data-stu-id="f0738-159">I'm fond of saying "As developers, we fail in two ways: we build the thing wrong, or we build the wrong thing."</span></span> <span data-ttu-id="f0738-160">單元測試確保您以正確的方式建置東西，而功能測試確保您建置正確的東西。</span><span class="sxs-lookup"><span data-stu-id="f0738-160">Unit tests ensure you are building the thing right; functional tests ensure you are building the right thing.</span></span>

<span data-ttu-id="f0738-161">由於功能測試在系統層級上操作，因此可能需要一定程度的 UI 自動化。</span><span class="sxs-lookup"><span data-stu-id="f0738-161">Since functional tests operate at the system level, they may require some degree of UI automation.</span></span> <span data-ttu-id="f0738-162">與整合測試一樣，功能測試通常也會使用某種類的測試基礎結構。</span><span class="sxs-lookup"><span data-stu-id="f0738-162">Like integration tests, they usually work with some kind of test infrastructure as well.</span></span> <span data-ttu-id="f0738-163">此活動讓它們比單元和整合測試更慢且更脆弱。</span><span class="sxs-lookup"><span data-stu-id="f0738-163">This activity makes them slower and more brittle than unit and integration tests.</span></span> <span data-ttu-id="f0738-164">功能測試的次數，只要足以確保系統會按照使用者的期望運作即可。</span><span class="sxs-lookup"><span data-stu-id="f0738-164">You should have only as many functional tests as you need to be confident the system is behaving as users expect.</span></span>

### <a name="testing-pyramid"></a><span data-ttu-id="f0738-165">測試金字塔圖</span><span class="sxs-lookup"><span data-stu-id="f0738-165">Testing Pyramid</span></span>

<span data-ttu-id="f0738-166">Martin Fowler 撰寫了測試金字塔相關事項，其中的一個範例如圖 9-1 所示。</span><span class="sxs-lookup"><span data-stu-id="f0738-166">Martin Fowler wrote about the testing pyramid, an example of which is shown in Figure 9-1.</span></span>

![測試金字塔圖](./media/image9-1.png)

<span data-ttu-id="f0738-168">**圖 9-1**.</span><span class="sxs-lookup"><span data-stu-id="f0738-168">**Figure 9-1**.</span></span> <span data-ttu-id="f0738-169">測試金字塔圖</span><span class="sxs-lookup"><span data-stu-id="f0738-169">Testing Pyramid</span></span>

<span data-ttu-id="f0738-170">金字塔的不同圖層及其相對大小代表了不同類型的測試，以及您應該為應用程式撰寫的測試數量。</span><span class="sxs-lookup"><span data-stu-id="f0738-170">The different layers of the pyramid, and their relative sizes, represent different kinds of tests and how many you should write for your application.</span></span> <span data-ttu-id="f0738-171">如您所見，建議以大型的單元測試作為基礎，由較小的整合測試層來支援，再加上一個更小的功能測試層。</span><span class="sxs-lookup"><span data-stu-id="f0738-171">As you can see, the recommendation is to have a large base of unit tests, supported by a smaller layer of integration tests, with an even smaller layer of functional tests.</span></span> <span data-ttu-id="f0738-172">理想情況下，每個圖層的測試只應能在該層中進行，而不能在較低層中充分進行。</span><span class="sxs-lookup"><span data-stu-id="f0738-172">Each layer should ideally only have tests in it that cannot be performed adequately at a lower layer.</span></span> <span data-ttu-id="f0738-173">在您嘗試決定需要在特定案例中使用哪種測試類型時，請記得測試金字塔。</span><span class="sxs-lookup"><span data-stu-id="f0738-173">Keep the testing pyramid in mind when you are trying to decide which kind of test you need for a particular scenario.</span></span>

### <a name="what-to-test"></a><span data-ttu-id="f0738-174">測試的內容</span><span class="sxs-lookup"><span data-stu-id="f0738-174">What to test</span></span>

<span data-ttu-id="f0738-175">對於沒有撰寫自動化測試經驗的開發人員來說，常見問題就是測試的內容。</span><span class="sxs-lookup"><span data-stu-id="f0738-175">A common problem for developers who are inexperienced with writing automated tests is coming up with what to test.</span></span> <span data-ttu-id="f0738-176">測試條件式邏輯是很好的起點。</span><span class="sxs-lookup"><span data-stu-id="f0738-176">A good starting point is to test conditional logic.</span></span> <span data-ttu-id="f0738-177">無論您有一個方法，其行為會根據條件陳述式而改變 (if-else、switch 等等) ，您應該能夠提出至少幾個測試來確認特定條件的正確行為。</span><span class="sxs-lookup"><span data-stu-id="f0738-177">Anywhere you have a method with behavior that changes based on a conditional statement (if-else, switch, and so on), you should be able to come up with at least a couple of tests that confirm the correct behavior for certain conditions.</span></span> <span data-ttu-id="f0738-178">如果您的程式碼有錯誤狀況，可透過程式碼撰寫至少一個「開心路徑」 (即沒有錯誤) 的測試，且至少一個「悲傷路徑」 (含有錯誤或非典型結果) 的測試，來確認您的應用程式在出現錯誤時的行為如預期。</span><span class="sxs-lookup"><span data-stu-id="f0738-178">If your code has error conditions, it's good to write at least one test for the "happy path" through the code (with no errors), and at least one test for the "sad path" (with errors or atypical results) to confirm your application behaves as expected in the face of errors.</span></span> <span data-ttu-id="f0738-179">最後，嘗試專注於測試可能失敗的事項，而不是專注於程式碼涵蓋範圍等指標。</span><span class="sxs-lookup"><span data-stu-id="f0738-179">Finally, try to focus on testing things that can fail, rather than focusing on metrics like code coverage.</span></span> <span data-ttu-id="f0738-180">一般來說，程式碼涵蓋範圍是多優於少。</span><span class="sxs-lookup"><span data-stu-id="f0738-180">More code coverage is better than less, generally.</span></span> <span data-ttu-id="f0738-181">不過，撰寫一些複雜和商務關鍵方法的測試，通常比撰寫自動屬性測試來改善測試程式碼涵蓋範圍度量更好用。</span><span class="sxs-lookup"><span data-stu-id="f0738-181">However, writing a few more tests of a complex and business-critical method is usually a better use of time than writing tests for auto-properties just to improve test code coverage metrics.</span></span>

## <a name="organizing-test-projects"></a><span data-ttu-id="f0738-182">組織測試專案</span><span class="sxs-lookup"><span data-stu-id="f0738-182">Organizing test projects</span></span>

<span data-ttu-id="f0738-183">可以使用最適合您的方式來組織測試專案。</span><span class="sxs-lookup"><span data-stu-id="f0738-183">Test projects can be organized however works best for you.</span></span> <span data-ttu-id="f0738-184">依照類型 (單元測試、整合測試) 和測試內容 (依照專案、命名空間) 來分隔測試是不錯的做法。</span><span class="sxs-lookup"><span data-stu-id="f0738-184">It's a good idea to separate tests by type (unit test, integration test) and by what they are testing (by project, by namespace).</span></span> <span data-ttu-id="f0738-185">此分隔該由單一測試專案中的資料夾組成，或是由多個測試專案組成，是設計上的決策。</span><span class="sxs-lookup"><span data-stu-id="f0738-185">Whether this separation consists of folders within a single test project, or multiple test projects, is a design decision.</span></span> <span data-ttu-id="f0738-186">單一專案是最簡單的，但針對有大量測試的大型專案，或為了能更容易執行不同的測試集，您可能需要有幾個不同的測試專案。</span><span class="sxs-lookup"><span data-stu-id="f0738-186">One project is simplest, but for large projects with many tests, or in order to more easily run different sets of tests, you might want to have several different test projects.</span></span> <span data-ttu-id="f0738-187">許多小組根據正在測試的專案來組織測試專案；對於具有許多專案的應用程式，這可能會導致大量測試專案，尤其是如果您仍然根據每個專案中的測試種類來分隔測試專案。</span><span class="sxs-lookup"><span data-stu-id="f0738-187">Many teams organize test projects based on the project they are testing, which for applications with more than a few projects can result in a large number of test projects, especially if you still break these down according to what kind of tests are in each project.</span></span> <span data-ttu-id="f0738-188">折衷方法是讓每個應用程式的每種測試都有一個專案，在測試專案中包含資料夾以指出正在測試的專案 (和類別)。</span><span class="sxs-lookup"><span data-stu-id="f0738-188">A compromise approach is to have one project per kind of test, per application, with folders inside the test projects to indicate the project (and class) being tested.</span></span>

<span data-ttu-id="f0738-189">常見的方法是在 ' src ' 資料夾下組織應用程式專案，並在平行「測試」資料夾下組織應用程式的測試專案。</span><span class="sxs-lookup"><span data-stu-id="f0738-189">A common approach is to organize the application projects under a 'src' folder, and the application's test projects under a parallel 'tests' folder.</span></span> <span data-ttu-id="f0738-190">如果您覺得這樣的組織很有用，您可以在 Visual Studio 中建立相符的解決方案資料夾。</span><span class="sxs-lookup"><span data-stu-id="f0738-190">You can create matching solution folders in Visual Studio, if you find this organization useful.</span></span>

![解決方案中的測試組織](./media/image9-2.png)

<span data-ttu-id="f0738-192">**圖 9-2**：</span><span class="sxs-lookup"><span data-stu-id="f0738-192">**Figure 9-2**.</span></span> <span data-ttu-id="f0738-193">解決方案中的測試組織</span><span class="sxs-lookup"><span data-stu-id="f0738-193">Test organization in your solution</span></span>

<span data-ttu-id="f0738-194">您可以使用您偏好的任何測試架構。</span><span class="sxs-lookup"><span data-stu-id="f0738-194">You can use whichever test framework you prefer.</span></span> <span data-ttu-id="f0738-195">xUnit 架構運作良好，且用來寫入所有的 ASP.NET Core 和 EF Core 測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-195">The xUnit framework works well and is what all of the ASP.NET Core and EF Core tests are written in.</span></span> <span data-ttu-id="f0738-196">您可以使用 [圖 9-3] 中所示的範本，或使用的 CLI，在 Visual Studio 中新增 xUnit 測試專案 `dotnet new xunit` 。</span><span class="sxs-lookup"><span data-stu-id="f0738-196">You can add an xUnit test project in Visual Studio using the template shown in Figure 9-3, or from the CLI using `dotnet new xunit`.</span></span>

![在 Visual Studio 中新增 xUnit 測試專案](./media/image9-3.png)

<span data-ttu-id="f0738-198">**圖 9-3**。</span><span class="sxs-lookup"><span data-stu-id="f0738-198">**Figure 9-3**.</span></span> <span data-ttu-id="f0738-199">在 Visual Studio 中新增 xUnit 測試專案</span><span class="sxs-lookup"><span data-stu-id="f0738-199">Add an xUnit Test Project in Visual Studio</span></span>

### <a name="test-naming"></a><span data-ttu-id="f0738-200">命名測試</span><span class="sxs-lookup"><span data-stu-id="f0738-200">Test naming</span></span>

<span data-ttu-id="f0738-201">以一致的方式命名測試，並以名稱表示每項測試的用途。</span><span class="sxs-lookup"><span data-stu-id="f0738-201">Name your tests in a consistent fashion, with names that indicate what each test does.</span></span> <span data-ttu-id="f0738-202">取得巨大成功的一種方法，是根據其正在測試的類別和方法來命名測試類別。</span><span class="sxs-lookup"><span data-stu-id="f0738-202">One approach I've had great success with is to name test classes according to the class and method they are testing.</span></span> <span data-ttu-id="f0738-203">這種方法會產生許多小型測試類別，但它會讓每個測試的責任非常明確。</span><span class="sxs-lookup"><span data-stu-id="f0738-203">This approach results in many small test classes, but it makes it extremely clear what each test is responsible for.</span></span> <span data-ttu-id="f0738-204">在設定測試類別名稱的情況下，若要識別要測試的類別和方法，可以使用測試方法名稱來指定要測試的行為。</span><span class="sxs-lookup"><span data-stu-id="f0738-204">With the test class name set up, to identify the class and method to be tested, the test method name can be used to specify the behavior being tested.</span></span> <span data-ttu-id="f0738-205">此名稱應包含預期的行為，以及應產生此行為的任何輸入或假設。</span><span class="sxs-lookup"><span data-stu-id="f0738-205">This name should include the expected behavior and any inputs or assumptions that should yield this behavior.</span></span> <span data-ttu-id="f0738-206">測試名稱的一些範例：</span><span class="sxs-lookup"><span data-stu-id="f0738-206">Some example test names:</span></span>

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

<span data-ttu-id="f0738-207">此方法的變體，會結束每個含有 "Should" 的測試類別名稱，並稍微修改時態：</span><span class="sxs-lookup"><span data-stu-id="f0738-207">A variation of this approach ends each test class name with "Should" and modifies the tense slightly:</span></span>

- <span data-ttu-id="f0738-208">`CatalogControllerGetImage`**應該** `.`**呼叫**`ImageServiceWithId`</span><span class="sxs-lookup"><span data-stu-id="f0738-208">`CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`</span></span>

- <span data-ttu-id="f0738-209">`CatalogControllerGetImage`**應該** `.`**記錄** 檔`WarningGivenImageMissingException`</span><span class="sxs-lookup"><span data-stu-id="f0738-209">`CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`</span></span>

<span data-ttu-id="f0738-210">有些小組會認為第二種命名方法更清楚，只是略為冗長。</span><span class="sxs-lookup"><span data-stu-id="f0738-210">Some teams find the second naming approach clearer, though slightly more verbose.</span></span> <span data-ttu-id="f0738-211">無論如何，請嘗試使用能深入了解測試行為的命名慣例；如此，當一或多項測試失敗時，從其名稱即可明顯看出是哪些案例失敗。</span><span class="sxs-lookup"><span data-stu-id="f0738-211">In any case, try to use a naming convention that provides insight into test behavior, so that when one or more tests fail, it's obvious from their names what cases have failed.</span></span> <span data-ttu-id="f0738-212">避免將您的測試命名模糊（例如 ControllerTests），因為當您在測試結果中看到這些名稱時，這些名稱不會提供任何值。</span><span class="sxs-lookup"><span data-stu-id="f0738-212">Avoid naming your tests vaguely, such as ControllerTests.Test1, as these names offer no value when you see them in test results.</span></span>

<span data-ttu-id="f0738-213">如果您遵循如上所述會產生許多小型測試類別的命名慣例，建議使用資料夾和命名空間來進一步組織測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-213">If you follow a naming convention like the one above that produces many small test classes, it's a good idea to further organize your tests using folders and namespaces.</span></span> <span data-ttu-id="f0738-214">圖 9-4 顯示在幾個測試專案中按資料夾組織測試的一種方法。</span><span class="sxs-lookup"><span data-stu-id="f0738-214">Figure 9-4 shows one approach to organizing tests by folder within several test projects.</span></span>

![根據要測試的類別依資料夾組織測試類別](./media/image9-4.png)

<span data-ttu-id="f0738-216">**圖 9-4。**</span><span class="sxs-lookup"><span data-stu-id="f0738-216">**Figure 9-4.**</span></span> <span data-ttu-id="f0738-217">根據正在測試的類別，按資料夾來組織測試類別。</span><span class="sxs-lookup"><span data-stu-id="f0738-217">Organizing test classes by folder based on class being tested.</span></span>

<span data-ttu-id="f0738-218">如果特定的應用程式類別有許多 (測試的方法，因此許多測試類別都) ，則將這些類別放在對應于應用程式類別的資料夾中可能會有意義。</span><span class="sxs-lookup"><span data-stu-id="f0738-218">If a particular application class has many methods being tested (and thus many test classes), it may make sense to place these classes in a folder corresponding to the application class.</span></span> <span data-ttu-id="f0738-219">這個組織與您如何將檔案組織到別處的資料夾中沒有區別。</span><span class="sxs-lookup"><span data-stu-id="f0738-219">This organization is no different than how you might organize files into folders elsewhere.</span></span> <span data-ttu-id="f0738-220">如果在包含許多其他檔案的資料夾中有三或四個以上相關檔案，將其移到其本身的子資料夾通常會很有幫助。</span><span class="sxs-lookup"><span data-stu-id="f0738-220">If you have more than three or four related files in a folder containing many other files, it's often helpful to move them into their own subfolder.</span></span>

## <a name="unit-testing-aspnet-core-apps"></a><span data-ttu-id="f0738-221">對 ASP.NET Core 應用程式進行單元測試</span><span class="sxs-lookup"><span data-stu-id="f0738-221">Unit testing ASP.NET Core apps</span></span>

<span data-ttu-id="f0738-222">在設計良好的 ASP.NET Core 應用程式中，大部分的複雜性和商務邏輯都會封裝在商務實體與各種服務中。</span><span class="sxs-lookup"><span data-stu-id="f0738-222">In a well-designed ASP.NET Core application, most of the complexity and business logic will be encapsulated in business entities and a variety of services.</span></span> <span data-ttu-id="f0738-223">ASP.NET Core MVC 應用程式本身，以及其控制器、篩選器、viewmodel 和 views，都應該需要一些單元測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-223">The ASP.NET Core MVC app itself, with its controllers, filters, viewmodels, and views, should require few unit tests.</span></span> <span data-ttu-id="f0738-224">指定動作的許多功能，大多在動作方法本身之外。</span><span class="sxs-lookup"><span data-stu-id="f0738-224">Much of the functionality of a given action lies outside the action method itself.</span></span> <span data-ttu-id="f0738-225">使用單元測試來測試路由或全域錯誤處理是否正常運作。</span><span class="sxs-lookup"><span data-stu-id="f0738-225">Testing whether routing or global error handling work correctly cannot be done effectively with a unit test.</span></span> <span data-ttu-id="f0738-226">同樣地，任何篩選準則（包括模型驗證、驗證和授權篩選）都無法使用以控制器動作方法為目標的測試進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-226">Likewise, any filters, including model validation and authentication and authorization filters, cannot be unit tested with a test targeting a controller's action method.</span></span> <span data-ttu-id="f0738-227">如果沒有這些行為來源，大多數行動方法應十分微小，會將其大部分工作委派給可獨立於使用它們的控制器來進行測試之服務。</span><span class="sxs-lookup"><span data-stu-id="f0738-227">Without these sources of behavior, most action methods should be trivially small, delegating the bulk of their work to services that can be tested independent of the controller that uses them.</span></span>

<span data-ttu-id="f0738-228">有時您需要重構程式碼才能進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-228">Sometimes you'll need to refactor your code in order to unit test it.</span></span> <span data-ttu-id="f0738-229">這項活動通常牽涉到識別抽象概念，並使用相依性插入來存取您想要測試之程式碼中的抽象概念，而不是直接針對基礎結構進行編碼。</span><span class="sxs-lookup"><span data-stu-id="f0738-229">Frequently this activity involves identifying abstractions and using dependency injection to access the abstraction in the code you'd like to test, rather than coding directly against infrastructure.</span></span> <span data-ttu-id="f0738-230">例如，請考慮這個簡單的動作方法來顯示影像：</span><span class="sxs-lookup"><span data-stu-id="f0738-230">For example, consider this easy action method for displaying images:</span></span>

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

<span data-ttu-id="f0738-231">對此方法進行單元測試很困難，因為其直接相依於 `System.IO.File`，用來從檔案系統中進行讀取。</span><span class="sxs-lookup"><span data-stu-id="f0738-231">Unit testing this method is made difficult by its direct dependency on `System.IO.File`, which it uses to read from the file system.</span></span> <span data-ttu-id="f0738-232">您可以測試此行為以確保其按預期運作，但對實際檔案執行此操作的是整合測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-232">You can test this behavior to ensure it works as expected, but doing so with real files is an integration test.</span></span> <span data-ttu-id="f0738-233">值得一提的是，您無法對此方法的路線進行單元測試 &mdash; ，您將會看到如何透過功能測試來進行這種測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-233">It's worth noting you can't unit test this method's route&mdash;you'll see how to do this testing with a functional test shortly.</span></span>

<span data-ttu-id="f0738-234">如果您不能直接對檔案系統行為進行單元測試，且無法測試路由，那麼需要測試哪些內容？</span><span class="sxs-lookup"><span data-stu-id="f0738-234">If you can't unit test the file system behavior directly, and you can't test the route, what is there to test?</span></span> <span data-ttu-id="f0738-235">在重構使單元測試成為可能之後，您可能會發現一些測試案例和遺失的行為，例如錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="f0738-235">Well, after refactoring to make unit testing possible, you may discover some test cases and missing behavior, such as error handling.</span></span> <span data-ttu-id="f0738-236">找不到檔案時，該方法會執行什麼操作？</span><span class="sxs-lookup"><span data-stu-id="f0738-236">What does the method do when a file isn't found?</span></span> <span data-ttu-id="f0738-237">它應該做什麼？</span><span class="sxs-lookup"><span data-stu-id="f0738-237">What should it do?</span></span> <span data-ttu-id="f0738-238">在此範例中，重構的方法如下所示：</span><span class="sxs-lookup"><span data-stu-id="f0738-238">In this example, the refactored method looks like this:</span></span>

```csharp
[HttpGet("[controller]/pic/{id}")]
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

<span data-ttu-id="f0738-239">`_logger` 和 `_imageService` 都插入為相依性。</span><span class="sxs-lookup"><span data-stu-id="f0738-239">`_logger` and `_imageService` are both injected as dependencies.</span></span> <span data-ttu-id="f0738-240">現在您可以測試傳遞給動作方法的相同識別碼是否已傳遞至 `_imageService` ，並將產生的位元組傳回做為 FileResult 的一部分。</span><span class="sxs-lookup"><span data-stu-id="f0738-240">Now you can test that the same ID that is passed to the action method is passed to `_imageService`, and that the resulting bytes are returned as part of the FileResult.</span></span> <span data-ttu-id="f0738-241">您也可以測試錯誤記錄是否如預期般發生，而且 `NotFound` 如果缺少影像，則會傳回結果，假設此行為是重要的應用程式行為 (也就是開發人員為了診斷問題而新增的暫存程式碼) 。</span><span class="sxs-lookup"><span data-stu-id="f0738-241">You can also test that error logging is happening as expected, and that a `NotFound` result is returned if the image is missing, assuming this behavior is important application behavior (that is, not just temporary code the developer added to diagnose an issue).</span></span> <span data-ttu-id="f0738-242">實際的檔案邏輯已移至另一個實作服務中，並且已擴大為針對遺失檔案情況來傳回應用程式特定的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f0738-242">The actual file logic has moved into a separate implementation service, and has been augmented to return an application-specific exception for the case of a missing file.</span></span> <span data-ttu-id="f0738-243">您可以使用整合測試來獨立測試此實作。</span><span class="sxs-lookup"><span data-stu-id="f0738-243">You can test this implementation independently, using an integration test.</span></span>

<span data-ttu-id="f0738-244">在大部分情況下，您會想要在控制器中使用全域例外狀況處理常式，因此它們中的邏輯數量應該很小，而且可能不值得進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="f0738-244">In most cases, you'll want to use global exception handlers in your controllers, so the amount of logic in them should be minimal and probably not worth unit testing.</span></span> <span data-ttu-id="f0738-245">使用功能測試和下面所述的類別，對控制器動作進行大部分的測試 `TestServer` 。</span><span class="sxs-lookup"><span data-stu-id="f0738-245">Do most of your testing of controller actions using functional tests and the `TestServer` class described below.</span></span>

## <a name="integration-testing-aspnet-core-apps"></a><span data-ttu-id="f0738-246">對 ASP.NET Core 應用程式進行整合測試</span><span class="sxs-lookup"><span data-stu-id="f0738-246">Integration testing ASP.NET Core apps</span></span>

<span data-ttu-id="f0738-247">您 ASP.NET Core 應用程式中大部分的整合測試都應該用來測試在您基礎結構專案中定義的服務及其他實作類型。</span><span class="sxs-lookup"><span data-stu-id="f0738-247">Most of the integration tests in your ASP.NET Core apps should be testing services and other implementation types defined in your Infrastructure project.</span></span> <span data-ttu-id="f0738-248">例如，您可以[測試 EF Core 是否成功更新，並從位於基礎結構專案中的資料存取類別中，擷取您想要的資料](/ef/core/miscellaneous/testing/)。</span><span class="sxs-lookup"><span data-stu-id="f0738-248">For example, you could [test that EF Core was successfully updating and retrieving the data that you expect](/ef/core/miscellaneous/testing/) from your data access classes residing in the Infrastructure project.</span></span> <span data-ttu-id="f0738-249">建議使用功能測試來測試 ASP.NET Core MVC 專案正確運作，該測試會對在測試主機中執行的應用程式執行。</span><span class="sxs-lookup"><span data-stu-id="f0738-249">The best way to test that your ASP.NET Core MVC project is behaving correctly is with functional tests that run against your app running in a test host.</span></span>

## <a name="functional-testing-aspnet-core-apps"></a><span data-ttu-id="f0738-250">對 ASP.NET Core 應用程式進行功能測試</span><span class="sxs-lookup"><span data-stu-id="f0738-250">Functional testing ASP.NET Core apps</span></span>

<span data-ttu-id="f0738-251">對 ASP.NET Core 應用程式來說，`TestServer` 類別使功能測試變得相當易於撰寫。</span><span class="sxs-lookup"><span data-stu-id="f0738-251">For ASP.NET Core applications, the `TestServer` class makes functional tests fairly easy to write.</span></span> <span data-ttu-id="f0738-252">您可以 `TestServer` 使用 `WebHostBuilder` (或 `HostBuilder`) 直接 (，如同您平常針對應用程式) ，或 `WebApplicationFactory` 從2.1 版開始提供的類型 (而設定。</span><span class="sxs-lookup"><span data-stu-id="f0738-252">You configure a `TestServer` using a `WebHostBuilder` (or `HostBuilder`) directly (as you normally do for your application), or with the `WebApplicationFactory` type (available since version 2.1).</span></span> <span data-ttu-id="f0738-253">盡可能盡可能地將您的測試主機與生產主機進行比對，以便測試的行為類似應用程式在生產環境中執行的動作。</span><span class="sxs-lookup"><span data-stu-id="f0738-253">Try to match your test host to your production host as closely as possible, so your tests exercise behavior similar to what the app will do in production.</span></span> <span data-ttu-id="f0738-254">`WebApplicationFactory` 類別有助於設定 TestServer 的 ContentRoot，ASP.NET Core 用它來尋找靜態資源 (如檢視)。</span><span class="sxs-lookup"><span data-stu-id="f0738-254">The `WebApplicationFactory` class is helpful for configuring the TestServer's ContentRoot, which is used by ASP.NET Core to locate static resource like Views.</span></span>

<span data-ttu-id="f0738-255">您可以建立一個測試類別來建立簡單的功能測試 `IClassFixture\<WebApplicationFactory\<TEntry>>` ，其中 `TEntry` 是您的 web 應用程式 `Startup` 類別。</span><span class="sxs-lookup"><span data-stu-id="f0738-255">You can create simple functional tests by creating a test class that implements `IClassFixture\<WebApplicationFactory\<TEntry>>`, where `TEntry` is your web application's `Startup` class.</span></span> <span data-ttu-id="f0738-256">有了這個介面之後，您的測試裝置就可以使用 factory 的方法來建立用戶端 `CreateClient` ：</span><span class="sxs-lookup"><span data-stu-id="f0738-256">With this interface in place, your test fixture can create a client using the factory's `CreateClient` method:</span></span>

```csharp
public class BasicWebTests : IClassFixture<WebApplicationFactory<Startup>>
{
    protected readonly HttpClient _client;

    public BasicWebTests(WebApplicationFactory<Startup> factory)
    {
        _client = factory.CreateClient();
    }

    // write tests that use _client
}
```

<span data-ttu-id="f0738-257">通常，您會想要在每次執行測試之前，先執行一些額外的網站設定，例如將應用程式設定為使用記憶體內部資料存放區，然後使用測試資料植入應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0738-257">Frequently, you'll want to perform some additional configuration of your site before each test runs, such as configuring the application to use an in-memory data store and then seeding the application with test data.</span></span> <span data-ttu-id="f0738-258">若要達成這項功能，請建立您自己的子類別， `WebApplicationFactory\<TEntry>` 並覆寫它的 `ConfigureWebHost` 方法。</span><span class="sxs-lookup"><span data-stu-id="f0738-258">To achieve this functionality, create your own subclass of `WebApplicationFactory\<TEntry>` and override its `ConfigureWebHost` method.</span></span> <span data-ttu-id="f0738-259">下列範例取自 eShopOnWeb FunctionalTests 專案，並做為主要 Web 應用程式測試的一部分。</span><span class="sxs-lookup"><span data-stu-id="f0738-259">The example below is from the eShopOnWeb FunctionalTests project and is used as part of the tests on the main web application.</span></span>

```csharp
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Identity;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.EntityFrameworkCore;
using Microsoft.eShopWeb.Infrastructure.Data;
using Microsoft.eShopWeb.Infrastructure.Identity;
using Microsoft.eShopWeb.Web;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;

namespace Microsoft.eShopWeb.FunctionalTests.Web
{
    public class WebTestFixture : WebApplicationFactory<Startup>
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            builder.UseEnvironment("Testing");

            builder.ConfigureServices(services =>
            {
                 services.AddEntityFrameworkInMemoryDatabase();

                // Create a new service provider.
                var provider = services
                    .AddEntityFrameworkInMemoryDatabase()
                    .BuildServiceProvider();

                // Add a database context (ApplicationDbContext) using an in-memory
                // database for testing.
                services.AddDbContext<CatalogContext>(options =>
                {
                    options.UseInMemoryDatabase("InMemoryDbForTesting");
                    options.UseInternalServiceProvider(provider);
                });

                services.AddDbContext<AppIdentityDbContext>(options =>
                {
                    options.UseInMemoryDatabase("Identity");
                    options.UseInternalServiceProvider(provider);
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
                        .GetRequiredService<ILogger<WebTestFixture>>();

                    // Ensure the database is created.
                    db.Database.EnsureCreated();

                    try
                    {
                        // Seed the database with test data.
                        CatalogContextSeed.SeedAsync(db, loggerFactory).Wait();

                        // seed sample user data
                        var userManager = scopedServices.GetRequiredService<UserManager<ApplicationUser>>();
                        var roleManager = scopedServices.GetRequiredService<RoleManager<IdentityRole>>();
                        AppIdentityDbContextSeed.SeedAsync(userManager, roleManager).Wait();
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

<span data-ttu-id="f0738-260">測試可以利用這個自訂的 WebApplicationFactory，使用它來建立用戶端，然後再使用此用戶端執行個體對應用程式提出要求。</span><span class="sxs-lookup"><span data-stu-id="f0738-260">Tests can make use of this custom WebApplicationFactory by using it to create a client and then making requests to the application using this client instance.</span></span> <span data-ttu-id="f0738-261">應用程式內將會有植入的資料，測試的判斷提示會用到這些資料。</span><span class="sxs-lookup"><span data-stu-id="f0738-261">The application will have data seeded that can be used as part of the test's assertions.</span></span> <span data-ttu-id="f0738-262">下列測試會確認 eShopOnWeb 應用程式的首頁可正確載入，並包含作為種子資料一部分新增到應用程式的產品清單。</span><span class="sxs-lookup"><span data-stu-id="f0738-262">The following test verifies that the home page of the eShopOnWeb application loads correctly and includes a product listing that was added to the application as part of the seed data.</span></span>

```csharp
using Microsoft.eShopWeb.FunctionalTests.Web;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace Microsoft.eShopWeb.FunctionalTests.WebRazorPages
{
    [Collection("Sequential")]
    public class HomePageOnGet : IClassFixture<WebTestFixture>
    {
        public HomePageOnGet(WebTestFixture factory)
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
            Assert.Contains(".NET Bot Black Sweatshirt", stringResponse);
        }
    }
}
```

<span data-ttu-id="f0738-263">這項功能測試會演練完整 ASP.NET Core MVC/Razor Pages 應用程式堆疊，包括可能已存在的所有中介軟體、篩選器和系結器。</span><span class="sxs-lookup"><span data-stu-id="f0738-263">This functional test exercises the full ASP.NET Core MVC / Razor Pages application stack, including all middleware, filters, and binders that may be in place.</span></span> <span data-ttu-id="f0738-264">它會確認指定的路由 ("/") 會傳回預期的成功狀態碼和 HTML 輸出。</span><span class="sxs-lookup"><span data-stu-id="f0738-264">It verifies that a given route ("/") returns the expected success status code and HTML output.</span></span> <span data-ttu-id="f0738-265">如此一來，就不需要設定真正的網頁伺服器，而且可以避免大部分使用真實 web 伺服器進行測試的肯定脆弱度，例如 (防火牆設定) 的問題。</span><span class="sxs-lookup"><span data-stu-id="f0738-265">It does so without setting up a real web server, and avoids much of the brittleness that using a real web server for testing can experience (for example, problems with firewall settings).</span></span> <span data-ttu-id="f0738-266">針對 TestServer 執行的功能測試通常比整合與單元測試要慢，但比在網路上執行測試之網頁伺服器的測試要快得多。</span><span class="sxs-lookup"><span data-stu-id="f0738-266">Functional tests that run against TestServer are usually slower than integration and unit tests, but are much faster than tests that would run over the network to a test web server.</span></span> <span data-ttu-id="f0738-267">使用功能測試，確保應用程式的前端堆疊如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="f0738-267">Use functional tests to ensure your application's front-end stack is working as expected.</span></span> <span data-ttu-id="f0738-268">當您在控制器或頁面中找到重複項目並透過新增篩選器來處理這些項目時，這些測試會特別有用。</span><span class="sxs-lookup"><span data-stu-id="f0738-268">These tests are especially useful when you find duplication in your controllers or pages and you address the duplication by adding filters.</span></span> <span data-ttu-id="f0738-269">在理想情況下，這種重構不會變更應用程式的行為，而一整套功能測試會確認合乎該情況。</span><span class="sxs-lookup"><span data-stu-id="f0738-269">Ideally, this refactoring won't change the behavior of the application, and a suite of functional tests will verify this is the case.</span></span>

> ### <a name="references--test-aspnet-core-mvc-apps"></a><span data-ttu-id="f0738-270">參考 - 測試 ASP.NET Core MVC 應用程式</span><span class="sxs-lookup"><span data-stu-id="f0738-270">References – Test ASP.NET Core MVC apps</span></span>
>
> - <span data-ttu-id="f0738-271">**ASP.NET Core 中的測試** </span><span class="sxs-lookup"><span data-stu-id="f0738-271">**Testing in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/testing/>
> - <span data-ttu-id="f0738-272">**單元測試命名慣例** </span><span class="sxs-lookup"><span data-stu-id="f0738-272">**Unit Test Naming Convention** </span></span>\
>   <https://ardalis.com/unit-test-naming-convention>
> - <span data-ttu-id="f0738-273">**測試 EF Core** </span><span class="sxs-lookup"><span data-stu-id="f0738-273">**Testing EF Core** </span></span>\
>   <https://docs.microsoft.com/ef/core/miscellaneous/testing/>
> - <span data-ttu-id="f0738-274">**ASP.NET Core 中的整合測試** </span><span class="sxs-lookup"><span data-stu-id="f0738-274">**Integration tests in ASP.NET Core** </span></span>\
>   <https://docs.microsoft.com/aspnet/core/test/integration-tests>

>[!div class="step-by-step"]
><span data-ttu-id="f0738-275">[上一個](work-with-data-in-asp-net-core-apps.md) 
>[下一步](development-process-for-azure.md)</span><span class="sxs-lookup"><span data-stu-id="f0738-275">[Previous](work-with-data-in-asp-net-core-apps.md)
[Next](development-process-for-azure.md)</span></span>
