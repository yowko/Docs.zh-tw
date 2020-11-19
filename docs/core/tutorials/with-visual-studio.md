---
title: 使用 Visual Studio 建立 .NET 主控台應用程式
description: '瞭解如何使用 Visual Studio 以 c # 或 Visual Basic 建立 .NET 主控台應用程式。'
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: e395122e59f17ed66bbd9d83b01610993f663ce1
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94915914"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio"></a><span data-ttu-id="cf26b-103">教學課程：使用 Visual Studio 建立 .NET 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="cf26b-103">Tutorial: Create a .NET console application using Visual Studio</span></span>

<span data-ttu-id="cf26b-104">本教學課程說明如何在 Visual Studio 2019 中建立和執行 .NET 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf26b-104">This tutorial shows how to create and run a .NET console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cf26b-105">先決條件</span><span class="sxs-lookup"><span data-stu-id="cf26b-105">Prerequisites</span></span>

- <span data-ttu-id="cf26b-106">已安裝 **.Net Core 跨平臺開發** 工作負載的 [Visual Studio 2019 16.8 版或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="cf26b-106">[Visual Studio 2019 version 16.8 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="cf26b-107">當您選取此工作負載時，會自動安裝 .NET 5.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="cf26b-107">The .NET 5.0 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="cf26b-108">如需詳細資訊，請參閱 [使用 Visual Studio 安裝 .NET SDK](../install/windows.md#install-with-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="cf26b-108">For more information, see [Install the .NET SDK with Visual Studio](../install/windows.md#install-with-visual-studio).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="cf26b-109">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="cf26b-109">Create the app</span></span>

<span data-ttu-id="cf26b-110">建立名為 "HelloWorld" 的 .NET 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="cf26b-110">Create a .NET console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="cf26b-111">啟動 Visual Studio 2019。</span><span class="sxs-lookup"><span data-stu-id="cf26b-111">Start Visual Studio 2019.</span></span>

1. <span data-ttu-id="cf26b-112">選取 [**工具**  >  **選項**  >  **環境**  >  **預覽功能**]，然後選取 **[在新專案中顯示所有 .net Core 範本] (需要重新開機)**。</span><span class="sxs-lookup"><span data-stu-id="cf26b-112">Select **Tools** > **Options** > **Environment** > **Preview features**, and then select **Show all .NET Core templates in the New project (requires restart)**.</span></span>

   :::image type="content" source="media/with-visual-studio/dotnet-options.png" alt-text="顯示所有 .NET 範本選項":::

1. <span data-ttu-id="cf26b-114">關閉並重新開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="cf26b-114">Close and reopen Visual Studio.</span></span>

1. <span data-ttu-id="cf26b-115">在 [開始] 頁面上，選擇 [ **建立新專案**]。</span><span class="sxs-lookup"><span data-stu-id="cf26b-115">On the start page, choose **Create a new project**.</span></span>

   :::image type="content" source="./media/with-visual-studio/start-window.png" alt-text="在 Visual Studio 開始] 頁面上選取 [建立新的專案] 按鈕":::

1. <span data-ttu-id="cf26b-117">在 [ **建立新專案** ] 頁面的 [搜尋] 方塊中，輸入 **主控台** 。</span><span class="sxs-lookup"><span data-stu-id="cf26b-117">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="cf26b-118">接著，選擇 [語言] 清單中的 [ **c #** ] 或 [ **Visual Basic** ]，然後從 [平臺] 清單中選擇 [ **所有平臺** ]。</span><span class="sxs-lookup"><span data-stu-id="cf26b-118">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="cf26b-119">選擇 [ **主控台應用程式** ] 範本，然後選擇 [ **下一步]**。</span><span class="sxs-lookup"><span data-stu-id="cf26b-119">Choose the **Console Application** template, and then choose **Next**.</span></span>

   :::image type="content" source="./media/with-visual-studio/create-new-project.png" alt-text="使用選取的篩選準則建立新的專案視窗":::

   > [!TIP]
   > <span data-ttu-id="cf26b-121">如果您看不到 .NET 範本，可能是缺少必要的工作負載。</span><span class="sxs-lookup"><span data-stu-id="cf26b-121">If you don't see the .NET templates, you're probably missing the required workload.</span></span> <span data-ttu-id="cf26b-122">在 [ **找不到您要尋找的專案嗎？** ] 訊息中，選擇 [ **安裝更多工具和功能** ] 連結。</span><span class="sxs-lookup"><span data-stu-id="cf26b-122">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="cf26b-123">Visual Studio 安裝程式隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="cf26b-123">The Visual Studio Installer opens.</span></span> <span data-ttu-id="cf26b-124">請確定您已安裝 **.Net Core 跨平臺開發** 工作負載。</span><span class="sxs-lookup"><span data-stu-id="cf26b-124">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

1. <span data-ttu-id="cf26b-125">在 [**設定您的新專案**] 對話方塊中，于 [**專案名稱**] 方塊中輸入 **HelloWorld** 。</span><span class="sxs-lookup"><span data-stu-id="cf26b-125">In the **Configure your new project** dialog,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="cf26b-126">接著，選擇 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="cf26b-126">Then choose **Create**.</span></span>

   :::image type="content" source="./media/with-visual-studio/configure-new-project.png" alt-text="使用 [專案名稱]、[位置] 和 [方案名稱] 欄位設定新的專案視窗":::

1. <span data-ttu-id="cf26b-128">在 [ **其他資訊** ] 對話方塊中，選取 [ **.Net 5.0 (目前的)**]，然後選取 [ **建立**]。</span><span class="sxs-lookup"><span data-stu-id="cf26b-128">In the **Additional information** dialog, select **.NET 5.0 (Current)**, and then select **Create**.</span></span>

   :::image type="content" source="media/with-visual-studio/additional-info.png" alt-text="其他資訊對話方塊":::

<span data-ttu-id="cf26b-130">此範本會建立簡單的 "Hello World" 應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf26b-130">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="cf26b-131">它會呼叫 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法來顯示 "Hello World！"</span><span class="sxs-lookup"><span data-stu-id="cf26b-131">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="cf26b-132">。</span><span class="sxs-lookup"><span data-stu-id="cf26b-132">in the console window.</span></span>

<span data-ttu-id="cf26b-133">範本 `Program` 程式碼會使用單一方法定義類別， `Main` 這個方法會採用 <xref:System.String> 陣列作為引數：</span><span class="sxs-lookup"><span data-stu-id="cf26b-133">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

```csharp
using System;

namespace HelloWorld
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.WriteLine("Hello World!");
        }
    }
}
```

```vb
Imports System

Module Program
    Sub Main(args As String())
        Console.WriteLine("Hello World!")
    End Sub
End Module
```

<span data-ttu-id="cf26b-134">`Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="cf26b-134">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="cf26b-135">在應用程式啟動時所提供的所有命令列引數，都會在 *args* 陣列中提供。</span><span class="sxs-lookup"><span data-stu-id="cf26b-135">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="cf26b-136">如果未顯示您想要使用的語言，請變更頁面頂端的語言選取器。</span><span class="sxs-lookup"><span data-stu-id="cf26b-136">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="cf26b-137">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="cf26b-137">Run the app</span></span>

1. <span data-ttu-id="cf26b-138">按下<kbd>Ctrl</kbd> + <kbd>F5</kbd>以執行程式，而不進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="cf26b-138">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

   <span data-ttu-id="cf26b-139">主控台視窗隨即開啟，並出現 "Hello World！" 文字</span><span class="sxs-lookup"><span data-stu-id="cf26b-139">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="cf26b-140">列印在螢幕上。</span><span class="sxs-lookup"><span data-stu-id="cf26b-140">printed on the screen.</span></span>

   :::image type="content" source="./media/with-visual-studio/hello-world-console.png" alt-text="主控台視窗顯示 Hello World，請按任意鍵以繼續":::

1. <span data-ttu-id="cf26b-142">按任意鍵關閉主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="cf26b-142">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="cf26b-143">增強應用程式</span><span class="sxs-lookup"><span data-stu-id="cf26b-143">Enhance the app</span></span>

<span data-ttu-id="cf26b-144">增強應用程式以提示使用者輸入其名稱，並將它與日期和時間一起顯示。</span><span class="sxs-lookup"><span data-stu-id="cf26b-144">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="cf26b-145">在 *Program.cs* 或 *Program* 中，以 `Main` 下列程式碼取代方法的內容，也就是呼叫的行 `Console.WriteLine` ：</span><span class="sxs-lookup"><span data-stu-id="cf26b-145">In *Program.cs* or *Program.vb*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::
   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="MainMethod":::

   <span data-ttu-id="cf26b-146">這段程式碼會在主控台視窗中顯示提示，並等候使用者輸入字串，然後按 <kbd>Enter</kbd> 鍵。</span><span class="sxs-lookup"><span data-stu-id="cf26b-146">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="cf26b-147">它會將此字串儲存在名為的變數中 `name` 。</span><span class="sxs-lookup"><span data-stu-id="cf26b-147">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="cf26b-148">它也會抓取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性值，其中包含目前的當地時間，並將它指派給 `date` Visual Basic) 中名為 (的變數 `currentDate` 。</span><span class="sxs-lookup"><span data-stu-id="cf26b-148">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date` (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="cf26b-149">它會在主控台視窗中顯示這些值。</span><span class="sxs-lookup"><span data-stu-id="cf26b-149">And it displays these values in the console window.</span></span> <span data-ttu-id="cf26b-150">最後，它會在主控台視窗中顯示提示，並呼叫 <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> 方法來等候使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="cf26b-150">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="cf26b-151">`\n` `vbCrLf` Visual Basic) 中的 (代表換行字元。</span><span class="sxs-lookup"><span data-stu-id="cf26b-151">The `\n` (`vbCrLf` in Visual Basic) represents a newline character.</span></span>

   <span data-ttu-id="cf26b-152">字串前面的貨幣符號 (`$`) 可讓您在字串中將運算式（例如變數名稱）放在大括弧中。</span><span class="sxs-lookup"><span data-stu-id="cf26b-152">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="cf26b-153">運算式值會插入字串以取代運算式。</span><span class="sxs-lookup"><span data-stu-id="cf26b-153">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="cf26b-154">這個語法稱為 [插補字串](../../csharp/language-reference/tokens/interpolated.md)。</span><span class="sxs-lookup"><span data-stu-id="cf26b-154">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="cf26b-155">按下<kbd>Ctrl</kbd> + <kbd>F5</kbd>以執行程式，而不進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="cf26b-155">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

1. <span data-ttu-id="cf26b-156">輸入名稱並按 <kbd>enter</kbd> 鍵，以回應提示。</span><span class="sxs-lookup"><span data-stu-id="cf26b-156">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="./media/with-visual-studio/hello-world-update.png" alt-text="含有已修改程式輸出的主控台視窗":::

1. <span data-ttu-id="cf26b-158">按任意鍵關閉主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="cf26b-158">Press any key to close the console window.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="cf26b-159">其他資源</span><span class="sxs-lookup"><span data-stu-id="cf26b-159">Additional resources</span></span>

- [<span data-ttu-id="cf26b-160">目前版本和長期支援版本</span><span class="sxs-lookup"><span data-stu-id="cf26b-160">Current releases and long-term support releases</span></span>](../releases-and-support.md#net-core-and-net-5-version-lifecycles)

## <a name="next-steps"></a><span data-ttu-id="cf26b-161">後續步驟</span><span class="sxs-lookup"><span data-stu-id="cf26b-161">Next steps</span></span>

<span data-ttu-id="cf26b-162">在本教學課程中，您已建立 .NET 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="cf26b-162">In this tutorial, you created a .NET console application.</span></span> <span data-ttu-id="cf26b-163">在下一個教學課程中，您將會對應用程式進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="cf26b-163">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="cf26b-164">使用 Visual Studio 來對 .NET 主控台應用程式進行偵錯工具</span><span class="sxs-lookup"><span data-stu-id="cf26b-164">Debug a .NET console application using Visual Studio</span></span>](debugging-with-visual-studio.md)
