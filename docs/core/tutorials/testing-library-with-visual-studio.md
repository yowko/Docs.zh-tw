---
title: 使用 Visual Studio 測試 .NET 類別庫
description: 瞭解如何使用 Visual Studio 來建立和執行 .NET 類別庫的單元測試專案。
ms.date: 11/18/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 3d56627b937fa0ad5f8002f396ce617e09ce9d2c
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94916119"
---
# <a name="tutorial-test-a-net-class-library-with-net-using-visual-studio"></a><span data-ttu-id="987b1-103">教學課程：使用 Visual Studio 以 .NET 測試 .NET 類別庫</span><span class="sxs-lookup"><span data-stu-id="987b1-103">Tutorial: Test a .NET class library with .NET using Visual Studio</span></span>

<span data-ttu-id="987b1-104">本教學課程示範如何將測試專案加入至方案，以自動化單元測試。</span><span class="sxs-lookup"><span data-stu-id="987b1-104">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="987b1-105">先決條件</span><span class="sxs-lookup"><span data-stu-id="987b1-105">Prerequisites</span></span>

- <span data-ttu-id="987b1-106">本教學課程適用于 [使用 Visual Studio 建立 .net 類別庫](library-with-visual-studio.md)中所建立的方案。</span><span class="sxs-lookup"><span data-stu-id="987b1-106">This tutorial works with the solution that you create in [Create a .NET class library using Visual Studio](library-with-visual-studio.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="987b1-107">建立單元測試專案</span><span class="sxs-lookup"><span data-stu-id="987b1-107">Create a unit test project</span></span>

<span data-ttu-id="987b1-108">單元測試能在開發與發佈期間提供自動化的軟體測試。</span><span class="sxs-lookup"><span data-stu-id="987b1-108">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="987b1-109">[MSTest](https://github.com/Microsoft/testfx-docs) 是您可以從中選擇的三種測試架構之一。</span><span class="sxs-lookup"><span data-stu-id="987b1-109">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="987b1-110">其他則為 [xUnit](https://xunit.net/) 和 [nUnit](https://nunit.org/)。</span><span class="sxs-lookup"><span data-stu-id="987b1-110">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="987b1-111">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="987b1-111">Start Visual Studio.</span></span>

1. <span data-ttu-id="987b1-112">開啟 `ClassLibraryProjects` 您在 [使用 Visual Studio 建立 .net 類別庫](library-with-visual-studio.md)中建立的方案。</span><span class="sxs-lookup"><span data-stu-id="987b1-112">Open the `ClassLibraryProjects` solution you created in [Create a .NET class library using Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="987b1-113">將名為 "StringLibraryTest" 的新單元測試專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="987b1-113">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="987b1-114">以滑鼠右鍵按一下 **方案總管** 中的方案，然後選取 [**加入**  >  **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="987b1-114">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="987b1-115">在 [ **加入新的專案** ] 頁面上，于 [搜尋] 方塊中輸入 **mstest** 。</span><span class="sxs-lookup"><span data-stu-id="987b1-115">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="987b1-116">從 [語言] 清單中選擇 [ **c #** ] 或 [ **Visual Basic** ，然後從 [平臺] 清單中選擇 [ **所有平臺** ]。</span><span class="sxs-lookup"><span data-stu-id="987b1-116">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="987b1-117">選擇 [ **單元測試專案** ] 範本，然後選擇 [ **下一步]**。</span><span class="sxs-lookup"><span data-stu-id="987b1-117">Choose the **Unit Test Project** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="987b1-118">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入 **StringLibraryTest** 。</span><span class="sxs-lookup"><span data-stu-id="987b1-118">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="987b1-119">然後選擇 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="987b1-119">Then choose **Next**.</span></span>

   1. <span data-ttu-id="987b1-120">在 [**其他資訊**] 頁面上，選取 [**目標 Framework** ] 方塊中的 [ **.net 5.0 (目前)** 。</span><span class="sxs-lookup"><span data-stu-id="987b1-120">On the **Additional information** page, select **.NET 5.0 (Current)** in the **Target Framework** box.</span></span> <span data-ttu-id="987b1-121">接著，選擇 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="987b1-121">Then choose **Create**.</span></span>

1. <span data-ttu-id="987b1-122">Visual Studio 建立專案，並使用下列程式碼在程式碼視窗中開啟類別檔案。</span><span class="sxs-lookup"><span data-stu-id="987b1-122">Visual Studio creates the project and opens the class file in the code window with the following code.</span></span> <span data-ttu-id="987b1-123">如果未顯示您想要使用的語言，請變更頁面頂端的語言選取器。</span><span class="sxs-lookup"><span data-stu-id="987b1-123">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

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

   <span data-ttu-id="987b1-124">單元測試範本建立的原始程式碼會執行下列動作︰</span><span class="sxs-lookup"><span data-stu-id="987b1-124">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="987b1-125">它會匯入 <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 命名空間，其中包含用於單元測試的類型。</span><span class="sxs-lookup"><span data-stu-id="987b1-125">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="987b1-126">它會將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 屬性套用至 `UnitTest1` 類別。</span><span class="sxs-lookup"><span data-stu-id="987b1-126">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="987b1-127">它會套用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性，以 `TestMethod1` 在 c # 或 `TestSub` Visual Basic 中定義。</span><span class="sxs-lookup"><span data-stu-id="987b1-127">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic.</span></span>

   <span data-ttu-id="987b1-128">執行單元測試時，會自動執行在標記為[[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute)的測試類別中，以[[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute)標記的每個方法。</span><span class="sxs-lookup"><span data-stu-id="987b1-128">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="987b1-129">新增專案參考</span><span class="sxs-lookup"><span data-stu-id="987b1-129">Add a project reference</span></span>

<span data-ttu-id="987b1-130">若要讓測試專案使用 `StringLibrary` 類別，請在 **StringLibraryTest** 專案中加入專案的參考 `StringLibrary` 。</span><span class="sxs-lookup"><span data-stu-id="987b1-130">For the test project to work with the `StringLibrary` class, add a reference in the **StringLibraryTest** project to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="987b1-131">在 **方案總管** 中，以滑鼠右鍵按一下 **StringLibraryTest** 專案的 [相依性] 節點，然後從內容功能表中選取 [**加入專案參考** **]** 。</span><span class="sxs-lookup"><span data-stu-id="987b1-131">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Project Reference** from the context menu.</span></span>

1. <span data-ttu-id="987b1-132">在 [ **參考管理員** ] 對話方塊中，展開 [ **專案** ] 節點，然後選取 [ **StringLibrary**] 旁的方塊。</span><span class="sxs-lookup"><span data-stu-id="987b1-132">In the **Reference Manager** dialog, expand the **Projects** node, and select the box next to **StringLibrary**.</span></span> <span data-ttu-id="987b1-133">加入元件的參考，可讓編譯器在 `StringLibrary` 編譯 **StringLibraryTest** 專案時尋找 **StringLibrary** 方法。</span><span class="sxs-lookup"><span data-stu-id="987b1-133">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods while compiling the **StringLibraryTest** project.</span></span>

1. <span data-ttu-id="987b1-134">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="987b1-134">Select **OK**.</span></span>

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="987b1-135">加入並執行單元測試方法</span><span class="sxs-lookup"><span data-stu-id="987b1-135">Add and run unit test methods</span></span>

<span data-ttu-id="987b1-136">當 Visual Studio 執行單元測試時，它會執行每個以屬性標記之 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 類別中的屬性標記的方法  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="987b1-136">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="987b1-137">當找到第一個失敗或方法中包含的所有測試都成功時，測試方法便會結束。</span><span class="sxs-lookup"><span data-stu-id="987b1-137">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="987b1-138">最常見的測試會呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 類別的成員。</span><span class="sxs-lookup"><span data-stu-id="987b1-138">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="987b1-139">許多判斷提示方法都至少包括兩個參數，一個是預期的測試結果，另一個是實際的測試結果。</span><span class="sxs-lookup"><span data-stu-id="987b1-139">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="987b1-140">`Assert`下表顯示某些類別最常呼叫的方法：</span><span class="sxs-lookup"><span data-stu-id="987b1-140">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="987b1-141">Assert 方法</span><span class="sxs-lookup"><span data-stu-id="987b1-141">Assert methods</span></span>     | <span data-ttu-id="987b1-142">函式</span><span class="sxs-lookup"><span data-stu-id="987b1-142">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="987b1-143">驗證兩個值或物件相等。</span><span class="sxs-lookup"><span data-stu-id="987b1-143">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="987b1-144">如果值或物件不相等，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="987b1-144">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="987b1-145">驗證兩個物件變數參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="987b1-145">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="987b1-146">如果變數參考不同的物件，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="987b1-146">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="987b1-147">驗證條件為 `false`。</span><span class="sxs-lookup"><span data-stu-id="987b1-147">Verifies that a condition is `false`.</span></span> <span data-ttu-id="987b1-148">如果條件為 `true`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="987b1-148">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="987b1-149">確認物件不是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="987b1-149">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="987b1-150">如果物件為 `null`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="987b1-150">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="987b1-151">您也可以 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> 在測試方法中使用方法，來指出預期會擲回的例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="987b1-151">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="987b1-152">如果未擲回指定的例外狀況，測試便會失敗。</span><span class="sxs-lookup"><span data-stu-id="987b1-152">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="987b1-153">在測試 `StringLibrary.StartsWithUpper` 方法時，您想提供幾個以大寫字元開頭的字串。</span><span class="sxs-lookup"><span data-stu-id="987b1-153">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="987b1-154">您預期此方法在這些情況下傳回 `true`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="987b1-154">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="987b1-155">同樣地，您想提供幾個開頭不是大寫字元的字串。</span><span class="sxs-lookup"><span data-stu-id="987b1-155">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="987b1-156">您預期此方法在這些情況下傳回 `false`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="987b1-156">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="987b1-157">因為您的程式庫方法會處理字串，您也想要確保它能成功處理 [空字串 (`String.Empty`) ](xref:System.String.Empty)、沒有任何字元且其為0的有效字串 <xref:System.String.Length> ，以及 `null` 尚未初始化的字串。</span><span class="sxs-lookup"><span data-stu-id="987b1-157">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="987b1-158">您可以 `StartsWithUpper` 直接呼叫作為靜態方法，並傳遞單一 <xref:System.String> 引數。</span><span class="sxs-lookup"><span data-stu-id="987b1-158">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="987b1-159">或者，您可以 `StartsWithUpper` 在指派給的變數上呼叫做為擴充方法 `string` `null` 。</span><span class="sxs-lookup"><span data-stu-id="987b1-159">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="987b1-160">您會定義三個方法，每個方法會 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 針對字串陣列中的每個元素呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="987b1-160">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="987b1-161">您將呼叫方法多載，讓您指定在測試失敗時所要顯示的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="987b1-161">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="987b1-162">訊息會識別造成失敗的字串。</span><span class="sxs-lookup"><span data-stu-id="987b1-162">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="987b1-163">建立測試方法：</span><span class="sxs-lookup"><span data-stu-id="987b1-163">To create the test methods:</span></span>

1. <span data-ttu-id="987b1-164">在 [ *UnitTest1.cs* ] 或 [ *UnitTest1* ] 程式碼視窗中，將程式碼取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="987b1-164">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibraryTest/UnitTest1.vb":::

   <span data-ttu-id="987b1-165">方法中的大寫字元測試 `TestStartsWithUpper` 包含希臘文大寫字母 Alpha (u + 0391) 和斯拉夫文大寫字母 EM (U + 041C) 。</span><span class="sxs-lookup"><span data-stu-id="987b1-165">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="987b1-166">方法中的小寫字元測試 `TestDoesNotStartWithUpper` 包含希臘文小寫字母 Alpha (u + 03B1) 和斯拉夫文小寫字母 Ghe (U + 0433) 。</span><span class="sxs-lookup"><span data-stu-id="987b1-166">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="987b1-167">在功能表列上，選取 [ **file**  >  **save UnitTest1.cs as** ] 或 [ **file**  >  **save UnitTest1**]。</span><span class="sxs-lookup"><span data-stu-id="987b1-167">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="987b1-168">在 [另存新檔] 對話方塊中，選取 [儲存] 按鈕旁的箭號，然後選取 [以編碼方式儲存]\*。</span><span class="sxs-lookup"><span data-stu-id="987b1-168">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/save-file-as-dialog.png" alt-text="Visual Studio 另存新檔] 對話方塊":::

1. <span data-ttu-id="987b1-170">在 [確認另存新檔] 對話方塊中，選取 [是] 按鈕以儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="987b1-170">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="987b1-171">在 [進階儲存選項] 對話方塊中，選取 [編碼] 下拉式清單中的 [Unicode (UTF-8 有簽章) - 字碼頁 65001]，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="987b1-171">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/advanced-save-options.png" alt-text="Visual Studio [進階儲存選項] 對話方塊":::

   <span data-ttu-id="987b1-173">如果您無法將您的原始程式碼儲存為 UTF8 編碼檔案，Visual Studio 可能會將它儲存為 ASCII 檔案。</span><span class="sxs-lookup"><span data-stu-id="987b1-173">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="987b1-174">當這種情況發生時，執行時間不會正確地解碼 ASCII 範圍以外的 UTF8 字元，而且測試結果將會不正確。</span><span class="sxs-lookup"><span data-stu-id="987b1-174">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="987b1-175">在功能表列上，選取 [**測試**  >  **執行所有測試**]。</span><span class="sxs-lookup"><span data-stu-id="987b1-175">On the menu bar, select **Test** > **Run All Tests**.</span></span> <span data-ttu-id="987b1-176">如果 [**測試瀏覽器**] 視窗未開啟，請選擇 [**測試**  >  **測試瀏覽器**] 將它開啟。</span><span class="sxs-lookup"><span data-stu-id="987b1-176">If the **Test Explorer** window doesn't open, open it by choosing **Test** > **Test Explorer**.</span></span> <span data-ttu-id="987b1-177">這三項測試都會列在 [通過的測試] 區段中，而 [摘要] 區段則報告測試回合的結果。</span><span class="sxs-lookup"><span data-stu-id="987b1-177">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/test-explorer-window.png" alt-text="測試總管視窗，其中包含通過的測試":::

## <a name="handle-test-failures"></a><span data-ttu-id="987b1-179">處理測試失敗</span><span class="sxs-lookup"><span data-stu-id="987b1-179">Handle test failures</span></span>

<span data-ttu-id="987b1-180">如果您正在執行以測試為導向的開發 (TDD) ，您會先撰寫測試，並在您第一次執行時失敗。</span><span class="sxs-lookup"><span data-stu-id="987b1-180">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="987b1-181">然後，將程式碼新增至應用程式，讓測試成功。</span><span class="sxs-lookup"><span data-stu-id="987b1-181">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="987b1-182">在本教學課程中，您已在撰寫應用程式程式碼驗證之後建立測試，因此您未看到測試失敗。</span><span class="sxs-lookup"><span data-stu-id="987b1-182">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="987b1-183">若要在預期測試失敗時驗證測試失敗，請將不正確值加入測試輸入。</span><span class="sxs-lookup"><span data-stu-id="987b1-183">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="987b1-184">修改 `TestDoesNotStartWithUpper` 方法中的 `words` 陣列，以包含字串「錯誤」。</span><span class="sxs-lookup"><span data-stu-id="987b1-184">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="987b1-185">您不需要儲存檔案，因為當組建方案以執行測試時，Visual Studio 會自動儲存開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="987b1-185">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="987b1-186">從功能表列選取 [**測試** 回合  >  **所有測試**] 以執行測試。</span><span class="sxs-lookup"><span data-stu-id="987b1-186">Run the test by selecting **Test** > **Run All Tests** from the menu bar.</span></span> <span data-ttu-id="987b1-187">[測試總管] 視窗表示兩個測試成功，而且有一項失敗。</span><span class="sxs-lookup"><span data-stu-id="987b1-187">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/failed-test-window.png" alt-text="測試總管視窗，其中包含失敗的測試":::

1. <span data-ttu-id="987b1-189">選取失敗的測試 `TestDoesNotStartWith` 。</span><span class="sxs-lookup"><span data-stu-id="987b1-189">Select the failed test, `TestDoesNotStartWith`.</span></span>

   <span data-ttu-id="987b1-190">**[測試總管]** 下方的窗格會顯示判斷提示產生的訊息：「Assert.IsFalse 失敗。</span><span class="sxs-lookup"><span data-stu-id="987b1-190">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="987b1-191">'Error' 的預期︰false；實際：True」。</span><span class="sxs-lookup"><span data-stu-id="987b1-191">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="987b1-192">因為失敗，所以在測試 "Error" 之後，陣列中沒有任何字串。</span><span class="sxs-lookup"><span data-stu-id="987b1-192">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/failed-test-detail.png" alt-text="顯示 IsFalse 判斷提示失敗的 Test Explorer 視窗":::

1. <span data-ttu-id="987b1-194">移除您在步驟1中新增的字串 "Error"。</span><span class="sxs-lookup"><span data-stu-id="987b1-194">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="987b1-195">重新執行測試和測試階段。</span><span class="sxs-lookup"><span data-stu-id="987b1-195">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="987b1-196">測試程式庫的發行版本</span><span class="sxs-lookup"><span data-stu-id="987b1-196">Test the Release version of the library</span></span>

<span data-ttu-id="987b1-197">現在，在執行程式庫的偵錯工具時，所有測試都已通過，請針對程式庫的發行組建執行額外的測試。</span><span class="sxs-lookup"><span data-stu-id="987b1-197">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="987b1-198">許多因素 (包括編譯器最佳化) 有時會在偵錯和發行組建之間導致不同的行為。</span><span class="sxs-lookup"><span data-stu-id="987b1-198">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="987b1-199">測試發行組建︰</span><span class="sxs-lookup"><span data-stu-id="987b1-199">To test the Release build:</span></span>

1. <span data-ttu-id="987b1-200">在 Visual Studio 工具列中，將組建組態從 [偵錯] 變更為 [發行]。</span><span class="sxs-lookup"><span data-stu-id="987b1-200">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png" alt-text="醒目提示 [發行] 組建的 Visual Studio 工具列":::

1. <span data-ttu-id="987b1-202">在方案總管 中，以滑鼠右鍵按一下 **StringLibrary** 專案，然後從內容功能表中選取 [組建] 以重新編譯程式庫。</span><span class="sxs-lookup"><span data-stu-id="987b1-202">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="./media/testing-library-with-visual-studio/build-library-context-menu.png" alt-text="StringLibrary 操作功能表和建置命令":::

1. <span data-ttu-id="987b1-204">從功能表列中選擇 [**測試** 回合  >  **所有測試**]，以執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="987b1-204">Run the unit tests by choosing **Test Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="987b1-205">所有測試皆通過。</span><span class="sxs-lookup"><span data-stu-id="987b1-205">The tests pass.</span></span>

## <a name="debug-tests"></a><span data-ttu-id="987b1-206">偵錯測試</span><span class="sxs-lookup"><span data-stu-id="987b1-206">Debug tests</span></span>

<span data-ttu-id="987b1-207">如果您使用 Visual Studio 作為 IDE，您可以使用教學課程：使用您的單元測試專案來進行程式碼 [的偵錯工具](debugging-with-visual-studio.md) 中所示的相同程式：使用 Visual Studio 來對程式碼進行程式碼處理。</span><span class="sxs-lookup"><span data-stu-id="987b1-207">If you're using Visual Studio as your IDE, you can use the same process shown in [Tutorial: Debug a .NET console application using Visual Studio](debugging-with-visual-studio.md) to debug code using your unit test project.</span></span> <span data-ttu-id="987b1-208">請以滑鼠右鍵按一下 **StringLibraryTests** 專案，然後從內容功能表中選取 [ **Debug 測試**]，而不是啟動 *展示* 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="987b1-208">Instead of starting the *ShowCase* app project, right-click the **StringLibraryTests** project, and select **Debug Tests** from the context menu.</span></span>

<span data-ttu-id="987b1-209">Visual Studio 啟動已附加偵錯工具的測試專案。</span><span class="sxs-lookup"><span data-stu-id="987b1-209">Visual Studio starts the test project with the debugger attached.</span></span> <span data-ttu-id="987b1-210">執行將會在您已新增至測試專案或基礎程式庫程式碼的任何中斷點停止執行。</span><span class="sxs-lookup"><span data-stu-id="987b1-210">Execution will stop at any breakpoint you've added to the test project or the underlying library code.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="987b1-211">其他資源</span><span class="sxs-lookup"><span data-stu-id="987b1-211">Additional resources</span></span>

* [<span data-ttu-id="987b1-212">單元測試基本概念-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="987b1-212">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)
* [<span data-ttu-id="987b1-213">.NET 中的單元測試</span><span class="sxs-lookup"><span data-stu-id="987b1-213">Unit testing in .NET</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="987b1-214">後續步驟</span><span class="sxs-lookup"><span data-stu-id="987b1-214">Next steps</span></span>

<span data-ttu-id="987b1-215">在本教學課程中，您已對類別庫進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="987b1-215">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="987b1-216">您可以將程式庫以套件的形式發佈至 [NuGet](https://nuget.org) ，以將程式庫提供給其他人使用。</span><span class="sxs-lookup"><span data-stu-id="987b1-216">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="987b1-217">若要深入瞭解，請遵循 NuGet 教學課程：</span><span class="sxs-lookup"><span data-stu-id="987b1-217">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="987b1-218">使用 Visual Studio 建立和發佈 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="987b1-218">Create and publish a NuGet package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

<span data-ttu-id="987b1-219">如果您將程式庫發佈為 NuGet 套件，其他人可以安裝和使用它。</span><span class="sxs-lookup"><span data-stu-id="987b1-219">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="987b1-220">若要深入瞭解，請遵循 NuGet 教學課程：</span><span class="sxs-lookup"><span data-stu-id="987b1-220">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="987b1-221">在 Visual Studio 中安裝並使用套件</span><span class="sxs-lookup"><span data-stu-id="987b1-221">Install and use a package in Visual Studio</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

<span data-ttu-id="987b1-222">程式庫不需要以套件的形式散發。</span><span class="sxs-lookup"><span data-stu-id="987b1-222">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="987b1-223">它可以與使用它的主控台應用程式配套。</span><span class="sxs-lookup"><span data-stu-id="987b1-223">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="987b1-224">若要瞭解如何發佈主控台應用程式，請參閱本系列的先前教學課程：</span><span class="sxs-lookup"><span data-stu-id="987b1-224">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="987b1-225">使用 Visual Studio 發佈 .NET 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="987b1-225">Publish a .NET console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
