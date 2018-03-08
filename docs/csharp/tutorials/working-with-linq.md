---
title: "處理 LINQ"
description: "本教學課程會教導您如何使用 LINQ 產生序列、撰寫用於 LINQ 查詢的方法，並區分立即和延遲評估。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/28/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: 3f0fcfebf37d9e6dad52c69111cc5e374ae27183
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/01/2018
---
# <a name="working-with-linq"></a><span data-ttu-id="3b710-104">處理 LINQ</span><span class="sxs-lookup"><span data-stu-id="3b710-104">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="3b710-105">簡介</span><span class="sxs-lookup"><span data-stu-id="3b710-105">Introduction</span></span>

<span data-ttu-id="3b710-106">本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。</span><span class="sxs-lookup"><span data-stu-id="3b710-106">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="3b710-107">您將了解：</span><span class="sxs-lookup"><span data-stu-id="3b710-107">You’ll learn:</span></span>

*   <span data-ttu-id="3b710-108">如何使用 LINQ 產生序列</span><span class="sxs-lookup"><span data-stu-id="3b710-108">How to generate sequences with LINQ</span></span>
*   <span data-ttu-id="3b710-109">如何撰寫可輕鬆用於 LINQ 查詢的方法。</span><span class="sxs-lookup"><span data-stu-id="3b710-109">How to write methods that can be easily used in LINQ queries.</span></span>
*   <span data-ttu-id="3b710-110">如何區分立即和延遲評估。</span><span class="sxs-lookup"><span data-stu-id="3b710-110">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="3b710-111">您將建置一個應用程式來學習這些技術，其中將示範任何魔術師都會的基礎技巧：[完美洗牌](https://en.wikipedia.org/wiki/Faro_shuffle) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="3b710-111">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="3b710-112">簡單地說，完美洗牌是將牌組確實分成兩半，然後互相交錯每一張紙牌來重建原始牌堆的技術。</span><span class="sxs-lookup"><span data-stu-id="3b710-112">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="3b710-113">魔術師使用這項技術的原因，是因為在每次洗牌後，每張紙牌都會在已知的位置，其順序會遵循重複性的模式。</span><span class="sxs-lookup"><span data-stu-id="3b710-113">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span> 

<span data-ttu-id="3b710-114">對我們而言，這是以較輕鬆的方式來了解對資料序列的操作。</span><span class="sxs-lookup"><span data-stu-id="3b710-114">For our purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="3b710-115">您將建置的應用程式會建構牌堆，然後執行一連串的洗牌，每次洗牌都會寫出序列。</span><span class="sxs-lookup"><span data-stu-id="3b710-115">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="3b710-116">您也會比較原始的順序與更新過的順序。</span><span class="sxs-lookup"><span data-stu-id="3b710-116">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="3b710-117">本教學課程有多個步驟。</span><span class="sxs-lookup"><span data-stu-id="3b710-117">This tutorial has multiple steps.</span></span> <span data-ttu-id="3b710-118">在每個步驟之後，您可以執行應用程式並查看進度。</span><span class="sxs-lookup"><span data-stu-id="3b710-118">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="3b710-119">您也可以在 dotnet/docs GitHub 存放庫中查看[完整範例](https://github.com/dotnet/docs/blob/master/samples/csharp/getting-started/console-linq)。</span><span class="sxs-lookup"><span data-stu-id="3b710-119">You can also see the [completed sample](https://github.com/dotnet/docs/blob/master/samples/csharp/getting-started/console-linq) in the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="3b710-120">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="3b710-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3b710-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="3b710-121">Prerequisites</span></span>

<span data-ttu-id="3b710-122">您必須設定電腦以執行 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="3b710-122">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="3b710-123">您可以在 [.NET Core](https://www.microsoft.com/net/core) \(英文\) 頁面上找到安裝指示。</span><span class="sxs-lookup"><span data-stu-id="3b710-123">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="3b710-124">您可以在 Windows、Ubuntu Linux、OS X 或是 Docker 容器中執行此應用程式。</span><span class="sxs-lookup"><span data-stu-id="3b710-124">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="3b710-125">您將必須安裝慣用的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="3b710-125">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="3b710-126">以下說明使用 [Visual Studio Code](https://code.visualstudio.com/) \(英文\)，這是開放原始碼的跨平台編輯器。</span><span class="sxs-lookup"><span data-stu-id="3b710-126">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="3b710-127">不過，您可以使用您熟悉的任何工具。</span><span class="sxs-lookup"><span data-stu-id="3b710-127">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="3b710-128">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="3b710-128">Create the Application</span></span>

<span data-ttu-id="3b710-129">第一個步驟是建立新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3b710-129">The first step is to create a new application.</span></span> <span data-ttu-id="3b710-130">請開啟命令提示字元，然後為您的應用程式建立新目錄。</span><span class="sxs-lookup"><span data-stu-id="3b710-130">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="3b710-131">使該目錄成為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="3b710-131">Make that the current directory.</span></span> <span data-ttu-id="3b710-132">在命令提示字元處輸入命令 `dotnet new console`。</span><span class="sxs-lookup"><span data-stu-id="3b710-132">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="3b710-133">這會建立基本 "Hello World" 應用程式的起始檔案。</span><span class="sxs-lookup"><span data-stu-id="3b710-133">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="3b710-134">如果您從未使用過 C#，[此教學課程](console-teleprompter.md)會說明 C# 程式的結構。</span><span class="sxs-lookup"><span data-stu-id="3b710-134">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="3b710-135">您可以閱讀該教學課程，然後再回到這裡以深入了解 LINQ。</span><span class="sxs-lookup"><span data-stu-id="3b710-135">You can read that and then return here to learn more about LINQ.</span></span> 

## <a name="creating-the-data-set"></a><span data-ttu-id="3b710-136">建立資料集</span><span class="sxs-lookup"><span data-stu-id="3b710-136">Creating the Data Set</span></span>

<span data-ttu-id="3b710-137">讓我們從建立一疊紙牌開始。</span><span class="sxs-lookup"><span data-stu-id="3b710-137">Let's start by creating a deck of cards.</span></span> <span data-ttu-id="3b710-138">您將會使用具有兩個來源 (一個針對四個花色，另一個針對十三個值) 的 LINQ 查詢來進行。</span><span class="sxs-lookup"><span data-stu-id="3b710-138">You'll do this using a LINQ query that has two sources (one for the four suits, one for the thirteen values).</span></span> <span data-ttu-id="3b710-139">您會將那些來源結合為 52 張紙牌的牌堆。</span><span class="sxs-lookup"><span data-stu-id="3b710-139">You'll combine those sources into a 52 card deck.</span></span> <span data-ttu-id="3b710-140">`foreach` 迴圈內的 `Console.WriteLine` 陳述式可顯示紙牌。</span><span class="sxs-lookup"><span data-stu-id="3b710-140">A `Console.WriteLine` statement inside a `foreach` loop displays the cards.</span></span>

<span data-ttu-id="3b710-141">以下便是該查詢：</span><span class="sxs-lookup"><span data-stu-id="3b710-141">Here's the query:</span></span>

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

<span data-ttu-id="3b710-142">多個 `from` 子句會產生 `SelectMany`，這會將第一個序列與第二個序列中的每個元素相互結合，來建立單一序列。</span><span class="sxs-lookup"><span data-stu-id="3b710-142">The multiple `from` clauses produce a `SelectMany`, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="3b710-143">其順序對我們來說很重要。</span><span class="sxs-lookup"><span data-stu-id="3b710-143">The order is important for our purposes.</span></span> <span data-ttu-id="3b710-144">第一個來源序列 (花色) 中的第一個元素，會與第二個序列 (值) 中的每個元素結合。</span><span class="sxs-lookup"><span data-stu-id="3b710-144">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Values).</span></span> <span data-ttu-id="3b710-145">這樣會產生第一個花色的十三張紙牌。</span><span class="sxs-lookup"><span data-stu-id="3b710-145">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="3b710-146">該程序會針對第一個序列 (花色) 中的每個元素重複執行。</span><span class="sxs-lookup"><span data-stu-id="3b710-146">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="3b710-147">最終結果是一疊先依花色，並接著依值排序的牌堆。</span><span class="sxs-lookup"><span data-stu-id="3b710-147">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="3b710-148">接下來，您需要建置 Suits() 和 Ranks() 方法。</span><span class="sxs-lookup"><span data-stu-id="3b710-148">Next, you'll need to build the Suits() and Ranks() methods.</span></span> <span data-ttu-id="3b710-149">我們從一組非常簡單的「迭代器方法」開始，該方法會產生為可列舉字串的序列：</span><span class="sxs-lookup"><span data-stu-id="3b710-149">Let's start with a really simple set of *iterator methods* that generate the sequence as an enumerable of strings:</span></span>

```csharp
static IEnumerable<string> Suits()
{
    yield return "clubs";
    yield return "diamonds";
    yield return "hearts";
    yield return "spades";
}

static IEnumerable<string> Ranks()
{
    yield return "two";
    yield return "three";
    yield return "four";
    yield return "five";
    yield return "six";
    yield return "seven";
    yield return "eight";
    yield return "nine";
    yield return "ten";
    yield return "jack";
    yield return "queen";
    yield return "king";
    yield return "ace";
}
```

<span data-ttu-id="3b710-150">這兩個方法都利用 `yield return` 語法，來在執行時產生序列。</span><span class="sxs-lookup"><span data-stu-id="3b710-150">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="3b710-151">編譯器會建置能實作 `IEnumerable<T>`，並會在要求它們時產生字串序列的物件。</span><span class="sxs-lookup"><span data-stu-id="3b710-151">The compiler builds an object that implements `IEnumerable<T>` and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="3b710-152">現在，請執行您目前所建置的範例。</span><span class="sxs-lookup"><span data-stu-id="3b710-152">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="3b710-153">它會顯示牌堆中全部 52 張紙牌。</span><span class="sxs-lookup"><span data-stu-id="3b710-153">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="3b710-154">您會發現以偵錯工具執行此範例，對於觀察 `Suits()` 和 `Values()` 方法的執行方式非常有用。</span><span class="sxs-lookup"><span data-stu-id="3b710-154">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Values()` methods execute.</span></span> <span data-ttu-id="3b710-155">您可以清楚地看見每個序列中的每個字串都只會在需要時產生。</span><span class="sxs-lookup"><span data-stu-id="3b710-155">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![主控台視窗顯示寫出 52 張紙牌的應用程式](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="3b710-157">操作順序</span><span class="sxs-lookup"><span data-stu-id="3b710-157">Manipulating the Order</span></span>

<span data-ttu-id="3b710-158">接下來，我們將建置可執行洗牌的公用程式方法。</span><span class="sxs-lookup"><span data-stu-id="3b710-158">Next, let's build a utility method that can perform the shuffle.</span></span> <span data-ttu-id="3b710-159">第一個步驟是將牌堆一分為二。</span><span class="sxs-lookup"><span data-stu-id="3b710-159">The first step is to split the deck in two.</span></span> <span data-ttu-id="3b710-160">包含於 LINQ API 的`Take()` 和 `Skip()` 方法可以為我們提供該功能：</span><span class="sxs-lookup"><span data-stu-id="3b710-160">The `Take()` and `Skip()` methods that are part of the LINQ APIs provide that feature for us:</span></span>

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

<span data-ttu-id="3b710-161">標準程式庫中不存在洗牌方法，所以您必須自行撰寫。</span><span class="sxs-lookup"><span data-stu-id="3b710-161">The shuffle method doesn't exist in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="3b710-162">這個新方法會說明數個您會搭配 LINQ 型程式使用的技術，因此我們將逐步說明方法的每個部分。</span><span class="sxs-lookup"><span data-stu-id="3b710-162">This new method illustrates several techniques that you'll use with LINQ-based programs, so let's explain each part of the method in steps.</span></span>

<span data-ttu-id="3b710-163">方法的簽章會建立「擴充方法」：</span><span class="sxs-lookup"><span data-stu-id="3b710-163">The signature for the method creates an *extension method*:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="3b710-164">擴充方法是特殊用途的「靜態方法」。</span><span class="sxs-lookup"><span data-stu-id="3b710-164">An extension method is a special purpose *static method.*</span></span> <span data-ttu-id="3b710-165">您可以方法的第一個引數上看到加入的 `this` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="3b710-165">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="3b710-166">這表示您會將方法當作第一個引數之型別的成員方法來呼叫。</span><span class="sxs-lookup"><span data-stu-id="3b710-166">That means you call the method as though it were a member method of the type of the first argument.</span></span>

<span data-ttu-id="3b710-167">您只能在 `static` 類別中宣告擴充方法，現在讓我們為這項功能建立稱為 `extensions` 的新靜態類別。</span><span class="sxs-lookup"><span data-stu-id="3b710-167">Extension methods can be declared only inside `static` classes, so let's create a new static class called `extensions` for this functionality.</span></span> <span data-ttu-id="3b710-168">在繼續本教學課程的同時，您將會加入更多擴充方法，那些擴充方法都會放置在相同的類別中。</span><span class="sxs-lookup"><span data-stu-id="3b710-168">You'll add more extension methods as you continue this tutorial, and those will be placed in the same class.</span></span>

<span data-ttu-id="3b710-169">此方法宣告也遵循標準慣用語，其中輸入和輸出型別為 `IEnumerable<T>`。</span><span class="sxs-lookup"><span data-stu-id="3b710-169">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="3b710-170">該作法可使 LINQ 方法鏈結在一起，以執行更複雜的查詢。</span><span class="sxs-lookup"><span data-stu-id="3b710-170">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

```csharp
using System.Collections.Generic;

namespace LinqFaroShuffle
{
    public static class Extensions
    {
        public static IEnumerable<T> InterleaveSequenceWith<T>
            (this IEnumerable<T> first, IEnumerable<T> second)
        {
            // implementation coming.
        }
    }
}
```

<span data-ttu-id="3b710-171">您將會同時列舉兩個序列，對元素進行交錯，然後建立單一物件。</span><span class="sxs-lookup"><span data-stu-id="3b710-171">You will be enumerating both sequences at once, interleaving the elements, and creating one object.</span></span>  <span data-ttu-id="3b710-172">若要撰寫可搭配兩個序列使用的 LINQ 方法，您必須先了解 `IEnumerable` 的運作方式。</span><span class="sxs-lookup"><span data-stu-id="3b710-172">Writing a LINQ method that works with two sequences requires that you understand how `IEnumerable` works.</span></span>

<span data-ttu-id="3b710-173">`IEnumerable` 介面具有單一方法：`GetEnumerator()`。</span><span class="sxs-lookup"><span data-stu-id="3b710-173">The `IEnumerable` interface has one method: `GetEnumerator()`.</span></span> <span data-ttu-id="3b710-174">`GetEnumerator()` 傳回的物件具有可移動到下一個元素的方法，以及可擷取目前序列中元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="3b710-174">The object returned by `GetEnumerator()` has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="3b710-175">您將會使用那兩個成員來列舉集合並傳回元素。</span><span class="sxs-lookup"><span data-stu-id="3b710-175">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="3b710-176">此交錯方法將會是迭代器方法，因此您將使用上述的 `yield return` 語法，而不是建置集合並傳回集合。</span><span class="sxs-lookup"><span data-stu-id="3b710-176">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span> 

<span data-ttu-id="3b710-177">以下是該方法的實作：</span><span class="sxs-lookup"><span data-stu-id="3b710-177">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="3b710-178">現在您已經撰寫了此方法，請回到 `Main` 方法，然後對牌堆洗牌一次：</span><span class="sxs-lookup"><span data-stu-id="3b710-178">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

```csharp
public static void Main(string[] args)
{
    var startingDeck = from s in Suits()
                       from r in Ranks()
                       select new { Suit = s, Rank = r };

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }
        
    var top = startingDeck.Take(26);
    var bottom = startingDeck.Skip(26);
    var shuffle = top.InterleaveSequenceWith(bottom);

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }
}
```

## <a name="comparisons"></a><span data-ttu-id="3b710-179">比較</span><span class="sxs-lookup"><span data-stu-id="3b710-179">Comparisons</span></span>

<span data-ttu-id="3b710-180">讓我們來看看需要洗牌多少次，才能將牌堆還原為原始的順序。</span><span class="sxs-lookup"><span data-stu-id="3b710-180">Let's see how many shuffles it takes to set the deck back to its original order.</span></span> <span data-ttu-id="3b710-181">您必須撰寫判斷兩個序列是否相等的方法。</span><span class="sxs-lookup"><span data-stu-id="3b710-181">You'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="3b710-182">在您完成該方法後，您需要將洗牌的程式碼放入迴圈中，然後看看牌堆何時會回到原始順序。</span><span class="sxs-lookup"><span data-stu-id="3b710-182">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="3b710-183">撰寫判斷兩個序列是否相等的方法應該很單純。</span><span class="sxs-lookup"><span data-stu-id="3b710-183">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="3b710-184">它的架構與您先前撰寫的洗牌方法類似。</span><span class="sxs-lookup"><span data-stu-id="3b710-184">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="3b710-185">只是這次不使用 yield 傳回每個元素，而是比較各序列的相符元素。</span><span class="sxs-lookup"><span data-stu-id="3b710-185">Only this time, instead of yield returning each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="3b710-186">當整個序列都已列舉後，如果每個元素都相符，則序列便為相同：</span><span class="sxs-lookup"><span data-stu-id="3b710-186">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="3b710-187">這裡示範第二個 LINQ 慣用語：終端方法。</span><span class="sxs-lookup"><span data-stu-id="3b710-187">This shows a second Linq idiom: terminal methods.</span></span> <span data-ttu-id="3b710-188">它們會將序列 (在此範例中為兩個序列) 當作輸入，並傳回單一純量值。</span><span class="sxs-lookup"><span data-stu-id="3b710-188">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="3b710-189">當使用這些方法時，它們一律會是查詢的最終方法。</span><span class="sxs-lookup"><span data-stu-id="3b710-189">These methods, when they are used, are always the final method of a query.</span></span> <span data-ttu-id="3b710-190">(也因此才名為終端方法)。</span><span class="sxs-lookup"><span data-stu-id="3b710-190">(Hence the name).</span></span> 

<span data-ttu-id="3b710-191">當您使用它來判斷牌堆何時回到原始順序時，便可以看到其作用。</span><span class="sxs-lookup"><span data-stu-id="3b710-191">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="3b710-192">將洗牌程式碼放到迴圈中，並透過套用 `SequenceEquals()` 方法，來在序列回到原始順序時停止迴圈。</span><span class="sxs-lookup"><span data-stu-id="3b710-192">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="3b710-193">您可以看到它在任何查詢中都一律是最終方法，因為它會傳回單一值而非序列：</span><span class="sxs-lookup"><span data-stu-id="3b710-193">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

```csharp
var times = 0;
var shuffle = startingDeck;

do
{
    shuffle = shuffle.Take(26).InterleaveSequenceWith(shuffle.Skip(26));

    foreach (var c in shuffle)
    {
        Console.WriteLine(c);
    }

    Console.WriteLine();
    times++;
} while (!startingDeck.SequenceEquals(shuffle));

Console.WriteLine(times);
```

<span data-ttu-id="3b710-194">執行範例，然後查看牌堆於每次洗牌時的重新排列方式，直到它在反覆運算 8 次後回到其原始設定。</span><span class="sxs-lookup"><span data-stu-id="3b710-194">Run the sample, and see how the deck rearranges on each shuffle, until it returns to its original configuration after 8 iterations.</span></span>

## <a name="optimizations"></a><span data-ttu-id="3b710-195">最佳化</span><span class="sxs-lookup"><span data-stu-id="3b710-195">Optimizations</span></span>

<span data-ttu-id="3b710-196">您目前建置的範例會執行「內部洗牌」，牌堆頂端和底部的紙牌，在每次執行時會保持不變。</span><span class="sxs-lookup"><span data-stu-id="3b710-196">The sample you've built so far executes an *in shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="3b710-197">讓我們來做個變化並執行「外部洗牌」，這會變更全部 52 張紙牌的位置。</span><span class="sxs-lookup"><span data-stu-id="3b710-197">Let's make one change, and run an *out shuffle*, where all 52 cards change position.</span></span> <span data-ttu-id="3b710-198">對於外部洗牌而言，您要交錯牌堆，讓下半部的第一張紙牌變為牌堆的第一張紙牌。</span><span class="sxs-lookup"><span data-stu-id="3b710-198">For an out shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="3b710-199">這表示上半部的最後一張紙牌會變為底部的排。</span><span class="sxs-lookup"><span data-stu-id="3b710-199">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="3b710-200">這只需要一行變更。</span><span class="sxs-lookup"><span data-stu-id="3b710-200">That's just a one line change.</span></span> <span data-ttu-id="3b710-201">更新洗牌的呼叫以變更牌堆上下半部的順序：</span><span class="sxs-lookup"><span data-stu-id="3b710-201">Update the call to shuffle to change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="3b710-202">再次執行程式，您將會看到需要反覆運算 52 次，才能使牌堆重新排列回原始順序。</span><span class="sxs-lookup"><span data-stu-id="3b710-202">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="3b710-203">隨著程式持續執行，您也會開始注意到一些效能嚴重降低的情況。</span><span class="sxs-lookup"><span data-stu-id="3b710-203">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="3b710-204">這有幾個原因。</span><span class="sxs-lookup"><span data-stu-id="3b710-204">There are a number of reasons for this.</span></span> <span data-ttu-id="3b710-205">讓我們處理其中一個主要原因：無法有效使用「延遲評估」。</span><span class="sxs-lookup"><span data-stu-id="3b710-205">Let's tackle one of the major causes: inefficient use of *lazy evaluation*.</span></span>

<span data-ttu-id="3b710-206">LINQ 查詢會以延遲的方式進行評估。</span><span class="sxs-lookup"><span data-stu-id="3b710-206">LINQ queries are evaluated lazily.</span></span> <span data-ttu-id="3b710-207">序列只會隨著要求元素產生。</span><span class="sxs-lookup"><span data-stu-id="3b710-207">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="3b710-208">通常，這是 LINQ 的主要優點。</span><span class="sxs-lookup"><span data-stu-id="3b710-208">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="3b710-209">不過，在使用如範例中的程式時，這會導致執行時間呈指數成長。</span><span class="sxs-lookup"><span data-stu-id="3b710-209">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="3b710-210">原始的牌堆是使用 LINQ 查詢產生。</span><span class="sxs-lookup"><span data-stu-id="3b710-210">The original deck was generated using a LINQ query.</span></span> <span data-ttu-id="3b710-211">每次洗牌都是透過對之前的牌堆執行三個 LINQ 查詢來產生。</span><span class="sxs-lookup"><span data-stu-id="3b710-211">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="3b710-212">這些都是以延遲方式執行。</span><span class="sxs-lookup"><span data-stu-id="3b710-212">All these are performed lazily.</span></span> <span data-ttu-id="3b710-213">這也表示每次要求序列時，它們都會再次執行。</span><span class="sxs-lookup"><span data-stu-id="3b710-213">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="3b710-214">當您達到第 52 次反覆運算時，您會非常多次地重複產生原始牌堆。</span><span class="sxs-lookup"><span data-stu-id="3b710-214">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="3b710-215">讓我們撰寫記錄以示範這個行為。</span><span class="sxs-lookup"><span data-stu-id="3b710-215">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="3b710-216">接著，您將會修正它。</span><span class="sxs-lookup"><span data-stu-id="3b710-216">Then, you'll fix it.</span></span>

<span data-ttu-id="3b710-217">以下是記錄方法，可以附加到任何查詢以標示查詢所執行的內容。</span><span class="sxs-lookup"><span data-stu-id="3b710-217">Here's a log method that can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="3b710-218">接下來，使用記錄訊息檢測每個查詢的定義：</span><span class="sxs-lookup"><span data-stu-id="3b710-218">Next, instrument the definition of each query with a log message:</span></span>

```csharp
public static void Main(string[] args)
{
    var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                        from r in Ranks().LogQuery("Rank Generation")
                        select new { Suit = s, Rank = r }).LogQuery("Starting Deck");

    foreach (var c in startingDeck)
    {
        Console.WriteLine(c);
    }
        
    Console.WriteLine();
    var times = 0;
    var shuffle = startingDeck;

    do
    {
        /*
        shuffle = shuffle.Take(26)
            .LogQuery("Top Half")
            .InterleaveSequenceWith(shuffle.Skip(26)
            .LogQuery("Bottom Half"))
            .LogQuery("Shuffle");
        */

        shuffle = shuffle.Skip(26)
            .LogQuery("Bottom Half")
            .InterleaveSequenceWith(shuffle.Take(26).LogQuery("Top Half"))
            .LogQuery("Shuffle");

        foreach (var c in shuffle)
        {
            Console.WriteLine(c);
        }

        times++;
        Console.WriteLine(times);
    } while (!startingDeck.SequenceEquals(shuffle));

    Console.WriteLine(times);
}
```

<span data-ttu-id="3b710-219">請注意，您不用在每次存取查詢時進行記錄。</span><span class="sxs-lookup"><span data-stu-id="3b710-219">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="3b710-220">您只需要在建立原始查詢時做出記錄。</span><span class="sxs-lookup"><span data-stu-id="3b710-220">You log only when you create the original query.</span></span> <span data-ttu-id="3b710-221">程式仍然會花費很長的時間執行，但現在您可以看到原因。</span><span class="sxs-lookup"><span data-stu-id="3b710-221">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="3b710-222">如果您在執行開啟記錄的外部洗牌期間失去耐心，請切換回內部洗牌。</span><span class="sxs-lookup"><span data-stu-id="3b710-222">If you run out of patience running the outer shuffle with logging turned on, switch back to the inner shuffle.</span></span> <span data-ttu-id="3b710-223">您仍然會看到延遲評估的效果。</span><span class="sxs-lookup"><span data-stu-id="3b710-223">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="3b710-224">在單次執行中，它會執行 2592 次查詢，其中包括所有值和花色的產生。</span><span class="sxs-lookup"><span data-stu-id="3b710-224">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="3b710-225">有一個簡單的方式可以更新此程式，以避免所有那些執行。</span><span class="sxs-lookup"><span data-stu-id="3b710-225">There is an easy way to update this program to avoid all those executions.</span></span> <span data-ttu-id="3b710-226">LINQ 方法 `ToArray()` 和 `ToList()` 可讓查詢執行，並分別將結果儲存於陣列或清單中。</span><span class="sxs-lookup"><span data-stu-id="3b710-226">There are LINQ methods `ToArray()` and `ToList()` that cause the query to run, and store the results in an array or a list, respectively.</span></span> <span data-ttu-id="3b710-227">您可以使用這些方法快取查詢的資料結果，而不需要再次執行來源查詢。</span><span class="sxs-lookup"><span data-stu-id="3b710-227">You use these methods to cache the data results of a query rather than execute the source query again.</span></span>  <span data-ttu-id="3b710-228">將對 `ToArray()` 的呼叫附加到產生牌堆的查詢，然後再次執行查詢：</span><span class="sxs-lookup"><span data-stu-id="3b710-228">Append the queries that generate the card decks with a call to `ToArray()` and run the query again:</span></span>

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="3b710-229">再次執行，內部洗牌的查詢次數會降至 30 次。</span><span class="sxs-lookup"><span data-stu-id="3b710-229">Run again, and the inner shuffle is down to 30 queries.</span></span> <span data-ttu-id="3b710-230">搭配外部洗牌再次執行，您將會看到類似的改善。</span><span class="sxs-lookup"><span data-stu-id="3b710-230">Run again with the outer shuffle and you'll see similar improvements.</span></span> <span data-ttu-id="3b710-231">(它現在只會執行 162 次查詢)。</span><span class="sxs-lookup"><span data-stu-id="3b710-231">(It now executes 162 queries).</span></span>

<span data-ttu-id="3b710-232">請勿因此案例，而認為所有的查詢都應該立即執行。</span><span class="sxs-lookup"><span data-stu-id="3b710-232">Don't misinterpret this example by thinking that all queries should run eagerly.</span></span> <span data-ttu-id="3b710-233">這個範例的設計，用意在於凸顯因延遲執行而造成效能問題的使用案例。</span><span class="sxs-lookup"><span data-stu-id="3b710-233">This example is designed to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="3b710-234">那是因為每個新的牌堆排列，都是從前一個排列所建立。</span><span class="sxs-lookup"><span data-stu-id="3b710-234">That's because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="3b710-235">使用延遲評估表示每個新的牌堆設定都是從原始牌堆建立，甚至會執行建置 `startingDeck` 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3b710-235">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="3b710-236">這會導致大量的額外工作。</span><span class="sxs-lookup"><span data-stu-id="3b710-236">That causes a large amount of extra work.</span></span> 

<span data-ttu-id="3b710-237">實際上，某些演算法會較適合使用立即評估，而其他演算法則較適合使用延遲評估。</span><span class="sxs-lookup"><span data-stu-id="3b710-237">In practice, some algorithms run much better using eager evaluation, and others run much better using lazy evaluation.</span></span> <span data-ttu-id="3b710-238">(一般而言，資料來源為獨立程序 (例如資料庫引擎) 的狀況，比較適合延遲評估。</span><span class="sxs-lookup"><span data-stu-id="3b710-238">(In general, lazy evaluation is a much better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="3b710-239">在那些情況下，延遲評估可讓更複雜的查詢，僅需針對資料庫程序執行單次反覆查詢)。LINQ 可使用延遲評估和立即評估。</span><span class="sxs-lookup"><span data-stu-id="3b710-239">In those cases, lazy evaluation enables more complex queries to execute only one round trip to the database process.) LINQ enables both lazy and eager evaluation.</span></span> <span data-ttu-id="3b710-240">請評量，然後挑選最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="3b710-240">Measure, and pick the best choice.</span></span>

## <a name="preparing-for-new-features"></a><span data-ttu-id="3b710-241">準備使用新功能</span><span class="sxs-lookup"><span data-stu-id="3b710-241">Preparing for New Features</span></span>

<span data-ttu-id="3b710-242">您針對此範例所撰寫的程式碼，是建立能完成工作之簡單原型的範例。</span><span class="sxs-lookup"><span data-stu-id="3b710-242">The code you've written for this sample is an example of creating a simple prototype that does the job.</span></span> <span data-ttu-id="3b710-243">這是探索問題範圍的絕佳方法，而對許多功能來說，它可能是最好的永久解決方案。</span><span class="sxs-lookup"><span data-stu-id="3b710-243">This is a great way to explore a problem space, and for many features, it may be the best permanent solution.</span></span> <span data-ttu-id="3b710-244">您對紙牌利用了「匿名型別」，而每張紙牌都會以字串表示。</span><span class="sxs-lookup"><span data-stu-id="3b710-244">You've leveraged *anonymous types* for the cards, and each card is represented by strings.</span></span>

<span data-ttu-id="3b710-245">「匿名型別」具有許多生產力優點。</span><span class="sxs-lookup"><span data-stu-id="3b710-245">*Anonymous Types* have many productivity advantages.</span></span> <span data-ttu-id="3b710-246">您不需要自行定義代表存放區的類別。</span><span class="sxs-lookup"><span data-stu-id="3b710-246">You don't need to define a class yourself to represent the storage.</span></span> <span data-ttu-id="3b710-247">編譯器會為您產生類別。</span><span class="sxs-lookup"><span data-stu-id="3b710-247">The compiler generates the type for you.</span></span> <span data-ttu-id="3b710-248">編譯器產生的類別會利用簡單資料物件的許多最佳做法。</span><span class="sxs-lookup"><span data-stu-id="3b710-248">The compiler generated type utilizes many of the best practices for simple data objects.</span></span> <span data-ttu-id="3b710-249">它是「不可變的」，這表示它在建構之後，其屬性皆不可變更。</span><span class="sxs-lookup"><span data-stu-id="3b710-249">It's *immutable*, meaning that none of its properties can be changed after it has been constructed.</span></span> <span data-ttu-id="3b710-250">匿名型別位於組件內部，因此不會被視為該組件公用 API 的一部分。</span><span class="sxs-lookup"><span data-stu-id="3b710-250">Anonymous types are internal to an assembly, so they aren't seen as part of the public API for that assembly.</span></span> <span data-ttu-id="3b710-251">匿名型別也包含 `ToString()` 方法的覆寫，其中會傳回每個值的格式化字串。</span><span class="sxs-lookup"><span data-stu-id="3b710-251">Anonymous types also contain an override of the `ToString()` method that returns a formatted string with each of the values.</span></span>

<span data-ttu-id="3b710-252">匿名型別也有缺點。</span><span class="sxs-lookup"><span data-stu-id="3b710-252">Anonymous types also have disadvantages.</span></span> <span data-ttu-id="3b710-253">它們不具有可存取的名稱，所以您無法使用它們做為傳回值或引數。</span><span class="sxs-lookup"><span data-stu-id="3b710-253">They don't have accessible names, so you can't use them as return values or arguments.</span></span> <span data-ttu-id="3b710-254">您會注意到上述所有使用這些匿名型別的方法都是泛型方法。</span><span class="sxs-lookup"><span data-stu-id="3b710-254">You'll notice that any methods above that used these anonymous types are generic methods.</span></span> <span data-ttu-id="3b710-255">隨著應用程式加入更多功能，`ToString()` 的覆寫可能不是您所要的。</span><span class="sxs-lookup"><span data-stu-id="3b710-255">The override of `ToString()` may not be what you want as the application grows more features.</span></span> 

<span data-ttu-id="3b710-256">範例針對花色和每張紙牌的順位也使用字串。</span><span class="sxs-lookup"><span data-stu-id="3b710-256">The sample also uses strings for the suit and the rank of each card.</span></span> <span data-ttu-id="3b710-257">那相對較為模糊。</span><span class="sxs-lookup"><span data-stu-id="3b710-257">That's quite open ended.</span></span> <span data-ttu-id="3b710-258">C# 型別系統可透過對那些值運用 `enum` 型別，來協助我們打造更棒的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3b710-258">The C# type system can help us make better code, by leveraging `enum` types for those values.</span></span>

<span data-ttu-id="3b710-259">從花色開始。</span><span class="sxs-lookup"><span data-stu-id="3b710-259">Start with the suits.</span></span> <span data-ttu-id="3b710-260">這是使用 `enum` 的完美時機：</span><span class="sxs-lookup"><span data-stu-id="3b710-260">This is a perfect time to use an `enum`:</span></span>

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

<span data-ttu-id="3b710-261">`Suits()` 方法也會變更型別和實作：</span><span class="sxs-lookup"><span data-stu-id="3b710-261">The `Suits()` method also changes type and implementation:</span></span>

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

<span data-ttu-id="3b710-262">接下來，請對紙牌的順序執行相同變更：</span><span class="sxs-lookup"><span data-stu-id="3b710-262">Next, do the same change with the Rank of the cards:</span></span>

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

<span data-ttu-id="3b710-263">而產生它們的方法為：</span><span class="sxs-lookup"><span data-stu-id="3b710-263">And the method that generates them:</span></span>

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

<span data-ttu-id="3b710-264">最後，我們會建立一個型別來代表紙牌，而不依賴匿名型別。</span><span class="sxs-lookup"><span data-stu-id="3b710-264">As one final cleanup, let's make a type to represent the card, instead of relying on an anonymous type.</span></span> <span data-ttu-id="3b710-265">匿名型別很適合用於輕量的區域型別，但在此範例中，紙牌是其中一項主要概念。</span><span class="sxs-lookup"><span data-stu-id="3b710-265">Anonymous types are great for lightweight, local types, but in this example, the playing card is one of the main concepts.</span></span> <span data-ttu-id="3b710-266">它應該要是具象型別。</span><span class="sxs-lookup"><span data-stu-id="3b710-266">It should be a concrete type.</span></span>

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

<span data-ttu-id="3b710-267">此型別使用「自動實作的唯讀屬性」，該屬性是在建構函式中設定，而且無法修改。</span><span class="sxs-lookup"><span data-stu-id="3b710-267">This type uses *auto-implemented read-only properties* which are set in the constructor, and then cannot be modified.</span></span> <span data-ttu-id="3b710-268">它也會利用新的「字串內插補點」功能，來更輕鬆地對字串輸出進行格式化。</span><span class="sxs-lookup"><span data-stu-id="3b710-268">It also makes use of the new *string interpolation* feature that makes it easier to format string output.</span></span>

<span data-ttu-id="3b710-269">更新產生起始牌堆的查詢，以使用新的型別：</span><span class="sxs-lookup"><span data-stu-id="3b710-269">Update the query that generates the starting deck to use the new type:</span></span>

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

<span data-ttu-id="3b710-270">編譯並再次執行。</span><span class="sxs-lookup"><span data-stu-id="3b710-270">Compile and run again.</span></span> <span data-ttu-id="3b710-271">輸出會變的更簡潔，程式碼也會更清楚，而且更容易擴充。</span><span class="sxs-lookup"><span data-stu-id="3b710-271">The output is a little cleaner, and the code is a bit more clear and can be extended more easily.</span></span>

## <a name="conclusion"></a><span data-ttu-id="3b710-272">結論</span><span class="sxs-lookup"><span data-stu-id="3b710-272">Conclusion</span></span>

<span data-ttu-id="3b710-273">這個範例為您示範了一些用於 LINQ 的方法，以及如何建立可輕鬆搭配啟用 LINQ 之程式碼來使用的方法。</span><span class="sxs-lookup"><span data-stu-id="3b710-273">This sample showed you some of the methods used in LINQ, how to create your own methods that will be easily used with LINQ enabled code.</span></span> <span data-ttu-id="3b710-274">它也示範延遲評估和立即評估的差異，以及兩者對效能可能會產生的效果。</span><span class="sxs-lookup"><span data-stu-id="3b710-274">It also showed you the differences between lazy and eager evaluation, and the effect that decision can have on performance.</span></span>

<span data-ttu-id="3b710-275">您學到了一點魔術師的技巧。</span><span class="sxs-lookup"><span data-stu-id="3b710-275">You learned a bit about one magician's technique.</span></span> <span data-ttu-id="3b710-276">魔術師之所以使用完美洗牌，是因為他們可以控制每張牌在牌堆中的動向。</span><span class="sxs-lookup"><span data-stu-id="3b710-276">Magicians use the faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="3b710-277">在某些戲法中，魔術師讓觀眾把紙牌放在牌堆最上方，並在洗牌數次之後，仍然能知道該紙牌的位置。</span><span class="sxs-lookup"><span data-stu-id="3b710-277">In some tricks, the magician has an audience member place a card on top of the deck, and shuffles a few times, knowing where that card goes.</span></span> <span data-ttu-id="3b710-278">其他的魔術則需要以特定方式設置牌堆。</span><span class="sxs-lookup"><span data-stu-id="3b710-278">Other illusions require the deck set a certain way.</span></span> <span data-ttu-id="3b710-279">魔術師會在表演戲法之前會先將牌堆設置好。</span><span class="sxs-lookup"><span data-stu-id="3b710-279">A magician will set the deck prior to performing the trick.</span></span> <span data-ttu-id="3b710-280">然後她會使用內部洗牌將牌堆洗 5 次。</span><span class="sxs-lookup"><span data-stu-id="3b710-280">Then she will shuffle the deck 5 times using an inner shuffle.</span></span> <span data-ttu-id="3b710-281">在舞台上，她可以展示看起來像是隨機順序的牌堆，然後將紙牌洗 3 次，這個手法正好會將牌堆洗為她所想要的設置。</span><span class="sxs-lookup"><span data-stu-id="3b710-281">On stage, she can show what looks like a random deck, shuffle it 3 more times, and have the deck set exactly how she wants.</span></span>
