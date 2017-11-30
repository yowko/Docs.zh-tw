---
title: "快速入門-C# 中的數字-C# 指南"
description: "了解 C# 中瀏覽數字型別、 屬性和方法。"
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 821cca4ea6d6148410e9b179f05d5b74c4844628
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2017
---
# <a name="numbers-in-c-quick-start"></a><span data-ttu-id="e8a6d-103">在 C# 快速入門中的數字</span><span class="sxs-lookup"><span data-stu-id="e8a6d-103">Numbers in C# quick start</span></span> #

<span data-ttu-id="e8a6d-104">本快速入門將教導您有關 C# 中的數字類型以互動方式。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-104">This quick start teaches you about the number types in C# interactively.</span></span> <span data-ttu-id="e8a6d-105">您會將寫入少量程式碼，然後您會編譯並執行該程式碼。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="e8a6d-106">快速入門中包含一系列的課程中，瀏覽數字和 C# 中的數學運算作業。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-106">The quick start contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="e8a6d-107">這些課程會教導您 C# 語言的基本概念。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="e8a6d-108">本快速入門預期要有可用於開發的機器。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-108">This quick start expects you to have a machine you can use for development.</span></span> <span data-ttu-id="e8a6d-109">.NET 主題[開始在 10 分鐘後](https://www.microsoft.com/net/core)已設定 Mac、 電腦或 Linux 本機開發環境的指示。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="e8a6d-110">探索整數運算</span><span class="sxs-lookup"><span data-stu-id="e8a6d-110">Explore integer math</span></span>

<span data-ttu-id="e8a6d-111">建立名為目錄**數字快速入門**。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-111">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="e8a6d-112">將該目錄設為目前的目錄，並執行 `dotnet new console -n NumbersInCSharp -o .`。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-112">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="e8a6d-113">開啟**Program.cs**中您最愛的編輯器和取代列`Console.Writeline("Hello World!");`為下列：</span><span class="sxs-lookup"><span data-stu-id="e8a6d-113">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="e8a6d-114">執行這個程式碼輸入`dotnet run`命令視窗中。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-114">Run this code by typing `dotnet run` in your command window.</span></span> 

<span data-ttu-id="e8a6d-115">您看到的只是一種基本的整數數學運算。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-115">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="e8a6d-116">`int` 型別代表**整數**，也就是正整數或負整數。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-116">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="e8a6d-117">您使用 `+` 符號來執行加法。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-117">You use the `+` symbol for addition.</span></span> <span data-ttu-id="e8a6d-118">整數常用的其他數學運算包括：</span><span class="sxs-lookup"><span data-stu-id="e8a6d-118">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="e8a6d-119">`-` 用於減法</span><span class="sxs-lookup"><span data-stu-id="e8a6d-119">`-` for subtraction</span></span>
- <span data-ttu-id="e8a6d-120">`*` 用於乘法</span><span class="sxs-lookup"><span data-stu-id="e8a6d-120">`*` for multiplication</span></span>
- <span data-ttu-id="e8a6d-121">`/` 用於除法</span><span class="sxs-lookup"><span data-stu-id="e8a6d-121">`/` for division</span></span>

<span data-ttu-id="e8a6d-122">讓我們開始探索這些不同的運算。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-122">Start by exploring those different operations.</span></span> <span data-ttu-id="e8a6d-123">值寫入的該行之後加入下列幾行`c`:</span><span class="sxs-lookup"><span data-stu-id="e8a6d-123">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="e8a6d-124">執行這個程式碼輸入`dotnet run`命令視窗中。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-124">Run this code by typing `dotnet run` in your command window.</span></span> 
    
<span data-ttu-id="e8a6d-125">如果您想要的話，也可以試著在同一行中執行多個數學運算。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-125">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="e8a6d-126">再試一次`c = a + b - 12 * 17;`例如。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-126">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="e8a6d-127">允許混合變數和常數的數字。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-127">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="e8a6d-128">在您探索 C# (或任何程式設計語言) 時，可能會在撰寫程式碼時犯錯。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-128">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="e8a6d-129">**編譯器**會找出那些錯誤並回報給您。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-129">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="e8a6d-130">當輸出會包含錯誤訊息時，仔細查看範例程式碼和您的視窗來查看要修正的項目中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-130">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="e8a6d-131">該練習將有助於您了解 C# 程式碼的結構。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-131">That exercise will help you learn the structure of C# code.</span></span>     

<span data-ttu-id="e8a6d-132">您已完成的第一個步驟。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-132">You've finished the first step.</span></span> <span data-ttu-id="e8a6d-133">在開始下一節之前，讓我們將目前的程式碼移到另一個個別的方法。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-133">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="e8a6d-134">這可讓您更輕鬆地開始處理新的範例。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-134">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="e8a6d-135">將 `Main` 方法重新命名為 `WorkingWithIntegers`，然後撰寫會呼叫 `WorkingWithIntegers` 的新 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-135">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="e8a6d-136">當您完成時，您的程式碼看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="e8a6d-136">When you have finished, your code should look like this:</span></span>

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

## <a name="explore-order-of-operations"></a><span data-ttu-id="e8a6d-137">探索運算的順序</span><span class="sxs-lookup"><span data-stu-id="e8a6d-137">Explore order of operations</span></span>

<span data-ttu-id="e8a6d-138">註解的呼叫`WorkingWithIntegers()`。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-138">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="e8a6d-139">如此可讓更整齊的您在這一節中工作的輸出：</span><span class="sxs-lookup"><span data-stu-id="e8a6d-139">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="e8a6d-140">`//`啟動**註解**C# 中。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-140">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="e8a6d-141">註解是您想要保留在原始程式碼中，但不是會以程式碼執行的任何文字。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-141">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="e8a6d-142">編譯器不從註解會產生任何可執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-142">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="e8a6d-143">針對不同數學運算的優先順序，C# 語言所定義的規則與您在數學所學的規則一致。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-143">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="e8a6d-144">乘法和除法的優先順序高於加法和減法。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-144">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="e8a6d-145">瀏覽，加入下列程式碼加入您`Main`方法，以及 execuing `dotnet run`:</span><span class="sxs-lookup"><span data-stu-id="e8a6d-145">Explore that by adding the following code to your `Main` method, and execuing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="e8a6d-146">輸出示範了程式會先執行乘法，然後再執行加法。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-146">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="e8a6d-147">您可以強制不同作業的順序加入周圍的括號，或您希望的作業執行第一次。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-147">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="e8a6d-148">加入下列幾行，然後再次執行：</span><span class="sxs-lookup"><span data-stu-id="e8a6d-148">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="e8a6d-149">結合許多不同的運算來深入探索。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-149">Explore more by combining many different operations.</span></span> <span data-ttu-id="e8a6d-150">結果類似下列幾行加入底部您`Main`方法。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-150">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="e8a6d-151">再試一次`dotnet run`一次。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-151">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="e8a6d-152">您可能已注意到整數某個有趣的行為。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-152">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="e8a6d-153">整數除法一律會產生整數結果，即使您希望的結果以包含十進位或小數部分。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-153">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="e8a6d-154">如果您還沒看過這項行為，請嘗試下列程式碼的結尾您`Main`方法：</span><span class="sxs-lookup"><span data-stu-id="e8a6d-154">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="e8a6d-155">型別`dotnet run`一次，以查看結果。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-155">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="e8a6d-156">再移，讓我們看您撰寫的這一節，並將其放在新的方法的所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-156">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="e8a6d-157">呼叫該新方法`OrderPrecedence`。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-157">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="e8a6d-158">您應該得到結果類似這樣：</span><span class="sxs-lookup"><span data-stu-id="e8a6d-158">You should end up with something like this:</span></span>

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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="e8a6d-159">探索整數的精確度與限制</span><span class="sxs-lookup"><span data-stu-id="e8a6d-159">Explore integer precision and limits</span></span>
<span data-ttu-id="e8a6d-160">上一個範例示範了整數除法運算會將結果截斷。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-160">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="e8a6d-161">您可以取得**餘數**使用**模數**運算子，`%`字元。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-161">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="e8a6d-162">請嘗試下列的程式碼中您`Main`方法：</span><span class="sxs-lookup"><span data-stu-id="e8a6d-162">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="e8a6d-163">C# 整數型別有一個地方與數學上的整數不同：`int` 型別有最小和最大限制。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-163">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="e8a6d-164">將此程式碼加入您`Main`方法以查看這些限制：</span><span class="sxs-lookup"><span data-stu-id="e8a6d-164">Add this code to your `Main` method to see those limits:</span></span>
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="e8a6d-165">如果計算產生的值超出這些限制，就會發生**反向溢位**或**溢位**的情況。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-165">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="e8a6d-166">答案看起來會是從其中一個限制回繞至另一個限制。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-166">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="e8a6d-167">加入至這兩行程式`Main`方法的範例，請參閱：</span><span class="sxs-lookup"><span data-stu-id="e8a6d-167">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
<span data-ttu-id="e8a6d-168">請注意，答案非常接近最小 (負) 整數。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-168">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="e8a6d-169">這與 `min + 2` 相同。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-169">It's the same as `min + 2`.</span></span> <span data-ttu-id="e8a6d-170">此加法運算已**溢出**整數允許的值。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-170">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="e8a6d-171">此答案是非常大的負數，這是因為溢位會從最大整數值「回繞」至最小整數值。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-171">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="e8a6d-172">當 `int` 型別不符合您的需求時，還有其他具有不同限制和精確度的數字型別可供使用。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-172">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="e8a6d-173">我們會在下一篇探索那些數字型別。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-173">Let's explore those next.</span></span>

<span data-ttu-id="e8a6d-174">同樣地，我們將移到不同的方法本節中您撰寫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-174">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="e8a6d-175">將它命名為 `TestLimits`。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-175">Name it `TestLimits`.</span></span> 

## <a name="work-with-the-double-type"></a><span data-ttu-id="e8a6d-176">使用 Double 型別</span><span class="sxs-lookup"><span data-stu-id="e8a6d-176">Work with the double type</span></span>

<span data-ttu-id="e8a6d-177">`double` 數字型別代表雙精確度浮點數。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-177">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="e8a6d-178">您可能不熟悉這些字詞。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-178">Those terms may be new to you.</span></span> <span data-ttu-id="e8a6d-179">A**浮點數**數目是用於表示非整數類資料可能非常大或最小範圍內的數字。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-179">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="e8a6d-180">**雙精確度**表示這些數字使用比**單精確度**更高的精確度來儲存。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-180">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="e8a6d-181">在現代的電腦上，比較常使用雙精確度而非單精確度數字。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-181">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="e8a6d-182">讓我們開始探索吧。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-182">Let's explore.</span></span> <span data-ttu-id="e8a6d-183">加入下列程式碼，並查看結果：</span><span class="sxs-lookup"><span data-stu-id="e8a6d-183">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="e8a6d-184">請注意答案包括商數的小數部分。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-184">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="e8a6d-185">請嘗試略為複雜的雙精確度浮點數運算式：</span><span class="sxs-lookup"><span data-stu-id="e8a6d-185">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="e8a6d-186">雙精確度浮點數值的範圍遠大於整數值。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-186">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="e8a6d-187">請嘗試下列您完成為止撰寫下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="e8a6d-187">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="e8a6d-188">這些值列印出來的科學記號標記法。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-188">These values are printed out in scientific notation.</span></span> <span data-ttu-id="e8a6d-189">左邊的數字`E`是有效的數字。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-189">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="e8a6d-190">右邊的數字則為指數，亦即 10 的次方。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-190">The number to the right is the exponent, as a power of 10.</span></span> 

<span data-ttu-id="e8a6d-191">就像數學上的小數數字，C# 中的雙精確度浮點數會發生捨入誤差。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-191">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="e8a6d-192">請嘗試此程式碼：</span><span class="sxs-lookup"><span data-stu-id="e8a6d-192">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="e8a6d-193">如您所知，`0.3` 循環與 `1/3` 並不完全相同。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-193">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="e8a6d-194">***挑戰***</span><span class="sxs-lookup"><span data-stu-id="e8a6d-194">***Challenge***</span></span>

<span data-ttu-id="e8a6d-195">嘗試使用 `double` 型別搭配大型數字、小型數字、乘法和除法的其他計算。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-195">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="e8a6d-196">嘗試更複雜的計算。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-196">Try more complicated calculations.</span></span>

<span data-ttu-id="e8a6d-197">您會花費一些時間與挑戰之後，需要您所撰寫，並將它放在新的方法中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-197">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="e8a6d-198">命名新方法`WorkWithDoubles`。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-198">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="e8a6d-199">使用固定點型別</span><span class="sxs-lookup"><span data-stu-id="e8a6d-199">Work with fixed point types</span></span>

<span data-ttu-id="e8a6d-200">您已經看過 C# 中的基本數字型別：整數和雙精確度浮點數。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-200">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="e8a6d-201">還有一個您要了解的其他型別：`decimal` 型別。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-201">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="e8a6d-202">`decimal`類型具有較小的範圍，但精確度卻高於`double`。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-202">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="e8a6d-203">**固定點**這個詞代表小數點 (或二進位點) 不會移動。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-203">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="e8a6d-204">讓我們來看一下：</span><span class="sxs-lookup"><span data-stu-id="e8a6d-204">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="e8a6d-205">請注意該範圍小於 `double` 型別。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-205">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="e8a6d-206">透過嘗試下列程式碼，您可以看到 decimal (小數) 型別有較高的精確度：</span><span class="sxs-lookup"><span data-stu-id="e8a6d-206">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="e8a6d-207">數字上的 `M` 尾碼乃是指示常數應使用 `decimal` 型別。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-207">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="e8a6d-208">請注意，使用 decimal (小數) 型別的運算在小數點右邊會有更多的數字。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-208">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span> 

<span data-ttu-id="e8a6d-209">***挑戰***</span><span class="sxs-lookup"><span data-stu-id="e8a6d-209">***Challenge***</span></span>

<span data-ttu-id="e8a6d-210">您已經了解不同的數字型別，接著請撰寫程式碼，以計算半徑 2.50 英吋的圓形面積。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-210">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 inches.</span></span> <span data-ttu-id="e8a6d-211">提醒您圓形面積是 PI 乘以半徑的平方。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-211">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="e8a6d-212">提示： C# 包含 PI 常數<xref:System.Math.PI?displayProperty=nameWithType>可讓您針對該值。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-212">One hint: C# contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span> 

<span data-ttu-id="e8a6d-213">您可以檢查您的答案，由[查看在 GitHub 上的 完成後的範例程式碼](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)</span><span class="sxs-lookup"><span data-stu-id="e8a6d-213">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="e8a6d-214">如果您想要，嘗試其他的公式。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-214">Try some other formulas if you'd like.</span></span> 

<span data-ttu-id="e8a6d-215">您已經完成 「 數字在 C# 中 「 快速入門。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-215">You've completed the "Numbers in C#" quick start.</span></span> <span data-ttu-id="e8a6d-216">您可以繼續使用[分支和迴圈](branches-and-loops-local.md)開發環境中的快速入門。</span><span class="sxs-lookup"><span data-stu-id="e8a6d-216">You can continue with the [Branches and loops](branches-and-loops-local.md) quick start in your own development environment.</span></span>

<span data-ttu-id="e8a6d-217">您可以在下列主題中深入了解 C# 中的數字：</span><span class="sxs-lookup"><span data-stu-id="e8a6d-217">You can learn more about numbers in C# in the following topics:</span></span>

<span data-ttu-id="e8a6d-218">[整數類型表](../language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="e8a6d-218">[Integral Types Table](../language-reference/keywords/integral-types-table.md) </span></span>  
<span data-ttu-id="e8a6d-219">[浮點類型表](../language-reference/keywords/floating-point-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="e8a6d-219">[Floating-Point Types Table](../language-reference/keywords/floating-point-types-table.md) </span></span>  
<span data-ttu-id="e8a6d-220">[內建類型表](../language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="e8a6d-220">[Built-In Types Table](../language-reference/keywords/built-in-types-table.md) </span></span>  
<span data-ttu-id="e8a6d-221">[隱含數值轉換表](../language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="e8a6d-221">[Implicit Numeric Conversions Table](../language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
[<span data-ttu-id="e8a6d-222">明確數值轉換表</span><span class="sxs-lookup"><span data-stu-id="e8a6d-222">Explicit Numeric Conversions Table</span></span>](../language-reference/keywords/explicit-numeric-conversions-table.md)

