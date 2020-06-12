---
title: 使用 Visual Studio for Mac 測試具有 .NET Core 的 .NET Standard 類別庫
description: 建立 .NET Core 類別庫的單元測試專案。 確認 .NET Core 類別庫可在單元測試中正常運作。
ms.date: 06/08/2020
ms.openlocfilehash: a183049623df44cbb8c4abd47ce6e78d91adae12
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84713606"
---
# <a name="test-a-net-standard-class-library-with-net-core-using-visual-studio"></a><span data-ttu-id="20de8-104">使用 Visual Studio 測試具有 .NET Core 的 .NET Standard 類別庫</span><span class="sxs-lookup"><span data-stu-id="20de8-104">Test a .NET Standard class library with .NET Core using Visual Studio</span></span>

<span data-ttu-id="20de8-105">本教學課程說明如何藉由將測試專案加入至方案，來自動化單元測試。</span><span class="sxs-lookup"><span data-stu-id="20de8-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="20de8-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="20de8-106">Prerequisites</span></span>

- <span data-ttu-id="20de8-107">本教學課程適用于您在[Visual Studio for Mac 中建立 .NET Standard 程式庫](library-with-visual-studio-mac.md)中建立的解決方案。</span><span class="sxs-lookup"><span data-stu-id="20de8-107">This tutorial works with the solution that you create in [Create a .NET Standard library in Visual Studio for Mac](library-with-visual-studio-mac.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="20de8-108">建立單元測試專案</span><span class="sxs-lookup"><span data-stu-id="20de8-108">Create a unit test project</span></span>

<span data-ttu-id="20de8-109">單元測試能在開發與發佈期間提供自動化的軟體測試。</span><span class="sxs-lookup"><span data-stu-id="20de8-109">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="20de8-110">[MSTest](https://github.com/Microsoft/testfx-docs)是您可以從中選擇的三種測試架構之一。</span><span class="sxs-lookup"><span data-stu-id="20de8-110">[MSTest](https://github.com/Microsoft/testfx-docs) is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="20de8-111">其他則是[xUnit](https://xunit.net/)和[nUnit](https://nunit.org/)。</span><span class="sxs-lookup"><span data-stu-id="20de8-111">The others are [xUnit](https://xunit.net/) and [nUnit](https://nunit.org/).</span></span>

1. <span data-ttu-id="20de8-112">啟動 Visual Studio for Mac。</span><span class="sxs-lookup"><span data-stu-id="20de8-112">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="20de8-113">開啟 `ClassLibraryProjects` 您在[Visual Studio for Mac 中建立 .NET Standard 程式庫](library-with-visual-studio-mac.md)中建立的解決方案。</span><span class="sxs-lookup"><span data-stu-id="20de8-113">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library in Visual Studio for Mac](library-with-visual-studio-mac.md).</span></span>

1. <span data-ttu-id="20de8-114">在**solution** pad 中，以<kbd>ctrl</kbd>-按一下 `ClassLibraryProjects` 方案，然後**Add**選取 [  >  **新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="20de8-114">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="20de8-115">在 [**新增專案**] 對話方塊中，從 [ **Web] 和 [主控台**] 節點選取 [**測試**]。</span><span class="sxs-lookup"><span data-stu-id="20de8-115">In the **New Project** dialog, select **Tests** from the **Web and Console** node.</span></span> <span data-ttu-id="20de8-116">選取**MSTest 專案**，後面接著 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="20de8-116">Select the **MSTest Project** followed by **Next**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-project.png" alt-text="Visual Studio Mac 新增專案] 對話方塊建立測試專案":::

1. <span data-ttu-id="20de8-118">選取 [ **.Net Core 3.1**]。</span><span class="sxs-lookup"><span data-stu-id="20de8-118">Select **.NET Core 3.1**.</span></span> <span data-ttu-id="20de8-119">將新專案命名為 "StringLibraryTest"，然後選取 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="20de8-119">Name the new project "StringLibraryTest" and select **Create**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-new-project-name.png" alt-text="提供專案名稱的 Visual Studio Mac [新增專案] 對話方塊":::

   <span data-ttu-id="20de8-121">Visual Studio 會使用下列程式碼建立類別檔案：</span><span class="sxs-lookup"><span data-stu-id="20de8-121">Visual Studio creates a class file with the following code:</span></span>

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

   <span data-ttu-id="20de8-122">單元測試範本建立的原始程式碼會執行下列動作︰</span><span class="sxs-lookup"><span data-stu-id="20de8-122">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="20de8-123">它會匯入 <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 命名空間，其中包含用於單元測試的類型。</span><span class="sxs-lookup"><span data-stu-id="20de8-123">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="20de8-124">它會將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 屬性套用至 `UnitTest1` 類別。</span><span class="sxs-lookup"><span data-stu-id="20de8-124">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="20de8-125">它會將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性套用至 `TestMethod1` 。</span><span class="sxs-lookup"><span data-stu-id="20de8-125">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to `TestMethod1`.</span></span>

   <span data-ttu-id="20de8-126">執行單元測試時，會自動執行在標記為[[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute)的測試類別中，以[[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute)標記的每個方法。</span><span class="sxs-lookup"><span data-stu-id="20de8-126">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="20de8-127">新增專案參考</span><span class="sxs-lookup"><span data-stu-id="20de8-127">Add a project reference</span></span>

<span data-ttu-id="20de8-128">若要讓測試專案與類別搭配使用 `StringLibrary` ，請加入專案的參考 `StringLibrary` 。</span><span class="sxs-lookup"><span data-stu-id="20de8-128">For the test project to work with the `StringLibrary` class, add a reference to the `StringLibrary` project.</span></span>

1. <span data-ttu-id="20de8-129">在 [ **Solution** pad] 中，按<kbd>ctrl</kbd>-按一下 [ **StringLibraryTest**] 底下的 [**相關性]** 。</span><span class="sxs-lookup"><span data-stu-id="20de8-129">In the **Solution** pad, <kbd>ctrl</kbd>-click **Dependencies** under **StringLibraryTest**.</span></span> <span data-ttu-id="20de8-130">從內容功能表中選取 [**新增參考**]。</span><span class="sxs-lookup"><span data-stu-id="20de8-130">Select **Add Reference** from the context menu.</span></span>

1. <span data-ttu-id="20de8-131">在 [**參考**] 對話方塊中，選取 [ **StringLibrary** ] 專案。</span><span class="sxs-lookup"><span data-stu-id="20de8-131">In the **References** dialog, select the **StringLibrary** project.</span></span> <span data-ttu-id="20de8-132">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="20de8-132">Select **OK**.</span></span>

      :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-edit-references.png" alt-text="Visual Studio Mac [編輯參考] 對話方塊":::

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="20de8-134">新增和執行單元測試方法</span><span class="sxs-lookup"><span data-stu-id="20de8-134">Add and run unit test methods</span></span>

<span data-ttu-id="20de8-135">當 Visual Studio 執行單元測試時，它會在以屬性標記的類別中，執行以屬性標記的每個方法 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="20de8-135">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="20de8-136">測試方法會在發現第一個失敗或方法中包含的所有測試都成功時結束。</span><span class="sxs-lookup"><span data-stu-id="20de8-136">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="20de8-137">最常見的測試會呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 類別的成員。</span><span class="sxs-lookup"><span data-stu-id="20de8-137">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="20de8-138">許多判斷提示方法都至少包括兩個參數，一個是預期的測試結果，另一個是實際的測試結果。</span><span class="sxs-lookup"><span data-stu-id="20de8-138">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="20de8-139">`Assert`下表顯示一些類別最常被呼叫的方法：</span><span class="sxs-lookup"><span data-stu-id="20de8-139">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="20de8-140">Assert 方法</span><span class="sxs-lookup"><span data-stu-id="20de8-140">Assert methods</span></span>     | <span data-ttu-id="20de8-141">函式</span><span class="sxs-lookup"><span data-stu-id="20de8-141">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="20de8-142">驗證兩個值或物件相等。</span><span class="sxs-lookup"><span data-stu-id="20de8-142">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="20de8-143">如果值或物件不相等，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="20de8-143">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="20de8-144">驗證兩個物件變數參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="20de8-144">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="20de8-145">如果變數參考不同的物件，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="20de8-145">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="20de8-146">驗證條件為 `false`。</span><span class="sxs-lookup"><span data-stu-id="20de8-146">Verifies that a condition is `false`.</span></span> <span data-ttu-id="20de8-147">如果條件為 `true`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="20de8-147">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="20de8-148">驗證物件不是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="20de8-148">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="20de8-149">如果物件為 `null`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="20de8-149">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="20de8-150">您也可以 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> 在測試方法中使用方法，以指出預期會擲回的例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="20de8-150">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="20de8-151">如果未擲回指定的例外狀況，測試將會失敗。</span><span class="sxs-lookup"><span data-stu-id="20de8-151">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="20de8-152">在測試 `StringLibrary.StartsWithUpper` 方法時，您想提供幾個以大寫字元開頭的字串。</span><span class="sxs-lookup"><span data-stu-id="20de8-152">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="20de8-153">您預期此方法在這些情況下傳回 `true`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="20de8-153">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="20de8-154">同樣地，您想提供幾個開頭不是大寫字元的字串。</span><span class="sxs-lookup"><span data-stu-id="20de8-154">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="20de8-155">您預期此方法在這些情況下傳回 `false`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="20de8-155">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="20de8-156">由於您的程式庫方法會處理字串，因此您也會想要確定它會成功處理[空字串（ `String.Empty` ）](xref:System.String.Empty)、沒有任何字元的有效字串，以及 <xref:System.String.Length> 未初始化的 `null` 字串。</span><span class="sxs-lookup"><span data-stu-id="20de8-156">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="20de8-157">您可以 `StartsWithUpper` 直接呼叫做為靜態方法，並傳遞單一 <xref:System.String> 引數。</span><span class="sxs-lookup"><span data-stu-id="20de8-157">You can call `StartsWithUpper` directly as a static method and pass a single <xref:System.String> argument.</span></span> <span data-ttu-id="20de8-158">或者，您可以 `StartsWithUpper` 在指派給的變數上呼叫作為擴充方法 `string` `null` 。</span><span class="sxs-lookup"><span data-stu-id="20de8-158">Or you can call `StartsWithUpper` as an extension method on a `string` variable assigned to `null`.</span></span>

<span data-ttu-id="20de8-159">您將定義三個方法，每個方法都會 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 針對字串陣列中的每個元素呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="20de8-159">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method for each element in a string array.</span></span> <span data-ttu-id="20de8-160">您將呼叫方法多載，讓您指定要在測試失敗時顯示的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="20de8-160">You'll call a method overload that lets you specify an error message to be displayed in case of test failure.</span></span> <span data-ttu-id="20de8-161">訊息會識別造成失敗的字串。</span><span class="sxs-lookup"><span data-stu-id="20de8-161">The message identifies the string that caused the failure.</span></span>

<span data-ttu-id="20de8-162">建立測試方法：</span><span class="sxs-lookup"><span data-stu-id="20de8-162">To create the test methods:</span></span>

1. <span data-ttu-id="20de8-163">開啟*UnitTest1.cs*檔案，並以下列程式碼取代程式碼：</span><span class="sxs-lookup"><span data-stu-id="20de8-163">Open the *UnitTest1.cs* file and replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::

   <span data-ttu-id="20de8-164">方法中的大寫字元測試 `TestStartsWithUpper` 包含希臘文大寫字母 Alpha （u + 0391）和斯拉夫文大寫字母 EM （u + 041C）。</span><span class="sxs-lookup"><span data-stu-id="20de8-164">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="20de8-165">方法中的小寫字元測試 `TestDoesNotStartWithUpper` 包含希臘文小寫字母 Alpha （u + 03B1）和斯拉夫文小寫字母 Ghe （u + 0433）。</span><span class="sxs-lookup"><span data-stu-id="20de8-165">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="20de8-166">在功能表列上 **，選取 [** 檔案] [  >  **另存**新檔]。</span><span class="sxs-lookup"><span data-stu-id="20de8-166">On the menu bar, select **File** > **Save As**.</span></span> <span data-ttu-id="20de8-167">在對話方塊中，請確定 [**編碼**] 設定為 **[Unicode （utf-8）**]。</span><span class="sxs-lookup"><span data-stu-id="20de8-167">In the dialog, make sure that **Encoding** is set to **Unicode (UTF-8)**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/save-file-as-dialog.png" alt-text="Visual Studio 另存新檔] 對話方塊":::

1. <span data-ttu-id="20de8-169">當系統詢問您是否要取代現有的檔案時，請選取 [**取代**]。</span><span class="sxs-lookup"><span data-stu-id="20de8-169">When you're asked if you want to replace the existing file, select **Replace**.</span></span>

   <span data-ttu-id="20de8-170">如果您無法將您的原始程式碼儲存為 UTF8 編碼檔案，Visual Studio 可能會將它儲存為 ASCII 檔案。</span><span class="sxs-lookup"><span data-stu-id="20de8-170">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="20de8-171">發生這種情況時，執行時間不會正確地解碼 ASCII 範圍以外的 UTF8 字元，而且測試結果將會不正確。</span><span class="sxs-lookup"><span data-stu-id="20de8-171">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="20de8-172">開啟螢幕右側的 [單元測試]\*\*\*\* 面板。</span><span class="sxs-lookup"><span data-stu-id="20de8-172">Open the **Unit Tests** panel on the right side of the screen.</span></span> <span data-ttu-id="20de8-173">**View**  >  從功能表中選取 [View**測試**]。</span><span class="sxs-lookup"><span data-stu-id="20de8-173">Select **View** > **Tests** from the menu.</span></span>

1. <span data-ttu-id="20de8-174">按一下**固定**圖示維持面板開啟。</span><span class="sxs-lookup"><span data-stu-id="20de8-174">Click the **Dock** icon to keep the panel open.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-dock-icon.png" alt-text="Visual Studio for Mac [單元測試] 面板固定圖示":::

1. <span data-ttu-id="20de8-176">按一下 [全部執行]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="20de8-176">Click the **Run All** button.</span></span>

   <span data-ttu-id="20de8-177">所有測試皆通過。</span><span class="sxs-lookup"><span data-stu-id="20de8-177">All tests pass.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-pass.png" alt-text="Visual Studio for Mac 預期的測試階段":::

## <a name="handle-test-failures"></a><span data-ttu-id="20de8-179">處理測試失敗</span><span class="sxs-lookup"><span data-stu-id="20de8-179">Handle test failures</span></span>

<span data-ttu-id="20de8-180">如果您執行的是測試導向開發（TDD），您必須先撰寫測試，而且第一次執行時才會失敗。</span><span class="sxs-lookup"><span data-stu-id="20de8-180">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="20de8-181">接著，您可以將程式碼新增至應用程式，讓測試成功。</span><span class="sxs-lookup"><span data-stu-id="20de8-181">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="20de8-182">在本教學課程中，您已在撰寫應用程式驗證碼之後建立測試，因此您未看到測試失敗。</span><span class="sxs-lookup"><span data-stu-id="20de8-182">For this tutorial, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="20de8-183">若要驗證測試在預期失敗時失敗，請在測試輸入中加入不正確值。</span><span class="sxs-lookup"><span data-stu-id="20de8-183">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="20de8-184">修改 `TestDoesNotStartWithUpper` 方法中的 `words` 陣列，以包含字串「錯誤」。</span><span class="sxs-lookup"><span data-stu-id="20de8-184">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="20de8-185">您不需要儲存檔案，因為當組建方案以執行測試時，Visual Studio 會自動儲存開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="20de8-185">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. <span data-ttu-id="20de8-186">再次執行測試。</span><span class="sxs-lookup"><span data-stu-id="20de8-186">Run the tests again.</span></span>

   <span data-ttu-id="20de8-187">這次，[**測試瀏覽器**] 視窗會指出兩個測試成功，其中一個失敗。</span><span class="sxs-lookup"><span data-stu-id="20de8-187">This time, the **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/failed-test-window.png" alt-text="測試總管視窗，其中包含失敗的測試":::

1. <span data-ttu-id="20de8-189">以<kbd>ctrl</kbd>-按一下失敗的測試， `TestDoesNotStartWithUpper` 然後從內容功能表中選取 [**顯示結果 Pad** ]。</span><span class="sxs-lookup"><span data-stu-id="20de8-189"><kbd>ctrl</kbd>-click the failed test, `TestDoesNotStartWithUpper`, and select **Show Results Pad** from the context menu.</span></span>

   <span data-ttu-id="20de8-190">[**結果**] 面板會顯示判斷提示所產生的訊息：「IsFalse 失敗。</span><span class="sxs-lookup"><span data-stu-id="20de8-190">The **Results** pad displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="20de8-191">'Error' 的預期︰false；實際：True」。</span><span class="sxs-lookup"><span data-stu-id="20de8-191">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="20de8-192">由於失敗，因此在測試「錯誤」之後，陣列中沒有任何字串。</span><span class="sxs-lookup"><span data-stu-id="20de8-192">Because of the failure, no strings in the array after "Error" were tested.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-mac-unit-test-failure.png" alt-text="顯示 IsFalse 判斷提示失敗的測試 Explorer 視窗":::

1. <span data-ttu-id="20de8-194">移除您在步驟1中新增的字串 "Error"。</span><span class="sxs-lookup"><span data-stu-id="20de8-194">Remove the string "Error" that you added in step 1.</span></span> <span data-ttu-id="20de8-195">重新執行測試和測試階段。</span><span class="sxs-lookup"><span data-stu-id="20de8-195">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="20de8-196">測試程式庫的發行版本</span><span class="sxs-lookup"><span data-stu-id="20de8-196">Test the Release version of the library</span></span>

<span data-ttu-id="20de8-197">現在，在執行程式庫的「偵錯工具」組建時，所有測試都已成功，請針對程式庫的發行組建，再次執行測試。</span><span class="sxs-lookup"><span data-stu-id="20de8-197">Now that the tests have all passed when running the Debug build of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="20de8-198">許多因素 (包括編譯器最佳化) 有時會在偵錯和發行組建之間導致不同的行為。</span><span class="sxs-lookup"><span data-stu-id="20de8-198">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="20de8-199">測試發行組建︰</span><span class="sxs-lookup"><span data-stu-id="20de8-199">To test the Release build:</span></span>

1. <span data-ttu-id="20de8-200">在 Visual Studio 工具列中，將組建組態從 [偵錯]\*\*\*\* 變更為 [發行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="20de8-200">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/visual-studio-toolbar-release.png" alt-text="醒目提示 [發行] 組建的 Visual Studio 工具列":::

1. <span data-ttu-id="20de8-202">在**Solution** pad 中，以<kbd>ctrl</kbd>-按一下 [ **StringLibrary** ] 專案，然後從內容功能表中選取 [**組建**]，以重新編譯程式庫。</span><span class="sxs-lookup"><span data-stu-id="20de8-202">In the **Solution** pad, <kbd>ctrl</kbd>-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   :::image type="content" source="media/testing-library-with-visual-studio-mac/build-library-context-menu.png" alt-text="StringLibrary 操作功能表和建置命令":::

1. <span data-ttu-id="20de8-204">再次執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="20de8-204">Run the unit tests again.</span></span>

   <span data-ttu-id="20de8-205">所有測試皆通過。</span><span class="sxs-lookup"><span data-stu-id="20de8-205">The tests pass.</span></span>

## <a name="debug-tests"></a><span data-ttu-id="20de8-206">偵錯測試</span><span class="sxs-lookup"><span data-stu-id="20de8-206">Debug tests</span></span>

<span data-ttu-id="20de8-207">您可以使用教學課程：使用 Visual Studio for Mac 來偵測[.Net Core 主控台應用程式](debugging-with-visual-studio-mac.md)中所示的相同進程，以使用您的單元測試專案來進行程式碼的 debug。</span><span class="sxs-lookup"><span data-stu-id="20de8-207">You can use the same process shown in [Tutorial: Debug a .NET Core console application using Visual Studio for Mac](debugging-with-visual-studio-mac.md) to debug code using your unit test project.</span></span> <span data-ttu-id="20de8-208">不要啟動展示應用程式專案，請以<kbd>ctrl</kbd>-按一下**StringLibraryTests**專案，然後從內容功能表中選取 [**開始調試專案**]。</span><span class="sxs-lookup"><span data-stu-id="20de8-208">Instead of starting the ShowCase app project, <kbd>ctrl</kbd>-click the **StringLibraryTests** project, and select **Start Debugging Project** from the context menu.</span></span> <span data-ttu-id="20de8-209">Visual Studio 啟動已附加偵錯工具的測試專案。</span><span class="sxs-lookup"><span data-stu-id="20de8-209">Visual Studio starts the test project with the debugger attached.</span></span> <span data-ttu-id="20de8-210">執行會在您已加入測試專案或基礎程式庫程式碼的任何中斷點停止。</span><span class="sxs-lookup"><span data-stu-id="20de8-210">Execution will stop at any breakpoint you've added to the test project or the underlying library code.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="20de8-211">其他資源</span><span class="sxs-lookup"><span data-stu-id="20de8-211">Additional resources</span></span>

* [<span data-ttu-id="20de8-212">.NET Core 與 .NET Standard 中的單元測試</span><span class="sxs-lookup"><span data-stu-id="20de8-212">Unit testing in .NET Core and .NET Standard</span></span>](../testing/index.md)

## <a name="next-steps"></a><span data-ttu-id="20de8-213">後續步驟</span><span class="sxs-lookup"><span data-stu-id="20de8-213">Next steps</span></span>

<span data-ttu-id="20de8-214">在本教學課程中，您已對類別庫進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="20de8-214">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="20de8-215">您可以將程式庫發佈至[NuGet](https://nuget.org)作為套件，以供其他人使用。</span><span class="sxs-lookup"><span data-stu-id="20de8-215">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="20de8-216">若要深入瞭解，請遵循 NuGet 教學課程：</span><span class="sxs-lookup"><span data-stu-id="20de8-216">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="20de8-217">建立及發行套件 (dotnet CLI)</span><span class="sxs-lookup"><span data-stu-id="20de8-217">Create and publish a package (dotnet CLI)</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)

<span data-ttu-id="20de8-218">如果您將程式庫發佈為 NuGet 套件，則其他人可以安裝並使用它。</span><span class="sxs-lookup"><span data-stu-id="20de8-218">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="20de8-219">若要深入瞭解，請遵循 NuGet 教學課程：</span><span class="sxs-lookup"><span data-stu-id="20de8-219">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="20de8-220">在 Visual Studio for Mac 中安裝和使用套件</span><span class="sxs-lookup"><span data-stu-id="20de8-220">Install and use a package in Visual Studio for Mac</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio-mac)

<span data-ttu-id="20de8-221">程式庫不一定要以封裝的形式散發。</span><span class="sxs-lookup"><span data-stu-id="20de8-221">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="20de8-222">它可以與使用它的主控台應用程式配套。</span><span class="sxs-lookup"><span data-stu-id="20de8-222">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="20de8-223">若要瞭解如何發佈主控台應用程式，請參閱本系列中的先前教學課程：</span><span class="sxs-lookup"><span data-stu-id="20de8-223">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="20de8-224">使用 Visual Studio for Mac 發行 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="20de8-224">Publish a .NET Core console application with Visual Studio for Mac</span></span>](publishing-with-visual-studio-mac.md)
