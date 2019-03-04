---
title: 泛型型別 (泛型) 概觀
description: 了解泛型如何作為程式碼範本，讓您定義型別安全資料結構，而不需要認可至實際資料類型。
author: kuhlenh
ms.author: wiwagn
ms.date: 10/09/2018
ms.openlocfilehash: 991e3800e1302843db0dc1c57ed3a7e4becd298e
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835287"
---
# <a name="generic-types-overview"></a><span data-ttu-id="bdc82-103">泛型型別概觀</span><span class="sxs-lookup"><span data-stu-id="bdc82-103">Generic types overview</span></span>

<span data-ttu-id="bdc82-104">開發人員經常會在 .NET 中使用泛型，不論是隱含使用或明確使用。</span><span class="sxs-lookup"><span data-stu-id="bdc82-104">Developers use generics all the time in .NET, whether implicitly or explicitly.</span></span> <span data-ttu-id="bdc82-105">當您在 .NET 中使用 LINQ 時，您是否曾注意到您正在使用 <xref:System.Collections.Generic.IEnumerable%601>？</span><span class="sxs-lookup"><span data-stu-id="bdc82-105">When you use LINQ in .NET, did you ever notice that you're working with <xref:System.Collections.Generic.IEnumerable%601>?</span></span> <span data-ttu-id="bdc82-106">如果您曾經看過使用 Entity Framework 與資料庫通訊的「一般存放庫」線上範例，您是否注意到大部分的方法會傳回 IQueryable<T>？</span><span class="sxs-lookup"><span data-stu-id="bdc82-106">Or if you ever saw an online sample of a "generic repository" for talking to databases using Entity Framework, did you see that most methods return IQueryable<T>?</span></span> <span data-ttu-id="bdc82-107">您可能想知道這些範例中的 **T** 為何，以及它出現在這裡的原因。</span><span class="sxs-lookup"><span data-stu-id="bdc82-107">You may have wondered what the **T** is in these examples and why it's in there.</span></span>

<span data-ttu-id="bdc82-108">在 .NET Framework 2.0 中首次引進，**泛型**基本上是「程式碼範本」，可讓開發人員定義[型別安全](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100))資料結構，而不需要認可至實際資料類型。</span><span class="sxs-lookup"><span data-stu-id="bdc82-108">First introduced in the .NET Framework 2.0, **generics** are essentially a "code template" that allows developers to define [type-safe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/hbzz1a9a(v=vs.100)) data structures without committing to an actual data type.</span></span> <span data-ttu-id="bdc82-109">例如，<xref:System.Collections.Generic.List%601> 是可宣告的[泛型集合](xref:System.Collections.Generic)，並可搭配任何型別使用：`List<int>`、`List<string>`、`List<Person>` 等等。</span><span class="sxs-lookup"><span data-stu-id="bdc82-109">For example, <xref:System.Collections.Generic.List%601> is a [generic collection](xref:System.Collections.Generic) that can be declared and used with any type, such as `List<int>`, `List<string>`, or `List<Person>`.</span></span>

<span data-ttu-id="bdc82-110">若要了解為什麼泛型十分實用，讓我們看看加入泛型前後的特定類別：<xref:System.Collections.ArrayList>。</span><span class="sxs-lookup"><span data-stu-id="bdc82-110">To understand why generics are useful, let's take a look at a specific class before and after adding generics: <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="bdc82-111">在 .NET Framework 1.0 中，`ArrayList` 元素的型別為 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="bdc82-111">In .NET Framework 1.0, the `ArrayList` elements were of type <xref:System.Object>.</span></span> <span data-ttu-id="bdc82-112">這表示任何加入的元素都會以無訊息模式轉換成 `Object`。</span><span class="sxs-lookup"><span data-stu-id="bdc82-112">This meant that any element added was silently converted into an `Object`.</span></span> <span data-ttu-id="bdc82-113">從清單中讀取元素時會發生同樣的情況。</span><span class="sxs-lookup"><span data-stu-id="bdc82-113">The same would happen when reading the elements from the list.</span></span> <span data-ttu-id="bdc82-114">此程序稱為 [Boxing 和 Unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md)，它會影響效能。</span><span class="sxs-lookup"><span data-stu-id="bdc82-114">This process is known as [boxing and unboxing](../csharp/programming-guide/types/boxing-and-unboxing.md), and it impacts performance.</span></span> <span data-ttu-id="bdc82-115">但更重要的是，在編譯時無法判斷清單中的資料型別。</span><span class="sxs-lookup"><span data-stu-id="bdc82-115">More than that, however, there's no way to determine the type of data in the list at compile time.</span></span> <span data-ttu-id="bdc82-116">因此很容易產生一些易損壞的程式碼。</span><span class="sxs-lookup"><span data-stu-id="bdc82-116">This makes for some fragile code.</span></span> <span data-ttu-id="bdc82-117">泛型可以透過定義每個清單執行個體將包含之資料的型別解決這個問題。</span><span class="sxs-lookup"><span data-stu-id="bdc82-117">Generics solve this problem by defining the type of data each instance of list will contain.</span></span> <span data-ttu-id="bdc82-118">例如，您只能將整數加入 `List<int>`，以及只能將 Persons 加入 `List<Person>`。</span><span class="sxs-lookup"><span data-stu-id="bdc82-118">For example, you can only add integers to `List<int>` and only add Persons to `List<Person>`.</span></span>

<span data-ttu-id="bdc82-119">泛型也可用於執行階段。</span><span class="sxs-lookup"><span data-stu-id="bdc82-119">Generics are also available at runtime.</span></span> <span data-ttu-id="bdc82-120">這表示執行階段知道您要使用的資料結構類型，因此可更有效率地將它儲存在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="bdc82-120">This means the runtime knows what type of data structure you're using and can store it in memory more efficiently.</span></span>

<span data-ttu-id="bdc82-121">下列範例是一個小程式，說明如何有效率地得知執行階段的資料結構類型：</span><span class="sxs-lookup"><span data-stu-id="bdc82-121">The following example is a small program that illustrates the efficiency of knowing the data structure type at runtime:</span></span>

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

<span data-ttu-id="bdc82-122">此程式會產生類似下列內容的輸出：</span><span class="sxs-lookup"><span data-stu-id="bdc82-122">This program produces output similar to the following:</span></span>

```console
Generic Sort: System.Collections.Generic.List`1[System.Int32]
 Time taken: 0.0034ms
Non-Generic Sort: System.Collections.ArrayList
 Time taken: 0.2592ms
```

<span data-ttu-id="bdc82-123">您在此首先可以注意到，泛型清單的排序速度比非泛型清單的排序速度明顯更快。</span><span class="sxs-lookup"><span data-stu-id="bdc82-123">The first thing you can notice here is that sorting the generic list is significantly faster than sorting the non-generic list.</span></span> <span data-ttu-id="bdc82-124">您也可能注意到，泛型清單的類型是獨特的 ([System.Int32])，而非泛型清單的類型則是一般化。</span><span class="sxs-lookup"><span data-stu-id="bdc82-124">You might also notice that the type for the generic list is distinct ([System.Int32]), whereas the type for the non-generic list is generalized.</span></span> <span data-ttu-id="bdc82-125">因為執行階段知道泛型 `List<int>` 的類型是 <xref:System.Int32>，所以它可以將清單元素儲存為記憶體中的基礎整數陣列，但非泛型 `ArrayList` 則必須將每個清單元素轉換成物件。</span><span class="sxs-lookup"><span data-stu-id="bdc82-125">Because the runtime knows the generic `List<int>` is of type <xref:System.Int32>, it can store the list elements in an underlying integer array in memory while the non-generic `ArrayList` has to cast each list element to an object.</span></span> <span data-ttu-id="bdc82-126">如此範例所示，額外的轉換需要時間，因此會使清單排序速度變慢。</span><span class="sxs-lookup"><span data-stu-id="bdc82-126">As this example shows, the extra casts take up time and slow down the list sort.</span></span>

<span data-ttu-id="bdc82-127">執行階段知道您的泛型型別的另一個優點是改進偵錯體驗。</span><span class="sxs-lookup"><span data-stu-id="bdc82-127">An additional advantage of the runtime knowing the type of your generic is a better debugging experience.</span></span> <span data-ttu-id="bdc82-128">當您偵錯 C# 中的泛型時，您知道資料結構中的每個元素是何種型別。</span><span class="sxs-lookup"><span data-stu-id="bdc82-128">When you're debugging a generic in C#, you know what type each element is in your data structure.</span></span> <span data-ttu-id="bdc82-129">如果沒有泛型，您就無法得知每個項目是何種類型。</span><span class="sxs-lookup"><span data-stu-id="bdc82-129">Without generics, you would have no idea what type each element was.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdc82-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bdc82-130">See also</span></span>

- [<span data-ttu-id="bdc82-131">C# 程式設計手冊 - 泛型</span><span class="sxs-lookup"><span data-stu-id="bdc82-131">C# Programming Guide - Generics</span></span>](../../docs/csharp/programming-guide/generics/index.md)
