---
title: 使用 Visual Studio 2017 來建置 C# .NET Standard 類別庫
description: 了解如何使用 Visual Studio 2017 建立以 C# 撰寫的 .NET Standard 類別庫。
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 0c98f8c8fc4847570964d8d4ea8deb221164441d
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168932"
---
# <a name="build-a-net-standard-class-library-with-c-and-the-net-core-sdk-in-visual-studio-2017"></a><span data-ttu-id="07d68-103">在 Visual Studio 2017 中使用 C# 和 .NET Core SDK 來建置 .NET Standard 類別庫</span><span class="sxs-lookup"><span data-stu-id="07d68-103">Build a .NET Standard class library with C# and the .NET Core SDK in Visual Studio 2017</span></span>

<span data-ttu-id="07d68-104">「類別庫」會定義應用程式所呼叫的類型和方法。</span><span class="sxs-lookup"><span data-stu-id="07d68-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="07d68-105">以 .NET Standard 2.0 為目標的類別庫，允許支援該 .NET Standard 版本的任何 .NET 實作呼叫您的類別庫。</span><span class="sxs-lookup"><span data-stu-id="07d68-105">A class library that targets the .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of the .NET Standard.</span></span> <span data-ttu-id="07d68-106">當您完成類別庫時，您可以決定要將它散發為協力廠商元件，還是要將它併入作為一或多個應用程式隨附的元件。</span><span class="sxs-lookup"><span data-stu-id="07d68-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="07d68-107">如需 .NET 標準版本與所支援平台的清單，請參閱 [.NET 標準](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="07d68-107">For a list of the .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="07d68-108">在本主題中，您將建立含有單一字串處理方法的簡單公用程式類別庫。</span><span class="sxs-lookup"><span data-stu-id="07d68-108">In this topic, you'll create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="07d68-109">您將它實作為[擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)，以便可以如同 <xref:System.String> 類別的成員一般來進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="07d68-109">You'll implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="creating-a-class-library-solution"></a><span data-ttu-id="07d68-110">建立類別庫方案</span><span class="sxs-lookup"><span data-stu-id="07d68-110">Creating a class library solution</span></span>

<span data-ttu-id="07d68-111">請開始建立類別庫專案和其相關專案的方案。</span><span class="sxs-lookup"><span data-stu-id="07d68-111">Start by creating a solution for your class library project and its related projects.</span></span> <span data-ttu-id="07d68-112">Visual Studio 方案只能做為一個或多個專案的容器。</span><span class="sxs-lookup"><span data-stu-id="07d68-112">A Visual Studio Solution just serves as a container for one or more projects.</span></span> <span data-ttu-id="07d68-113">建立方案：</span><span class="sxs-lookup"><span data-stu-id="07d68-113">To create the solution:</span></span>

1. <span data-ttu-id="07d68-114">在 Visual Studio 功能表列上，選擇 [檔案]  >  [新增]   >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="07d68-114">On the Visual Studio menu bar, choose **File** > **New** > **Project**.</span></span>

1. <span data-ttu-id="07d68-115">在 **[新增專案]** 對話方塊中，展開 **[其他專案類型]** 節點，並選取 **[Visual Studio 方案]**。</span><span class="sxs-lookup"><span data-stu-id="07d68-115">In the **New Project** dialog, expand the **Other Project Types** node, and select **Visual Studio Solutions**.</span></span> <span data-ttu-id="07d68-116">將方案命名為 "ClassLibraryProjects"，然後選取 **[確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="07d68-116">Name the solution "ClassLibraryProjects" and select the **OK** button.</span></span>

   ![[新增專案] 對話方塊，其中醒目提示新的空白方案](./media/library-with-visual-studio/new-project-dialog.png)

## <a name="creating-the-class-library-project"></a><span data-ttu-id="07d68-118">建立類別庫專案</span><span class="sxs-lookup"><span data-stu-id="07d68-118">Creating the class library project</span></span>

<span data-ttu-id="07d68-119">建立您的類別庫專案：</span><span class="sxs-lookup"><span data-stu-id="07d68-119">Create your class library project:</span></span>

1. <span data-ttu-id="07d68-120">在方案總管  中，以滑鼠右鍵按一下 **ClassLibraryProjects** 方案檔，然後從內容功能表中，選取 [新增]  >  [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="07d68-120">In **Solution Explorer**, right-click on the **ClassLibraryProjects** solution file and from the context menu, select **Add** > **New Project**.</span></span>

1. <span data-ttu-id="07d68-121">在 **[新增專案]** 對話方塊中，展開 **[Visual C#]** 節點，然後選取後面跟著 **[類別庫 (.NET Standard)]** 專案範本的 **[.NET Standard]** 節點。</span><span class="sxs-lookup"><span data-stu-id="07d68-121">In the **Add New Project** dialog, expand the **Visual C#** node, then select the **.NET Standard** node followed by the **Class Library (.NET Standard)** project template.</span></span> <span data-ttu-id="07d68-122">在 **[名稱]** 文字方塊中，輸入 "StringLibrary" 作為專案名稱。</span><span class="sxs-lookup"><span data-stu-id="07d68-122">In the **Name** text box, enter "StringLibrary" as the name of the project.</span></span> <span data-ttu-id="07d68-123">選取 [確定] 以建立類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="07d68-123">Select **OK** to create the class library project.</span></span>

   ![新增程式庫專案對話方塊](./media/library-with-visual-studio/add-new-library-project.png)

   <span data-ttu-id="07d68-125">然後在 Visual Studio 開發環境中開啟程式碼視窗。</span><span class="sxs-lookup"><span data-stu-id="07d68-125">The code window then opens in the Visual Studio development environment.</span></span>

   ![Visual Studio 應用程式視窗顯示預設的類別庫範本程式碼](./media/library-with-visual-studio/string-library-project.png)

1. <span data-ttu-id="07d68-127">請檢查以確定程式庫以正確的 .NET Standard 版本為目標。</span><span class="sxs-lookup"><span data-stu-id="07d68-127">Check to make sure that our library targets the correct version of the .NET Standard.</span></span> <span data-ttu-id="07d68-128">在**方案總管**視窗中，以滑鼠右鍵按一下程式庫專案，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="07d68-128">Right-click on the library project in the **Solution Explorer** windows, then select **Properties**.</span></span> <span data-ttu-id="07d68-129">[目標 Framework] 文字方塊顯示我們的目標是 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="07d68-129">The **Target Framework** text box shows that we're targeting .NET Standard 2.0.</span></span>

   ![類別庫的專案屬性](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="07d68-131">以下列程式碼取代程式碼視窗中的程式碼，並儲存檔案：</span><span class="sxs-lookup"><span data-stu-id="07d68-131">Replace the code in the code window with the following code and save the file:</span></span>

   [!CODE-csharp[ClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]

   <span data-ttu-id="07d68-132">類別庫 `UtilityLibraries.StringLibrary` 包含一個名為 `StartsWithUpper` 的方法，它會傳回 <xref:System.Boolean> 值，指出目前的字串執行個體是否以大寫字元開頭。</span><span class="sxs-lookup"><span data-stu-id="07d68-132">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`, which returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="07d68-133">Unicode 標準會區別大寫和小寫字元。</span><span class="sxs-lookup"><span data-stu-id="07d68-133">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="07d68-134">如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="07d68-134">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="07d68-135">在功能表列中，選取 [組建]  >  [組建方案]。</span><span class="sxs-lookup"><span data-stu-id="07d68-135">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="07d68-136">專案應該會編譯而不會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="07d68-136">The project should compile without error.</span></span>

   ![輸出窗格顯示組建成功](./media/library-with-visual-studio/output-pane-successful-build.png)

## <a name="next-step"></a><span data-ttu-id="07d68-138">後續步驟</span><span class="sxs-lookup"><span data-stu-id="07d68-138">Next step</span></span>

<span data-ttu-id="07d68-139">您已成功組建類別庫。</span><span class="sxs-lookup"><span data-stu-id="07d68-139">You've successfully built the library.</span></span> <span data-ttu-id="07d68-140">因為您尚未呼叫它的任何方法，所以它能否正常運作還不得而知。</span><span class="sxs-lookup"><span data-stu-id="07d68-140">Because you haven't called any of its methods, you don't know whether it works as expected.</span></span> <span data-ttu-id="07d68-141">開發程式庫的下一個步驟是使用[單元測試專案](testing-library-with-visual-studio.md)來測試它。</span><span class="sxs-lookup"><span data-stu-id="07d68-141">The next step in developing your library is to test it by using a [Unit Test Project](testing-library-with-visual-studio.md).</span></span>