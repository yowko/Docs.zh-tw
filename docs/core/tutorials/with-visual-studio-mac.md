---
title: 使用 Visual Studio for Mac 建立 .NET Core 主控台應用程式
description: 瞭解如何使用 Visual Studio for Mac 來建立 .NET Core 主控台應用程式。
ms.date: 06/02/2020
ms.openlocfilehash: 8ffcb05ad85f53180ca1aaefbd2dfc7496946142
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867655"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="8e2ec-103">教學課程：使用 Visual Studio for Mac 建立 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="8e2ec-103">Tutorial: Create a .NET Core console application using Visual Studio for Mac</span></span>

<span data-ttu-id="8e2ec-104">本教學課程說明如何使用 Visual Studio for Mac 來建立和執行 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-104">This tutorial shows how to create and run a .NET Core console application using Visual Studio for Mac.</span></span>

> [!NOTE]
> <span data-ttu-id="8e2ec-105">我們非常重視您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-105">Your feedback is highly valued.</span></span> <span data-ttu-id="8e2ec-106">您有兩種方式可以提供意見反應給 Visual Studio for Mac 開發小組：</span><span class="sxs-lookup"><span data-stu-id="8e2ec-106">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> * <span data-ttu-id="8e2ec-107">在 Visual Studio for Mac 中， **Help**  >  **Report a Problem**從功能表中選取 [說明]，或從歡迎畫面回報**問題**，這會開啟用來提出錯誤報表的視窗。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-107">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which will open a window for filing a bug report.</span></span> <span data-ttu-id="8e2ec-108">您可在[開發人員社群](https://developercommunity.visualstudio.com/spaces/8/index.html)入口網站追蹤您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-108">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/8/index.html) portal.</span></span>
> * <span data-ttu-id="8e2ec-109">若要提出建議，請**Help**  >  從功能表中選取 [說明]**提供建議**，或從歡迎畫面**提供**建議，這會帶您前往[Visual Studio for Mac 開發人員社群網頁](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-109">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which will take you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8e2ec-110">先決條件</span><span class="sxs-lookup"><span data-stu-id="8e2ec-110">Prerequisites</span></span>

* <span data-ttu-id="8e2ec-111">[Visual Studio for Mac 8.6 版或更新版本](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-111">[Visual Studio for Mac version 8.6 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="8e2ec-112">選取安裝 .NET Core 的選項。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-112">Select the option to install .NET Core.</span></span> <span data-ttu-id="8e2ec-113">安裝 Xamarin 是 .NET Core 開發的選擇性選項。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-113">Installing Xamarin is optional for .NET Core development.</span></span> <span data-ttu-id="8e2ec-114">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="8e2ec-114">For more information, see the following resources:</span></span>

  * <span data-ttu-id="8e2ec-115">[教學課程：安裝 Visual Studio for Mac](/visualstudio/mac/installation)。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-115">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="8e2ec-116">[支援的 macOS 版本](../install/dependencies.md?pivots=os-macos)。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-116">[Supported macOS versions](../install/dependencies.md?pivots=os-macos).</span></span>
  * <span data-ttu-id="8e2ec-117">[Visual Studio for Mac 支援的 .Net Core 版本](/visualstudio/mac/net-core-support)。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-117">[.NET Core versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-the-app"></a><span data-ttu-id="8e2ec-118">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="8e2ec-118">Create the app</span></span>

<span data-ttu-id="8e2ec-119">建立名為 "HelloWorld" 的 .NET Core 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-119">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="8e2ec-120">開始 Visual Studio for Mac。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-120">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="8e2ec-121">在 [開始] 視窗中選取 [ **新增** ]。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-121">Select **New** in the start window.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="Visual Studio for Mac [開始] 畫面上的 [新增] 按鈕":::

1. <span data-ttu-id="8e2ec-123">在 [**新增專案**] 對話方塊的 [Web]**和 [主控台**] 節點底下，選取 [**應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-123">In the **New Project** dialog, select **App** under the **Web and Console** node.</span></span> <span data-ttu-id="8e2ec-124">選取 [ **主控台應用程式** ] 範本，然後選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-124">Select the **Console Application** template, and select **Next**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-dialog.png" alt-text="[新增專案] 範本清單":::

1. <span data-ttu-id="8e2ec-126">在 [**設定您的新主控台應用程式**] 對話方塊的 [**目標 Framework** ] 下拉式清單中，選取 [ **.net Core 3.1**]，然後選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-126">In the **Target Framework** drop-down of the **Configure your new Console Application** dialog, select **.NET Core 3.1**, and select **Next**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/target-framework.png" alt-text="選取目標 Framework":::

1. <span data-ttu-id="8e2ec-128">輸入 "HelloWorld" 作為 **專案名稱**，然後選取 [ **建立**]。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-128">Type "HelloWorld" for the **Project Name**, and select **Create**.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-new-options.png" alt-text="設定新主控台應用程式對話方塊":::

<span data-ttu-id="8e2ec-130">此範本會建立簡單的 "Hello World" 應用程式。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-130">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="8e2ec-131">它會呼叫 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法來顯示 "Hello World！"</span><span class="sxs-lookup"><span data-stu-id="8e2ec-131">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="8e2ec-132">在終端機視窗中。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-132">in the terminal window.</span></span>

<span data-ttu-id="8e2ec-133">範本 `Program` 程式碼會使用單一方法定義類別， `Main` 這個方法會採用 <xref:System.String> 陣列作為引數：</span><span class="sxs-lookup"><span data-stu-id="8e2ec-133">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="8e2ec-134">`Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-134">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="8e2ec-135">當應用程式啟動時所提供的任何命令列引數都可在陣列中使用 `args` 。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-135">Any command-line arguments supplied when the application is launched are available in the `args` array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="8e2ec-136">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="8e2ec-136">Run the app</span></span>

1. <span data-ttu-id="8e2ec-137">按<kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>命令</kbd> + <kbd>輸入</kbd>) 來執行應用程式，而不進行任何偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-137">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run the app without debugging.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/visual-studio-mac-output.png" alt-text="終端機會顯示 Hello World！":::

1. <span data-ttu-id="8e2ec-139">關閉 **終端** 機視窗。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-139">Close the **Terminal** window.</span></span>

## <a name="enhance-the-app"></a><span data-ttu-id="8e2ec-140">增強應用程式</span><span class="sxs-lookup"><span data-stu-id="8e2ec-140">Enhance the app</span></span>

<span data-ttu-id="8e2ec-141">增強應用程式以提示使用者輸入其名稱，並將它與日期和時間一起顯示。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-141">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="8e2ec-142">在 *Program.cs*中， `Main` 使用下列程式碼取代方法的內容，也就是呼叫的行 `Console.WriteLine` ：</span><span class="sxs-lookup"><span data-stu-id="8e2ec-142">In *Program.cs*, replace the contents of the `Main` method, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   <span data-ttu-id="8e2ec-143">這段程式碼會在主控台視窗中顯示提示，並等候使用者輸入字串，然後按 <kbd>enter</kbd> 鍵。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-143">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>enter</kbd> key.</span></span> <span data-ttu-id="8e2ec-144">它會將此字串儲存在名為的變數中 `name` 。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-144">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="8e2ec-145">此程式碼也會擷取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性的值，其中包含目前的當地時間，並將它指派至名稱為 `date` 的變數。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-145">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="8e2ec-146">它會在主控台視窗中顯示這些值。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-146">And it displays these values in the console window.</span></span> <span data-ttu-id="8e2ec-147">最後，它會在主控台視窗中顯示提示，並呼叫 <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> 方法來等候使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-147">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="8e2ec-148">`\n`代表換行字元。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-148">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="8e2ec-149">字串前面的貨幣符號 (`$`) 可讓您在字串中將運算式（例如變數名稱）放在大括弧中。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-149">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="8e2ec-150">運算式值會插入字串以取代運算式。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-150">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="8e2ec-151">這個語法稱為 [插補字串](../../csharp/language-reference/tokens/interpolated.md)。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-151">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="8e2ec-152">按<kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd> + <kbd>命令</kbd> + <kbd>輸入</kbd>) 來執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-152">Press <kbd>⌥</kbd><kbd>⌘</kbd><kbd>↵</kbd> (<kbd>option</kbd>+<kbd>command</kbd>+<kbd>enter</kbd>) to run the app.</span></span>

1. <span data-ttu-id="8e2ec-153">輸入名稱並按 <kbd>enter</kbd>，以回應提示。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-153">Respond to the prompt by entering a name and pressing <kbd>enter</kbd>.</span></span>

   :::image type="content" source="media/with-visual-studio-mac/hello-world-update.png" alt-text="終端機顯示修改過的程式輸出":::

1. <span data-ttu-id="8e2ec-155">關閉終端機。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-155">Close the terminal.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8e2ec-156">後續步驟</span><span class="sxs-lookup"><span data-stu-id="8e2ec-156">Next steps</span></span>

<span data-ttu-id="8e2ec-157">在本教學課程中，您已建立 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-157">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="8e2ec-158">在下一個教學課程中，您將會對應用程式進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="8e2ec-158">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8e2ec-159">使用 Visual Studio for Mac 來對 .NET Core 主控台應用程式進行偵錯工具</span><span class="sxs-lookup"><span data-stu-id="8e2ec-159">Debug a .NET Core console application using Visual Studio for Mac</span></span>](debugging-with-visual-studio-mac.md)
