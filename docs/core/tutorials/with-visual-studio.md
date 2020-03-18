---
title: 在視覺化工作室中使用 .NET 核心創建 Hello World 應用程式
description: 瞭解如何使用 Visual Studio 使用 C# 或視覺化基本版創建第一個 .NET 核心主控台應用程式。
author: BillWagner
ms.author: wiwagn
ms.date: 12/09/2019
ms.custom: vs-dotnet
ms.openlocfilehash: ba996e4add1cfe44681154b00a6530b1f3e70b37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714003"
---
# <a name="tutorial-create-your-first-net-core-console-application-in-visual-studio-2019"></a><span data-ttu-id="c6684-103">教程：在 Visual Studio 2019 中創建您的第一個 .NET 核心主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="c6684-103">Tutorial: Create your first .NET Core console application in Visual Studio 2019</span></span>

<span data-ttu-id="c6684-104">本文提供了在 Visual Studio 2019 中創建和運行 Hello World .NET 核心主控台應用程式的分步介紹。</span><span class="sxs-lookup"><span data-stu-id="c6684-104">This article provides a step-by-step introduction to create and run a Hello World .NET Core console application in Visual Studio 2019.</span></span> <span data-ttu-id="c6684-105">Hello World 應用程式傳統上用於向初學者介紹新的程式設計語言。</span><span class="sxs-lookup"><span data-stu-id="c6684-105">A Hello World application is traditionally used to introduce beginners to a new programming language.</span></span> <span data-ttu-id="c6684-106">這個程式只是顯示短語"你好世界！</span><span class="sxs-lookup"><span data-stu-id="c6684-106">This program simply displays the phrase "Hello World!"</span></span> <span data-ttu-id="c6684-107">。</span><span class="sxs-lookup"><span data-stu-id="c6684-107">on the screen.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c6684-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="c6684-108">Prerequisites</span></span>

- <span data-ttu-id="c6684-109">[Visual Studio 2019 版本 16.4 或更高版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)，安裝了 **.NET Core 跨平臺開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="c6684-109">[Visual Studio 2019 version 16.4 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="c6684-110">.NET 核心 3.1 SDK 在選擇此工作負載時會自動安裝。</span><span class="sxs-lookup"><span data-stu-id="c6684-110">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

<span data-ttu-id="c6684-111">有關詳細資訊，請參閱[安裝 .NET 核心 SDK](../install/sdk.md?pivots=os-windows)一文上的["使用視覺化工作室安裝](../install/sdk.md?pivots=os-windows#install-with-visual-studio)"部分。</span><span class="sxs-lookup"><span data-stu-id="c6684-111">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="c6684-112">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="c6684-112">Create the app</span></span>

<span data-ttu-id="c6684-113">以下說明創建一個簡單的 Hello World 主控台應用程式：</span><span class="sxs-lookup"><span data-stu-id="c6684-113">The following instructions create a simple Hello World console application:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="c6684-114">C#</span><span class="sxs-lookup"><span data-stu-id="c6684-114">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="c6684-115">開啟 Visual Studio 2019。</span><span class="sxs-lookup"><span data-stu-id="c6684-115">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="c6684-116">創建新的 C# .NET 核心主控台應用專案，名為"HelloWorld"。</span><span class="sxs-lookup"><span data-stu-id="c6684-116">Create a new C# .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="c6684-117">在啟動視窗中，選擇 **"創建新專案**"。</span><span class="sxs-lookup"><span data-stu-id="c6684-117">On the start window, choose **Create a new project**.</span></span>

      ![創建在視覺化工作室啟動視窗中選擇的新專案按鈕](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="c6684-119">在"**創建新專案**"頁上，在搜索框中輸入**主控台**。</span><span class="sxs-lookup"><span data-stu-id="c6684-119">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="c6684-120">接下來，從"語言"清單中選擇**C#，** 然後從"平臺"清單中選擇 **"所有平臺**"。</span><span class="sxs-lookup"><span data-stu-id="c6684-120">Next, choose **C#** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="c6684-121">選擇**主控台應用 （.NET 核心）** 範本，然後選擇 **"下一步**"。</span><span class="sxs-lookup"><span data-stu-id="c6684-121">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![創建一個選中篩選器的新專案視窗](./media/with-visual-studio/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="c6684-123">如果未看到 .NET Core 範本，則可能缺少安裝所需的工作負載。</span><span class="sxs-lookup"><span data-stu-id="c6684-123">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="c6684-124">在 **"未查找要查找的內容"** 消息下，選擇 **"安裝更多工具和功能**"連結。</span><span class="sxs-lookup"><span data-stu-id="c6684-124">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="c6684-125">視覺化工作室安裝程式將打開。</span><span class="sxs-lookup"><span data-stu-id="c6684-125">The Visual Studio Installer opens.</span></span> <span data-ttu-id="c6684-126">確保您安裝了 **.NET Core 跨平臺開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="c6684-126">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="c6684-127">在"**配置新專案**"頁上，在 **"專案名稱"** 框中輸入**HelloWorld。**</span><span class="sxs-lookup"><span data-stu-id="c6684-127">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="c6684-128">然後，選擇 **"創建**"。</span><span class="sxs-lookup"><span data-stu-id="c6684-128">Then, choose **Create**.</span></span>

      ![使用專案名稱、位置和解決方案名稱欄位配置新專案視窗](./media/with-visual-studio/configure-new-project.png)

   <span data-ttu-id="c6684-130">.NET Core 的 C# 主控台應用程式範本會自動定義一個 `Program` 類別，該類別具有採用 <xref:System.String> 陣列為引數的單一 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="c6684-130">The C# Console Application template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="c6684-131">`Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="c6684-131">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="c6684-132">在應用程式啟動時所提供的所有命令列引數，都會在 *args* 陣列中提供。</span><span class="sxs-lookup"><span data-stu-id="c6684-132">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

   ![Visual Studio 和新的 HelloWorld 專案](./media/with-visual-studio/visual-studio-main-window.png)

# <a name="visual-basic"></a>[<span data-ttu-id="c6684-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6684-134">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="c6684-135">開啟 Visual Studio 2019。</span><span class="sxs-lookup"><span data-stu-id="c6684-135">Open Visual Studio 2019.</span></span>

1. <span data-ttu-id="c6684-136">創建新的視覺基礎 .NET 核心主控台應用程式專案名為"HelloWorld"。</span><span class="sxs-lookup"><span data-stu-id="c6684-136">Create a new Visual Basic .NET Core console app project named "HelloWorld".</span></span>

   1. <span data-ttu-id="c6684-137">在啟動視窗中，選擇 **"創建新專案**"。</span><span class="sxs-lookup"><span data-stu-id="c6684-137">On the start window, choose **Create a new project**.</span></span>

      ![創建在視覺化工作室啟動視窗中選擇的新專案按鈕](./media/with-visual-studio/start-window.png)

   1. <span data-ttu-id="c6684-139">在"**創建新專案**"頁上，在搜索框中輸入**主控台**。</span><span class="sxs-lookup"><span data-stu-id="c6684-139">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="c6684-140">接下來，從"語言"清單中選擇 **"視覺化基礎知識**"，然後從"平臺"清單中選擇 **"所有平臺**"。</span><span class="sxs-lookup"><span data-stu-id="c6684-140">Next, choose **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="c6684-141">選擇**主控台應用 （.NET 核心）** 範本，然後選擇 **"下一步**"。</span><span class="sxs-lookup"><span data-stu-id="c6684-141">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

      ![選擇主控台應用程式 (.NET Framework) 的 Visual Basic 專案範本](./media/with-visual-studio/vb/create-new-project.png)

      > [!TIP]
      > <span data-ttu-id="c6684-143">如果未看到 .NET Core 範本，則可能缺少安裝所需的工作負載。</span><span class="sxs-lookup"><span data-stu-id="c6684-143">If you don't see the .NET Core templates, you're probably missing the required workload installed.</span></span> <span data-ttu-id="c6684-144">在 **"未查找要查找的內容"** 消息下，選擇 **"安裝更多工具和功能**"連結。</span><span class="sxs-lookup"><span data-stu-id="c6684-144">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="c6684-145">視覺化工作室安裝程式將打開。</span><span class="sxs-lookup"><span data-stu-id="c6684-145">The Visual Studio Installer opens.</span></span> <span data-ttu-id="c6684-146">確保您安裝了 **.NET Core 跨平臺開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="c6684-146">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

   1. <span data-ttu-id="c6684-147">在"**配置新專案**"頁上，在 **"專案名稱"** 框中輸入**HelloWorld。**</span><span class="sxs-lookup"><span data-stu-id="c6684-147">On the **Configure your new project** page,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="c6684-148">然後，選擇 **"創建**"。</span><span class="sxs-lookup"><span data-stu-id="c6684-148">Then, choose **Create**.</span></span>

   <span data-ttu-id="c6684-149">.NET Core 的主控台應用範本自動定義一個類`Program`，使用單個方法 ，`Main`將<xref:System.String>陣列作為參數。</span><span class="sxs-lookup"><span data-stu-id="c6684-149">The console app template for .NET Core automatically defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="c6684-150">`Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="c6684-150">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="c6684-151">在`args`參數中提供了啟動應用程式時提供的任何命令列參數。</span><span class="sxs-lookup"><span data-stu-id="c6684-151">Any command-line arguments supplied when the application is launched are available in the `args` parameter.</span></span>

   ![Visual Studio 和新的 HelloWorld 專案](./media/with-visual-studio/vb/visual-studio-main-window.png)

---

   <span data-ttu-id="c6684-153">此範本會建立簡單的 "Hello World" 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c6684-153">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="c6684-154">它會呼叫 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法，以在主控台視窗中顯示常值字串 "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="c6684-154">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display the literal string "Hello World!"</span></span> <span data-ttu-id="c6684-155">。</span><span class="sxs-lookup"><span data-stu-id="c6684-155">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="c6684-156">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="c6684-156">Run the app</span></span>

1. <span data-ttu-id="c6684-157">要運行該程式，請選擇工具列上的**HelloWorld，** 或按**F5**。</span><span class="sxs-lookup"><span data-stu-id="c6684-157">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

   ![已選擇 HelloWorld 運行按鈕的視覺化工作室工具列](./media/with-visual-studio/run-program.png)

   <span data-ttu-id="c6684-159">主控台視窗打開，上面寫著"你好世界！</span><span class="sxs-lookup"><span data-stu-id="c6684-159">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="c6684-160">列印在螢幕上和一些視覺化工作室調試資訊。</span><span class="sxs-lookup"><span data-stu-id="c6684-160">printed on the screen and some Visual Studio debug information.</span></span>

   ![主控台視窗顯示 Hello World，請按任意鍵以繼續](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="c6684-162">按任意鍵關閉主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="c6684-162">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="c6684-163">增強應用程式</span><span class="sxs-lookup"><span data-stu-id="c6684-163">Enhance the app</span></span>

<span data-ttu-id="c6684-164">增強您的應用程式以提示使用者輸入其名稱，並將其與日期和時間一起顯示。</span><span class="sxs-lookup"><span data-stu-id="c6684-164">Enhance your application to prompt the user for their name and display it along with the date and time.</span></span> <span data-ttu-id="c6684-165">以下說明再次修改並運行應用：</span><span class="sxs-lookup"><span data-stu-id="c6684-165">The following instructions modify and run the app again:</span></span>

# <a name="c"></a>[<span data-ttu-id="c6684-166">C#</span><span class="sxs-lookup"><span data-stu-id="c6684-166">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="c6684-167">將`Main`方法的內容（當前只是調用`Console.WriteLine`的行）替換為以下代碼：</span><span class="sxs-lookup"><span data-stu-id="c6684-167">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-csharp[GettingStarted#1](~/samples/snippets/csharp/getting_started/with_visual_studio/helloworld.cs#1)]

   <span data-ttu-id="c6684-168">此程式碼會在主控台中顯示「What is your name?」，</span><span class="sxs-lookup"><span data-stu-id="c6684-168">This code displays "What is your name?"</span></span> <span data-ttu-id="c6684-169">然後等待使用者輸入字串並按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="c6684-169">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="c6684-170">它會將此字串儲存至名為 `name` 的變數。</span><span class="sxs-lookup"><span data-stu-id="c6684-170">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="c6684-171">此程式碼也會擷取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性的值，其中包含目前的當地時間，並將它指派至名稱為 `date` 的變數。</span><span class="sxs-lookup"><span data-stu-id="c6684-171">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="c6684-172">最後，使用[字串插值](../../csharp/language-reference/tokens/interpolated.md)在主控台視窗中顯示這些值。</span><span class="sxs-lookup"><span data-stu-id="c6684-172">Finally, it uses an [interpolated string](../../csharp/language-reference/tokens/interpolated.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="c6684-173">通過選擇**生成** > **解決方案**編譯器。</span><span class="sxs-lookup"><span data-stu-id="c6684-173">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="c6684-174">要運行該程式，請選擇工具列上的**HelloWorld，** 或按**F5**。</span><span class="sxs-lookup"><span data-stu-id="c6684-174">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="c6684-175">通過輸入名稱並按**Enter**鍵回應提示。</span><span class="sxs-lookup"><span data-stu-id="c6684-175">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![含有已修改程式輸出的主控台視窗](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="c6684-177">按任意鍵關閉主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="c6684-177">Press any key to close the console window.</span></span>

# <a name="visual-basic"></a>[<span data-ttu-id="c6684-178">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6684-178">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="c6684-179">將`Main`方法的內容（當前只是調用`Console.WriteLine`的行）替換為以下代碼：</span><span class="sxs-lookup"><span data-stu-id="c6684-179">Replace the contents of the `Main` method, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-vb[GettingStarted#1](~/samples/snippets/core/tutorials/vb-with-visual-studio/helloworld.vb#1)]

   <span data-ttu-id="c6684-180">此程式碼會在主控台中顯示「What is your name?」，</span><span class="sxs-lookup"><span data-stu-id="c6684-180">This code displays "What is your name?"</span></span> <span data-ttu-id="c6684-181">然後等待使用者輸入字串並按 Enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="c6684-181">in the console window and waits until the user enters a string followed by the Enter key.</span></span> <span data-ttu-id="c6684-182">它會將此字串儲存至名為 `name` 的變數。</span><span class="sxs-lookup"><span data-stu-id="c6684-182">It stores this string into a variable named `name`.</span></span> <span data-ttu-id="c6684-183">此程式碼也會擷取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性的值，其中包含目前的當地時間，並將它指派至名稱為 `date` 的變數。</span><span class="sxs-lookup"><span data-stu-id="c6684-183">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="c6684-184">最後，使用[字串插值](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)在主控台視窗中顯示這些值。</span><span class="sxs-lookup"><span data-stu-id="c6684-184">Finally, it uses an [interpolated string](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md) to display these values in the console window.</span></span>

1. <span data-ttu-id="c6684-185">通過選擇**生成** > **解決方案**編譯器。</span><span class="sxs-lookup"><span data-stu-id="c6684-185">Compile the program by choosing **Build** > **Build Solution**.</span></span>

1. <span data-ttu-id="c6684-186">要運行該程式，請選擇工具列上的**HelloWorld，** 或按**F5**。</span><span class="sxs-lookup"><span data-stu-id="c6684-186">To run the program, choose **HelloWorld** on the toolbar, or press **F5**.</span></span>

1. <span data-ttu-id="c6684-187">通過輸入名稱並按**Enter**鍵回應提示。</span><span class="sxs-lookup"><span data-stu-id="c6684-187">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   ![含有已修改程式輸出的主控台視窗](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="c6684-189">按任意鍵關閉主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="c6684-189">Press any key to close the console window.</span></span>

---

## <a name="next-steps"></a><span data-ttu-id="c6684-190">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c6684-190">Next steps</span></span>

<span data-ttu-id="c6684-191">在本文中，您已經創建並運行了第一個 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c6684-191">In this article, you've created and run your first .NET Core application.</span></span> <span data-ttu-id="c6684-192">在下一步中，您將調試應用。</span><span class="sxs-lookup"><span data-stu-id="c6684-192">In the next step, you debug your app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c6684-193">在視覺工作室調試 .NET 核心 Hello World 應用程式</span><span class="sxs-lookup"><span data-stu-id="c6684-193">Debug a .NET Core Hello World application in Visual Studio</span></span>](debugging-with-visual-studio.md)
