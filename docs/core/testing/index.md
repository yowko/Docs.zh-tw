---
title: 在 .NET 中測試
description: 本文簡要說明在 .NET 中測試的測試概念、術語和工具。
author: IEvangelist
ms.author: dapine
ms.date: 10/19/2020
ms.openlocfilehash: 36e88cc059447a98931593e0535c70cbc92a2cf4
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/20/2020
ms.locfileid: "92223472"
---
# <a name="testing-in-net"></a><span data-ttu-id="beba8-103">在 .NET 中測試</span><span class="sxs-lookup"><span data-stu-id="beba8-103">Testing in .NET</span></span>

<span data-ttu-id="beba8-104">本文介紹測試的概念，並說明如何使用不同類型的測試來驗證程式代碼。</span><span class="sxs-lookup"><span data-stu-id="beba8-104">This article introduces the concept of testing, and illustrates how different kinds of tests can be used to validate code.</span></span> <span data-ttu-id="beba8-105">有多種工具可用來測試 .NET 應用程式，例如 [.NET CLI](#net-cli) 或 [整合式開發環境 (ide) ](#ide)。</span><span class="sxs-lookup"><span data-stu-id="beba8-105">There are various tools available for testing .NET applications, such as the [.NET CLI](#net-cli) or [Integrated Development Environments (IDEs)](#ide).</span></span>

## <a name="test-types"></a><span data-ttu-id="beba8-106">測試類型</span><span class="sxs-lookup"><span data-stu-id="beba8-106">Test types</span></span>

<span data-ttu-id="beba8-107">擁有自動化測試是確保應用程式程式碼會執行其作者所要執行之作業的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="beba8-107">Having automated tests is a great way to ensure that application code does what its authors intend it to do.</span></span> <span data-ttu-id="beba8-108">本文涵蓋單元測試、整合測試和負載測試。</span><span class="sxs-lookup"><span data-stu-id="beba8-108">This article covers unit tests, integration tests, and load tests.</span></span>

### <a name="unit-tests"></a><span data-ttu-id="beba8-109">單元測試</span><span class="sxs-lookup"><span data-stu-id="beba8-109">Unit tests</span></span>

<span data-ttu-id="beba8-110">*單元測試*是練習個別軟體元件或方法（也稱為「工作單位」）的測試。</span><span class="sxs-lookup"><span data-stu-id="beba8-110">A *unit test* is a test that exercises individual software components or methods, also known as "unit of work".</span></span> <span data-ttu-id="beba8-111">單元測試應該只測試開發人員控制項內的程式碼。</span><span class="sxs-lookup"><span data-stu-id="beba8-111">Unit tests should only test code within the developer's control.</span></span> <span data-ttu-id="beba8-112">它們並不會測試基礎結構的考慮。</span><span class="sxs-lookup"><span data-stu-id="beba8-112">They do not test infrastructure concerns.</span></span> <span data-ttu-id="beba8-113">基礎結構的考慮包括與資料庫、檔案系統和網路資源的互動。</span><span class="sxs-lookup"><span data-stu-id="beba8-113">Infrastructure concerns include interacting with databases, file systems, and network resources.</span></span>

<span data-ttu-id="beba8-114">如需有關建立單元測試的詳細資訊，請參閱 [測試控管](#testing-tools)。</span><span class="sxs-lookup"><span data-stu-id="beba8-114">For more information on creating unit tests, see [Testing tools](#testing-tools).</span></span>

### <a name="integration-tests"></a><span data-ttu-id="beba8-115">整合測試</span><span class="sxs-lookup"><span data-stu-id="beba8-115">Integration tests</span></span>

<span data-ttu-id="beba8-116">*整合測試*與單元測試不同之處在于，它會演練兩個或多個軟體元件的功能，也稱為「整合」。</span><span class="sxs-lookup"><span data-stu-id="beba8-116">An *integration test* differs from a unit test in that it exercises two or more software components' ability to function together, also known as their "integration."</span></span> <span data-ttu-id="beba8-117">這些測試會在較廣泛的受測系統上運作，而單元測試則著重于個別的元件。</span><span class="sxs-lookup"><span data-stu-id="beba8-117">These tests operate on a broader spectrum of the system under test, whereas unit tests focus on individual components.</span></span> <span data-ttu-id="beba8-118">整合測試通常會包含基礎結構考慮。</span><span class="sxs-lookup"><span data-stu-id="beba8-118">Often, integration tests do include infrastructure concerns.</span></span>

### <a name="load-tests"></a><span data-ttu-id="beba8-119">負載測試</span><span class="sxs-lookup"><span data-stu-id="beba8-119">Load tests</span></span>

<span data-ttu-id="beba8-120">*負載測試*的目標是要判斷系統是否可以處理指定的負載，例如，使用應用程式的並行使用者數目，以及應用程式處理互動佳的能力。</span><span class="sxs-lookup"><span data-stu-id="beba8-120">A *load test* aims to determine whether or not a system can handle a specified load, for example, the number of concurrent users using an application and the app's ability to handle interactions responsively.</span></span> <span data-ttu-id="beba8-121">如需有關 web 應用程式負載測試的詳細資訊，請參閱 [ASP.NET Core 負載/壓力測試](/aspnet/core/test/load-tests)。</span><span class="sxs-lookup"><span data-stu-id="beba8-121">For more information on load testing of web applications, see [ASP.NET Core load/stress testing](/aspnet/core/test/load-tests).</span></span>

## <a name="test-considerations"></a><span data-ttu-id="beba8-122">測試考慮</span><span class="sxs-lookup"><span data-stu-id="beba8-122">Test considerations</span></span>

<span data-ttu-id="beba8-123">請記住，有撰寫測試的 [最佳做法](unit-testing-best-practices.md) 。</span><span class="sxs-lookup"><span data-stu-id="beba8-123">Keep in mind there are [best practices](unit-testing-best-practices.md) for writing tests.</span></span> <span data-ttu-id="beba8-124">例如， [測試導向開發 (TDD) ](https://deviq.com/test-driven-development) 就是在要檢查的程式碼之前寫入單元測試。</span><span class="sxs-lookup"><span data-stu-id="beba8-124">For example, [Test Driven Development (TDD)](https://deviq.com/test-driven-development) is when a unit test is written before the code it's meant to check.</span></span> <span data-ttu-id="beba8-125">TDD 就像是在您撰寫書籍之前建立書籍的大綱。</span><span class="sxs-lookup"><span data-stu-id="beba8-125">TDD is like creating an outline for a book before you write it.</span></span> <span data-ttu-id="beba8-126">它的目標是協助開發人員撰寫更簡單、更易讀且更有效率的程式碼。</span><span class="sxs-lookup"><span data-stu-id="beba8-126">It is meant to help developers write simpler, more readable, and efficient code.</span></span>

## <a name="testing-tools"></a><span data-ttu-id="beba8-127">測試工具</span><span class="sxs-lookup"><span data-stu-id="beba8-127">Testing tools</span></span>

<span data-ttu-id="beba8-128">.Net 是多國語言的開發平臺，您可以撰寫適用于 [c #](../../csharp/index.yml)、 [F #](../../fsharp/index.yml)和 [Visual Basic](../../visual-basic/index.yml)的各種測試類型。</span><span class="sxs-lookup"><span data-stu-id="beba8-128">.NET is a multi-language development platform, and you can write various test types for [C#](../../csharp/index.yml), [F#](../../fsharp/index.yml), and [Visual Basic](../../visual-basic/index.yml).</span></span> <span data-ttu-id="beba8-129">針對上述每一種語言，您可以選擇數個測試架構。</span><span class="sxs-lookup"><span data-stu-id="beba8-129">For each of these languages, you can choose between several test frameworks.</span></span>

### <a name="xunit"></a><span data-ttu-id="beba8-130">xUnit</span><span class="sxs-lookup"><span data-stu-id="beba8-130">xUnit</span></span>

<span data-ttu-id="beba8-131">[xUnit](https://xunit.net) 是適用于 .net 的免費開放原始碼、以社區為導向的單元測試工具。</span><span class="sxs-lookup"><span data-stu-id="beba8-131">[xUnit](https://xunit.net) is a free, open source, community-focused unit testing tool for .NET.</span></span> <span data-ttu-id="beba8-132">XUnit.net 是由 NUnit v2 的原始發明者所撰寫，是適用于 .NET 應用程式單元測試的最新技術。</span><span class="sxs-lookup"><span data-stu-id="beba8-132">Written by the original inventor of NUnit v2, xUnit.net is the latest technology for unit testing .NET apps.</span></span> <span data-ttu-id="beba8-133">xUnit.net 適用于 ReSharper、CodeRush、TestDriven.NET 和 [Xamarin](/apps/xamarin)。</span><span class="sxs-lookup"><span data-stu-id="beba8-133">xUnit.net works with ReSharper, CodeRush, TestDriven.NET, and [Xamarin](/apps/xamarin).</span></span> <span data-ttu-id="beba8-134">它是 [.Net Foundation](https://dotnetfoundation.org) 的專案，並在其管理辦法下運作。</span><span class="sxs-lookup"><span data-stu-id="beba8-134">It is a project of the [.NET Foundation](https://dotnetfoundation.org) and operates under their code of conduct.</span></span>

<span data-ttu-id="beba8-135">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="beba8-135">For more information, see the following resources:</span></span>

- [<span data-ttu-id="beba8-136">使用 C 的單元測試#</span><span class="sxs-lookup"><span data-stu-id="beba8-136">Unit testing with C#</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="beba8-137">使用 F 的單元測試#</span><span class="sxs-lookup"><span data-stu-id="beba8-137">Unit testing with F#</span></span>](unit-testing-fsharp-with-dotnet-test.md)
- [<span data-ttu-id="beba8-138">使用 Visual Basic 的單元測試</span><span class="sxs-lookup"><span data-stu-id="beba8-138">Unit testing with Visual Basic</span></span>](unit-testing-visual-basic-with-dotnet-test.md)

### <a name="nunit"></a><span data-ttu-id="beba8-139">NUnit</span><span class="sxs-lookup"><span data-stu-id="beba8-139">NUnit</span></span>

<span data-ttu-id="beba8-140">[NUnit](https://nunit.org) 是適用于所有 .net 語言的單元測試架構。</span><span class="sxs-lookup"><span data-stu-id="beba8-140">[NUnit](https://nunit.org) is a unit-testing framework for all .NET languages.</span></span> <span data-ttu-id="beba8-141">從 JUnit 開始，目前的生產版本已重寫許多新功能，並支援各種不同的 .NET 平臺。</span><span class="sxs-lookup"><span data-stu-id="beba8-141">Initially ported from JUnit, the current production release has been rewritten with many new features and support for a wide range of .NET platforms.</span></span> <span data-ttu-id="beba8-142">它是 [.Net Foundation](https://dotnetfoundation.org)的專案。</span><span class="sxs-lookup"><span data-stu-id="beba8-142">It is a project of the [.NET Foundation](https://dotnetfoundation.org).</span></span>

<span data-ttu-id="beba8-143">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="beba8-143">For more information, see the following resources:</span></span>

- [<span data-ttu-id="beba8-144">使用 C 的單元測試#</span><span class="sxs-lookup"><span data-stu-id="beba8-144">Unit testing with C#</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="beba8-145">使用 F 的單元測試#</span><span class="sxs-lookup"><span data-stu-id="beba8-145">Unit testing with F#</span></span>](unit-testing-fsharp-with-nunit.md)
- [<span data-ttu-id="beba8-146">使用 Visual Basic 的單元測試</span><span class="sxs-lookup"><span data-stu-id="beba8-146">Unit testing with Visual Basic</span></span>](unit-testing-visual-basic-with-nunit.md)

### <a name="mstest"></a><span data-ttu-id="beba8-147">MSTest</span><span class="sxs-lookup"><span data-stu-id="beba8-147">MSTest</span></span>

<span data-ttu-id="beba8-148">[MSTest](https://github.com/Microsoft/testfx-docs) 是適用于所有 .net 語言的 Microsoft 測試架構。</span><span class="sxs-lookup"><span data-stu-id="beba8-148">[MSTest](https://github.com/Microsoft/testfx-docs) is the Microsoft test framework for all .NET languages.</span></span> <span data-ttu-id="beba8-149">它是可擴充的，而且可搭配 .NET CLI 和 Visual Studio 使用。</span><span class="sxs-lookup"><span data-stu-id="beba8-149">It's extensible and works with both .NET CLI and Visual Studio.</span></span> <span data-ttu-id="beba8-150">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="beba8-150">For more information, see the following resources:</span></span>

- [<span data-ttu-id="beba8-151">使用 C 的單元測試#</span><span class="sxs-lookup"><span data-stu-id="beba8-151">Unit testing with C#</span></span>](unit-testing-with-mstest.md)
- [<span data-ttu-id="beba8-152">使用 F 的單元測試#</span><span class="sxs-lookup"><span data-stu-id="beba8-152">Unit testing with F#</span></span>](unit-testing-fsharp-with-mstest.md)
- [<span data-ttu-id="beba8-153">使用 Visual Basic 的單元測試</span><span class="sxs-lookup"><span data-stu-id="beba8-153">Unit testing with Visual Basic</span></span>](unit-testing-visual-basic-with-mstest.md)

### <a name="net-cli"></a><span data-ttu-id="beba8-154">.NET CLI</span><span class="sxs-lookup"><span data-stu-id="beba8-154">.NET CLI</span></span>

<span data-ttu-id="beba8-155">您可以使用[dotnet test](../tools/dotnet-test.md)命令，從[.net CLI](../tools/index.md)執行解決方案單元測試。</span><span class="sxs-lookup"><span data-stu-id="beba8-155">You can run a solutions unit tests from the [.NET CLI](../tools/index.md), with the [dotnet test](../tools/dotnet-test.md) command.</span></span> <span data-ttu-id="beba8-156">.NET CLI [ (ide) ](#ide) 提供的大部分功能，都可透過使用者介面來公開。</span><span class="sxs-lookup"><span data-stu-id="beba8-156">The .NET CLI exposes a majority of the functionality that [Integrated Development Environments (IDEs)](#ide) make available through user interfaces.</span></span> <span data-ttu-id="beba8-157">.NET CLI 可跨平臺使用，並可作為持續整合和傳遞管線的一部分。</span><span class="sxs-lookup"><span data-stu-id="beba8-157">The .NET CLI is cross-platform and available to use as part of continuous integration and delivery pipelines.</span></span> <span data-ttu-id="beba8-158">.NET CLI 會與腳本處理常式搭配使用，以將一般工作自動化。</span><span class="sxs-lookup"><span data-stu-id="beba8-158">The .NET CLI is used with scripted processes to automate common tasks.</span></span>

### <a name="ide"></a><span data-ttu-id="beba8-159">IDE</span><span class="sxs-lookup"><span data-stu-id="beba8-159">IDE</span></span>

<span data-ttu-id="beba8-160">無論您是使用 Visual Studio、Visual Studio for Mac 或 Visual Studio Code，都有用於測試功能的圖形化使用者介面。</span><span class="sxs-lookup"><span data-stu-id="beba8-160">Whether you're using Visual Studio, Visual Studio for Mac, or Visual Studio Code, there are graphical user interfaces for testing functionality.</span></span> <span data-ttu-id="beba8-161">Ide 有比 CLI 更多的可用功能，例如 [Live Unit Testing](/visualstudio/test/live-unit-testing)。</span><span class="sxs-lookup"><span data-stu-id="beba8-161">There are more features available to IDEs than the CLI, for example [Live Unit Testing](/visualstudio/test/live-unit-testing).</span></span> <span data-ttu-id="beba8-162">如需詳細資訊，請參閱 [包含和排除具有 Visual Studio 的測試](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods)。</span><span class="sxs-lookup"><span data-stu-id="beba8-162">For more information, see [Including and excluding tests with Visual Studio](/visualstudio/test/live-unit-testing#include-and-exclude-test-projects-and-test-methods).</span></span>

## <a name="see-also"></a><span data-ttu-id="beba8-163">請參閱</span><span class="sxs-lookup"><span data-stu-id="beba8-163">See also</span></span>

<span data-ttu-id="beba8-164">如需詳細資訊，請參閱下列文章：</span><span class="sxs-lookup"><span data-stu-id="beba8-164">For more information, see the following articles:</span></span>

- [<span data-ttu-id="beba8-165">使用 .NET 的單元測試最佳做法</span><span class="sxs-lookup"><span data-stu-id="beba8-165">Unit testing best practices with .NET</span></span>](unit-testing-best-practices.md)
- [<span data-ttu-id="beba8-166">ASP.NET Core 中的整合測試</span><span class="sxs-lookup"><span data-stu-id="beba8-166">Integration tests in ASP.NET Core</span></span>](/aspnet/core/test/integration-tests#test-app-prerequisites)
- [<span data-ttu-id="beba8-167">執行選擇性單元測試</span><span class="sxs-lookup"><span data-stu-id="beba8-167">Running selective unit tests</span></span>](selective-unit-tests.md)
- [<span data-ttu-id="beba8-168">使用程式碼涵蓋範圍進行單元測試</span><span class="sxs-lookup"><span data-stu-id="beba8-168">Use code coverage for unit testing</span></span>](unit-testing-code-coverage.md)
