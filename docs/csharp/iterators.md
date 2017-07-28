---
title: Iterator
description: Iterator
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 5cf36f45-f91a-4fca-a0b7-87f233e108e9
ms.translationtype: Human Translation
ms.sourcegitcommit: 890c058bd09893c2adb185e1d8107246eef2e20a
ms.openlocfilehash: 7fea22be3b98c3218d173e5d80f1f22ef7ecf7e2
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---

# <a name="iterators"></a>Iterator

您撰寫的幾乎所有程式或多或少都需要逐一查看集合。 您將會撰寫程式碼，以查看集合中的每個項目。 

您也會建立迭代器方法，也就是為該類別的項目產生迭代器的方法。 這些方法可用於：

+ 在集合中的每個項目上執行動作。
+ 列舉自訂集合。
+ 擴充 [LINQ](linq/index.md) 或其他程式庫。
+ 建立資料管線，其中的資料會透過迭代器方法有效率地流動。

C# 語言會為上述兩個案例提供功能。 本文將概述這些功能。

本教學課程有多個步驟。 在每個步驟之後，您可以執行應用程式並查看進度。 您也可以[檢視或下載完整的範例](https://github.com/dotnet/docs/blob/master/samples/csharp/iterators)以了解此主題。 如需下載指示，請參閱[範例和教學課程](../samples-and-tutorials/index.md#viewing-and-downloading-samples)。

## <a name="iterating-with-foreach"></a>使用 foreach 逐一查看

列舉集合很簡單︰`foreach` 關鍵字會列舉集合，並對集合中的每個項目執行一次內嵌陳述式：
 
```csharp
foreach (var item in collection)
{
   Console.WriteLine(item.ToString());
}
```

這樣就全部完成了。 若要逐一查看集合的所有內容，只需要 `foreach` 陳述式即可。 不過，`foreach` 陳述式不是魔法。 它需要在 .NET Core 程式庫中定義下列兩個泛型介面，才能產生逐一查看集合所需的程式碼︰`IEnumerable<T>` 和 `IEnumerator<T>`。 以下會更詳細說明這個機制。

這兩種介面也有非泛型對應項目︰`IEnumerable` 和 `IEnumerator`。 新式程式碼適合使用[泛型](programming-guide/generics/index.md)版本。

## <a name="enumeration-sources-with-iterator-methods"></a>具有迭代器方法的列舉來源

C# 語言另一個很棒的功能是可讓您建立方法，以建立列舉的來源。 這些方法稱為「迭代器方法」。 迭代器方法定義如何在要求時於序列中產生物件。 您可以使用 `yield return` 內容關鍵字來定義迭代器方法。 

您可以撰寫這個方法，以產生從 0 到 9 的整數序列：

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    yield return 0;
    yield return 1;
    yield return 2;
    yield return 3;
    yield return 4;
    yield return 5;
    yield return 6;
    yield return 7;
    yield return 8;
    yield return 9;
}
```

上述程式碼顯示不同的 `yield return` 陳述式，強調您可以在迭代器方法中使用多個不連續的 `yield return` 陳述式。
您可以 (經常) 使用其他語言建構，來簡化迭代器方法的程式碼。 下列方法定義會產生完全相同的數值序列：

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
}
```

您不必決定其中一個。 您可以視需要擁有許多 `yield return` 陳述式，以符合您的方法需求：

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
        
    yield return 50;
    
    index = 100;
    while (index++ < 110)
        yield return index;
}
```

這是基本語法。 讓我們來看一個真實世界範例，您可以在其中撰寫迭代器方法。 假設您在某個 IoT 專案中，而裝置感應器會產生很大的資料流。 為了熟悉資料，您可以撰寫一個方法，每 N 個資料項目取樣一個項目。 此小型迭代器方法即可達成目的：

```csharp
public static IEnumerable<T> Sample(this IEnumerable<T> sourceSequence, int interval)
{
    int index = 0;
    foreach (T item in sourceSequence)
    {
        if (index++ % interval == 0)
            yield return item;
    }
}
```

迭代器方法有一項重要限制︰相同的方法中不能同時有 `return` 陳述式和 `yield return` 陳述式。 系統將不會編譯下列程式碼：

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
        
    yield return 50;
   
    // generates a compile time error: 
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    return items;  
}
```

這項限制通常不成問題。 您可以選擇在整個方法中使用 `yield return`，或是將原始方法分成多個方法，有些方法使用 `return`，而有些方法使用 `yield return`。

您可以稍微修改最後一個方法，以在所有位置使用 `yield return`：

```csharp
public IEnumerable<int> GetSingleDigitNumbers()
{
    int index = 0;
    while (index++ < 10)
        yield return index;
        
    yield return 50;
   
    var items = new int[] {100, 101, 102, 103, 104, 105, 106, 107, 108, 109 };
    foreach (var item in items)
        yield return item;
}
```
 
有時候，適當的解決方法是將一個迭代器方法分成兩個不同的方法。 其中一個方法使用 `return`，而第二個方法使用 `yield return`。 請考慮您可能需要根據布林值引數傳回空集合或前 5 個奇數的情況。 您可以將其撰寫成下列兩個方法：

```csharp
public IEnumerable<int> GetSingleDigitOddNumbers(bool getCollection)
{
    if (getCollection == false)
        return new int[0];
    else
        return IteratorMethod();
}

private IEnumerable<int> IteratorMethod()
{
    int index = 0;
    while (index++ < 10)
        if (index % 2 == 1)
            yield return index;
}
```
 
請看看上述方法。 第一個方法使用標準 `return` 陳述式來傳回空集合，或第二個方法所建立的迭代器。 第二個方法使用 `yield return` 陳述式來建立要求的序列。

## <a name="deeper-dive-into-foreach"></a>深入探討 `foreach`

`foreach` 陳述式會展開為一個標準慣例，該慣例使用 `IEnumable<T>` 和 `IEnumerator<T>` 介面來逐一查看集合的所有項目。 它也會將開發人員未正確管理資源時所發生的錯誤降到最低。 

編譯器會將第一個範例中所示的 `foreach` 迴圈轉譯為類似下列建構的程式碼：

```csharp
IEnumerator<int> enumerator = collection.GetEnumerator();
while (enumerator.MoveNext())
{
    var item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

上述建構代表 C# 編譯器第 5 版 (含) 以上版本所產生的程式碼。 在第 5 版之前，`item` 變數有不同的範圍：

```csharp
// C# versions 1 through 4:
IEnumerator<int> enumerator = collection.GetEnumerator();
int item = default(int);
while (enumerator.MoveNext())
{
    item = enumerator.Current;
    Console.WriteLine(item.ToString());
}
```

因為舊版行為可能會導致很難診斷涉及 Lambda 運算式的 Bug ，所以已變更此行為。 如需詳細資訊，請參閱 [Lambda 運算式](lambda-expressions.md)一節。 

編譯器所產生的實際程式碼稍微複雜一點，而且會處理 `GetEnumerator()` 所傳回的物件實作 `IDisposable` 介面的情況。 完全展開會產生類似如下的程式碼：

```csharp
{
    var enumerator = collection.GetEnumerator();
    try 
    {
        while (enumerator.MoveNext())
        {
            var item = enumerator.Current;
            Console.WriteLine(item.ToString());
        }
    } finally 
    {
        // dispose of enumerator.
    }
}
```

用來處置列舉程式的方法取決於 `enumerator` 類型的特性。 在一般情況下，`finally` 子句會展開為：

```csharp
finally 
{
   (enumerator as IDisposable)?.Dispose();
} 
```

不過，如果 `enumerator` 的類型是密封類型，而且不會將 `enumerator` 的類型隱含轉換成 `IDisposable`，則 `finally` 子句會展開為空白區塊：
```csharp
finally 
{
} 
```

如果會將 `enumerator` 的類型隱含轉換成 `IDisposable`，而且 `enumerator` 是不可為 null 的實值型別，`finally` 子句會展開為：

```csharp
finally 
{
   ((IDisposable)enumerator).Dispose();
} 
```

還好，您不需要記住上述所有詳細資料。 `foreach` 陳述式會為您處理上述所有細微差異。 編譯器會為上述任何建構產生正確的程式碼。 



