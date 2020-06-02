---
title: 在 Visual Studio Code 中使用 .NET Core 測試 .NET Standard 類別庫
description: 建立 .NET Core 類別庫的單元測試專案。 確認 .NET Core 類別庫可在單元測試中正常運作。
ms.date: 05/29/2020
ms.openlocfilehash: be227453bd441028cc6ce348c00fad944140238f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292186"
---
# <a name="tutorial-test-a-net-standard-library-with-net-core-in-visual-studio-code"></a><span data-ttu-id="db12d-104">教學課程：在 Visual Studio Code 中使用 .NET Core 測試 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="db12d-104">Tutorial: Test a .NET Standard library with .NET Core in Visual Studio Code</span></span>

<span data-ttu-id="db12d-105">本教學課程說明如何藉由將測試專案加入至方案，來自動化單元測試。</span><span class="sxs-lookup"><span data-stu-id="db12d-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="db12d-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="db12d-106">Prerequisites</span></span>

- <span data-ttu-id="db12d-107">本教學課程適用于您在[Visual Studio Code 中建立 .NET Standard 程式庫](library-with-visual-studio-code.md)中建立的解決方案。</span><span class="sxs-lookup"><span data-stu-id="db12d-107">This tutorial works with the solution that you create in [Create a .NET Standard library in Visual Studio Code](library-with-visual-studio-code.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="db12d-108">建立單元測試專案</span><span class="sxs-lookup"><span data-stu-id="db12d-108">Create a unit test project</span></span>

1. <span data-ttu-id="db12d-109">開啟 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="db12d-109">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="db12d-110">開啟 `ClassLibraryProjects` 您在[Visual Studio 中建立 .NET Standard 程式庫](library-with-visual-studio.md)中建立的解決方案。</span><span class="sxs-lookup"><span data-stu-id="db12d-110">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="db12d-111">建立名為 "StringLibraryTest" 的單元測試專案。</span><span class="sxs-lookup"><span data-stu-id="db12d-111">Create a unit test project named "StringLibraryTest".</span></span>

   ```dotnetcli
   dotnet new mstest -o StringLibraryTest
   ```

   <span data-ttu-id="db12d-112">專案範本會使用下列程式碼來建立 UnitTest1.cs 檔案：</span><span class="sxs-lookup"><span data-stu-id="db12d-112">The project template creates a UnitTest1.cs file with the following code:</span></span>

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

   <span data-ttu-id="db12d-113">單元測試範本建立的原始程式碼會執行下列動作︰</span><span class="sxs-lookup"><span data-stu-id="db12d-113">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="db12d-114">它會匯入 <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 命名空間，其中包含用於單元測試的類型。</span><span class="sxs-lookup"><span data-stu-id="db12d-114">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="db12d-115">它會將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 屬性套用至 `UnitTest1` 類別。</span><span class="sxs-lookup"><span data-stu-id="db12d-115">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="db12d-116">它會套用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性來定義 `TestMethod1` 。</span><span class="sxs-lookup"><span data-stu-id="db12d-116">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1`.</span></span>

   <span data-ttu-id="db12d-117">執行單元測試時，會自動執行在標記為[[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute)的測試類別中，以[[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute)標記的每個方法。</span><span class="sxs-lookup"><span data-stu-id="db12d-117">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

   > [!NOTE]
   > <span data-ttu-id="db12d-118">MSTest 是您可以從中選擇的三種測試架構之一。</span><span class="sxs-lookup"><span data-stu-id="db12d-118">MSTest is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="db12d-119">其他則是 xUnit 和 nUnit。</span><span class="sxs-lookup"><span data-stu-id="db12d-119">The others are xUnit and nUnit.</span></span>

1. <span data-ttu-id="db12d-120">將測試專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="db12d-120">Add the test project to the solution.</span></span>

   ```dotnetcli
   dotnet sln add StringLibraryTest/StringLibraryTest.csproj
   ```

1. <span data-ttu-id="db12d-121">執行下列命令，以建立類別庫專案的專案參考：</span><span class="sxs-lookup"><span data-stu-id="db12d-121">Create a project reference to the class library project by running the following command:</span></span>

   ```dotnetcli
   dotnet add StringLibraryTest/StringLibraryTest.csproj reference StringLibrary/StringLibrary.csproj
   ```

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="db12d-122">新增和執行單元測試方法</span><span class="sxs-lookup"><span data-stu-id="db12d-122">Add and run unit test methods</span></span>

<span data-ttu-id="db12d-123">當 Visual Studio 執行單元測試時，它會在以屬性標記的類別中，執行以屬性標記的每個方法 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="db12d-123">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="db12d-124">測試方法會在發現第一個失敗或方法中包含的所有測試都成功時結束。</span><span class="sxs-lookup"><span data-stu-id="db12d-124">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="db12d-125">最常見的測試會呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 類別的成員。</span><span class="sxs-lookup"><span data-stu-id="db12d-125">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="db12d-126">許多判斷提示方法都至少包括兩個參數，一個是預期的測試結果，另一個是實際的測試結果。</span><span class="sxs-lookup"><span data-stu-id="db12d-126">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="db12d-127">`Assert`下表顯示一些類別最常被呼叫的方法：</span><span class="sxs-lookup"><span data-stu-id="db12d-127">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="db12d-128">Assert 方法</span><span class="sxs-lookup"><span data-stu-id="db12d-128">Assert methods</span></span>     | <span data-ttu-id="db12d-129">函式</span><span class="sxs-lookup"><span data-stu-id="db12d-129">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="db12d-130">驗證兩個值或物件相等。</span><span class="sxs-lookup"><span data-stu-id="db12d-130">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="db12d-131">如果值或物件不相等，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="db12d-131">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="db12d-132">驗證兩個物件變數參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="db12d-132">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="db12d-133">如果變數參考不同的物件，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="db12d-133">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="db12d-134">驗證條件為 `false`。</span><span class="sxs-lookup"><span data-stu-id="db12d-134">Verifies that a condition is `false`.</span></span> <span data-ttu-id="db12d-135">如果條件為 `true`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="db12d-135">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="db12d-136">驗證物件不是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="db12d-136">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="db12d-137">如果物件為 `null`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="db12d-137">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="db12d-138">您也可以 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> 在測試方法中使用方法，以指出預期會擲回的例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="db12d-138">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="db12d-139">如果未擲回指定的例外狀況，測試將會失敗。</span><span class="sxs-lookup"><span data-stu-id="db12d-139">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="db12d-140">在測試 `StringLibrary.StartsWithUpper` 方法時，您想提供幾個以大寫字元開頭的字串。</span><span class="sxs-lookup"><span data-stu-id="db12d-140">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="db12d-141">您預期此方法在這些情況下傳回 `true`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="db12d-141">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="db12d-142">同樣地，您想提供幾個開頭不是大寫字元的字串。</span><span class="sxs-lookup"><span data-stu-id="db12d-142">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="db12d-143">您預期此方法在這些情況下傳回 `false`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="db12d-143">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="db12d-144">由於您的程式庫方法會處理字串，因此您也會想要確定它會成功處理[空字串（ `String.Empty` ）](xref:System.String.Empty)和和 `null` 字串。</span><span class="sxs-lookup"><span data-stu-id="db12d-144">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty) and a and a `null` string.</span></span> <span data-ttu-id="db12d-145">空字串是沒有任何字元的，其 <xref:System.String.Length> 為0。</span><span class="sxs-lookup"><span data-stu-id="db12d-145">An empty string is one that has no characters and whose <xref:System.String.Length> is 0.</span></span> <span data-ttu-id="db12d-146">一個 `null` 字串尚未初始化。</span><span class="sxs-lookup"><span data-stu-id="db12d-146">A `null` string is one that hasn't been initialized.</span></span> <span data-ttu-id="db12d-147">您可以 `StartsWithUpper` 直接呼叫做為靜態方法，並傳遞單一 <xref:System.String> 引數。</span><span class="sxs-lookup"><span data-stu-id="db12d-147">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="db12d-148">或者，您可以 `StartsWithUpper` 在指派給的變數上呼叫作為擴充方法 `string` `null` 。</span><span class="sxs-lookup"><span data-stu-id="db12d-148">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="db12d-149">您會定義三個方法，每個方法會 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 針對字串陣列中的每個元素重複呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="db12d-149">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="db12d-150">因為測試方法會在發現第一次失敗時失敗，所以您會呼叫方法多載，讓您傳遞一個字串來表示方法呼叫中所使用的字串值。</span><span class="sxs-lookup"><span data-stu-id="db12d-150">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="db12d-151">建立測試方法：</span><span class="sxs-lookup"><span data-stu-id="db12d-151">To create the test methods:</span></span>

1. <span data-ttu-id="db12d-152">開啟*StringLibraryTest/unittest1.cpp* ，並以下列程式碼取代所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="db12d-152">Open *StringLibraryTest/UnitTest1.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="db12d-153">方法中的大寫字元測試 `TestStartsWithUpper` 包含希臘文大寫字母 Alpha （u + 0391）和斯拉夫文大寫字母 EM （u + 041C）。</span><span class="sxs-lookup"><span data-stu-id="db12d-153">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="db12d-154">方法中的小寫字元測試 `TestDoesNotStartWithUpper` 包含希臘文小寫字母 Alpha （u + 03B1）和斯拉夫文小寫字母 Ghe （u + 0433）。</span><span class="sxs-lookup"><span data-stu-id="db12d-154">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="db12d-155">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="db12d-155">Save your changes.</span></span>

1. <span data-ttu-id="db12d-156">執行測試：</span><span class="sxs-lookup"><span data-stu-id="db12d-156">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="db12d-157">終端機輸出顯示所有測試都已通過。</span><span class="sxs-lookup"><span data-stu-id="db12d-157">The terminal output shows that all tests passed.</span></span>

   ```
   Starting test execution, please wait...

   A total of 1 test files matched the specified pattern.

   Test Run Successful.
   Total tests: 3
        Passed: 3
   Total time: 5.1116 Seconds
   ```

## <a name="handle-test-failures"></a><span data-ttu-id="db12d-158">處理測試失敗</span><span class="sxs-lookup"><span data-stu-id="db12d-158">Handle test failures</span></span>

<span data-ttu-id="db12d-159">如果您執行的是測試導向開發（TDD），您必須先撰寫測試，而且第一次執行時才會失敗。</span><span class="sxs-lookup"><span data-stu-id="db12d-159">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="db12d-160">接著，您可以將程式碼新增至應用程式，讓測試成功。</span><span class="sxs-lookup"><span data-stu-id="db12d-160">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="db12d-161">在此情況下，您在撰寫應用程式驗證碼之後就已建立測試，因此您未看到測試失敗。</span><span class="sxs-lookup"><span data-stu-id="db12d-161">In this case, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="db12d-162">若要驗證測試在預期失敗時失敗，請在測試輸入中加入不正確值。</span><span class="sxs-lookup"><span data-stu-id="db12d-162">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="db12d-163">修改 `TestDoesNotStartWithUpper` 方法中的 `words` 陣列，以包含字串「錯誤」。</span><span class="sxs-lookup"><span data-stu-id="db12d-163">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="db12d-164">執行測試：</span><span class="sxs-lookup"><span data-stu-id="db12d-164">Run the tests:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj
   ```

   <span data-ttu-id="db12d-165">終端機輸出顯示一個測試失敗，並提供失敗測試的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="db12d-165">The terminal output shows that one test fails, and it provides an error message for the failed test.</span></span>

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

1. <span data-ttu-id="db12d-166">復原您在步驟 1 中所做的修改，並移除字串 "Error"。</span><span class="sxs-lookup"><span data-stu-id="db12d-166">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="db12d-167">重新執行測試和測試階段。</span><span class="sxs-lookup"><span data-stu-id="db12d-167">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="db12d-168">測試程式庫的發行版本</span><span class="sxs-lookup"><span data-stu-id="db12d-168">Test the Release version of the library</span></span>

<span data-ttu-id="db12d-169">在執行程式庫的「偵錯工具」版本後，現在所有測試都已成功，請針對程式庫的發行組建，再次執行測試。</span><span class="sxs-lookup"><span data-stu-id="db12d-169">Now that the tests have all passed when running the Debug version of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="db12d-170">許多因素 (包括編譯器最佳化) 有時會在偵錯和發行組建之間導致不同的行為。</span><span class="sxs-lookup"><span data-stu-id="db12d-170">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

1. <span data-ttu-id="db12d-171">使用發行組建設定執行測試：</span><span class="sxs-lookup"><span data-stu-id="db12d-171">Run the tests with the Release build configuration:</span></span>

   ```dotnetcli
   dotnet test StringLibraryTest/StringLibraryTest.csproj --configuration Release
   ```

   <span data-ttu-id="db12d-172">所有測試皆通過。</span><span class="sxs-lookup"><span data-stu-id="db12d-172">The tests pass.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="db12d-173">其他資源</span><span class="sxs-lookup"><span data-stu-id="db12d-173">Additional resources</span></span>

- [<span data-ttu-id="db12d-174">.NET Core 與 .NET Standard 中的單元測試</span><span class="sxs-lookup"><span data-stu-id="db12d-174">Unit testing in .NET Core and .NET Standard</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="db12d-175">後續步驟</span><span class="sxs-lookup"><span data-stu-id="db12d-175">Next steps</span></span>

<span data-ttu-id="db12d-176">在本教學課程中，您已對類別庫進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="db12d-176">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="db12d-177">您可以將程式庫發佈至[NuGet](https://nuget.org)作為套件，以供其他人使用。</span><span class="sxs-lookup"><span data-stu-id="db12d-177">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="db12d-178">若要深入瞭解，請遵循 NuGet 教學課程：</span><span class="sxs-lookup"><span data-stu-id="db12d-178">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="db12d-179">使用 dotnet CLI 建立及發佈套件</span><span class="sxs-lookup"><span data-stu-id="db12d-179">Create and publish a package using the dotnet CLI</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="db12d-180">如果您將程式庫發佈為 NuGet 套件，則其他人可以安裝並使用它。</span><span class="sxs-lookup"><span data-stu-id="db12d-180">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="db12d-181">若要深入瞭解，請遵循 NuGet 教學課程：</span><span class="sxs-lookup"><span data-stu-id="db12d-181">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="db12d-182">利用 dotnet CLI 安裝並使用套件</span><span class="sxs-lookup"><span data-stu-id="db12d-182">Install and use a package using the dotnet CLI</span></span>](/nuget/quickstart/install-and-use-a-package-using-the-dotnet-cli)

<span data-ttu-id="db12d-183">程式庫不一定要以封裝的形式散發。</span><span class="sxs-lookup"><span data-stu-id="db12d-183">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="db12d-184">它可以與使用它的主控台應用程式配套。</span><span class="sxs-lookup"><span data-stu-id="db12d-184">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="db12d-185">若要瞭解如何發佈主控台應用程式，請參閱本系列中的先前教學課程：</span><span class="sxs-lookup"><span data-stu-id="db12d-185">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="db12d-186">使用 Visual Studio Code 發行 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="db12d-186">Publish a .NET Core console application with Visual Studio Code</span></span>](publishing-with-visual-studio-code.md)
