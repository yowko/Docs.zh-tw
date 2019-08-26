---
title: 作法：新增 LINQ 查詢的自訂方法 (C#)
ms.date: 07/20/2015
ms.assetid: 1a500f60-2e10-49fb-8b2a-d8d08e4817cb
ms.openlocfilehash: fcf6814c8b3076a18e807a378796094a9ce2cf84
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594142"
---
# <a name="how-to-add-custom-methods-for-linq-queries-c"></a>作法：新增 LINQ 查詢的自訂方法 (C#)

您可以將擴充方法新增至 <xref:System.Collections.Generic.IEnumerable%601> 介面，來延伸您可以用於 LINQ 查詢的方法組。 例如，除了標準平均值或最多作業，您可以建立自訂的彙總方法，計算一系列值的單一值。 您也可以建立一個方法，用為自訂篩選器或一系列值的特定資料轉換，並傳回新的序列。 這類方法的範例包括 <xref:System.Linq.Enumerable.Distinct%2A>、<xref:System.Linq.Enumerable.Skip%2A> 和 <xref:System.Linq.Enumerable.Reverse%2A>。

當您延伸 <xref:System.Collections.Generic.IEnumerable%601> 介面時，可將自訂方法套用至任何可列舉的集合。 如需詳細資訊，請參閱[擴充方法](../../classes-and-structs/extension-methods.md)。

## <a name="adding-an-aggregate-method"></a>新增彙總方法

彙總方法會計算一組值的單一值。 LINQ 提供數種彙總方法，包括 <xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.Min%2A> 和 <xref:System.Linq.Enumerable.Max%2A>。 您可將擴充方法新增至 <xref:System.Collections.Generic.IEnumerable%601> 介面，建立自己的彙總方法。

下列程式碼範例示範如何建立呼叫 `Median` 的擴充方法，來計算一系列類型為 `double` 的中位數。

```csharp
public static class LINQExtension
{
    public static double Median(this IEnumerable<double> source)
    {
        if (source.Count() == 0)
        {
            throw new InvalidOperationException("Cannot compute median for an empty set.");
        }

        var sortedList = from number in source
                         orderby number
                         select number;

        int itemIndex = (int)sortedList.Count() / 2;

        if (sortedList.Count() % 2 == 0)
        {
            // Even number of items.
            return (sortedList.ElementAt(itemIndex) + sortedList.ElementAt(itemIndex - 1)) / 2;
        }
        else
        {
            // Odd number of items.
            return sortedList.ElementAt(itemIndex);
        }
    }
}
```

您可以使用從 <xref:System.Collections.Generic.IEnumerable%601> 介面呼叫其他彙總方法同樣的方式，為任何可列舉集合呼叫此擴充方法。

下列程式碼範例示範如何使用 `Median` 方法處理 `double` 類型的陣列。

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
*/
```

### <a name="overloading-an-aggregate-method-to-accept-various-types"></a>多載彙總方法以接受各種類型

您可以多載自己的彙總方法，讓它接受各種類型的序列。 標準方法是為每種類型建立多載。 另一種方法是建立採用泛型型別的多載，使用委派將它轉換成特定的類型。 您也可以結合這兩種方法。

#### <a name="to-create-an-overload-for-each-type"></a>為每種類型建立多載

您可以為想要支援的每種類型建立特定的多載。 下列程式碼範例示範適合 `integer` 類型之 `Median` 方法的多載。

```csharp
//int overload

public static double Median(this IEnumerable<int> source)
{
    return (from num in source select (double)num).Median();
}
```

您現在可以呼叫 `integer` 和 `double` 類型的 `Median` 多載，如下列程式碼所示︰

```csharp
double[] numbers1 = { 1.9, 2, 8, 4, 5.7, 6, 7.2, 0 };

var query1 = numbers1.Median();

Console.WriteLine("double: Median = " + query1);
```

```csharp
int[] numbers2 = { 1, 2, 3, 4, 5 };

var query2 = numbers2.Median();

Console.WriteLine("int: Median = " + query2);
```

```csharp
/*
 This code produces the following output:

 Double: Median = 4.85
 Integer: Median = 3
*/
```

#### <a name="to-create-a-generic-overload"></a>建立一般多載

您也可以建立接受一系列泛型物件的多載。 這個多載會接受委派作為參數，並使用它將泛型型別物件的序列轉換成特定的類型。

下列程式碼顯示 `Median` 方法的多載，接受 <xref:System.Func%602> 委派為參數。 這個委派會接受泛型型別 T 的物件，並傳回 `double` 類型的物件。

```csharp
// Generic overload.

public static double Median<T>(this IEnumerable<T> numbers,
                       Func<T, double> selector)
{
    return (from num in numbers select selector(num)).Median();
}
```

您現在可以針對一系列的類型物件呼叫 `Median` 方法。 如果類型沒有自己的方法多載，您就必須傳遞委派參數。 在 C# 中，您可以針對此目的使用 Lambda 運算式。 另僅限 Visual Basic，如果您使用 `Aggregate` 或 `Group By` 子句而不是方法呼叫，您可以傳遞此子句範圍內的任何值或運算式。

下列程式碼範例示範如何呼叫 `Median` 方法，處理整數陣列及字串陣列。 針對字串，會計算陣列字串長度的中間值。 此範例會示範如何將 <xref:System.Func%602> 委派參數傳遞至每個案例的 `Median` 方法。

```csharp
int[] numbers3 = { 1, 2, 3, 4, 5 };

/*
  You can use the num=>num lambda expression as a parameter for the Median method
  so that the compiler will implicitly convert its value to double.
  If there is no implicit conversion, the compiler will display an error message.
*/

var query3 = numbers3.Median(num => num);

Console.WriteLine("int: Median = " + query3);

string[] numbers4 = { "one", "two", "three", "four", "five" };

// With the generic overload, you can also use numeric properties of objects.

var query4 = numbers4.Median(str => str.Length);

Console.WriteLine("String: Median = " + query4);

/*
 This code produces the following output:

 Integer: Median = 3
 String: Median = 4
*/
```

## <a name="adding-a-method-that-returns-a-collection"></a>新增傳回集合的方法

您可以使用傳回一系列值的自訂查詢方法來延伸 <xref:System.Collections.Generic.IEnumerable%601> 介面。 在此情況下，方法必須傳回型別 <xref:System.Collections.Generic.IEnumerable%601> 的集合。 此等方法可用來將篩選條件或資料轉換套用至一系列的值。

下例示範如何建立名為 `AlternateElements` 的擴充方法，傳回集合中的每隔個項目，從第一個項目開始。

```csharp
// Extension method for the IEnumerable<T> interface.
// The method returns every other element of a sequence.

public static IEnumerable<T> AlternateElements<T>(this IEnumerable<T> source)
{
    List<T> list = new List<T>();

    int i = 0;

    foreach (var element in source)
    {
        if (i % 2 == 0)
        {
            list.Add(element);
        }

        i++;
    }

    return list;
}
```

您可為任何可列舉集合呼叫此擴充方法，就和您從 <xref:System.Collections.Generic.IEnumerable%601> 介面呼叫其他方法一樣，如下列程式碼所示：

```csharp
string[] strings = { "a", "b", "c", "d", "e" };

var query = strings.AlternateElements();

foreach (var element in query)
{
    Console.WriteLine(element);
}
/*
 This code produces the following output:

 a
 c
 e
*/
```

## <a name="see-also"></a>另請參閱

- <xref:System.Collections.Generic.IEnumerable%601>
- [擴充方法](../../classes-and-structs/extension-methods.md)
