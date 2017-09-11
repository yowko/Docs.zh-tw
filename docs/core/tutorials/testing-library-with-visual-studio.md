---
title: "在 Visual Studio 2017 中使用 .NET Core 測試類別庫"
description: "了解如何使用 Visual Studio 2017 測試以 C# 撰寫的類別庫"
keywords: ".NET Core, .NET 標準類別庫, Visual Studio 2017, 單元測試"
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 069ad711-3eaa-45c6-94d7-b40249cc8b99
ms.translationtype: HT
ms.sourcegitcommit: 3a25c1c3b540bac8ef963a8bbf708b0700c3e9e2
ms.openlocfilehash: 30e46ae97563add2bdf34948349cf2d6214d0de8
ms.contentlocale: zh-tw
ms.lasthandoff: 09/08/2017

---

# <a name="testing-a-class-library-with-net-core-in-visual-studio-2017"></a><span data-ttu-id="67c67-104">在 Visual Studio 2017 中使用 .NET Core 測試類別庫</span><span class="sxs-lookup"><span data-stu-id="67c67-104">Testing a class library with .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="67c67-105">於[在 Visual Studio 2017 中使用 C# 和 .NET Core 建置類別庫](library-with-visual-studio.md)或[在 Visual Studio 2017 中使用 Visual Basic 和 .NET Core 建置類別庫](vb-library-with-visual-studio.md)中，您建立了一個將擴充方法新增至 <xref:System.String> 類別的簡易類別庫。</span><span class="sxs-lookup"><span data-stu-id="67c67-105">In [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md) or [Building a class library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md), you created a simple class library that adds an extension method to the <xref:System.String> class.</span></span> <span data-ttu-id="67c67-106">現在您將建立單元測試，確定它如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="67c67-106">Now, you'll create a unit test to make sure that it works as expected.</span></span> <span data-ttu-id="67c67-107">您會將您的單元測試專案新增至上一個主題中所建立的方案。</span><span class="sxs-lookup"><span data-stu-id="67c67-107">You'll add your unit test project to the solution you created in the previous topic.</span></span>

## <a name="creating-a-unit-test-project"></a><span data-ttu-id="67c67-108">建立單元測試專案</span><span class="sxs-lookup"><span data-stu-id="67c67-108">Creating a unit test project</span></span>

<span data-ttu-id="67c67-109">若要建立單元測試專案，請執行下列作業︰</span><span class="sxs-lookup"><span data-stu-id="67c67-109">To create the unit test project, do the following:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="67c67-110">C#</span><span class="sxs-lookup"><span data-stu-id="67c67-110">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="67c67-111">在方案總管 中，開啟 **ClassLibraryProject** 方案節點的內容功能表，然後選取 [新增]  >  [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="67c67-111">In **Solution Explorer**, open the context menu for the **ClassLibraryProjects** solution node and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="67c67-112">在 [新增專案] 對話方塊中，選取 [Visual C#] 節點。</span><span class="sxs-lookup"><span data-stu-id="67c67-112">In the **Add New Project** dialog, select the **Visual C#** node.</span></span> <span data-ttu-id="67c67-113">然後選取後面跟著 [單元測試專案 (.NET Core)] 專案範本的 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="67c67-113">Then select the **.NET Core** node followed by the **Unit Test Project (.NET Core)** project template.</span></span> <span data-ttu-id="67c67-114">在 [名稱] 文字方塊中，輸入 "StringLibraryTest" 作為專案名稱。</span><span class="sxs-lookup"><span data-stu-id="67c67-114">In the **Name** text box, enter "StringLibraryTest" as the name of the project.</span></span> <span data-ttu-id="67c67-115">選取 [確定] 以建立單元測試專案。</span><span class="sxs-lookup"><span data-stu-id="67c67-115">Select **OK** to create the unit test project.</span></span>

   ![[新增專案] 對話方塊](./media/testing-library-with-visual-studio/testproject.png)

   > [!NOTE]  
   > <span data-ttu-id="67c67-117">除了單元測試專案之外，您也可以使用 Visual Studio 建立適用於 .NET Core 的 xUnit 測試專案。</span><span class="sxs-lookup"><span data-stu-id="67c67-117">In addition to a Unit Test project, you can also use Visual Studio to create an xUnit test project for .NET Core.</span></span>

1. <span data-ttu-id="67c67-118">Visual Studio 會建立專案，並在程式碼視窗中開啟 *UnitTest1.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="67c67-118">Visual Studio creates the project and opens the *UnitTest1.cs* file in the code window.</span></span>

   ![Visual Studio 程式碼視窗顯示預設的單元測試專案 UnitTest1 類別和 TestMethod1 方法](./media/testing-library-with-visual-studio/unittestwindow.png)

   <span data-ttu-id="67c67-120">單元測試範本建立的原始程式碼會執行下列動作︰</span><span class="sxs-lookup"><span data-stu-id="67c67-120">The source code created by the unit test template does the following:</span></span>

   * <span data-ttu-id="67c67-121">它會匯入 [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) 命名空間，其中包含用於單元測試的類型。</span><span class="sxs-lookup"><span data-stu-id="67c67-121">It imports the [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) namespace, which contains the types used for unit testing.</span></span>

   * <span data-ttu-id="67c67-122">它會將 [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) 屬性套用至 `UnitTest1` 類別。</span><span class="sxs-lookup"><span data-stu-id="67c67-122">It applies the [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="67c67-123">執行單元測試時，在測試類別中標示 \[TestMethod\] 屬性的每個測試方法都將自動執行。</span><span class="sxs-lookup"><span data-stu-id="67c67-123">Each test method in a test class tagged with the \[TestMethod\] attribute is executed automatically when the unit test is run.</span></span>

   * <span data-ttu-id="67c67-124">它會套用 [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) 屬性，以將 `TestMethod1` 定義為在執行單元測試時自動執行的測試方法。</span><span class="sxs-lookup"><span data-stu-id="67c67-124">It applies the [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) attribute to define `TestMethod1` as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="67c67-125">在方案總管 中，以滑鼠右鍵按一下 **StringLibraryTest** 專案的 [相依性] 節點，然後從內容功能表中選取 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="67c67-125">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   ![StringLibraryTest 相依性的內容功能表](./media/testing-library-with-visual-studio/addreference.png)

1. <span data-ttu-id="67c67-127">在 [參考管理員] 對話方塊中，展開 [專案] 節點並核取 [StringLibrary] 旁的方塊。</span><span class="sxs-lookup"><span data-stu-id="67c67-127">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="67c67-128">將參考新增至 `StringLibrary` 組件，可讓編譯器找出 **StringLibrary** 方法。</span><span class="sxs-lookup"><span data-stu-id="67c67-128">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="67c67-129">選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="67c67-129">Select the **OK** button.</span></span> <span data-ttu-id="67c67-130">這會在您的類別庫專案 `StringLibrary` 中新增參考。</span><span class="sxs-lookup"><span data-stu-id="67c67-130">This adds a reference to your class library project, `StringLibrary`.</span></span>

   ![參考管理員](./media/testing-library-with-visual-studio/referencemanager.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="67c67-132">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="67c67-132">Visual Basic</span></span>](#tab/visual-basic) 
1. <span data-ttu-id="67c67-133">在方案總管 中，開啟 **ClassLibraryProject** 方案節點的內容功能表，然後選取 [新增]  >  [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="67c67-133">In **Solution Explorer**, open the context menu for the **ClassLibraryProjects** solution node and select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="67c67-134">在 [新增專案] 對話方塊中，選取 [Visual Basic] 節點。</span><span class="sxs-lookup"><span data-stu-id="67c67-134">In the **Add New Project** dialog, select the **Visual Basic** node.</span></span> <span data-ttu-id="67c67-135">然後選取後面跟著 [單元測試專案 (.NET Core)] 專案範本的 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="67c67-135">Then select the **.NET Core** node followed by the **Unit Test Project (.NET Core)** project template.</span></span> <span data-ttu-id="67c67-136">在 [名稱] 文字方塊中，輸入 "StringLibraryTest" 作為專案名稱。</span><span class="sxs-lookup"><span data-stu-id="67c67-136">In the **Name** text box, enter "StringLibraryTest" as the name of the project.</span></span> <span data-ttu-id="67c67-137">選取 [確定] 以建立單元測試專案。</span><span class="sxs-lookup"><span data-stu-id="67c67-137">Select **OK** to create the unit test project.</span></span>

   ![[新增專案] 對話方塊](./media/testing-library-with-visual-studio/vb-testproject.png)

   > [!NOTE]  
   > <span data-ttu-id="67c67-139">除了單元測試專案之外，您也可以使用 Visual Studio 建立適用於 .NET Core 的 xUnit 測試專案。</span><span class="sxs-lookup"><span data-stu-id="67c67-139">In addition to a Unit Test project, you can also use Visual Studio to create an xUnit test project for .NET Core.</span></span>

1. <span data-ttu-id="67c67-140">Visual Studio 會建立專案，並在程式碼視窗中開啟 *UnitTest1.vb* 檔案。</span><span class="sxs-lookup"><span data-stu-id="67c67-140">Visual Studio creates the project and opens the *UnitTest1.vb* file in the code window.</span></span>

   ![Visual Studio 程式碼視窗顯示預設的單元測試專案 UnitTest1 類別和 TestMethod1 方法](./media/testing-library-with-visual-studio/vb-unittestwindow.png)

   <span data-ttu-id="67c67-142">單元測試範本建立的原始程式碼會執行下列動作︰</span><span class="sxs-lookup"><span data-stu-id="67c67-142">The source code created by the unit test template does the following:</span></span>

   * <span data-ttu-id="67c67-143">它會匯入 [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) 命名空間，其中包含用於單元測試的類型。</span><span class="sxs-lookup"><span data-stu-id="67c67-143">It imports the [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx) namespace, which contains the types used for unit testing.</span></span>

   * <span data-ttu-id="67c67-144">它會將 [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) 屬性套用至 `UnitTest1` 類別。</span><span class="sxs-lookup"><span data-stu-id="67c67-144">It applies the [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) attribute to the `UnitTest1` class.</span></span> <span data-ttu-id="67c67-145">執行單元測試時，在測試類別中標示 \[TestMethod\] 屬性的每個測試方法都將自動執行。</span><span class="sxs-lookup"><span data-stu-id="67c67-145">Each test method in a test class tagged with the \[TestMethod\] attribute is executed automatically when the unit test is run.</span></span>

   * <span data-ttu-id="67c67-146">它會套用 [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) 屬性，以將 `TestMethod1` 定義為在執行單元測試時自動執行的測試方法。</span><span class="sxs-lookup"><span data-stu-id="67c67-146">It applies the [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) attribute to define `TestMethod1` as a test method for automatic execution when the unit test is run.</span></span>

1. <span data-ttu-id="67c67-147">在方案總管 中，以滑鼠右鍵按一下 **StringLibraryTest** 專案的 [相依性] 節點，然後從內容功能表中選取 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="67c67-147">In **Solution Explorer**, right-click the **Dependencies** node of the **StringLibraryTest** project and select **Add Reference** from the context menu.</span></span>

   ![StringLibraryTest 相依性的內容功能表](./media/testing-library-with-visual-studio/addreference.png)

1. <span data-ttu-id="67c67-149">在 [參考管理員] 對話方塊中，展開 [專案] 節點並核取 [StringLibrary] 旁的方塊。</span><span class="sxs-lookup"><span data-stu-id="67c67-149">In the **Reference Manager** dialog, expand the **Projects** node and check the box next to **StringLibrary**.</span></span> <span data-ttu-id="67c67-150">將參考新增至 `StringLibrary` 組件，可讓編譯器找出 **StringLibrary** 方法。</span><span class="sxs-lookup"><span data-stu-id="67c67-150">Adding a reference to the `StringLibrary` assembly allows the compiler to find **StringLibrary** methods.</span></span> <span data-ttu-id="67c67-151">選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="67c67-151">Select the **OK** button.</span></span> <span data-ttu-id="67c67-152">這會在您的類別庫專案 `StringLibrary` 中新增參考。</span><span class="sxs-lookup"><span data-stu-id="67c67-152">This adds a reference to your class library project, `StringLibrary`.</span></span>

   ![參考管理員](./media/testing-library-with-visual-studio/referencemanager.png)
---

## <a name="adding-and-running-unit-test-methods"></a><span data-ttu-id="67c67-154">新增和執行單元測試方法</span><span class="sxs-lookup"><span data-stu-id="67c67-154">Adding and running unit test methods</span></span>

<span data-ttu-id="67c67-155">Visual Studio 執行單元測試時，它會執行單元測試類別 (即套用 [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) 屬性的類別) 中標示 [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) 屬性的每個方法。</span><span class="sxs-lookup"><span data-stu-id="67c67-155">When Visual Studio runs a unit test, it executes each method marked with the [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) attribute in a unit test class, the class to which the  [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) attribute is applied.</span></span> <span data-ttu-id="67c67-156">測試方法會在發生第一次失敗時或方法中包含的所有測試均成功時結束。</span><span class="sxs-lookup"><span data-stu-id="67c67-156">A test method ends when the first failure is encountered or when all tests contained in the method have succeeded.</span></span>

<span data-ttu-id="67c67-157">最常見的測試會呼叫 [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) 類別的成員。</span><span class="sxs-lookup"><span data-stu-id="67c67-157">The most common tests call members of the [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) class.</span></span> <span data-ttu-id="67c67-158">許多判斷提示方法都至少包括兩個參數，一個是預期的測試結果，另一個是實際的測試結果。</span><span class="sxs-lookup"><span data-stu-id="67c67-158">Many assert methods include at least two parameters, one of which is the expected test result and the other of which is the actual test result.</span></span> <span data-ttu-id="67c67-159">它最常呼叫的一些方法如下表所示。</span><span class="sxs-lookup"><span data-stu-id="67c67-159">Some of its most frequently called methods are shown in the table below.</span></span>

<span data-ttu-id="67c67-160">Assert 方法</span><span class="sxs-lookup"><span data-stu-id="67c67-160">Assert methods</span></span> | <span data-ttu-id="67c67-161">函式</span><span class="sxs-lookup"><span data-stu-id="67c67-161">Function</span></span>
--- | ---
`Assert.AreEqual` | <span data-ttu-id="67c67-162">驗證兩個值或物件相等。</span><span class="sxs-lookup"><span data-stu-id="67c67-162">Verifies that two values or objects are equal.</span></span> <span data-ttu-id="67c67-163">如果值或物件不相等，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="67c67-163">The assert fails if the values or objects are not equal.</span></span>
`Assert.AreSame` | <span data-ttu-id="67c67-164">驗證兩個物件變數參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="67c67-164">Verifies that two object variables refer to the same object.</span></span> <span data-ttu-id="67c67-165">如果變數參考不同的物件，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="67c67-165">The assert fails if the variables refer to different objects.</span></span>
`Assert.IsFalse` | <span data-ttu-id="67c67-166">驗證條件為 `false`。</span><span class="sxs-lookup"><span data-stu-id="67c67-166">Verifies that a condition is `false`.</span></span> <span data-ttu-id="67c67-167">如果條件為 `true`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="67c67-167">The assert fails if the condition is `true`.</span></span>
`Assert.IsNotNull` | <span data-ttu-id="67c67-168">驗證物件不是 `null`。</span><span class="sxs-lookup"><span data-stu-id="67c67-168">Verifies that an object is not `null`.</span></span> <span data-ttu-id="67c67-169">如果物件為 `null`，判斷提示就會失敗。</span><span class="sxs-lookup"><span data-stu-id="67c67-169">The assert fails if the object is `null`.</span></span>

<span data-ttu-id="67c67-170">您也可以將 [\[ExpectedException\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.expectedexceptionattribute.aspx) 屬性套用到測試方法。</span><span class="sxs-lookup"><span data-stu-id="67c67-170">You can also apply the [\[ExpectedException\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.expectedexceptionattribute.aspx) attribute to a test method.</span></span> <span data-ttu-id="67c67-171">指出測試方法預期擲回的例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="67c67-171">It indicates the type of exception a test method is expected to throw.</span></span> <span data-ttu-id="67c67-172">如果沒有擲回指定的例外狀況，測試便會失敗。</span><span class="sxs-lookup"><span data-stu-id="67c67-172">The test fails if the specified exception is not thrown.</span></span>

<span data-ttu-id="67c67-173">在測試 `StringLibrary.StartsWithUpper` 方法時，您想提供幾個以大寫字元開頭的字串。</span><span class="sxs-lookup"><span data-stu-id="67c67-173">In testing the `StringLibrary.StartsWithUpper` method, you want to provide a number of strings that begin with an uppercase character.</span></span> <span data-ttu-id="67c67-174">您預期此方法在這些情況下傳回 `true`，因此您可以呼叫 [Assert.IsTrue (布林值,字串)](https://msdn.microsoft.com/library/ms243754.aspx) 方法。</span><span class="sxs-lookup"><span data-stu-id="67c67-174">You expect the method to return `true` in these cases, so you can call the [Assert.IsTrue(Boolean, String)](https://msdn.microsoft.com/library/ms243754.aspx) method.</span></span> <span data-ttu-id="67c67-175">同樣地，您想提供幾個開頭不是大寫字元的字串。</span><span class="sxs-lookup"><span data-stu-id="67c67-175">Similarly, you want to provide a number of strings that begin with something other than an uppercase character.</span></span> <span data-ttu-id="67c67-176">您預期此方法在這些情況下傳回 `false`，因此您可以呼叫 [Assert.IsFalse (布林值,字串)](https://msdn.microsoft.com/library/ms243805.aspx) 方法。</span><span class="sxs-lookup"><span data-stu-id="67c67-176">You expect the method to return `false` in these cases, so you can call the [Assert.IsFalse(Boolean, String)](https://msdn.microsoft.com/library/ms243805.aspx) method.</span></span>

<span data-ttu-id="67c67-177">因為您的程式庫方法會處理字串，您也想確定它會成功處理[空字串 (`String.Empty`)](xref:System.String.Empty)，這是不包含任何字元且其 @System.String.Length 為 0 的有效字串和尚未初始化的 `null` 字串。</span><span class="sxs-lookup"><span data-stu-id="67c67-177">Since your library method handles strings, you also want to make sure that it successfully handles an [empty string (`String.Empty`)](xref:System.String.Empty), a valid string that has no characters and whose @System.String.Length is 0, and a `null` string that has not been initialized.</span></span> <span data-ttu-id="67c67-178">如果在 @System.String 執行個體上呼叫 `StartsWithUpper` 做為擴充方法，它將無法傳遞 `null` 字串。</span><span class="sxs-lookup"><span data-stu-id="67c67-178">If `StartsWithUpper` is called as an extension method on a @System.String instance, it cannot be passed a `null` string.</span></span> <span data-ttu-id="67c67-179">不過，您也可以將其作為靜態方法來直接呼叫，並傳遞單一 @System.String 引數。</span><span class="sxs-lookup"><span data-stu-id="67c67-179">However, you can also call it directly as a static method and pass a single @System.String argument.</span></span>

<span data-ttu-id="67c67-180">您會定義三個方法，每個方法會針對字串陣列中的每個項目重複呼叫其 [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) 方法。</span><span class="sxs-lookup"><span data-stu-id="67c67-180">You'll define three methods, each of which calls its [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) method repeatedly for each element in a string array.</span></span> <span data-ttu-id="67c67-181">因為測試方法會在發生第一次失敗時立即失敗，您將呼叫一個方法多載，以便傳遞一個字串來指示在方法呼叫中使用的字串值。</span><span class="sxs-lookup"><span data-stu-id="67c67-181">Because the test method fails as soon as it encounters the first failure, you'll call a method overload that allows you to pass a string that indicates the string value used in the method call.</span></span>

<span data-ttu-id="67c67-182">建立測試方法：</span><span class="sxs-lookup"><span data-stu-id="67c67-182">To create the test methods:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="67c67-183">C#</span><span class="sxs-lookup"><span data-stu-id="67c67-183">C#</span></span>](#tab/csharp) 
1. <span data-ttu-id="67c67-184">在 *UnitTest1.cs* 程式碼視窗中，以下列程式碼取代程式碼：</span><span class="sxs-lookup"><span data-stu-id="67c67-184">In the *UnitTest1.cs* code window, replace the code with the following code:</span></span>

   <span data-ttu-id="67c67-185">[!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]</span><span class="sxs-lookup"><span data-stu-id="67c67-185">[!CODE-csharp[Test#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs)]</span></span>

   <span data-ttu-id="67c67-186">請注意，您在 `TestStartsWithUpper` 方法中的大寫字元測試包含希臘文大寫字母 alpha (U+0391) 和斯拉夫文大寫字母 EM (U+041C)，`TestDoesNotStartWithUpper` 方法中的小寫字元測試包含希臘文小寫字母 alpha (U+03B1) 和斯拉夫文小寫字母 Ghe (U+0433)。</span><span class="sxs-lookup"><span data-stu-id="67c67-186">Note that your test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C), and the test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="67c67-187">在功能表列上，選取 [檔案] >  [將 UnitTest1.cs As 另存為]。</span><span class="sxs-lookup"><span data-stu-id="67c67-187">On the menu bar, select **File** > **Save UnitTest1.cs As**.</span></span> <span data-ttu-id="67c67-188">在 [另存新檔] 對話方塊中，選取 [儲存] 按鈕旁的箭號，然後選取 [以編碼方式儲存]*。</span><span class="sxs-lookup"><span data-stu-id="67c67-188">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   ![[另存新檔] 對話方塊](./media/testing-library-with-visual-studio/savefileas.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="67c67-190">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="67c67-190">Visual Basic</span></span>](#tab/visual-basic) 
1. <span data-ttu-id="67c67-191">在 *UnitTest1.vb* 程式碼視窗中，以下列程式碼取代程式碼：</span><span class="sxs-lookup"><span data-stu-id="67c67-191">In the *UnitTest1.vb* code window, replace the code with the following code:</span></span>

    <span data-ttu-id="67c67-192">[!CODE-vb[Test#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]</span><span class="sxs-lookup"><span data-stu-id="67c67-192">[!CODE-vb[Test#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/testlib.vb)]</span></span>

   <span data-ttu-id="67c67-193">請注意，您在 `TestStartsWithUpper` 方法中的大寫字元測試包含希臘文大寫字母 alpha (U+0391) 和斯拉夫文大寫字母 EM (U+041C)，`TestDoesNotStartWithUpper` 方法中的小寫字元測試包含希臘文小寫字母 alpha (U+03B1) 和斯拉夫文小寫字母 Ghe (U+0433)。</span><span class="sxs-lookup"><span data-stu-id="67c67-193">Note that your test of uppercase characters in the `TestStartsWithUpper` method includes the Greek capital letter alpha (U+0391) and the Cyrillic capital letter EM (U+041C), and the test of lowercase characters in the `TestDoesNotStartWithUpper` method includes the Greek small letter alpha (U+03B1) and the Cyrillic small letter Ghe (U+0433).</span></span>

1. <span data-ttu-id="67c67-194">在功能表列上，選取 [檔案] > [將 UnitTest1.vb 另存為]。</span><span class="sxs-lookup"><span data-stu-id="67c67-194">On the menu bar, select **File** > **Save UnitTest1.vb As**.</span></span> <span data-ttu-id="67c67-195">在 [另存新檔] 對話方塊中，選取 [儲存] 按鈕旁的箭號，然後選取 [以編碼方式儲存]*。</span><span class="sxs-lookup"><span data-stu-id="67c67-195">In the **Save File As** dialog, select the arrow beside the **Save** button, and select **Save with Encoding**.</span></span>

   ![[另存新檔] 對話方塊](./media/testing-library-with-visual-studio/savefileas.png)
---

1. <span data-ttu-id="67c67-197">在 [確認另存新檔] 對話方塊中，選取 [是] 按鈕以儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="67c67-197">In the **Confirm Save As** dialog, select the **Yes** button to save the file.</span></span>

1. <span data-ttu-id="67c67-198">在 [進階儲存選項] 對話方塊中，選取 [編碼] 下拉式清單中的 [Unicode (UTF-8 有簽章) - 字碼頁 65001]，然後選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="67c67-198">In the **Advanced Save Options** dialog, select **Unicode (UTF-8 with signature) - Codepage 65001** from the **Encoding** drop-down list and select **OK**.</span></span>

   ![[進階儲存選項] 對話方塊](./media/testing-library-with-visual-studio/advancedsaveoptions.png)

   <span data-ttu-id="67c67-200">如果您無法將您的原始程式碼儲存為 UTF8 編碼檔案，Visual Studio 可能會將它儲存為 ASCII 檔案。</span><span class="sxs-lookup"><span data-stu-id="67c67-200">If you fail to save your source code as a UTF8-encoded file, Visual Studio may save it as an ASCII file.</span></span> <span data-ttu-id="67c67-201">發生該情況時，執行階段無法正確解碼 ASCII 範圍之外的 UTF8 字元，因此測試結果將不精確。</span><span class="sxs-lookup"><span data-stu-id="67c67-201">When that happens, the runtime doesn't accurately decode the UTF8 characters outside of the ASCII range, and the test results won't be accurate.</span></span>

1. <span data-ttu-id="67c67-202">在功能表列中，選取 [測試]  >  [執行]  >  [所有測試]。</span><span class="sxs-lookup"><span data-stu-id="67c67-202">On the menu bar, select **Test** > **Run** > **All Tests**.</span></span> <span data-ttu-id="67c67-203">[測試總管] 視窗隨即開啟並顯示測試成功執行。</span><span class="sxs-lookup"><span data-stu-id="67c67-203">The **Test Explorer** window opens and shows that the tests ran successfully.</span></span> <span data-ttu-id="67c67-204">這三項測試都會列在 [通過的測試] 區段中，而 [摘要] 區段則報告測試回合的結果。</span><span class="sxs-lookup"><span data-stu-id="67c67-204">The three tests are listed in the **Passed Tests** section, and the **Summary** section reports the result of the test run.</span></span>

   ![[測試總管] 視窗](./media/testing-library-with-visual-studio/firsttest.png)

## <a name="handling-test-failures"></a><span data-ttu-id="67c67-206">處理測試失敗</span><span class="sxs-lookup"><span data-stu-id="67c67-206">Handling test failures</span></span>

<span data-ttu-id="67c67-207">您的測試回合未失敗，但將它稍微變更，使其中一個測試方法失敗：</span><span class="sxs-lookup"><span data-stu-id="67c67-207">Your test run had no failures, but change it slightly so that one of the test methods fails:</span></span>

1. <span data-ttu-id="67c67-208">修改 `TestDoesNotStartWithUpper` 方法中的 `words` 陣列，以包含字串「錯誤」。</span><span class="sxs-lookup"><span data-stu-id="67c67-208">Modify the `words` array in the `TestDoesNotStartWithUpper` method to include the string "Error".</span></span> <span data-ttu-id="67c67-209">您不需要儲存檔案，因為當組建方案以執行測試時，Visual Studio 會自動儲存開啟的檔案。</span><span class="sxs-lookup"><span data-stu-id="67c67-209">You don't need to save the file because Visual Studio automatically saves open files when a solution is built to run tests.</span></span>

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```
   ```vb
   Dim words() As String = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " }

   ```
1. <span data-ttu-id="67c67-210">從功能表列中，選取 [測試]  >  [執行]  >  [所有測試] 來執行測試。</span><span class="sxs-lookup"><span data-stu-id="67c67-210">Run the test by selecting **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="67c67-211">[測試總管] 視窗表示兩個測試成功，而且有一項失敗。</span><span class="sxs-lookup"><span data-stu-id="67c67-211">The **Test Explorer** window indicates that two tests succeeded and one failed.</span></span>

   ![[測試總管] 視窗](./media/testing-library-with-visual-studio/failedtest.png)

1. <span data-ttu-id="67c67-213">在 [失敗的測試] 區段中，選取失敗的測試 `TestDoesNotStartWith`。</span><span class="sxs-lookup"><span data-stu-id="67c67-213">In the **Failed Tests** section, select the failed test, `TestDoesNotStartWith`.</span></span> <span data-ttu-id="67c67-214">[測試總管] 視窗會顯示判斷提示產生的訊息：「Assert.IsFalse 失敗。</span><span class="sxs-lookup"><span data-stu-id="67c67-214">The **Test Explorer** window displays the message produced by the assert: "Assert.IsFalse failed.</span></span> <span data-ttu-id="67c67-215">'Error' 的預期︰false；實際：True」。</span><span class="sxs-lookup"><span data-stu-id="67c67-215">Expected for 'Error': false; actual: True".</span></span> <span data-ttu-id="67c67-216">因為發生失敗，陣列中 "Error" 之後的所有字串並未經過測試。</span><span class="sxs-lookup"><span data-stu-id="67c67-216">Because of the failure, all strings in the array after "Error" were not tested.</span></span>

   ![[測試總管] 視窗顯示「為 False」的判斷提示失敗](./media/testing-library-with-visual-studio/failedtestdetail.png)

1. <span data-ttu-id="67c67-218">移除已新增的程式碼 (`"Error", `)，然後重新執行測試。</span><span class="sxs-lookup"><span data-stu-id="67c67-218">Remove the code that you added (`"Error", `) and rerun the test.</span></span> <span data-ttu-id="67c67-219">測試將通過。</span><span class="sxs-lookup"><span data-stu-id="67c67-219">The tests will pass.</span></span>

## <a name="testing-the-release-version-of-the-library"></a><span data-ttu-id="67c67-220">測試程式庫的發行版本</span><span class="sxs-lookup"><span data-stu-id="67c67-220">Testing the Release version of the library</span></span>

<span data-ttu-id="67c67-221">您已針對偵錯版本的程式庫執行測試。</span><span class="sxs-lookup"><span data-stu-id="67c67-221">You've been running your tests against the Debug version of the library.</span></span> <span data-ttu-id="67c67-222">既然您的測試全部通過，並已充分測試過您的程式庫，您應針對程式庫的發行組建執行更多時間的測試。</span><span class="sxs-lookup"><span data-stu-id="67c67-222">Now that your tests have all passed and you've adequately tested your library, you should run the tests an additional time against the Release build of the library.</span></span> <span data-ttu-id="67c67-223">許多因素 (包括編譯器最佳化) 有時會在偵錯和發行組建之間導致不同的行為。</span><span class="sxs-lookup"><span data-stu-id="67c67-223">A number of factors, including compiler optimizations, can sometimes produce different behavior between Debug and Release builds.</span></span>

<span data-ttu-id="67c67-224">測試發行組建︰</span><span class="sxs-lookup"><span data-stu-id="67c67-224">To test the Release build:</span></span>

1. <span data-ttu-id="67c67-225">在 Visual Studio 工具列中，將組建組態從 [偵錯] 變更為 [發行]。</span><span class="sxs-lookup"><span data-stu-id="67c67-225">In the Visual Studio toolbar, change the build configuration from **Debug** to **Release**.</span></span>

   ![Visual Studio 工具列](./media/testing-library-with-visual-studio/toolbar.png)

1. <span data-ttu-id="67c67-227">在方案總管 中，以滑鼠右鍵按一下 **StringLibrary** 專案，然後從內容功能表中選取 [組建] 以重新編譯程式庫。</span><span class="sxs-lookup"><span data-stu-id="67c67-227">In **Solution Explorer**, right-click the **StringLibrary** project and select **Build** from the context menu to recompile the library.</span></span>

   ![StringLibrary 內容功能表](./media/testing-library-with-visual-studio/buildlibrary.png)

1. <span data-ttu-id="67c67-229">從功能表列中，選擇 [測試]  >  [執行]  >  [所有測試] 來執行單元測試。</span><span class="sxs-lookup"><span data-stu-id="67c67-229">Run the unit tests by choosing **Test** > **Run** > **All Tests** from the menu bar.</span></span> <span data-ttu-id="67c67-230">所有測試皆通過。</span><span class="sxs-lookup"><span data-stu-id="67c67-230">The tests pass.</span></span>

<span data-ttu-id="67c67-231">既然您已經完成程式庫測試，下一步是將它提供給呼叫端。</span><span class="sxs-lookup"><span data-stu-id="67c67-231">Now that you've finished testing your library, the next step is to make it available to callers.</span></span> <span data-ttu-id="67c67-232">您可以將它與一或多個應用程式搭售，或是將將它發佈為 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="67c67-232">You can bundle it with one or more applications, or you can distribute it as a NuGet package.</span></span> <span data-ttu-id="67c67-233">如需詳細資訊，請參閱[使用 .NET Standard 類別庫](./consuming-library-with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="67c67-233">For more information, see [Consuming a .NET Standard Class Library](./consuming-library-with-visual-studio.md).</span></span>

