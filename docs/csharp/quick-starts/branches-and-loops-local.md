---
title: "快速入門-分支和 lops-C# 手冊"
description: "在這個快速入門有關分支和迴圈中，撰寫 C# 程式碼來瀏覽支援條件式分支和迴圈重複執行陳述式的語言語法。"
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 4b077a29cf42072a93b054f50a13a4580ad54304
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2017
---
# <a name="branches-and-loops"></a><span data-ttu-id="f0a21-103">分支和迴圈</span><span class="sxs-lookup"><span data-stu-id="f0a21-103">Branches and loops</span></span>

<span data-ttu-id="f0a21-104">本快速入門將教導您如何撰寫程式碼，以檢查變數，並變更這些變數為基礎的執行路徑。</span><span class="sxs-lookup"><span data-stu-id="f0a21-104">This quick start teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="f0a21-105">您撰寫 C# 程式碼，請參閱 < 編譯和執行它的結果。</span><span class="sxs-lookup"><span data-stu-id="f0a21-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="f0a21-106">快速入門中包含一系列的瀏覽分支和迴圈建構在 C# 中的課程。</span><span class="sxs-lookup"><span data-stu-id="f0a21-106">The quick start contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="f0a21-107">這些課程會教導您 C# 語言的基本概念。</span><span class="sxs-lookup"><span data-stu-id="f0a21-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="f0a21-108">本快速入門預期要有可用於開發的機器。</span><span class="sxs-lookup"><span data-stu-id="f0a21-108">This quick start expects you to have a machine you can use for development.</span></span> <span data-ttu-id="f0a21-109">.NET 主題[開始在 10 分鐘後](https://www.microsoft.com/net/core)已設定 Mac、 電腦或 Linux 本機開發環境的指示。</span><span class="sxs-lookup"><span data-stu-id="f0a21-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="f0a21-110">使用進行決策`if`陳述式</span><span class="sxs-lookup"><span data-stu-id="f0a21-110">Make decisions using the `if` statement</span></span>

<span data-ttu-id="f0a21-111">建立名為目錄**分支快速入門**。</span><span class="sxs-lookup"><span data-stu-id="f0a21-111">Create a directory named **branches-quickstart**.</span></span> <span data-ttu-id="f0a21-112">將該目錄設為目前的目錄，並執行 `dotnet new console -n BranchesAndLoops -o .`。</span><span class="sxs-lookup"><span data-stu-id="f0a21-112">Make that the current directory and run `dotnet new console -n BranchesAndLoops -o .`.</span></span> <span data-ttu-id="f0a21-113">此命令會建立新的.NET Core 主控台應用程式目前的目錄中。</span><span class="sxs-lookup"><span data-stu-id="f0a21-113">This command creates a new .NET Core console application in the current directory.</span></span> 

<span data-ttu-id="f0a21-114">開啟**Program.cs**中您最愛的編輯器和取代列`Console.Writeline("Hello World!");`為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="f0a21-114">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="f0a21-115">此程式碼嘗試輸入`dotnet run`在主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="f0a21-115">Try this code by typing `dotnet run` in the your console window.</span></span> <span data-ttu-id="f0a21-116">您應該會看到訊息 「 回應 」 大於 10。</span><span class="sxs-lookup"><span data-stu-id="f0a21-116">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="f0a21-117">列印至主控台。</span><span class="sxs-lookup"><span data-stu-id="f0a21-117">printed to your console.</span></span>

<span data-ttu-id="f0a21-118">修改 `b` 的宣告，讓總和小於 10：</span><span class="sxs-lookup"><span data-stu-id="f0a21-118">Modify the declaration of `b` so that the sum is less than 10:</span></span> 

```csharp
int b = 3;
```

<span data-ttu-id="f0a21-119">型別`dotnet run`一次。</span><span class="sxs-lookup"><span data-stu-id="f0a21-119">Type `dotnet run` again.</span></span> <span data-ttu-id="f0a21-120">因為答案小於 10，所以不會印出任何東西。</span><span class="sxs-lookup"><span data-stu-id="f0a21-120">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="f0a21-121">您正在測試的**條件**為 False。</span><span class="sxs-lookup"><span data-stu-id="f0a21-121">The **condition** you're testing is false.</span></span> <span data-ttu-id="f0a21-122">您尚未有可執行的程式碼，因為您在 `if` 陳述式中僅撰寫了一個可能的分支：True 分支。</span><span class="sxs-lookup"><span data-stu-id="f0a21-122">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="f0a21-123">在您探索 C# (或任何程式設計語言) 時，可能會在撰寫程式碼時犯錯。</span><span class="sxs-lookup"><span data-stu-id="f0a21-123">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="f0a21-124">編譯器會尋找並報告該錯誤。</span><span class="sxs-lookup"><span data-stu-id="f0a21-124">The compiler will find and report the errors.</span></span> <span data-ttu-id="f0a21-125">請仔細查看錯誤輸出，並且產生錯誤的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f0a21-125">Look closely the the error output and the code that generated the error.</span></span> <span data-ttu-id="f0a21-126">Compler 錯誤通常可協助您找出問題。</span><span class="sxs-lookup"><span data-stu-id="f0a21-126">The compler error can usually help you find the problem.</span></span> 

<span data-ttu-id="f0a21-127">此第一個範例顯示的電源`if`和布林型別。</span><span class="sxs-lookup"><span data-stu-id="f0a21-127">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="f0a21-128">A*布林*是一個變數，可以有兩個值之一：`true`或`false`。</span><span class="sxs-lookup"><span data-stu-id="f0a21-128">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="f0a21-129">C# 定義一種特殊類型，`bool`的布林值變數。</span><span class="sxs-lookup"><span data-stu-id="f0a21-129">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="f0a21-130">`if` 陳述式會檢查 `bool` 的值。</span><span class="sxs-lookup"><span data-stu-id="f0a21-130">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="f0a21-131">當值為 `true` 時，就會執行 `if` 之後的陳述式。</span><span class="sxs-lookup"><span data-stu-id="f0a21-131">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="f0a21-132">否則，就會略過。</span><span class="sxs-lookup"><span data-stu-id="f0a21-132">Otherwise, it is skipped.</span></span> 

<span data-ttu-id="f0a21-133">這個流程可以檢查條件，並根據條件來執行陳述式，因此非常實用。</span><span class="sxs-lookup"><span data-stu-id="f0a21-133">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>


## <a name="make-if-and-else-work-together"></a><span data-ttu-id="f0a21-134">搭配使用 if 和 else</span><span class="sxs-lookup"><span data-stu-id="f0a21-134">Make if and else work together</span></span>

<span data-ttu-id="f0a21-135">若要在 True 和 False 分支中執行不同的程式碼，則必須建立可在條件為 False 時執行的 `else` 分支。</span><span class="sxs-lookup"><span data-stu-id="f0a21-135">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="f0a21-136">試試看。</span><span class="sxs-lookup"><span data-stu-id="f0a21-136">Try this.</span></span> <span data-ttu-id="f0a21-137">在下列程式碼，若要加入的最後兩行程式`Main`（您應該已經前四個） 的方法：</span><span class="sxs-lookup"><span data-stu-id="f0a21-137">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="f0a21-138">只有當測試的條件為 `false` 時，才會執行 `else` 關鍵字之後的陳述式。</span><span class="sxs-lookup"><span data-stu-id="f0a21-138">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="f0a21-139">結合`if`和`else`使用布林值條件提供您需要同時處理的所有電源`true`和`false`條件。</span><span class="sxs-lookup"><span data-stu-id="f0a21-139">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0a21-140">`if` 和 `else` 陳述式之下的縮排是為了方便人類閱讀。</span><span class="sxs-lookup"><span data-stu-id="f0a21-140">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="f0a21-141">C# 語言不會將縮排或空格視為有意義的內容。</span><span class="sxs-lookup"><span data-stu-id="f0a21-141">The C# language doesn't treat indentation or whitespace as significant.</span></span> <span data-ttu-id="f0a21-142">`if` 或 `else` 關鍵字之後的陳述式將會根據條件來執行。</span><span class="sxs-lookup"><span data-stu-id="f0a21-142">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="f0a21-143">在這個快速入門中的所有範例，請依照都下列常見的作法是根據陳述式的控制流程的行縮排。</span><span class="sxs-lookup"><span data-stu-id="f0a21-143">All the samples in this quick start follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="f0a21-144">因為縮排沒有意義，當您要依條件執行的區塊中有超過一個陳述式時，就需要使用 `{` 和 `}` 來表示。</span><span class="sxs-lookup"><span data-stu-id="f0a21-144">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="f0a21-145">C# 程式設計人員通常會在所有的 `if` 和 `else` 子句上使用這些大括號。</span><span class="sxs-lookup"><span data-stu-id="f0a21-145">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="f0a21-146">下列範例是您剛才建立一個相同。</span><span class="sxs-lookup"><span data-stu-id="f0a21-146">The following example is the same as the one you just created.</span></span> <span data-ttu-id="f0a21-147">修改以符合下列程式碼上述程式碼：</span><span class="sxs-lookup"><span data-stu-id="f0a21-147">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="f0a21-148">透過本快速入門的其餘部分，所有的程式碼範例包含大括號，接受的作法。</span><span class="sxs-lookup"><span data-stu-id="f0a21-148">Through the rest of this quick start, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="f0a21-149">您可以測試更複雜的條件。</span><span class="sxs-lookup"><span data-stu-id="f0a21-149">You can test more complicated conditions.</span></span> <span data-ttu-id="f0a21-150">加入下列程式碼中的您`Main`到目前為止，您所撰寫的程式碼之後的方法：</span><span class="sxs-lookup"><span data-stu-id="f0a21-150">Add the following code in your `Main` method after the code you've written so far:</span></span>

```csharp
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
```

<span data-ttu-id="f0a21-151">`&&` 代表「且」。</span><span class="sxs-lookup"><span data-stu-id="f0a21-151">The `&&` represents "and".</span></span> <span data-ttu-id="f0a21-152">這表示兩個條件都必須為 True，才會執行 True 分支中的陳述式。</span><span class="sxs-lookup"><span data-stu-id="f0a21-152">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="f0a21-153">這些範例也示範在每個條件式分支中可以有多個陳述式，前提是必須將陳述式放在 `{` 和 `}` 之中。</span><span class="sxs-lookup"><span data-stu-id="f0a21-153">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="f0a21-154">您也可以使用`||`來代表 「 或 」。</span><span class="sxs-lookup"><span data-stu-id="f0a21-154">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="f0a21-155">加入下列程式碼之後您已經為止寫,：</span><span class="sxs-lookup"><span data-stu-id="f0a21-155">Add the following code after what you've written so far:</span></span>

```csharp
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
```

<span data-ttu-id="f0a21-156">您已完成的第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="f0a21-156">You've finished the first step.</span></span> <span data-ttu-id="f0a21-157">在開始下一節之前，讓我們將目前的程式碼移到另一個個別的方法。</span><span class="sxs-lookup"><span data-stu-id="f0a21-157">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="f0a21-158">這可讓您更輕鬆地開始處理新的範例。</span><span class="sxs-lookup"><span data-stu-id="f0a21-158">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="f0a21-159">將 `Main` 方法重新命名為 `ExploreIf`，然後撰寫會呼叫 `ExploreIf` 的新 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="f0a21-159">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="f0a21-160">當您完成時，您的程式碼看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="f0a21-160">When you have finished, your code should look like this:</span></span>

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

<span data-ttu-id="f0a21-161">註解的呼叫`ExploreIf()`。</span><span class="sxs-lookup"><span data-stu-id="f0a21-161">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="f0a21-162">如此可讓更整齊的您在這一節中工作的輸出：</span><span class="sxs-lookup"><span data-stu-id="f0a21-162">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="f0a21-163">`//`啟動**註解**C# 中。</span><span class="sxs-lookup"><span data-stu-id="f0a21-163">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="f0a21-164">註解是您想要保留在原始程式碼中，但不是會以程式碼執行的任何文字。</span><span class="sxs-lookup"><span data-stu-id="f0a21-164">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="f0a21-165">編譯器不從註解會產生任何可執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="f0a21-165">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="f0a21-166">使用迴圈重複執行作業</span><span class="sxs-lookup"><span data-stu-id="f0a21-166">Use loops to repeat operations</span></span>

<span data-ttu-id="f0a21-167">在您使用這一節**迴圈**重複陳述式。</span><span class="sxs-lookup"><span data-stu-id="f0a21-167">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="f0a21-168">請嘗試此程式碼中的您`Main`方法：</span><span class="sxs-lookup"><span data-stu-id="f0a21-168">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="f0a21-169">`while`陳述式會檢查條件，並執行陳述式或之後的陳述式區塊`while`。</span><span class="sxs-lookup"><span data-stu-id="f0a21-169">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="f0a21-170">它會重複檢查的條件和執行這些陳述式，直到條件為 false。</span><span class="sxs-lookup"><span data-stu-id="f0a21-170">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="f0a21-171">在此範例中有一個新的運算子。</span><span class="sxs-lookup"><span data-stu-id="f0a21-171">There's one other new operator in this example.</span></span> <span data-ttu-id="f0a21-172">`counter` 變數之後的 `++` 是**遞增**運算子。</span><span class="sxs-lookup"><span data-stu-id="f0a21-172">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="f0a21-173">它將值加 1 `counter` ，並將此值於`counter`變數。</span><span class="sxs-lookup"><span data-stu-id="f0a21-173">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f0a21-174">請確定`while`迴圈條件變更為 false，因為執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f0a21-174">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="f0a21-175">否則，您建立的**無限迴圈**程式永遠不會結束。</span><span class="sxs-lookup"><span data-stu-id="f0a21-175">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="f0a21-176">不會示範在此範例中，因此您可以強制執行您的程式，若要結束使用**CTRL-C**或其他方式。</span><span class="sxs-lookup"><span data-stu-id="f0a21-176">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="f0a21-177">`while` 迴圈會先測試條件，然後才執行 `while` 之後的程式碼。</span><span class="sxs-lookup"><span data-stu-id="f0a21-177">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="f0a21-178">`do` ... `while` 迴圈會先執行程式碼，然後才檢查條件。</span><span class="sxs-lookup"><span data-stu-id="f0a21-178">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="f0a21-179">執行下列程式碼所示迴圈時：</span><span class="sxs-lookup"><span data-stu-id="f0a21-179">The do while loop is shown in the following code:</span></span>

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="f0a21-180">這`do`迴圈及更早版本`while`迴圈產生相同的輸出。</span><span class="sxs-lookup"><span data-stu-id="f0a21-180">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="f0a21-181">使用 for 迴圈</span><span class="sxs-lookup"><span data-stu-id="f0a21-181">Work with the for loop</span></span>

<span data-ttu-id="f0a21-182">**如**迴圈常用於 C#。</span><span class="sxs-lookup"><span data-stu-id="f0a21-182">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="f0a21-183">請嘗試在您的 main （） 方法中的這段程式碼：</span><span class="sxs-lookup"><span data-stu-id="f0a21-183">Try this code in your Main() method:</span></span>

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

<span data-ttu-id="f0a21-184">這與先前使用的 `while` 迴圈和 `do` 迴圈有相同的功能。</span><span class="sxs-lookup"><span data-stu-id="f0a21-184">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="f0a21-185">`for` 陳述式有三個部分來控制其運作方式。</span><span class="sxs-lookup"><span data-stu-id="f0a21-185">The `for` statement has three parts that control how it works.</span></span> 

<span data-ttu-id="f0a21-186">第一個部分是 **for 初始設定式**：`for index = 0;` 宣告 `index` 是迴圈變數，然後將它的初始值設為 `0`。</span><span class="sxs-lookup"><span data-stu-id="f0a21-186">The first part is the **for initializer**: `for index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="f0a21-187">中間的部分是 **for 條件**：`index < 10` 宣告此 `for` 迴圈只要 counter (計數器) 的值小於 10，就會繼續執行。</span><span class="sxs-lookup"><span data-stu-id="f0a21-187">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="f0a21-188">最後一個部分是 **for 迭代器**：`index++` 會指定在執行 `for` 陳述式之後的區塊後，如何修改迴圈變數。</span><span class="sxs-lookup"><span data-stu-id="f0a21-188">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="f0a21-189">在這裡，它指定 `index` 應該在每次執行區塊之後遞增 1。</span><span class="sxs-lookup"><span data-stu-id="f0a21-189">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="f0a21-190">您可以自行實驗這些部分。</span><span class="sxs-lookup"><span data-stu-id="f0a21-190">Experiment with these yourself.</span></span> <span data-ttu-id="f0a21-191">請嘗試下列各項：</span><span class="sxs-lookup"><span data-stu-id="f0a21-191">Try each of the following:</span></span>

- <span data-ttu-id="f0a21-192">變更初始設定式，以不同的值開始。</span><span class="sxs-lookup"><span data-stu-id="f0a21-192">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="f0a21-193">變更條件，以不同的值停止。</span><span class="sxs-lookup"><span data-stu-id="f0a21-193">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="f0a21-194">當您完成後，我們會繼續使用您學到的內容來撰寫一些程式碼。</span><span class="sxs-lookup"><span data-stu-id="f0a21-194">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="f0a21-195">結合分支和迴圈</span><span class="sxs-lookup"><span data-stu-id="f0a21-195">Combine branches and loops</span></span>

<span data-ttu-id="f0a21-196">您已經了解 C# 語言中的 `if` 陳述式和迴圈建構，接著看看您是否能夠撰寫 C# 程式碼，以找出從整數 1 至 20 能夠被 3 整除之數字的總和。</span><span class="sxs-lookup"><span data-stu-id="f0a21-196">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="f0a21-197">下列提供幾個提示：</span><span class="sxs-lookup"><span data-stu-id="f0a21-197">Here are a few hints:</span></span>

- <span data-ttu-id="f0a21-198">`%` 運算子可提供除法運算的餘數。</span><span class="sxs-lookup"><span data-stu-id="f0a21-198">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="f0a21-199">`if`陳述式可讓您的條件，請參閱是否數字應該加總的一部分。</span><span class="sxs-lookup"><span data-stu-id="f0a21-199">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="f0a21-200">`for` 迴圈可協助您將 1 到 20 的所有數字重複一系列的步驟。</span><span class="sxs-lookup"><span data-stu-id="f0a21-200">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="f0a21-201">請自己試試看。</span><span class="sxs-lookup"><span data-stu-id="f0a21-201">Try it yourself.</span></span> <span data-ttu-id="f0a21-202">然後檢查成果。</span><span class="sxs-lookup"><span data-stu-id="f0a21-202">Then check how you did.</span></span> <span data-ttu-id="f0a21-203">您可以看到所可能解答[GitHub 上檢視已完成的程式碼](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54)。</span><span class="sxs-lookup"><span data-stu-id="f0a21-203">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="f0a21-204">您已經完成 「 分支和迴圈 」 的快速入門。</span><span class="sxs-lookup"><span data-stu-id="f0a21-204">You've completed the "branches and loops" quick start.</span></span>

<span data-ttu-id="f0a21-205">您可以繼續使用[陣列與集合](arrays-and-collections.md)開發環境中的快速入門。</span><span class="sxs-lookup"><span data-stu-id="f0a21-205">You can continue with the [Arrays and collections](arrays-and-collections.md) quick start in your own development environment.</span></span>

<span data-ttu-id="f0a21-206">您可以在下列主題中深入了解這些概念：</span><span class="sxs-lookup"><span data-stu-id="f0a21-206">You can learn more about these concepts in these topics:</span></span>

<span data-ttu-id="f0a21-207">[If 和 else 陳述式](../language-reference/keywords/if-else.md) </span><span class="sxs-lookup"><span data-stu-id="f0a21-207">[If and else statement](../language-reference/keywords/if-else.md) </span></span>  
<span data-ttu-id="f0a21-208">[While 陳述式](../language-reference/keywords/while.md) </span><span class="sxs-lookup"><span data-stu-id="f0a21-208">[While statement](../language-reference/keywords/while.md) </span></span>  
<span data-ttu-id="f0a21-209">[Do 陳述式](../language-reference/keywords/do.md) </span><span class="sxs-lookup"><span data-stu-id="f0a21-209">[Do statement](../language-reference/keywords/do.md) </span></span>  
[<span data-ttu-id="f0a21-210">For 陳述式</span><span class="sxs-lookup"><span data-stu-id="f0a21-210">For statement</span></span>](../language-reference/keywords/for.md)   
