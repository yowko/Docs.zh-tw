---
title: 在視覺化工作室中構建 .NET 標準類庫
description: 瞭解如何使用 Visual Studio 構建以 C# 或視覺化基本編寫的 .NET 標準類庫
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 748a1499e0c3a4a41613a69b715dbcfbd585bfe3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714012"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="93818-103">在視覺化工作室中構建 .NET 標準庫</span><span class="sxs-lookup"><span data-stu-id="93818-103">Build a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="93818-104">「類別庫」\*\* 會定義應用程式所呼叫的類型和方法。</span><span class="sxs-lookup"><span data-stu-id="93818-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="93818-105">以 .NET 標準 2.0 為目標的類庫允許支援 .NET 標準版本的任何 .NET 實現調用庫。</span><span class="sxs-lookup"><span data-stu-id="93818-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="93818-106">當您完成類別庫時，您可以決定要將它散發為協力廠商元件，還是要將它併入作為一或多個應用程式隨附的元件。</span><span class="sxs-lookup"><span data-stu-id="93818-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="93818-107">有關 .NET 標準版本及其支援的平臺的清單，請參閱[.NET 標準](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="93818-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="93818-108">在本主題中，您將建立含有單一字串處理方法的簡單公用程式類別庫。</span><span class="sxs-lookup"><span data-stu-id="93818-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="93818-109">您將它實作為[擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)，以便可以如同 <xref:System.String> 類別的成員一般來進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="93818-109">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="93818-110">創建視覺化工作室解決方案</span><span class="sxs-lookup"><span data-stu-id="93818-110">Create a Visual Studio solution</span></span>

<span data-ttu-id="93818-111">首先創建一個空白解決方案來放入類庫專案。</span><span class="sxs-lookup"><span data-stu-id="93818-111">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="93818-112">Visual Studio 解決方案用作一個或多個專案的容器。</span><span class="sxs-lookup"><span data-stu-id="93818-112">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="93818-113">如果繼續教程系列，您將向同一解決方案添加其他相關專案。</span><span class="sxs-lookup"><span data-stu-id="93818-113">You'll add additional, related projects to the same solution if you continue on with the tutorial series.</span></span>

<span data-ttu-id="93818-114">要創建空白解決方案，</span><span class="sxs-lookup"><span data-stu-id="93818-114">To create the blank solution:</span></span>

1. <span data-ttu-id="93818-115">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="93818-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="93818-116">在啟動視窗中，選擇 **"創建新專案**"。</span><span class="sxs-lookup"><span data-stu-id="93818-116">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="93818-117">在"**創建新專案**"頁上，在搜索框中輸入**解決方案**。</span><span class="sxs-lookup"><span data-stu-id="93818-117">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="93818-118">選擇 **"空白解決方案"** 範本，然後選擇 **"下一步**"。</span><span class="sxs-lookup"><span data-stu-id="93818-118">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Visual Studio 中的空白方案範本](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="93818-120">在"**配置新專案**"頁上，在 **"專案名稱**"框中輸入**類庫專案**。</span><span class="sxs-lookup"><span data-stu-id="93818-120">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="93818-121">然後，選擇 **"創建**"。</span><span class="sxs-lookup"><span data-stu-id="93818-121">Then, choose **Create**.</span></span>

> [!TIP]
> <span data-ttu-id="93818-122">您還可以跳過此步驟，讓 Visual Studio 在下一步中創建專案時為您創建解決方案。</span><span class="sxs-lookup"><span data-stu-id="93818-122">You can also skip this step and let Visual Studio create the solution for you when you create the project in the next step.</span></span> <span data-ttu-id="93818-123">在 **"配置新專案**"頁上查找解決方案選項。</span><span class="sxs-lookup"><span data-stu-id="93818-123">Look for the solution options on the **Configure your new project** page.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="93818-124">建立類別庫專案</span><span class="sxs-lookup"><span data-stu-id="93818-124">Create a class library project</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="93818-125">C#</span><span class="sxs-lookup"><span data-stu-id="93818-125">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="93818-126">向解決方案添加新的 C# .NET 標準類庫專案，稱為"StringLibrary"。</span><span class="sxs-lookup"><span data-stu-id="93818-126">Add a new C# .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="93818-127">按右鍵**解決方案資源管理器**中的解決方案，然後選擇"**添加新** > **專案**"。</span><span class="sxs-lookup"><span data-stu-id="93818-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="93818-128">在"**添加新專案**"頁上，在搜索框中輸入**庫**。</span><span class="sxs-lookup"><span data-stu-id="93818-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="93818-129">從"語言"清單中選擇**C#，** 然後從"平臺"清單中選擇 **"所有平臺**"。</span><span class="sxs-lookup"><span data-stu-id="93818-129">Choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="93818-130">選擇**類庫 （.NET 標準）** 範本，然後選擇 **"下一步**"。</span><span class="sxs-lookup"><span data-stu-id="93818-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="93818-131">在"**配置新專案**"頁上，在 **"專案名稱**"框中輸入**字串庫**。</span><span class="sxs-lookup"><span data-stu-id="93818-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="93818-132">然後，選擇 **"創建**"。</span><span class="sxs-lookup"><span data-stu-id="93818-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="93818-133">檢查以確保庫面向正確的版本 .NET 標準。</span><span class="sxs-lookup"><span data-stu-id="93818-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="93818-134">按右鍵**解決方案資源管理器**中的庫專案，然後選擇**屬性**。</span><span class="sxs-lookup"><span data-stu-id="93818-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="93818-135">"**目標框架**"文字方塊顯示專案目標 .NET 標準 2.0。</span><span class="sxs-lookup"><span data-stu-id="93818-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![類別庫的專案屬性](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="93818-137">以下列程式碼取代程式碼視窗中的程式碼，並儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="93818-137">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="93818-138">類庫`UtilityLibraries.StringLibrary`包含名為 的方法`StartsWithUpper`。</span><span class="sxs-lookup"><span data-stu-id="93818-138">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="93818-139">此方法返回指示<xref:System.Boolean>當前字串實例是否以大寫字元開頭的值。</span><span class="sxs-lookup"><span data-stu-id="93818-139">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="93818-140">Unicode 標準會區別大寫和小寫字元。</span><span class="sxs-lookup"><span data-stu-id="93818-140">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="93818-141">如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="93818-141">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="93818-142">在功能表列上，選擇 **"生成** > **解決方案**"。</span><span class="sxs-lookup"><span data-stu-id="93818-142">On the menu bar, select **Build** > **Build Solution**.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="93818-143">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93818-143">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="93818-144">向解決方案添加新的 Visual Basic .NET 標準類庫專案，該專案名為"StringLibrary"。</span><span class="sxs-lookup"><span data-stu-id="93818-144">Add a new Visual Basic .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="93818-145">按右鍵**解決方案資源管理器**中的解決方案，然後選擇"**添加新** > **專案**"。</span><span class="sxs-lookup"><span data-stu-id="93818-145">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="93818-146">在"**添加新專案**"頁上，在搜索框中輸入**庫**。</span><span class="sxs-lookup"><span data-stu-id="93818-146">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="93818-147">從"語言"清單中選擇 **"視覺化基礎知識**"，然後從"平臺"清單中選擇 **"所有平臺**"。</span><span class="sxs-lookup"><span data-stu-id="93818-147">Choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="93818-148">選擇**類庫 （.NET 標準）** 範本，然後選擇 **"下一步**"。</span><span class="sxs-lookup"><span data-stu-id="93818-148">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="93818-149">在"**配置新專案**"頁上，在 **"專案名稱**"框中輸入**字串庫**。</span><span class="sxs-lookup"><span data-stu-id="93818-149">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="93818-150">然後，選擇 **"創建**"。</span><span class="sxs-lookup"><span data-stu-id="93818-150">Then, choose **Create**.</span></span>

1. <span data-ttu-id="93818-151">檢查以確保庫面向正確的版本 .NET 標準。</span><span class="sxs-lookup"><span data-stu-id="93818-151">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="93818-152">按右鍵**解決方案資源管理器**中的庫專案，然後選擇**屬性**。</span><span class="sxs-lookup"><span data-stu-id="93818-152">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="93818-153">"**目標框架**"文字方塊顯示專案目標 .NET 標準 2.0。</span><span class="sxs-lookup"><span data-stu-id="93818-153">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![類別庫的專案屬性](./media/library-with-visual-studio/vb/library-project-properties.png)

1. <span data-ttu-id="93818-155">在"**屬性"** 對話方塊中，清除 **"根命名空間**"文字方塊中的文本。</span><span class="sxs-lookup"><span data-stu-id="93818-155">In the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="93818-156">對於每個專案，Visual Basic 會自動創建對應于專案名稱的命名空間。</span><span class="sxs-lookup"><span data-stu-id="93818-156">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="93818-157">在本教程中，通過使用代碼檔中的[`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md)關鍵字定義頂級命名空間。</span><span class="sxs-lookup"><span data-stu-id="93818-157">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="93818-158">以下列程式碼取代程式碼視窗中的程式碼，並儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="93818-158">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="93818-159">類庫`UtilityLibraries.StringLibrary`包含名為 的方法`StartsWithUpper`。</span><span class="sxs-lookup"><span data-stu-id="93818-159">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="93818-160">此方法返回指示<xref:System.Boolean>當前字串實例是否以大寫字元開頭的值。</span><span class="sxs-lookup"><span data-stu-id="93818-160">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="93818-161">Unicode 標準會區別大寫和小寫字元。</span><span class="sxs-lookup"><span data-stu-id="93818-161">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="93818-162">如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="93818-162">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="93818-163">在功能表列上，選擇 **"生成** > **解決方案**"。</span><span class="sxs-lookup"><span data-stu-id="93818-163">On the menu bar, select **Build** > **Build Solution**.</span></span>

---

   <span data-ttu-id="93818-164">專案應該會編譯而不會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="93818-164">The project should compile without error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="93818-165">後續步驟</span><span class="sxs-lookup"><span data-stu-id="93818-165">Next steps</span></span>

<span data-ttu-id="93818-166">您已成功組建類別庫。</span><span class="sxs-lookup"><span data-stu-id="93818-166">You've successfully built the library.</span></span> <span data-ttu-id="93818-167">因為您尚未呼叫它的任何方法，所以它能否正常運作還不得而知。</span><span class="sxs-lookup"><span data-stu-id="93818-167">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="93818-168">開發庫的下一步是對其進行測試。</span><span class="sxs-lookup"><span data-stu-id="93818-168">The next step in developing your library is to test it.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="93818-169">創建單元測試專案</span><span class="sxs-lookup"><span data-stu-id="93818-169">Create a unit test project</span></span>](testing-library-with-visual-studio.md)
