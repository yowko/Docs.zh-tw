---
title: 使用 Visual Studio Code 建立 .NET 主控台應用程式
description: 瞭解如何使用 Visual Studio Code 和 .NET CLI 來建立 .NET 主控台應用程式。
ms.date: 11/17/2020
ms.openlocfilehash: dbbdf88b0c84089249eb7e446c25eddc11543c1a
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94915865"
---
# <a name="tutorial-create-a-net-console-application-using-visual-studio-code"></a><span data-ttu-id="dc0f2-103">教學課程：使用 Visual Studio Code 建立 .NET 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="dc0f2-103">Tutorial: Create a .NET console application using Visual Studio Code</span></span>

<span data-ttu-id="dc0f2-104">本教學課程說明如何使用 Visual Studio Code 和 .NET CLI 來建立和執行 .NET 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-104">This tutorial shows how to create and run a .NET console application by using Visual Studio Code and the .NET CLI.</span></span> <span data-ttu-id="dc0f2-105">專案工作（例如建立、編譯和執行專案）是使用 .NET CLI 來完成。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-105">Project tasks, such as creating, compiling, and running a project are done by using the .NET CLI.</span></span> <span data-ttu-id="dc0f2-106">您可以使用不同的程式碼編輯器來進行本教學課程，並在您想要的情況下在終端機中執行命令。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-106">You can follow this tutorial with a different code editor and run commands in a terminal if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="dc0f2-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="dc0f2-107">Prerequisites</span></span>

1. <span data-ttu-id="dc0f2-108">已安裝[c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能的[Visual Studio Code](https://code.visualstudio.com/) 。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-108">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="dc0f2-109">如需有關如何在 Visual Studio Code 上安裝擴充功能的詳細資訊，請參閱 [VS Code 擴充功能 Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery)。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-109">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="dc0f2-110">[.Net 5.0 SDK 或更新版本](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="dc0f2-110">The [.NET 5.0 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-the-app"></a><span data-ttu-id="dc0f2-111">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="dc0f2-111">Create the app</span></span>

<span data-ttu-id="dc0f2-112">建立名為 "HelloWorld" 的 .NET 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-112">Create a .NET console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="dc0f2-113">啟動 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-113">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="dc0f2-114">**File**  >  從主功能表選取 [ **File** 檔案 **開啟資料夾** (檔案開啟  >  **...** ] macOS) 。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-114">Select **File** > **Open Folder** (**File** > **Open...** on macOS) from the main menu.</span></span>

1. <span data-ttu-id="dc0f2-115">在 [ **開啟資料夾** ] 對話方塊中，建立 *HelloWorld* 資料夾，然後按一下 [ **選取資料夾** (在 macOS) **開啟** ]。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-115">In the **Open Folder** dialog, create a *HelloWorld* folder and click **Select Folder** (**Open** on macOS).</span></span>

   <span data-ttu-id="dc0f2-116">資料夾名稱預設會變成專案名稱和命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-116">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="dc0f2-117">您稍後會在教學課程中假設專案命名空間為的程式碼中加入程式碼 `HelloWorld` 。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-117">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

1. <span data-ttu-id="dc0f2-118">從主功能表中選取 [ **View** terminal]，以在 Visual Studio Code 中開啟 **終端** 機  >  **Terminal** 。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-118">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="dc0f2-119">**終端** 機會在 *HelloWorld* 資料夾中使用命令提示字元開啟。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-119">The **Terminal** opens with the command prompt in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="dc0f2-120">在 **終端** 機中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="dc0f2-120">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new console
   ```

<span data-ttu-id="dc0f2-121">此範本會建立簡單的 "Hello World" 應用程式。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-121">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="dc0f2-122">它會呼叫 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法，以 :::no-loc text="Hello World!"::: 在主控台視窗中顯示 ""。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-122">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display ":::no-loc text="Hello World!":::" in the console window.</span></span>

<span data-ttu-id="dc0f2-123">範本 `Program` 程式碼會使用單一方法定義類別， `Main` 這個方法會採用 <xref:System.String> 陣列作為引數：</span><span class="sxs-lookup"><span data-stu-id="dc0f2-123">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="dc0f2-124">`Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-124">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="dc0f2-125">在應用程式啟動時所提供的所有命令列引數，都會在 *args* 陣列中提供。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-125">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="dc0f2-126">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="dc0f2-126">Run the app</span></span>

<span data-ttu-id="dc0f2-127">在 **終端** 機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="dc0f2-127">Run the following command in the **Terminal**:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="dc0f2-128">程式會顯示 "Hello World！"</span><span class="sxs-lookup"><span data-stu-id="dc0f2-128">The program displays "Hello World!"</span></span> <span data-ttu-id="dc0f2-129">並結束。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-129">and ends.</span></span>

![DotNet 執行命令](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a><span data-ttu-id="dc0f2-131">增強應用程式</span><span class="sxs-lookup"><span data-stu-id="dc0f2-131">Enhance the app</span></span>

<span data-ttu-id="dc0f2-132">增強應用程式以提示使用者輸入其名稱，並將它與日期和時間一起顯示。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-132">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="dc0f2-133">按一下 *Program.cs* 來開啟它。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-133">Open *Program.cs* by clicking on it.</span></span>

   <span data-ttu-id="dc0f2-134">在 Visual Studio Code 中第一次開啟 C# 檔案時，會在編輯器中載入 [OmniSharp](https://www.omnisharp.net/)。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-134">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

   ![開啟 Program.cs 檔案](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="dc0f2-136">當 Visual Studio Code 提示您新增遺失的資產來建立和偵測應用程式時，請選取 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-136">Select **Yes** when Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span>

   ![遺失資產的提示](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="dc0f2-138">以 `Main` 下列程式碼取代 *Program.cs* 中的方法內容，這是呼叫的行 `Console.WriteLine` ：</span><span class="sxs-lookup"><span data-stu-id="dc0f2-138">Replace the contents of the `Main` method in *Program.cs*, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="MainMethod":::

   <span data-ttu-id="dc0f2-139">這段程式碼會在主控台視窗中顯示提示，並等候使用者輸入字串，然後按 <kbd>Enter</kbd> 鍵。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-139">This code displays a prompt in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="dc0f2-140">它會將此字串儲存在名為的變數中 `name` 。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-140">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="dc0f2-141">此程式碼也會擷取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性的值，其中包含目前的當地時間，並將它指派至名稱為 `date` 的變數。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-141">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="dc0f2-142">它會在主控台視窗中顯示這些值。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-142">And it displays these values in the console window.</span></span> <span data-ttu-id="dc0f2-143">最後，它會在主控台視窗中顯示提示，並呼叫 <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> 方法來等候使用者輸入。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-143">Finally, it displays a prompt in the console window and calls the <xref:System.Console.ReadKey(System.Boolean)?displayProperty=nameWithType> method to wait for user input.</span></span>

   <span data-ttu-id="dc0f2-144">`\n`代表換行字元。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-144">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="dc0f2-145">字串前面的貨幣符號 (`$`) 可讓您在字串中將運算式（例如變數名稱）放在大括弧中。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-145">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="dc0f2-146">運算式值會插入字串以取代運算式。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-146">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="dc0f2-147">這個語法稱為 [插補字串](../../csharp/language-reference/tokens/interpolated.md)。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-147">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="dc0f2-148">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-148">Save your changes.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="dc0f2-149">在 Visual Studio Code 中，您必須明確地儲存變更。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-149">In Visual Studio Code, you have to explicitly save changes.</span></span> <span data-ttu-id="dc0f2-150">不同于 Visual Studio，當您建立並執行應用程式時，不會自動儲存檔案變更。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-150">Unlike Visual Studio, file changes are not automatically saved when you build and run an app.</span></span>

1. <span data-ttu-id="dc0f2-151">重新執行程式：</span><span class="sxs-lookup"><span data-stu-id="dc0f2-151">Run the program again:</span></span>

   ```dotnetcli
   dotnet run
   ```

1. <span data-ttu-id="dc0f2-152">輸入名稱並按 <kbd>enter</kbd> 鍵，以回應提示。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-152">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="已修改之程式輸出的終端視窗":::

1. <span data-ttu-id="dc0f2-154">按任意鍵以結束該程式。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-154">Press any key to exit the program.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="dc0f2-155">其他資源</span><span class="sxs-lookup"><span data-stu-id="dc0f2-155">Additional resources</span></span>

- [<span data-ttu-id="dc0f2-156">設定 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="dc0f2-156">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a><span data-ttu-id="dc0f2-157">後續步驟</span><span class="sxs-lookup"><span data-stu-id="dc0f2-157">Next steps</span></span>

<span data-ttu-id="dc0f2-158">在本教學課程中，您已建立 .NET 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-158">In this tutorial, you created a .NET console application.</span></span> <span data-ttu-id="dc0f2-159">在下一個教學課程中，您將會對應用程式進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="dc0f2-159">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="dc0f2-160">使用 Visual Studio Code 來對 .NET 主控台應用程式進行偵錯工具</span><span class="sxs-lookup"><span data-stu-id="dc0f2-160">Debug a .NET console application using Visual Studio Code</span></span>](debugging-with-visual-studio-code.md)
