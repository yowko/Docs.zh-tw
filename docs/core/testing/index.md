---
title: ".NET Core 的單元測試"
description: "單元測試從未如此輕鬆。 了解如何在 .NET Core 專案中使用單元測試。"
keywords: .NET, .NET Core
author: ardalis
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 815ac74c-4bd9-4a94-a87c-78288b27c0e2
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 22647a9ad7723bbfcf0d54530b3c0538198e7c35
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="unit-testing-in-net-core"></a><span data-ttu-id="6327b-105">.NET Core 的單元測試</span><span class="sxs-lookup"><span data-stu-id="6327b-105">Unit Testing in .NET Core</span></span>

<span data-ttu-id="6327b-106">.NET Core 在設計時就已將可測試性納入考量，因此您可以更輕鬆地針對應用程式建立單元測試。</span><span class="sxs-lookup"><span data-stu-id="6327b-106">.NET Core has been designed with testability in mind, so that creating unit tests for your applications is easier than ever before.</span></span> <span data-ttu-id="6327b-107">這篇文章簡短介紹單元測試，以及它們和其他種類測試之間的差異。</span><span class="sxs-lookup"><span data-stu-id="6327b-107">This article briefly introduces unit tests (and how they differ from other kinds of tests).</span></span> <span data-ttu-id="6327b-108">連結的資源會示範如何將測試專案新增至您的解決方案，然後使用命令列或 Visual Studio 來執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="6327b-108">Linked resources demonstrates how to add a test project to your solution and then run unit tests using either the command line or Visual Studio.</span></span>

## <a name="getting-started-with-testing"></a><span data-ttu-id="6327b-109">開始測試</span><span class="sxs-lookup"><span data-stu-id="6327b-109">Getting Started with Testing</span></span>
 
<span data-ttu-id="6327b-110">最理想的方法是使用自動化的測試套件，以確保軟體應用程式按照作者想要的結果執行。</span><span class="sxs-lookup"><span data-stu-id="6327b-110">Having a suite of automated tests is one of the best ways to ensure a software application does what its authors intended it to do.</span></span> <span data-ttu-id="6327b-111">軟體應用程式測試的種類繁多，包括整合測試、Web 測試、負載測試等等。</span><span class="sxs-lookup"><span data-stu-id="6327b-111">There are many different kinds of tests for software applications, including integration tests, web tests, load tests, and many others.</span></span> <span data-ttu-id="6327b-112">單元測試是其中最基層的測試，可用來測試個別的軟體元件或方法。</span><span class="sxs-lookup"><span data-stu-id="6327b-112">At the lowest level are unit tests, which test individual software components or methods.</span></span> <span data-ttu-id="6327b-113">單元測試應該只測試開發人員控制項內的程式碼，而不應針對基礎結構考量進行測試，例如資料庫、檔案系統或網路資源。</span><span class="sxs-lookup"><span data-stu-id="6327b-113">Unit tests should only test code within the developer’s control, and should not test infrastructure concerns, like databases, file systems, or network resources.</span></span> <span data-ttu-id="6327b-114">單元測試可能會使用[測試導向開發 (TDD)](http://deviq.com/test-driven-development/) 來進行寫入，或新增到現有的程式碼，以確認其正確性。</span><span class="sxs-lookup"><span data-stu-id="6327b-114">Unit tests may be written using [Test Driven Development (TDD)](http://deviq.com/test-driven-development/), or they can be added to existing code to confirm its correctness.</span></span> <span data-ttu-id="6327b-115">不論何種情況，單元測試應該是小型、妥善具名且可快速完成，因為在將變更推送到專案的共用程式碼存放庫之前，您可能需要先執行數百次的單元測試。</span><span class="sxs-lookup"><span data-stu-id="6327b-115">In either case, they should be small, well-named, and fast, since ideally you will want to be able to run hundreds of them before pushing your changes into the project’s shared code repository.</span></span>

> [!NOTE]
> <span data-ttu-id="6327b-116">開發人員經常必須絞盡腦汁才能想出適合其測試類別和方法的名稱。</span><span class="sxs-lookup"><span data-stu-id="6327b-116">Developers often struggle with coming up with good names for their test classes and methods.</span></span> <span data-ttu-id="6327b-117">因此，ASP.NET 產品團隊會遵循[這些慣例](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests)以做為起點。</span><span class="sxs-lookup"><span data-stu-id="6327b-117">As a starting point, the ASP.NET product team follows [these conventions](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests).</span></span>

<span data-ttu-id="6327b-118">在撰寫單元測試時，務必小心不要在基礎結構中導入相依性。</span><span class="sxs-lookup"><span data-stu-id="6327b-118">When writing unit tests, be careful you don’t accidentally introduce dependencies on infrastructure.</span></span> <span data-ttu-id="6327b-119">這些相依性通常會讓測試速度更慢，而且更不可靠，因此應該將其保留到整合測試時進行。</span><span class="sxs-lookup"><span data-stu-id="6327b-119">These tend to make tests slower and more brittle, and thus should be reserved for integration tests.</span></span> <span data-ttu-id="6327b-120">您可以遵循 [Explicit Dependencies Principle](http://deviq.com/explicit-dependencies-principle/) (明確相依性準則) 的內容，在應用程式程式碼中避免這些隱藏的相依性，並使用 [Dependency Injection](/aspnet/core/fundamentals/dependency-injection) (相依性注入) 來要求架構的相依性。</span><span class="sxs-lookup"><span data-stu-id="6327b-120">You can avoid these hidden dependencies in your application code by following the [Explicit Dependencies Principle](http://deviq.com/explicit-dependencies-principle/) and using [Dependency Injection](/aspnet/core/fundamentals/dependency-injection) to request your dependencies from the framework.</span></span> <span data-ttu-id="6327b-121">您也可以將單元測試保存在整合測試以外的個別專案中，並確保您的單元測試專案不會參考基礎結構套件，或不具有基礎結構套件的相依性。</span><span class="sxs-lookup"><span data-stu-id="6327b-121">You can also keep your unit tests in a separate project from your integration tests, and ensure your unit test project doesn’t have references to or dependencies on infrastructure packages.</span></span>

<span data-ttu-id="6327b-122">進一步了解 .NET Core 專案的單元測試：</span><span class="sxs-lookup"><span data-stu-id="6327b-122">Learn more about unit testing in .NET Core projects:</span></span>

* <span data-ttu-id="6327b-123">請參閱這份[使用 xUnit 和 .NET Core CLI 建立單元測試的逐步解說](unit-testing-with-dotnet-test.md)。</span><span class="sxs-lookup"><span data-stu-id="6327b-123">Try this [walkthrough creating unit tests with xUnit and the .NET Core CLI](unit-testing-with-dotnet-test.md).</span></span> 
* <span data-ttu-id="6327b-124">XUnit 小組已撰寫本教學課程以說明[如何在 .NET Core 和 Visual Studio 中搭配使用 xUnit](http://xunit.github.io/docs/getting-started-dotnet-core.html)。</span><span class="sxs-lookup"><span data-stu-id="6327b-124">The XUnit team has written a tutorial that shows [how to use xUnit with .NET Core and Visual Studio](http://xunit.github.io/docs/getting-started-dotnet-core.html).</span></span>
* <span data-ttu-id="6327b-125">如果您偏好使用 MSTest，請參閱這份[使用 MSTest 和 .NET Core CLI 建立單元測試的逐步解說](unit-testing-with-mstest.md)。</span><span class="sxs-lookup"><span data-stu-id="6327b-125">If you prefer using MSTest, try the [walkthrough creating unit tests with MSTest and the .NET Core CLI](unit-testing-with-mstest.md).</span></span>
* <span data-ttu-id="6327b-126">如需如何使用選擇性單元測試篩選的其他資訊及範例，請參閱[執行選擇性單元測試](../testing/selective-unit-tests.md)。</span><span class="sxs-lookup"><span data-stu-id="6327b-126">For a additional information and examples on how to use selective unit test filtering, see [Running selective unit tests](../testing/selective-unit-tests.md).</span></span>

