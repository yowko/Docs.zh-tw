---
title: 使用 Visual Studio 測試具有 .NET Core 的 .NET Standard 類別庫
description: 建立 .NET Core 類別庫的單元測試專案。 確認 .NET Core 類別庫可在單元測試中正確運作。
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 04d0120622697d1e0c84fc169dfc50951cb8aa3c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177289"
---
# <a name="tutorial-test-a-net-standard-class-library-with-net-core-using-visual-studio"></a><span data-ttu-id="04661-104">教學課程：使用 Visual Studio 以 .NET Core 測試 .NET Standard 類別庫</span><span class="sxs-lookup"><span data-stu-id="04661-104">Tutorial: Test a .NET Standard class library with .NET Core using Visual Studio</span></span>

<span data-ttu-id="04661-105">本教學課程示範如何將測試專案加入至方案，以自動化單元測試。</span><span class="sxs-lookup"><span data-stu-id="04661-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="04661-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="04661-106">Prerequisites</span></span>

- <span data-ttu-id="04661-107">本教學課程適用于 [使用 Visual Studio 建立 .NET Standard 程式庫](library-with-visual-studio.md)中所建立的解決方案。</span><span class="sxs-lookup"><span data-stu-id="04661-107">This tutorial works with the solution that you create in [Create a .NET Standard library using Visual Studio](library-with-visual-studio.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="04661-108">建立單元測試專案</span><span class="sxs-lookup"><span data-stu-id="04661-108">Create a unit test project</span></span>

<span data-ttu-id="04661-109">單元測試能在開發與發佈期間提供自動化的軟體測試。</span><span class="sxs-lookup"><span data-stu-id="04661-109">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="04661-110">[MSTest](https://github.com/Microsoft/testfx-docs) 是您可以從中選擇的三種測試架構之一。</span><span class="sxs-lookup"><span data-stu-id="04661-110">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="04661-111">其他則為 [xUnit](https://xunit.net/) 和 [nUnit](https://nunit.org/)。</span><span class="sxs-lookup"><span data-stu-id="04661-111">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="04661-112">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="04661-112">Start Visual Studio.</span></span>

1. <span data-ttu-id="04661-113">開啟 `ClassLibraryProjects` 您在 [使用 Visual Studio 建立 .NET Standard 程式庫](library-with-visual-studio.md)中建立的方案。</span><span class="sxs-lookup"><span data-stu-id="04661-113">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library using Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="04661-114">將名為 "StringLibraryTest" 的新單元測試專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="04661-114">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="04661-115">以滑鼠右鍵按一下**方案總管**中的方案，然後選取 [**加入**  >  **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="04661-115">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="04661-116">在 [ **加入新的專案** ] 頁面上，于 [搜尋] 方塊中輸入 **mstest** 。</span><span class="sxs-lookup"><span data-stu-id="04661-116">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="04661-117">從 [語言] 清單中選擇 [ **c #** ] 或 [ **Visual Basic** ，然後從 [平臺] 清單中選擇 [ **所有平臺** ]。</span><span class="sxs-lookup"><span data-stu-id="04661-117">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="04661-118">選擇 [ \*\*MSTest 測試專案 ( .Net Core) \*\* 範本]，然後選擇 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="04661-118">Choose the **MSTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="04661-119">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**StringLibraryTest** 。</span><span class="sxs-lookup"><span data-stu-id="04661-119">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="04661-120">接著，選擇 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="04661-120">Then choose **Create**.</span></span>

1. <span data-ttu-id="04661-121">Visual Studio 建立專案，並使用下列程式碼在程式碼視窗中開啟類別檔案。</span><span class="sxs-lookup"><span data-stu-id="04661-121">Visual Studio creates the project and opens the class file in the code window with the following code.</span></span> <span data-ttu-id="04661-122">如果未顯示您想要使用的語言，請變更頁面頂端的語言選取器。</span><span class="sxs-lookup"><span data-stu-id="04661-122">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

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

   ```vb
   Imports Microsoft.VisualStudio.TestTools.UnitTesting

   Namespace StringLibraryTest
       <TestClass>
       Public Class UnitTest1
           <TestMethod>
           Sub TestSub()

           End Sub
       End Class
   End Namespace
   ```

   <span data-ttu-id="04661-123">單元測試範本建立的原始程式碼會執行下列動作︰</span><span class="sxs-lookup"><span data-stu-id="04661-123">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="04661-124">它會匯入 <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 命名空間，其中包含用於單元測試的類型。</span><span class="sxs-lookup"><span data-stu-id="04661-124">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="04661-125">它會將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 屬性套用至 `UnitTest1` 類別。</span><span class="sxs-lookup"><span data-stu-id="04661-125">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="04661-126">它會套用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性，以 `TestMethod1` 在 c # 或 `TestSub` Visual Basic 中定義。</span><span class="sxs-lookup"><span data-stu-id="04661-126">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic.</span></span>

   <span data-ttu-id="04661-127">執行單元測試時，會自動執行在標記為[[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute)的測試類別中，以[[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute)標記的每個方法。</span><span class="sxs-lookup"><span data-stu-id="04661-127">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="04661-128">新增專案參考</span><span class="sxs-lookup"><span data-stu-id="04661-128">Add a project reference</span></span>

<span data-ttu-id="04661-129">若要讓測試專案使用 `StringLibrary` 類別，請在 **StringLibraryTest** 專案中加入專案的參考 `StringLibrary` 。</span><span class="sxs-lookup"><span data-stu-id="04661-129">For the test project to work with the `StringLibrary` class, add a reference in the **StringLibraryTest** project to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="04661-130">在**方案總管**中，以滑鼠右鍵按一下**StringLibraryTest**專案的 [相依性] 節點，然後從內容功能表中選取 [**加入專案參考** **]** 。</span><span class="sxs-lookup"><span data-stu-id="04661-130">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Project Reference** from the context menu.</span></span>

1. <span data-ttu-id="04661-131">在 [ **參考管理員** ] 對話方塊中，展開 [ **專案** ] 節點，然後選取 [ **StringLibrary**] 旁的方塊。</span><span class="sxs-lookup"><span data-stu-id="04661-131">In the **Reference Manager** dialog, expand the **Projects** node, and select the box next to **StringLibrary**.</span></span> <span data-ttu-id="04661-132">加入元件的參考，可讓編譯器在 `StringLibrary` 編譯**StringLibraryTest**專案時尋找**StringLibrary**方法。</span><span class="sxs-lookup"><span data-stu-id="04661-132">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods while compiling the **StringLibraryTest** project.</span></span>

1. <span data-ttu-id="04661-133">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="04661-133">Select **OK**.</span></span>

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="04661-134">加入並執行單元測試方法</span><span class="sxs-lookup"><span data-stu-id="04661-134">Add and run unit test methods</span></span>

<span data-ttu-id="04661-135">當 Visual Studio 執行單元測試時，它會執行每個以屬性標記之 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 類別中的屬性標記的方法  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="04661-135">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="04661-136">當找到第一個失敗或方法中包含的所有測試都成功時，測試方法便會結束。</span><span class="sxs-lookup"><span data-stu-id="04661-136">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="04661-137">最常見的測試會呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 類別的成員。</span><span class="sxs-lookup"><span data-stu-id="04661-137">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="04661-138">許多判斷提示方法都至少包括兩個參數，一個是預期的測試結果，另一個是實際的測試結果。</span><span class="sxs-lookup"><span data-stu-id="04661-138">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="04661-139">`Assert`下表顯示某些類別最常呼叫的方法：</span><span class="sxs-lookup"><span data-stu-id="04661-139">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="04661-140">Assert 方法</span><span class="sxs-lookup"><span data-stu-id="04661-140">Assert methods</span></span>     | <span data-ttu-id="04661-141">函式</span><span class="sxs-lookup"><span data-stu-id="04661-141">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="04661-142">驗證兩個值或物件相等。</span><span class="sxs-lookup"><span data-stu-id="04661-142">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="04661-143">如果值或物件不相等，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="04661-143">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="04661-144">驗證兩個物件變數參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="04661-144">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="04661-145">如果變數參考不同的物件，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="04661-145">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="04661-146">驗證條件為 `false`。</span><span class="sxs-lookup"><span data-stu-id="04661-146">Verifies that a condition is `false`.</span></span> <span data-ttu-id="04661-147">如果條件為 `true`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="04661-147">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="04661-148">確認物件不是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="04661-148">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="04661-149">如果物件為 `null`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="04661-149">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="04661-150">您也可以 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> 在測試方法中使用方法，來指出預期會擲回的例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="04661-150">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="04661-151">如果未擲回指定的例外狀況，測試便會失敗。</span><span class="sxs-lookup"><span data-stu-id="04661-151">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="04661-152">在測試 `StringLibrary.StartsWithUpper` 方法時，您想提供幾個以大寫字元開頭的字串。</span><span class="sxs-lookup"><span data-stu-id="04661-152">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="04661-153">您預期此方法在這些情況下傳回 `true`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="04661-153">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="04661-154">同樣地，您想提供幾個開頭不是大寫字元的字串。</span><span class="sxs-lookup"><span data-stu-id="04661-154">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="04661-155">您預期此方法在這些情況下傳回 `false`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="04661-155">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="04661-156">因為您的程式庫方法會處理字串，您也想要確保它能成功處理 [空字串 (`String.Empty`) ](xref:System.String.Empty)、沒有任何字元且其為0的有效字串 <xref:System.String.Length> ，以及 `null` 尚未初始化的字串。</span><span class="sxs-lookup"><span data-stu-id="04661-156">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="04661-157">您可以 `StartsWithUpper` 直接呼叫作為靜態方法，並傳遞單一 <xref:System.String> 引數。</span><span class="sxs-lookup"><span data-stu-id="04661-157">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="04661-158">或者，您可以 `StartsWithUpper` 在指派給的變數上呼叫做為擴充方法 `string` `null` 。</span><span class="sxs-lookup"><span data-stu-id="04661-158">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="04661-159">您會定義三個方法，每個方法會 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 針對字串陣列中的每個元素呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="04661-159">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="04661-160">您將呼叫方法多載，讓您指定在測試失敗時所要顯示的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="04661-160">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="04661-161">訊息會識別造成失敗的字串。</span><span class="sxs-lookup"><span data-stu-id="04661-161">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="04661-162">建立測試方法：</span><span class="sxs-lookup"><span data-stu-id="04661-162">To create the test methods:</span></span>

1. <span data-ttu-id="04661-163">在 [ *UnitTest1.cs* ] 或 [ *UnitTest1* ] 程式碼視窗中，將程式碼取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="04661-163">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibraryTest/UnitTest1.vb":::

   <span data-ttu-id="04661-164">方法中的大寫字元測試 `TestStartsWithUpper` 包含希臘文大寫字母 Alpha (u + 0391) 和斯拉夫文大寫字母 EM (U + 041C) 。</span><span class="sxs-lookup"><span data-stu-id="04661-164">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="04661-165">方法中的小寫字元測試 `TestDoesNotStartWithUpper` 包含希臘文小寫字母 Alpha (u + 03B1) 和斯拉夫文小寫字母 Ghe (U + 0433) 。</span><span class="sxs-lookup"><span data-stu-id="04661-165">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="04661-166">在功能表列上，選取 [ **file**  >  **save UnitTest1.cs as** ] 或 [ **file**  >  **save UnitTest1**]。</span><span class="sxs-lookup"><span data-stu-id="04661-166">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="04661-167">在 [另存新檔]\*\*\*\* 對話方塊中，選取 [儲存]\*\*\*\* 按鈕旁的箭號，然後選取 [以編碼方式儲存]\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="04661-167">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="04661-168">![Visual Studio 另存新檔] 對話方塊](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="04661-168">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="04661-169">在 [確認另存新檔]\*\*\*\* 對話方塊中，選取 [是]\*\*\*\* 按鈕以儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="04661-169">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="04661-170">在 [進階儲存選項]\*\*\*\* 對話方塊中，選取 [編碼]\*\*\*\* 下拉式清單中的 [Unicode (UTF-8 有簽章) - 字碼頁 65001]\*\*\*\*，然後選取 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="04661-170">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="04661-171">![Visual Studio [進階儲存選項] 對話方塊](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="04661-171">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="04661-172">如果您無法將您的原始程式碼儲存為 UTF8 編碼檔案，Visual Studio 可能會將它儲存為 ASCII 檔案。</span><span class="sxs-lookup"><span data-stu-id="04661-172">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="04661-173">當這種情況發生時，執行時間不會正確地解碼 ASCII 範圍以外的 UTF8 字元，而且測試結果將會不正確。</span><span class="sxs-lookup"><span data-stu-id="04661-173">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="04661-174">在功能表列上，選取 [**測試**  >  **執行所有測試**]。</span><span class="sxs-lookup"><span data-stu-id="04661-174">On the menu bar, select **Test** > **Run All Tests**.</span></span> <span data-ttu-id="04661-175">如果 [**測試瀏覽器**] 視窗未開啟，請選擇 [**測試**  >  **測試瀏覽器**] 將它開啟。</span><span class="sxs-lookup"><span data-stu-id="04661-175">If the **Test Explorer** window doesn't open, open it by choosing **Test** > **Test Explorer**.</span></span> <span data-ttu-id="04661-176">這三項測試都會列在 [通過的測試]\*\*\*\* 區段中，而 [摘要]\*\*\*\* 區段則報告測試回合的結果。</span><span class="sxs-lookup"><span data-stu-id="04661-176">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="04661-177">![測試總管視窗，其中包含通過的測試](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="04661-177">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="04661-178">處理測試失敗</span><span class="sxs-lookup"><span data-stu-id="04661-178">Handle test failures</span></span>

<span data-ttu-id="04661-179">如果您正在執行以測試為導向的開發 (TDD) ，您會先撰寫測試，並在您第一次執行時失敗。</span><span class="sxs-lookup"><span data-stu-id="04661-179">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="04661-180">然後，將程式碼新增至應用程式，讓測試成功。</span><span class="sxs-lookup"><span data-stu-id="04661-180">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="04661-181">在本教學課程中，您已在撰寫應用程式程式碼驗證之後建立測試，因此您未看到測試失敗。</span><span class="sxs-lookup"><span data-stu-id="04661-181">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="04661-182">若要在預期測試失敗時驗證測試失敗，請將不正確值加入測試輸入。</span><span class="sxs-lookup"><span data-stu-id="04661-182">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="04661-183">修改 `TestDoesNotStartWithUpper` 方法中的 `words` 陣列，以包含字串「錯誤」。</span><span class="sxs-lookup"><span data-stu-id="04661-183">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="04661-184">您不需要儲存檔案，因為當組建方案以執行測試時，Visual Studio 會自動儲存開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="04661-184">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="04661-185">從功能表列選取 [**測試**回合  >  **所有測試**] 以執行測試。</span><span class="sxs-lookup"><span data-stu-id="04661-185">Run the test by selecting **Test** > **Run All Tests** from the menu bar.</span></span> <span data-ttu-id="04661-186">[測試總管]\*\*\*\* 視窗表示兩個測試成功，而且有一項失敗。</span><span class="sxs-lookup"><span data-stu-id="04661-186">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="04661-187">![測試總管視窗，其中包含失敗的測試](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="04661-187">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="04661-188">選取失敗的測試 `TestDoesNotStartWith` 。</span><span class="sxs-lookup"><span data-stu-id="04661-188">Select the failed test, `TestDoesNotStartWith`.</span></span>

   <span data-ttu-id="04661-189">**[測試總管]** 下方的窗格會顯示判斷提示產生的訊息：「Assert.IsFalse 失敗。</span><span class="sxs-lookup"><span data-stu-id="04661-189">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="04661-190">'Error' 的預期︰false；實際：True」。</span><span class="sxs-lookup"><span data-stu-id="04661-190">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="04661-191">因為失敗，所以在測試 "Error" 之後，陣列中沒有任何字串。</span><span class="sxs-lookup"><span data-stu-id="04661-191">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="04661-192">![顯示 IsFalse 判斷提示失敗的 Test Explorer 視窗](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="04661-192">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="04661-193">移除您在步驟1中新增的字串 "Error"。</span><span class="sxs-lookup"><span data-stu-id="04661-193">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="04661-194">重新執行測試和測試階段。</span><span class="sxs-lookup"><span data-stu-id="04661-194">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="04661-195">測試程式庫的發行版本</span><span class="sxs-lookup"><span data-stu-id="04661-195">Test the Release version of the library</span></span>

<span data-ttu-id="04661-196">現在，在執行程式庫的偵錯工具時，所有測試都已通過，請針對程式庫的發行組建執行額外的測試。</span><span class="sxs-lookup"><span data-stu-id="04661-196">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="04661-197">許多因素 (包括編譯器最佳化) 有時會在偵錯和發行組建之間導致不同的行為。</span><span class="sxs-lookup"><span data-stu-id="04661-197">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="04661-198">測試發行組建︰</span><span class="sxs-lookup"><span data-stu-id="04661-198">To test the Release build:</span></span>

1. <span data-ttu-id="04661-199">在 Visual Studio 工具列中，將組建組態從 [偵錯]\*\*\*\* 變更為 [發行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="04661-199">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="04661-200">![醒目提示 [發行] 組建的 Visual Studio 工具列](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="04661-200">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="04661-201">在方案總管\*\*\*\* 中，以滑鼠右鍵按一下 **StringLibrary** 專案，然後從內容功能表中選取 [組建]\*\*\*\* 以重新編譯程式庫。</span><span class="sxs-lookup"><span data-stu-id="04661-201">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="04661-202">![StringLibrary 操作功能表和建置命令](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="04661-202">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="04661-203">從功能表列中選擇 [**測試**回合  >  **所有測試**]，以執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="04661-203">Run the unit tests by choosing **Test Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="04661-204">所有測試皆通過。</span><span class="sxs-lookup"><span data-stu-id="04661-204">The tests pass.</span></span>

## <a name="debug-tests"></a><span data-ttu-id="04661-205">偵錯測試</span><span class="sxs-lookup"><span data-stu-id="04661-205">Debug tests</span></span>

<span data-ttu-id="04661-206">如果您使用 Visual Studio 作為 IDE，您可以使用教學課程：使用您的單元測試專案來進行程式碼 [的偵錯工具](debugging-with-visual-studio.md) 中所示的相同程式：使用 Visual Studio 來偵錯工具代碼。</span><span class="sxs-lookup"><span data-stu-id="04661-206">If you're using Visual Studio as your IDE, you can use the same process shown in [Tutorial: Debug a .NET Core console application using Visual Studio](debugging-with-visual-studio.md) to debug code using your unit test project.</span></span> <span data-ttu-id="04661-207">請以滑鼠右鍵按一下**StringLibraryTests**專案，然後從內容功能表中選取 [ **Debug 測試**]，而不是啟動*展示*應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="04661-207">Instead of starting the *ShowCase* app project, right-click the **StringLibraryTests** project, and select **Debug Tests** from the context menu.</span></span>

<span data-ttu-id="04661-208">Visual Studio 啟動已附加偵錯工具的測試專案。</span><span class="sxs-lookup"><span data-stu-id="04661-208">Visual Studio starts the test project with the debugger attached.</span></span> <span data-ttu-id="04661-209">執行將會在您已新增至測試專案或基礎程式庫程式碼的任何中斷點停止執行。</span><span class="sxs-lookup"><span data-stu-id="04661-209">Execution will stop at any breakpoint you've added to the test project or the underlying library code.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="04661-210">其他資源</span><span class="sxs-lookup"><span data-stu-id="04661-210">Additional resources</span></span>

* [<span data-ttu-id="04661-211">單元測試基本概念-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="04661-211">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)
* [<span data-ttu-id="04661-212">.NET Core 與 .NET Standard 中的單元測試</span><span class="sxs-lookup"><span data-stu-id="04661-212">Unit testing in .NET Core and .NET Standard</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="04661-213">後續步驟</span><span class="sxs-lookup"><span data-stu-id="04661-213">Next steps</span></span>

<span data-ttu-id="04661-214">在本教學課程中，您已對類別庫進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="04661-214">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="04661-215">您可以將程式庫以套件的形式發佈至 [NuGet](https://nuget.org) ，以將程式庫提供給其他人使用。</span><span class="sxs-lookup"><span data-stu-id="04661-215">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="04661-216">若要深入瞭解，請遵循 NuGet 教學課程：</span><span class="sxs-lookup"><span data-stu-id="04661-216">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="04661-217">使用 Visual Studio 建立和發佈 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="04661-217">Create and publish a NuGet package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

<span data-ttu-id="04661-218">如果您將程式庫發佈為 NuGet 套件，其他人可以安裝和使用它。</span><span class="sxs-lookup"><span data-stu-id="04661-218">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="04661-219">若要深入瞭解，請遵循 NuGet 教學課程：</span><span class="sxs-lookup"><span data-stu-id="04661-219">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="04661-220">在 Visual Studio 中安裝並使用套件</span><span class="sxs-lookup"><span data-stu-id="04661-220">Install and use a package in Visual Studio</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

<span data-ttu-id="04661-221">程式庫不需要以套件的形式散發。</span><span class="sxs-lookup"><span data-stu-id="04661-221">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="04661-222">它可以與使用它的主控台應用程式配套。</span><span class="sxs-lookup"><span data-stu-id="04661-222">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="04661-223">若要瞭解如何發佈主控台應用程式，請參閱本系列的先前教學課程：</span><span class="sxs-lookup"><span data-stu-id="04661-223">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="04661-224">使用 Visual Studio 發佈 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="04661-224">Publish a .NET Core console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
