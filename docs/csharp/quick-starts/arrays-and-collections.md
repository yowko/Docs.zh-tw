---
title: 集合教學課程 - C# 本機快速入門
description: 在此教學課程中探索 List 集合來了解 C#。
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 51e8ce47165cd4ce22a72ed78138b36d15a97156
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362911"
---
# <a name="c-quickstart-collections"></a><span data-ttu-id="b0c50-103">C# 快速入門：集合</span><span class="sxs-lookup"><span data-stu-id="b0c50-103">C# Quickstart: Collections</span></span>

<span data-ttu-id="b0c50-104">本快速入門提供 C# 語言的簡介，以及 <xref:System.Collections.Generic.List%601> 類別的基本概念。</span><span class="sxs-lookup"><span data-stu-id="b0c50-104">This quickstart provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="b0c50-105">本快速入門需要您具備可用於開發的電腦。</span><span class="sxs-lookup"><span data-stu-id="b0c50-105">This quickstart expects you to have a machine you can use for development.</span></span> <span data-ttu-id="b0c50-106">.NET 主題[只要 10 分鐘立即上手](https://www.microsoft.com/net/core) \(英文\) 中有關於在 Mac、PC 或 Linux 上設定本機開發環境的指示。</span><span class="sxs-lookup"><span data-stu-id="b0c50-106">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="b0c50-107">您可以在[本機快速入門簡介](local-environment.md)中快速檢視將會用到的命令，並取得可提供詳細資料的連結。</span><span class="sxs-lookup"><span data-stu-id="b0c50-107">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="b0c50-108">基本的清單範例</span><span class="sxs-lookup"><span data-stu-id="b0c50-108">A basic list example</span></span>

<span data-ttu-id="b0c50-109">建立名為 **list-quickstart** 的目錄。</span><span class="sxs-lookup"><span data-stu-id="b0c50-109">Create a directory named **list-quickstart**.</span></span> <span data-ttu-id="b0c50-110">將該目錄設為目前的目錄，並執行 `dotnet new console`。</span><span class="sxs-lookup"><span data-stu-id="b0c50-110">Make that the current directory and run `dotnet new console`.</span></span>

> [!NOTE]
> <span data-ttu-id="b0c50-111">如果您剛完成[只要 10 分鐘立即上手 .NET](https://www.microsoft.com/net) \(英文\)，則可以繼續使用剛才建立的 myApp 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b0c50-111">If you just completed [Get started with .NET in 10 minutes](https://www.microsoft.com/net), you can keep using the myApp application that you just created.</span></span>

<span data-ttu-id="b0c50-112">在您最愛的編輯器中開啟 **Program.cs**，並以下列內容取代現有的程式碼：</span><span class="sxs-lookup"><span data-stu-id="b0c50-112">Open **Program.cs** in your favorite editor, and replace the existing code with the following:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
{
    class Program
    {
        static void Main(string[] args)
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

<span data-ttu-id="b0c50-113">以您的名稱取代 `<name>`。</span><span class="sxs-lookup"><span data-stu-id="b0c50-113">Replace `<name>` with your name.</span></span> <span data-ttu-id="b0c50-114">儲存 **Program.cs**。</span><span class="sxs-lookup"><span data-stu-id="b0c50-114">Save **Program.cs**.</span></span> <span data-ttu-id="b0c50-115">在主控台視窗中輸入 `dotnet run` 來嘗試它。</span><span class="sxs-lookup"><span data-stu-id="b0c50-115">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="b0c50-116">您剛才已建立字串清單，在該清單中新增三個名稱，並以全部大寫的形式列印出那些名稱。</span><span class="sxs-lookup"><span data-stu-id="b0c50-116">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="b0c50-117">您會使用從先前的快速入門中學習到的概念，在清單中執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="b0c50-117">You're using concepts that you've learned in earlier quickstarts to loop through the list.</span></span>

<span data-ttu-id="b0c50-118">顯示名稱的程式碼會運用[字串內插補點](../language-reference/tokens/interpolated.md)功能。</span><span class="sxs-lookup"><span data-stu-id="b0c50-118">The code to display names makes use of the [string interpolation](../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="b0c50-119">當您在 `string` 的前方放置 `$` 時，您可以在字串宣告中內嵌 C# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b0c50-119">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="b0c50-120">實際的字串會以它所產生的值取代 C# 程式碼。</span><span class="sxs-lookup"><span data-stu-id="b0c50-120">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="b0c50-121">在此範例中，它會以每個 (轉換成大寫字母的) 名稱取代 `{name.ToUpper()}`，因為您呼叫了 <xref:System.String.ToUpper%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="b0c50-121">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="b0c50-122">讓我們繼續探索。</span><span class="sxs-lookup"><span data-stu-id="b0c50-122">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="b0c50-123">修改清單內容</span><span class="sxs-lookup"><span data-stu-id="b0c50-123">Modify list contents</span></span>

<span data-ttu-id="b0c50-124">您所建立的集合會使用 <xref:System.Collections.Generic.List%601> 類型。</span><span class="sxs-lookup"><span data-stu-id="b0c50-124">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="b0c50-125">此類型會儲存元素的序列。</span><span class="sxs-lookup"><span data-stu-id="b0c50-125">This type stores sequences of elements.</span></span> <span data-ttu-id="b0c50-126">您會在角括弧之間指定元素的類型。</span><span class="sxs-lookup"><span data-stu-id="b0c50-126">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="b0c50-127">此 <xref:System.Collections.Generic.List%601> 類型的其中一個重要層面，在於它可以擴張或縮小，使您可以新增或移除元素。</span><span class="sxs-lookup"><span data-stu-id="b0c50-127">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="b0c50-128">在 `Main` 方法中關閉 `}` 之前，新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b0c50-128">Add this code before the closing `}` in the `Main` method:</span></span>

```csharp
Console.WriteLine();
names.Add("Maria");
names.Add("Bill");
names.Remove("Ana");
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="b0c50-129">您已在清單末端新增兩個額外的名稱。</span><span class="sxs-lookup"><span data-stu-id="b0c50-129">You've added two more names to the end of the list.</span></span> <span data-ttu-id="b0c50-130">您也移除了一個名稱。</span><span class="sxs-lookup"><span data-stu-id="b0c50-130">You've also removed one as well.</span></span> <span data-ttu-id="b0c50-131">儲存檔案，並輸入 `dotnet run` 來嘗試它。</span><span class="sxs-lookup"><span data-stu-id="b0c50-131">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="b0c50-132"><xref:System.Collections.Generic.List%601> 也可讓您透過**索引**參考個別的項目。</span><span class="sxs-lookup"><span data-stu-id="b0c50-132">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="b0c50-133">您需將索引放在 `[` 和 `]` 語彙基元之間，位於清單名稱之後。</span><span class="sxs-lookup"><span data-stu-id="b0c50-133">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="b0c50-134">C# 使用 0 作為第一個索引。</span><span class="sxs-lookup"><span data-stu-id="b0c50-134">C# uses 0 for the first index.</span></span> <span data-ttu-id="b0c50-135">將下列程式碼新增至您剛才新增的程式碼下方，然後嘗試它：</span><span class="sxs-lookup"><span data-stu-id="b0c50-135">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="b0c50-136">您無法存取位於清單結尾之外的索引。</span><span class="sxs-lookup"><span data-stu-id="b0c50-136">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="b0c50-137">請記住，索引是從 0 開始，因此最大的有效索引數目為清單項目數目減去 1。</span><span class="sxs-lookup"><span data-stu-id="b0c50-137">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="b0c50-138">您可以使用 <xref:System.Collections.Generic.List%601.Count%2A> 屬性檢查清單的長度。</span><span class="sxs-lookup"><span data-stu-id="b0c50-138">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="b0c50-139">在 Main 方法的結尾，加入下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b0c50-139">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="b0c50-140">儲存檔案，然後再次輸入 `dotnet run` 以查看結果。</span><span class="sxs-lookup"><span data-stu-id="b0c50-140">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="b0c50-141">針對清單進行搜尋和排序</span><span class="sxs-lookup"><span data-stu-id="b0c50-141">Search and sort lists</span></span>

<span data-ttu-id="b0c50-142">我們的範例所使用的清單相對較小，但是您的應用程式可能經常會建立具有更多元素的清單，數量甚至會達數千個之多。</span><span class="sxs-lookup"><span data-stu-id="b0c50-142">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="b0c50-143">若要在這些較大的集合中尋找元素，您需要在清單中搜尋不同的項目。</span><span class="sxs-lookup"><span data-stu-id="b0c50-143">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="b0c50-144"><xref:System.Collections.Generic.List%601.IndexOf%2A> 方法會搜尋項目，並傳回該項目的索引。</span><span class="sxs-lookup"><span data-stu-id="b0c50-144">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="b0c50-145">將下列程式碼新增到 `Main` 方法的底部：</span><span class="sxs-lookup"><span data-stu-id="b0c50-145">Add this code to the bottom of your `Main` method:</span></span>

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");

}
```

<span data-ttu-id="b0c50-146">也可以對您清單中的項目進行排序。</span><span class="sxs-lookup"><span data-stu-id="b0c50-146">The items in your list can be sorted as well.</span></span> <span data-ttu-id="b0c50-147"><xref:System.Collections.Generic.List%601.Sort%2A> 方法會依項目的一般順序方式，對清單中的所有項目進行排序 (針對字串會依字母順序排列)。</span><span class="sxs-lookup"><span data-stu-id="b0c50-147">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="b0c50-148">將下列程式碼新增到 `Main` 方法的底部：</span><span class="sxs-lookup"><span data-stu-id="b0c50-148">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="b0c50-149">儲存檔案並輸入 `dotnet run` 以嘗試此最新版本。</span><span class="sxs-lookup"><span data-stu-id="b0c50-149">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="b0c50-150">在開始下一節之前，讓我們將目前的程式碼移到另一個個別的方法。</span><span class="sxs-lookup"><span data-stu-id="b0c50-150">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="b0c50-151">這可讓您更輕鬆地開始處理新的範例。</span><span class="sxs-lookup"><span data-stu-id="b0c50-151">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="b0c50-152">將 `Main` 方法重新命名為 `WorkingWithStrings`，然後撰寫會呼叫 `WorkingWithStrings` 的新 `Main` 方法。</span><span class="sxs-lookup"><span data-stu-id="b0c50-152">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="b0c50-153">當您完成時，您的程式碼看起來應該像這樣：</span><span class="sxs-lookup"><span data-stu-id="b0c50-153">When you have finished, your code should look like this:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
{
    class Program
    {
        static void Main(string[] args)
        {
            WorkingWithStrings();
        }

        public static void WorkingWithStrings()
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine();
            names.Add("Maria");
            names.Add("Bill");
            names.Remove("Ana");
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine($"My name is {names[0]}");
            Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");

            Console.WriteLine($"The list has {names.Count} people in it");

            var index = names.IndexOf("Felipe");
            Console.WriteLine($"The name {names[index]} is at index {index}");

            var notFound = names.IndexOf("Not Found");
            Console.WriteLine($"When an item is not found, IndexOf returns {notFound}");

            names.Sort();
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

## <a name="lists-of-other-types"></a><span data-ttu-id="b0c50-154">其他類型的清單</span><span class="sxs-lookup"><span data-stu-id="b0c50-154">Lists of other types</span></span>

<span data-ttu-id="b0c50-155">到目前為止，您都是使用清單中的 `string` 類型。</span><span class="sxs-lookup"><span data-stu-id="b0c50-155">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="b0c50-156">讓我們使用不同的類型建立 <xref:System.Collections.Generic.List%601>。</span><span class="sxs-lookup"><span data-stu-id="b0c50-156">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="b0c50-157">讓我們來建置一組數字。</span><span class="sxs-lookup"><span data-stu-id="b0c50-157">Let's build a set of numbers.</span></span>

<span data-ttu-id="b0c50-158">將下列內容新增到新 `Main` 方法的底部：</span><span class="sxs-lookup"><span data-stu-id="b0c50-158">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="b0c50-159">這將會建立整數清單，並將前兩個整數設定為 1 的值。</span><span class="sxs-lookup"><span data-stu-id="b0c50-159">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="b0c50-160">這是*費氏數列*的前兩個值。</span><span class="sxs-lookup"><span data-stu-id="b0c50-160">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="b0c50-161">這兩個值之後每個費式數列數字，都會是其前兩個數字的總和。</span><span class="sxs-lookup"><span data-stu-id="b0c50-161">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="b0c50-162">新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b0c50-162">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="b0c50-163">儲存檔案並輸入 `dotnet run` 來查看結果。</span><span class="sxs-lookup"><span data-stu-id="b0c50-163">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="b0c50-164">若要僅專注於本節的內容，您可以對呼叫 `WorkingWithStrings();` 的程式碼進行註解化。</span><span class="sxs-lookup"><span data-stu-id="b0c50-164">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="b0c50-165">請在該呼叫之前放置兩個 `/` 字元，例如：`// WorkingWithStrings();`。</span><span class="sxs-lookup"><span data-stu-id="b0c50-165">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="b0c50-166">挑戰</span><span class="sxs-lookup"><span data-stu-id="b0c50-166">Challenge</span></span>

<span data-ttu-id="b0c50-167">看看您是否可以結合運用來自此課程和先前課程的概念。</span><span class="sxs-lookup"><span data-stu-id="b0c50-167">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="b0c50-168">請依費式數列數字，擴展您到目前為止所建立的內容。</span><span class="sxs-lookup"><span data-stu-id="b0c50-168">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="b0c50-169">請嘗試將程式碼撰寫成可產生該數列的前 20 個數字。</span><span class="sxs-lookup"><span data-stu-id="b0c50-169">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="b0c50-170">(小提示：第 20 個費式數列數字為 6765)。</span><span class="sxs-lookup"><span data-stu-id="b0c50-170">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="b0c50-171">完成挑戰</span><span class="sxs-lookup"><span data-stu-id="b0c50-171">Complete challenge</span></span>

<span data-ttu-id="b0c50-172">您可以[在 GitHub 上查看完成的範例程式碼](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23) \(英文\) 來取得範例解決方案</span><span class="sxs-lookup"><span data-stu-id="b0c50-172">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23)</span></span>

<span data-ttu-id="b0c50-173">在迴圈每次反覆運算時，您都必須取清單中的最後兩個整數，將它們加總，並將該值新增至清單。</span><span class="sxs-lookup"><span data-stu-id="b0c50-173">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="b0c50-174">迴圈會持續重複，直到將 20 個項目新增至清單為止。</span><span class="sxs-lookup"><span data-stu-id="b0c50-174">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="b0c50-175">恭喜，您已完成清單的快速入門。</span><span class="sxs-lookup"><span data-stu-id="b0c50-175">Congratulations, you've completed the list quickstart.</span></span> <span data-ttu-id="b0c50-176">您可以在自己的開發環境中，繼續完成[類別簡介](introduction-to-classes.md)快速入門中的內容。</span><span class="sxs-lookup"><span data-stu-id="b0c50-176">You can continue with the [Introduction to classes](introduction-to-classes.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="b0c50-177">您可以在關於[集合](../../standard/collections/index.md)的 [.NET 指南](../../standard/index.md)主題中，深入了解 `List` 類型的使用方式。</span><span class="sxs-lookup"><span data-stu-id="b0c50-177">You can learn more about working with the `List` type in the [.NET Guide](../../standard/index.md) topic on [collections](../../standard/collections/index.md).</span></span> <span data-ttu-id="b0c50-178">您也能學習到許多其他的集合類型。</span><span class="sxs-lookup"><span data-stu-id="b0c50-178">You'll also learn about many other collection types.</span></span>