---
title: "泛型型別 (泛型) 概觀"
description: "了解泛型如何作為程式碼範本，讓您定義型別安全資料結構，而不需要認可至實際資料類型。"
keywords: .NET, .NET Core
author: kuhlenh
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: a315b111-8e48-446c-ab19-acb6405894a7
ms.translationtype: HT
ms.sourcegitcommit: 75642ff3beb4462faa9068db76c89f3cb5f75ab8
ms.openlocfilehash: 08b8de2fe17a0032a1c1180667f39b1d6ce0feb6
ms.contentlocale: zh-tw
ms.lasthandoff: 08/21/2017

---

# <a name="generic-types-generics-overview"></a><span data-ttu-id="59e7b-104">泛型型別 (泛型) 概觀</span><span class="sxs-lookup"><span data-stu-id="59e7b-104">Generic Types (Generics) Overview</span></span>

<span data-ttu-id="59e7b-105">我們經常會在 C# 中使用泛型，不論是隱含使用或明確使用。</span><span class="sxs-lookup"><span data-stu-id="59e7b-105">We use generics all the time in C#, whether implicitly or explicitly.</span></span> <span data-ttu-id="59e7b-106">當您在 C# 中使用 LINQ 時，您是否曾注意到您正在使用 IEnumerable<T>？</span><span class="sxs-lookup"><span data-stu-id="59e7b-106">When you use LINQ in C#, did you ever notice that you are working with IEnumerable<T>?</span></span> <span data-ttu-id="59e7b-107">如果您曾經看過使用 Entity Framework 與資料庫通訊的「一般存放庫」線上範例，您是否注意到大部分的方法會傳回 IQueryable<T>？</span><span class="sxs-lookup"><span data-stu-id="59e7b-107">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return IQueryable<T>?</span></span> <span data-ttu-id="59e7b-108">您可能想知道這些範例中的 **T** 為何，以及它出現在這裡的原因。</span><span class="sxs-lookup"><span data-stu-id="59e7b-108">You may have wondered what the **T** is in these examples and why is it in there?</span></span>

<span data-ttu-id="59e7b-109">泛型是在 .NET Framework 2.0 中第一次引入，需要變更 C# 語言和 Common Language Runtime (CLR)。</span><span class="sxs-lookup"><span data-stu-id="59e7b-109">First introduced to the .NET Framework 2.0, generics involved changes to both the C# language and the Common Language Runtime (CLR).</span></span> <span data-ttu-id="59e7b-110">**泛型**基本上是「程式碼範本」，可讓開發人員定義[型別安全](https://msdn.microsoft.com/library/hbzz1a9a.aspx)資料結構，而不需要認可至實際資料類型。</span><span class="sxs-lookup"><span data-stu-id="59e7b-110">**Generics** are essentially a "code template" that allows developers to define [type-safe](https://msdn.microsoft.com/library/hbzz1a9a.aspx) data structures without committing to an actual data type.</span></span> <span data-ttu-id="59e7b-111">例如，`List<T>` 是可宣告的[泛型集合](xref:System.Collections.Generic)，並可搭配任何類型使用：`List<int>`、`List<string>`、`List<Person>` 等等。</span><span class="sxs-lookup"><span data-stu-id="59e7b-111">For example, `List<T>` is a [Generic Collection](xref:System.Collections.Generic) that can be declared and used with any type: `List<int>`, `List<string>`, `List<Person>`, etc.</span></span>

<span data-ttu-id="59e7b-112">重點到底是什麼？</span><span class="sxs-lookup"><span data-stu-id="59e7b-112">So, what’s the point?</span></span> <span data-ttu-id="59e7b-113">為什麼泛型很有用？</span><span class="sxs-lookup"><span data-stu-id="59e7b-113">Why are generics useful?</span></span> <span data-ttu-id="59e7b-114">若要了解這一點，我們必須看看加入泛型前後的特定類別。</span><span class="sxs-lookup"><span data-stu-id="59e7b-114">In order to understand this, we need to take a look at a specific class before and after adding generics.</span></span> <span data-ttu-id="59e7b-115">以 `ArrayList` 為例。</span><span class="sxs-lookup"><span data-stu-id="59e7b-115">Let’s look at the `ArrayList`.</span></span> <span data-ttu-id="59e7b-116">在 C# 1.0 中，`ArrayList` 項目的類型是 `object`。</span><span class="sxs-lookup"><span data-stu-id="59e7b-116">In C# 1.0, the `ArrayList` elements were of type `object`.</span></span> <span data-ttu-id="59e7b-117">這表示任何加入的項目都會以無訊息模式轉換成 `object`；讀取清單中的項目時也會發生相同的情況 (此程序分別稱為 [Boxing](https://msdn.microsoft.com/library/yz2be5wk.aspx) 和 Unboxing)。</span><span class="sxs-lookup"><span data-stu-id="59e7b-117">This meant that any element that was added was silently converted into an `object`; same thing happens on reading the elements from the list (this process is known as [boxing](https://msdn.microsoft.com/library/yz2be5wk.aspx) and unboxing respectively).</span></span> <span data-ttu-id="59e7b-118">Boxing 和 Unboxing 會影響效能。</span><span class="sxs-lookup"><span data-stu-id="59e7b-118">Boxing and unboxing have an impact of performance.</span></span> <span data-ttu-id="59e7b-119">此外，您無法在編譯時期判斷清單中資料的實際類型。</span><span class="sxs-lookup"><span data-stu-id="59e7b-119">More than that, however, there is no way to tell at compile time what is the actual type of the data in the list.</span></span> <span data-ttu-id="59e7b-120">因此很容易產生一些易損壞的程式碼。</span><span class="sxs-lookup"><span data-stu-id="59e7b-120">This makes for some fragile code.</span></span> <span data-ttu-id="59e7b-121">泛型可以解決這個問題，它提供額外的資訊，也就是每個清單執行個體將包含之資料的類型。</span><span class="sxs-lookup"><span data-stu-id="59e7b-121">Generics solve this problem by providing additional information the type of data each instance of list will contain.</span></span> <span data-ttu-id="59e7b-122">簡單來說，您只能將整數加入 `List<int>`、只能將 Persons 加入 `List<Person>`，依此類推。</span><span class="sxs-lookup"><span data-stu-id="59e7b-122">Put simply, you can only add integers to `List<int>` and only add Persons to `List<Person>`, etc.</span></span>

<span data-ttu-id="59e7b-123">泛型也可用於執行階段，或加以**具體化**。</span><span class="sxs-lookup"><span data-stu-id="59e7b-123">Generics are also available at runtime, or **reified**.</span></span> <span data-ttu-id="59e7b-124">這表示執行階段知道您要使用的資料結構類型，因此可更有效率地將它儲存在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="59e7b-124">This means the runtime knows what type of data structure you are using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="59e7b-125">以下是一個小程式，說明如何有效率地得知執行階段的資料結構類型：</span><span class="sxs-lookup"><span data-stu-id="59e7b-125">Here is a small program that illustrates the efficiency of knowing the data structure type at runtime:</span></span>

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

<span data-ttu-id="59e7b-126">此程式會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="59e7b-126">This program yields the following output:</span></span>

```console
Generic Sort: System.Collections.Generic.List\`1[System.Int32] Time taken: 0.0789ms
Non-Generic Sort: System.Collections.ArrayList Time taken: 2.4324ms
```

<span data-ttu-id="59e7b-127">您在此首先會注意到，泛型清單的排序速度比非泛型清單的排序速度明顯更快。</span><span class="sxs-lookup"><span data-stu-id="59e7b-127">The first thing you notice here is that sorting the generic list is significantly faster than for the non-generic list.</span></span> <span data-ttu-id="59e7b-128">您也可能注意到，泛型清單的類型是獨特的 ([System.Int32])，而非泛型清單的類型則是一般化。</span><span class="sxs-lookup"><span data-stu-id="59e7b-128">You might also notice that the type for the generic list is distinct ([System.Int32]) whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="59e7b-129">因為執行階段知道泛型 `List<int>` 的類型是 int，所以它可以將清單項目儲存為記憶體中的基礎整數陣列，但非泛型 `ArrayList` 則必須將每個清單項目轉換成物件，再儲存為記憶體中的物件陣列。</span><span class="sxs-lookup"><span data-stu-id="59e7b-129">Because the runtime knows the generic `List<int>` is of type int, it can store the list elements in an underlying integer array in memory while the non-generic `ArrayList` has to cast each list element as an object as stored in an object array in memory.</span></span> <span data-ttu-id="59e7b-130">如此範例所示，額外的轉換需要時間，因此會使清單排序速度變慢。</span><span class="sxs-lookup"><span data-stu-id="59e7b-130">As shown through this example, the extra castings take up time and slow down the list sort.</span></span>

<span data-ttu-id="59e7b-131">有關執行階段知道您的泛型類型的最後一個用處是改進偵錯體驗。</span><span class="sxs-lookup"><span data-stu-id="59e7b-131">The last useful thing about the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="59e7b-132">當您偵錯 C# 中的泛型時，您知道資料結構中的每個項目是何種類型。</span><span class="sxs-lookup"><span data-stu-id="59e7b-132">When you are debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="59e7b-133">如果沒有泛型，您就無法得知每個項目是何種類型。</span><span class="sxs-lookup"><span data-stu-id="59e7b-133">Without generics, you would have no idea what type each element was.</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="59e7b-134">延伸閱讀和資源</span><span class="sxs-lookup"><span data-stu-id="59e7b-134">Further reading and resources</span></span>

*   [<span data-ttu-id="59e7b-135">C# 泛型簡介</span><span class="sxs-lookup"><span data-stu-id="59e7b-135">An Introduction to C# Generics</span></span>](https://msdn.microsoft.com/library/ms379564.aspx)
*   [<span data-ttu-id="59e7b-136">C# 程式設計手冊 - 泛型</span><span class="sxs-lookup"><span data-stu-id="59e7b-136">C# Programming Guide - Generics</span></span>](https://msdn.microsoft.com/library/512aeb7t.aspx)

