---
title: 使用 Visual Studio Code 建立具有 .NET Core 的主控台應用程式
description: 瞭解如何使用 Visual Studio Code 和 .NET Core CLI 建立 .NET Core 主控台應用程式。
ms.date: 05/22/2020
ms.openlocfilehash: 673c4a639a2cab26261b7cdafd5d8e20acfafb94
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201693"
---
# <a name="tutorial-create-a-console-application-with-net-core-using-visual-studio-code"></a><span data-ttu-id="5714b-103">教學課程：使用 Visual Studio Code 建立具有 .NET Core 的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="5714b-103">Tutorial: Create a console application with .NET Core using Visual Studio Code</span></span>

<span data-ttu-id="5714b-104">本教學課程說明如何使用 Visual Studio Code 和 .NET Core CLI 來建立和執行 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="5714b-104">This tutorial shows how to create and run a .NET Core console application by using Visual Studio Code and the .NET Core CLI.</span></span> <span data-ttu-id="5714b-105">專案工作（例如建立、編譯和執行專案）是使用 CLI 來完成，因此，您可以使用不同的程式碼編輯器來遵循此教學課程，並視需要在終端機中執行命令。</span><span class="sxs-lookup"><span data-stu-id="5714b-105">Project tasks, such as creating, compiling, and running a project are done by using the CLI, so you can follow this tutorial with a different code editor and run commands in a terminal if you prefer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5714b-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="5714b-106">Prerequisites</span></span>

1. <span data-ttu-id="5714b-107">已安裝[c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能的[Visual Studio Code](https://code.visualstudio.com/) 。</span><span class="sxs-lookup"><span data-stu-id="5714b-107">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="5714b-108">如需有關如何在 Visual Studio Code 上安裝延伸模組的詳細資訊，請參閱[VS Code 延伸模組 Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery)。</span><span class="sxs-lookup"><span data-stu-id="5714b-108">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="5714b-109">[.Net Core 3.1 SDK 或更新版本](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="5714b-109">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-the-app"></a><span data-ttu-id="5714b-110">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="5714b-110">Create the app</span></span>

1. <span data-ttu-id="5714b-111">開啟 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="5714b-111">Open Visual Studio Code.</span></span>

1. <span data-ttu-id="5714b-112">建立專案。</span><span class="sxs-lookup"><span data-stu-id="5714b-112">Create a project.</span></span>

   1. <span data-ttu-id="5714b-113">**File**  >  從主功能表選取 [檔案] [**開啟資料夾**] / [**開啟 ...** ]，建立*HelloWorld*資料夾，然後按一下 [**選取資料夾**] [ / **開啟**]。</span><span class="sxs-lookup"><span data-stu-id="5714b-113">Select **File** > **Open Folder**/**Open...** from the main menu, create a *HelloWorld* folder, and click **Select Folder**/**Open**.</span></span>

      <span data-ttu-id="5714b-114">資料夾名稱預設會成為專案名稱和命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="5714b-114">The folder name becomes the project name and the namespace name by default.</span></span> <span data-ttu-id="5714b-115">您稍後會在本教學課程中新增程式碼，假設專案命名空間為 `HelloWorld` 。</span><span class="sxs-lookup"><span data-stu-id="5714b-115">You'll add code later in the tutorial that assumes the project namespace is `HelloWorld`.</span></span>

   1. <span data-ttu-id="5714b-116">從主功能表選取 [**查看**終端機]，以在 Visual Studio Code 中開啟**終端**機  >  **Terminal** 。</span><span class="sxs-lookup"><span data-stu-id="5714b-116">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

      <span data-ttu-id="5714b-117">**終端**機會在*HelloWorld*資料夾中以命令提示字元開啟。</span><span class="sxs-lookup"><span data-stu-id="5714b-117">The **Terminal** opens with the command prompt in the *HelloWorld* folder.</span></span>

   1. <span data-ttu-id="5714b-118">在**終端**機中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="5714b-118">In the **Terminal**, enter the following command:</span></span>

      ```dotnetcli
      dotnet new console
      ```

<span data-ttu-id="5714b-119">適用于 .NET Core 的主控台應用程式範本會定義一個類別， `Program` 其中包含單一方法，其 `Main` 採用 <xref:System.String> 陣列做為引數。</span><span class="sxs-lookup"><span data-stu-id="5714b-119">The Console Application template for .NET Core defines a class, `Program`, with a single method, `Main`, that takes a <xref:System.String> array as an argument.</span></span> <span data-ttu-id="5714b-120">*Program.cs*檔案包含下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="5714b-120">The *Program.cs* file has the following code:</span></span>

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

<span data-ttu-id="5714b-121">`Main` 是應用程式進入點，是執行階段在啟動應用程式時會自動呼叫的方法。</span><span class="sxs-lookup"><span data-stu-id="5714b-121">`Main` is the application entry point, the method that's called automatically by the runtime when it launches the application.</span></span> <span data-ttu-id="5714b-122">在應用程式啟動時所提供的所有命令列引數，都會在 *args* 陣列中提供。</span><span class="sxs-lookup"><span data-stu-id="5714b-122">Any command-line arguments supplied when the application is launched are available in the *args* array.</span></span>

<span data-ttu-id="5714b-123">此範本會建立一個簡單的應用程式， <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> 以呼叫方法來顯示 "Hello World！"</span><span class="sxs-lookup"><span data-stu-id="5714b-123">The template creates a simple application that calls the <xref:System.Console.WriteLine(System.String)?displayProperty=nameWithType> method to display "Hello World!"</span></span> <span data-ttu-id="5714b-124">。</span><span class="sxs-lookup"><span data-stu-id="5714b-124">in the console window.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="5714b-125">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="5714b-125">Run the app</span></span>

<span data-ttu-id="5714b-126">在**終端**機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="5714b-126">Run the following command in the **Terminal**:</span></span>

```dotnetcli
dotnet run
```

<span data-ttu-id="5714b-127">程式會顯示 "Hello World！"</span><span class="sxs-lookup"><span data-stu-id="5714b-127">The program displays "Hello World!"</span></span> <span data-ttu-id="5714b-128">和結束。</span><span class="sxs-lookup"><span data-stu-id="5714b-128">and ends.</span></span>

![DotNet 執行命令](media/with-visual-studio-code/dotnet-run-command.png)

## <a name="enhance-the-app"></a><span data-ttu-id="5714b-130">增強應用程式</span><span class="sxs-lookup"><span data-stu-id="5714b-130">Enhance the app</span></span>

<span data-ttu-id="5714b-131">增強應用程式，以提示使用者輸入其名稱，並連同日期和時間一起顯示。</span><span class="sxs-lookup"><span data-stu-id="5714b-131">Enhance the application to prompt the user for their name and display it along with the date and time.</span></span>

1. <span data-ttu-id="5714b-132">按一下 *Program.cs* 來開啟它。</span><span class="sxs-lookup"><span data-stu-id="5714b-132">Open *Program.cs* by clicking on it.</span></span>

   <span data-ttu-id="5714b-133">在 Visual Studio Code 中第一次開啟 C# 檔案時，會在編輯器中載入 [OmniSharp](https://www.omnisharp.net/)。</span><span class="sxs-lookup"><span data-stu-id="5714b-133">The first time you open a C# file in Visual Studio Code, [OmniSharp](https://www.omnisharp.net/) loads in the editor.</span></span>

   ![開啟 Program.cs 檔案](media/with-visual-studio-code/open-program-cs.png)

1. <span data-ttu-id="5714b-135">當 Visual Studio Code 提示您新增遺失的資產，以建立和偵錯工具時，請選取 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="5714b-135">Select **Yes** when Visual Studio Code prompts you to add the missing assets to build and debug your app.</span></span>

   ![遺失資產的提示](media/with-visual-studio-code/missing-assets.png)

1. <span data-ttu-id="5714b-137">以 `Main` 下列程式碼取代*Program.cs*中方法的內容，這目前只是呼叫的那一行 `Console.WriteLine` ：</span><span class="sxs-lookup"><span data-stu-id="5714b-137">Replace the contents of the `Main` method in *Program.cs*, which is currently just the line that calls `Console.WriteLine`, with the following code:</span></span>

   :::code language="csharp" source="./snippets/with-visual-studio/csharp/Program.cs" id="Snippet1":::

   <span data-ttu-id="5714b-138">此程式碼會在主控台中顯示「What is your name?」，</span><span class="sxs-lookup"><span data-stu-id="5714b-138">This code displays "What is your name?"</span></span> <span data-ttu-id="5714b-139">在主控台視窗中，等候使用者輸入後面接著**Enter**鍵的字串。</span><span class="sxs-lookup"><span data-stu-id="5714b-139">in the console window and waits until the user enters a string followed by the **Enter** key.</span></span> <span data-ttu-id="5714b-140">它會將此字串儲存在名為的變數中 `name` 。</span><span class="sxs-lookup"><span data-stu-id="5714b-140">It stores this string in a variable named `name`.</span></span> <span data-ttu-id="5714b-141">此程式碼也會擷取 <xref:System.DateTime.Now?displayProperty=nameWithType> 屬性的值，其中包含目前的當地時間，並將它指派至名稱為 `date` 的變數。</span><span class="sxs-lookup"><span data-stu-id="5714b-141">It also retrieves the value of the <xref:System.DateTime.Now?displayProperty=nameWithType> property, which contains the current local time, and assigns it to a variable named `date`.</span></span> <span data-ttu-id="5714b-142">最後，它會在主控台視窗中顯示這些值。</span><span class="sxs-lookup"><span data-stu-id="5714b-142">Finally, it displays these values in the console window.</span></span>

   <span data-ttu-id="5714b-143">`\n`代表換行字元。</span><span class="sxs-lookup"><span data-stu-id="5714b-143">The `\n` represents a newline character.</span></span>

   <span data-ttu-id="5714b-144">字串前面的貨幣符號（ `$` ）可讓您在字串中的大括弧內放置運算式，例如變數名稱。</span><span class="sxs-lookup"><span data-stu-id="5714b-144">The dollar sign (`$`) in front of a string lets you put expressions such as variable names in curly braces in the string.</span></span> <span data-ttu-id="5714b-145">運算式值會插入字串中，以取代運算式。</span><span class="sxs-lookup"><span data-stu-id="5714b-145">The expression value is inserted into the string in place of the expression.</span></span> <span data-ttu-id="5714b-146">此語法稱為「插入[字串](../../csharp/language-reference/tokens/interpolated.md)」。</span><span class="sxs-lookup"><span data-stu-id="5714b-146">This syntax is referred to as [interpolated strings](../../csharp/language-reference/tokens/interpolated.md).</span></span>

1. <span data-ttu-id="5714b-147">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="5714b-147">Save your changes.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="5714b-148">在 Visual Studio Code 中，您必須明確地儲存變更。</span><span class="sxs-lookup"><span data-stu-id="5714b-148">In Visual Studio Code, you have to explicitly save changes.</span></span> <span data-ttu-id="5714b-149">不同于 Visual Studio，當您建立並執行應用程式時，不會自動儲存檔案變更。</span><span class="sxs-lookup"><span data-stu-id="5714b-149">Unlike Visual Studio, file changes are not automatically saved when you build and run an app.</span></span>

1. <span data-ttu-id="5714b-150">再次執行程式：</span><span class="sxs-lookup"><span data-stu-id="5714b-150">Run the program again:</span></span>

   ```dotnetcli
   dotnet run
   ```

1. <span data-ttu-id="5714b-151">輸入名稱並按**enter**鍵，以回應提示。</span><span class="sxs-lookup"><span data-stu-id="5714b-151">Respond to the prompt by entering a name and pressing the **Enter** key.</span></span>

   :::image type="content" source="media/debugging-with-visual-studio-code/run-modified-program.png" alt-text="已修改程式輸出的終端機視窗":::

1. <span data-ttu-id="5714b-153">按任意鍵以結束程式。</span><span class="sxs-lookup"><span data-stu-id="5714b-153">Press any key to exit the program.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="5714b-154">其他資源</span><span class="sxs-lookup"><span data-stu-id="5714b-154">Additional resources</span></span>

- [<span data-ttu-id="5714b-155">設定 Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5714b-155">Setting up Visual Studio Code</span></span>](https://code.visualstudio.com/docs/setup/setup-overview)

## <a name="next-steps"></a><span data-ttu-id="5714b-156">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5714b-156">Next steps</span></span>

<span data-ttu-id="5714b-157">在本教學課程中，您已建立 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5714b-157">In this tutorial, you created a .NET Core application.</span></span> <span data-ttu-id="5714b-158">在下一個教學課程中，您會對應用程式進行 debug。</span><span class="sxs-lookup"><span data-stu-id="5714b-158">In the next tutorial, you debug the app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="5714b-159">使用 Visual Studio Code 來調試 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="5714b-159">Debug a .NET Core console application using Visual Studio Code</span></span>](debugging-with-visual-studio-code.md)
