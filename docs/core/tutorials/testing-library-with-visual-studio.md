---
title: 在 Visual Studio 中使用 .NET Core 測試 .NET Standard 類別庫
description: 為您的 .NET Core 類別庫建立單元測試專案。 藉由單元測試確認您的 .NET Core 類別庫運作正常。
ms.date: 05/21/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 48ada77b8422030fd93aa29df1df50a3ae5104fe
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283503"
---
# <a name="tutorial-test-a-net-standard-library-with-net-core-in-visual-studio"></a><span data-ttu-id="c3a23-104">教學課程：在 Visual Studio 中使用 .NET Core 測試 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="c3a23-104">Tutorial: Test a .NET Standard library with .NET Core in Visual Studio</span></span>

<span data-ttu-id="c3a23-105">本教學課程說明如何藉由將測試專案加入至方案，來自動化單元測試。</span><span class="sxs-lookup"><span data-stu-id="c3a23-105">This tutorial shows how to automate unit testing by adding a test project to a solution.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c3a23-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="c3a23-106">Prerequisites</span></span>

- <span data-ttu-id="c3a23-107">本教學課程適用于您在[Visual Studio 中建立 .NET Standard 程式庫](library-with-visual-studio.md)中建立的解決方案。</span><span class="sxs-lookup"><span data-stu-id="c3a23-107">This tutorial works with the solution that you create in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="c3a23-108">建立單元測試專案</span><span class="sxs-lookup"><span data-stu-id="c3a23-108">Create a unit test project</span></span>

1. <span data-ttu-id="c3a23-109">開啟 `ClassLibraryProjects` 您在[Visual Studio 中建立 .NET Standard 程式庫](library-with-visual-studio.md)中建立的解決方案。</span><span class="sxs-lookup"><span data-stu-id="c3a23-109">Open the `ClassLibraryProjects` solution you created in [Create a .NET Standard library in Visual Studio](library-with-visual-studio.md).</span></span>

1. <span data-ttu-id="c3a23-110">將名為 "StringLibraryTest" 的新單元測試專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="c3a23-110">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="c3a23-111">以滑鼠右鍵按一下**方案總管**中的方案，然後選取 [**加入**  >  **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="c3a23-111">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="c3a23-112">在 [**加入新專案**] 頁面的 [搜尋] 方塊中，輸入**mstest** 。</span><span class="sxs-lookup"><span data-stu-id="c3a23-112">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="c3a23-113">選擇 [語言] 清單中的 [ **c #** ] 或 [ **Visual Basic** ，然後從 [平臺] 清單中選擇 [**所有平臺**]。</span><span class="sxs-lookup"><span data-stu-id="c3a23-113">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="c3a23-114">選擇 [ **MSTest 測試專案（.Net Core）** ] 範本，然後選擇 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="c3a23-114">Choose the **MSTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="c3a23-115">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**StringLibraryTest** 。</span><span class="sxs-lookup"><span data-stu-id="c3a23-115">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="c3a23-116">接著，選擇 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="c3a23-116">Then choose **Create**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="c3a23-117">MSTest 是您可以從中選擇的三種測試架構之一。</span><span class="sxs-lookup"><span data-stu-id="c3a23-117">MSTest is one of three test frameworks you can choose from.</span></span> <span data-ttu-id="c3a23-118">其他則是 xUnit 和 nUnit。</span><span class="sxs-lookup"><span data-stu-id="c3a23-118">The others are xUnit and nUnit.</span></span>

1. <span data-ttu-id="c3a23-119">Visual Studio 會建立專案，並使用下列程式碼在程式碼視窗中開啟類別檔案。</span><span class="sxs-lookup"><span data-stu-id="c3a23-119">Visual Studio creates the project and opens the class file in the code window with the following code.</span></span> <span data-ttu-id="c3a23-120">如果未顯示您想要使用的語言，請變更頁面頂端的 [語言選取器]。</span><span class="sxs-lookup"><span data-stu-id="c3a23-120">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

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

   <span data-ttu-id="c3a23-121">單元測試範本建立的原始程式碼會執行下列動作︰</span><span class="sxs-lookup"><span data-stu-id="c3a23-121">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="c3a23-122">它會匯入 <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 命名空間，其中包含用於單元測試的類型。</span><span class="sxs-lookup"><span data-stu-id="c3a23-122">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>
   - <span data-ttu-id="c3a23-123">它會將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 屬性套用至 `UnitTest1` 類別。</span><span class="sxs-lookup"><span data-stu-id="c3a23-123">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span>
   - <span data-ttu-id="c3a23-124">它會套用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性，以 `TestMethod1` 在 c # 中或 `TestSub` 在 Visual Basic 中定義。</span><span class="sxs-lookup"><span data-stu-id="c3a23-124">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic.</span></span>

   <span data-ttu-id="c3a23-125">執行單元測試時，會自動執行在標記為[[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute)的測試類別中，以[[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute)標記的每個方法。</span><span class="sxs-lookup"><span data-stu-id="c3a23-125">Each method tagged with [[TestMethod]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) in a test class tagged with [[TestClass]](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) is executed automatically when the unit test is run.</span></span>

1. <span data-ttu-id="c3a23-126">在**方案總管**中，以滑鼠右鍵按一下**StringLibraryTest**專案的 [相依性] 節點，然後從內容功能表中選取 [**加入專案參考** **]** 。</span><span class="sxs-lookup"><span data-stu-id="c3a23-126">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Project Reference** from the context menu.</span></span>

1. <span data-ttu-id="c3a23-127">在 [**參考管理員**] 對話方塊中，展開 [**專案**] 節點，然後選取 [ **StringLibrary**] 旁的方塊。</span><span class="sxs-lookup"><span data-stu-id="c3a23-127">In the **Reference Manager** dialog, expand the **Projects** node, and select the box next to **StringLibrary**.</span></span> <span data-ttu-id="c3a23-128">將參考加入 `StringLibrary` 元件，可讓編譯器在編譯**StringLibraryTest**專案時尋找**StringLibrary**方法。</span><span class="sxs-lookup"><span data-stu-id="c3a23-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods while compiling the **StringLibraryTest** project.</span></span>

1. <span data-ttu-id="c3a23-129">選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="c3a23-129">Select **OK**.</span></span>

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="c3a23-130">新增和執行單元測試方法</span><span class="sxs-lookup"><span data-stu-id="c3a23-130">Add and run unit test methods</span></span>

<span data-ttu-id="c3a23-131">當 Visual Studio 執行單元測試時，它會在以屬性標記的類別中，執行以屬性標記的每個方法 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 。</span><span class="sxs-lookup"><span data-stu-id="c3a23-131">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a class that is marked with the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute.</span></span> <span data-ttu-id="c3a23-132">測試方法會在發現第一個失敗或方法中包含的所有測試都成功時結束。</span><span class="sxs-lookup"><span data-stu-id="c3a23-132">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="c3a23-133">最常見的測試會呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 類別的成員。</span><span class="sxs-lookup"><span data-stu-id="c3a23-133">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="c3a23-134">許多判斷提示方法都至少包括兩個參數，一個是預期的測試結果，另一個是實際的測試結果。</span><span class="sxs-lookup"><span data-stu-id="c3a23-134">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="c3a23-135">`Assert`下表顯示一些類別最常被呼叫的方法：</span><span class="sxs-lookup"><span data-stu-id="c3a23-135">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="c3a23-136">Assert 方法</span><span class="sxs-lookup"><span data-stu-id="c3a23-136">Assert methods</span></span>     | <span data-ttu-id="c3a23-137">函式</span><span class="sxs-lookup"><span data-stu-id="c3a23-137">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="c3a23-138">驗證兩個值或物件相等。</span><span class="sxs-lookup"><span data-stu-id="c3a23-138">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="c3a23-139">如果值或物件不相等，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="c3a23-139">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="c3a23-140">驗證兩個物件變數參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="c3a23-140">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="c3a23-141">如果變數參考不同的物件，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="c3a23-141">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="c3a23-142">驗證條件為 `false`。</span><span class="sxs-lookup"><span data-stu-id="c3a23-142">Verifies that a condition is `false`.</span></span> <span data-ttu-id="c3a23-143">如果條件為 `true`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="c3a23-143">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="c3a23-144">驗證物件不是 `null` 。</span><span class="sxs-lookup"><span data-stu-id="c3a23-144">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="c3a23-145">如果物件為 `null`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="c3a23-145">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="c3a23-146">您也可以 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> 在測試方法中使用方法，以指出預期會擲回的例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="c3a23-146">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A?displayProperty=nameWithType> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="c3a23-147">如果未擲回指定的例外狀況，測試將會失敗。</span><span class="sxs-lookup"><span data-stu-id="c3a23-147">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="c3a23-148">在測試 `StringLibrary.StartsWithUpper` 方法時，您想提供幾個以大寫字元開頭的字串。</span><span class="sxs-lookup"><span data-stu-id="c3a23-148">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="c3a23-149">您預期此方法在這些情況下傳回 `true`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="c3a23-149">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="c3a23-150">同樣地，您想提供幾個開頭不是大寫字元的字串。</span><span class="sxs-lookup"><span data-stu-id="c3a23-150">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="c3a23-151">您預期此方法在這些情況下傳回 `false`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="c3a23-151">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c3a23-152">由於您的程式庫方法會處理字串，因此您也會想要確定它會成功處理[空字串（ `String.Empty` ）](xref:System.String.Empty)、沒有任何字元的有效字串，以及 <xref:System.String.Length> 未初始化的 `null` 字串。</span><span class="sxs-lookup"><span data-stu-id="c3a23-152">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="c3a23-153">如果在 `StartsWithUpper` 實例上呼叫作為擴充方法 <xref:System.String> ，則不能將字串傳遞給它 `null` 。</span><span class="sxs-lookup"><span data-stu-id="c3a23-153">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it can't be passed a `null` string.</span></span> <span data-ttu-id="c3a23-154">不過，您也可以將其作為靜態方法來直接呼叫，並傳遞單一 <xref:System.String> 引數。</span><span class="sxs-lookup"><span data-stu-id="c3a23-154">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="c3a23-155">您會定義三個方法，每個方法會 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 針對字串陣列中的每個元素重複呼叫方法。</span><span class="sxs-lookup"><span data-stu-id="c3a23-155">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="c3a23-156">因為測試方法會在發現第一次失敗時失敗，所以您會呼叫方法多載，讓您傳遞一個字串來表示方法呼叫中所使用的字串值。</span><span class="sxs-lookup"><span data-stu-id="c3a23-156">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="c3a23-157">建立測試方法：</span><span class="sxs-lookup"><span data-stu-id="c3a23-157">To create the test methods:</span></span>

1. <span data-ttu-id="c3a23-158">在 [ *UnitTest1.cs* ] 或 [ *unittest1.cpp* ] 程式碼視窗中，將程式碼取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="c3a23-158">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibraryTest/UnitTest1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibraryTest/UnitTest1.vb":::

   <span data-ttu-id="c3a23-159">方法中的大寫字元測試 `TestStartsWithUpper` 包含希臘文大寫字母 Alpha （u + 0391）和斯拉夫文大寫字母 EM （u + 041C）。</span><span class="sxs-lookup"><span data-stu-id="c3a23-159">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="c3a23-160">方法中的小寫字元測試 `TestDoesNotStartWithUpper` 包含希臘文小寫字母 Alpha （u + 03B1）和斯拉夫文小寫字母 Ghe （u + 0433）。</span><span class="sxs-lookup"><span data-stu-id="c3a23-160">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="c3a23-161">在功能表列上，選取 [ **file**  >  **save UnitTest1.cs as** ] 或 [ **file**  >  **save unittest1.cpp .vb as**]。</span><span class="sxs-lookup"><span data-stu-id="c3a23-161">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="c3a23-162">在 [另存新檔]\*\*\*\* 對話方塊中，選取 [儲存]\*\*\*\* 按鈕旁的箭號，然後選取 [以編碼方式儲存]\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c3a23-162">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="c3a23-163">![Visual Studio 另存新檔] 對話方塊](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="c3a23-163">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="c3a23-164">在 [確認另存新檔]\*\*\*\* 對話方塊中，選取 [是]\*\*\*\* 按鈕以儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="c3a23-164">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="c3a23-165">在 [進階儲存選項]\*\*\*\* 對話方塊中，選取 [編碼]\*\*\*\* 下拉式清單中的 [Unicode (UTF-8 有簽章) - 字碼頁 65001]\*\*\*\*，然後選取 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c3a23-165">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="c3a23-166">![Visual Studio [進階儲存選項] 對話方塊](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="c3a23-166">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="c3a23-167">如果您無法將您的原始程式碼儲存為 UTF8 編碼檔案，Visual Studio 可能會將它儲存為 ASCII 檔案。</span><span class="sxs-lookup"><span data-stu-id="c3a23-167">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="c3a23-168">發生這種情況時，執行時間不會正確地解碼 ASCII 範圍以外的 UTF8 字元，而且測試結果將會不正確。</span><span class="sxs-lookup"><span data-stu-id="c3a23-168">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="c3a23-169">在功能表列上，選取 [**測試**] [執行] [  >  **所有測試**]。</span><span class="sxs-lookup"><span data-stu-id="c3a23-169">On the menu bar, select **Test** > **Run All Tests**.</span></span> <span data-ttu-id="c3a23-170">如果 [**測試 explorer** ] 視窗未開啟，請選擇 [**測試**] [測試  >  **瀏覽器**] 加以開啟。</span><span class="sxs-lookup"><span data-stu-id="c3a23-170">If the **Test Explorer** window doesn't open, open it by choosing **Test** > **Test Explorer**.</span></span> <span data-ttu-id="c3a23-171">這三項測試都會列在 [通過的測試]\*\*\*\* 區段中，而 [摘要]\*\*\*\* 區段則報告測試回合的結果。</span><span class="sxs-lookup"><span data-stu-id="c3a23-171">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="c3a23-172">![測試總管視窗，其中包含通過的測試](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="c3a23-172">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="c3a23-173">處理測試失敗</span><span class="sxs-lookup"><span data-stu-id="c3a23-173">Handle test failures</span></span>

<span data-ttu-id="c3a23-174">如果您執行的是測試導向開發（TDD），您必須先撰寫測試，而且第一次執行時才會失敗。</span><span class="sxs-lookup"><span data-stu-id="c3a23-174">If you're doing test-driven development (TDD), you write tests first and they fail the first time you run them.</span></span> <span data-ttu-id="c3a23-175">接著，您可以將程式碼新增至應用程式，讓測試成功。</span><span class="sxs-lookup"><span data-stu-id="c3a23-175">Then you add code to the app that makes the test succeed.</span></span> <span data-ttu-id="c3a23-176">在此情況下，您在撰寫應用程式驗證碼之後就已建立測試，因此您未看到測試失敗。</span><span class="sxs-lookup"><span data-stu-id="c3a23-176">In this case, you created the test after writing the app code that it validates, so you haven't seen the test fail.</span></span> <span data-ttu-id="c3a23-177">若要驗證測試在預期失敗時失敗，請在測試輸入中加入不正確值。</span><span class="sxs-lookup"><span data-stu-id="c3a23-177">To validate that a test fails when you expect it to fail, add an invalid value to the test input.</span></span>

1. <span data-ttu-id="c3a23-178">修改 `TestDoesNotStartWithUpper` 方法中的 `words` 陣列，以包含字串「錯誤」。</span><span class="sxs-lookup"><span data-stu-id="c3a23-178">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="c3a23-179">您不需要儲存檔案，因為當組建方案以執行測試時，Visual Studio 會自動儲存開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="c3a23-179">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="c3a23-180">從功能表列選取 [**測試**] [執行] [  >  **所有測試**] 來執行測試。</span><span class="sxs-lookup"><span data-stu-id="c3a23-180">Run the test by selecting **Test** > **Run All Tests** from the menu bar.</span></span> <span data-ttu-id="c3a23-181">[測試總管]\*\*\*\* 視窗表示兩個測試成功，而且有一項失敗。</span><span class="sxs-lookup"><span data-stu-id="c3a23-181">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="c3a23-182">![測試總管視窗，其中包含失敗的測試](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="c3a23-182">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="c3a23-183">選取失敗的測試 `TestDoesNotStartWith` 。</span><span class="sxs-lookup"><span data-stu-id="c3a23-183">Select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="c3a23-184">**[測試總管]** 下方的窗格會顯示判斷提示產生的訊息：「Assert.IsFalse 失敗。</span><span class="sxs-lookup"><span data-stu-id="c3a23-184">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="c3a23-185">'Error' 的預期︰false；實際：True」。</span><span class="sxs-lookup"><span data-stu-id="c3a23-185">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="c3a23-186">因為失敗，在「錯誤」之後的陣列中的所有字串都未經過測試。</span><span class="sxs-lookup"><span data-stu-id="c3a23-186">Because of the failure, all strings in the array after "Error" weren't tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="c3a23-187">![顯示 IsFalse 判斷提示失敗的測試 Explorer 視窗](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="c3a23-187">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="c3a23-188">復原您在步驟 1 中所做的修改，並移除字串 "Error"。</span><span class="sxs-lookup"><span data-stu-id="c3a23-188">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="c3a23-189">重新執行測試和測試階段。</span><span class="sxs-lookup"><span data-stu-id="c3a23-189">Rerun the test and the tests pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="c3a23-190">測試程式庫的發行版本</span><span class="sxs-lookup"><span data-stu-id="c3a23-190">Test the Release version of the library</span></span>

<span data-ttu-id="c3a23-191">在執行程式庫的「偵錯工具」版本後，現在所有測試都已成功，請針對程式庫的發行組建，再次執行測試。</span><span class="sxs-lookup"><span data-stu-id="c3a23-191">Now that the tests have all passed when running the Debug version of the library, run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="c3a23-192">許多因素 (包括編譯器最佳化) 有時會在偵錯和發行組建之間導致不同的行為。</span><span class="sxs-lookup"><span data-stu-id="c3a23-192">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="c3a23-193">測試發行組建︰</span><span class="sxs-lookup"><span data-stu-id="c3a23-193">To test the Release build:</span></span>

1. <span data-ttu-id="c3a23-194">在 Visual Studio 工具列中，將組建組態從 [偵錯]\*\*\*\* 變更為 [發行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c3a23-194">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="c3a23-195">![醒目提示 [發行] 組建的 Visual Studio 工具列](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="c3a23-195">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="c3a23-196">在方案總管\*\*\*\* 中，以滑鼠右鍵按一下 **StringLibrary** 專案，然後從內容功能表中選取 [組建]\*\*\*\* 以重新編譯程式庫。</span><span class="sxs-lookup"><span data-stu-id="c3a23-196">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="c3a23-197">![StringLibrary 操作功能表和建置命令](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="c3a23-197">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="c3a23-198">從功能表列中選擇 [**測試**] [執行] [  >  **所有測試**] 來執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="c3a23-198">Run the unit tests by choosing **Test Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="c3a23-199">所有測試皆通過。</span><span class="sxs-lookup"><span data-stu-id="c3a23-199">The tests pass.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c3a23-200">其他資源</span><span class="sxs-lookup"><span data-stu-id="c3a23-200">Additional resources</span></span>

- [<span data-ttu-id="c3a23-201">單元測試基本概念-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c3a23-201">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)

## <a name="next-steps"></a><span data-ttu-id="c3a23-202">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c3a23-202">Next steps</span></span>

<span data-ttu-id="c3a23-203">在本教學課程中，您已對類別庫進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="c3a23-203">In this tutorial, you unit tested a class library.</span></span> <span data-ttu-id="c3a23-204">您可以將程式庫發佈至[NuGet](https://nuget.org)作為套件，以供其他人使用。</span><span class="sxs-lookup"><span data-stu-id="c3a23-204">You can make the library available to others by publishing it to [NuGet](https://nuget.org) as a package.</span></span> <span data-ttu-id="c3a23-205">若要深入瞭解，請遵循 NuGet 教學課程：</span><span class="sxs-lookup"><span data-stu-id="c3a23-205">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c3a23-206">使用 Visual Studio 建立和發佈 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="c3a23-206">Create and publish a NuGet package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio?tabs=netcore-cli)

<span data-ttu-id="c3a23-207">如果您將程式庫發佈為 NuGet 套件，則其他人可以安裝並使用它。</span><span class="sxs-lookup"><span data-stu-id="c3a23-207">If you publish a library as a NuGet package, others can install and use it.</span></span> <span data-ttu-id="c3a23-208">若要深入瞭解，請遵循 NuGet 教學課程：</span><span class="sxs-lookup"><span data-stu-id="c3a23-208">To learn how, follow a NuGet tutorial:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c3a23-209">在 Visual Studio 中安裝並使用套件</span><span class="sxs-lookup"><span data-stu-id="c3a23-209">Install and use a package in Visual Studio</span></span>](/nuget/quickstart/install-and-use-a-package-in-visual-studio)

<span data-ttu-id="c3a23-210">程式庫不一定要以封裝的形式散發。</span><span class="sxs-lookup"><span data-stu-id="c3a23-210">A library doesn't have to be distributed as a package.</span></span> <span data-ttu-id="c3a23-211">它可以與使用它的主控台應用程式配套。</span><span class="sxs-lookup"><span data-stu-id="c3a23-211">It can be bundled with a console app that uses it.</span></span> <span data-ttu-id="c3a23-212">若要瞭解如何發佈主控台應用程式，請參閱本系列中的先前教學課程：</span><span class="sxs-lookup"><span data-stu-id="c3a23-212">To learn how to publish a console app, see the earlier tutorial in this series:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c3a23-213">使用 Visual Studio 發行 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="c3a23-213">Publish a .NET Core console application with Visual Studio</span></span>](publishing-with-visual-studio.md)
