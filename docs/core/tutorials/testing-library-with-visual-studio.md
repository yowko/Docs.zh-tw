---
title: 在視覺化工作室中使用 .NET 核心測試 .NET 標準類庫
description: 為您的 .NET Core 類別庫建立單元測試專案。 藉由單元測試確認您的 .NET Core 類別庫運作正常。
ms.date: 12/24/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 307261088f5c7c69c0e69fbd6b99940c04842eec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156617"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio"></a><span data-ttu-id="4e387-104">在視覺化工作室中使用 .NET 核心測試 .NET 標準庫</span><span class="sxs-lookup"><span data-stu-id="4e387-104">Test a .NET Standard library with .NET Core in Visual Studio</span></span>

<span data-ttu-id="4e387-105">在[Visual Studio 中構建 .NET 標準庫中](library-with-visual-studio.md)，您創建了一個簡單的類庫，向<xref:System.String>類添加擴充方法。</span><span class="sxs-lookup"><span data-stu-id="4e387-105">In [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md), you created a simple class library that adds an extension method to the <xref:System.String> class.</span></span> <span data-ttu-id="4e387-106">現在您將建立單元測試，確定它如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="4e387-106">Now, you'll create a unit test to make sure that it works as expected.</span></span> <span data-ttu-id="4e387-107">我們會將我們的單元測試專案加入在上一篇文章中建立的方案。</span><span class="sxs-lookup"><span data-stu-id="4e387-107">You'll add your unit test project to the solution you created in the previous article.</span></span>

## <a name="create-a-unit-test-project"></a><span data-ttu-id="4e387-108">建立單元測試專案</span><span class="sxs-lookup"><span data-stu-id="4e387-108">Create a unit test project</span></span>

<span data-ttu-id="4e387-109">若要建立單元測試專案，請執行下列作業︰</span><span class="sxs-lookup"><span data-stu-id="4e387-109">To create the unit test project, do the following:</span></span>

1. <span data-ttu-id="4e387-110">打開在`ClassLibraryProjects`Visual Studio 文章中[生成 .NET 標準庫中](library-with-visual-studio.md)創建的解決方案。</span><span class="sxs-lookup"><span data-stu-id="4e387-110">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="4e387-111">向解決方案添加名為"StringLibraryTest"的新單元測試專案。</span><span class="sxs-lookup"><span data-stu-id="4e387-111">Add a new unit test project named "StringLibraryTest" to the solution.</span></span>

   1. <span data-ttu-id="4e387-112">按右鍵**解決方案資源管理器**中的解決方案，然後選擇"**添加新** > **專案**"。</span><span class="sxs-lookup"><span data-stu-id="4e387-112">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="4e387-113">在"**添加新專案**"頁上，在搜索框中輸入**mstest。**</span><span class="sxs-lookup"><span data-stu-id="4e387-113">On the **Add a new project** page, enter **mstest** in the search box.</span></span> <span data-ttu-id="4e387-114">從"語言"清單中選擇**C#** 或**視覺化基本，** 然後從"平臺"清單中選擇 **"所有平臺**"。</span><span class="sxs-lookup"><span data-stu-id="4e387-114">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="4e387-115">選擇**MsTest 測試專案 （.NET 核心）** 範本，然後選擇 **"下一步**"。</span><span class="sxs-lookup"><span data-stu-id="4e387-115">Choose the **MsTest Test Project (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="4e387-116">在"**配置新專案**"頁上，在 **"專案名稱"** 框中輸入**字串庫測試**。</span><span class="sxs-lookup"><span data-stu-id="4e387-116">On the **Configure your new project** page, enter **StringLibraryTest** in the **Project name** box.</span></span> <span data-ttu-id="4e387-117">然後選擇 [建立]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4e387-117">Then choose **Create**.</span></span>

   > [!NOTE]
   > <span data-ttu-id="4e387-118">除了 MSTest 之外，您還可以在視覺化工作室中為 .NET Core 創建 xUnit 和 nUnit 測試專案。</span><span class="sxs-lookup"><span data-stu-id="4e387-118">In addition to an MSTest, you can also create xUnit and nUnit test projects for .NET Core in Visual Studio.</span></span>

1. <span data-ttu-id="4e387-119">Visual Studio 創建專案，並在代碼視窗中使用以下代碼打開類檔：</span><span class="sxs-lookup"><span data-stu-id="4e387-119">Visual Studio creates the project and opens the class file in the code window with the following code:</span></span>

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

   <span data-ttu-id="4e387-120">單元測試範本建立的原始程式碼會執行下列動作︰</span><span class="sxs-lookup"><span data-stu-id="4e387-120">The source code created by the unit test template does the following:</span></span>

   - <span data-ttu-id="4e387-121">它會匯入 <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 命名空間，其中包含用於單元測試的類型。</span><span class="sxs-lookup"><span data-stu-id="4e387-121">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>

   - <span data-ttu-id="4e387-122">它會將 [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) 屬性套用至 `UnitTest1` 類別。</span><span class="sxs-lookup"><span data-stu-id="4e387-122">It applies the [TestClass](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute) attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="4e387-123">執行單元測試時，在測試類別中標示 [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) 屬性的每個測試方法都將自動執行。</span><span class="sxs-lookup"><span data-stu-id="4e387-123">Each test method in a test class tagged with the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute is executed automatically when the unit test is run.</span></span>

   - <span data-ttu-id="4e387-124">它將[TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute)屬性應用於在`TestMethod1`C#`TestSub`或 Visual Basic 中定義，作為運行單元測試時自動執行的測試方法。</span><span class="sxs-lookup"><span data-stu-id="4e387-124">It applies the [TestMethod](xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute) attribute to define `TestMethod1` in C# or `TestSub` in Visual Basic as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="4e387-125">在方案總管\*\*\*\* 中，以滑鼠右鍵按一下 **StringLibraryTest** 專案的 [相依性]\*\*\*\* 節點，然後從內容功能表中選取 [新增參考]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4e387-125">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4e387-126">![字串庫測試依賴項的內容功能表](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="4e387-126">![Context menu of StringLibraryTest dependencies](./media/testing-library-with-visual-studio/add-reference-context-menu.png)</span></span>

1. <span data-ttu-id="4e387-127">在 [參考管理員]\*\*\*\* 對話方塊中，展開 [專案]\*\*\*\* 節點並核取 [StringLibrary]\*\*\*\* 旁的方塊。</span><span class="sxs-lookup"><span data-stu-id="4e387-127">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="4e387-128">將參考新增至 `StringLibrary` 組件，可讓編譯器找出 **StringLibrary** 方法。</span><span class="sxs-lookup"><span data-stu-id="4e387-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="4e387-129">選擇"**確定"** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4e387-129">Select the **OK** button.</span></span> <span data-ttu-id="4e387-130">引用將添加到類庫專案 。 `StringLibrary`</span><span class="sxs-lookup"><span data-stu-id="4e387-130">A reference is added to your class library project, `StringLibrary`.</span></span>

   ![視覺化工作室中的參考管理器對話方塊](./media/testing-library-with-visual-studio/project-reference-manager.png)

## <a name="add-and-run-unit-test-methods"></a><span data-ttu-id="4e387-132">添加和運行單元測試方法</span><span class="sxs-lookup"><span data-stu-id="4e387-132">Add and run unit test methods</span></span>

<span data-ttu-id="4e387-133">當 Visual Studio 運行單元測試時，它將執行在單元測試類中<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute>標記屬性的每個方法，即應用該屬性的<xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>類。</span><span class="sxs-lookup"><span data-stu-id="4e387-133">When Visual Studio runs a unit test, it executes each method that is marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a unit test class, the class to which the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute is applied.</span></span> <span data-ttu-id="4e387-134">當發現第一個失敗或該方法中包含的所有測試都成功時，測試方法將結束。</span><span class="sxs-lookup"><span data-stu-id="4e387-134">A test method ends when the first failure is found or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="4e387-135">最常見的測試會呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 類別的成員。</span><span class="sxs-lookup"><span data-stu-id="4e387-135">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="4e387-136">許多判斷提示方法都至少包括兩個參數，一個是預期的測試結果，另一個是實際的測試結果。</span><span class="sxs-lookup"><span data-stu-id="4e387-136">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="4e387-137">`Assert`類中一些最常用的方法顯示在下表中：</span><span class="sxs-lookup"><span data-stu-id="4e387-137">Some of the `Assert` class's most frequently called methods are shown in the following table:</span></span>

| <span data-ttu-id="4e387-138">Assert 方法</span><span class="sxs-lookup"><span data-stu-id="4e387-138">Assert methods</span></span>     | <span data-ttu-id="4e387-139">函式</span><span class="sxs-lookup"><span data-stu-id="4e387-139">Function</span></span> |
| ------------------ | -------- |
| `Assert.AreEqual`  | <span data-ttu-id="4e387-140">驗證兩個值或物件相等。</span><span class="sxs-lookup"><span data-stu-id="4e387-140">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="4e387-141">如果值或物件不相等，斷言將失敗。</span><span class="sxs-lookup"><span data-stu-id="4e387-141">The assert fails if the values or objects aren't equal.</span></span> |
| `Assert.AreSame`   | <span data-ttu-id="4e387-142">驗證兩個物件變數參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="4e387-142">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="4e387-143">如果變數參考不同的物件，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="4e387-143">The assert fails if the variables refer to different objects.</span></span> |
| `Assert.IsFalse`   | <span data-ttu-id="4e387-144">驗證條件為 `false`。</span><span class="sxs-lookup"><span data-stu-id="4e387-144">Verifies that a condition is `false`.</span></span> <span data-ttu-id="4e387-145">如果條件為 `true`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="4e387-145">The assert fails if the condition is `true`.</span></span> |
| `Assert.IsNotNull` | <span data-ttu-id="4e387-146">驗證物件不是`null`。</span><span class="sxs-lookup"><span data-stu-id="4e387-146">Verifies that an object isn't `null`.</span></span> <span data-ttu-id="4e387-147">如果物件為 `null`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="4e387-147">The assert fails if the object is `null`.</span></span> |

<span data-ttu-id="4e387-148">您還可以在測試方法中使用<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A>方法來指示預期要引發的異常類型。</span><span class="sxs-lookup"><span data-stu-id="4e387-148">You can also use the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.ThrowsException%2A> method in a test method to indicate the type of exception it's expected to throw.</span></span> <span data-ttu-id="4e387-149">如果未引發指定的異常，則測試將失敗。</span><span class="sxs-lookup"><span data-stu-id="4e387-149">The test fails if the specified exception isn't thrown.</span></span>

<span data-ttu-id="4e387-150">在測試 `StringLibrary.StartsWithUpper` 方法時，您想提供幾個以大寫字元開頭的字串。</span><span class="sxs-lookup"><span data-stu-id="4e387-150">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="4e387-151">您預期此方法在這些情況下傳回 `true`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="4e387-151">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> method.</span></span> <span data-ttu-id="4e387-152">同樣地，您想提供幾個開頭不是大寫字元的字串。</span><span class="sxs-lookup"><span data-stu-id="4e387-152">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="4e387-153">您預期此方法在這些情況下傳回 `false`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="4e387-153">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> method.</span></span>

<span data-ttu-id="4e387-154">由於庫方法處理字串，您還希望確保它成功處理[一個空字串`String.Empty`（），](xref:System.String.Empty)一個沒有字元且其<xref:System.String.Length>為 0 的有效字串，以及尚未初始化的`null`字串。</span><span class="sxs-lookup"><span data-stu-id="4e387-154">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that hasn't been initialized.</span></span> <span data-ttu-id="4e387-155">如果在`StartsWithUpper`<xref:System.String>實例上調用為擴充方法，則無法傳遞`null`字串。</span><span class="sxs-lookup"><span data-stu-id="4e387-155">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it can't be passed a `null` string.</span></span> <span data-ttu-id="4e387-156">不過，您也可以將其作為靜態方法來直接呼叫，並傳遞單一 <xref:System.String> 引數。</span><span class="sxs-lookup"><span data-stu-id="4e387-156">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="4e387-157">您將定義三種方法，每個方法都針對字串陣列中的每個<xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert>元素重複調用一個方法。</span><span class="sxs-lookup"><span data-stu-id="4e387-157">You'll define three methods, each of which calls an <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="4e387-158">由於 test 方法發現第一個失敗後立即失敗，因此您將調用一個方法重載，該重載允許您傳遞指示方法調用中使用的字串值的字串。</span><span class="sxs-lookup"><span data-stu-id="4e387-158">Because the test method fails as soon as it finds the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="4e387-159">建立測試方法：</span><span class="sxs-lookup"><span data-stu-id="4e387-159">To create the test methods:</span></span>

1. <span data-ttu-id="4e387-160">在*UnitTest1.cs*或*UnitTest1.vb*代碼視窗中，用以下代碼替換代碼：</span><span class="sxs-lookup"><span data-stu-id="4e387-160">In the *UnitTest1.cs* or *UnitTest1.vb* code window, replace the code with the following code:</span></span>

   [!code-csharp[Test#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]
   [!code-vb[Test#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   <span data-ttu-id="4e387-161">`TestStartsWithUpper`該方法中的大寫字元測試包括希臘大寫字母 Alpha （U+0391） 和西瑞爾大寫字母 EM （U+041C）。</span><span class="sxs-lookup"><span data-stu-id="4e387-161">The test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C).</span></span> <span data-ttu-id="4e387-162">`TestDoesNotStartWithUpper`該方法中小寫字元的測試包括希臘小寫字母 Alpha （U+03B1） 和西瑞爾小字母 Ghe （U+0433）。</span><span class="sxs-lookup"><span data-stu-id="4e387-162">The test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="4e387-163">在功能表列上，選擇 **"檔** > **保存UnitTest1.cs為**或**檔** > **保存單元測試1.vb為**。</span><span class="sxs-lookup"><span data-stu-id="4e387-163">On the menu bar, select **File** > **Save UnitTest1.cs As** or **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="4e387-164">在 [另存新檔]\*\*\*\* 對話方塊中，選取 [儲存]\*\*\*\* 按鈕旁的箭號，然後選取 [以編碼方式儲存]\*\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4e387-164">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4e387-165">![視覺化工作室保存檔作為對話方塊](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span><span class="sxs-lookup"><span data-stu-id="4e387-165">![Visual Studio Save File As dialog](./media/testing-library-with-visual-studio/save-file-as-dialog.png)</span></span>

1. <span data-ttu-id="4e387-166">在 [確認另存新檔]\*\*\*\* 對話方塊中，選取 [是]\*\*\*\* 按鈕以儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="4e387-166">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="4e387-167">在 [進階儲存選項]\*\*\*\* 對話方塊中，選取 [編碼]\*\*\*\* 下拉式清單中的 [Unicode (UTF-8 有簽章) - 字碼頁 65001]\*\*\*\*，然後選取 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4e387-167">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4e387-168">![Visual Studio [進階儲存選項] 對話方塊](./media/testing-library-with-visual-studio/advanced-save-options.png)</span><span class="sxs-lookup"><span data-stu-id="4e387-168">![Visual Studio Advanced Save Options dialog](./media/testing-library-with-visual-studio/advanced-save-options.png)</span></span>

   <span data-ttu-id="4e387-169">如果您無法將您的原始程式碼儲存為 UTF8 編碼檔案，Visual Studio 可能會將它儲存為 ASCII 檔案。</span><span class="sxs-lookup"><span data-stu-id="4e387-169">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="4e387-170">發生這種情況時，運行時無法準確解碼 ASCII 範圍之外的 UTF8 字元，並且測試結果將不正確。</span><span class="sxs-lookup"><span data-stu-id="4e387-170">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be correct.</span></span>

1. <span data-ttu-id="4e387-171">在功能表列上，選擇 **"測試** > **運行** > **所有測試**"。</span><span class="sxs-lookup"><span data-stu-id="4e387-171">On the menu bar, select **Test** > **Run** > **All Tests**.</span></span> <span data-ttu-id="4e387-172">[測試總管]\*\*\*\* 視窗隨即開啟並顯示測試成功執行。</span><span class="sxs-lookup"><span data-stu-id="4e387-172">The **Test Explorer** window opens and shows that the tests ran successfully.</span></span> <span data-ttu-id="4e387-173">這三項測試都會列在 [通過的測試]\*\*\*\* 區段中，而 [摘要]\*\*\*\* 區段則報告測試回合的結果。</span><span class="sxs-lookup"><span data-stu-id="4e387-173">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4e387-174">![測試總管視窗，其中包含通過的測試](./media/testing-library-with-visual-studio/test-explorer-window.png)</span><span class="sxs-lookup"><span data-stu-id="4e387-174">![Test Explorer window with passing tests](./media/testing-library-with-visual-studio/test-explorer-window.png)</span></span>

## <a name="handle-test-failures"></a><span data-ttu-id="4e387-175">處理測試失敗</span><span class="sxs-lookup"><span data-stu-id="4e387-175">Handle test failures</span></span>

<span data-ttu-id="4e387-176">您的測試回合未失敗，但將它稍微變更，使其中一個測試方法失敗：</span><span class="sxs-lookup"><span data-stu-id="4e387-176">Your test run had no failures, but change it slightly so that one of the test methods fails:</span></span>

1. <span data-ttu-id="4e387-177">修改 `TestDoesNotStartWithUpper` 方法中的 `words` 陣列，以包含字串「錯誤」。</span><span class="sxs-lookup"><span data-stu-id="4e387-177">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="4e387-178">您不需要儲存檔案，因為當組建方案以執行測試時，Visual Studio 會自動儲存開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="4e387-178">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="4e387-179">通過從功能表列中選擇 **"測試** > **運行** > **所有測試**"來運行測試。</span><span class="sxs-lookup"><span data-stu-id="4e387-179">Run the test by selecting **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="4e387-180">[測試總管]\*\*\*\* 視窗表示兩個測試成功，而且有一項失敗。</span><span class="sxs-lookup"><span data-stu-id="4e387-180">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4e387-181">![測試總管視窗，其中包含失敗的測試](./media/testing-library-with-visual-studio/failed-test-window.png)</span><span class="sxs-lookup"><span data-stu-id="4e387-181">![Test Explorer window with failing tests](./media/testing-library-with-visual-studio/failed-test-window.png)</span></span>

1. <span data-ttu-id="4e387-182">選擇失敗的測試。 `TestDoesNotStartWith`</span><span class="sxs-lookup"><span data-stu-id="4e387-182">Select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="4e387-183">**[測試總管]** 下方的窗格會顯示判斷提示產生的訊息：「Assert.IsFalse 失敗。</span><span class="sxs-lookup"><span data-stu-id="4e387-183">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="4e387-184">'Error' 的預期︰false；實際：True」。</span><span class="sxs-lookup"><span data-stu-id="4e387-184">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="4e387-185">由於失敗，陣列中"錯誤"後的所有字串都未測試。</span><span class="sxs-lookup"><span data-stu-id="4e387-185">Because of the failure, all strings in the array after "Error" weren't tested.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4e387-186">![顯示 IsFalse 宣告失敗的測試資源管理器視窗](./media/testing-library-with-visual-studio/failed-test-detail.png)</span><span class="sxs-lookup"><span data-stu-id="4e387-186">![Test Explorer window showing the IsFalse assertion failure](./media/testing-library-with-visual-studio/failed-test-detail.png)</span></span>

1. <span data-ttu-id="4e387-187">復原您在步驟 1 中所做的修改，並移除字串 "Error"。</span><span class="sxs-lookup"><span data-stu-id="4e387-187">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="4e387-188">重新執行該測試，測試將會通過。</span><span class="sxs-lookup"><span data-stu-id="4e387-188">Rerun the test and the tests will pass.</span></span>

## <a name="test-the-release-version-of-the-library"></a><span data-ttu-id="4e387-189">測試庫的發佈版本</span><span class="sxs-lookup"><span data-stu-id="4e387-189">Test the Release version of the library</span></span>

<span data-ttu-id="4e387-190">您已針對偵錯版本的程式庫執行測試。</span><span class="sxs-lookup"><span data-stu-id="4e387-190">You've been running your tests against the Debug version of the library.</span></span> <span data-ttu-id="4e387-191">既然您的測試全部通過，並已充分測試過您的程式庫，您應針對程式庫的發行組建執行更多時間的測試。</span><span class="sxs-lookup"><span data-stu-id="4e387-191">Now that your tests have all passed and you've adequately tested your library, you should run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="4e387-192">許多因素 (包括編譯器最佳化) 有時會在偵錯和發行組建之間導致不同的行為。</span><span class="sxs-lookup"><span data-stu-id="4e387-192">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="4e387-193">測試發行組建︰</span><span class="sxs-lookup"><span data-stu-id="4e387-193">To test the Release build:</span></span>

1. <span data-ttu-id="4e387-194">在 Visual Studio 工具列中，將組建組態從 [偵錯]\*\*\*\* 變更為 [發行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="4e387-194">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4e387-195">![醒目提示 [發行] 組建的 Visual Studio 工具列](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span><span class="sxs-lookup"><span data-stu-id="4e387-195">![Visual Studio toolbar with release build highlighted](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)</span></span>

1. <span data-ttu-id="4e387-196">在方案總管\*\*\*\* 中，以滑鼠右鍵按一下 **StringLibrary** 專案，然後從內容功能表中選取 [組建]\*\*\*\* 以重新編譯程式庫。</span><span class="sxs-lookup"><span data-stu-id="4e387-196">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="4e387-197">![StringLibrary 操作功能表和建置命令](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span><span class="sxs-lookup"><span data-stu-id="4e387-197">![StringLibrary context menu with build command](./media/testing-library-with-visual-studio/build-library-context-menu.png)</span></span>

1. <span data-ttu-id="4e387-198">通過從功能表列中選擇 **"測試** > **運行** > **所有測試**"來運行單元測試。</span><span class="sxs-lookup"><span data-stu-id="4e387-198">Run the unit tests by choosing **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="4e387-199">所有測試皆通過。</span><span class="sxs-lookup"><span data-stu-id="4e387-199">The tests pass.</span></span>

<span data-ttu-id="4e387-200">既然您已經完成程式庫測試，下一步是將它提供給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="4e387-200">Now that you've finished testing your library, the next step is to make it available to callers.</span></span> <span data-ttu-id="4e387-201">您可以將它與一或多個應用程式搭售，或是將將它發佈為 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="4e387-201">You can bundle it with one or more applications, or you can distribute it as a NuGet package.</span></span> <span data-ttu-id="4e387-202">如需詳細資訊，請參閱[使用 .NET Standard 類別庫](consuming-library-with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="4e387-202">For more information, see [Consuming a .NET Standard Class Library](consuming-library-with-visual-studio.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e387-203">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e387-203">See also</span></span>

- [<span data-ttu-id="4e387-204">單元測試基礎知識 - 視覺化工作室</span><span class="sxs-lookup"><span data-stu-id="4e387-204">Unit test basics - Visual Studio</span></span>](/visualstudio/test/unit-test-basics)
