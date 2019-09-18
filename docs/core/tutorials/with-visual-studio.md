---
title: 在 Visual Studio 2017 中使用 .NET Core 建置 C# Hello World 應用程式
description: 了解如何使用 Visual Studio 2017 以 C# 建置簡單的 .NET Core 主控台應用程式。
author: BillWagner
ms.author: wiwagn
ms.date: 09/13/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: b42a71993cb120c88b90e867b7af23873b99d280
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039602"
---
# <a name="build-a-c-hello-world-application-with-the-net-core-sdk-in-visual-studio-2017"></a><span data-ttu-id="78474-103">在 Visual Studio 2017 中使用 .NET Core SDK 來建置 C# Hello World 應用程式</span><span class="sxs-lookup"><span data-stu-id="78474-103">Build a C# Hello World application with the .NET Core SDK in Visual Studio 2017</span></span>

<span data-ttu-id="78474-104">本主題提供在 Visual Studio 2017 中使用 C# 建置、偵錯及發行簡單 .NET Core 主控台應用程式的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="78474-104">This topic provides a step-by-step introduction to building, debugging, and publishing a simple .NET Core console application using C# in Visual Studio 2017.</span></span> <span data-ttu-id="78474-105">Visual Studio 2017 提供功能完整的開發環境來建置 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="78474-105">Visual Studio 2017 provides a full-featured development environment for building .NET Core applications.</span></span> <span data-ttu-id="78474-106">只要應用程式沒有平台特定的相依性，應用程式就可以在 .NET Core 的任何目標平台，以及安裝 .NET Core 的任何系統上執行。</span><span class="sxs-lookup"><span data-stu-id="78474-106">As long as the application doesn't have platform-specific dependencies, the application can run on any platform that .NET Core targets and on any system that has .NET Core installed.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="78474-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="78474-107">Prerequisites</span></span>

<span data-ttu-id="78474-108">已安裝「.NET Core 跨平台開發」工作負載的 [Visual Studio 2017 (英文)](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)。</span><span class="sxs-lookup"><span data-stu-id="78474-108">[Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) with the ".NET Core cross-platform development" workload installed.</span></span> <span data-ttu-id="78474-109">您可以使用 .NET Core 2.1 或更新版本來開發您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="78474-109">You can develop your app with .NET Core 2.1 or later versions.</span></span>

<span data-ttu-id="78474-110">如需詳細資訊，請參閱 [Windows 上 .NET Core 的必要條件](../windows-prerequisites.md)。</span><span class="sxs-lookup"><span data-stu-id="78474-110">For more information, see the [Prerequisites for .NET Core on Windows](../windows-prerequisites.md) topic.</span></span>

## <a name="a-simple-hello-world-application"></a><span data-ttu-id="78474-111">簡單的 Hello World 應用程式</span><span class="sxs-lookup"><span data-stu-id="78474-111">A simple Hello World application</span></span>

<span data-ttu-id="78474-112">請開始建立簡單的 "Hello World" 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="78474-112">Begin by creating a simple "Hello World" console application.</span></span> <span data-ttu-id="78474-113">請依照下列步驟：</span><span class="sxs-lookup"><span data-stu-id="78474-113">Follow these steps:</span></span>

1. <span data-ttu-id="78474-114">啟動 Visual Studio 2017。</span><span class="sxs-lookup"><span data-stu-id="78474-114">Launch Visual Studio 2017.</span></span> <span data-ttu-id="78474-115">從功能表列中選取 [檔案]  >  [新增]  >  [專案]。</span><span class="sxs-lookup"><span data-stu-id="78474-115">Select **File** > **New** > **Project** from the menu bar.</span></span> <span data-ttu-id="78474-116">在 [新增專案]\* 對話方塊中，選取後面跟著 [.NET Core] 節點的 [Visual C#] 節點。</span><span class="sxs-lookup"><span data-stu-id="78474-116">In the *New Project*\* dialog, select the **Visual C#** node followed by the **.NET Core** node.</span></span> <span data-ttu-id="78474-117">然後選取 [主控台應用程式 (.NET Core)] 專案範本。</span><span class="sxs-lookup"><span data-stu-id="78474-117">Then select the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="78474-118">在 [名稱] 文字方塊中，鍵入 "HelloWorld"。</span><span class="sxs-lookup"><span data-stu-id="78474-118">In the **Name** text box, type "HelloWorld".</span></span> <span data-ttu-id="78474-119">選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="78474-119">Select the **OK** button.</span></span>

   ![已選取 [主控台應用程式] 的 [新增專案] 對話方塊](./media/with-visual-studio/visual-studio-new-project.png)

1. <span data-ttu-id="78474-121">Visual Studio 使用範本建立專案。</span><span class="sxs-lookup"><span data-stu-id="78474-121">Visual Studio uses the template to create your project.</span></span> <span data-ttu-id="78474-122">.NET Core 的 C# 主控台應用程式範本會自動定義一個 `Program` 類別，該類別具有採用 <xref:System.String> 陣列為引數的單一 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="78474-122">The C# Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="78474-123">`Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="78474-123">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="78474-124">在應用程式啟動時所提供的所有命令列引數，都會在 *args* 陣列中提供。</span><span class="sxs-lookup"><span data-stu-id="78474-124">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio 和新的 HelloWorld 專案](./media/with-visual-studio/visual-studio-main-window.png)

   <span data-ttu-id="78474-126">此範本會建立簡單的 "Hello World" 應用程式。</span><span class="sxs-lookup"><span data-stu-id="78474-126">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="78474-127">它會呼叫 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法，以在主控台視窗中顯示常值字串 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="78474-127">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="78474-128">。</span><span class="sxs-lookup"><span data-stu-id="78474-128">in the console window.</span></span> <span data-ttu-id="78474-129">透過使用工具列上的綠色箭頭選取 **HelloWorld** 按鈕，您可以 [偵錯] 模式執行程式。</span><span class="sxs-lookup"><span data-stu-id="78474-129">By selecting the **HelloWorld** button with the green arrow on the toolbar, you can run the program in Debug mode.</span></span> <span data-ttu-id="78474-130">不過，如果您這樣做，主控台視窗將會在簡短顯示之後關閉。</span><span class="sxs-lookup"><span data-stu-id="78474-130">If you do, the console window is visible for only a brief time interval before it closes.</span></span> <span data-ttu-id="78474-131">這是因為在 `Main` 方法中的單一陳述式執行完畢之後，`Main` 方法會立即終止，而應用程式會立即結束。</span><span class="sxs-lookup"><span data-stu-id="78474-131">This occurs because the `Main` method terminates and the application ends as soon as the single statement in the `Main` method executes.</span></span>

1. <span data-ttu-id="78474-132">若要使應用程式在關閉主控台視窗之前先暫停，請在 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法呼叫之後立即新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="78474-132">To cause the application to pause before it closes the console window, add the following code immediately after the call to the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method:</span></span>

   ```csharp
   Console.Write("Press any key to continue...");
   Console.ReadKey(true);
   ```

   <span data-ttu-id="78474-133">此程式碼會提示使用者按下任意鍵，並暫停程式直到按下按鍵為止。</span><span class="sxs-lookup"><span data-stu-id="78474-133">This code prompts the user to press any key and then pauses the program until a key is pressed.</span></span>

1. <span data-ttu-id="78474-134">在功能表列中，選取 [組建]  >  [組建方案]。</span><span class="sxs-lookup"><span data-stu-id="78474-134">On the menu bar, select **Build** > **Build Solution**.</span></span> <span data-ttu-id="78474-135">這會將您的程式編譯成中繼語言 (IL)，而該語言是由 Just-In-Time (JIT) 編譯器轉換為二進位程式碼。</span><span class="sxs-lookup"><span data-stu-id="78474-135">This compiles your program into an intermediate language (IL) that's converted into binary code by a just-in-time (JIT) compiler.</span></span>

1. <span data-ttu-id="78474-136">透過使用工具列上的綠色箭頭選取 **HelloWorld** 按鈕來執行程式。</span><span class="sxs-lookup"><span data-stu-id="78474-136">Run the program by selecting the **HelloWorld** button with the green arrow on the toolbar.</span></span>

   ![主控台視窗顯示 Hello World，請按任意鍵以繼續](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="78474-138">按任意鍵以關閉主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="78474-138">Press any key to close the console window.</span></span>

## <a name="enhancing-the-hello-world-application"></a><span data-ttu-id="78474-139">增強 Hello World 應用程式</span><span class="sxs-lookup"><span data-stu-id="78474-139">Enhancing the Hello World application</span></span>

<span data-ttu-id="78474-140">增強您的應用程式以提示使用者輸入其名稱，並將其與日期和時間一起顯示。</span><span class="sxs-lookup"><span data-stu-id="78474-140">Enhance your application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="78474-141">若要修改並測試程式，請執行下列動作︰</span><span class="sxs-lookup"><span data-stu-id="78474-141">To modify and test the program, do the following:</span></span>

1. <span data-ttu-id="78474-142">在程式碼視窗中，於 `static void Main(string[] args)` 行之後的左括弧後方，以及第一個右括弧之前輸入下列 C# 程式碼：</span><span class="sxs-lookup"><span data-stu-id="78474-142">Enter the following C# code in the code window immediately after the opening bracket that follows the `static void Main(string[] args)` line and before the first closing bracket:</span></span>

   [!code-csharp[GettingStarted#1](../../../samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   <span data-ttu-id="78474-143">此程式碼會取代 `Main` 方法的內容。</span><span class="sxs-lookup"><span data-stu-id="78474-143">This code replaces the contents of the `Main` method.</span></span>

   ![含有已更新之 Main 方法的 Visual Studio 程式 c-sharp 檔案](./media/with-visual-studio/visual-csharp-code-window.png)

   <span data-ttu-id="78474-145">此程式碼會在主控台中顯示「What is your name?」，</span><span class="sxs-lookup"><span data-stu-id="78474-145">This code displays "What is your name?"</span></span> <span data-ttu-id="78474-146">然後等待使用者輸入字串並按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="78474-146">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="78474-147">它會將此字串儲存至名為 `name` 的變數。</span><span class="sxs-lookup"><span data-stu-id="78474-147">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="78474-148">此程式碼也會擷取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性的值，其中包含目前的當地時間，並將它指派至名稱為 `date` 的變數。</span><span class="sxs-lookup"><span data-stu-id="78474-148">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="78474-149">最後，使用[字串插值](../../csharp/language-reference/tokens/interpolated.md)在主控台視窗中顯示這些值。</span><span class="sxs-lookup"><span data-stu-id="78474-149">Finally, it uses an [interpolated string](../../csharp/language-reference/tokens/interpolated.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="78474-150">選擇 [建置]  >  [建置方案] 來編譯程式。</span><span class="sxs-lookup"><span data-stu-id="78474-150">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="78474-151">在 Visual Studio 中以 [偵錯] 模式執行程式，方法為選取工具列上的綠色箭頭，按 F5，或是選擇 [偵錯]  >  [開始偵錯] 功能表項目。</span><span class="sxs-lookup"><span data-stu-id="78474-151">Run the program in Debug mode in Visual Studio by selecting the green arrow on the toolbar, pressing F5, or choosing the **Debug** > **Start Debugging** menu item.</span></span> <span data-ttu-id="78474-152">輸入名稱並按 Enter 鍵來回應提示。</span><span class="sxs-lookup"><span data-stu-id="78474-152">Respond to the prompt by entering a name and pressing the Enter key.</span></span>

   ![含有已修改程式輸出的主控台視窗](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="78474-154">按任意鍵以關閉主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="78474-154">Press any key to close the console window.</span></span>

<span data-ttu-id="78474-155">您已建立並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="78474-155">You've created and run your application.</span></span> <span data-ttu-id="78474-156">若要開發專業的應用程式，請執行一些其他步驟，來針對發行準備應用程式：</span><span class="sxs-lookup"><span data-stu-id="78474-156">To develop a professional application, take some additional steps to make your application ready for release:</span></span>

- <span data-ttu-id="78474-157">如需對應用程式進行偵錯的資訊，請參閱[使用 Visual Studio 2017 針對 .NET Core Hello World 應用程式進行偵錯](debugging-with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="78474-157">For information on debugging your application, see [Debug your .NET Core Hello World application using Visual Studio 2017](debugging-with-visual-studio.md).</span></span>

- <span data-ttu-id="78474-158">如需開發和發行應用程式可散發版本的資訊，請參閱[使用 Visual Studio 2017 發行 .NET Core Hello World 應用程式](publishing-with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="78474-158">For information on developing and publishing a distributable version of your application, see [Publish your .NET Core Hello World application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="78474-159">相關主題</span><span class="sxs-lookup"><span data-stu-id="78474-159">Related topics</span></span>

<span data-ttu-id="78474-160">除了主控台應用程式之外，您也可以使用 .NET Core 和 Visual Studio 2017 建置類別庫。</span><span class="sxs-lookup"><span data-stu-id="78474-160">Instead of a console application, you can also build a class library with .NET Core and Visual Studio 2017.</span></span> <span data-ttu-id="78474-161">如需逐步介紹，請參閱[在 Visual Studio 2017 中使用 C# 和 .NET Core 建置類別庫](library-with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="78474-161">For a step-by-step introduction, see [Building a class library with C# and .NET Core in Visual Studio 2017](library-with-visual-studio.md).</span></span>

<span data-ttu-id="78474-162">您也可以使用 [Visual Studio Code](https://code.visualstudio.com/) (可免費下載的程式碼編輯器)，在 Mac、Linux 和 Windows 上開發 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="78474-162">You can also develop a .NET Core console app on Mac, Linux, and Windows by using [Visual Studio Code](https://code.visualstudio.com/), a downloadable code editor.</span></span> <span data-ttu-id="78474-163">如需逐步教學課程，請參閱[開始使用 Visual Studio Code](with-visual-studio-code.md)。</span><span class="sxs-lookup"><span data-stu-id="78474-163">For a step-by-step tutorial, see [Getting Started with Visual Studio Code](with-visual-studio-code.md).</span></span>
