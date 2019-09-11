---
title: C# 中的數字 - C# 教學課程簡介
description: 透過探索數值類型及其屬性和方法來了解 C#。
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 436e8db10f973b468458987150e1312a16103b91
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850689"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="9d1c8-103">在 C\# 中操作整數和浮點數數字</span><span class="sxs-lookup"><span data-stu-id="9d1c8-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="9d1c8-104">此教學課程會以互動方式教導您有關 C# 中的數字型別。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="9d1c8-105">您將會撰寫少量程式碼，然後編譯並執行該程式碼。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="9d1c8-106">教學課程包含一系列探索 C# 中數字和數學運算的課程。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="9d1c8-107">這些課程會教導您 C# 語言的基本概念。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="9d1c8-108">此教學課程要求您必須有可用於開發的電腦。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="9d1c8-109">.NET 教學課程[Hello World 在10分鐘內](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)，有在 MAC、PC 或 Linux 上設定本機開發環境的指示。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="9d1c8-110">您可以在[熟悉開發工具](local-environment.md)中快速檢視將會用到的命令，並取得可提供詳細資料的連結。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="9d1c8-111">探索整數運算</span><span class="sxs-lookup"><span data-stu-id="9d1c8-111">Explore integer math</span></span>

<span data-ttu-id="9d1c8-112">建立名為 **numbers-quickstart** 的目錄。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-112">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="9d1c8-113">將該目錄設為目前的目錄，並執行 `dotnet new console -n NumbersInCSharp -o .`。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-113">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="9d1c8-114">在您最愛的編輯器中開啟 **Program.cs**，並以下列程式碼取代 `Console.WriteLine("Hello World!");` 程式碼行：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-114">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="9d1c8-115">在命令視窗中輸入 `dotnet run` 來執行此程式碼。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-115">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="9d1c8-116">您看到的只是一種基本的整數數學運算。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="9d1c8-117">`int` 型別代表**整數**，也就是正整數或負整數。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-117">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="9d1c8-118">您使用 `+` 符號來執行加法。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="9d1c8-119">整數常用的其他數學運算包括：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="9d1c8-120">`-` 用於減法</span><span class="sxs-lookup"><span data-stu-id="9d1c8-120">`-` for subtraction</span></span>
- <span data-ttu-id="9d1c8-121">`*` 用於乘法</span><span class="sxs-lookup"><span data-stu-id="9d1c8-121">`*` for multiplication</span></span>
- <span data-ttu-id="9d1c8-122">`/` 用於除法</span><span class="sxs-lookup"><span data-stu-id="9d1c8-122">`/` for division</span></span>

<span data-ttu-id="9d1c8-123">讓我們開始探索這些不同的運算。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-123">Start by exploring those different operations.</span></span> <span data-ttu-id="9d1c8-124">將下列程式碼行新增至撰寫 `c` 值的程式碼行後方：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="9d1c8-125">在命令視窗中輸入 `dotnet run` 來執行此程式碼。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-125">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="9d1c8-126">如果您想要的話，也可以試著在同一行中執行多個數學運算。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="9d1c8-127">嘗試使用 `c = a + b - 12 * 17;` 作為範例。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="9d1c8-128">允許混合變數和常數數字。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="9d1c8-129">在您探索 C# (或任何程式設計語言) 時，可能會在撰寫程式碼時犯錯。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="9d1c8-130">**編譯器**會找出那些錯誤並回報給您。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="9d1c8-131">當輸出包含錯誤訊息時，請仔細查看範例程式碼及視窗中的程式碼，看看有哪些可以修正。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="9d1c8-132">該練習將有助於您了解 C# 程式碼的結構。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-132">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="9d1c8-133">您已完成第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-133">You've finished the first step.</span></span> <span data-ttu-id="9d1c8-134">在開始下一節之前，讓我們將目前的程式碼移到另一個個別的方法。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="9d1c8-135">這可讓您更輕鬆地開始處理新的範例。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="9d1c8-136">將 `Main` 方法重新命名為 `WorkingWithIntegers`，然後撰寫會呼叫 `WorkingWithIntegers` 的新 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="9d1c8-137">當您完成時，您的程式碼看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-137">When you have finished, your code should look like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a><span data-ttu-id="9d1c8-138">探索運算的順序</span><span class="sxs-lookup"><span data-stu-id="9d1c8-138">Explore order of operations</span></span>

<span data-ttu-id="9d1c8-139">將針對 `WorkingWithIntegers()` 的呼叫註解化。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="9d1c8-140">這會在您處理本節的內容時，使輸出變得較為整齊：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="9d1c8-141">`//` 會在 C# 中起始一段**註解**。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="9d1c8-142">註解是您想保留在原始程式碼中，但不想要作為程式碼執行的任何文字。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="9d1c8-143">編譯器不會從註解產生任何可執行的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="9d1c8-144">針對不同數學運算的優先順序，C# 語言所定義的規則與您在數學所學的規則一致。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="9d1c8-145">乘法和除法的優先順序高於加法和減法。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="9d1c8-146">將下列程式碼新增至 `Main` 方法，並執行 `dotnet run` 來探索：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="9d1c8-147">輸出示範了程式會先執行乘法，然後再執行加法。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="9d1c8-148">您可以在想要優先執行的一個或多個運算前後加上括號，以強制執行不同的運算順序。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="9d1c8-149">新增下列程式碼行並再次執行：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-149">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="9d1c8-150">結合許多不同的運算來深入探索。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="9d1c8-151">在 `Main` 方法的底部新增類似下列程式碼行的內容。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="9d1c8-152">再次嘗試執行 `dotnet run`。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="9d1c8-153">您可能已注意到整數某個有趣的行為。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="9d1c8-154">整數的除法一律會產生整數結果，即使您認為結果應有小數或分數部分也一樣。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="9d1c8-155">如果您沒有看到此行為，請在 `Main` 方法的末端嘗試下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="9d1c8-156">再次輸入 `dotnet run` 來查看結果。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="9d1c8-157">在繼續後續內容之前，讓我們將您在本節中所撰寫的所有程式碼置於新的方法中。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="9d1c8-158">將新方法命名為 `OrderPrecedence`。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="9d1c8-159">最後的結果應該如下：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-159">You should end up with something like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
            c = a / b;
            Console.WriteLine(c);
        }

        static void OrderPrecedence()
        {
            int a = 5;
            int b = 4;
            int c = 2;
            int d = a + b * c;
            Console.WriteLine(d);

            d = (a  + b) * c;
            Console.WriteLine(d);

            d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
            Console.WriteLine(d);

            int e = 7;
            int f = 4;
            int g = 3;
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="9d1c8-160">探索整數的精確度與限制</span><span class="sxs-lookup"><span data-stu-id="9d1c8-160">Explore integer precision and limits</span></span>

<span data-ttu-id="9d1c8-161">上一個範例示範了整數除法運算會將結果截斷。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="9d1c8-162">您可以使用**模數**運算子 (`%` 字元) 來取得**餘數**。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="9d1c8-163">在 `Main` 方法中嘗試下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="9d1c8-164">C# 整數型別有一個地方與數學上的整數不同：`int` 型別有最小和最大限制。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="9d1c8-165">將下列程式碼新增至 `Main` 方法以查看那些限制：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-165">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="9d1c8-166">如果計算產生的值超出這些限制，就會發生**反向溢位**或**溢位**的情況。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="9d1c8-167">答案看起來會是從其中一個限制回繞至另一個限制。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="9d1c8-168">將下列兩行新增至 `Main` 方法以查看範例：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="9d1c8-169">請注意，答案非常接近最小 (負) 整數。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="9d1c8-170">這與 `min + 2` 相同。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-170">It's the same as `min + 2`.</span></span>
<span data-ttu-id="9d1c8-171">此加法運算已**溢出**整數允許的值。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="9d1c8-172">此答案是非常大的負數，這是因為溢位會從最大整數值「回繞」至最小整數值。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="9d1c8-173">當 `int` 型別不符合您的需求時，還有其他具有不同限制和精確度的數字型別可供使用。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="9d1c8-174">我們會在下一篇探索那些數字型別。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-174">Let's explore those next.</span></span>

<span data-ttu-id="9d1c8-175">同樣地，讓我們將您在本節中所撰寫的程式碼置於個別的方法中。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="9d1c8-176">將它命名為 `TestLimits`。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-176">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="9d1c8-177">使用 Double 型別</span><span class="sxs-lookup"><span data-stu-id="9d1c8-177">Work with the double type</span></span>

<span data-ttu-id="9d1c8-178">`double` 數字型別代表雙精確度浮點數。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="9d1c8-179">您可能不熟悉這些字詞。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-179">Those terms may be new to you.</span></span> <span data-ttu-id="9d1c8-180">**浮點數**可用以代表非常大或非常小的非整數數字。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="9d1c8-181">**雙精確度**表示這些數字使用比**單精確度**更高的精確度來儲存。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="9d1c8-182">在現代的電腦上，比較常使用雙精確度而非單精確度數字。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="9d1c8-183">讓我們開始探索吧。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-183">Let's explore.</span></span> <span data-ttu-id="9d1c8-184">新增下列程式碼並查看結果：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="9d1c8-185">請注意答案包括商數的小數部分。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="9d1c8-186">請嘗試略為複雜的雙精確度浮點數運算式：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="9d1c8-187">雙精確度浮點數值的範圍遠大於整數值。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="9d1c8-188">在您目前已撰寫的程式碼下方嘗試下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="9d1c8-189">這些值會以科學記號標記法呈現。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="9d1c8-190">`E` 左邊的數字是有效數字。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="9d1c8-191">右邊的數字則為指數，亦即 10 的次方。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-191">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="9d1c8-192">就像數學上的小數數字，C# 中的雙精確度浮點數會發生捨入誤差。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="9d1c8-193">請嘗試此程式碼：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="9d1c8-194">如您所知，`0.3` 循環與 `1/3` 並不完全相同。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="9d1c8-195">***挑戰***</span><span class="sxs-lookup"><span data-stu-id="9d1c8-195">***Challenge***</span></span>

<span data-ttu-id="9d1c8-196">嘗試使用 `double` 型別搭配大型數字、小型數字、乘法和除法的其他計算。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="9d1c8-197">嘗試更複雜的計算。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-197">Try more complicated calculations.</span></span>

<span data-ttu-id="9d1c8-198">在嘗試完成挑戰之後，請將您所撰寫的程式碼置於新的方法中。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="9d1c8-199">將新方法命名為 `WorkWithDoubles`。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="9d1c8-200">使用固定點型別</span><span class="sxs-lookup"><span data-stu-id="9d1c8-200">Work with fixed point types</span></span>

<span data-ttu-id="9d1c8-201">您已經看過 C# 中的基本數字型別：整數和雙精確度浮點數。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="9d1c8-202">還有一個您要了解的其他型別：`decimal` 型別。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="9d1c8-203">`decimal` 類型的範圍較小，但精確度較 `double` 來得高。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="9d1c8-204">**固定點**這個詞代表小數點 (或二進位點) 不會移動。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="9d1c8-205">讓我們來看一下：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="9d1c8-206">請注意該範圍小於 `double` 型別。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="9d1c8-207">透過嘗試下列程式碼，您可以看到 decimal (小數) 型別有較高的精確度：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="9d1c8-208">數字上的 `M` 尾碼乃是指示常數應使用 `decimal` 型別。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="9d1c8-209">請注意，使用 decimal (小數) 型別的運算在小數點右邊會有更多的數字。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="9d1c8-210">***挑戰***</span><span class="sxs-lookup"><span data-stu-id="9d1c8-210">***Challenge***</span></span>

<span data-ttu-id="9d1c8-211">您已經了解不同的數字型別，接著請撰寫程式碼，以計算半徑 2.50 公分的圓形面積。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="9d1c8-212">提醒您圓形面積是 PI 乘以半徑的平方。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="9d1c8-213">提示：.NET 包含 PI 的常數：<xref:System.Math.PI?displayProperty=nameWithType>，可用來作為該值。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span>

<span data-ttu-id="9d1c8-214">您應該會取得介於 19 和 20 的答案。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="9d1c8-215">您可以[在 GitHub 上查看完成的範例程式碼](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106) \(英文\) 來檢查您的答案</span><span class="sxs-lookup"><span data-stu-id="9d1c8-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="9d1c8-216">如果您想要的話，可以嘗試其他公式。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-216">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="9d1c8-217">您已完成＜C# 中的數字＞快速入門。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="9d1c8-218">您可以在自己的開發環境中，繼續完成[分支和迴圈](branches-and-loops-local.md)快速入門中的內容。</span><span class="sxs-lookup"><span data-stu-id="9d1c8-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="9d1c8-219">您可以在下列主題中深入了解 C# 中的數字：</span><span class="sxs-lookup"><span data-stu-id="9d1c8-219">You can learn more about numbers in C# in the following topics:</span></span>

- [<span data-ttu-id="9d1c8-220">整數型別</span><span class="sxs-lookup"><span data-stu-id="9d1c8-220">Integral types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="9d1c8-221">浮點型別表</span><span class="sxs-lookup"><span data-stu-id="9d1c8-221">Floating-Point Types Table</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="9d1c8-222">內建型別表</span><span class="sxs-lookup"><span data-stu-id="9d1c8-222">Built-In Types Table</span></span>](../../language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="9d1c8-223">隱含數值轉換表</span><span class="sxs-lookup"><span data-stu-id="9d1c8-223">Implicit Numeric Conversions Table</span></span>](../../language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="9d1c8-224">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="9d1c8-224">Explicit Numeric Conversions Table</span></span>](../../language-reference/keywords/explicit-numeric-conversions-table.md)
