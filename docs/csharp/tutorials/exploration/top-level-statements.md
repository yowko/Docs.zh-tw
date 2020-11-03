---
title: '最上層語句-c # 教學課程'
description: 本教學課程示範如何使用最上層的語句來實驗和證明概念，同時探索您的想法
ms.date: 10/28/2020
ms.openlocfilehash: 210fbd83bf4677061cab303089d0b27f1a4a7d01
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2020
ms.locfileid: "93189388"
---
# <a name="tutorial-explore-ideas-using-top-level-statements-to-build-code-as-you-learn"></a><span data-ttu-id="5ecec-103">教學課程：使用最上層的語句探索想法，以在您學習時建立程式碼</span><span class="sxs-lookup"><span data-stu-id="5ecec-103">Tutorial: Explore ideas using top-level statements to build code as you learn</span></span>

<span data-ttu-id="5ecec-104">在本教學課程中，您將了解如何：</span><span class="sxs-lookup"><span data-stu-id="5ecec-104">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="5ecec-105">瞭解如何使用最上層語句的規則。</span><span class="sxs-lookup"><span data-stu-id="5ecec-105">Learn the rules governing your use of top-level statements.</span></span>
> - <span data-ttu-id="5ecec-106">使用最上層的語句來探索演算法。</span><span class="sxs-lookup"><span data-stu-id="5ecec-106">Use top-level statements to explore algorithms.</span></span>
> - <span data-ttu-id="5ecec-107">將探勘重構為可重複使用的元件。</span><span class="sxs-lookup"><span data-stu-id="5ecec-107">Refactor explorations into reusable components.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5ecec-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="5ecec-108">Prerequisites</span></span>

<span data-ttu-id="5ecec-109">您將需要設定您的電腦以執行 .NET 5，其中包括 c # 9 編譯器。</span><span class="sxs-lookup"><span data-stu-id="5ecec-109">You'll need to set up your machine to run .NET 5, which includes the C# 9 compiler.</span></span> <span data-ttu-id="5ecec-110">從 [Visual Studio 2019 16.9 版 preview 1](https://visualstudio.microsoft.com/vs/preview/) 或 [.net 5.0 SDK](https://dot.net/get-dotnet5)開始，可以使用 c # 9 編譯器。</span><span class="sxs-lookup"><span data-stu-id="5ecec-110">The C# 9 compiler is available starting with [Visual Studio 2019 version 16.9 preview 1](https://visualstudio.microsoft.com/vs/preview/) or [.NET 5.0 SDK](https://dot.net/get-dotnet5).</span></span>

<span data-ttu-id="5ecec-111">本教學課程假設您已熟悉 C# 和 .NET，包括 Visual Studio 或 .NET Core CLI。</span><span class="sxs-lookup"><span data-stu-id="5ecec-111">This tutorial assumes you're familiar with C# and .NET, including either Visual Studio or the .NET Core CLI.</span></span>

## <a name="start-exploring"></a><span data-ttu-id="5ecec-112">開始探索</span><span class="sxs-lookup"><span data-stu-id="5ecec-112">Start exploring</span></span>

<span data-ttu-id="5ecec-113">最上層的語句可讓您將程式的進入點放在類別中的靜態方法，以避免需要額外的繁瑣。</span><span class="sxs-lookup"><span data-stu-id="5ecec-113">Top-level statements enable you to avoid the extra ceremony required by placing your program's entry point in a static method in a class.</span></span> <span data-ttu-id="5ecec-114">新主控台應用程式的一般起點看起來會像下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="5ecec-114">The typical starting point for a new console application looks like the following code:</span></span>

```csharp
using System;

namespace Application
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

<span data-ttu-id="5ecec-115">上述程式碼是 `dotnet new console` 執行命令並建立新的主控台應用程式的結果。</span><span class="sxs-lookup"><span data-stu-id="5ecec-115">The preceding code is the result of running the `dotnet new console` command and creating a new console application.</span></span> <span data-ttu-id="5ecec-116">這11行只包含一行可執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="5ecec-116">Those 11 lines contain only one line of executable code.</span></span> <span data-ttu-id="5ecec-117">您可以使用新的最上層語句功能來簡化該程式。</span><span class="sxs-lookup"><span data-stu-id="5ecec-117">You can simplify that program with the new top-level statements feature.</span></span> <span data-ttu-id="5ecec-118">這可讓您移除此程式中的所有程式程式碼，而不是兩行：</span><span class="sxs-lookup"><span data-stu-id="5ecec-118">That enables you to remove all but two of the lines in this program:</span></span>

```csharp
using System;

Console.WriteLine("Hello World!");
```

<span data-ttu-id="5ecec-119">此動作可簡化開始探索新構想所需的一切。</span><span class="sxs-lookup"><span data-stu-id="5ecec-119">This action simplifies what's needed to begin exploring new ideas.</span></span> <span data-ttu-id="5ecec-120">您可以使用最上層的語句來撰寫腳本案例，或使用來進行探索。</span><span class="sxs-lookup"><span data-stu-id="5ecec-120">You can use top-level statements for scripting scenarios, or to explore.</span></span> <span data-ttu-id="5ecec-121">完成基本工作之後，您就可以開始重構程式碼，並建立方法、類別或其他元件，以使用您所建立的可重複使用元件。</span><span class="sxs-lookup"><span data-stu-id="5ecec-121">Once you've got the basics working, you can start refactoring the code and create methods, classes, or other assemblies for reusable components you've built.</span></span> <span data-ttu-id="5ecec-122">最上層的語句可讓您快速實驗和初學者教學課程。</span><span class="sxs-lookup"><span data-stu-id="5ecec-122">Top-level statements do enable quick experimentation and beginner tutorials.</span></span> <span data-ttu-id="5ecec-123">它們也提供從實驗到完整程式的流暢途徑。</span><span class="sxs-lookup"><span data-stu-id="5ecec-123">They also provide a smooth path from experimentation to full programs.</span></span>

<span data-ttu-id="5ecec-124">最上層的語句會依它們出現在檔案中的順序來執行。</span><span class="sxs-lookup"><span data-stu-id="5ecec-124">Top-level statements are executed in the order they appear in the file.</span></span> <span data-ttu-id="5ecec-125">最上層的語句只可用於應用程式中的一個原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="5ecec-125">Top-level statements can only be used in one source file in your application.</span></span> <span data-ttu-id="5ecec-126">如果您在多個檔案中使用，編譯器會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="5ecec-126">The compiler generates an error if you use them in more than one file.</span></span>

## <a name="build-a-magic-net-answer-machine"></a><span data-ttu-id="5ecec-127">打造魔術 .NET 回應機器</span><span class="sxs-lookup"><span data-stu-id="5ecec-127">Build a magic .NET answer machine</span></span>

<span data-ttu-id="5ecec-128">在本教學課程中，我們將建立一個主控台應用程式，以隨機答案回答「是」或「否」問題。</span><span class="sxs-lookup"><span data-stu-id="5ecec-128">For this tutorial, let's build a console application that answers a "yes" or "no" question with a random answer.</span></span> <span data-ttu-id="5ecec-129">您將逐步建立功能。</span><span class="sxs-lookup"><span data-stu-id="5ecec-129">You'll build out the functionality step by step.</span></span> <span data-ttu-id="5ecec-130">您可以專注于工作，而不是一般程式結構所需的工作。</span><span class="sxs-lookup"><span data-stu-id="5ecec-130">You can focus on your task rather than ceremony needed for the structure of a typical program.</span></span> <span data-ttu-id="5ecec-131">然後，當您對功能感到滿意之後，就可以依照您的需要重構應用程式。</span><span class="sxs-lookup"><span data-stu-id="5ecec-131">Then, once you're happy with the functionality, you can refactor the application as you see fit.</span></span>

<span data-ttu-id="5ecec-132">好的起點是將問題寫回主控台。</span><span class="sxs-lookup"><span data-stu-id="5ecec-132">A good starting point is to write the question back to the console.</span></span> <span data-ttu-id="5ecec-133">您可以從撰寫下列程式碼開始：</span><span class="sxs-lookup"><span data-stu-id="5ecec-133">You can start by writing the following code:</span></span>

```csharp
using System;

Console.WriteLine(args);
```

<span data-ttu-id="5ecec-134">您不會宣告 `args` 變數。</span><span class="sxs-lookup"><span data-stu-id="5ecec-134">You don't declare an `args` variable.</span></span> <span data-ttu-id="5ecec-135">針對包含最上層語句的單一原始程式檔，編譯器會辨識 `args` 為代表命令列引數。</span><span class="sxs-lookup"><span data-stu-id="5ecec-135">For the single source file that contains your top-level statements, the compiler recognizes `args` to mean the command-line arguments.</span></span> <span data-ttu-id="5ecec-136">引數的類型為 `string[]` ，如同在所有 c # 程式中一樣。</span><span class="sxs-lookup"><span data-stu-id="5ecec-136">The type of args is a `string[]`, as in all C# programs.</span></span>

<span data-ttu-id="5ecec-137">您可以藉由執行下列命令來測試您的程式碼 `dotnet run` ：</span><span class="sxs-lookup"><span data-stu-id="5ecec-137">You can test your code by running the following `dotnet run` command:</span></span>

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?
```

<span data-ttu-id="5ecec-138">`--`命令列上的引數會傳遞至程式。</span><span class="sxs-lookup"><span data-stu-id="5ecec-138">The arguments after the `--` on the command line are passed to the program.</span></span> <span data-ttu-id="5ecec-139">您可以看到變數的類型 `args` ，因為這會功能列印到主控台：</span><span class="sxs-lookup"><span data-stu-id="5ecec-139">You can see the type of the `args` variable, because that's what's printed to the console:</span></span>

```console
System.String[]
```

<span data-ttu-id="5ecec-140">若要將問題寫入主控台，您必須列舉引數，並以空格分隔。</span><span class="sxs-lookup"><span data-stu-id="5ecec-140">To write the question to the console, you'll need to enumerate the arguments and separate them with a space.</span></span> <span data-ttu-id="5ecec-141">`WriteLine`以下列程式碼取代呼叫：</span><span class="sxs-lookup"><span data-stu-id="5ecec-141">Replace the `WriteLine` call with the following code:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="EchoInput":::

<span data-ttu-id="5ecec-142">現在，當您執行程式時，它會正確地將問題顯示為引數字串。</span><span class="sxs-lookup"><span data-stu-id="5ecec-142">Now, when you run the program, it will correctly display the question as a string of arguments.</span></span>

## <a name="respond-with-a-random-answer"></a><span data-ttu-id="5ecec-143">以隨機答案回應</span><span class="sxs-lookup"><span data-stu-id="5ecec-143">Respond with a random answer</span></span>

<span data-ttu-id="5ecec-144">回應問題之後，您可以加入程式碼來產生隨機答案。</span><span class="sxs-lookup"><span data-stu-id="5ecec-144">After echoing the question, you can add the code to generate the random answer.</span></span> <span data-ttu-id="5ecec-145">從新增可能的答案陣列開始：</span><span class="sxs-lookup"><span data-stu-id="5ecec-145">Start by adding an array of possible answers:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="Answers":::

<span data-ttu-id="5ecec-146">這個陣列有12個肯定的答案，六個是非順序，六個為負數。</span><span class="sxs-lookup"><span data-stu-id="5ecec-146">This array has 12 answers that are affirmative, six that are non-committal, and six that are negative.</span></span> <span data-ttu-id="5ecec-147">接下來，新增下列程式碼，以產生並顯示來自陣列的隨機答案：</span><span class="sxs-lookup"><span data-stu-id="5ecec-147">Next, add the following code to generate and display a random answer from the array:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Program.cs" ID="GenerateAnswer":::

<span data-ttu-id="5ecec-148">您可以再次執行應用程式以查看結果。</span><span class="sxs-lookup"><span data-stu-id="5ecec-148">You can run the application again to see the results.</span></span> <span data-ttu-id="5ecec-149">您應該會看到類似下列輸出的內容：</span><span class="sxs-lookup"><span data-stu-id="5ecec-149">You should see something like the following output:</span></span>

```dotnetcli
dotnet run -- Should I use top level statements in all my programs?

Should I use top level statements in all my programs?
Better not tell you now.
```

<span data-ttu-id="5ecec-150">這段程式碼會回答問題，但讓我們再新增一項功能。</span><span class="sxs-lookup"><span data-stu-id="5ecec-150">This code answers the questions, but let's add one more feature.</span></span> <span data-ttu-id="5ecec-151">您希望您的問題應用程式模擬對答案的思考。</span><span class="sxs-lookup"><span data-stu-id="5ecec-151">You'd like your question app to simulate thinking about the answer.</span></span> <span data-ttu-id="5ecec-152">您可以藉由新增一些 ASCII 動畫，並在工作時暫停。</span><span class="sxs-lookup"><span data-stu-id="5ecec-152">You can do that by adding a bit of ASCII animation, and pausing while working.</span></span>  <span data-ttu-id="5ecec-153">將下列程式碼新增至回顯問題的行之後：</span><span class="sxs-lookup"><span data-stu-id="5ecec-153">Add the following code after the line that echoes the question:</span></span>

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="AnimationFirstPass":::

<span data-ttu-id="5ecec-154">您也需要將 `using` 語句新增至原始程式檔的頂端：</span><span class="sxs-lookup"><span data-stu-id="5ecec-154">You'll also need to add a `using` statement to the top of the source file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="5ecec-155">`using`語句必須在檔案中的任何其他語句之前。</span><span class="sxs-lookup"><span data-stu-id="5ecec-155">The `using` statements must be before any other statements in the file.</span></span> <span data-ttu-id="5ecec-156">否則，就是編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="5ecec-156">Otherwise, it's a compiler error.</span></span> <span data-ttu-id="5ecec-157">您可以再次執行程式，並查看動畫。</span><span class="sxs-lookup"><span data-stu-id="5ecec-157">You can run the program again and see the animation.</span></span> <span data-ttu-id="5ecec-158">這可提供更好的體驗。</span><span class="sxs-lookup"><span data-stu-id="5ecec-158">That makes a better experience.</span></span> <span data-ttu-id="5ecec-159">請試驗延遲的長度，以符合您的感受。</span><span class="sxs-lookup"><span data-stu-id="5ecec-159">Experiment with the length of the delay to match your taste.</span></span>

<span data-ttu-id="5ecec-160">上述程式碼會建立一組以空格分隔的旋轉線。</span><span class="sxs-lookup"><span data-stu-id="5ecec-160">The preceding code creates a set of spinning lines separated by a space.</span></span> <span data-ttu-id="5ecec-161">新增 `await` 關鍵字會指示編譯器以具有修飾詞的方法產生程式進入點 `async` ，並傳回 <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="5ecec-161">Adding the `await` keyword instructs the compiler to generate the program entry point as a method that has the `async` modifier, and returns a <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5ecec-162">此程式不會傳回值，因此程式進入點會傳回 `Task` 。</span><span class="sxs-lookup"><span data-stu-id="5ecec-162">This program does not return a value, so the program entry point returns a `Task`.</span></span> <span data-ttu-id="5ecec-163">如果您的程式傳回整數值，您可以在最上層語句的結尾加入 return 語句。</span><span class="sxs-lookup"><span data-stu-id="5ecec-163">If your program returns an integer value, you would add a return statement to the end of your top-level statements.</span></span> <span data-ttu-id="5ecec-164">該 return 語句會指定要傳回的整數值。</span><span class="sxs-lookup"><span data-stu-id="5ecec-164">That return statement would specify the integer value to return.</span></span> <span data-ttu-id="5ecec-165">如果最上層的語句包含 `await` 運算式，則傳回類型會變成 <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="5ecec-165">If your top-level statements include an `await` expression, the return type becomes <xref:System.Threading.Tasks.Task%601?displayProperty=nameWithType>.</span></span>

## <a name="refactoring-for-the-future"></a><span data-ttu-id="5ecec-166">未來的重構</span><span class="sxs-lookup"><span data-stu-id="5ecec-166">Refactoring for the future</span></span>

<span data-ttu-id="5ecec-167">您的程式看起來應該像下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="5ecec-167">Your program should look like the following code:</span></span>

```csharp
using System;
using System.Threading.Tasks;

Console.WriteLine();
foreach(var s in args)
{
    Console.Write(s);
    Console.Write(' ');
}
Console.WriteLine();

for (int i = 0; i < 20; i++)
{
    Console.Write("| -");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("/ \\");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("- |");
    await Task.Delay(50);
    Console.Write("\b\b\b");
    Console.Write("\\ /");
    await Task.Delay(50);
    Console.Write("\b\b\b");
}
Console.WriteLine();

string[] answers =
{
    "It is certain.",       "Reply hazy, try again.",     "Don’t count on it.",
    "It is decidedly so.",  "Ask again later.",           "My reply is no.",
    "Without a doubt.",     "Better not tell you now.",   "My sources say no.",
    "Yes – definitely.",    "Cannot predict now.",        "Outlook not so good.",
    "You may rely on it.",  "Concentrate and ask again.", "Very doubtful.",
    "As I see it, yes.",
    "Most likely.",
    "Outlook good.",
    "Yes.",
    "Signs point to yes.",
};

var index = new Random().Next(answers.Length - 1);
Console.WriteLine(answers[index]);
```

<span data-ttu-id="5ecec-168">上述程式碼是合理的。</span><span class="sxs-lookup"><span data-stu-id="5ecec-168">The preceding code is reasonable.</span></span> <span data-ttu-id="5ecec-169">這麼做確實有成效。</span><span class="sxs-lookup"><span data-stu-id="5ecec-169">It works.</span></span> <span data-ttu-id="5ecec-170">但它無法重複使用。</span><span class="sxs-lookup"><span data-stu-id="5ecec-170">But it isn't reusable.</span></span> <span data-ttu-id="5ecec-171">現在您已讓應用程式運作，接下來可以提取可重複使用的元件。</span><span class="sxs-lookup"><span data-stu-id="5ecec-171">Now that you have the application working, it's time to pull out reusable parts.</span></span>

<span data-ttu-id="5ecec-172">其中一個候選項是顯示等候動畫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="5ecec-172">One candidate is the code that displays the waiting animation.</span></span> <span data-ttu-id="5ecec-173">該程式碼片段可能會變成方法：</span><span class="sxs-lookup"><span data-stu-id="5ecec-173">That snippet can become a method:</span></span>

<span data-ttu-id="5ecec-174">您可以從在檔案中建立區域函數開始。</span><span class="sxs-lookup"><span data-stu-id="5ecec-174">You can start by creating a local function in your file.</span></span> <span data-ttu-id="5ecec-175">以下列程式碼取代目前的動畫：</span><span class="sxs-lookup"><span data-stu-id="5ecec-175">Replace the current animation with the following code:</span></span>

```csharp
await ShowConsoleAnimation();

static async Task ShowConsoleAnimation()
{
    for (int i = 0; i < 20; i++)
    {
        Console.Write("| -");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("/ \\");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("- |");
        await Task.Delay(50);
        Console.Write("\b\b\b");
        Console.Write("\\ /");
        await Task.Delay(50);
        Console.Write("\b\b\b");
    }
    Console.WriteLine();
}
```

<span data-ttu-id="5ecec-176">上述程式碼會在您的 main 方法內建立區域函數。</span><span class="sxs-lookup"><span data-stu-id="5ecec-176">The preceding code creates a local function inside your main method.</span></span> <span data-ttu-id="5ecec-177">這仍然無法重複使用。</span><span class="sxs-lookup"><span data-stu-id="5ecec-177">That's still not reusable.</span></span> <span data-ttu-id="5ecec-178">因此，請將該程式碼解壓縮至類別中。</span><span class="sxs-lookup"><span data-stu-id="5ecec-178">So, extract that code into a class.</span></span> <span data-ttu-id="5ecec-179">建立名為 *utilities.cs* 的新檔案，並新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="5ecec-179">Create a new file named *utilities.cs* and add the following code:</span></span>

:::code language="csharp" source="snippets/top-level-statements/UtilitiesPassOne.cs" ID="SnippetUtilities":::

<span data-ttu-id="5ecec-180">最上層的語句只能在一個檔案中，而該檔案不能包含命名空間或類型。</span><span class="sxs-lookup"><span data-stu-id="5ecec-180">Top-level statements can only be in one file, and that file cannot contain namespaces or types.</span></span>

<span data-ttu-id="5ecec-181">最後，您可以清除動畫程式碼以移除一些重複項：</span><span class="sxs-lookup"><span data-stu-id="5ecec-181">Finally, you can clean the animation code to remove some duplication:</span></span>

:::code language="csharp" source="snippets/top-level-statements/Utiliities.cs" ID="Animation":::

<span data-ttu-id="5ecec-182">現在您有一個完整的應用程式，而且您已經重構可重複使用的元件，以供稍後使用。</span><span class="sxs-lookup"><span data-stu-id="5ecec-182">Now you have a complete application, and you've refactored the reusable parts for later use.</span></span>

## <a name="summary"></a><span data-ttu-id="5ecec-183">摘要</span><span class="sxs-lookup"><span data-stu-id="5ecec-183">Summary</span></span>

<span data-ttu-id="5ecec-184">最上層的語句可讓您更輕鬆地建立簡單的程式，以用來探索新的演算法。</span><span class="sxs-lookup"><span data-stu-id="5ecec-184">Top-level statements make it easier to create simple programs for use to explore new algorithms.</span></span> <span data-ttu-id="5ecec-185">您可以嘗試使用不同的程式碼片段來實驗演算法。</span><span class="sxs-lookup"><span data-stu-id="5ecec-185">You can experiment with algorithms by trying different snippets of code.</span></span> <span data-ttu-id="5ecec-186">一旦您瞭解運作方式之後，就可以重構程式碼，以更容易維護。</span><span class="sxs-lookup"><span data-stu-id="5ecec-186">Once you've learned what works, you can refactor the code to be more maintainable.</span></span>

<span data-ttu-id="5ecec-187">最上層的語句可簡化以主控台應用程式為基礎的程式。</span><span class="sxs-lookup"><span data-stu-id="5ecec-187">Top-level statements simplify programs that are based on console applications.</span></span> <span data-ttu-id="5ecec-188">這些功能包括 Azure 函式、GitHub 動作和其他小型公用程式。</span><span class="sxs-lookup"><span data-stu-id="5ecec-188">These include Azure functions, GitHub actions, and other small utilities.</span></span>
