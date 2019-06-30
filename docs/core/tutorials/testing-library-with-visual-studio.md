---
title: 在 Visual Studio 2017 中使用 .NET Core 測試 .NET Standard 類別程式庫
description: 為您的 .NET Core 類別庫建立單元測試專案。 藉由單元測試確認您的 .NET Core 類別庫運作正常。
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodoc18
ms.openlocfilehash: 32593465c1a161aa1293b7b233539fa930c7e1d8
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402200"
---
# <a name="test-a-net-standard-library-with-net-core-in-visual-studio-2017"></a><span data-ttu-id="b8a66-104">在 Visual Studio 2017 中使用 .NET Core 測試 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="b8a66-104">Test a .NET Standard library with .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="b8a66-105">於[在 Visual Studio 2017 中使用 C# 和 .NET Core 建置 .NET Standard 程式庫](library-with-visual-studio.md)或[在 Visual Studio 2017 中使用 Visual Basic 和 .NET Core 建置 .NET Standard 程式庫](vb-library-with-visual-studio.md)中，您建立了一個將擴充方法新增至 <xref:System.String> 類別的簡易類別庫。</span><span class="sxs-lookup"><span data-stu-id="b8a66-105">In [Build a .NET Standard library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md) or [Build a .NET Standard library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md), you created a simple class library that adds an extension method to the <xref:System.String> class.</span></span> <span data-ttu-id="b8a66-106">現在我們將建立單元測試，確定它如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="b8a66-106">Now, you'll create a unit test to make sure that it works as expected.</span></span> <span data-ttu-id="b8a66-107">我們會將我們的單元測試專案加入在上一篇文章中建立的方案。</span><span class="sxs-lookup"><span data-stu-id="b8a66-107">You'll add your unit test project to the solution you created in the previous article.</span></span>

## <a name="creating-a-unit-test-project"></a><span data-ttu-id="b8a66-108">建立單元測試專案</span><span class="sxs-lookup"><span data-stu-id="b8a66-108">Creating a unit test project</span></span>

<span data-ttu-id="b8a66-109">若要建立單元測試專案，請執行下列作業︰</span><span class="sxs-lookup"><span data-stu-id="b8a66-109">To create the unit test project, do the following:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="b8a66-110">C#</span><span class="sxs-lookup"><span data-stu-id="b8a66-110">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="b8a66-111">在方案總管  中，開啟 **ClassLibraryProject** 方案節點的內容功能表，然後選取 [新增]   >  [新增專案]  。</span><span class="sxs-lookup"><span data-stu-id="b8a66-111">In **Solution Explorer**, open the context menu for the **ClassLibraryProjects** solution node and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="b8a66-112">在 [新增專案]  對話方塊中，選取 [Visual C#]  節點。</span><span class="sxs-lookup"><span data-stu-id="b8a66-112">In the **Add New Project** dialog, select the **Visual C#** node.</span></span> <span data-ttu-id="b8a66-113">然後選取後面跟著 [MSTest 測試專案 (.NET Core)]  專案範本的 [.NET Core]  節點。</span><span class="sxs-lookup"><span data-stu-id="b8a66-113">Then select the **.NET Core** node followed by the **MSTest Test Project (.NET Core)** project template.</span></span> <span data-ttu-id="b8a66-114">在 **[名稱]** 文字方塊中，輸入 "StringLibraryTest" 作為專案名稱。</span><span class="sxs-lookup"><span data-stu-id="b8a66-114">In the **Name** text box, enter "StringLibraryTest" as the name of the project.</span></span> <span data-ttu-id="b8a66-115">選取 [確定]  以建立單元測試專案。</span><span class="sxs-lookup"><span data-stu-id="b8a66-115">Select **OK** to create the unit test project.</span></span>

   ![顯示單元測試專案的 [新增專案] 對話方塊 - C#](./media/testing-library-with-visual-studio/create-new-test-project.png)

   > [!NOTE]  
   > <span data-ttu-id="b8a66-117">除了 MSTest 測試專案之外，您也可以使用 Visual Studio 建立適用於 .NET Core 的 xUnit 測試專案。</span><span class="sxs-lookup"><span data-stu-id="b8a66-117">In addition to an MSTest Test project, you can also use Visual Studio to create an xUnit test project for .NET Core.</span></span>

1. <span data-ttu-id="b8a66-118">Visual Studio 會建立專案，並在程式碼視窗中開啟 *UnitTest1.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="b8a66-118">Visual Studio creates the project and opens the *UnitTest1.cs* file in the code window.</span></span>

   ![單元測試專案類別和方法的 Visual Studio 程式碼視窗 - C#](./media/testing-library-with-visual-studio/unit-test-editor-window.png)

   <span data-ttu-id="b8a66-120">單元測試範本建立的原始程式碼會執行下列動作︰</span><span class="sxs-lookup"><span data-stu-id="b8a66-120">The source code created by the unit test template does the following:</span></span>

   * <span data-ttu-id="b8a66-121">它會匯入 <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 命名空間，其中包含用於單元測試的類型。</span><span class="sxs-lookup"><span data-stu-id="b8a66-121">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>

   * <span data-ttu-id="b8a66-122">它會將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 屬性套用至 `UnitTest1` 類別。</span><span class="sxs-lookup"><span data-stu-id="b8a66-122">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="b8a66-123">執行單元測試時，在測試類別中標示 \[TestMethod\] 屬性的每個測試方法都將自動執行。</span><span class="sxs-lookup"><span data-stu-id="b8a66-123">Each test method in a test class tagged with the \[TestMethod\] attribute is executed automatically when the unit test is run.</span></span>

   * <span data-ttu-id="b8a66-124">它會套用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性，以將 `TestMethod1` 定義為在執行單元測試時自動執行的測試方法。</span><span class="sxs-lookup"><span data-stu-id="b8a66-124">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="b8a66-125">在 **方案總管** 中，以滑鼠右鍵按一下 **StringLibraryTest** 專案的 **[相依性]** 節點，然後從內容功能表中選取 **[新增參考]** 。</span><span class="sxs-lookup"><span data-stu-id="b8a66-125">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   ![StringLibraryTest 相依性的操作功能表 - C#](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="b8a66-127">在 **[參考管理員]** 對話方塊中，展開 **[專案]** 節點並核取 **[StringLibrary]** 旁的方塊。</span><span class="sxs-lookup"><span data-stu-id="b8a66-127">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="b8a66-128">將參考新增至 `StringLibrary` 組件，可讓編譯器找出 **StringLibrary** 方法。</span><span class="sxs-lookup"><span data-stu-id="b8a66-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="b8a66-129">選取 [確定]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="b8a66-129">Select the **OK** button.</span></span> <span data-ttu-id="b8a66-130">這會在您的類別庫專案 `StringLibrary` 中新增參考。</span><span class="sxs-lookup"><span data-stu-id="b8a66-130">This adds a reference to your class library project, `StringLibrary`.</span></span>

   ![Visual Studio 新增專案參考對話方塊](./media/testing-library-with-visual-studio/project-reference-manager.png)
# <a name="visual-basictabvb"></a>[<span data-ttu-id="b8a66-132">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b8a66-132">Visual Basic</span></span>](#tab/vb) 
1. <span data-ttu-id="b8a66-133">在方案總管  中，開啟 **ClassLibraryProject** 方案節點的內容功能表，然後選取 [新增]   >  [新增專案]  。</span><span class="sxs-lookup"><span data-stu-id="b8a66-133">In **Solution Explorer**, open the context menu for the **ClassLibraryProjects** solution node and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="b8a66-134">在 [新增專案]  對話方塊中，選取 [Visual Basic]  節點。</span><span class="sxs-lookup"><span data-stu-id="b8a66-134">In the **Add New Project** dialog, select the **Visual Basic** node.</span></span> <span data-ttu-id="b8a66-135">然後選取後面跟著 [MSTest 測試專案 (.NET Core)]  專案範本的 [.NET Core]  節點。</span><span class="sxs-lookup"><span data-stu-id="b8a66-135">Then select the **.NET Core** node followed by the **MSTest Test Project (.NET Core)** project template.</span></span> <span data-ttu-id="b8a66-136">在 **[名稱]** 文字方塊中，輸入 "StringLibraryTest" 作為專案名稱。</span><span class="sxs-lookup"><span data-stu-id="b8a66-136">In the **Name** text box, enter "StringLibraryTest" as the name of the project.</span></span> <span data-ttu-id="b8a66-137">選取 [確定]  以建立單元測試專案。</span><span class="sxs-lookup"><span data-stu-id="b8a66-137">Select **OK** to create the unit test project.</span></span>

   ![顯示單元測試專案的 [新增專案] 對話方塊 - Visual Basic](./media/testing-library-with-visual-studio/vb-create-new-test-project.png)

   > [!NOTE]  
   > <span data-ttu-id="b8a66-139">除了 MSTest 測試專案之外，您也可以使用 Visual Studio 建立適用於 .NET Core 的 xUnit 測試專案。</span><span class="sxs-lookup"><span data-stu-id="b8a66-139">In addition to an MSTest Test project, you can also use Visual Studio to create an xUnit test project for .NET Core.</span></span>

1. <span data-ttu-id="b8a66-140">Visual Studio 會建立專案，並在程式碼視窗中開啟 *UnitTest1.vb* 檔案。</span><span class="sxs-lookup"><span data-stu-id="b8a66-140">Visual Studio creates the project and opens the *UnitTest1.vb* file in the code window.</span></span>

   ![單元測試專案類別和方法的 Visual Studio 程式碼視窗 - Visual Basic](./media/testing-library-with-visual-studio/vb-unit-test-editor-window.png)

   <span data-ttu-id="b8a66-142">單元測試範本建立的原始程式碼會執行下列動作︰</span><span class="sxs-lookup"><span data-stu-id="b8a66-142">The source code created by the unit test template does the following:</span></span>

   * <span data-ttu-id="b8a66-143">它會匯入 <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> 命名空間，其中包含用於單元測試的類型。</span><span class="sxs-lookup"><span data-stu-id="b8a66-143">It imports the <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=nameWithType> namespace, which contains the types used for unit testing.</span></span>

   * <span data-ttu-id="b8a66-144">它會將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>) 屬性套用至 `UnitTest1` 類別。</span><span class="sxs-lookup"><span data-stu-id="b8a66-144">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute>) attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="b8a66-145">執行單元測試時，在測試類別中標示 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性的每個測試方法都將自動執行。</span><span class="sxs-lookup"><span data-stu-id="b8a66-145">Each test method in a test class tagged with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute is executed automatically when the unit test is run.</span></span>

   * <span data-ttu-id="b8a66-146">它會套用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性，以將 `TestMethod1` 定義為在執行單元測試時自動執行的測試方法。</span><span class="sxs-lookup"><span data-stu-id="b8a66-146">It applies the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute to define `TestMethod1` as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="b8a66-147">在 **方案總管** 中，以滑鼠右鍵按一下 **StringLibraryTest** 專案的 **[相依性]** 節點，然後從內容功能表中選取 **[新增參考]** 。</span><span class="sxs-lookup"><span data-stu-id="b8a66-147">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   ![StringLibraryTest 相依性的內容功能表](./media/testing-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="b8a66-149">在 [參考管理員]  對話方塊中，展開 [專案]  節點並核取 [StringLibrary]  旁的方塊。</span><span class="sxs-lookup"><span data-stu-id="b8a66-149">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="b8a66-150">將參考新增至 `StringLibrary` 組件，可讓編譯器找出 **StringLibrary** 方法。</span><span class="sxs-lookup"><span data-stu-id="b8a66-150">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="b8a66-151">選取 [確定]  按鈕。</span><span class="sxs-lookup"><span data-stu-id="b8a66-151">Select the **OK** button.</span></span> <span data-ttu-id="b8a66-152">這會在您的類別庫專案 `StringLibrary` 中新增參考。</span><span class="sxs-lookup"><span data-stu-id="b8a66-152">This adds a reference to your class library project, `StringLibrary`.</span></span>

   ![Visual Studio 新增專案參考對話方塊 - Visual Basic](./media/testing-library-with-visual-studio/project-reference-manager.png)
---

## <a name="adding-and-running-unit-test-methods"></a><span data-ttu-id="b8a66-154">新增和執行單元測試方法</span><span class="sxs-lookup"><span data-stu-id="b8a66-154">Adding and running unit test methods</span></span>

<span data-ttu-id="b8a66-155">Visual Studio 執行單元測試時，會執行單元測試類別 (即套用 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> 屬性的類別) 中標示 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> 屬性的每個方法。</span><span class="sxs-lookup"><span data-stu-id="b8a66-155">When Visual Studio runs a unit test, it executes each method marked with the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestMethodAttribute> attribute in a unit test class, the class to which the  <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestClassAttribute> attribute is applied.</span></span> <span data-ttu-id="b8a66-156">測試方法會在發生第一次失敗時或方法中包含的所有測試均成功時結束。</span><span class="sxs-lookup"><span data-stu-id="b8a66-156">A test method ends when the first failure is encountered or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="b8a66-157">最常見的測試會呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 類別的成員。</span><span class="sxs-lookup"><span data-stu-id="b8a66-157">The most common tests call members of the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> class.</span></span> <span data-ttu-id="b8a66-158">許多判斷提示方法都至少包括兩個參數，一個是預期的測試結果，另一個是實際的測試結果。</span><span class="sxs-lookup"><span data-stu-id="b8a66-158">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="b8a66-159">它最常呼叫的一些方法如下表所示。</span><span class="sxs-lookup"><span data-stu-id="b8a66-159">Some of its most frequently called methods are shown in the table below.</span></span>

<span data-ttu-id="b8a66-160">Assert 方法</span><span class="sxs-lookup"><span data-stu-id="b8a66-160">Assert methods</span></span> | <span data-ttu-id="b8a66-161">功能</span><span class="sxs-lookup"><span data-stu-id="b8a66-161">Function</span></span>
--- | ---
`Assert.AreEqual` | <span data-ttu-id="b8a66-162">驗證兩個值或物件相等。</span><span class="sxs-lookup"><span data-stu-id="b8a66-162">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="b8a66-163">如果值或物件不相等，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="b8a66-163">The assert fails if the values or objects are not equal.</span></span>
`Assert.AreSame` | <span data-ttu-id="b8a66-164">驗證兩個物件變數參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="b8a66-164">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="b8a66-165">如果變數參考不同的物件，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="b8a66-165">The assert fails if the variables refer to different objects.</span></span>
`Assert.IsFalse` | <span data-ttu-id="b8a66-166">驗證條件為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b8a66-166">Verifies that a condition is `false`.</span></span> <span data-ttu-id="b8a66-167">如果條件為 `true`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="b8a66-167">The assert fails if the condition is `true`.</span></span>
`Assert.IsNotNull` | <span data-ttu-id="b8a66-168">驗證物件不是 `null`。</span><span class="sxs-lookup"><span data-stu-id="b8a66-168">Verifies that an object is not `null`.</span></span> <span data-ttu-id="b8a66-169">如果物件為 `null`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="b8a66-169">The assert fails if the object is `null`.</span></span>

<span data-ttu-id="b8a66-170">您也可以將 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> 屬性套用到測試方法。</span><span class="sxs-lookup"><span data-stu-id="b8a66-170">You can also apply the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> attribute to a test method.</span></span> <span data-ttu-id="b8a66-171">指出測試方法預期擲回的例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="b8a66-171">It indicates the type of exception a test method is expected to throw.</span></span> <span data-ttu-id="b8a66-172">如果沒有擲回指定的例外狀況，測試便會失敗。</span><span class="sxs-lookup"><span data-stu-id="b8a66-172">The test fails if the specified exception is not thrown.</span></span>

<span data-ttu-id="b8a66-173">在測試 `StringLibrary.StartsWithUpper` 方法時，您想提供幾個以大寫字元開頭的字串。</span><span class="sxs-lookup"><span data-stu-id="b8a66-173">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="b8a66-174">您預期此方法在這些情況下傳回 `true`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b8a66-174">You expect the method to return `true` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsTrue%2A> method.</span></span> <span data-ttu-id="b8a66-175">同樣地，您想提供幾個開頭不是大寫字元的字串。</span><span class="sxs-lookup"><span data-stu-id="b8a66-175">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="b8a66-176">您預期此方法在這些情況下傳回 `false`，因此您可以呼叫 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b8a66-176">You expect the method to return `false` in these cases, so you can call the <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.IsFalse%2A> method.</span></span>

<span data-ttu-id="b8a66-177">因為您的程式庫方法會處理字串，您也想確定它會成功處理[空字串 (`String.Empty`)](xref:System.String.Empty)，這是不包含任何字元且其 <xref:System.String.Length> 為 0 的有效字串和尚未初始化的 `null` 字串。</span><span class="sxs-lookup"><span data-stu-id="b8a66-177">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose <xref:System.String.Length> is 0, and a `null` string that has not been initialized.</span></span> <span data-ttu-id="b8a66-178">如果在 <xref:System.String> 執行個體上呼叫 `StartsWithUpper` 做為擴充方法，它將無法傳遞 `null` 字串。</span><span class="sxs-lookup"><span data-stu-id="b8a66-178">If `StartsWithUpper` is called as an extension method on a <xref:System.String> instance, it cannot be passed a `null` string.</span></span> <span data-ttu-id="b8a66-179">不過，您也可以將其作為靜態方法來直接呼叫，並傳遞單一 <xref:System.String> 引數。</span><span class="sxs-lookup"><span data-stu-id="b8a66-179">However, you can also call it directly as a static method and pass a single <xref:System.String> argument.</span></span>

<span data-ttu-id="b8a66-180">您會定義三個方法，每個方法會針對字串陣列中的每個項目重複呼叫其 <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> 方法。</span><span class="sxs-lookup"><span data-stu-id="b8a66-180">You'll define three methods, each of which calls its <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert> method repeatedly for each element in a string array.</span></span> <span data-ttu-id="b8a66-181">因為測試方法會在發生第一次失敗時立即失敗，您將呼叫一個方法多載，以便傳遞一個字串來指示在方法呼叫中使用的字串值。</span><span class="sxs-lookup"><span data-stu-id="b8a66-181">Because the test method fails as soon as it encounters the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="b8a66-182">建立測試方法：</span><span class="sxs-lookup"><span data-stu-id="b8a66-182">To create the test methods:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="b8a66-183">C#</span><span class="sxs-lookup"><span data-stu-id="b8a66-183">C#</span></span>](#tab/csharp) 
1. <span data-ttu-id="b8a66-184">在 *UnitTest1.cs* 程式碼視窗中，以下列程式碼取代程式碼：</span><span class="sxs-lookup"><span data-stu-id="b8a66-184">In the *UnitTest1.cs* code window, replace the code with the following code:</span></span>

   [!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]

   <span data-ttu-id="b8a66-185">請注意，您在 `TestStartsWithUpper` 方法中的大寫字元測試包含希臘文大寫字母 alpha (U+0391) 和斯拉夫文大寫字母 EM (U+041C)，`TestDoesNotStartWithUpper` 方法中的小寫字元測試包含希臘文小寫字母 alpha (U+03B1) 和斯拉夫文小寫字母 Ghe (U+0433)。</span><span class="sxs-lookup"><span data-stu-id="b8a66-185">Note that your test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C), and the test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="b8a66-186">在功能表列上，選取 [檔案]   >  [將 UnitTest1.cs As 另存為]  。</span><span class="sxs-lookup"><span data-stu-id="b8a66-186">On the menu bar, select **File** > **Save UnitTest1.cs As**.</span></span> <span data-ttu-id="b8a66-187">在 **[另存新檔]** 對話方塊中，選擇 **[儲存]** 按鈕旁的箭號，然後選擇 **[以編碼方式儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="b8a66-187">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   ![Visual Studio [另存新檔] 對話方塊 - C#](./media/testing-library-with-visual-studio/save-file-as-dialog.png)
# <a name="visual-basictabvb"></a>[<span data-ttu-id="b8a66-189">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b8a66-189">Visual Basic</span></span>](#tab/vb) 
1. <span data-ttu-id="b8a66-190">在 *UnitTest1.vb* 程式碼視窗中，以下列程式碼取代程式碼：</span><span class="sxs-lookup"><span data-stu-id="b8a66-190">In the *UnitTest1.vb* code window, replace the code with the following code:</span></span>

    [!CODE-vb[Test#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]

   <span data-ttu-id="b8a66-191">請注意，您在 `TestStartsWithUpper` 方法中的大寫字元測試包含希臘文大寫字母 alpha (U+0391) 和斯拉夫文大寫字母 EM (U+041C)，`TestDoesNotStartWithUpper` 方法中的小寫字元測試包含希臘文小寫字母 alpha (U+03B1) 和斯拉夫文小寫字母 Ghe (U+0433)。</span><span class="sxs-lookup"><span data-stu-id="b8a66-191">Note that your test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C), and the test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="b8a66-192">在功能表列上，選取 [檔案]   > [將 UnitTest1.vb 另存為]  。</span><span class="sxs-lookup"><span data-stu-id="b8a66-192">On the menu bar, select **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="b8a66-193">在 **[另存新檔]** 對話方塊中，選擇 **[儲存]** 按鈕旁的箭號，然後選擇 **[以編碼方式儲存]** 。</span><span class="sxs-lookup"><span data-stu-id="b8a66-193">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   ![Visual Studio [另存新檔] 對話方塊 - Visual Basic](./media/testing-library-with-visual-studio/save-file-as-dialog.png)
---

1. <span data-ttu-id="b8a66-195">在 **[確認另存新檔]** 對話方塊中，選擇 **[是]** 按鈕以儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="b8a66-195">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="b8a66-196">在 **[進階儲存選項]** 對話方塊的，選取 **[編碼]** 下拉式清單中選擇 **[Unicode (UTF-8 有簽章) - 字碼頁 65001]** ，然後選擇 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="b8a66-196">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   ![Visual Studio [進階儲存選項] 對話方塊](./media/testing-library-with-visual-studio/advanced-save-options.png)

   <span data-ttu-id="b8a66-198">如果您無法將您的原始程式碼儲存為 UTF8 編碼檔案，Visual Studio 可能會將它儲存為 ASCII 檔案。</span><span class="sxs-lookup"><span data-stu-id="b8a66-198">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="b8a66-199">發生該情況時，執行階段無法正確解碼 ASCII 範圍之外的 UTF8 字元，因此測試結果將不精確。</span><span class="sxs-lookup"><span data-stu-id="b8a66-199">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be accurate.</span></span>

1. <span data-ttu-id="b8a66-200">在功能表列上，選擇 **[測試]**  >  **[執行]**  >  **[所有測試]** 。</span><span class="sxs-lookup"><span data-stu-id="b8a66-200">On the menu bar, select **Test** > **Run** > **All Tests**.</span></span> <span data-ttu-id="b8a66-201">[測試總管]  視窗隨即開啟並顯示測試成功執行。</span><span class="sxs-lookup"><span data-stu-id="b8a66-201">The **Test Explorer** window opens and shows that the tests ran successfully.</span></span> <span data-ttu-id="b8a66-202">這三項測試都會列在 [通過的測試]  區段中，而 [摘要]  區段則報告測試回合的結果。</span><span class="sxs-lookup"><span data-stu-id="b8a66-202">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   ![測試總管視窗，其中包含通過的測試](./media/testing-library-with-visual-studio/test-explorer-window.png)

## <a name="handling-test-failures"></a><span data-ttu-id="b8a66-204">處理測試失敗</span><span class="sxs-lookup"><span data-stu-id="b8a66-204">Handling test failures</span></span>

<span data-ttu-id="b8a66-205">您的測試回合未失敗，但將它稍微變更，使其中一個測試方法失敗：</span><span class="sxs-lookup"><span data-stu-id="b8a66-205">Your test run had no failures, but change it slightly so that one of the test methods fails:</span></span>

1. <span data-ttu-id="b8a66-206">修改 `TestDoesNotStartWithUpper` 方法中的 `words` 陣列，以包含字串「錯誤」。</span><span class="sxs-lookup"><span data-stu-id="b8a66-206">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="b8a66-207">您不需要儲存檔案，因為當組建方案以執行測試時，Visual Studio 會自動儲存開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="b8a66-207">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```

1. <span data-ttu-id="b8a66-208">從功能表列中，選取 [測試]   >  [執行]   >  [所有測試]  來執行測試。</span><span class="sxs-lookup"><span data-stu-id="b8a66-208">Run the test by selecting **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="b8a66-209">[測試總管]  視窗表示兩個測試成功，而且有一項失敗。</span><span class="sxs-lookup"><span data-stu-id="b8a66-209">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   ![測試總管視窗，其中包含失敗的測試](./media/testing-library-with-visual-studio/failed-test-window.png)

1. <span data-ttu-id="b8a66-211">在 **[失敗的測試]** 區段中選擇失敗的測試 `TestDoesNotStartWith`。</span><span class="sxs-lookup"><span data-stu-id="b8a66-211">In the **Failed Tests** section, select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="b8a66-212">[測試總管]  視窗會顯示判斷提示產生的訊息："Assert.IsFalse failed.</span><span class="sxs-lookup"><span data-stu-id="b8a66-212">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="b8a66-213">Expected for 'Error': false; actual:True" (Assert.IsFalse 失敗。預期為 'Error'：false；實際為：True)。</span><span class="sxs-lookup"><span data-stu-id="b8a66-213">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="b8a66-214">因為發生失敗，陣列中 "Error" 之後的所有字串並未經過測試。</span><span class="sxs-lookup"><span data-stu-id="b8a66-214">Because of the failure, all strings in the array after "Error" were not tested.</span></span>

   ![[測試總管] 視窗顯示「為 False」的判斷提示失敗](./media/testing-library-with-visual-studio/failed-test-detail.png)

1. <span data-ttu-id="b8a66-216">復原您在步驟 1 中所做的修改，並移除字串 "Error"。</span><span class="sxs-lookup"><span data-stu-id="b8a66-216">Undo the modification you did in step 1 and remove the string "Error".</span></span> <span data-ttu-id="b8a66-217">重新執行該測試，測試將會通過。</span><span class="sxs-lookup"><span data-stu-id="b8a66-217">Rerun the test and the tests will pass.</span></span>

## <a name="testing-the-release-version-of-the-library"></a><span data-ttu-id="b8a66-218">測試程式庫的發行版本</span><span class="sxs-lookup"><span data-stu-id="b8a66-218">Testing the Release version of the library</span></span>

<span data-ttu-id="b8a66-219">您已針對偵錯版本的程式庫執行測試。</span><span class="sxs-lookup"><span data-stu-id="b8a66-219">You've been running your tests against the Debug version of the library.</span></span> <span data-ttu-id="b8a66-220">既然您的測試全部通過，並已充分測試過您的程式庫，您應針對程式庫的發行組建執行更多時間的測試。</span><span class="sxs-lookup"><span data-stu-id="b8a66-220">Now that your tests have all passed and you've adequately tested your library, you should run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="b8a66-221">許多因素 (包括編譯器最佳化) 有時會在偵錯和發行組建之間導致不同的行為。</span><span class="sxs-lookup"><span data-stu-id="b8a66-221">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="b8a66-222">測試發行組建︰</span><span class="sxs-lookup"><span data-stu-id="b8a66-222">To test the Release build:</span></span>

1. <span data-ttu-id="b8a66-223">在 Visual Studio 工具列中，將組建組態從 [偵錯]  變更為 [發行]  。</span><span class="sxs-lookup"><span data-stu-id="b8a66-223">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   ![醒目提示 [發行] 組建的 Visual Studio 工具列](./media/testing-library-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="b8a66-225">在 **方案總管** 中，以滑鼠右鍵按一下 **StringLibrary** 專案，然後從內容功能表中選取 **[組建]** 以重新編譯程式庫。</span><span class="sxs-lookup"><span data-stu-id="b8a66-225">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   ![StringLibrary 操作功能表和建置命令](./media/testing-library-with-visual-studio/build-library-context-menu.png)

1. <span data-ttu-id="b8a66-227">從功能表列中，選擇 [測試]   >  [執行]   >  [所有測試]  來執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="b8a66-227">Run the unit tests by choosing **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="b8a66-228">所有測試皆通過。</span><span class="sxs-lookup"><span data-stu-id="b8a66-228">The tests pass.</span></span>

<span data-ttu-id="b8a66-229">既然您已經完成程式庫測試，下一步是將它提供給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="b8a66-229">Now that you've finished testing your library, the next step is to make it available to callers.</span></span> <span data-ttu-id="b8a66-230">您可以將它與一或多個應用程式搭售，或是將將它發佈為 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="b8a66-230">You can bundle it with one or more applications, or you can distribute it as a NuGet package.</span></span> <span data-ttu-id="b8a66-231">如需詳細資訊，請參閱[使用 .NET Standard 類別庫](./consuming-library-with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="b8a66-231">For more information, see [Consuming a .NET Standard Class Library](./consuming-library-with-visual-studio.md).</span></span>
