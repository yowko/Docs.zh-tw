---
title: 使用 Visual Studio Code 測試具有 .NET Core 的 .NET Standard 類別庫
description: 建立 .NET Core 類別庫的單元測試專案。 確認 .NET Core 類別庫可在單元測試中正常運作。
ms.date: 06/08/2020
ms.openlocfilehash: a61fd952eea2dec0d5a9f351d3f3d01c738e8fad
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701029"
---
# <a name="tutorial-test-a-net-standard-class-library-with-net-core-using-visual-studio-code"></a><span data-ttu-id="6b3c5-104">教學課程：使用 Visual Studio Code 測試具有 .NET Core 的 .NET Standard 類別庫</span><span class="sxs-lookup"><span data-stu-id="6b3c5-104">Tutorial: Test a .NET Standard class library with .NET Core using Visual Studio Code</span></span>

<span data-ttu-id="6b3c5-105">本教學課程說明如何藉由將測試專案加入至方案，來自動化單元測試。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6b3c5-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="6b3c5-106">Prerequisites</span></span>

- <span data-ttu-id="6b3c5-107">本教學課程適用于您在[Visual Studio Code 中建立 .NET Standard 程式庫](library-with-visual-studio-code.md)中建立的解決方案。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-107">This tutorial works with the solution that you create in [Create a .NET Standard library in Visual Studio Code](library-with-visual-studio-code.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="6b3c5-108">建立單元測試專案</span><span class="sxs-lookup"><span data-stu-id="6b3c5-108">Create a unit test project</span></span>

<span data-ttu-id="6b3c5-109">單元測試能在開發與發佈期間提供自動化的軟體測試。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-109">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="6b3c5-110">您在本教學課程中使用的測試架構是 MSTest。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-110">The testing framework that you use in this tutorial is MSTest.</span></span> <span data-ttu-id="6b3c5-111">[MSTest](https://github.com/Microsoft/testfx-docs)是您可以從中選擇的三種測試架構之一。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-111">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="6b3c5-112">其他則是[xUnit](https://xunit.net/)和[nUnit](https://nunit.org/)。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-112">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="6b3c5-113">啟動 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-113">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="6b3c5-114">開啟 `ClassLibraryProjects` 您在[Visual Studio 中建立 .NET Standard 程式庫](library-with-visual-studio.md)中建立的解決方案。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-114">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="6b3c5-115">建立名為 "StringLibraryTest" 的單元測試專案。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-115">Create a unit test project named "StringLibraryTest".</span></span>

   ```dotnetcli
   dotnet new mstest -o StringLibraryTest
   ```

   <span data-ttu-id="6b3c5-116">專案範本會使用下列程式碼來建立 UnitTest1.cs 檔案：</span><span class="sxs-lookup"><span data-stu-id="6b3c5-116">The project template creates a UnitTest1.cs file with the following code:</span></span>

   ```csharp
   using Microsoft.VisualStudio.TestTools.UnitTesting;

   namespace StringLibraryTest
   {
       [TestClass]
       public class UnitTest1
       {
           [TestMethod]
           public void TestMethod1()
           {
           }
       }
   }
   ```

   <span data-ttu-id="6b3c5-117">單元測試範本建立的原始程式碼會執行下列動作︰</span><span class="sxs-lookup"><span data-stu-id="6b3c5-117">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="6b3c5-118">它會匯入 <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 命名空間，其中包含用於單元測試的類型。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-118">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="6b3c5-119">它會將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 屬性套用至 `UnitTest1` 類別。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-119">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="6b3c5-120">它會套用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性來定義 `TestMethod1` 。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-120">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1`.</span></span>

   <span data-ttu-id="6b3c5-121">執行單元測試時，會自動執行在標記為[[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute)的測試類別中，以[[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute)標記的每個方法。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-121">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

1. <span data-ttu-id="6b3c5-122">將測試專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-122">Add the test project to the solution.</span></span>

   ```dotnetcli
   dotnet sln add StringLibraryTest/StringLibraryTest.csproj
   ```

## <a name="add-a-project-reference"></a><span data-ttu-id="6b3c5-123">新增專案參考</span><span class="sxs-lookup"><span data-stu-id="6b3c5-123">Add a project reference</span></span>

<span data-ttu-id="6b3c5-124">若要讓測試專案與類別搭配使用 `StringLibrary` ，請在專案中加入 `StringLibraryTest` 專案的參考 `StringLibrary` 。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-124">For the test project to work with the `StringLibrary` class, add a reference in the `StringLibraryTest` project to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="6b3c5-125">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="6b3c5-125">Run the following command:</span></span>

   ```dotnetcli
   dotnet add StringLibraryTest/StringLibraryTest.csproj reference StringLibrary/StringLibrary.csproj
   ```

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="6b3c5-126">新增和執行單元測試方法</span><span class="sxs-lookup"><span data-stu-id="6b3c5-126">Add and run unit test methods</span></span>

<span data-ttu-id="6b3c5-127">當 Visual Studio 執行單元測試時，它會在以屬性標記的類別中，執行以屬性標記的每個方法 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-127">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="6b3c5-128">測試方法會在發現第一個失敗或方法中包含的所有測試都成功時結束。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-128">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="6b3c5-129">最常見的測試會呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 類別的成員。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-129">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="6b3c5-130">許多判斷提示方法都至少包括兩個參數，一個是預期的測試結果，另一個是實際的測試結果。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-130">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="6b3c5-131">`Assert`下表顯示一些類別最常被呼叫的方法：</span><span class="sxs-lookup"><span data-stu-id="6b3c5-131">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="6b3c5-132">Assert 方法</span><span class="sxs-lookup"><span data-stu-id="6b3c5-132">Assert methods</span></span>     | <span data-ttu-id="6b3c5-133">函式</span><span class="sxs-lookup"><span data-stu-id="6b3c5-133">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="6b3c5-134">驗證兩個值或物件相等。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-134">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="6b3c5-135">如果值或物件不相等，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-135">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="6b3c5-136">驗證兩個物件變數參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-136">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="6b3c5-137">如果變數參考不同的物件，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-137">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="6b3c5-138">驗證條件為 `false`。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-138">Verifies that a condition is `false`.</span></span> <span data-ttu-id="6b3c5-139">如果條件為 `true`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-139">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="6b3c5-140">驗證物件不是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-140">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="6b3c5-141">如果物件為 `null`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-141">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="6b3c5-142">您也可以 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> 在測試方法中使用方法，以指出預期會擲回的例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-142">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="6b3c5-143">如果未擲回指定的例外狀況，測試將會失敗。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-143">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="6b3c5-144">在測試 `StringLibrary.StartsWithUpper` 方法時，您想提供幾個以大寫字元開頭的字串。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-144">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="6b3c5-145">您預期此方法在這些情況下傳回 `true`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-145">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="6b3c5-146">同樣地，您想提供幾個開頭不是大寫字元的字串。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-146">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="6b3c5-147">您預期此方法在這些情況下傳回 `false`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-147">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="6b3c5-148">由於您的程式庫方法會處理字串，因此您也會想要確定它會成功處理[空字串（ `String.Empty` ）](xref:System.String.Empty)和和 `null` 字串。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-148">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty) and a and a `null` string.</span></span> <span data-ttu-id="6b3c5-149">空字串是沒有任何字元的，其 <xref:System.String.Length> 為0。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-149">An empty string is one that has no characters and whose <xref:System.String.Length> is 0.</span></span> <span data-ttu-id="6b3c5-150">一個 `null` 字串尚未初始化。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-150">A `null` string is one that hasn't been initialized.</span></span> <span data-ttu-id="6b3c5-151">您可以 `StartsWithUpper` 直接呼叫做為靜態方法，並傳遞單一 <xref:System.String> 引數。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-151">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="6b3c5-152">或者，您可以 `StartsWithUpper` 在指派給的變數上呼叫作為擴充方法 `string` `null` 。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-152">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="6b3c5-153">您將定義三個方法，每個方法都會 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 針對字串陣列中的每個元素呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-153">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="6b3c5-154">您將呼叫方法多載，讓您指定要在測試失敗時顯示的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-154">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="6b3c5-155">訊息會識別造成失敗的字串。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-155">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="6b3c5-156">建立測試方法：</span><span class="sxs-lookup"><span data-stu-id="6b3c5-156">To create the test methods:</span></span>

1. <span data-ttu-id="6b3c5-157">開啟*StringLibraryTest/unittest1.cpp* ，並以下列程式碼取代所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-157">Open *StringLibraryTest/UnitTest1.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="6b3c5-158">方法中的大寫字元測試 `TestStartsWithUpper` 包含希臘文大寫字母 Alpha （u + 0391）和斯拉夫文大寫字母 EM （u + 041C）。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-158">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="6b3c5-159">方法中的小寫字元測試 `TestDoesNotStartWithUpper` 包含希臘文小寫字母 Alpha （u + 03B1）和斯拉夫文小寫字母 Ghe （u + 0433）。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-159">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="6b3c5-160">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-160">Save your changes.</span></span>

1. <span data-ttu-id="6b3c5-161">執行測試：</span><span class="sxs-lookup"><span data-stu-id="6b3c5-161">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="6b3c5-162">終端機輸出顯示所有測試都已通過。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-162">The terminal output shows that all tests passed.</span></span>

   ```
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.

   Test Run Successful.
   Total tests: 3
        Passed: 3
   Total time: 5.1116 Seconds
   ```

## <a name="handle-test-failures"></a><span data-ttu-id="6b3c5-163">處理測試失敗</span><span class="sxs-lookup"><span data-stu-id="6b3c5-163">Handle test failures</span></span>

<span data-ttu-id="6b3c5-164">如果您執行的是測試導向開發（TDD），您必須先撰寫測試，而且第一次執行時才會失敗。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-164">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="6b3c5-165">接著，您可以將程式碼新增至應用程式，讓測試成功。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-165">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="6b3c5-166">在本教學課程中，您已在撰寫應用程式驗證碼之後建立測試，因此您未看到測試失敗。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-166">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="6b3c5-167">若要驗證測試在預期失敗時失敗，請在測試輸入中加入不正確值。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-167">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="6b3c5-168">修改 `TestDoesNotStartWithUpper` 方法中的 `words` 陣列，以包含字串「錯誤」。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-168">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="6b3c5-169">執行測試：</span><span class="sxs-lookup"><span data-stu-id="6b3c5-169">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="6b3c5-170">終端機輸出顯示一個測試失敗，並提供失敗測試的錯誤訊息：「IsFalse 失敗。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-170">The terminal output shows that one test fails, and it provides an error message for the failed test: "Assert.IsFalse failed.</span></span> <span data-ttu-id="6b3c5-171">'Error' 的預期︰false；實際：True」。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-171">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="6b3c5-172">由於失敗，因此在測試「錯誤」之後，陣列中沒有任何字串。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-172">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   ```
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.
     X TestDoesNotStartWithUpper [283ms]
     Error Message:
      Assert.IsFalse failed. Expected for 'Error': false; Actual: True
     Stack Trace:
     at StringLibraryTest.UnitTest1.TestDoesNotStartWithUpper()
       in C:\Projects\ClassLibraryProjects\StringLibraryTest\UnitTest1.cs:line 33

   Test Run Failed.
   Total tests: 3
        Passed: 2
        Failed: 1
   Total time: 1.7825 Seconds
   ```

1. <span data-ttu-id="6b3c5-173">移除您在步驟1中新增的字串 "Error"。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-173">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="6b3c5-174">重新執行測試和測試階段。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-174">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="6b3c5-175">測試程式庫的發行版本</span><span class="sxs-lookup"><span data-stu-id="6b3c5-175">Test the Release version of the library</span></span>

<span data-ttu-id="6b3c5-176">現在，在執行程式庫的「偵錯工具」組建時，所有測試都已成功，請針對程式庫的發行組建，再次執行測試。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-176">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="6b3c5-177">許多因素 (包括編譯器最佳化) 有時會在偵錯和發行組建之間導致不同的行為。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-177">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

1. <span data-ttu-id="6b3c5-178">使用發行組建設定執行測試：</span><span class="sxs-lookup"><span data-stu-id="6b3c5-178">Run the tests with the Release build configuration:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj --configuration Release
   ```

   <span data-ttu-id="6b3c5-179">所有測試皆通過。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-179">The tests pass.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="6b3c5-180">其他資源</span><span class="sxs-lookup"><span data-stu-id="6b3c5-180">Additional resources</span></span>

* [<span data-ttu-id="6b3c5-181">.NET Core 與 .NET Standard 中的單元測試</span><span class="sxs-lookup"><span data-stu-id="6b3c5-181">Unit testing in .NET Core and .NET Standard</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="6b3c5-182">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6b3c5-182">Next steps</span></span>

<span data-ttu-id="6b3c5-183">在本教學課程中，您已對類別庫進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-183">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="6b3c5-184">您可以將程式庫發佈至[NuGet](https://nuget.org)作為套件，以供其他人使用。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-184">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="6b3c5-185">若要深入瞭解，請遵循 NuGet 教學課程：</span><span class="sxs-lookup"><span data-stu-id="6b3c5-185">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6b3c5-186">使用 dotnet CLI 建立及發佈套件</span><span class="sxs-lookup"><span data-stu-id="6b3c5-186">Create and publish a package using the dotnet CLI</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="6b3c5-187">如果您將程式庫發佈為 NuGet 套件，則其他人可以安裝並使用它。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-187">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="6b3c5-188">若要深入瞭解，請遵循 NuGet 教學課程：</span><span class="sxs-lookup"><span data-stu-id="6b3c5-188">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6b3c5-189">利用 dotnet CLI 安裝並使用套件</span><span class="sxs-lookup"><span data-stu-id="6b3c5-189">Install and use a package using the dotnet CLI</span></span>](/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli)

<span data-ttu-id="6b3c5-190">程式庫不一定要以封裝的形式散發。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-190">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="6b3c5-191">它可以與使用它的主控台應用程式配套。</span><span class="sxs-lookup"><span data-stu-id="6b3c5-191">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="6b3c5-192">若要瞭解如何發佈主控台應用程式，請參閱本系列中的先前教學課程：</span><span class="sxs-lookup"><span data-stu-id="6b3c5-192">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6b3c5-193">使用 Visual Studio Code 發行 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="6b3c5-193">Publish a .NET Core console application with Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)
