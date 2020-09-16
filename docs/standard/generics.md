---
title: 泛型型別 (泛型) 概觀
description: 了解泛型如何作為程式碼範本，讓您定義型別安全資料結構，而不需要認可至實際資料類型。
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 5f6e84e23b5bcdcb3dcd742823d83728fb43d195
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557940"
---
# <a name="generic-types-overview"></a><span data-ttu-id="4a187-103">泛型型別概觀</span><span class="sxs-lookup"><span data-stu-id="4a187-103">Generic types overview</span></span>

<span data-ttu-id="4a187-104">開發人員經常會在 .NET 中使用泛型，不論是隱含使用或明確使用。</span><span class="sxs-lookup"><span data-stu-id="4a187-104">Developers use generics all the time in .NET, whether implicitly or explicitly.</span></span> <span data-ttu-id="4a187-105">當您在 .NET 中使用 LINQ 時，您是否曾注意到您正在使用 <xref:System.Collections.Generic.IEnumerable%601>？</span><span class="sxs-lookup"><span data-stu-id="4a187-105">When you use LINQ in .NET, did you ever notice that you're working with <xref:System.Collections.Generic.IEnumerable%601>?</span></span> <span data-ttu-id="4a187-106">或者，如果您看到「一般存放庫」的線上範例使用 Entity Framework 來與資料庫交談，您是否看到大部分的方法都會傳回 `IQueryable<T>` ？</span><span class="sxs-lookup"><span data-stu-id="4a187-106">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return `IQueryable<T>`?</span></span> <span data-ttu-id="4a187-107">您可能想知道這些範例中的 **T** 為何，以及它出現在這裡的原因。</span><span class="sxs-lookup"><span data-stu-id="4a187-107">You may have wondered what the **T** is in these examples and why it's in there.</span></span>

<span data-ttu-id="4a187-108">在 .NET Framework 2.0 中首次引進，泛型基本上是「程式碼範本」，可讓開發人員定義[型別安全](/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100))資料結構，而不需要認可至實際資料類型。</span><span class="sxs-lookup"><span data-stu-id="4a187-108">First introduced in the .NET Framework 2.0, generics are essentially a "code template" that allows developers to define [type-safe](/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) data structures without committing to an actual data type.</span></span> <span data-ttu-id="4a187-109">例如， <xref:System.Collections.Generic.List%601> 是一個 [泛型集合](xref:System.Collections.Generic) ，可以使用任何型別（例如、或）來宣告和使用 `List<int>` `List<string>` `List<Person>` 。</span><span class="sxs-lookup"><span data-stu-id="4a187-109">For example, <xref:System.Collections.Generic.List%601> is a [generic collection](xref:System.Collections.Generic) that can be declared and used with any type, such as `List<int>`, `List<string>`, or `List<Person>`.</span></span>

<span data-ttu-id="4a187-110">若要了解為什麼泛型十分實用，讓我們看看加入泛型前後的特定類別：<xref:System.Collections.ArrayList>。</span><span class="sxs-lookup"><span data-stu-id="4a187-110">To understand why generics are useful, let's take a look at a specific class before and after adding generics: <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="4a187-111">在 .NET Framework 1.0 中，`ArrayList` 元素的型別為 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="4a187-111">In .NET Framework 1.0, the `ArrayList` elements were of type <xref:System.Object>.</span></span> <span data-ttu-id="4a187-112">加入至集合的任何元素都會以無訊息模式轉換成 `Object` 。</span><span class="sxs-lookup"><span data-stu-id="4a187-112">Any element added to the collection was silently converted into an `Object`.</span></span> <span data-ttu-id="4a187-113">從清單中讀取專案時，也會發生相同的情況。</span><span class="sxs-lookup"><span data-stu-id="4a187-113">The same would happen when reading elements from the list.</span></span> <span data-ttu-id="4a187-114">此程序稱為 [Boxing 和 Unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md)，它會影響效能。</span><span class="sxs-lookup"><span data-stu-id="4a187-114">This process is known as [boxing and unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), and it impacts performance.</span></span> <span data-ttu-id="4a187-115">不過除了效能之外，在編譯時期並沒有任何方法可以判斷清單中的資料類型，這會產生一些脆弱的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4a187-115">Aside from performance, however, there's no way to determine the type of data in the list at compile time, which makes for some fragile code.</span></span> <span data-ttu-id="4a187-116">泛型可以透過定義每個清單執行個體將包含之資料的型別解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="4a187-116">Generics solve this problem by defining the type of data each instance of list will contain.</span></span> <span data-ttu-id="4a187-117">例如，您只能將整數加入 `List<int>`，以及只能將 Persons 加入 `List<Person>`。</span><span class="sxs-lookup"><span data-stu-id="4a187-117">For example, you can only add integers to `List<int>` and only add Persons to `List<Person>`.</span></span>

<span data-ttu-id="4a187-118">泛型也可在執行時間使用。</span><span class="sxs-lookup"><span data-stu-id="4a187-118">Generics are also available at run time.</span></span> <span data-ttu-id="4a187-119">執行時間知道您所使用的資料結構類型，而且可以更有效率地將它儲存在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="4a187-119">The runtime knows what type of data structure you're using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="4a187-120">下列範例是一個小程式，說明在執行時間瞭解資料結構類型的效率：</span><span class="sxs-lookup"><span data-stu-id="4a187-120">The following example is a small program that illustrates the efficiency of knowing the data structure type at run time:</span></span>

```csharp
  using System;
  using System.Collections;
  using System.Collections.Generic;
  using System.Diagnostics;

  namespace GenericsExample {
    class Program {
      static void Main(string[] args) {
        //generic list
        List<int> ListGeneric = new List<int> { 5, 9, 1, 4 };
        //non-generic list
        ArrayList ListNonGeneric = new ArrayList { 5, 9, 1, 4 };
        // timer for generic list sort
        Stopwatch s = Stopwatch.StartNew();
        ListGeneric.Sort();
        s.Stop();
        Console.WriteLine($"Generic Sort: {ListGeneric}  \n Time taken: {s.Elapsed.TotalMilliseconds}ms");

        //timer for non-generic list sort
        Stopwatch s2 = Stopwatch.StartNew();
        ListNonGeneric.Sort();
        s2.Stop();
        Console.WriteLine($"Non-Generic Sort: {ListNonGeneric}  \n Time taken: {s2.Elapsed.TotalMilliseconds}ms");
        Console.ReadLine();
      }
    }
  }
```

<span data-ttu-id="4a187-121">此程式會產生類似下列內容的輸出：</span><span class="sxs-lookup"><span data-stu-id="4a187-121">This program produces output similar to the following:</span></span>

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

<span data-ttu-id="4a187-122">您在此首先可以注意到，泛型清單的排序速度比非泛型清單的排序速度明顯更快。</span><span class="sxs-lookup"><span data-stu-id="4a187-122">The first thing you can notice here is that sorting the generic list is significantly faster than sorting the non-generic list.</span></span> <span data-ttu-id="4a187-123">您也可能注意到，泛型清單的類型是獨特的 ([System.Int32])，而非泛型清單的類型則是一般化。</span><span class="sxs-lookup"><span data-stu-id="4a187-123">You might also notice that the type for the generic list is distinct ([System.Int32]), whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="4a187-124">因為執行時間知道泛型 `List<int>` 是型別 <xref:System.Int32> ，所以它可以將清單專案儲存在記憶體中的基礎整數陣列，而非泛型 `ArrayList` 必須將每個清單專案轉換成物件。</span><span class="sxs-lookup"><span data-stu-id="4a187-124">Because the runtime knows the generic `List<int>` is of type <xref:System.Int32>, it can store the list elements in an underlying integer array in memory, while the non-generic `ArrayList` has to cast each list element to an object.</span></span> <span data-ttu-id="4a187-125">如此範例所示，額外的轉換需要時間，因此會使清單排序速度變慢。</span><span class="sxs-lookup"><span data-stu-id="4a187-125">As this example shows, the extra casts take up time and slow down the list sort.</span></span>

<span data-ttu-id="4a187-126">執行階段知道您的泛型型別的另一個優點是改進偵錯體驗。</span><span class="sxs-lookup"><span data-stu-id="4a187-126">An additional advantage of the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="4a187-127">當您偵錯 C# 中的泛型時，您知道資料結構中的每個元素是何種型別。</span><span class="sxs-lookup"><span data-stu-id="4a187-127">When you're debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="4a187-128">如果沒有泛型，您就無法得知每個項目是何種類型。</span><span class="sxs-lookup"><span data-stu-id="4a187-128">Without generics, you would have no idea what type each element was.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a187-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a187-129">See also</span></span>

- [<span data-ttu-id="4a187-130">C# 程式設計手冊 - 泛型</span><span class="sxs-lookup"><span data-stu-id="4a187-130">C# Programming Guide - Generics</span></span>](../csharp/programming-guide/generics/index.md)
