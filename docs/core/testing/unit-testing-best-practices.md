---
title: 撰寫單元測試的最佳做法
description: 了解撰寫單元測試的最佳做法，提高程式碼品質和復原功能
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.openlocfilehash: 00a0b999c9a08b04cb33bcb3a332513292beb363
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143404"
---
# <a name="unit-testing-best-practices"></a><span data-ttu-id="80ce6-103">單元測試最佳做法</span><span class="sxs-lookup"><span data-stu-id="80ce6-103">Unit testing best practices</span></span>

<span data-ttu-id="80ce6-104">作者：[John Reese](http://reesespieces.io) (特別感謝 [Roy Osherove](http://osherove.com/))</span><span class="sxs-lookup"><span data-stu-id="80ce6-104">By [John Reese](http://reesespieces.io) with special thanks to [Roy Osherove](http://osherove.com/)</span></span>

<span data-ttu-id="80ce6-105">撰寫單元測試有許多優點；運用迴歸加以協助、提供文件，並增進良好的設計。</span><span class="sxs-lookup"><span data-stu-id="80ce6-105">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="80ce6-106">不過，難以閱讀且容易損毀的單元測試可能會破壞程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="80ce6-106">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span>

<span data-ttu-id="80ce6-107">本指南中，您將了解一些撰寫單元測試時的最佳做法，讓您的測試保有復原能力且易於了解。</span><span class="sxs-lookup"><span data-stu-id="80ce6-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="80ce6-108">為何選擇單元測試？</span><span class="sxs-lookup"><span data-stu-id="80ce6-108">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="80ce6-109">執行功能測試的時間較少</span><span class="sxs-lookup"><span data-stu-id="80ce6-109">Less time performing functional tests</span></span>
<span data-ttu-id="80ce6-110">功能測試很耗費資源。</span><span class="sxs-lookup"><span data-stu-id="80ce6-110">Functional tests are expensive.</span></span> <span data-ttu-id="80ce6-111">功能測試通常涉及開啟應用程式，以及執行您 (或其他人) 必須遵循的一系列步驟，藉此驗證預期行為。</span><span class="sxs-lookup"><span data-stu-id="80ce6-111">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="80ce6-112">測試人員不一定會熟悉這些步驟，表示他們必須連絡該領域中更加專業的人員，才得以執行測試。</span><span class="sxs-lookup"><span data-stu-id="80ce6-112">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="80ce6-113">對於較細瑣的變更，測試本身可能需要費時幾秒鐘，而對於較大的變更，可能會花上幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="80ce6-113">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="80ce6-114">最後，將必須對您在系統中所做的所有變更重複執行此程序。</span><span class="sxs-lookup"><span data-stu-id="80ce6-114">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="80ce6-115">另一方面，單元測試只需費時幾毫秒，按下按鈕便可執行，並不需要有整個系統的相關知識。</span><span class="sxs-lookup"><span data-stu-id="80ce6-115">Unit tests, on the other hand, take milliseconds, can be run at the press of a button and do not necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="80ce6-116">測試通過或失敗取決於測試執行者，而不是個人。</span><span class="sxs-lookup"><span data-stu-id="80ce6-116">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="80ce6-117">對於迴歸的保護</span><span class="sxs-lookup"><span data-stu-id="80ce6-117">Protection against regression</span></span>
<span data-ttu-id="80ce6-118">迴歸缺失是對應用程式進行變更時帶來的缺失。</span><span class="sxs-lookup"><span data-stu-id="80ce6-118">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="80ce6-119">通常測試人員不僅要測試其新功能，也要測試早已存在的功能，確認先前實作的功能仍可如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="80ce6-119">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="80ce6-120">利用單元測試，您就可以在每次建置之後，甚至是您變更程式碼行之後，重新執行一整套測試。</span><span class="sxs-lookup"><span data-stu-id="80ce6-120">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="80ce6-121">讓您確信新的程式碼不會中斷現有的功能。</span><span class="sxs-lookup"><span data-stu-id="80ce6-121">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="80ce6-122">可執行檔文件</span><span class="sxs-lookup"><span data-stu-id="80ce6-122">Executable documentation</span></span>
<span data-ttu-id="80ce6-123">在提供特定輸入的情況下，特定方法的用途或其運作方式不一定很明顯。</span><span class="sxs-lookup"><span data-stu-id="80ce6-123">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="80ce6-124">您可能會自問：如果我將空白字串傳遞給此方法，其運作方式為何？</span><span class="sxs-lookup"><span data-stu-id="80ce6-124">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="80ce6-125">Null 呢？</span><span class="sxs-lookup"><span data-stu-id="80ce6-125">Null?</span></span>

<span data-ttu-id="80ce6-126">如果您有一套妥善命名的單元測試，每個測試都應該能清楚說明給定輸入的預期輸出。</span><span class="sxs-lookup"><span data-stu-id="80ce6-126">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="80ce6-127">此外，應該還能確認它實際上可正常運作。</span><span class="sxs-lookup"><span data-stu-id="80ce6-127">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="80ce6-128">結合的程式碼較少</span><span class="sxs-lookup"><span data-stu-id="80ce6-128">Less coupled code</span></span>
<span data-ttu-id="80ce6-129">當程式碼緊密結合時，可能難以進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="80ce6-129">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="80ce6-130">如果不針對您所撰寫的程式碼建立單元測試，結合程度就可能較不明顯。</span><span class="sxs-lookup"><span data-stu-id="80ce6-130">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="80ce6-131">為您的程式碼撰寫測試時會自然分離程式碼，否則它會更難以測試。</span><span class="sxs-lookup"><span data-stu-id="80ce6-131">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="80ce6-132">良好單元測試的特性</span><span class="sxs-lookup"><span data-stu-id="80ce6-132">Characteristics of a good unit test</span></span>
- <span data-ttu-id="80ce6-133">**快速**。</span><span class="sxs-lookup"><span data-stu-id="80ce6-133">**Fast**.</span></span> <span data-ttu-id="80ce6-134">具有數千個單元測試的成熟專案並不罕見。</span><span class="sxs-lookup"><span data-stu-id="80ce6-134">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="80ce6-135">單元測試應只需要極少的時間執行。</span><span class="sxs-lookup"><span data-stu-id="80ce6-135">Unit tests should take very little time to run.</span></span> <span data-ttu-id="80ce6-136">毫秒。</span><span class="sxs-lookup"><span data-stu-id="80ce6-136">Milliseconds.</span></span>
- <span data-ttu-id="80ce6-137">**隔離**。</span><span class="sxs-lookup"><span data-stu-id="80ce6-137">**Isolated**.</span></span> <span data-ttu-id="80ce6-138">單元測試是獨立的，可以單獨執行，並且對所有外部因素 (例如檔案系統或資料庫) 沒有任何相依性。</span><span class="sxs-lookup"><span data-stu-id="80ce6-138">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="80ce6-139">**可重複**。</span><span class="sxs-lookup"><span data-stu-id="80ce6-139">**Repeatable**.</span></span> <span data-ttu-id="80ce6-140">執行單元測試應該與其結果一致，亦即，如果您未變更回合之間的任何項目，會一律傳回相同的結果。</span><span class="sxs-lookup"><span data-stu-id="80ce6-140">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="80ce6-141">**自我檢查**。</span><span class="sxs-lookup"><span data-stu-id="80ce6-141">**Self-Checking**.</span></span> <span data-ttu-id="80ce6-142">測試應該能夠自行偵測到通過或失敗，不需要任何人為互動。</span><span class="sxs-lookup"><span data-stu-id="80ce6-142">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="80ce6-143">**及時**。</span><span class="sxs-lookup"><span data-stu-id="80ce6-143">**Timely**.</span></span> <span data-ttu-id="80ce6-144">相較於所測試的程式碼，單元測試不應耗費不成比例的冗長時間來撰寫。</span><span class="sxs-lookup"><span data-stu-id="80ce6-144">A unit test should not take a disproportionally long time to write compared to the code being tested.</span></span> <span data-ttu-id="80ce6-145">相較於撰寫程式碼，如果您發現測試程式碼花費大量時間，請考慮使用更易於測試的設計。</span><span class="sxs-lookup"><span data-stu-id="80ce6-145">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="80ce6-146">讓我們使用相同的語言</span><span class="sxs-lookup"><span data-stu-id="80ce6-146">Let's speak the same language</span></span>
<span data-ttu-id="80ce6-147">說到測試，遺憾的是「模擬」(*mock*) 一詞遭到誤用。</span><span class="sxs-lookup"><span data-stu-id="80ce6-147">The term *mock* is unfortunately very misused when talking about testing.</span></span> <span data-ttu-id="80ce6-148">以下將定義撰寫單元測試時最常見的 *fakes* 類型：</span><span class="sxs-lookup"><span data-stu-id="80ce6-148">The following defines the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="80ce6-149">假功能 (*Fake*) - 假功能是一般詞彙，用來描述虛設常式或模擬物件。</span><span class="sxs-lookup"><span data-stu-id="80ce6-149">*Fake* - A fake is a generic term which can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="80ce6-150">至於是虛設常式還是模擬，取決於使用的內容而定。</span><span class="sxs-lookup"><span data-stu-id="80ce6-150">Whether it is a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="80ce6-151">因此，換句話說，假功能可以是虛設常式或是模擬。</span><span class="sxs-lookup"><span data-stu-id="80ce6-151">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="80ce6-152">模擬 (*Mock*) - 模擬物件是系統中的假物件，可決定單元測試通過或失敗。</span><span class="sxs-lookup"><span data-stu-id="80ce6-152">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="80ce6-153">模擬一開始是假功能，直到另行判定為止。</span><span class="sxs-lookup"><span data-stu-id="80ce6-153">A mock starts out as a Fake until it is asserted against.</span></span>

<span data-ttu-id="80ce6-154">虛設常式 (*Stub*) - 虛設常式是系統中現有相依性 (或共同作業者) 的可控制取代項目。</span><span class="sxs-lookup"><span data-stu-id="80ce6-154">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="80ce6-155">藉由使用虛設常式，您可以測試程式碼，而不必直接處理相依性。</span><span class="sxs-lookup"><span data-stu-id="80ce6-155">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="80ce6-156">根據預設，假功能一開始是虛設常式。</span><span class="sxs-lookup"><span data-stu-id="80ce6-156">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="80ce6-157">請考慮下列程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="80ce6-157">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="80ce6-158">這是稱為模擬 (mock) 的虛設常式範例。</span><span class="sxs-lookup"><span data-stu-id="80ce6-158">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="80ce6-159">在此情況下為虛設常式。</span><span class="sxs-lookup"><span data-stu-id="80ce6-159">In this case, it is a stub.</span></span> <span data-ttu-id="80ce6-160">您只是傳入訂單，作為能夠具現化 `Purchase` (待測系統) 的方法。</span><span class="sxs-lookup"><span data-stu-id="80ce6-160">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="80ce6-161">名稱 `MockOrder` 也很容易產生誤導，因為訂單並不是模擬。</span><span class="sxs-lookup"><span data-stu-id="80ce6-161">The name `MockOrder` is also very misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="80ce6-162">更好的方式會是</span><span class="sxs-lookup"><span data-stu-id="80ce6-162">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="80ce6-163">透過將類別重新命名為 `FakeOrder`，您已使該類別更加通用，因此可將該類別作為模擬或虛設常式使用。</span><span class="sxs-lookup"><span data-stu-id="80ce6-163">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="80ce6-164">請取其更適合測試案例者。</span><span class="sxs-lookup"><span data-stu-id="80ce6-164">Whichever is better for the test case.</span></span> <span data-ttu-id="80ce6-165">在上述範例中，`FakeOrder` 作為虛設常式使用。</span><span class="sxs-lookup"><span data-stu-id="80ce6-165">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="80ce6-166">在判定期間，您沒有以任何形式使用 `FakeOrder`。</span><span class="sxs-lookup"><span data-stu-id="80ce6-166">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="80ce6-167">`FakeOrder` 只是傳入 `Purchase` 類別以滿足建構函式的需求。</span><span class="sxs-lookup"><span data-stu-id="80ce6-167">`FakeOrder` was just passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="80ce6-168">若要用作模擬，您可以執行類似下述內容</span><span class="sxs-lookup"><span data-stu-id="80ce6-168">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="80ce6-169">在此情況下，您正在檢查假功能上的屬性 (另行判定)，因此在上述程式碼片段中，屬性 `mockOrder` 是模擬。</span><span class="sxs-lookup"><span data-stu-id="80ce6-169">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="80ce6-170">請務必正確使用這個術語。</span><span class="sxs-lookup"><span data-stu-id="80ce6-170">It's important to get this terminology correct.</span></span> <span data-ttu-id="80ce6-171">如果您將虛設常式稱為「模擬」，其他開發人員會對您的意圖帶有錯誤的假設。</span><span class="sxs-lookup"><span data-stu-id="80ce6-171">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="80ce6-172">關於模擬與虛設常式要記住的重點在於，模擬就像虛設常式一樣，只是您會對模擬物件另行判定，而不會對虛設常式另行判定。</span><span class="sxs-lookup"><span data-stu-id="80ce6-172">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="80ce6-173">最佳作法</span><span class="sxs-lookup"><span data-stu-id="80ce6-173">Best practices</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="80ce6-174">為測試命名</span><span class="sxs-lookup"><span data-stu-id="80ce6-174">Naming your tests</span></span>
<span data-ttu-id="80ce6-175">測試的名稱應該包含三個部分：</span><span class="sxs-lookup"><span data-stu-id="80ce6-175">The name of your test should consist of three parts:</span></span>
- <span data-ttu-id="80ce6-176">所測試的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="80ce6-176">The name of the method being tested.</span></span>
- <span data-ttu-id="80ce6-177">用以測試的案例。</span><span class="sxs-lookup"><span data-stu-id="80ce6-177">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="80ce6-178">叫用案例時的預期行為。</span><span class="sxs-lookup"><span data-stu-id="80ce6-178">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="80ce6-179">為什麼？</span><span class="sxs-lookup"><span data-stu-id="80ce6-179">Why?</span></span>
- <span data-ttu-id="80ce6-180">命名標準很重要，因為名稱會明確表示測試目的。</span><span class="sxs-lookup"><span data-stu-id="80ce6-180">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="80ce6-181">測試不只要確定您的程式碼能夠運作，還會提供文件。</span><span class="sxs-lookup"><span data-stu-id="80ce6-181">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="80ce6-182">只要查看這套單元測試，您應能推斷程式碼的行為，甚至無需查看程式碼本身。</span><span class="sxs-lookup"><span data-stu-id="80ce6-182">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="80ce6-183">此外，當測試失敗時，您可以確切看到哪些案例不符合預期。</span><span class="sxs-lookup"><span data-stu-id="80ce6-183">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="80ce6-184">不良：</span><span class="sxs-lookup"><span data-stu-id="80ce6-184">Bad:</span></span>
[!code-csharp[BeforeNaming](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="80ce6-185">較佳：</span><span class="sxs-lookup"><span data-stu-id="80ce6-185">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="80ce6-186">排列測試</span><span class="sxs-lookup"><span data-stu-id="80ce6-186">Arranging your tests</span></span>
<span data-ttu-id="80ce6-187">**排列、採取動作、判定**是進行單元測試時的常見模式。</span><span class="sxs-lookup"><span data-stu-id="80ce6-187">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="80ce6-188">顧名思義，其中包含三個主要動作：</span><span class="sxs-lookup"><span data-stu-id="80ce6-188">As the name implies, it consists of three main actions:</span></span>
- <span data-ttu-id="80ce6-189">「排列」物件，並視需要建立和設定這些物件。</span><span class="sxs-lookup"><span data-stu-id="80ce6-189">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="80ce6-190">對物件「採取動作」。</span><span class="sxs-lookup"><span data-stu-id="80ce6-190">*Act* on an object.</span></span>
- <span data-ttu-id="80ce6-191">「判定」某個項目如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="80ce6-191">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="80ce6-192">為什麼？</span><span class="sxs-lookup"><span data-stu-id="80ce6-192">Why?</span></span>
- <span data-ttu-id="80ce6-193">清楚分隔正在測試的項目與「排列」和「判定」步驟。</span><span class="sxs-lookup"><span data-stu-id="80ce6-193">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="80ce6-194">這麼做可使判定與「採取動作」程式碼相互摻雜的機率更低。</span><span class="sxs-lookup"><span data-stu-id="80ce6-194">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="80ce6-195">可讀性是撰寫測試時最重要的層面之一。</span><span class="sxs-lookup"><span data-stu-id="80ce6-195">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="80ce6-196">分隔測試內的每個動作可清楚突顯呼叫程式碼、如何呼叫程式碼，以及您嘗試進行判定所需的相依性。</span><span class="sxs-lookup"><span data-stu-id="80ce6-196">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="80ce6-197">雖然可以合併某些步驟並減少測試的大小，但主要目標是盡可能讓測試可讀。</span><span class="sxs-lookup"><span data-stu-id="80ce6-197">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="80ce6-198">不良：</span><span class="sxs-lookup"><span data-stu-id="80ce6-198">Bad:</span></span>
[!code-csharp[BeforeArranging](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="80ce6-199">較佳：</span><span class="sxs-lookup"><span data-stu-id="80ce6-199">Better:</span></span>
[!code-csharp[AfterArranging](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="80ce6-200">撰寫最低限度通過測試</span><span class="sxs-lookup"><span data-stu-id="80ce6-200">Write minimally passing tests</span></span>
<span data-ttu-id="80ce6-201">要在單元測試中使用的輸入應該是最簡單的，才能驗證您目前正在測試的行為。</span><span class="sxs-lookup"><span data-stu-id="80ce6-201">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="80ce6-202">為什麼？</span><span class="sxs-lookup"><span data-stu-id="80ce6-202">Why?</span></span>
- <span data-ttu-id="80ce6-203">測試對程式碼基底的未來變更變得更具復原性。</span><span class="sxs-lookup"><span data-stu-id="80ce6-203">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="80ce6-204">更接近測試行為而不是實作。</span><span class="sxs-lookup"><span data-stu-id="80ce6-204">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="80ce6-205">如果測試包含的資訊比通過測試所需還要多，更有可能會將錯誤帶進測試中，且會讓測試的意圖較不清楚。</span><span class="sxs-lookup"><span data-stu-id="80ce6-205">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="80ce6-206">撰寫測試時，您想要著重於行為。</span><span class="sxs-lookup"><span data-stu-id="80ce6-206">When writing tests you want to focus on the behavior.</span></span> <span data-ttu-id="80ce6-207">在模型上設定額外的屬性，或在不需要時使用非零值，只會減損您嘗試證明的項目。</span><span class="sxs-lookup"><span data-stu-id="80ce6-207">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="80ce6-208">不良：</span><span class="sxs-lookup"><span data-stu-id="80ce6-208">Bad:</span></span>
[!code-csharp[BeforeMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="80ce6-209">較佳：</span><span class="sxs-lookup"><span data-stu-id="80ce6-209">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="80ce6-210">避免魔術字串</span><span class="sxs-lookup"><span data-stu-id="80ce6-210">Avoid magic strings</span></span>
<span data-ttu-id="80ce6-211">相較於在生產環境程式碼中為變數命名，在單元測試中為變數命名的重要性有過之而無不及。</span><span class="sxs-lookup"><span data-stu-id="80ce6-211">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="80ce6-212">單元測試不應該包含魔術字串。</span><span class="sxs-lookup"><span data-stu-id="80ce6-212">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="80ce6-213">為什麼？</span><span class="sxs-lookup"><span data-stu-id="80ce6-213">Why?</span></span>
- <span data-ttu-id="80ce6-214">避免測試的讀者為了找出使該值變得特殊的原因而需要檢查生產環境程式碼。</span><span class="sxs-lookup"><span data-stu-id="80ce6-214">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="80ce6-215">明確地顯示您想要「證明」的項目，而不是嘗試「完成」的項目。</span><span class="sxs-lookup"><span data-stu-id="80ce6-215">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="80ce6-216">魔術字串可能會對測試的讀者造成混淆。</span><span class="sxs-lookup"><span data-stu-id="80ce6-216">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="80ce6-217">如果字串看起來不正常，讀者可能會納悶為什麼針對參數或傳回值選擇特定值。</span><span class="sxs-lookup"><span data-stu-id="80ce6-217">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="80ce6-218">這可能會導致他們過於仔細查看實作詳細資料，而不是專注於測試。</span><span class="sxs-lookup"><span data-stu-id="80ce6-218">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP] 
> <span data-ttu-id="80ce6-219">在撰寫測試時，您的目標應該是盡可能表達意圖。</span><span class="sxs-lookup"><span data-stu-id="80ce6-219">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="80ce6-220">如果是魔術字串，將這些值指派給常數會是不錯的方法。</span><span class="sxs-lookup"><span data-stu-id="80ce6-220">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="80ce6-221">不良：</span><span class="sxs-lookup"><span data-stu-id="80ce6-221">Bad:</span></span>
[!code-csharp[BeforeMagicString](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="80ce6-222">較佳：</span><span class="sxs-lookup"><span data-stu-id="80ce6-222">Better:</span></span>
[!code-csharp[AfterMagicString](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="80ce6-223">避免在測試中使用邏輯</span><span class="sxs-lookup"><span data-stu-id="80ce6-223">Avoid logic in tests</span></span>
<span data-ttu-id="80ce6-224">撰寫您的單元測試時，請避免使用手動字串串連和邏輯條件，例如 `if`、`while`、`for`、`switch` 等等。</span><span class="sxs-lookup"><span data-stu-id="80ce6-224">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="80ce6-225">為什麼？</span><span class="sxs-lookup"><span data-stu-id="80ce6-225">Why?</span></span>
- <span data-ttu-id="80ce6-226">在測試內帶進 Bug 的機率更低。</span><span class="sxs-lookup"><span data-stu-id="80ce6-226">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="80ce6-227">著重最終結果，而不是實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="80ce6-227">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="80ce6-228">將邏輯引入您的測試套件時，在其中帶進 Bug 的機率會大幅增加。</span><span class="sxs-lookup"><span data-stu-id="80ce6-228">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="80ce6-229">您不會想要在您的測試套件尋找 Bug。</span><span class="sxs-lookup"><span data-stu-id="80ce6-229">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="80ce6-230">您應該對測試正確運作的結果具有高度信心，否則您不會信任測試。</span><span class="sxs-lookup"><span data-stu-id="80ce6-230">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="80ce6-231">您不信任的測試將無法提供任何價值。</span><span class="sxs-lookup"><span data-stu-id="80ce6-231">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="80ce6-232">當測試失敗時，您要意識到確實是程式碼發生問題，且無法予以忽略。</span><span class="sxs-lookup"><span data-stu-id="80ce6-232">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="80ce6-233">如果測試中的邏輯看似無法避免，請考慮將測試分割成兩個或多個不同的測試。</span><span class="sxs-lookup"><span data-stu-id="80ce6-233">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="80ce6-234">不良：</span><span class="sxs-lookup"><span data-stu-id="80ce6-234">Bad:</span></span>
[!code-csharp[LogicInTests](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="80ce6-235">較佳：</span><span class="sxs-lookup"><span data-stu-id="80ce6-235">Better:</span></span>
[!code-csharp[AfterTestLogic](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="80ce6-236">慣用 Helper 方法來設定及終止</span><span class="sxs-lookup"><span data-stu-id="80ce6-236">Prefer helper methods to setup and teardown</span></span>
<span data-ttu-id="80ce6-237">如果您的測試需要類似的物件或狀態，比起利用 Setup 和 Teardown 屬性 (若有)，更慣用 Helper 方法。</span><span class="sxs-lookup"><span data-stu-id="80ce6-237">If you require a similar object or state for your tests, prefer a helper method than leveraging Setup and Teardown attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="80ce6-238">為什麼？</span><span class="sxs-lookup"><span data-stu-id="80ce6-238">Why?</span></span>
- <span data-ttu-id="80ce6-239">讀取測試時混淆較少，因為在每個測試內都可以看見所有的程式碼。</span><span class="sxs-lookup"><span data-stu-id="80ce6-239">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="80ce6-240">對於給定的測試，設定太多或太少的機率更低。</span><span class="sxs-lookup"><span data-stu-id="80ce6-240">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="80ce6-241">在測試之間共用狀態，進而在測試之間建立非必要相依性的機率更低。</span><span class="sxs-lookup"><span data-stu-id="80ce6-241">Less chance of sharing state between tests which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="80ce6-242">在單元測試架構中，會在測試套件內的每個單元測試之前或其中呼叫 `Setup`。</span><span class="sxs-lookup"><span data-stu-id="80ce6-242">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="80ce6-243">雖然有人可能會認為這是很有用的工具，但它最後通常會導致測試過大且難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="80ce6-243">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="80ce6-244">每個測試通常會有不同的需求，以便啟動及執測試。</span><span class="sxs-lookup"><span data-stu-id="80ce6-244">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="80ce6-245">不幸的是，`Setup` 會強迫您針對每個測試使用完全相同的需求。</span><span class="sxs-lookup"><span data-stu-id="80ce6-245">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE] 
> <span data-ttu-id="80ce6-246">自 2.x 版開始，xUnit 已移除 Setup 及 TearDown 這兩者</span><span class="sxs-lookup"><span data-stu-id="80ce6-246">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="80ce6-247">不良：</span><span class="sxs-lookup"><span data-stu-id="80ce6-247">Bad:</span></span>
[!code-csharp[BeforeSetup](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="80ce6-248">較佳：</span><span class="sxs-lookup"><span data-stu-id="80ce6-248">Better:</span></span>
[!code-csharp[AfterHelperMethod](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="80ce6-249">避免多個判定</span><span class="sxs-lookup"><span data-stu-id="80ce6-249">Avoid multiple asserts</span></span>
<span data-ttu-id="80ce6-250">在撰寫測試時，請嘗試於每個測試只包含一個判定。</span><span class="sxs-lookup"><span data-stu-id="80ce6-250">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="80ce6-251">只使用一個判定的常見方法包括：</span><span class="sxs-lookup"><span data-stu-id="80ce6-251">Common approaches to using only one assert include:</span></span>
- <span data-ttu-id="80ce6-252">為每個判定建立個別測試。</span><span class="sxs-lookup"><span data-stu-id="80ce6-252">Create a separate test for each assert.</span></span>
- <span data-ttu-id="80ce6-253">使用參數化測試。</span><span class="sxs-lookup"><span data-stu-id="80ce6-253">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="80ce6-254">為什麼？</span><span class="sxs-lookup"><span data-stu-id="80ce6-254">Why?</span></span>
- <span data-ttu-id="80ce6-255">如果某個判定失敗，將不會評估後續的判定。</span><span class="sxs-lookup"><span data-stu-id="80ce6-255">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="80ce6-256">確保您不會在測試中判定多個案例。</span><span class="sxs-lookup"><span data-stu-id="80ce6-256">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="80ce6-257">為您提供測試失敗原因的全貌。</span><span class="sxs-lookup"><span data-stu-id="80ce6-257">Gives you the entire picture as to why your tests are failing.</span></span> 

<span data-ttu-id="80ce6-258">將多個判定帶進測試案例時，並不保證所有的判定皆會執行。</span><span class="sxs-lookup"><span data-stu-id="80ce6-258">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="80ce6-259">在大部分的單元測試架構中，一旦判定在單元測試中失敗，進行中的測試將自動視為失敗。</span><span class="sxs-lookup"><span data-stu-id="80ce6-259">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="80ce6-260">這可能會令人困惑，因為實際運作的功能會顯示為失敗。</span><span class="sxs-lookup"><span data-stu-id="80ce6-260">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="80ce6-261">這項規則的常見例外狀況是針對物件進行判定時。</span><span class="sxs-lookup"><span data-stu-id="80ce6-261">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="80ce6-262">在此情況下，通常可以接受對每個屬性擁有多個判定，確保物件處於您預期的狀態。</span><span class="sxs-lookup"><span data-stu-id="80ce6-262">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="80ce6-263">不良：</span><span class="sxs-lookup"><span data-stu-id="80ce6-263">Bad:</span></span>
[!code-csharp[BeforeMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="80ce6-264">較佳：</span><span class="sxs-lookup"><span data-stu-id="80ce6-264">Better:</span></span>
[!code-csharp[AfterMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="80ce6-265">透過單元測試的公用方法驗證私用方法</span><span class="sxs-lookup"><span data-stu-id="80ce6-265">Validate private methods by unit testing public methods</span></span>
<span data-ttu-id="80ce6-266">在大部分情況下，應該不需要測試私用方法。</span><span class="sxs-lookup"><span data-stu-id="80ce6-266">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="80ce6-267">私用方法是實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="80ce6-267">Private methods are an implementation detail.</span></span> <span data-ttu-id="80ce6-268">您可以這樣來看：私用方法永遠不會單獨存在。</span><span class="sxs-lookup"><span data-stu-id="80ce6-268">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="80ce6-269">在某個時間點，將有一個公眾對應方法呼叫私用方法作為其實作的一部分。</span><span class="sxs-lookup"><span data-stu-id="80ce6-269">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="80ce6-270">您應該關注的是呼叫私用方法的公用方法最終結果。</span><span class="sxs-lookup"><span data-stu-id="80ce6-270">What you should care about is the end result of the public method that calls into the private one.</span></span> 

<span data-ttu-id="80ce6-271">請考慮下列情況</span><span class="sxs-lookup"><span data-stu-id="80ce6-271">Consider the following case</span></span>

```csharp
public string ParseLogLine(string input)
{
    var sanitizedInput = trimInput(input);
    return sanitizedInput;
}

private string trimInput(string input)
{
    return input.Trim();
}
```

<span data-ttu-id="80ce6-272">您的第一個反應可能是開始撰寫 `trimInput` 的測試，因為您想要確定該方法是否如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="80ce6-272">Your first reaction may be to start writing a test for `trimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="80ce6-273">不過，`ParseLogLine` 很有可能會以非預期的方式操作 `sanitizedInput`，使得對 `trimInput` 的測試變得毫無用處。</span><span class="sxs-lookup"><span data-stu-id="80ce6-273">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `trimInput` useless.</span></span> 

<span data-ttu-id="80ce6-274">實際的測試應該針對公眾對應方法 `ParseLogLine` 執行，因為這才是您最應關注的項目。</span><span class="sxs-lookup"><span data-stu-id="80ce6-274">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span> 

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="80ce6-275">從這個觀點來看，如果您看到私用方法，請找出公開方法，並針對該方法撰寫您的測試。</span><span class="sxs-lookup"><span data-stu-id="80ce6-275">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="80ce6-276">私用方法傳回預期結果，並不表示最終呼叫私用方法的系統會正確地使用結果。</span><span class="sxs-lookup"><span data-stu-id="80ce6-276">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="80ce6-277">虛設 (Stub) 靜態參考</span><span class="sxs-lookup"><span data-stu-id="80ce6-277">Stub static references</span></span>
<span data-ttu-id="80ce6-278">單元測試的其中一個準則是，其必須具有待測系統的完整控制權。</span><span class="sxs-lookup"><span data-stu-id="80ce6-278">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="80ce6-279">這可能會在生產環境程式碼包含靜態參考呼叫時 (例如 `DateTime.Now`) 造成問題。</span><span class="sxs-lookup"><span data-stu-id="80ce6-279">This can be problematic when production code includes calls to static references (e.g. `DateTime.Now`).</span></span> <span data-ttu-id="80ce6-280">請考慮下列程式碼</span><span class="sxs-lookup"><span data-stu-id="80ce6-280">Consider the following code</span></span>

```csharp
public int GetDiscountedPrice(int price)
{
    if(DateTime.Now == DayOfWeek.Tuesday) 
    {
        return price / 2;
    }
    else 
    {
        return price;
    }
}
```

<span data-ttu-id="80ce6-281">如何對此程式碼進行單元測試？</span><span class="sxs-lookup"><span data-stu-id="80ce6-281">How can this code possibly be unit tested?</span></span> <span data-ttu-id="80ce6-282">您可以嘗試一種方法，例如</span><span class="sxs-lookup"><span data-stu-id="80ce6-282">You may try an approach such as</span></span>

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(2, actual)
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();

    var actual = priceCalculator.GetDiscountedPrice(2);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="80ce6-283">不幸的是，您很快就會發現測試有幾個問題。</span><span class="sxs-lookup"><span data-stu-id="80ce6-283">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span> 

- <span data-ttu-id="80ce6-284">如果測試套件是在星期二執行，第二項測試會通過，但第一項測試會失敗。</span><span class="sxs-lookup"><span data-stu-id="80ce6-284">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="80ce6-285">如果測試套件是在其他天執行，第一項測試會通過，但第二項測試會失敗。</span><span class="sxs-lookup"><span data-stu-id="80ce6-285">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="80ce6-286">若要解決這些問題，您需要將「接合線」帶進生產環境程式碼。</span><span class="sxs-lookup"><span data-stu-id="80ce6-286">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="80ce6-287">其中一個方法是在介面中包裝您需要控制的程式碼，並使生產環境程式碼相依於該介面。</span><span class="sxs-lookup"><span data-stu-id="80ce6-287">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

```csharp
public interface IDateTimeProvider
{
    DayOfWeek DayOfWeek();
}

public int GetDiscountedPrice(int price, IDateTimeProvider dateTimeProvider)
{
    if(dateTimeProvider.DayOfWeek() == DayOfWeek.Tuesday) 
    {
        return price / 2;
    }
    else 
    {
        return price;
    }
}
```

<span data-ttu-id="80ce6-288">您的測試套件現在已變成</span><span class="sxs-lookup"><span data-stu-id="80ce6-288">Your test suite now becomes</span></span>

```csharp
public void GetDiscountedPrice_ByDefault_ReturnsFullPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Monday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(2, actual);
}

public void GetDiscountedPrice_OnTuesday_ReturnsHalfPrice()
{
    var priceCalculator = new PriceCalculator();
    var dateTimeProviderStub = new Mock<IDateTimeProvider>();
    dateTimeProviderStub.Setup(dtp => dtp.DayOfWeek()).Returns(DayOfWeek.Tuesday);

    var actual = priceCalculator.GetDiscountedPrice(2, dateTimeProviderStub);

    Assert.Equals(1, actual);
}
```

<span data-ttu-id="80ce6-289">現在，測試套件具有 `DateTime.Now` 的完整控制權，而且可以在呼叫方法時虛設任何值。</span><span class="sxs-lookup"><span data-stu-id="80ce6-289">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
