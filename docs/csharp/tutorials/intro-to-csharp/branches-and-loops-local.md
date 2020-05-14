---
title: 分支和迴圈 - C# 教學課程簡介
description: 在這個關於分支和迴圈的教學課程中，您將會撰寫 C# 程式碼以探索支援條件式分支和迴圈的語言語法，以重複執行陳述式。
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d67cfe359634783bb542e9ac34df52a095b45c20
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396885"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="04bb5-103">透過分支和迴圈陳述式了解條件式邏輯</span><span class="sxs-lookup"><span data-stu-id="04bb5-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="04bb5-104">此教學課程將教您如何撰寫程式碼來檢查變數，並根據那些變數來變更執行路徑。</span><span class="sxs-lookup"><span data-stu-id="04bb5-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="04bb5-105">您將會撰寫 C# 程式碼，並查看程式碼編譯和執行的結果。</span><span class="sxs-lookup"><span data-stu-id="04bb5-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="04bb5-106">此教學課程包含一系列探索 C# 中分支和迴圈建構的課程。</span><span class="sxs-lookup"><span data-stu-id="04bb5-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="04bb5-107">這些課程會教導您 C# 語言的基本概念。</span><span class="sxs-lookup"><span data-stu-id="04bb5-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="04bb5-108">此教學課程要求您必須有可用於開發的電腦。</span><span class="sxs-lookup"><span data-stu-id="04bb5-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="04bb5-109">.NET 教學課程[Hello World 在10分鐘內](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)，有在 Windows、Linux 或 macOS 上設定本機開發環境的指示。</span><span class="sxs-lookup"><span data-stu-id="04bb5-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="04bb5-110">您可以在[熟悉開發工具](local-environment.md)中快速檢視將會用到的命令，並取得可提供詳細資料的連結。</span><span class="sxs-lookup"><span data-stu-id="04bb5-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="04bb5-111">使用 `if` 陳述式來做決策</span><span class="sxs-lookup"><span data-stu-id="04bb5-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="04bb5-112">建立名為 *branches-tutorial* 的目錄。</span><span class="sxs-lookup"><span data-stu-id="04bb5-112">Create a directory named *branches-tutorial*.</span></span> <span data-ttu-id="04bb5-113">將它設為目前的目錄，然後執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="04bb5-113">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

<span data-ttu-id="04bb5-114">此命令會在目前的目錄中建立新的 .NET Core 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="04bb5-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="04bb5-115">在您最愛的編輯器中開啟 *Program.cs*，並以下列程式碼取代 `Console.WriteLine("Hello World!");` 程式碼行：</span><span class="sxs-lookup"><span data-stu-id="04bb5-115">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="04bb5-116">在主控台視窗中鍵入 `dotnet run` 來嘗試此程式碼。</span><span class="sxs-lookup"><span data-stu-id="04bb5-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="04bb5-117">您應該會看見訊息 "The answer is greater than 10"</span><span class="sxs-lookup"><span data-stu-id="04bb5-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="04bb5-118">顯示於主控台中。</span><span class="sxs-lookup"><span data-stu-id="04bb5-118">printed to your console.</span></span>

<span data-ttu-id="04bb5-119">修改 `b` 的宣告，讓總和小於 10：</span><span class="sxs-lookup"><span data-stu-id="04bb5-119">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="04bb5-120">再次輸入 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="04bb5-120">Type `dotnet run` again.</span></span> <span data-ttu-id="04bb5-121">因為答案小於 10，所以不會印出任何東西。</span><span class="sxs-lookup"><span data-stu-id="04bb5-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="04bb5-122">您正在測試的**條件**為 False。</span><span class="sxs-lookup"><span data-stu-id="04bb5-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="04bb5-123">您尚未有可執行的程式碼，因為您在 `if` 陳述式中僅撰寫了一個可能的分支：True 分支。</span><span class="sxs-lookup"><span data-stu-id="04bb5-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="04bb5-124">在您探索 C# (或任何程式設計語言) 時，可能會在撰寫程式碼時犯錯。</span><span class="sxs-lookup"><span data-stu-id="04bb5-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="04bb5-125">編譯器會找出並回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="04bb5-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="04bb5-126">仔細查看錯誤輸出，以及產生該錯誤的程式碼。</span><span class="sxs-lookup"><span data-stu-id="04bb5-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="04bb5-127">編譯器錯誤通常可以協助找出問題。</span><span class="sxs-lookup"><span data-stu-id="04bb5-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="04bb5-128">此第一個範例示範 `if` 和布林值類型的功能。</span><span class="sxs-lookup"><span data-stu-id="04bb5-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="04bb5-129">「*布林*值」是一個變數，可以有兩個值的其中一個： `true` 或 `false` 。</span><span class="sxs-lookup"><span data-stu-id="04bb5-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="04bb5-130">C# 會針對布林值變數定義特殊類型：`bool`。</span><span class="sxs-lookup"><span data-stu-id="04bb5-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="04bb5-131">`if` 陳述式會檢查 `bool` 的值。</span><span class="sxs-lookup"><span data-stu-id="04bb5-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="04bb5-132">當值為 `true` 時，就會執行 `if` 之後的陳述式。</span><span class="sxs-lookup"><span data-stu-id="04bb5-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="04bb5-133">否則會略過。</span><span class="sxs-lookup"><span data-stu-id="04bb5-133">Otherwise, it's skipped.</span></span>

<span data-ttu-id="04bb5-134">這項檢查條件和根據這些條件執行語句的程式功能強大。</span><span class="sxs-lookup"><span data-stu-id="04bb5-134">This process of checking conditions and executing statements based on those conditions is powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="04bb5-135">搭配使用 if 和 else</span><span class="sxs-lookup"><span data-stu-id="04bb5-135">Make if and else work together</span></span>

<span data-ttu-id="04bb5-136">若要在 True 和 False 分支中執行不同的程式碼，則必須建立可在條件為 False 時執行的 `else` 分支。</span><span class="sxs-lookup"><span data-stu-id="04bb5-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="04bb5-137">試試這個。</span><span class="sxs-lookup"><span data-stu-id="04bb5-137">Try this.</span></span> <span data-ttu-id="04bb5-138">將下列程式碼的最後兩行新增至您的 `Main` 方法 (您應該已經具有前面四行)：</span><span class="sxs-lookup"><span data-stu-id="04bb5-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="04bb5-139">只有當測試的條件為 `false` 時，才會執行 `else` 關鍵字之後的陳述式。</span><span class="sxs-lookup"><span data-stu-id="04bb5-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="04bb5-140">將 `if` 和 `else` 結合布林值條件，就可提供處理 `true` 和 `false` 條件的所有功能。</span><span class="sxs-lookup"><span data-stu-id="04bb5-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="04bb5-141">`if` 和 `else` 陳述式之下的縮排是為了方便人類閱讀。</span><span class="sxs-lookup"><span data-stu-id="04bb5-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="04bb5-142">C# 語言不會將縮排或空白字元視為有意義的內容。</span><span class="sxs-lookup"><span data-stu-id="04bb5-142">The C# language doesn't treat indentation or white space as significant.</span></span>
> <span data-ttu-id="04bb5-143">`if` 或 `else` 關鍵字之後的陳述式將會根據條件來執行。</span><span class="sxs-lookup"><span data-stu-id="04bb5-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="04bb5-144">此教學課程中的所有範例都遵循常見的實務，根據陳述式的控制流程縮排程式碼行。</span><span class="sxs-lookup"><span data-stu-id="04bb5-144">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="04bb5-145">因為縮排沒有意義，所以您需要使用 `{` 和 `}` 來表示當您想要有一個以上的語句是有條件地執行之區塊的一部分時。</span><span class="sxs-lookup"><span data-stu-id="04bb5-145">Because indentation isn't significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="04bb5-146">C# 程式設計人員通常會在所有的 `if` 和 `else` 子句上使用這些大括號。</span><span class="sxs-lookup"><span data-stu-id="04bb5-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="04bb5-147">下列範例與您建立的相同。</span><span class="sxs-lookup"><span data-stu-id="04bb5-147">The following example is the same as the one you created.</span></span> <span data-ttu-id="04bb5-148">修改程式碼，使它符合下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="04bb5-148">Modify your code above to match the following code:</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> <span data-ttu-id="04bb5-149">本教學課程的其餘部分，程式碼範例都會遵循常見的做法，在程式碼中包含大括號。</span><span class="sxs-lookup"><span data-stu-id="04bb5-149">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="04bb5-150">您可以測試更複雜的條件。</span><span class="sxs-lookup"><span data-stu-id="04bb5-150">You can test more complicated conditions.</span></span> <span data-ttu-id="04bb5-151">將下列程式碼新增至您目前已在 `Main` 方法中撰寫的內容後方：</span><span class="sxs-lookup"><span data-stu-id="04bb5-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

```csharp
int c = 4;
if ((a + b + c > 10) && (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not equal to the second");
}
```

<span data-ttu-id="04bb5-152">適用於*相等*的 `==` 符號測試。</span><span class="sxs-lookup"><span data-stu-id="04bb5-152">The `==` symbol tests for *equality*.</span></span> <span data-ttu-id="04bb5-153">使用 `==` 可區分指派中相等的測試，您在 `a = 5` 中看過該指派。</span><span class="sxs-lookup"><span data-stu-id="04bb5-153">Using `==` distinguishes the test for equality from assignment, which you saw in `a = 5`.</span></span>

<span data-ttu-id="04bb5-154">`&&` 代表「且」。</span><span class="sxs-lookup"><span data-stu-id="04bb5-154">The `&&` represents "and".</span></span> <span data-ttu-id="04bb5-155">這表示兩個條件都必須為 True，才會執行 True 分支中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="04bb5-155">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="04bb5-156">這些範例也示範在每個條件式分支中可以有多個陳述式，前提是必須將陳述式放在 `{` 和 `}` 之中。</span><span class="sxs-lookup"><span data-stu-id="04bb5-156">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="04bb5-157">您也可以使用 `||` 來代表「或」。</span><span class="sxs-lookup"><span data-stu-id="04bb5-157">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="04bb5-158">在您目前已撰寫的程式碼後方新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="04bb5-158">Add the following code after what you've written so far:</span></span>

```csharp
if ((a + b + c > 10) || (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not equal to the second");
}
```

<span data-ttu-id="04bb5-159">修改 `a`、`b` 和 `c` 的值，並在 `&&` 和 `||` 之間切換以進行探索。</span><span class="sxs-lookup"><span data-stu-id="04bb5-159">Modify the values of `a`, `b`, and `c` and switch between `&&` and `||` to explore.</span></span> <span data-ttu-id="04bb5-160">您將更加了解 `&&` 和 `||` 運算子的工作原理。</span><span class="sxs-lookup"><span data-stu-id="04bb5-160">You'll gain more understanding of how the `&&` and `||` operators work.</span></span>

<span data-ttu-id="04bb5-161">您已完成第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="04bb5-161">You've finished the first step.</span></span> <span data-ttu-id="04bb5-162">在開始下一節之前，讓我們將目前的程式碼移到另一個個別的方法。</span><span class="sxs-lookup"><span data-stu-id="04bb5-162">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="04bb5-163">這可讓您更輕鬆地開始處理新的範例。</span><span class="sxs-lookup"><span data-stu-id="04bb5-163">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="04bb5-164">將 `Main` 方法重新命名為 `ExploreIf`，然後撰寫會呼叫 `ExploreIf` 的新 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="04bb5-164">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="04bb5-165">當您完成時，您的程式碼看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="04bb5-165">When you've finished, your code should look like this:</span></span>

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            int c = 4;
            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

<span data-ttu-id="04bb5-166">將針對 `ExploreIf()` 的呼叫註解化。</span><span class="sxs-lookup"><span data-stu-id="04bb5-166">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="04bb5-167">這會在您處理本節的內容時，使輸出變得較為整齊：</span><span class="sxs-lookup"><span data-stu-id="04bb5-167">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="04bb5-168">`//` 會在 C# 中起始一段**註解**。</span><span class="sxs-lookup"><span data-stu-id="04bb5-168">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="04bb5-169">註解是您想保留在原始程式碼中，但不想要作為程式碼執行的任何文字。</span><span class="sxs-lookup"><span data-stu-id="04bb5-169">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="04bb5-170">編譯器不會從批註產生任何可執行檔程式碼。</span><span class="sxs-lookup"><span data-stu-id="04bb5-170">The compiler doesn't generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="04bb5-171">使用迴圈重複執行作業</span><span class="sxs-lookup"><span data-stu-id="04bb5-171">Use loops to repeat operations</span></span>

<span data-ttu-id="04bb5-172">在本節中，您會使用**迴圈**來重複語句。</span><span class="sxs-lookup"><span data-stu-id="04bb5-172">In this section, you use **loops** to repeat statements.</span></span> <span data-ttu-id="04bb5-173">請在您的 `Main` 方法中嘗試此程式碼：</span><span class="sxs-lookup"><span data-stu-id="04bb5-173">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="04bb5-174">`while` 陳述式會檢查條件，並執行 `while` 之後的陳述式或陳述式區塊。</span><span class="sxs-lookup"><span data-stu-id="04bb5-174">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="04bb5-175">它會重複檢查條件並執行那些陳述式，直到條件為 False 為止。</span><span class="sxs-lookup"><span data-stu-id="04bb5-175">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="04bb5-176">在此範例中有一個新的運算子。</span><span class="sxs-lookup"><span data-stu-id="04bb5-176">There's one other new operator in this example.</span></span> <span data-ttu-id="04bb5-177">`counter` 變數之後的 `++` 是**遞增**運算子。</span><span class="sxs-lookup"><span data-stu-id="04bb5-177">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="04bb5-178">它會將 1 加到 `counter` 上，並將該值儲存在 `counter` 變數中。</span><span class="sxs-lookup"><span data-stu-id="04bb5-178">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="04bb5-179">請確定 `while` 迴圈條件會在您執行程式碼時會切換至 False。</span><span class="sxs-lookup"><span data-stu-id="04bb5-179">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="04bb5-180">否則，您建立的**無限迴圈**程式永遠不會結束。</span><span class="sxs-lookup"><span data-stu-id="04bb5-180">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="04bb5-181">我們不會在此範例中示範此狀況，因為您將必須使用 **CTRL-C**或其他方法來將程式強制結束。</span><span class="sxs-lookup"><span data-stu-id="04bb5-181">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="04bb5-182">`while` 迴圈會先測試條件，然後才執行 `while` 之後的程式碼。</span><span class="sxs-lookup"><span data-stu-id="04bb5-182">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="04bb5-183">`do` ... `while` 迴圈會先執行程式碼，然後才檢查條件。</span><span class="sxs-lookup"><span data-stu-id="04bb5-183">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="04bb5-184">*Do while*迴圈會顯示在下列程式碼中：</span><span class="sxs-lookup"><span data-stu-id="04bb5-184">The *do while* loop is shown in the following code:</span></span>

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="04bb5-185">此 `do` 迴圈和稍早的 `while` 迴圈都會產生相同的輸出。</span><span class="sxs-lookup"><span data-stu-id="04bb5-185">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="04bb5-186">使用 for 迴圈</span><span class="sxs-lookup"><span data-stu-id="04bb5-186">Work with the for loop</span></span>

<span data-ttu-id="04bb5-187">**for** 迴圈經常用於 C#。</span><span class="sxs-lookup"><span data-stu-id="04bb5-187">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="04bb5-188">請在您的 Main() 方法中嘗試此程式碼：</span><span class="sxs-lookup"><span data-stu-id="04bb5-188">Try this code in your Main() method:</span></span>

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="04bb5-189">先前的程式碼會執行與 `while` 您已使用的迴圈和迴圈相同的工作 `do` 。</span><span class="sxs-lookup"><span data-stu-id="04bb5-189">The previous code does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="04bb5-190">`for` 陳述式有三個部分來控制其運作方式。</span><span class="sxs-lookup"><span data-stu-id="04bb5-190">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="04bb5-191">第一個部分是**for 初始化運算式**：宣告 `int index = 0;` `index` 是迴圈變數，並將它的初始值設為 `0` 。</span><span class="sxs-lookup"><span data-stu-id="04bb5-191">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="04bb5-192">中間部分是**for 條件**：宣告 `index < 10` 此 `for` 迴圈只要 counter 的值小於10，就會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="04bb5-192">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="04bb5-193">最後一個部分是**for iterator**： `index++` 指定在語句後面執行區塊之後，如何修改迴圈變數 `for` 。</span><span class="sxs-lookup"><span data-stu-id="04bb5-193">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="04bb5-194">在這裡，它指定 `index` 應該在每次執行區塊之後遞增 1。</span><span class="sxs-lookup"><span data-stu-id="04bb5-194">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="04bb5-195">自行實驗。</span><span class="sxs-lookup"><span data-stu-id="04bb5-195">Experiment yourself.</span></span> <span data-ttu-id="04bb5-196">請嘗試下列每個變化：</span><span class="sxs-lookup"><span data-stu-id="04bb5-196">Try each of the following variations:</span></span>

- <span data-ttu-id="04bb5-197">變更初始設定式，以不同的值開始。</span><span class="sxs-lookup"><span data-stu-id="04bb5-197">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="04bb5-198">變更條件，以不同的值停止。</span><span class="sxs-lookup"><span data-stu-id="04bb5-198">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="04bb5-199">當您完成後，我們會繼續使用您學到的內容來撰寫一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="04bb5-199">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

<span data-ttu-id="04bb5-200">本教學課程未涵蓋的另一個迴圈語句： `foreach` 語句。</span><span class="sxs-lookup"><span data-stu-id="04bb5-200">There's one other looping statement that isn't covered in this tutorial: the `foreach` statement.</span></span> <span data-ttu-id="04bb5-201">`foreach`語句會針對專案序列中的每個專案重複其語句。</span><span class="sxs-lookup"><span data-stu-id="04bb5-201">The `foreach` statement repeats its statement for every item in a sequence of items.</span></span> <span data-ttu-id="04bb5-202">它最常用於*集合*，因此在下一個教學課程中有涵蓋。</span><span class="sxs-lookup"><span data-stu-id="04bb5-202">It's most often used with *collections*, so it's covered in the next tutorial.</span></span>

## <a name="created-nested-loops"></a><span data-ttu-id="04bb5-203">建立的嵌套迴圈</span><span class="sxs-lookup"><span data-stu-id="04bb5-203">Created nested loops</span></span>

<span data-ttu-id="04bb5-204">`while`、 `do` 或 `for` 迴圈可以嵌套在另一個迴圈內，以使用外部迴圈中每個專案的組合與內部迴圈中的每個專案來建立矩陣。</span><span class="sxs-lookup"><span data-stu-id="04bb5-204">A `while`, `do`, or `for` loop can be nested inside another loop to create a matrix using the combination of each item in the outer loop with each item in the inner loop.</span></span> <span data-ttu-id="04bb5-205">讓我們來建立一組英數位元，以代表資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="04bb5-205">Let's do that to build a set of alphanumeric pairs to represent rows and columns.</span></span>

<span data-ttu-id="04bb5-206">一個 `for` 迴圈可以產生資料列：</span><span class="sxs-lookup"><span data-stu-id="04bb5-206">One `for` loop can generate the rows:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    Console.WriteLine($"The row is {row}");
}
```

<span data-ttu-id="04bb5-207">另一個迴圈可以產生資料行：</span><span class="sxs-lookup"><span data-stu-id="04bb5-207">Another loop can generate the columns:</span></span>

```csharp
for (char column = 'a'; column < 'k'; column++)
{
    Console.WriteLine($"The column is {column}");
}
```

<span data-ttu-id="04bb5-208">您可以將一個迴圈放在另一個，以形成配對：</span><span class="sxs-lookup"><span data-stu-id="04bb5-208">You can nest one loop inside the other to form pairs:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    for (char column = 'a'; column < 'k'; column++)
    {
        Console.WriteLine($"The cell is ({row}, {column})");
    }
}
```

<span data-ttu-id="04bb5-209">您可以看到外部迴圈會針對內部迴圈的每個完整執行遞增一次。</span><span class="sxs-lookup"><span data-stu-id="04bb5-209">You can see that the outer loop increments once for each full run of the inner loop.</span></span> <span data-ttu-id="04bb5-210">反轉資料列和資料行的嵌套，並查看您自己的變更。</span><span class="sxs-lookup"><span data-stu-id="04bb5-210">Reverse the row and column nesting, and see the changes for yourself.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="04bb5-211">結合分支和迴圈</span><span class="sxs-lookup"><span data-stu-id="04bb5-211">Combine branches and loops</span></span>

<span data-ttu-id="04bb5-212">您已經了解 C# 語言中的 `if` 陳述式和迴圈建構，接著看看您是否能夠撰寫 C# 程式碼，以找出從整數 1 至 20 能夠被 3 整除之數字的總和。</span><span class="sxs-lookup"><span data-stu-id="04bb5-212">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="04bb5-213">下列提供幾個提示：</span><span class="sxs-lookup"><span data-stu-id="04bb5-213">Here are a few hints:</span></span>

- <span data-ttu-id="04bb5-214">`%` 運算子可提供除法運算的餘數。</span><span class="sxs-lookup"><span data-stu-id="04bb5-214">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="04bb5-215">`if` 陳述式可提供條件，以判斷數字是否應為總和的一部分。</span><span class="sxs-lookup"><span data-stu-id="04bb5-215">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="04bb5-216">`for` 迴圈可協助您將 1 到 20 的所有數字重複一系列的步驟。</span><span class="sxs-lookup"><span data-stu-id="04bb5-216">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="04bb5-217">請自己試試看。</span><span class="sxs-lookup"><span data-stu-id="04bb5-217">Try it yourself.</span></span> <span data-ttu-id="04bb5-218">然後檢查成果。</span><span class="sxs-lookup"><span data-stu-id="04bb5-218">Then check how you did.</span></span> <span data-ttu-id="04bb5-219">您獲得的答案應該是 63。</span><span class="sxs-lookup"><span data-stu-id="04bb5-219">You should get 63 for an answer.</span></span> <span data-ttu-id="04bb5-220">您可以[在 GitHub 上檢視完整的程式碼](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54) \(英文\) 來查看其中一個可能的答案。</span><span class="sxs-lookup"><span data-stu-id="04bb5-220">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="04bb5-221">您已經完成＜分支和迴圈＞教學課程。</span><span class="sxs-lookup"><span data-stu-id="04bb5-221">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="04bb5-222">您可以在自己的開發環境中，繼續完成[陣列和集合](arrays-and-collections.md)教學課程中的內容。</span><span class="sxs-lookup"><span data-stu-id="04bb5-222">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="04bb5-223">您可以在下列文章中深入瞭解這些概念：</span><span class="sxs-lookup"><span data-stu-id="04bb5-223">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="04bb5-224">If 和 else 陳述式</span><span class="sxs-lookup"><span data-stu-id="04bb5-224">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="04bb5-225">While 語句</span><span class="sxs-lookup"><span data-stu-id="04bb5-225">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="04bb5-226">Do 陳述式</span><span class="sxs-lookup"><span data-stu-id="04bb5-226">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="04bb5-227">For 語句</span><span class="sxs-lookup"><span data-stu-id="04bb5-227">For statement</span></span>](../../language-reference/keywords/for.md)
