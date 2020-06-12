---
title: 使用 Visual Studio 建立 .NET Core 主控台應用程式
description: '瞭解如何使用 Visual Studio，以 c # 或 Visual Basic 建立 .NET Core 主控台應用程式。'
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 7ef8e17b8a42defc0858123332976d30c83f20c8
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84700428"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="3641d-103">教學課程：使用 Visual Studio 建立 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="3641d-103">Tutorial: Create a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="3641d-104">本教學課程說明如何在 Visual Studio 2019 中建立及執行 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="3641d-104">This tutorial shows how to create and run a .NET Core console application in Visual Studio 2019.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3641d-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="3641d-105">Prerequisites</span></span>

- <span data-ttu-id="3641d-106">已安裝 **.Net Core 跨平臺開發**工作負載的[Visual Studio 2019 16.6 版或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="3641d-106">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="3641d-107">當您選取此工作負載時，會自動安裝 .NET Core 3.1 SDK。</span><span class="sxs-lookup"><span data-stu-id="3641d-107">The .NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="3641d-108">如需詳細資訊，請參閱[使用 Visual Studio 安裝 .NET Core SDK](../install/sdk.md?pivots=os-windows#install-with-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="3641d-108">For more information, see [Install the .NET Core SDK with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="3641d-109">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="3641d-109">Create the app</span></span>

<span data-ttu-id="3641d-110">建立名為 "HelloWorld" 的 .NET Core 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="3641d-110">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="3641d-111">啟動 Visual Studio 2019。</span><span class="sxs-lookup"><span data-stu-id="3641d-111">Start Visual Studio 2019.</span></span>

1. <span data-ttu-id="3641d-112">在 [開始] 頁面上，選擇 [**建立新專案**]。</span><span class="sxs-lookup"><span data-stu-id="3641d-112">On the start page, choose **Create a new project**.</span></span>

   ![在 Visual Studio 起始頁上選取 [建立新專案] 按鈕](./media/with-visual-studio/start-window.png)

1. <span data-ttu-id="3641d-114">在 [**建立新專案**] 頁面的 [搜尋] 方塊中，輸入**主控台**。</span><span class="sxs-lookup"><span data-stu-id="3641d-114">On the **Create a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="3641d-115">接著，從 [語言] 清單中選擇 [ **c #** ] 或 [ **Visual Basic** ]，然後從 [平臺] 清單中選擇 [**所有平臺**]。</span><span class="sxs-lookup"><span data-stu-id="3641d-115">Next, choose **C#** or **Visual Basic** from the language list, and then choose **All platforms** from the platform list.</span></span> <span data-ttu-id="3641d-116">選擇 [**主控台應用程式（.Net Core）** ] 範本，然後選擇 [**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="3641d-116">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   ![建立已選取篩選的新專案視窗](./media/with-visual-studio/create-new-project.png)

   > [!TIP]
   > <span data-ttu-id="3641d-118">如果您看不到 .NET Core 範本，可能會遺失必要的工作負載。</span><span class="sxs-lookup"><span data-stu-id="3641d-118">If you don't see the .NET Core templates, you're probably missing the required workload.</span></span> <span data-ttu-id="3641d-119">在 [**找不到您要尋找的內容嗎？** ] 訊息底下，選擇 [**安裝更多工具和功能**] 連結。</span><span class="sxs-lookup"><span data-stu-id="3641d-119">Under the **Not finding what you're looking for?** message, choose the **Install more tools and features** link.</span></span> <span data-ttu-id="3641d-120">Visual Studio 安裝程式隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="3641d-120">The Visual Studio Installer opens.</span></span> <span data-ttu-id="3641d-121">請確定您已安裝 **.Net Core 跨平臺開發**工作負載。</span><span class="sxs-lookup"><span data-stu-id="3641d-121">Make sure you have the **.NET Core cross-platform development** workload installed.</span></span>

1. <span data-ttu-id="3641d-122">在 [**設定您的新專案**] 對話方塊的 [**專案名稱**] 方塊中，輸入**HelloWorld** 。</span><span class="sxs-lookup"><span data-stu-id="3641d-122">In the **Configure your new project** dialog,  enter **HelloWorld** in the **Project name** box.</span></span> <span data-ttu-id="3641d-123">接著，選擇 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="3641d-123">Then choose **Create**.</span></span>

   ![以 [專案名稱]、[位置] 和 [方案名稱] 欄位設定新的專案視窗](./media/with-visual-studio/configure-new-project.png)

<span data-ttu-id="3641d-125">此範本會建立簡單的 "Hello World" 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3641d-125">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="3641d-126">它會呼叫 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法來顯示 "Hello World！"</span><span class="sxs-lookup"><span data-stu-id="3641d-126">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="3641d-127">。</span><span class="sxs-lookup"><span data-stu-id="3641d-127">in the console window.</span></span>

<span data-ttu-id="3641d-128">範本程式碼會定義具有單一方法的類別，其 `Program` `Main` 接受 <xref:System.String> 陣列做為引數：</span><span class="sxs-lookup"><span data-stu-id="3641d-128">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="3641d-129">`Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="3641d-129">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="3641d-130">在應用程式啟動時所提供的所有命令列引數，都會在 *args* 陣列中提供。</span><span class="sxs-lookup"><span data-stu-id="3641d-130">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="3641d-131">如果未顯示您想要使用的語言，請變更頁面頂端的 [語言選取器]。</span><span class="sxs-lookup"><span data-stu-id="3641d-131">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="3641d-132">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="3641d-132">Run the app</span></span>

1. <span data-ttu-id="3641d-133">按<kbd>Shift</kbd> + <kbd>F5</kbd>以執行程式而不進行偵測。</span><span class="sxs-lookup"><span data-stu-id="3641d-133">Press <kbd>Shift</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

   <span data-ttu-id="3641d-134">主控台視窗隨即開啟，並出現 "Hello World！" 文字</span><span class="sxs-lookup"><span data-stu-id="3641d-134">A console window opens with the text "Hello World!"</span></span> <span data-ttu-id="3641d-135">列印在畫面上，而部分 Visual Studio 的調試資訊。</span><span class="sxs-lookup"><span data-stu-id="3641d-135">printed on the screen and some Visual Studio debug information.</span></span>

   ![主控台視窗顯示 Hello World，請按任意鍵以繼續](./media/with-visual-studio/hello-world-console.png)

1. <span data-ttu-id="3641d-137">按任意鍵關閉主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="3641d-137">Press any key to close the console window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="3641d-138">增強應用程式</span><span class="sxs-lookup"><span data-stu-id="3641d-138">Enhance the app</span></span>

<span data-ttu-id="3641d-139">增強應用程式，以提示使用者輸入其名稱，並連同日期和時間一起顯示。</span><span class="sxs-lookup"><span data-stu-id="3641d-139">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="3641d-140">在*Program.cs*或*Program .vb*中，以 `Main` 下列程式碼取代方法的內容，也就是呼叫的那一行 `Console.WriteLine` ：</span><span class="sxs-lookup"><span data-stu-id="3641d-140">In *Program.cs* or *Program.vb*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   [!code-csharp[GettingStarted#1](./snippets/with-visual-studio/csharp/Program.cs#1)]
   [!code-vb[GettingStarted#1](./snippets/with-visual-studio/vb/Program.vb#1)]

   <span data-ttu-id="3641d-141">此程式碼會在主控台中顯示「What is your name?」，</span><span class="sxs-lookup"><span data-stu-id="3641d-141">This code displays "What is your name?"</span></span> <span data-ttu-id="3641d-142">在主控台視窗中，等候使用者輸入後面接著<kbd>Enter</kbd>鍵的字串。</span><span class="sxs-lookup"><span data-stu-id="3641d-142">in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="3641d-143">它會將此字串儲存在名為的變數中 `name` 。</span><span class="sxs-lookup"><span data-stu-id="3641d-143">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="3641d-144">它也會抓取屬性的值 <xref:System.DateTime.Now?displayProperty=nameWithType> ，其中包含目前的本地時間，並將它指派給名為的變數 `date` （ `currentDate` 在 Visual Basic 中）。</span><span class="sxs-lookup"><span data-stu-id="3641d-144">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date` (`currentDate` in Visual Basic).</span></span> <span data-ttu-id="3641d-145">最後，它會在主控台視窗中顯示這些值。</span><span class="sxs-lookup"><span data-stu-id="3641d-145">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="3641d-146">`\n`（ `vbCrLf` 在 Visual Basic 中）代表分行符號。</span><span class="sxs-lookup"><span data-stu-id="3641d-146">The `\n` (`vbCrLf` in Visual Basic) represents a newline character.</span></span>

   <span data-ttu-id="3641d-147">字串前面的貨幣符號（ `$` ）可讓您在字串中的大括弧內放置運算式，例如變數名稱。</span><span class="sxs-lookup"><span data-stu-id="3641d-147">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="3641d-148">運算式值會插入字串中，以取代運算式。</span><span class="sxs-lookup"><span data-stu-id="3641d-148">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="3641d-149">此語法稱為「插入[字串](../../csharp/language-reference/tokens/interpolated.md)」。</span><span class="sxs-lookup"><span data-stu-id="3641d-149">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="3641d-150">按<kbd>Shift</kbd> + <kbd>F5</kbd>以執行程式而不進行偵測。</span><span class="sxs-lookup"><span data-stu-id="3641d-150">Press <kbd>Shift</kbd>+<kbd>F5</kbd> to run the program without debugging.</span></span>

1. <span data-ttu-id="3641d-151">輸入名稱並按<kbd>enter</kbd>鍵，以回應提示。</span><span class="sxs-lookup"><span data-stu-id="3641d-151">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   ![含有已修改程式輸出的主控台視窗](./media/with-visual-studio/hello-world-update.png)

1. <span data-ttu-id="3641d-153">按任意鍵關閉主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="3641d-153">Press any key to close the console window.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3641d-154">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3641d-154">Next steps</span></span>

<span data-ttu-id="3641d-155">在本教學課程中，您已建立 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="3641d-155">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="3641d-156">在下一個教學課程中，您會對應用程式進行 debug。</span><span class="sxs-lookup"><span data-stu-id="3641d-156">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3641d-157">在 Visual Studio 中，對 .NET Core 主控台應用程式進行 Debug</span><span class="sxs-lookup"><span data-stu-id="3641d-157">Debug a .NET Core console application in Visual Studio</span></span>](debugging-with-visual-studio.md)
