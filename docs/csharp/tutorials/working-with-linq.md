---
title: 處理 LINQ
description: 本教學課程會教導您如何使用 LINQ 產生序列、撰寫用於 LINQ 查詢的方法，並區分立即和延遲評估。
ms.date: 03/28/2017
ms.assetid: 0db12548-82cb-4903-ac88-13103d70aa77
ms.openlocfilehash: e5f9baab13cddfb9e294de1e1a6ce967ccbe0813
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2018
---
# <a name="working-with-linq"></a><span data-ttu-id="40c89-103">處理 LINQ</span><span class="sxs-lookup"><span data-stu-id="40c89-103">Working with LINQ</span></span>

## <a name="introduction"></a><span data-ttu-id="40c89-104">簡介</span><span class="sxs-lookup"><span data-stu-id="40c89-104">Introduction</span></span>

<span data-ttu-id="40c89-105">本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。</span><span class="sxs-lookup"><span data-stu-id="40c89-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="40c89-106">您將了解：</span><span class="sxs-lookup"><span data-stu-id="40c89-106">You’ll learn:</span></span>

*   <span data-ttu-id="40c89-107">如何使用 LINQ 產生序列</span><span class="sxs-lookup"><span data-stu-id="40c89-107">How to generate sequences with LINQ</span></span>
*   <span data-ttu-id="40c89-108">如何撰寫可輕鬆用於 LINQ 查詢的方法。</span><span class="sxs-lookup"><span data-stu-id="40c89-108">How to write methods that can be easily used in LINQ queries.</span></span>
*   <span data-ttu-id="40c89-109">如何區分立即和延遲評估。</span><span class="sxs-lookup"><span data-stu-id="40c89-109">How to distinguish between eager and lazy evaluation.</span></span>

<span data-ttu-id="40c89-110">您將建置一個應用程式來學習這些技術，其中將示範任何魔術師都會的基礎技巧：[完美洗牌 (英文)](https://en.wikipedia.org/wiki/Faro_shuffle)。</span><span class="sxs-lookup"><span data-stu-id="40c89-110">You'll learn these techniques by building an application that demonstrates one of the basic skills of any magician: the [faro shuffle](https://en.wikipedia.org/wiki/Faro_shuffle).</span></span> <span data-ttu-id="40c89-111">簡單地說，完美洗牌是將牌組確實分成兩半，然後互相交錯每一張紙牌來重建原始牌堆的技術。</span><span class="sxs-lookup"><span data-stu-id="40c89-111">Briefly, a faro shuffle is a technique where you split a card deck exactly in half, then the shuffle interleaves each one card from each half to rebuild the original deck.</span></span>

<span data-ttu-id="40c89-112">魔術師使用這項技術的原因，是因為在每次洗牌後，每張紙牌都會在已知的位置，其順序會遵循重複性的模式。</span><span class="sxs-lookup"><span data-stu-id="40c89-112">Magicians use this technique because every card is in a known location after each shuffle, and the order is a repeating pattern.</span></span> 

<span data-ttu-id="40c89-113">對我們而言，這是以較輕鬆的方式來了解對資料序列的操作。</span><span class="sxs-lookup"><span data-stu-id="40c89-113">For our purposes, it is a light hearted look at manipulating sequences of data.</span></span> <span data-ttu-id="40c89-114">您將建置的應用程式會建構牌堆，然後執行一連串的洗牌，每次洗牌都會寫出序列。</span><span class="sxs-lookup"><span data-stu-id="40c89-114">The application you'll build will construct a card deck, and then perform a sequence of shuffles, writing the sequence out each time.</span></span> <span data-ttu-id="40c89-115">您也會比較原始的順序與更新過的順序。</span><span class="sxs-lookup"><span data-stu-id="40c89-115">You'll also compare the updated order to the original order.</span></span>

<span data-ttu-id="40c89-116">本教學課程有多個步驟。</span><span class="sxs-lookup"><span data-stu-id="40c89-116">This tutorial has multiple steps.</span></span> <span data-ttu-id="40c89-117">在每個步驟之後，您可以執行應用程式並查看進度。</span><span class="sxs-lookup"><span data-stu-id="40c89-117">After each step, you can run the application and see the progress.</span></span> <span data-ttu-id="40c89-118">您也可以在 dotnet/samples GitHub 存放機制中查看[完整範例](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq)。</span><span class="sxs-lookup"><span data-stu-id="40c89-118">You can also see the [completed sample](https://github.com/dotnet/samples/blob/master/csharp/getting-started/console-linq) in the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="40c89-119">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="40c89-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="40c89-120">必要條件</span><span class="sxs-lookup"><span data-stu-id="40c89-120">Prerequisites</span></span>

<span data-ttu-id="40c89-121">您必須設定電腦以執行 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="40c89-121">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="40c89-122">您可以在 [.NET Core (英文)](https://www.microsoft.com/net/core) 頁面找到安裝指示。</span><span class="sxs-lookup"><span data-stu-id="40c89-122">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="40c89-123">您可以在 Windows、Ubuntu Linux、OS X 或是 Docker 容器中執行此應用程式。</span><span class="sxs-lookup"><span data-stu-id="40c89-123">You can run this application on Windows, Ubuntu Linux, OS X or in a Docker container.</span></span> <span data-ttu-id="40c89-124">您將必須安裝慣用的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="40c89-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="40c89-125">以下說明使用 [Visual Studio Code (英文)](https://code.visualstudio.com/)，這是開放原始碼的跨平台編輯器。</span><span class="sxs-lookup"><span data-stu-id="40c89-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="40c89-126">不過，您可以使用您熟悉的任何工具。</span><span class="sxs-lookup"><span data-stu-id="40c89-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="40c89-127">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="40c89-127">Create the Application</span></span>

<span data-ttu-id="40c89-128">第一個步驟是建立新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="40c89-128">The first step is to create a new application.</span></span> <span data-ttu-id="40c89-129">請開啟命令提示字元，然後為您的應用程式建立新目錄。</span><span class="sxs-lookup"><span data-stu-id="40c89-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="40c89-130">使該目錄成為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="40c89-130">Make that the current directory.</span></span> <span data-ttu-id="40c89-131">在命令提示字元處輸入命令 `dotnet new console`。</span><span class="sxs-lookup"><span data-stu-id="40c89-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="40c89-132">這會建立基本 "Hello World" 應用程式的起始檔案。</span><span class="sxs-lookup"><span data-stu-id="40c89-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="40c89-133">如果您從未使用過 C#，[此教學課程](console-teleprompter.md)會說明 C# 程式的結構。</span><span class="sxs-lookup"><span data-stu-id="40c89-133">If you've never used C# before, [this tutorial](console-teleprompter.md) explains the structure of a C# program.</span></span> <span data-ttu-id="40c89-134">您可以閱讀該教學課程，然後再回到這裡以深入了解 LINQ。</span><span class="sxs-lookup"><span data-stu-id="40c89-134">You can read that and then return here to learn more about LINQ.</span></span> 

## <a name="creating-the-data-set"></a><span data-ttu-id="40c89-135">建立資料集</span><span class="sxs-lookup"><span data-stu-id="40c89-135">Creating the Data Set</span></span>

<span data-ttu-id="40c89-136">讓我們從建立一疊紙牌開始。</span><span class="sxs-lookup"><span data-stu-id="40c89-136">Let's start by creating a deck of cards.</span></span> <span data-ttu-id="40c89-137">您將會使用具有兩個來源 (一個針對四個花色，另一個針對十三個值) 的 LINQ 查詢來進行。</span><span class="sxs-lookup"><span data-stu-id="40c89-137">You'll do this using a LINQ query that has two sources (one for the four suits, one for the thirteen values).</span></span> <span data-ttu-id="40c89-138">您會將那些來源結合為 52 張紙牌的牌堆。</span><span class="sxs-lookup"><span data-stu-id="40c89-138">You'll combine those sources into a 52 card deck.</span></span> <span data-ttu-id="40c89-139">`foreach` 迴圈內的 `Console.WriteLine` 陳述式可顯示紙牌。</span><span class="sxs-lookup"><span data-stu-id="40c89-139">A `Console.WriteLine` statement inside a `foreach` loop displays the cards.</span></span>

<span data-ttu-id="40c89-140">以下便是該查詢：</span><span class="sxs-lookup"><span data-stu-id="40c89-140">Here's the query:</span></span>

```csharp
var startingDeck = from s in Suits()
                   from r in Ranks()
                   select new { Suit = s, Rank = r };

foreach (var c in startingDeck)
{
    Console.WriteLine(c);
}
```

<span data-ttu-id="40c89-141">多個 `from` 子句會產生 `SelectMany`，這會將第一個序列與第二個序列中的每個元素相互結合，來建立單一序列。</span><span class="sxs-lookup"><span data-stu-id="40c89-141">The multiple `from` clauses produce a `SelectMany`, which creates a single sequence from combining each element in the first sequence with each element in the second sequence.</span></span> <span data-ttu-id="40c89-142">其順序對我們來說很重要。</span><span class="sxs-lookup"><span data-stu-id="40c89-142">The order is important for our purposes.</span></span> <span data-ttu-id="40c89-143">第一個來源序列 (花色) 中的第一個元素，會與第二個序列 (值) 中的每個元素結合。</span><span class="sxs-lookup"><span data-stu-id="40c89-143">The first element in the first source sequence (Suits) is combined with every element in the second sequence (Values).</span></span> <span data-ttu-id="40c89-144">這樣會產生第一個花色的十三張紙牌。</span><span class="sxs-lookup"><span data-stu-id="40c89-144">This produces all thirteen cards of first suit.</span></span> <span data-ttu-id="40c89-145">該程序會針對第一個序列 (花色) 中的每個元素重複執行。</span><span class="sxs-lookup"><span data-stu-id="40c89-145">That process is repeated with each element in the first sequence (Suits).</span></span> <span data-ttu-id="40c89-146">最終結果是一疊先依花色，並接著依值排序的牌堆。</span><span class="sxs-lookup"><span data-stu-id="40c89-146">The end result is a deck of cards ordered by suits, followed by values.</span></span>

<span data-ttu-id="40c89-147">接下來，您需要建置 Suits() 和 Ranks() 方法。</span><span class="sxs-lookup"><span data-stu-id="40c89-147">Next, you'll need to build the Suits() and Ranks() methods.</span></span> <span data-ttu-id="40c89-148">我們從一組非常簡單的「迭代器方法」開始，該方法會產生為可列舉字串的序列：</span><span class="sxs-lookup"><span data-stu-id="40c89-148">Let's start with a really simple set of *iterator methods* that generate the sequence as an enumerable of strings:</span></span>

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

<span data-ttu-id="40c89-149">這兩個方法都利用 `yield return` 語法，來在執行時產生序列。</span><span class="sxs-lookup"><span data-stu-id="40c89-149">These two methods both utilize the `yield return` syntax to produce a sequence as they run.</span></span> <span data-ttu-id="40c89-150">編譯器會建置能實作 `IEnumerable<T>`，並會在要求它們時產生字串序列的物件。</span><span class="sxs-lookup"><span data-stu-id="40c89-150">The compiler builds an object that implements `IEnumerable<T>` and generates the sequence of strings as they are requested.</span></span>

<span data-ttu-id="40c89-151">現在，請執行您目前所建置的範例。</span><span class="sxs-lookup"><span data-stu-id="40c89-151">Go ahead and run the sample you've built at this point.</span></span> <span data-ttu-id="40c89-152">它會顯示牌堆中全部 52 張紙牌。</span><span class="sxs-lookup"><span data-stu-id="40c89-152">It will display all 52 cards in the deck.</span></span> <span data-ttu-id="40c89-153">您會發現以偵錯工具執行此範例，對於觀察 `Suits()` 和 `Values()` 方法的執行方式非常有用。</span><span class="sxs-lookup"><span data-stu-id="40c89-153">You may find it very helpful to run this sample under a debugger to observe how the `Suits()` and `Values()` methods execute.</span></span> <span data-ttu-id="40c89-154">您可以清楚地看見每個序列中的每個字串都只會在需要時產生。</span><span class="sxs-lookup"><span data-stu-id="40c89-154">You can clearly see that each string in each sequence is generated only as it is needed.</span></span>

![主控台視窗顯示寫出 52 張紙牌的應用程式](./media/working-with-linq/console.png)

## <a name="manipulating-the-order"></a><span data-ttu-id="40c89-156">操作順序</span><span class="sxs-lookup"><span data-stu-id="40c89-156">Manipulating the Order</span></span>

<span data-ttu-id="40c89-157">接下來，我們將建置可執行洗牌的公用程式方法。</span><span class="sxs-lookup"><span data-stu-id="40c89-157">Next, let's build a utility method that can perform the shuffle.</span></span> <span data-ttu-id="40c89-158">第一個步驟是將牌堆一分為二。</span><span class="sxs-lookup"><span data-stu-id="40c89-158">The first step is to split the deck in two.</span></span> <span data-ttu-id="40c89-159">包含於 LINQ API 的`Take()` 和 `Skip()` 方法可以為我們提供該功能：</span><span class="sxs-lookup"><span data-stu-id="40c89-159">The `Take()` and `Skip()` methods that are part of the LINQ APIs provide that feature for us:</span></span>

```csharp
var top = startingDeck.Take(26);
var bottom = startingDeck.Skip(26);
```

<span data-ttu-id="40c89-160">標準程式庫中不存在洗牌方法，所以您必須自行撰寫。</span><span class="sxs-lookup"><span data-stu-id="40c89-160">The shuffle method doesn't exist in the standard library, so you'll have to write your own.</span></span> <span data-ttu-id="40c89-161">這個新方法會說明數個您會搭配 LINQ 型程式使用的技術，因此我們將逐步說明方法的每個部分。</span><span class="sxs-lookup"><span data-stu-id="40c89-161">This new method illustrates several techniques that you'll use with LINQ-based programs, so let's explain each part of the method in steps.</span></span>

<span data-ttu-id="40c89-162">方法的簽章會建立「擴充方法」：</span><span class="sxs-lookup"><span data-stu-id="40c89-162">The signature for the method creates an *extension method*:</span></span>

```csharp
public static IEnumerable<T> InterleaveSequenceWith<T>
    (this IEnumerable<T> first, IEnumerable<T> second)
```

<span data-ttu-id="40c89-163">擴充方法是特殊用途的「靜態方法」。</span><span class="sxs-lookup"><span data-stu-id="40c89-163">An extension method is a special purpose *static method.*</span></span> <span data-ttu-id="40c89-164">您可以方法的第一個引數上看到加入的 `this` 修飾詞。</span><span class="sxs-lookup"><span data-stu-id="40c89-164">You can see the addition of the `this` modifier on the first argument to the method.</span></span> <span data-ttu-id="40c89-165">這表示您會將方法當作第一個引數之型別的成員方法來呼叫。</span><span class="sxs-lookup"><span data-stu-id="40c89-165">That means you call the method as though it were a member method of the type of the first argument.</span></span>

<span data-ttu-id="40c89-166">您只能在 `static` 類別中宣告擴充方法，現在讓我們為這項功能建立稱為 `extensions` 的新靜態類別。</span><span class="sxs-lookup"><span data-stu-id="40c89-166">Extension methods can be declared only inside `static` classes, so let's create a new static class called `extensions` for this functionality.</span></span> <span data-ttu-id="40c89-167">在繼續本教學課程的同時，您將會加入更多擴充方法，那些擴充方法都會放置在相同的類別中。</span><span class="sxs-lookup"><span data-stu-id="40c89-167">You'll add more extension methods as you continue this tutorial, and those will be placed in the same class.</span></span>

<span data-ttu-id="40c89-168">此方法宣告也遵循標準慣用語，其中輸入和輸出型別為 `IEnumerable<T>`。</span><span class="sxs-lookup"><span data-stu-id="40c89-168">This method declaration also follows a standard idiom where the input and output types are `IEnumerable<T>`.</span></span> <span data-ttu-id="40c89-169">該作法可使 LINQ 方法鏈結在一起，以執行更複雜的查詢。</span><span class="sxs-lookup"><span data-stu-id="40c89-169">That practice enables LINQ methods to be chained together to perform more complex queries.</span></span>

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

<span data-ttu-id="40c89-170">您將會同時列舉兩個序列，對元素進行交錯，然後建立單一物件。</span><span class="sxs-lookup"><span data-stu-id="40c89-170">You will be enumerating both sequences at once, interleaving the elements, and creating one object.</span></span>  <span data-ttu-id="40c89-171">若要撰寫可搭配兩個序列使用的 LINQ 方法，您必須先了解 `IEnumerable` 的運作方式。</span><span class="sxs-lookup"><span data-stu-id="40c89-171">Writing a LINQ method that works with two sequences requires that you understand how `IEnumerable` works.</span></span>

<span data-ttu-id="40c89-172">`IEnumerable` 介面具有單一方法：`GetEnumerator()`。</span><span class="sxs-lookup"><span data-stu-id="40c89-172">The `IEnumerable` interface has one method: `GetEnumerator()`.</span></span> <span data-ttu-id="40c89-173">`GetEnumerator()` 傳回的物件具有可移動到下一個元素的方法，以及可擷取目前序列中元素的屬性。</span><span class="sxs-lookup"><span data-stu-id="40c89-173">The object returned by `GetEnumerator()` has a method to move to the next element, and a property that retrieves the current element in the sequence.</span></span> <span data-ttu-id="40c89-174">您將會使用那兩個成員來列舉集合並傳回元素。</span><span class="sxs-lookup"><span data-stu-id="40c89-174">You will use those two members to enumerate the collection and return the elements.</span></span> <span data-ttu-id="40c89-175">此交錯方法將會是迭代器方法，因此您將使用上述的 `yield return` 語法，而不是建置集合並傳回集合。</span><span class="sxs-lookup"><span data-stu-id="40c89-175">This Interleave method will be an iterator method, so instead of building a collection and returning the collection, you'll use the `yield return` syntax shown above.</span></span> 

<span data-ttu-id="40c89-176">以下是該方法的實作：</span><span class="sxs-lookup"><span data-stu-id="40c89-176">Here's the implementation of that method:</span></span>

[!CODE-csharp[InterleaveSequenceWith](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet1)]

<span data-ttu-id="40c89-177">現在您已經撰寫了此方法，請回到 `Main` 方法，然後對牌堆洗牌一次：</span><span class="sxs-lookup"><span data-stu-id="40c89-177">Now that you've written this method, go back to the `Main` method and shuffle the deck once:</span></span>

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

## <a name="comparisons"></a><span data-ttu-id="40c89-178">比較</span><span class="sxs-lookup"><span data-stu-id="40c89-178">Comparisons</span></span>

<span data-ttu-id="40c89-179">讓我們來看看需要洗牌多少次，才能將牌堆還原為原始的順序。</span><span class="sxs-lookup"><span data-stu-id="40c89-179">Let's see how many shuffles it takes to set the deck back to its original order.</span></span> <span data-ttu-id="40c89-180">您必須撰寫判斷兩個序列是否相等的方法。</span><span class="sxs-lookup"><span data-stu-id="40c89-180">You'll need to write a method that determines if two sequences are equal.</span></span> <span data-ttu-id="40c89-181">在您完成該方法後，您需要將洗牌的程式碼放入迴圈中，然後看看牌堆何時會回到原始順序。</span><span class="sxs-lookup"><span data-stu-id="40c89-181">After you have that method, you'll need to place the code that shuffles the deck in a loop, and check to see when the deck is back in order.</span></span>

<span data-ttu-id="40c89-182">撰寫判斷兩個序列是否相等的方法應該很單純。</span><span class="sxs-lookup"><span data-stu-id="40c89-182">Writing a method to determine if the two sequences are equal should be straightforward.</span></span> <span data-ttu-id="40c89-183">它的架構與您先前撰寫的洗牌方法類似。</span><span class="sxs-lookup"><span data-stu-id="40c89-183">It's a similar structure to the method you wrote to shuffle the deck.</span></span> <span data-ttu-id="40c89-184">只是這次不使用 yield 傳回每個元素，而是比較各序列的相符元素。</span><span class="sxs-lookup"><span data-stu-id="40c89-184">Only this time, instead of yield returning each element, you'll compare the matching elements of each sequence.</span></span> <span data-ttu-id="40c89-185">當整個序列都已列舉後，如果每個元素都相符，則序列便為相同：</span><span class="sxs-lookup"><span data-stu-id="40c89-185">When the entire sequence has been enumerated, if every element matches, the sequences are the same:</span></span>

[!CODE-csharp[SequenceEquals](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet2)]

<span data-ttu-id="40c89-186">這裡示範第二個 LINQ 慣用語：終端方法。</span><span class="sxs-lookup"><span data-stu-id="40c89-186">This shows a second Linq idiom: terminal methods.</span></span> <span data-ttu-id="40c89-187">它們會將序列 (在此範例中為兩個序列) 當作輸入，並傳回單一純量值。</span><span class="sxs-lookup"><span data-stu-id="40c89-187">They take a sequence as input (or in this case, two sequences), and return a single scalar value.</span></span> <span data-ttu-id="40c89-188">當使用這些方法時，它們一律會是查詢的最終方法。</span><span class="sxs-lookup"><span data-stu-id="40c89-188">These methods, when they are used, are always the final method of a query.</span></span> <span data-ttu-id="40c89-189">(也因此才名為終端方法)。</span><span class="sxs-lookup"><span data-stu-id="40c89-189">(Hence the name).</span></span> 

<span data-ttu-id="40c89-190">當您使用它來判斷牌堆何時回到原始順序時，便可以看到其作用。</span><span class="sxs-lookup"><span data-stu-id="40c89-190">You can see this in action when you use it to determine when the deck is back in its original order.</span></span> <span data-ttu-id="40c89-191">將洗牌程式碼放到迴圈中，並透過套用 `SequenceEquals()` 方法，來在序列回到原始順序時停止迴圈。</span><span class="sxs-lookup"><span data-stu-id="40c89-191">Put the shuffle code inside a loop, and stop when the sequence is back in its original order by applying the `SequenceEquals()` method.</span></span> <span data-ttu-id="40c89-192">您可以看到它在任何查詢中都一律是最終方法，因為它會傳回單一值而非序列：</span><span class="sxs-lookup"><span data-stu-id="40c89-192">You can see it would always be the final method in any query, because it returns a single value instead of a sequence:</span></span>

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

<span data-ttu-id="40c89-193">執行範例，然後查看牌堆於每次洗牌時的重新排列方式，直到它在反覆運算 8 次後回到其原始設定。</span><span class="sxs-lookup"><span data-stu-id="40c89-193">Run the sample, and see how the deck rearranges on each shuffle, until it returns to its original configuration after 8 iterations.</span></span>

## <a name="optimizations"></a><span data-ttu-id="40c89-194">最佳化</span><span class="sxs-lookup"><span data-stu-id="40c89-194">Optimizations</span></span>

<span data-ttu-id="40c89-195">您目前建置的範例會執行「外部洗牌」，牌堆頂端和底部的紙牌，在每次執行時會保持不變。</span><span class="sxs-lookup"><span data-stu-id="40c89-195">The sample you've built so far executes an *out shuffle*, where the top and bottom cards stay the same on each run.</span></span> <span data-ttu-id="40c89-196">讓我們來做個變化並執行「內部洗牌」，這會變更全部 52 張紙牌的位置。</span><span class="sxs-lookup"><span data-stu-id="40c89-196">Let's make one change, and run an *in shuffle*, where all 52 cards change position.</span></span> <span data-ttu-id="40c89-197">對於內部洗牌而言，您要交錯牌堆，讓下半部的第一張紙牌變為牌堆的第一張紙牌。</span><span class="sxs-lookup"><span data-stu-id="40c89-197">For an in shuffle, you interleave the deck so that the first card in the bottom half becomes the first card in the deck.</span></span> <span data-ttu-id="40c89-198">這表示上半部的最後一張紙牌會變為底部的排。</span><span class="sxs-lookup"><span data-stu-id="40c89-198">That means the last card in the top half becomes the bottom card.</span></span> <span data-ttu-id="40c89-199">這只需要一行變更。</span><span class="sxs-lookup"><span data-stu-id="40c89-199">That's just a one line change.</span></span> <span data-ttu-id="40c89-200">更新洗牌的呼叫以變更牌堆上下半部的順序：</span><span class="sxs-lookup"><span data-stu-id="40c89-200">Update the call to shuffle to change the order of the top and bottom halves of the deck:</span></span>

```csharp
shuffle = shuffle.Skip(26).InterleaveSequenceWith(shuffle.Take(26));
```

<span data-ttu-id="40c89-201">再次執行程式，您將會看到需要反覆運算 52 次，才能使牌堆重新排列回原始順序。</span><span class="sxs-lookup"><span data-stu-id="40c89-201">Run the program again, and you'll see that it takes 52 iterations for the deck to reorder itself.</span></span> <span data-ttu-id="40c89-202">隨著程式持續執行，您也會開始注意到一些效能嚴重降低的情況。</span><span class="sxs-lookup"><span data-stu-id="40c89-202">You'll also start to notice some serious performance degradations as the program continues to run.</span></span>

<span data-ttu-id="40c89-203">這有幾個原因。</span><span class="sxs-lookup"><span data-stu-id="40c89-203">There are a number of reasons for this.</span></span> <span data-ttu-id="40c89-204">讓我們處理其中一個主要原因：無法有效使用「延遲評估」。</span><span class="sxs-lookup"><span data-stu-id="40c89-204">Let's tackle one of the major causes: inefficient use of *lazy evaluation*.</span></span>

<span data-ttu-id="40c89-205">LINQ 查詢會以延遲的方式進行評估。</span><span class="sxs-lookup"><span data-stu-id="40c89-205">LINQ queries are evaluated lazily.</span></span> <span data-ttu-id="40c89-206">序列只會隨著要求元素產生。</span><span class="sxs-lookup"><span data-stu-id="40c89-206">The sequences are generated only as the elements are requested.</span></span> <span data-ttu-id="40c89-207">通常，這是 LINQ 的主要優點。</span><span class="sxs-lookup"><span data-stu-id="40c89-207">Usually, that's a major benefit of LINQ.</span></span> <span data-ttu-id="40c89-208">不過，在使用如範例中的程式時，這會導致執行時間呈指數成長。</span><span class="sxs-lookup"><span data-stu-id="40c89-208">However, in a use such as this program, this causes exponential growth in execution time.</span></span>

<span data-ttu-id="40c89-209">原始的牌堆是使用 LINQ 查詢產生。</span><span class="sxs-lookup"><span data-stu-id="40c89-209">The original deck was generated using a LINQ query.</span></span> <span data-ttu-id="40c89-210">每次洗牌都是透過對之前的牌堆執行三個 LINQ 查詢來產生。</span><span class="sxs-lookup"><span data-stu-id="40c89-210">Each shuffle is generated by performing three LINQ queries on the previous deck.</span></span> <span data-ttu-id="40c89-211">這些都是以延遲方式執行。</span><span class="sxs-lookup"><span data-stu-id="40c89-211">All these are performed lazily.</span></span> <span data-ttu-id="40c89-212">這也表示每次要求序列時，它們都會再次執行。</span><span class="sxs-lookup"><span data-stu-id="40c89-212">That also means they are performed again each time the sequence is requested.</span></span> <span data-ttu-id="40c89-213">當您達到第 52 次反覆運算時，您會非常多次地重複產生原始牌堆。</span><span class="sxs-lookup"><span data-stu-id="40c89-213">By the time you get to the 52nd iteration, you're regenerating the original deck many, many times.</span></span> <span data-ttu-id="40c89-214">讓我們撰寫記錄以示範這個行為。</span><span class="sxs-lookup"><span data-stu-id="40c89-214">Let's write a log to demonstrate this behavior.</span></span> <span data-ttu-id="40c89-215">接著，您將會修正它。</span><span class="sxs-lookup"><span data-stu-id="40c89-215">Then, you'll fix it.</span></span>

<span data-ttu-id="40c89-216">以下是記錄方法，可以附加到任何查詢以標示查詢所執行的內容。</span><span class="sxs-lookup"><span data-stu-id="40c89-216">Here's a log method that can be appended to any query to mark that the query executed.</span></span>

[!CODE-csharp[LogQuery](../../../samples/csharp/getting-started/console-linq/extensions.cs?name=snippet3)]

<span data-ttu-id="40c89-217">接下來，使用記錄訊息檢測每個查詢的定義：</span><span class="sxs-lookup"><span data-stu-id="40c89-217">Next, instrument the definition of each query with a log message:</span></span>

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

<span data-ttu-id="40c89-218">請注意，您不用在每次存取查詢時進行記錄。</span><span class="sxs-lookup"><span data-stu-id="40c89-218">Notice that you don't log every time you access a query.</span></span> <span data-ttu-id="40c89-219">您只需要在建立原始查詢時做出記錄。</span><span class="sxs-lookup"><span data-stu-id="40c89-219">You log only when you create the original query.</span></span> <span data-ttu-id="40c89-220">程式仍然會花費很長的時間執行，但現在您可以看到原因。</span><span class="sxs-lookup"><span data-stu-id="40c89-220">The program still takes a long time to run, but now you can see why.</span></span> <span data-ttu-id="40c89-221">如果您在執行開啟記錄的內部洗牌期間失去耐心，請切換回外部洗牌。</span><span class="sxs-lookup"><span data-stu-id="40c89-221">If you run out of patience running the inner shuffle with logging turned on, switch back to the outer shuffle.</span></span> <span data-ttu-id="40c89-222">您仍然會看到延遲評估的效果。</span><span class="sxs-lookup"><span data-stu-id="40c89-222">You'll still see the lazy evaluation effects.</span></span> <span data-ttu-id="40c89-223">在單次執行中，它會執行 2592 次查詢，其中包括所有值和花色的產生。</span><span class="sxs-lookup"><span data-stu-id="40c89-223">In one run, it executes 2592 queries, including all the value and suit generation.</span></span>

<span data-ttu-id="40c89-224">有一個簡單的方式可以更新此程式，以避免所有那些執行。</span><span class="sxs-lookup"><span data-stu-id="40c89-224">There is an easy way to update this program to avoid all those executions.</span></span> <span data-ttu-id="40c89-225">LINQ 方法 `ToArray()` 和 `ToList()` 可讓查詢執行，並分別將結果儲存於陣列或清單中。</span><span class="sxs-lookup"><span data-stu-id="40c89-225">There are LINQ methods `ToArray()` and `ToList()` that cause the query to run, and store the results in an array or a list, respectively.</span></span> <span data-ttu-id="40c89-226">您可以使用這些方法快取查詢的資料結果，而不需要再次執行來源查詢。</span><span class="sxs-lookup"><span data-stu-id="40c89-226">You use these methods to cache the data results of a query rather than execute the source query again.</span></span>  <span data-ttu-id="40c89-227">將對 `ToArray()` 的呼叫附加到產生牌堆的查詢，然後再次執行查詢：</span><span class="sxs-lookup"><span data-stu-id="40c89-227">Append the queries that generate the card decks with a call to `ToArray()` and run the query again:</span></span>

[!CODE-csharp[Main](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet1)]

<span data-ttu-id="40c89-228">再次執行，外部洗牌的查詢次數會降至 30 次。</span><span class="sxs-lookup"><span data-stu-id="40c89-228">Run again, and the outer shuffle is down to 30 queries.</span></span> <span data-ttu-id="40c89-229">搭配內部洗牌再次執行，您將會看到類似的改善。</span><span class="sxs-lookup"><span data-stu-id="40c89-229">Run again with the inner shuffle and you'll see similar improvements.</span></span> <span data-ttu-id="40c89-230">(它現在只會執行 162 次查詢)。</span><span class="sxs-lookup"><span data-stu-id="40c89-230">(It now executes 162 queries).</span></span>

<span data-ttu-id="40c89-231">請勿因此案例，而認為所有的查詢都應該立即執行。</span><span class="sxs-lookup"><span data-stu-id="40c89-231">Don't misinterpret this example by thinking that all queries should run eagerly.</span></span> <span data-ttu-id="40c89-232">這個範例的設計，用意在於凸顯因延遲執行而造成效能問題的使用案例。</span><span class="sxs-lookup"><span data-stu-id="40c89-232">This example is designed to highlight the use cases where lazy evaluation can cause performance difficulties.</span></span> <span data-ttu-id="40c89-233">那是因為每個新的牌堆排列，都是從前一個排列所建立。</span><span class="sxs-lookup"><span data-stu-id="40c89-233">That's because each new arrangement of the deck of cards is built from the previous arrangement.</span></span> <span data-ttu-id="40c89-234">使用延遲評估表示每個新的牌堆設定都是從原始牌堆建立，甚至會執行建置 `startingDeck` 的程式碼。</span><span class="sxs-lookup"><span data-stu-id="40c89-234">Using lazy evaluation means each new deck configuration is built from the original deck, even executing the code that built the `startingDeck`.</span></span> <span data-ttu-id="40c89-235">這會導致大量的額外工作。</span><span class="sxs-lookup"><span data-stu-id="40c89-235">That causes a large amount of extra work.</span></span> 

<span data-ttu-id="40c89-236">實際上，某些演算法會較適合使用立即評估，而其他演算法則較適合使用延遲評估。</span><span class="sxs-lookup"><span data-stu-id="40c89-236">In practice, some algorithms run much better using eager evaluation, and others run much better using lazy evaluation.</span></span> <span data-ttu-id="40c89-237">(一般而言，資料來源為獨立程序 (例如資料庫引擎) 的狀況，比較適合延遲評估。</span><span class="sxs-lookup"><span data-stu-id="40c89-237">(In general, lazy evaluation is a much better choice when the data source is a separate process, like a database engine.</span></span> <span data-ttu-id="40c89-238">在那些情況下，延遲評估可讓更複雜的查詢，僅需針對資料庫程序執行單次反覆查詢)。LINQ 可使用延遲評估和立即評估。</span><span class="sxs-lookup"><span data-stu-id="40c89-238">In those cases, lazy evaluation enables more complex queries to execute only one round trip to the database process.) LINQ enables both lazy and eager evaluation.</span></span> <span data-ttu-id="40c89-239">請評量，然後挑選最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="40c89-239">Measure, and pick the best choice.</span></span>

## <a name="preparing-for-new-features"></a><span data-ttu-id="40c89-240">準備使用新功能</span><span class="sxs-lookup"><span data-stu-id="40c89-240">Preparing for New Features</span></span>

<span data-ttu-id="40c89-241">您針對此範例所撰寫的程式碼，是建立能完成工作之簡單原型的範例。</span><span class="sxs-lookup"><span data-stu-id="40c89-241">The code you've written for this sample is an example of creating a simple prototype that does the job.</span></span> <span data-ttu-id="40c89-242">這是探索問題範圍的絕佳方法，而對許多功能來說，它可能是最好的永久解決方案。</span><span class="sxs-lookup"><span data-stu-id="40c89-242">This is a great way to explore a problem space, and for many features, it may be the best permanent solution.</span></span> <span data-ttu-id="40c89-243">您對紙牌利用了「匿名型別」，而每張紙牌都會以字串表示。</span><span class="sxs-lookup"><span data-stu-id="40c89-243">You've leveraged *anonymous types* for the cards, and each card is represented by strings.</span></span>

<span data-ttu-id="40c89-244">「匿名型別」具有許多生產力優點。</span><span class="sxs-lookup"><span data-stu-id="40c89-244">*Anonymous Types* have many productivity advantages.</span></span> <span data-ttu-id="40c89-245">您不需要自行定義代表存放區的類別。</span><span class="sxs-lookup"><span data-stu-id="40c89-245">You don't need to define a class yourself to represent the storage.</span></span> <span data-ttu-id="40c89-246">編譯器會為您產生類別。</span><span class="sxs-lookup"><span data-stu-id="40c89-246">The compiler generates the type for you.</span></span> <span data-ttu-id="40c89-247">編譯器產生的類別會利用簡單資料物件的許多最佳做法。</span><span class="sxs-lookup"><span data-stu-id="40c89-247">The compiler generated type utilizes many of the best practices for simple data objects.</span></span> <span data-ttu-id="40c89-248">它是「不可變的」，這表示它在建構之後，其屬性皆不可變更。</span><span class="sxs-lookup"><span data-stu-id="40c89-248">It's *immutable*, meaning that none of its properties can be changed after it has been constructed.</span></span> <span data-ttu-id="40c89-249">匿名型別位於組件內部，因此不會被視為該組件公用 API 的一部分。</span><span class="sxs-lookup"><span data-stu-id="40c89-249">Anonymous types are internal to an assembly, so they aren't seen as part of the public API for that assembly.</span></span> <span data-ttu-id="40c89-250">匿名型別也包含 `ToString()` 方法的覆寫，其中會傳回每個值的格式化字串。</span><span class="sxs-lookup"><span data-stu-id="40c89-250">Anonymous types also contain an override of the `ToString()` method that returns a formatted string with each of the values.</span></span>

<span data-ttu-id="40c89-251">匿名型別也有缺點。</span><span class="sxs-lookup"><span data-stu-id="40c89-251">Anonymous types also have disadvantages.</span></span> <span data-ttu-id="40c89-252">它們不具有可存取的名稱，所以您無法使用它們做為傳回值或引數。</span><span class="sxs-lookup"><span data-stu-id="40c89-252">They don't have accessible names, so you can't use them as return values or arguments.</span></span> <span data-ttu-id="40c89-253">您會注意到上述所有使用這些匿名型別的方法都是泛型方法。</span><span class="sxs-lookup"><span data-stu-id="40c89-253">You'll notice that any methods above that used these anonymous types are generic methods.</span></span> <span data-ttu-id="40c89-254">隨著應用程式加入更多功能，`ToString()` 的覆寫可能不是您所要的。</span><span class="sxs-lookup"><span data-stu-id="40c89-254">The override of `ToString()` may not be what you want as the application grows more features.</span></span> 

<span data-ttu-id="40c89-255">範例針對花色和每張紙牌的順位也使用字串。</span><span class="sxs-lookup"><span data-stu-id="40c89-255">The sample also uses strings for the suit and the rank of each card.</span></span> <span data-ttu-id="40c89-256">那相對較為模糊。</span><span class="sxs-lookup"><span data-stu-id="40c89-256">That's quite open ended.</span></span> <span data-ttu-id="40c89-257">C# 型別系統可透過對那些值運用 `enum` 型別，來協助我們打造更棒的程式碼。</span><span class="sxs-lookup"><span data-stu-id="40c89-257">The C# type system can help us make better code, by leveraging `enum` types for those values.</span></span>

<span data-ttu-id="40c89-258">從花色開始。</span><span class="sxs-lookup"><span data-stu-id="40c89-258">Start with the suits.</span></span> <span data-ttu-id="40c89-259">這是使用 `enum` 的完美時機：</span><span class="sxs-lookup"><span data-stu-id="40c89-259">This is a perfect time to use an `enum`:</span></span>

[!CODE-csharp[Suit enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet2)]

<span data-ttu-id="40c89-260">`Suits()` 方法也會變更型別和實作：</span><span class="sxs-lookup"><span data-stu-id="40c89-260">The `Suits()` method also changes type and implementation:</span></span>

[!CODE-csharp[Suit IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet4)]

<span data-ttu-id="40c89-261">接下來，請對紙牌的順序執行相同變更：</span><span class="sxs-lookup"><span data-stu-id="40c89-261">Next, do the same change with the Rank of the cards:</span></span>

[!CODE-csharp[Rank enum](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet3)]

<span data-ttu-id="40c89-262">而產生它們的方法為：</span><span class="sxs-lookup"><span data-stu-id="40c89-262">And the method that generates them:</span></span>

[!CODE-csharp[Rank IEnumerable](../../../samples/csharp/getting-started/console-linq/Program.cs?name=snippet5)]

<span data-ttu-id="40c89-263">最後，我們會建立一個型別來代表紙牌，而不依賴匿名型別。</span><span class="sxs-lookup"><span data-stu-id="40c89-263">As one final cleanup, let's make a type to represent the card, instead of relying on an anonymous type.</span></span> <span data-ttu-id="40c89-264">匿名型別很適合用於輕量的區域型別，但在此範例中，紙牌是其中一項主要概念。</span><span class="sxs-lookup"><span data-stu-id="40c89-264">Anonymous types are great for lightweight, local types, but in this example, the playing card is one of the main concepts.</span></span> <span data-ttu-id="40c89-265">它應該要是具象型別。</span><span class="sxs-lookup"><span data-stu-id="40c89-265">It should be a concrete type.</span></span>

[!CODE-csharp[PlayingCard](../../../samples/csharp/getting-started/console-linq/playingcard.cs?name=snippet1)]

<span data-ttu-id="40c89-266">此型別使用「自動實作的唯讀屬性」，該屬性是在建構函式中設定，而且無法修改。</span><span class="sxs-lookup"><span data-stu-id="40c89-266">This type uses *auto-implemented read-only properties* which are set in the constructor, and then cannot be modified.</span></span> <span data-ttu-id="40c89-267">它也會利用[字串內插補點](../language-reference/tokens/interpolated.md)功能，來更輕鬆地對字串輸出進行格式化。</span><span class="sxs-lookup"><span data-stu-id="40c89-267">It also makes use of the [string interpolation](../language-reference/tokens/interpolated.md) feature that makes it easier to format string output.</span></span>

<span data-ttu-id="40c89-268">更新產生起始牌堆的查詢，以使用新的型別：</span><span class="sxs-lookup"><span data-stu-id="40c89-268">Update the query that generates the starting deck to use the new type:</span></span>

```csharp
var startingDeck = (from s in Suits().LogQuery("Suit Generation")
                    from r in Ranks().LogQuery("Value Generation")
                    select new PlayingCard(s, r))
                    .LogQuery("Starting Deck")
                    .ToArray();
```

<span data-ttu-id="40c89-269">編譯並再次執行。</span><span class="sxs-lookup"><span data-stu-id="40c89-269">Compile and run again.</span></span> <span data-ttu-id="40c89-270">輸出會變的更簡潔，程式碼也會更清楚，而且更容易擴充。</span><span class="sxs-lookup"><span data-stu-id="40c89-270">The output is a little cleaner, and the code is a bit more clear and can be extended more easily.</span></span>

## <a name="conclusion"></a><span data-ttu-id="40c89-271">結論</span><span class="sxs-lookup"><span data-stu-id="40c89-271">Conclusion</span></span>

<span data-ttu-id="40c89-272">這個範例為您示範了一些用於 LINQ 的方法，以及如何建立可輕鬆搭配啟用 LINQ 之程式碼來使用的方法。</span><span class="sxs-lookup"><span data-stu-id="40c89-272">This sample showed you some of the methods used in LINQ, how to create your own methods that will be easily used with LINQ enabled code.</span></span> <span data-ttu-id="40c89-273">它也示範延遲評估和立即評估的差異，以及兩者對效能可能會產生的效果。</span><span class="sxs-lookup"><span data-stu-id="40c89-273">It also showed you the differences between lazy and eager evaluation, and the effect that decision can have on performance.</span></span>

<span data-ttu-id="40c89-274">您學到了一點魔術師的技巧。</span><span class="sxs-lookup"><span data-stu-id="40c89-274">You learned a bit about one magician's technique.</span></span> <span data-ttu-id="40c89-275">魔術師之所以使用完美洗牌，是因為他們可以控制每張牌在牌堆中的動向。</span><span class="sxs-lookup"><span data-stu-id="40c89-275">Magicians use the faro shuffle because they can control where every card moves in the deck.</span></span> <span data-ttu-id="40c89-276">在某些戲法中，魔術師讓觀眾把紙牌放在牌堆最上方，並在洗牌數次之後，仍然能知道該紙牌的位置。</span><span class="sxs-lookup"><span data-stu-id="40c89-276">In some tricks, the magician has an audience member place a card on top of the deck, and shuffles a few times, knowing where that card goes.</span></span> <span data-ttu-id="40c89-277">其他的魔術則需要以特定方式設置牌堆。</span><span class="sxs-lookup"><span data-stu-id="40c89-277">Other illusions require the deck set a certain way.</span></span> <span data-ttu-id="40c89-278">魔術師會在表演戲法之前會先將牌堆設置好。</span><span class="sxs-lookup"><span data-stu-id="40c89-278">A magician will set the deck prior to performing the trick.</span></span> <span data-ttu-id="40c89-279">然後她會使用外部洗牌將牌堆洗 5 次。</span><span class="sxs-lookup"><span data-stu-id="40c89-279">Then she will shuffle the deck 5 times using an outer shuffle.</span></span> <span data-ttu-id="40c89-280">在舞台上，她可以展示看起來像是隨機順序的牌堆，然後將紙牌洗 3 次，這個手法正好會將牌堆洗為她所想要的設置。</span><span class="sxs-lookup"><span data-stu-id="40c89-280">On stage, she can show what looks like a random deck, shuffle it 3 more times, and have the deck set exactly how she wants.</span></span>
