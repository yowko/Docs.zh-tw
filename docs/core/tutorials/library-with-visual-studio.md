---
title: 在 Visual Studio 中建立 .NET Standard 類別庫
description: 瞭解如何使用 Visual Studio 來建立以C#或 Visual Basic 撰寫的 .NET Standard 類別庫
ms.date: 12/09/2019
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 160993a4dd40356cde541616a1f15f87712e8ae2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343132"
---
# <a name="build-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="55da5-103">在 Visual Studio 中建立 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="55da5-103">Build a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="55da5-104">「類別庫」會定義應用程式所呼叫的類型和方法。</span><span class="sxs-lookup"><span data-stu-id="55da5-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="55da5-105">以 .NET Standard 2.0 為目標的類別庫，可讓任何支援該版本 .NET Standard 的 .NET 部署呼叫您的程式庫。</span><span class="sxs-lookup"><span data-stu-id="55da5-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="55da5-106">當您完成類別庫時，您可以決定要將它散發為協力廠商元件，還是要將它併入作為一或多個應用程式隨附的元件。</span><span class="sxs-lookup"><span data-stu-id="55da5-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="55da5-107">如需所支援的 .NET Standard 版本和平臺清單，請參閱[.NET Standard](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="55da5-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="55da5-108">在本主題中，您將建立含有單一字串處理方法的簡單公用程式類別庫。</span><span class="sxs-lookup"><span data-stu-id="55da5-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="55da5-109">您將它實作為[擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)，以便可以如同 <xref:System.String> 類別的成員一般來進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="55da5-109">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="55da5-110">建立 Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="55da5-110">Create a Visual Studio solution</span></span>

<span data-ttu-id="55da5-111">一開始先建立一個空白的方案，將類別庫專案放入中。</span><span class="sxs-lookup"><span data-stu-id="55da5-111">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="55da5-112">Visual Studio 方案會當做一個或多個專案的容器。</span><span class="sxs-lookup"><span data-stu-id="55da5-112">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="55da5-113">如果您繼續進行教學課程系列，您會將其他的相關專案新增至相同的方案。</span><span class="sxs-lookup"><span data-stu-id="55da5-113">You'll add additional, related projects to the same solution if you continue on with the tutorial series.</span></span>

<span data-ttu-id="55da5-114">若要建立空白解決方案：</span><span class="sxs-lookup"><span data-stu-id="55da5-114">To create the blank solution:</span></span>

1. <span data-ttu-id="55da5-115">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="55da5-115">Open Visual Studio.</span></span>

2. <span data-ttu-id="55da5-116">在開始視窗中，選擇 [建立新專案]。</span><span class="sxs-lookup"><span data-stu-id="55da5-116">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="55da5-117">在 [**建立新專案**] 頁面的 [搜尋] 方塊中，輸入 [**方案**]。</span><span class="sxs-lookup"><span data-stu-id="55da5-117">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="55da5-118">選擇 [**空白解決方案**] 範本，然後選擇 [**下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="55da5-118">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Visual Studio 中的空白方案範本](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="55da5-120">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**ClassLibraryProjects** 。</span><span class="sxs-lookup"><span data-stu-id="55da5-120">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="55da5-121">接著，選擇 [建立]。</span><span class="sxs-lookup"><span data-stu-id="55da5-121">Then, choose **Create**.</span></span>

> [!TIP]
> <span data-ttu-id="55da5-122">您也可以略過此步驟，並在下一個步驟中建立專案時，讓 Visual Studio 為您建立解決方案。</span><span class="sxs-lookup"><span data-stu-id="55da5-122">You can also skip this step and let Visual Studio create the solution for you when you create the project in the next step.</span></span> <span data-ttu-id="55da5-123">在 [**設定您的新專案**] 頁面上尋找解決方案選項。</span><span class="sxs-lookup"><span data-stu-id="55da5-123">Look for the solution options on the **Configure your new project** page.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="55da5-124">建立類別庫專案</span><span class="sxs-lookup"><span data-stu-id="55da5-124">Create a class library project</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[<span data-ttu-id="55da5-125">C#</span><span class="sxs-lookup"><span data-stu-id="55da5-125">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="55da5-126">將名為C# "StringLibrary" 的新 .NET Standard 類別庫專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="55da5-126">Add a new C# .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="55da5-127">以滑鼠右鍵按一下**方案總管**中的方案，然後選取 [**加入** > **新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="55da5-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="55da5-128">在 [**加入新專案**] 頁面的 [搜尋] 方塊中，輸入 [連結**庫**]。</span><span class="sxs-lookup"><span data-stu-id="55da5-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="55da5-129">從**C#** [語言] 清單中選擇，然後從 [平臺] 清單中選擇 [**所有平臺**]。</span><span class="sxs-lookup"><span data-stu-id="55da5-129">Choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="55da5-130">選擇 [**類別庫（.NET Standard）** ] 範本，然後選擇 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="55da5-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="55da5-131">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**StringLibrary** 。</span><span class="sxs-lookup"><span data-stu-id="55da5-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="55da5-132">接著，選擇 [建立]。</span><span class="sxs-lookup"><span data-stu-id="55da5-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="55da5-133">請檢查並確定程式庫的目標是正確的 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="55da5-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="55da5-134">以滑鼠右鍵按一下**方案總管**中的 [程式庫] 專案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="55da5-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="55da5-135">[**目標 Framework** ] 文字方塊會顯示專案的目標為 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="55da5-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![類別庫的專案屬性](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="55da5-137">以下列程式碼取代程式碼視窗中的程式碼，並儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="55da5-137">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="55da5-138">類別庫（`UtilityLibraries.StringLibrary`）包含名為 `StartsWithUpper`的方法。</span><span class="sxs-lookup"><span data-stu-id="55da5-138">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="55da5-139">這個方法會傳回 <xref:System.Boolean> 值，指出目前的字串實例是否以大寫字元開頭。</span><span class="sxs-lookup"><span data-stu-id="55da5-139">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="55da5-140">Unicode 標準會區別大寫和小寫字元。</span><span class="sxs-lookup"><span data-stu-id="55da5-140">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="55da5-141">如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="55da5-141">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="55da5-142">在功能表列中，選取 [組建] >  [組建方案]。</span><span class="sxs-lookup"><span data-stu-id="55da5-142">On the menu bar, select **Build** > **Build Solution**.</span></span>

# <a name="visual-basictabvb"></a>[<span data-ttu-id="55da5-143">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="55da5-143">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="55da5-144">將名為 "StringLibrary" 的新 Visual Basic .NET Standard 類別庫專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="55da5-144">Add a new Visual Basic .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="55da5-145">以滑鼠右鍵按一下**方案總管**中的方案，然後選取 [**加入** > **新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="55da5-145">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="55da5-146">在 [**加入新專案**] 頁面的 [搜尋] 方塊中，輸入 [連結**庫**]。</span><span class="sxs-lookup"><span data-stu-id="55da5-146">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="55da5-147">從 [語言] 清單中選擇 [ **Visual Basic** ]，然後從 [平臺] 清單中選擇 [**所有平臺**]。</span><span class="sxs-lookup"><span data-stu-id="55da5-147">Choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="55da5-148">選擇 [**類別庫（.NET Standard）** ] 範本，然後選擇 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="55da5-148">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="55da5-149">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**StringLibrary** 。</span><span class="sxs-lookup"><span data-stu-id="55da5-149">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="55da5-150">接著，選擇 [建立]。</span><span class="sxs-lookup"><span data-stu-id="55da5-150">Then, choose **Create**.</span></span>

1. <span data-ttu-id="55da5-151">請檢查並確定程式庫的目標是正確的 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="55da5-151">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="55da5-152">以滑鼠右鍵按一下**方案總管**中的 [程式庫] 專案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="55da5-152">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="55da5-153">[**目標 Framework** ] 文字方塊會顯示專案的目標為 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="55da5-153">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![類別庫的專案屬性](./media/library-with-visual-studio/vb/library-project-properties.png)

1. <span data-ttu-id="55da5-155">在 [**屬性**] 對話方塊中，清除 [**根命名空間**] 文字方塊中的文字。</span><span class="sxs-lookup"><span data-stu-id="55da5-155">In the **Properties** dialog, clear the text in the **Root namespace** text box.</span></span> <span data-ttu-id="55da5-156">針對每個專案，Visual Basic 會自動建立對應至專案名稱的命名空間。</span><span class="sxs-lookup"><span data-stu-id="55da5-156">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="55da5-157">在本教學課程中，您會使用程式碼檔案中的[`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md)關鍵字來定義最上層命名空間。</span><span class="sxs-lookup"><span data-stu-id="55da5-157">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="55da5-158">以下列程式碼取代程式碼視窗中的程式碼，並儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="55da5-158">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-vb[ClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="55da5-159">類別庫（`UtilityLibraries.StringLibrary`）包含名為 `StartsWithUpper`的方法。</span><span class="sxs-lookup"><span data-stu-id="55da5-159">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="55da5-160">這個方法會傳回 <xref:System.Boolean> 值，指出目前的字串實例是否以大寫字元開頭。</span><span class="sxs-lookup"><span data-stu-id="55da5-160">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="55da5-161">Unicode 標準會區別大寫和小寫字元。</span><span class="sxs-lookup"><span data-stu-id="55da5-161">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="55da5-162">如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="55da5-162">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="55da5-163">在功能表列中，選取 [組建] >  [組建方案]。</span><span class="sxs-lookup"><span data-stu-id="55da5-163">On the menu bar, select **Build** > **Build Solution**.</span></span>

---

   <span data-ttu-id="55da5-164">專案應該會編譯而不會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="55da5-164">The project should compile without error.</span></span>

## <a name="next-steps"></a><span data-ttu-id="55da5-165">後續步驟</span><span class="sxs-lookup"><span data-stu-id="55da5-165">Next steps</span></span>

<span data-ttu-id="55da5-166">您已成功組建類別庫。</span><span class="sxs-lookup"><span data-stu-id="55da5-166">You've successfully built the library.</span></span> <span data-ttu-id="55da5-167">因為您尚未呼叫它的任何方法，所以它能否正常運作還不得而知。</span><span class="sxs-lookup"><span data-stu-id="55da5-167">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="55da5-168">開發程式庫的下一個步驟是測試它。</span><span class="sxs-lookup"><span data-stu-id="55da5-168">The next step in developing your library is to test it.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="55da5-169">建立單元測試專案</span><span class="sxs-lookup"><span data-stu-id="55da5-169">Create a unit test project</span></span>](testing-library-with-visual-studio.md)
