---
title: 撰寫單元測試的最佳做法
description: 了解撰寫單元測試的最佳做法，提高 .NET Core 和 .NET Standard 專案的程式碼品質和復原功能。
author: jpreese
ms.author: wiwagn
ms.date: 07/28/2018
ms.custom: seodec18
ms.openlocfilehash: 79c8e216126353bdf5fca34baf432496aacb93ce
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151523"
---
# <a name="unit-testing-best-practices-with-net-core-and-net-standard"></a><span data-ttu-id="bd177-103">.NET Core 和 .NET Standard 的單元測試最佳做法</span><span class="sxs-lookup"><span data-stu-id="bd177-103">Unit testing best practices with .NET Core and .NET Standard</span></span>

<span data-ttu-id="bd177-104">撰寫單元測試有許多優點；運用迴歸加以協助、提供文件，並增進良好的設計。</span><span class="sxs-lookup"><span data-stu-id="bd177-104">There are numerous benefits to writing unit tests; they help with regression, provide documentation, and facilitate good design.</span></span> <span data-ttu-id="bd177-105">不過，難以閱讀且容易損毀的單元測試可能會破壞程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="bd177-105">However, hard to read and brittle unit tests can wreak havoc on your code base.</span></span> <span data-ttu-id="bd177-106">本文描述有關為 .NET Core 和 .NET Standard 專案設計單元測試的一些最佳做法。</span><span class="sxs-lookup"><span data-stu-id="bd177-106">This article describes some best practices regarding unit test design for your .NET Core and .NET Standard projects.</span></span>

<span data-ttu-id="bd177-107">本指南中，您將了解一些撰寫單元測試時的最佳做法，讓您的測試保有復原能力且易於了解。</span><span class="sxs-lookup"><span data-stu-id="bd177-107">In this guide, you'll learn some best practices when writing unit tests to keep your tests resilient and easy to understand.</span></span>

<span data-ttu-id="bd177-108">作者：[John Reese](https://reesespieces.io) (特別感謝 [Roy Osherove](http://osherove.com/))</span><span class="sxs-lookup"><span data-stu-id="bd177-108">By [John Reese](https://reesespieces.io) with special thanks to [Roy Osherove](http://osherove.com/)</span></span>

## <a name="why-unit-test"></a><span data-ttu-id="bd177-109">為何選擇單元測試？</span><span class="sxs-lookup"><span data-stu-id="bd177-109">Why unit test?</span></span>

### <a name="less-time-performing-functional-tests"></a><span data-ttu-id="bd177-110">執行功能測試的時間較少</span><span class="sxs-lookup"><span data-stu-id="bd177-110">Less time performing functional tests</span></span>
<span data-ttu-id="bd177-111">功能測試很耗費資源。</span><span class="sxs-lookup"><span data-stu-id="bd177-111">Functional tests are expensive.</span></span> <span data-ttu-id="bd177-112">功能測試通常涉及開啟應用程式，以及執行您 (或其他人) 必須遵循的一系列步驟，藉此驗證預期行為。</span><span class="sxs-lookup"><span data-stu-id="bd177-112">They typically involve opening up the application and performing a series of steps that you (or someone else), must follow in order to validate the expected behavior.</span></span> <span data-ttu-id="bd177-113">測試人員不一定會熟悉這些步驟，表示他們必須連絡該領域中更加專業的人員，才得以執行測試。</span><span class="sxs-lookup"><span data-stu-id="bd177-113">These steps may not always be known to the tester, which means they will have to reach out to someone more knowledgeable in the area in order to carry out the test.</span></span> <span data-ttu-id="bd177-114">對於較細瑣的變更，測試本身可能需要費時幾秒鐘，而對於較大的變更，可能會花上幾分鐘的時間。</span><span class="sxs-lookup"><span data-stu-id="bd177-114">Testing itself could take seconds for trivial changes, or minutes for larger changes.</span></span> <span data-ttu-id="bd177-115">最後，將必須對您在系統中所做的所有變更重複執行此程序。</span><span class="sxs-lookup"><span data-stu-id="bd177-115">Lastly, this process must be repeated for every change that you make in the system.</span></span>

<span data-ttu-id="bd177-116">另一方面，單元測試只需費時幾毫秒，按下按鈕便可執行，並不需要有整個系統的相關知識。</span><span class="sxs-lookup"><span data-stu-id="bd177-116">Unit tests, on the other hand, take milliseconds, can be run at the press of a button and do not necessarily require any knowledge of the system at large.</span></span> <span data-ttu-id="bd177-117">測試通過或失敗取決於測試執行者，而不是個人。</span><span class="sxs-lookup"><span data-stu-id="bd177-117">Whether or not the test passes or fails is up to the test runner, not the individual.</span></span>

### <a name="protection-against-regression"></a><span data-ttu-id="bd177-118">對於迴歸的保護</span><span class="sxs-lookup"><span data-stu-id="bd177-118">Protection against regression</span></span>
<span data-ttu-id="bd177-119">迴歸缺失是對應用程式進行變更時帶來的缺失。</span><span class="sxs-lookup"><span data-stu-id="bd177-119">Regression defects are defects that are introduced when a change is made to the application.</span></span> <span data-ttu-id="bd177-120">通常測試人員不僅要測試其新功能，也要測試早已存在的功能，確認先前實作的功能仍可如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="bd177-120">It is common for testers to not only test their new feature but also features that existed beforehand in order to verify that previously implemented features still function as expected.</span></span>

<span data-ttu-id="bd177-121">利用單元測試，您就可以在每次建置之後，甚至是您變更程式碼行之後，重新執行一整套測試。</span><span class="sxs-lookup"><span data-stu-id="bd177-121">With unit testing, it's possible to rerun your entire suite of tests after every build or even after you change a line of code.</span></span> <span data-ttu-id="bd177-122">讓您確信新的程式碼不會中斷現有的功能。</span><span class="sxs-lookup"><span data-stu-id="bd177-122">Giving you confidence that your new code does not break existing functionality.</span></span>

### <a name="executable-documentation"></a><span data-ttu-id="bd177-123">可執行檔文件</span><span class="sxs-lookup"><span data-stu-id="bd177-123">Executable documentation</span></span>
<span data-ttu-id="bd177-124">在提供特定輸入的情況下，特定方法的用途或其運作方式不一定很明顯。</span><span class="sxs-lookup"><span data-stu-id="bd177-124">It may not always be obvious what a particular method does or how it behaves given a certain input.</span></span> <span data-ttu-id="bd177-125">您可能會自問：如果我將空白字串傳遞給此方法，其運作方式為何？</span><span class="sxs-lookup"><span data-stu-id="bd177-125">You may ask yourself: How does this method behave if I pass it a blank string?</span></span> <span data-ttu-id="bd177-126">Null 呢？</span><span class="sxs-lookup"><span data-stu-id="bd177-126">Null?</span></span>

<span data-ttu-id="bd177-127">如果您有一套妥善命名的單元測試，每個測試都應該能清楚說明給定輸入的預期輸出。</span><span class="sxs-lookup"><span data-stu-id="bd177-127">When you have a suite of well-named unit tests, each test should be able to clearly explain the expected output for a given input.</span></span> <span data-ttu-id="bd177-128">此外，應該還能確認它實際上可正常運作。</span><span class="sxs-lookup"><span data-stu-id="bd177-128">In addition, it should be able to verify that it actually works.</span></span>

### <a name="less-coupled-code"></a><span data-ttu-id="bd177-129">結合的程式碼較少</span><span class="sxs-lookup"><span data-stu-id="bd177-129">Less coupled code</span></span>
<span data-ttu-id="bd177-130">當程式碼緊密結合時，可能難以進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="bd177-130">When code is tightly coupled, it can be difficult to unit test.</span></span> <span data-ttu-id="bd177-131">如果不針對您所撰寫的程式碼建立單元測試，結合程度就可能較不明顯。</span><span class="sxs-lookup"><span data-stu-id="bd177-131">Without creating unit tests for the code that you're writing, coupling may be less apparent.</span></span>

<span data-ttu-id="bd177-132">為您的程式碼撰寫測試時會自然分離程式碼，否則它會更難以測試。</span><span class="sxs-lookup"><span data-stu-id="bd177-132">Writing tests for your code will naturally decouple your code, because it would be more difficult to test otherwise.</span></span>

## <a name="characteristics-of-a-good-unit-test"></a><span data-ttu-id="bd177-133">良好單元測試的特性</span><span class="sxs-lookup"><span data-stu-id="bd177-133">Characteristics of a good unit test</span></span>
- <span data-ttu-id="bd177-134">**快速**。</span><span class="sxs-lookup"><span data-stu-id="bd177-134">**Fast**.</span></span> <span data-ttu-id="bd177-135">具有數千個單元測試的成熟專案並不罕見。</span><span class="sxs-lookup"><span data-stu-id="bd177-135">It is not uncommon for mature projects to have thousands of unit tests.</span></span> <span data-ttu-id="bd177-136">單元測試應只需要極少的時間執行。</span><span class="sxs-lookup"><span data-stu-id="bd177-136">Unit tests should take very little time to run.</span></span> <span data-ttu-id="bd177-137">毫秒。</span><span class="sxs-lookup"><span data-stu-id="bd177-137">Milliseconds.</span></span>
- <span data-ttu-id="bd177-138">**隔離**。</span><span class="sxs-lookup"><span data-stu-id="bd177-138">**Isolated**.</span></span> <span data-ttu-id="bd177-139">單元測試是獨立的，可以單獨執行，並且對所有外部因素 (例如檔案系統或資料庫) 沒有任何相依性。</span><span class="sxs-lookup"><span data-stu-id="bd177-139">Unit tests are standalone, can be run in isolation, and have no dependencies on any outside factors such as a file system or database.</span></span>
- <span data-ttu-id="bd177-140">**可重複**。</span><span class="sxs-lookup"><span data-stu-id="bd177-140">**Repeatable**.</span></span> <span data-ttu-id="bd177-141">執行單元測試應該與其結果一致，亦即，如果您未變更回合之間的任何項目，會一律傳回相同的結果。</span><span class="sxs-lookup"><span data-stu-id="bd177-141">Running a unit test should be consistent with its results, that is, it always returns the same result if you do not change anything in between runs.</span></span>
- <span data-ttu-id="bd177-142">**自我檢查**。</span><span class="sxs-lookup"><span data-stu-id="bd177-142">**Self-Checking**.</span></span> <span data-ttu-id="bd177-143">測試應該能夠自行偵測到通過或失敗，不需要任何人為互動。</span><span class="sxs-lookup"><span data-stu-id="bd177-143">The test should be able to automatically detect if it passed or failed without any human interaction.</span></span>
- <span data-ttu-id="bd177-144">**及時**。</span><span class="sxs-lookup"><span data-stu-id="bd177-144">**Timely**.</span></span> <span data-ttu-id="bd177-145">相較於所測試的程式碼，單元測試不應耗費不成比例的冗長時間來撰寫。</span><span class="sxs-lookup"><span data-stu-id="bd177-145">A unit test should not take a disproportionally long time to write compared to the code being tested.</span></span> <span data-ttu-id="bd177-146">相較於撰寫程式碼，如果您發現測試程式碼花費大量時間，請考慮使用更易於測試的設計。</span><span class="sxs-lookup"><span data-stu-id="bd177-146">If you find testing the code taking a large amount of time compared to writing the code, consider a design that is more testable.</span></span>

## <a name="lets-speak-the-same-language"></a><span data-ttu-id="bd177-147">讓我們使用相同的語言</span><span class="sxs-lookup"><span data-stu-id="bd177-147">Let's speak the same language</span></span>
<span data-ttu-id="bd177-148">說到測試，遺憾的是「模擬」(*mock*) 一詞遭到誤用。</span><span class="sxs-lookup"><span data-stu-id="bd177-148">The term *mock* is unfortunately very misused when talking about testing.</span></span> <span data-ttu-id="bd177-149">以下將定義撰寫單元測試時最常見的 *fakes* 類型：</span><span class="sxs-lookup"><span data-stu-id="bd177-149">The following defines the most common types of *fakes* when writing unit tests:</span></span>

<span data-ttu-id="bd177-150">假功能 (*Fake*) - 假功能是一般詞彙，用來描述虛設常式或模擬物件。</span><span class="sxs-lookup"><span data-stu-id="bd177-150">*Fake* - A fake is a generic term which can be used to describe either a stub or a mock object.</span></span> <span data-ttu-id="bd177-151">至於是虛設常式還是模擬，取決於使用的內容而定。</span><span class="sxs-lookup"><span data-stu-id="bd177-151">Whether it is a stub or a mock depends on the context in which it's used.</span></span> <span data-ttu-id="bd177-152">因此，換句話說，假功能可以是虛設常式或是模擬。</span><span class="sxs-lookup"><span data-stu-id="bd177-152">So in other words, a fake can be a stub or a mock.</span></span>

<span data-ttu-id="bd177-153">模擬 (*Mock*) - 模擬物件是系統中的假物件，可決定單元測試通過或失敗。</span><span class="sxs-lookup"><span data-stu-id="bd177-153">*Mock* - A mock object is a fake object in the system that decides whether or not a unit test has passed or failed.</span></span> <span data-ttu-id="bd177-154">模擬一開始是假功能，直到另行判定為止。</span><span class="sxs-lookup"><span data-stu-id="bd177-154">A mock starts out as a Fake until it is asserted against.</span></span>

<span data-ttu-id="bd177-155">虛設常式 (*Stub*) - 虛設常式是系統中現有相依性 (或共同作業者) 的可控制取代項目。</span><span class="sxs-lookup"><span data-stu-id="bd177-155">*Stub* - A stub is a controllable replacement for an existing dependency (or collaborator) in the system.</span></span> <span data-ttu-id="bd177-156">藉由使用虛設常式，您可以測試程式碼，而不必直接處理相依性。</span><span class="sxs-lookup"><span data-stu-id="bd177-156">By using a stub, you can test your code without dealing with the dependency directly.</span></span> <span data-ttu-id="bd177-157">根據預設，假功能一開始是虛設常式。</span><span class="sxs-lookup"><span data-stu-id="bd177-157">By default, a fake starts out as a stub.</span></span>

<span data-ttu-id="bd177-158">請考慮下列程式碼片段：</span><span class="sxs-lookup"><span data-stu-id="bd177-158">Consider the following code snippet:</span></span>

```csharp
var mockOrder = new MockOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="bd177-159">這是稱為模擬 (mock) 的虛設常式範例。</span><span class="sxs-lookup"><span data-stu-id="bd177-159">This would be an example of stub being referred to as a mock.</span></span> <span data-ttu-id="bd177-160">在此情況下為虛設常式。</span><span class="sxs-lookup"><span data-stu-id="bd177-160">In this case, it is a stub.</span></span> <span data-ttu-id="bd177-161">您只是傳入訂單，作為能夠具現化 `Purchase` (待測系統) 的方法。</span><span class="sxs-lookup"><span data-stu-id="bd177-161">You're just passing in the Order as a means to be able to instantiate `Purchase` (the system under test).</span></span> <span data-ttu-id="bd177-162">名稱 `MockOrder` 也很容易產生誤導，因為訂單並不是模擬。</span><span class="sxs-lookup"><span data-stu-id="bd177-162">The name `MockOrder` is also very misleading because again, the order is not a mock.</span></span>

<span data-ttu-id="bd177-163">更好的方式會是</span><span class="sxs-lookup"><span data-stu-id="bd177-163">A better approach would be</span></span>

```csharp
var stubOrder = new FakeOrder();
var purchase = new Purchase(stubOrder);

purchase.ValidateOrders();

Assert.True(purchase.CanBeShipped);
```

<span data-ttu-id="bd177-164">透過將類別重新命名為 `FakeOrder`，您已使該類別更加通用，因此可將該類別作為模擬或虛設常式使用。</span><span class="sxs-lookup"><span data-stu-id="bd177-164">By renaming the class to `FakeOrder`, you've made the class a lot more generic, the class can be used as a mock or a stub.</span></span> <span data-ttu-id="bd177-165">請取其更適合測試案例者。</span><span class="sxs-lookup"><span data-stu-id="bd177-165">Whichever is better for the test case.</span></span> <span data-ttu-id="bd177-166">在上述範例中，`FakeOrder` 作為虛設常式使用。</span><span class="sxs-lookup"><span data-stu-id="bd177-166">In the above example, `FakeOrder` is used as a stub.</span></span> <span data-ttu-id="bd177-167">在判定期間，您沒有以任何形式使用 `FakeOrder`。</span><span class="sxs-lookup"><span data-stu-id="bd177-167">You're not using the `FakeOrder` in any shape or form during the assert.</span></span> <span data-ttu-id="bd177-168">`FakeOrder` 只是傳入 `Purchase` 類別以滿足建構函式的需求。</span><span class="sxs-lookup"><span data-stu-id="bd177-168">`FakeOrder` was just passed into the `Purchase` class to satisfy the requirements of the constructor.</span></span>

<span data-ttu-id="bd177-169">若要用作模擬，您可以執行類似下述內容</span><span class="sxs-lookup"><span data-stu-id="bd177-169">To use it as a Mock, you could do something like this</span></span>

```csharp
var mockOrder = new FakeOrder();
var purchase = new Purchase(mockOrder);

purchase.ValidateOrders();

Assert.True(mockOrder.Validated);
```

<span data-ttu-id="bd177-170">在此情況下，您正在檢查假功能上的屬性 (另行判定)，因此在上述程式碼片段中，屬性 `mockOrder` 是模擬。</span><span class="sxs-lookup"><span data-stu-id="bd177-170">In this case, you are checking a property on the Fake (asserting against it), so in the above code snippet, the `mockOrder` is a Mock.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd177-171">請務必正確使用這個術語。</span><span class="sxs-lookup"><span data-stu-id="bd177-171">It's important to get this terminology correct.</span></span> <span data-ttu-id="bd177-172">如果您將虛設常式稱為「模擬」，其他開發人員會對您的意圖帶有錯誤的假設。</span><span class="sxs-lookup"><span data-stu-id="bd177-172">If you call your stubs "mocks", other developers are going to make false assumptions about your intent.</span></span>

<span data-ttu-id="bd177-173">關於模擬與虛設常式要記住的重點在於，模擬就像虛設常式一樣，只是您會對模擬物件另行判定，而不會對虛設常式另行判定。</span><span class="sxs-lookup"><span data-stu-id="bd177-173">The main thing to remember about mocks versus stubs is that mocks are just like stubs, but you assert against the mock object, whereas you do not assert against a stub.</span></span>

## <a name="best-practices"></a><span data-ttu-id="bd177-174">最佳作法</span><span class="sxs-lookup"><span data-stu-id="bd177-174">Best practices</span></span>

### <a name="naming-your-tests"></a><span data-ttu-id="bd177-175">為測試命名</span><span class="sxs-lookup"><span data-stu-id="bd177-175">Naming your tests</span></span>
<span data-ttu-id="bd177-176">測試的名稱應該包含三個部分：</span><span class="sxs-lookup"><span data-stu-id="bd177-176">The name of your test should consist of three parts:</span></span>
- <span data-ttu-id="bd177-177">所測試的方法名稱。</span><span class="sxs-lookup"><span data-stu-id="bd177-177">The name of the method being tested.</span></span>
- <span data-ttu-id="bd177-178">用以測試的案例。</span><span class="sxs-lookup"><span data-stu-id="bd177-178">The scenario under which it's being tested.</span></span>
- <span data-ttu-id="bd177-179">叫用案例時的預期行為。</span><span class="sxs-lookup"><span data-stu-id="bd177-179">The expected behavior when the scenario is invoked.</span></span>

#### <a name="why"></a><span data-ttu-id="bd177-180">為什麼？</span><span class="sxs-lookup"><span data-stu-id="bd177-180">Why?</span></span>
- <span data-ttu-id="bd177-181">命名標準很重要，因為名稱會明確表示測試目的。</span><span class="sxs-lookup"><span data-stu-id="bd177-181">Naming standards are important because they explicitly express the intent of the test.</span></span>

<span data-ttu-id="bd177-182">測試不只要確定您的程式碼能夠運作，還會提供文件。</span><span class="sxs-lookup"><span data-stu-id="bd177-182">Tests are more than just making sure your code works, they also provide documentation.</span></span> <span data-ttu-id="bd177-183">只要查看這套單元測試，您應能推斷程式碼的行為，甚至無需查看程式碼本身。</span><span class="sxs-lookup"><span data-stu-id="bd177-183">Just by looking at the suite of unit tests, you should be able to infer the behavior of your code without even looking at the code itself.</span></span> <span data-ttu-id="bd177-184">此外，當測試失敗時，您可以確切看到哪些案例不符合預期。</span><span class="sxs-lookup"><span data-stu-id="bd177-184">Additionally, when tests fail, you can see exactly which scenarios do not meet your expectations.</span></span>

#### <a name="bad"></a><span data-ttu-id="bd177-185">不良：</span><span class="sxs-lookup"><span data-stu-id="bd177-185">Bad:</span></span>
[!code-csharp[BeforeNaming](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeNaming)]

#### <a name="better"></a><span data-ttu-id="bd177-186">較佳：</span><span class="sxs-lookup"><span data-stu-id="bd177-186">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="arranging-your-tests"></a><span data-ttu-id="bd177-187">排列測試</span><span class="sxs-lookup"><span data-stu-id="bd177-187">Arranging your tests</span></span>
<span data-ttu-id="bd177-188">**排列、採取動作、判定**是進行單元測試時的常見模式。</span><span class="sxs-lookup"><span data-stu-id="bd177-188">**Arrange, Act, Assert** is a common pattern when unit testing.</span></span> <span data-ttu-id="bd177-189">顧名思義，其中包含三個主要動作：</span><span class="sxs-lookup"><span data-stu-id="bd177-189">As the name implies, it consists of three main actions:</span></span>
- <span data-ttu-id="bd177-190">「排列」物件，並視需要建立和設定這些物件。</span><span class="sxs-lookup"><span data-stu-id="bd177-190">*Arrange* your objects, creating and setting them up as necessary.</span></span>
- <span data-ttu-id="bd177-191">對物件「採取動作」。</span><span class="sxs-lookup"><span data-stu-id="bd177-191">*Act* on an object.</span></span>
- <span data-ttu-id="bd177-192">「判定」某個項目如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="bd177-192">*Assert* that something is as expected.</span></span>

#### <a name="why"></a><span data-ttu-id="bd177-193">為什麼？</span><span class="sxs-lookup"><span data-stu-id="bd177-193">Why?</span></span>
- <span data-ttu-id="bd177-194">清楚分隔正在測試的項目與「排列」和「判定」步驟。</span><span class="sxs-lookup"><span data-stu-id="bd177-194">Clearly separates what is being tested from the *arrange* and *assert* steps.</span></span>
- <span data-ttu-id="bd177-195">這麼做可使判定與「採取動作」程式碼相互摻雜的機率更低。</span><span class="sxs-lookup"><span data-stu-id="bd177-195">Less chance to intermix assertions with "Act" code.</span></span>

<span data-ttu-id="bd177-196">可讀性是撰寫測試時最重要的層面之一。</span><span class="sxs-lookup"><span data-stu-id="bd177-196">Readability is one of the most important aspects when writing a test.</span></span> <span data-ttu-id="bd177-197">分隔測試內的每個動作可清楚突顯呼叫程式碼、如何呼叫程式碼，以及您嘗試進行判定所需的相依性。</span><span class="sxs-lookup"><span data-stu-id="bd177-197">Separating each of these actions within the test clearly highlight the dependencies required to call your code, how your code is being called, and what you are trying to assert.</span></span> <span data-ttu-id="bd177-198">雖然可以合併某些步驟並減少測試的大小，但主要目標是盡可能讓測試可讀。</span><span class="sxs-lookup"><span data-stu-id="bd177-198">While it may be possible to combine some steps and reduce the size of your test, the primary goal is to make the test as readable as possible.</span></span>

#### <a name="bad"></a><span data-ttu-id="bd177-199">不良：</span><span class="sxs-lookup"><span data-stu-id="bd177-199">Bad:</span></span>
[!code-csharp[BeforeArranging](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeArranging)]

#### <a name="better"></a><span data-ttu-id="bd177-200">較佳：</span><span class="sxs-lookup"><span data-stu-id="bd177-200">Better:</span></span>
[!code-csharp[AfterArranging](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterArranging)]

### <a name="write-minimally-passing-tests"></a><span data-ttu-id="bd177-201">撰寫最低限度通過測試</span><span class="sxs-lookup"><span data-stu-id="bd177-201">Write minimally passing tests</span></span>
<span data-ttu-id="bd177-202">要在單元測試中使用的輸入應該是最簡單的，才能驗證您目前正在測試的行為。</span><span class="sxs-lookup"><span data-stu-id="bd177-202">The input to be used in a unit test should be the simplest possible in order to verify the behavior that you are currently testing.</span></span>

#### <a name="why"></a><span data-ttu-id="bd177-203">為什麼？</span><span class="sxs-lookup"><span data-stu-id="bd177-203">Why?</span></span>
- <span data-ttu-id="bd177-204">測試對程式碼基底的未來變更變得更具復原性。</span><span class="sxs-lookup"><span data-stu-id="bd177-204">Tests become more resilient to future changes in the codebase.</span></span>
- <span data-ttu-id="bd177-205">更接近測試行為而不是實作。</span><span class="sxs-lookup"><span data-stu-id="bd177-205">Closer to testing behavior over implementation.</span></span>

<span data-ttu-id="bd177-206">如果測試包含的資訊比通過測試所需還要多，更有可能會將錯誤帶進測試中，且會讓測試的意圖較不清楚。</span><span class="sxs-lookup"><span data-stu-id="bd177-206">Tests that include more information than required to pass the test have a higher chance of introducing errors into the test and can make the intent of the test less clear.</span></span> <span data-ttu-id="bd177-207">撰寫測試時，您想要著重於行為。</span><span class="sxs-lookup"><span data-stu-id="bd177-207">When writing tests you want to focus on the behavior.</span></span> <span data-ttu-id="bd177-208">在模型上設定額外的屬性，或在不需要時使用非零值，只會減損您嘗試證明的項目。</span><span class="sxs-lookup"><span data-stu-id="bd177-208">Setting extra properties on models or using non-zero values when not required, only detracts from what you are trying to prove.</span></span>

#### <a name="bad"></a><span data-ttu-id="bd177-209">不良：</span><span class="sxs-lookup"><span data-stu-id="bd177-209">Bad:</span></span>
[!code-csharp[BeforeMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMinimallyPassing)]

#### <a name="better"></a><span data-ttu-id="bd177-210">較佳：</span><span class="sxs-lookup"><span data-stu-id="bd177-210">Better:</span></span>
[!code-csharp[AfterNamingAndMinimallyPassing](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterNamingAndMinimallyPassing)]

### <a name="avoid-magic-strings"></a><span data-ttu-id="bd177-211">避免魔術字串</span><span class="sxs-lookup"><span data-stu-id="bd177-211">Avoid magic strings</span></span>
<span data-ttu-id="bd177-212">相較於在生產環境程式碼中為變數命名，在單元測試中為變數命名的重要性有過之而無不及。</span><span class="sxs-lookup"><span data-stu-id="bd177-212">Naming variables in unit tests is as important, if not more important, than naming variables in production code.</span></span> <span data-ttu-id="bd177-213">單元測試不應該包含魔術字串。</span><span class="sxs-lookup"><span data-stu-id="bd177-213">Unit tests should not contain magic strings.</span></span>

#### <a name="why"></a><span data-ttu-id="bd177-214">為什麼？</span><span class="sxs-lookup"><span data-stu-id="bd177-214">Why?</span></span>
- <span data-ttu-id="bd177-215">避免測試的讀者為了找出使該值變得特殊的原因而需要檢查生產環境程式碼。</span><span class="sxs-lookup"><span data-stu-id="bd177-215">Prevents the need for the reader of the test to inspect the production code in order to figure out what makes the value special.</span></span>
- <span data-ttu-id="bd177-216">明確地顯示您想要「證明」的項目，而不是嘗試「完成」的項目。</span><span class="sxs-lookup"><span data-stu-id="bd177-216">Explicitly shows what you're trying to *prove* rather than trying to *accomplish*.</span></span>

<span data-ttu-id="bd177-217">魔術字串可能會對測試的讀者造成混淆。</span><span class="sxs-lookup"><span data-stu-id="bd177-217">Magic strings can cause confusion to the reader of your tests.</span></span> <span data-ttu-id="bd177-218">如果字串看起來不正常，讀者可能會納悶為什麼針對參數或傳回值選擇特定值。</span><span class="sxs-lookup"><span data-stu-id="bd177-218">If a string looks out of the ordinary, they may wonder why a certain value was chosen for a parameter or return value.</span></span> <span data-ttu-id="bd177-219">這可能會導致他們過於仔細查看實作詳細資料，而不是專注於測試。</span><span class="sxs-lookup"><span data-stu-id="bd177-219">This may lead them to take a closer look at the implementation details, rather than focus on the test.</span></span>

> [!TIP] 
> <span data-ttu-id="bd177-220">在撰寫測試時，您的目標應該是盡可能表達意圖。</span><span class="sxs-lookup"><span data-stu-id="bd177-220">When writing tests, you should aim to express as much intent as possible.</span></span> <span data-ttu-id="bd177-221">如果是魔術字串，將這些值指派給常數會是不錯的方法。</span><span class="sxs-lookup"><span data-stu-id="bd177-221">In the case of magic strings, a good approach is to assign these values to constants.</span></span>

#### <a name="bad"></a><span data-ttu-id="bd177-222">不良：</span><span class="sxs-lookup"><span data-stu-id="bd177-222">Bad:</span></span>
[!code-csharp[BeforeMagicString](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMagicString)]

#### <a name="better"></a><span data-ttu-id="bd177-223">較佳：</span><span class="sxs-lookup"><span data-stu-id="bd177-223">Better:</span></span>
[!code-csharp[AfterMagicString](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMagicString)]

### <a name="avoid-logic-in-tests"></a><span data-ttu-id="bd177-224">避免在測試中使用邏輯</span><span class="sxs-lookup"><span data-stu-id="bd177-224">Avoid logic in tests</span></span>
<span data-ttu-id="bd177-225">撰寫您的單元測試時，請避免使用手動字串串連和邏輯條件，例如 `if`、`while`、`for`、`switch` 等等。</span><span class="sxs-lookup"><span data-stu-id="bd177-225">When writing your unit tests avoid manual string concatenation and logical conditions such as `if`, `while`, `for`, `switch`, etc.</span></span>

#### <a name="why"></a><span data-ttu-id="bd177-226">為什麼？</span><span class="sxs-lookup"><span data-stu-id="bd177-226">Why?</span></span>
- <span data-ttu-id="bd177-227">在測試內帶進 Bug 的機率更低。</span><span class="sxs-lookup"><span data-stu-id="bd177-227">Less chance to introduce a bug inside of your tests.</span></span>
- <span data-ttu-id="bd177-228">著重最終結果，而不是實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="bd177-228">Focus on the end result, rather than implementation details.</span></span>

<span data-ttu-id="bd177-229">將邏輯引入您的測試套件時，在其中帶進 Bug 的機率會大幅增加。</span><span class="sxs-lookup"><span data-stu-id="bd177-229">When you introduce logic into your test suite, the chance of introducing a bug into it increases dramatically.</span></span> <span data-ttu-id="bd177-230">您不會想要在您的測試套件尋找 Bug。</span><span class="sxs-lookup"><span data-stu-id="bd177-230">The last place that you want to find a bug is within your test suite.</span></span> <span data-ttu-id="bd177-231">您應該對測試正確運作的結果具有高度信心，否則您不會信任測試。</span><span class="sxs-lookup"><span data-stu-id="bd177-231">You should have a high level of confidence that your tests work, otherwise, you will not trust them.</span></span> <span data-ttu-id="bd177-232">您不信任的測試將無法提供任何價值。</span><span class="sxs-lookup"><span data-stu-id="bd177-232">Tests that you do not trust, do not provide any value.</span></span> <span data-ttu-id="bd177-233">當測試失敗時，您要意識到確實是程式碼發生問題，且無法予以忽略。</span><span class="sxs-lookup"><span data-stu-id="bd177-233">When a test fails, you want to have a sense that something is actually wrong with your code and that it cannot be ignored.</span></span>

> [!TIP]
> <span data-ttu-id="bd177-234">如果測試中的邏輯看似無法避免，請考慮將測試分割成兩個或多個不同的測試。</span><span class="sxs-lookup"><span data-stu-id="bd177-234">If logic in your test seems unavoidable, consider splitting the test up into two or more different tests.</span></span>

#### <a name="bad"></a><span data-ttu-id="bd177-235">不良：</span><span class="sxs-lookup"><span data-stu-id="bd177-235">Bad:</span></span>
[!code-csharp[LogicInTests](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#LogicInTests)]

#### <a name="better"></a><span data-ttu-id="bd177-236">較佳：</span><span class="sxs-lookup"><span data-stu-id="bd177-236">Better:</span></span>
[!code-csharp[AfterTestLogic](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterTestLogic)]

### <a name="prefer-helper-methods-to-setup-and-teardown"></a><span data-ttu-id="bd177-237">慣用 Helper 方法來設定及終止</span><span class="sxs-lookup"><span data-stu-id="bd177-237">Prefer helper methods to setup and teardown</span></span>
<span data-ttu-id="bd177-238">如果您的測試需要類似的物件或狀態，比起利用 Setup 和 Teardown 屬性 (若有)，更慣用 Helper 方法。</span><span class="sxs-lookup"><span data-stu-id="bd177-238">If you require a similar object or state for your tests, prefer a helper method than leveraging Setup and Teardown attributes if they exist.</span></span>

#### <a name="why"></a><span data-ttu-id="bd177-239">為什麼？</span><span class="sxs-lookup"><span data-stu-id="bd177-239">Why?</span></span>
- <span data-ttu-id="bd177-240">讀取測試時混淆較少，因為在每個測試內都可以看見所有的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bd177-240">Less confusion when reading the tests since all of the code is visible from within each test.</span></span>
- <span data-ttu-id="bd177-241">對於給定的測試，設定太多或太少的機率更低。</span><span class="sxs-lookup"><span data-stu-id="bd177-241">Less chance of setting up too much or too little for the given test.</span></span>
- <span data-ttu-id="bd177-242">在測試之間共用狀態，進而在測試之間建立非必要相依性的機率更低。</span><span class="sxs-lookup"><span data-stu-id="bd177-242">Less chance of sharing state between tests which creates unwanted dependencies between them.</span></span>

<span data-ttu-id="bd177-243">在單元測試架構中，會在測試套件內的每個單元測試之前或其中呼叫 `Setup`。</span><span class="sxs-lookup"><span data-stu-id="bd177-243">In unit testing frameworks, `Setup` is called before each and every unit test within your test suite.</span></span> <span data-ttu-id="bd177-244">雖然有人可能會認為這是很有用的工具，但它最後通常會導致測試過大且難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="bd177-244">While some may see this as a useful tool, it generally ends up leading to bloated and hard to read tests.</span></span> <span data-ttu-id="bd177-245">每個測試通常會有不同的需求，以便啟動及執測試。</span><span class="sxs-lookup"><span data-stu-id="bd177-245">Each test will generally have different requirements in order to get the test up and running.</span></span> <span data-ttu-id="bd177-246">不幸的是，`Setup` 會強迫您針對每個測試使用完全相同的需求。</span><span class="sxs-lookup"><span data-stu-id="bd177-246">Unfortunately, `Setup` forces you to use the exact same requirements for each test.</span></span>

> [!NOTE] 
> <span data-ttu-id="bd177-247">自 2.x 版開始，xUnit 已移除 Setup 及 TearDown 這兩者</span><span class="sxs-lookup"><span data-stu-id="bd177-247">xUnit has removed both SetUp and TearDown as of version 2.x</span></span>

#### <a name="bad"></a><span data-ttu-id="bd177-248">不良：</span><span class="sxs-lookup"><span data-stu-id="bd177-248">Bad:</span></span>
[!code-csharp[BeforeSetup](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeSetup)]

```csharp
// more tests...
```

[!code-csharp[BeforeHelperMethod](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeHelperMethod)]

#### <a name="better"></a><span data-ttu-id="bd177-249">較佳：</span><span class="sxs-lookup"><span data-stu-id="bd177-249">Better:</span></span>
[!code-csharp[AfterHelperMethod](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterHelperMethod)]

```csharp
// more tests...
```

[!code-csharp[AfterSetup](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterSetup)]

### <a name="avoid-multiple-asserts"></a><span data-ttu-id="bd177-250">避免多個判定</span><span class="sxs-lookup"><span data-stu-id="bd177-250">Avoid multiple asserts</span></span>
<span data-ttu-id="bd177-251">在撰寫測試時，請嘗試於每個測試只包含一個判定。</span><span class="sxs-lookup"><span data-stu-id="bd177-251">When writing your tests, try to only include one Assert per test.</span></span> <span data-ttu-id="bd177-252">只使用一個判定的常見方法包括：</span><span class="sxs-lookup"><span data-stu-id="bd177-252">Common approaches to using only one assert include:</span></span>
- <span data-ttu-id="bd177-253">為每個判定建立個別測試。</span><span class="sxs-lookup"><span data-stu-id="bd177-253">Create a separate test for each assert.</span></span>
- <span data-ttu-id="bd177-254">使用參數化測試。</span><span class="sxs-lookup"><span data-stu-id="bd177-254">Use parameterized tests.</span></span>

#### <a name="why"></a><span data-ttu-id="bd177-255">為什麼？</span><span class="sxs-lookup"><span data-stu-id="bd177-255">Why?</span></span>
- <span data-ttu-id="bd177-256">如果某個判定失敗，將不會評估後續的判定。</span><span class="sxs-lookup"><span data-stu-id="bd177-256">If one Assert fails, the subsequent Asserts will not be evaluated.</span></span>
- <span data-ttu-id="bd177-257">確保您不會在測試中判定多個案例。</span><span class="sxs-lookup"><span data-stu-id="bd177-257">Ensures you are not asserting multiple cases in your tests.</span></span>
- <span data-ttu-id="bd177-258">為您提供測試失敗原因的全貌。</span><span class="sxs-lookup"><span data-stu-id="bd177-258">Gives you the entire picture as to why your tests are failing.</span></span> 

<span data-ttu-id="bd177-259">將多個判定帶進測試案例時，並不保證所有的判定皆會執行。</span><span class="sxs-lookup"><span data-stu-id="bd177-259">When introducing multiple asserts into a test case, it is not guaranteed that all of the asserts will be executed.</span></span> <span data-ttu-id="bd177-260">在大部分的單元測試架構中，一旦判定在單元測試中失敗，進行中的測試將自動視為失敗。</span><span class="sxs-lookup"><span data-stu-id="bd177-260">In most unit testing frameworks, once an assertion fails in a unit test, the proceeding tests are automatically considered to be failing.</span></span> <span data-ttu-id="bd177-261">這可能會令人困惑，因為實際運作的功能會顯示為失敗。</span><span class="sxs-lookup"><span data-stu-id="bd177-261">This can be confusing as functionality that is actually working, will be shown as failing.</span></span>

> [!NOTE]
> <span data-ttu-id="bd177-262">這項規則的常見例外狀況是針對物件進行判定時。</span><span class="sxs-lookup"><span data-stu-id="bd177-262">A common exception to this rule is when asserting against an object.</span></span> <span data-ttu-id="bd177-263">在此情況下，通常可以接受對每個屬性擁有多個判定，確保物件處於您預期的狀態。</span><span class="sxs-lookup"><span data-stu-id="bd177-263">In this case, it is generally acceptable to have multiple asserts against each property to ensure the object is in the state that you expect it to be in.</span></span>

#### <a name="bad"></a><span data-ttu-id="bd177-264">不良：</span><span class="sxs-lookup"><span data-stu-id="bd177-264">Bad:</span></span>
[!code-csharp[BeforeMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/before/StringCalculatorTests.cs#BeforeMultipleAsserts)]

#### <a name="better"></a><span data-ttu-id="bd177-265">較佳：</span><span class="sxs-lookup"><span data-stu-id="bd177-265">Better:</span></span>
[!code-csharp[AfterMultipleAsserts](../../../samples/csharp/unit-testing-best-practices/after/StringCalculatorTests.cs#AfterMultipleAsserts)]

### <a name="validate-private-methods-by-unit-testing-public-methods"></a><span data-ttu-id="bd177-266">透過單元測試的公用方法驗證私用方法</span><span class="sxs-lookup"><span data-stu-id="bd177-266">Validate private methods by unit testing public methods</span></span>
<span data-ttu-id="bd177-267">在大部分情況下，應該不需要測試私用方法。</span><span class="sxs-lookup"><span data-stu-id="bd177-267">In most cases, there should not be a need to test a private method.</span></span> <span data-ttu-id="bd177-268">私用方法是實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="bd177-268">Private methods are an implementation detail.</span></span> <span data-ttu-id="bd177-269">您可以這樣來看：私用方法永遠不會單獨存在。</span><span class="sxs-lookup"><span data-stu-id="bd177-269">You can think of it this way: private methods never exist in isolation.</span></span> <span data-ttu-id="bd177-270">在某個時間點，將有一個公眾對應方法呼叫私用方法作為其實作的一部分。</span><span class="sxs-lookup"><span data-stu-id="bd177-270">At some point, there is going to be a public facing method that calls the private method as part of its implementation.</span></span> <span data-ttu-id="bd177-271">您應該關注的是呼叫私用方法的公用方法最終結果。</span><span class="sxs-lookup"><span data-stu-id="bd177-271">What you should care about is the end result of the public method that calls into the private one.</span></span> 

<span data-ttu-id="bd177-272">請考慮下列情況</span><span class="sxs-lookup"><span data-stu-id="bd177-272">Consider the following case</span></span>

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

<span data-ttu-id="bd177-273">您的第一個反應可能是開始撰寫 `trimInput` 的測試，因為您想要確定該方法是否如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="bd177-273">Your first reaction may be to start writing a test for `trimInput` because you want to make sure that the method is working as expected.</span></span> <span data-ttu-id="bd177-274">不過，`ParseLogLine` 很有可能會以非預期的方式操作 `sanitizedInput`，使得對 `trimInput` 的測試變得毫無用處。</span><span class="sxs-lookup"><span data-stu-id="bd177-274">However, it is entirely possible that `ParseLogLine` manipulates `sanitizedInput` in such a way that you do not expect, rendering a test against `trimInput` useless.</span></span> 

<span data-ttu-id="bd177-275">實際的測試應該針對公眾對應方法 `ParseLogLine` 執行，因為這才是您最應關注的項目。</span><span class="sxs-lookup"><span data-stu-id="bd177-275">The real test should be done against the public facing method `ParseLogLine` because that is what you should ultimately care about.</span></span> 

```csharp
public void ParseLogLine_ByDefault_ReturnsTrimmedResult()
{
    var parser = new Parser();

    var result = parser.ParseLogLine(" a ");

    Assert.Equals("a", result);
}
```

<span data-ttu-id="bd177-276">從這個觀點來看，如果您看到私用方法，請找出公開方法，並針對該方法撰寫您的測試。</span><span class="sxs-lookup"><span data-stu-id="bd177-276">With this viewpoint, if you see a private method, find the public method and write your tests against that method.</span></span> <span data-ttu-id="bd177-277">私用方法傳回預期結果，並不表示最終呼叫私用方法的系統會正確地使用結果。</span><span class="sxs-lookup"><span data-stu-id="bd177-277">Just because a private method returns the expected result, does not mean the system that eventually calls the private method uses the result correctly.</span></span>

### <a name="stub-static-references"></a><span data-ttu-id="bd177-278">虛設 (Stub) 靜態參考</span><span class="sxs-lookup"><span data-stu-id="bd177-278">Stub static references</span></span>
<span data-ttu-id="bd177-279">單元測試的其中一個準則是，其必須具有待測系統的完整控制權。</span><span class="sxs-lookup"><span data-stu-id="bd177-279">One of the principles of a unit test is that it must have full control of the system under test.</span></span> <span data-ttu-id="bd177-280">這可能會在生產環境程式碼包含靜態參考呼叫時 (例如 `DateTime.Now`) 造成問題。</span><span class="sxs-lookup"><span data-stu-id="bd177-280">This can be problematic when production code includes calls to static references (e.g. `DateTime.Now`).</span></span> <span data-ttu-id="bd177-281">請考慮下列程式碼</span><span class="sxs-lookup"><span data-stu-id="bd177-281">Consider the following code</span></span>

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

<span data-ttu-id="bd177-282">如何對此程式碼進行單元測試？</span><span class="sxs-lookup"><span data-stu-id="bd177-282">How can this code possibly be unit tested?</span></span> <span data-ttu-id="bd177-283">您可以嘗試一種方法，例如</span><span class="sxs-lookup"><span data-stu-id="bd177-283">You may try an approach such as</span></span>

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

<span data-ttu-id="bd177-284">不幸的是，您很快就會發現測試有幾個問題。</span><span class="sxs-lookup"><span data-stu-id="bd177-284">Unfortunately, you will quickly realize that there are a couple problems with your tests.</span></span> 

- <span data-ttu-id="bd177-285">如果測試套件是在星期二執行，第二項測試會通過，但第一項測試會失敗。</span><span class="sxs-lookup"><span data-stu-id="bd177-285">If the test suite is run on a Tuesday, the second test will pass, but the first test will fail.</span></span>
- <span data-ttu-id="bd177-286">如果測試套件是在其他天執行，第一項測試會通過，但第二項測試會失敗。</span><span class="sxs-lookup"><span data-stu-id="bd177-286">If the test suite is run on any other day, the first test will pass, but the second test will fail.</span></span>

<span data-ttu-id="bd177-287">若要解決這些問題，您需要將「接合線」帶進生產環境程式碼。</span><span class="sxs-lookup"><span data-stu-id="bd177-287">To solve these problems, you'll need to introduce a *seam* into your production code.</span></span> <span data-ttu-id="bd177-288">其中一個方法是在介面中包裝您需要控制的程式碼，並使生產環境程式碼相依於該介面。</span><span class="sxs-lookup"><span data-stu-id="bd177-288">One approach is to wrap the code that you need to control in an interface and have the production code depend on that interface.</span></span>

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

<span data-ttu-id="bd177-289">您的測試套件現在已變成</span><span class="sxs-lookup"><span data-stu-id="bd177-289">Your test suite now becomes</span></span>

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

<span data-ttu-id="bd177-290">現在，測試套件具有 `DateTime.Now` 的完整控制權，而且可以在呼叫方法時虛設任何值。</span><span class="sxs-lookup"><span data-stu-id="bd177-290">Now the test suite has full control over `DateTime.Now` and can stub any value when calling into the method.</span></span>
