---
title: 使用 Visual Studio 建立 .NET Core 主控台應用程式
description: '瞭解如何使用 Visual Studio 以 c # 或 Visual Basic 來建立 .NET Core 主控台應用程式。'
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: d543a05eb00a59c5c08ada28fc8392875385aa8a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537531"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="c5442-103">教學課程：使用 Visual Studio 建立 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="c5442-103">Tutorial: Create a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="c5442-104">本教學課程說明如何在 Visual Studio 2019 中建立和執行 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="c5442-104">This tutorial shows how to create and run a .NET Core console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c5442-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="c5442-105">Prerequisites</span></span>

- <span data-ttu-id="c5442-106">已安裝 **.Net Core 跨平臺開發**工作負載的[Visual Studio 2019 16.6 版或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="c5442-106">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="c5442-107">當您選取此工作負載時，會自動安裝 .NET Core 3.1 SDK。</span><span class="sxs-lookup"><span data-stu-id="c5442-107">The .NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="c5442-108">如需詳細資訊，請參閱 [使用 Visual Studio 安裝 .NET Core SDK](../install/windows.md#install-with-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="c5442-108">For more information, see [Install the .NET Core SDK with Visual Studio](../install/windows.md#install-with-visual-studio).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="c5442-109">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="c5442-109">Create the app</span></span>

<span data-ttu-id="c5442-110">建立名為 "HelloWorld" 的 .NET Core 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="c5442-110">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="c5442-111">啟動 Visual Studio 2019。</span><span class="sxs-lookup"><span data-stu-id="c5442-111">Start Visual Studio 2019.</span></span>

1. <span data-ttu-id="c5442-112">在 [開始] 頁面上，選擇 [ **建立新專案**]。</span><span class="sxs-lookup"><span data-stu-id="c5442-112">On the start page, choose **Create a new project**.</span></span>

   ![在 Visual Studio 開始] 頁面上選取 [建立新的專案] 按鈕](./media/with-visual-studio/start-window.png)

1. <span data-ttu-id="c5442-114">在 [ **建立新專案** ] 頁面的 [搜尋] 方塊中，輸入 **主控台** 。</span><span class="sxs-lookup"><span data-stu-id="c5442-114">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="c5442-115">接著，選擇 [語言] 清單中的 [ **c #** ] 或 [ **Visual Basic** ]，然後從 [平臺] 清單中選擇 [ **所有平臺** ]。</span><span class="sxs-lookup"><span data-stu-id="c5442-115">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="c5442-116">選擇 \*\* ( .Net Core) 範本的主控台應用程式 \*\* ，然後選擇 [ **下一步]**。</span><span class="sxs-lookup"><span data-stu-id="c5442-116">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   ![使用選取的篩選準則建立新的專案視窗](./media/with-visual-studio/create-new-project.png)

   > [!TIP]
   > <span data-ttu-id="c5442-118">如果您看不到 .NET Core 範本，可能是缺少必要的工作負載。</span><span class="sxs-lookup"><span data-stu-id="c5442-118">If you don't see the .NET Core templates, you're probably missing the required workload.</span></span> <span data-ttu-id="c5442-119">在 [ **找不到您要尋找的專案嗎？** ] 訊息中，選擇 [ **安裝更多工具和功能** ] 連結。</span><span class="sxs-lookup"><span data-stu-id="c5442-119">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="c5442-120">Visual Studio 安裝程式隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="c5442-120">The Visual Studio Installer opens.</span></span> <span data-ttu-id="c5442-121">請確定您已安裝 **.Net Core 跨平臺開發** 工作負載。</span><span class="sxs-lookup"><span data-stu-id="c5442-121">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

1. <span data-ttu-id="c5442-122">在 [**設定您的新專案**] 對話方塊中，于 [**專案名稱**] 方塊中輸入**HelloWorld** 。</span><span class="sxs-lookup"><span data-stu-id="c5442-122">In the **Configure your new project** dialog,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="c5442-123">接著，選擇 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="c5442-123">Then choose **Create**.</span></span>

   ![使用 [專案名稱]、[位置] 和 [方案名稱] 欄位設定新的專案視窗](./media/with-visual-studio/configure-new-project.png)

<span data-ttu-id="c5442-125">此範本會建立簡單的 "Hello World" 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c5442-125">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="c5442-126">它會呼叫 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法來顯示 "Hello World！"</span><span class="sxs-lookup"><span data-stu-id="c5442-126">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="c5442-127">。</span><span class="sxs-lookup"><span data-stu-id="c5442-127">in the console window.</span></span>

<span data-ttu-id="c5442-128">範本 `Program` 程式碼會使用單一方法定義類別， `Main` 這個方法會採用 <xref:System.String> 陣列作為引數：</span><span class="sxs-lookup"><span data-stu-id="c5442-128">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="c5442-129">`Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="c5442-129">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="c5442-130">在應用程式啟動時所提供的所有命令列引數，都會在 *args* 陣列中提供。</span><span class="sxs-lookup"><span data-stu-id="c5442-130">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="c5442-131">如果未顯示您想要使用的語言，請變更頁面頂端的語言選取器。</span><span class="sxs-lookup"><span data-stu-id="c5442-131">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="c5442-132">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="c5442-132">Run the app</span></span>

1. <span data-ttu-id="c5442-133">按下<kbd>Ctrl</kbd> + <kbd>F5</kbd>以執行程式，而不進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="c5442-133">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

   <span data-ttu-id="c5442-134">主控台視窗隨即開啟，並出現 "Hello World！" 文字</span><span class="sxs-lookup"><span data-stu-id="c5442-134">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="c5442-135">列印在畫面上，而某些 Visual Studio 的 debug 資訊。</span><span class="sxs-lookup"><span data-stu-id="c5442-135">printed on the screen and some Visual Studio debug information.</span></span>

   ![主控台視窗顯示 Hello World，請按任意鍵以繼續](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="c5442-137">按任意鍵關閉主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="c5442-137">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="c5442-138">增強應用程式</span><span class="sxs-lookup"><span data-stu-id="c5442-138">Enhance the app</span></span>

<span data-ttu-id="c5442-139">增強應用程式以提示使用者輸入其名稱，並將它與日期和時間一起顯示。</span><span class="sxs-lookup"><span data-stu-id="c5442-139">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="c5442-140">在 *Program.cs* 或 *Program*中，以 `Main` 下列程式碼取代方法的內容，也就是呼叫的行 `Console.WriteLine` ：</span><span class="sxs-lookup"><span data-stu-id="c5442-140">In *Program.cs* or *Program.vb*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::
   :::code language="vb" source="./snippets/with-visual-studio/vb/Program.vb" id="MainMethod":::

   <span data-ttu-id="c5442-141">這段程式碼會在主控台視窗中顯示提示，並等候使用者輸入字串，然後按 <kbd>Enter</kbd> 鍵。</span><span class="sxs-lookup"><span data-stu-id="c5442-141">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="c5442-142">它會將此字串儲存在名為的變數中 `name` 。</span><span class="sxs-lookup"><span data-stu-id="c5442-142">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="c5442-143">它也會抓取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性值，其中包含目前的當地時間，並將它指派給 `date` Visual Basic) 中名為 (的變數 `currentDate` 。</span><span class="sxs-lookup"><span data-stu-id="c5442-143">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date` (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="c5442-144">它會在主控台視窗中顯示這些值。</span><span class="sxs-lookup"><span data-stu-id="c5442-144">And it displays these values in the console window.</span></span> <span data-ttu-id="c5442-145">最後，它會在主控台視窗中顯示提示，並呼叫 <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> 方法來等候使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="c5442-145">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="c5442-146">`\n` `vbCrLf` Visual Basic) 中的 (代表換行字元。</span><span class="sxs-lookup"><span data-stu-id="c5442-146">The `\n` (`vbCrLf` in Visual Basic) represents a newline character.</span></span>

   <span data-ttu-id="c5442-147">字串前面的貨幣符號 (`$`) 可讓您在字串中將運算式（例如變數名稱）放在大括弧中。</span><span class="sxs-lookup"><span data-stu-id="c5442-147">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="c5442-148">運算式值會插入字串以取代運算式。</span><span class="sxs-lookup"><span data-stu-id="c5442-148">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="c5442-149">這個語法稱為 [插補字串](../../csharp/language-reference/tokens/interpolated.md)。</span><span class="sxs-lookup"><span data-stu-id="c5442-149">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="c5442-150">按下<kbd>Ctrl</kbd> + <kbd>F5</kbd>以執行程式，而不進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="c5442-150">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

1. <span data-ttu-id="c5442-151">輸入名稱並按 <kbd>enter</kbd> 鍵，以回應提示。</span><span class="sxs-lookup"><span data-stu-id="c5442-151">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   ![含有已修改程式輸出的主控台視窗](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="c5442-153">按任意鍵關閉主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="c5442-153">Press any key to close the console window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c5442-154">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c5442-154">Next steps</span></span>

<span data-ttu-id="c5442-155">在本教學課程中，您已建立 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="c5442-155">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="c5442-156">在下一個教學課程中，您將會對應用程式進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="c5442-156">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c5442-157">使用 Visual Studio 來對 .NET Core 主控台應用程式進行偵錯工具</span><span class="sxs-lookup"><span data-stu-id="c5442-157">Debug a .NET Core console application using Visual Studio</span></span>](debugging-with-visual-studio.md)
