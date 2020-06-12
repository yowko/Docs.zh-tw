---
title: 使用 Visual Studio Code 建立 .NET Core 主控台應用程式
description: 瞭解如何使用 Visual Studio Code 和 .NET Core CLI 建立 .NET Core 主控台應用程式。
ms.date: 05/22/2020
ms.openlocfilehash: 6d8f9adb2f77dbfd2d1cf54c80f1cdea582b1d96
ms.sourcegitcommit: f6350c2c542e6edd52d7e9d6667b96d85d810e67
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84717506"
---
# <a name="tutorial-create-a-net-core-console-application-using-visual-studio-code"></a><span data-ttu-id="c70d7-103">教學課程：使用 Visual Studio Code 建立 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="c70d7-103">Tutorial: Create a .NET Core console application using Visual Studio Code</span></span>

<span data-ttu-id="c70d7-104">本教學課程說明如何使用 Visual Studio Code 和 .NET Core CLI 來建立和執行 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="c70d7-104">This tutorial shows how to create and run a .NET Core console application by using Visual Studio Code and the .NET Core CLI.</span></span> <span data-ttu-id="c70d7-105">專案工作，例如建立、編譯和執行專案，都是使用 .NET Core CLI 來完成。</span><span class="sxs-lookup"><span data-stu-id="c70d7-105">Project tasks, such as creating, compiling, and running a project are done by using the .NET Core CLI.</span></span> <span data-ttu-id="c70d7-106">您可以使用不同的程式碼編輯器來遵循此教學課程，並視需要在終端機中執行命令。</span><span class="sxs-lookup"><span data-stu-id="c70d7-106">You can follow this tutorial with a different code editor and run commands in a terminal if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c70d7-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="c70d7-107">Prerequisites</span></span>

1. <span data-ttu-id="c70d7-108">已安裝[c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能的[Visual Studio Code](https://code.visualstudio.com/) 。</span><span class="sxs-lookup"><span data-stu-id="c70d7-108">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="c70d7-109">如需有關如何在 Visual Studio Code 上安裝延伸模組的詳細資訊，請參閱[VS Code 延伸模組 Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery)。</span><span class="sxs-lookup"><span data-stu-id="c70d7-109">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="c70d7-110">[.Net Core 3.1 SDK 或更新版本](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="c70d7-110">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-the-app"></a><span data-ttu-id="c70d7-111">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="c70d7-111">Create the app</span></span>

<span data-ttu-id="c70d7-112">建立名為 "HelloWorld" 的 .NET Core 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="c70d7-112">Create a .NET Core console app project named "HelloWorld".</span></span>

1. <span data-ttu-id="c70d7-113">啟動 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="c70d7-113">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="c70d7-114">從**File**主功能表選取 [檔案] [  >  **開啟資料夾**] （檔案開啟**File**  >  **...** on macOS）。</span><span class="sxs-lookup"><span data-stu-id="c70d7-114">Select **File** > **Open Folder** (**File** > **Open...** on macOS) from the main menu.</span></span>

1. <span data-ttu-id="c70d7-115">在 [**開啟資料夾**] 對話方塊中，建立*HelloWorld*資料夾，然後按一下 [**選取資料夾**] （在 macOS 上**開啟**）。</span><span class="sxs-lookup"><span data-stu-id="c70d7-115">In the **Open Folder** dialog, create a *HelloWorld* folder and click **Select Folder** (**Open** on macOS).</span></span>

   <span data-ttu-id="c70d7-116">資料夾名稱預設會成為專案名稱和命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="c70d7-116">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="c70d7-117">您稍後會在本教學課程中新增程式碼，假設專案命名空間為 `HelloWorld` 。</span><span class="sxs-lookup"><span data-stu-id="c70d7-117">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

1. <span data-ttu-id="c70d7-118">從主功能表選取 [**查看**終端機]，以在 Visual Studio Code 中開啟**終端**機  >  **Terminal** 。</span><span class="sxs-lookup"><span data-stu-id="c70d7-118">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="c70d7-119">**終端**機會在*HelloWorld*資料夾中以命令提示字元開啟。</span><span class="sxs-lookup"><span data-stu-id="c70d7-119">The **Terminal** opens with the command prompt in the *HelloWorld* folder.</span></span>

1. <span data-ttu-id="c70d7-120">在**終端**機中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="c70d7-120">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new console
   ```

<span data-ttu-id="c70d7-121">此範本會建立簡單的 "Hello World" 應用程式。</span><span class="sxs-lookup"><span data-stu-id="c70d7-121">The template creates a simple "Hello World" application.</span></span> <span data-ttu-id="c70d7-122">它會呼叫 <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 方法來顯示 "Hello World！"</span><span class="sxs-lookup"><span data-stu-id="c70d7-122">It calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="c70d7-123">。</span><span class="sxs-lookup"><span data-stu-id="c70d7-123">in the console window.</span></span>

<span data-ttu-id="c70d7-124">範本程式碼會定義具有單一方法的類別，其 `Program` `Main` 接受 <xref:System.String> 陣列做為引數：</span><span class="sxs-lookup"><span data-stu-id="c70d7-124">The template code defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument:</span></span>

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

<span data-ttu-id="c70d7-125">`Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="c70d7-125">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="c70d7-126">在應用程式啟動時所提供的所有命令列引數，都會在 *args* 陣列中提供。</span><span class="sxs-lookup"><span data-stu-id="c70d7-126">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="c70d7-127">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="c70d7-127">Run the app</span></span>

<span data-ttu-id="c70d7-128">在**終端**機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="c70d7-128">Run the following command in the **Terminal**:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="c70d7-129">程式會顯示 "Hello World！"</span><span class="sxs-lookup"><span data-stu-id="c70d7-129">The program displays "Hello World!"</span></span> <span data-ttu-id="c70d7-130">和結束。</span><span class="sxs-lookup"><span data-stu-id="c70d7-130">and ends.</span></span>

![DotNet 執行命令](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a><span data-ttu-id="c70d7-132">增強應用程式</span><span class="sxs-lookup"><span data-stu-id="c70d7-132">Enhance the app</span></span>

<span data-ttu-id="c70d7-133">增強應用程式，以提示使用者輸入其名稱，並連同日期和時間一起顯示。</span><span class="sxs-lookup"><span data-stu-id="c70d7-133">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="c70d7-134">按一下 *Program.cs* 來開啟它。</span><span class="sxs-lookup"><span data-stu-id="c70d7-134">Open *Program.cs* by clicking on it.</span></span>

   <span data-ttu-id="c70d7-135">在 Visual Studio Code 中第一次開啟 C# 檔案時，會在編輯器中載入 [OmniSharp](https://www.omnisharp.net/)。</span><span class="sxs-lookup"><span data-stu-id="c70d7-135">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

   ![開啟 Program.cs 檔案](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="c70d7-137">當 Visual Studio Code 提示您新增遺失的資產，以建立和偵錯工具時，請選取 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="c70d7-137">Select **Yes** when Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span>

   ![遺失資產的提示](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="c70d7-139">以下列程式碼取代 `Main` *Program.cs*中方法的內容，也就是呼叫的那一行 `Console.WriteLine` ：</span><span class="sxs-lookup"><span data-stu-id="c70d7-139">Replace the contents of the `Main` method in *Program.cs*, which is the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="1":::

   <span data-ttu-id="c70d7-140">此程式碼會在主控台中顯示「What is your name?」，</span><span class="sxs-lookup"><span data-stu-id="c70d7-140">This code displays "What is your name?"</span></span> <span data-ttu-id="c70d7-141">在主控台視窗中，等候使用者輸入後面接著<kbd>Enter</kbd>鍵的字串。</span><span class="sxs-lookup"><span data-stu-id="c70d7-141">in the console window and waits until the user enters a string followed by the <kbd>Enter</kbd> key.</span></span> <span data-ttu-id="c70d7-142">它會將此字串儲存在名為的變數中 `name` 。</span><span class="sxs-lookup"><span data-stu-id="c70d7-142">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="c70d7-143">此程式碼也會擷取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性的值，其中包含目前的當地時間，並將它指派至名稱為 `date` 的變數。</span><span class="sxs-lookup"><span data-stu-id="c70d7-143">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="c70d7-144">最後，它會在主控台視窗中顯示這些值。</span><span class="sxs-lookup"><span data-stu-id="c70d7-144">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="c70d7-145">`\n`代表換行字元。</span><span class="sxs-lookup"><span data-stu-id="c70d7-145">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="c70d7-146">字串前面的貨幣符號（ `$` ）可讓您在字串中的大括弧內放置運算式，例如變數名稱。</span><span class="sxs-lookup"><span data-stu-id="c70d7-146">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="c70d7-147">運算式值會插入字串中，以取代運算式。</span><span class="sxs-lookup"><span data-stu-id="c70d7-147">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="c70d7-148">此語法稱為「插入[字串](../../csharp/language-reference/tokens/interpolated.md)」。</span><span class="sxs-lookup"><span data-stu-id="c70d7-148">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="c70d7-149">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="c70d7-149">Save your changes.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="c70d7-150">在 Visual Studio Code 中，您必須明確地儲存變更。</span><span class="sxs-lookup"><span data-stu-id="c70d7-150">In Visual Studio Code, you have to explicitly save changes.</span></span> <span data-ttu-id="c70d7-151">不同于 Visual Studio，當您建立並執行應用程式時，不會自動儲存檔案變更。</span><span class="sxs-lookup"><span data-stu-id="c70d7-151">Unlike Visual Studio, file changes are not automatically saved when you build and run an app.</span></span>

1. <span data-ttu-id="c70d7-152">再次執行程式：</span><span class="sxs-lookup"><span data-stu-id="c70d7-152">Run the program again:</span></span>

   ```dotnetcli
   dotnet run
   ```

1. <span data-ttu-id="c70d7-153">輸入名稱並按<kbd>enter</kbd>鍵，以回應提示。</span><span class="sxs-lookup"><span data-stu-id="c70d7-153">Respond to the prompt by entering a name and pressing the <kbd>Enter</kbd> key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="已修改程式輸出的終端機視窗":::

1. <span data-ttu-id="c70d7-155">按任意鍵以結束程式。</span><span class="sxs-lookup"><span data-stu-id="c70d7-155">Press any key to exit the program.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c70d7-156">其他資源</span><span class="sxs-lookup"><span data-stu-id="c70d7-156">Additional resources</span></span>

- [<span data-ttu-id="c70d7-157">設定 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c70d7-157">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a><span data-ttu-id="c70d7-158">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c70d7-158">Next steps</span></span>

<span data-ttu-id="c70d7-159">在本教學課程中，您已建立 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="c70d7-159">In this tutorial, you created a .NET Core console application.</span></span> <span data-ttu-id="c70d7-160">在下一個教學課程中，您會對應用程式進行 debug。</span><span class="sxs-lookup"><span data-stu-id="c70d7-160">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c70d7-161">使用 Visual Studio Code 來調試 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="c70d7-161">Debug a .NET Core console application using Visual Studio Code</span></span>](debugging-with-visual-studio-code.md)
