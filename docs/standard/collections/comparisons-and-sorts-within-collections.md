---
title: "在集合內比較和排序"
description: "在集合內比較和排序"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: c7b7c005-628d-427a-91ad-af0c3958c00e
translationtype: Human Translation
ms.sourcegitcommit: e07788926a995b41571be276379ad9285747951d
ms.openlocfilehash: de1fe3bb9b9a75561b4f28ec4609491d6f3c39f5

---

# <a name="comparisons-and-sorts-within-collections"></a>在集合內比較和排序

[System.Collections](https://docs.microsoft.com/dotnet/core/api/System.Collections) 類別幾乎會在管理集合內的所有處理序中執行比較，包含搜尋要移除的元素，或傳回成對的索引鍵與值。

集合通常會利用等號比較子和 (或) 排序比較子。 比較會使用兩個建構。 

## <a name="checking-for-equality"></a>檢查相等

例如，`Contains`、`IndexOf`、`LastIndexOf` 和 `Remove` 方法會為集合元素使用相等比較子。 如果集合為泛型，則會根據下列方針，比較項目是否相等：

*   如果類型 T 實作 [IEquatable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IEquatable-1) 泛型介面，則相等比較子會是該介面的 `Equals` 方法。

*   如果類型 T 未實作 `IEquatable<T>`，則會使用 `Object.Equals`。

此外，有些字典集合的建構函式多載，能接受 [IEqualityComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IEqualityComparer-1) 實作，其可用以比較索引鍵是否相等。

## <a name="determining-sort-order"></a>決定排序順序

例如，方法 `BinarySearch` 和 `Sort` 會為集合元素使用排序比較子。 比較可以在集合的元素之間進行，或在元素和指定的值之間進行。 若為比較物件，會有預設比較子和明確比較子的概念。 

預設比較子會依賴至少一個所比較的物件，實作 `IComparable` 介面。 最好的作法是在所有用做為清單集合中的值或是用做為字典集合中索引鍵的類別上，實作 `IComparable`。 若為泛型集合，會根據下列項目來決定相等比較：

*   如果類型 T 實作 [System.IComparable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IComparable-1) 泛型介面，則預設比較子會是該介面的 `CompareTo(T)` 方法。

*   如果類型 T 實作非泛型 [System.IComparable](https://docs.microsoft.com/dotnet/core/api/System.IComparable) 介面，則預設比較子會是該介面的 `CompareTo`(Object) 方法。

*   如果類型 T 沒有實作其中一個介面，則不會有預設比較子，且必須明確地提供比較子或比較委派。

若要提供明確比較，某些方法接受以 `IComparer` 實作為參數。 例如，`List<T>.Sort` 方法接受 [System.Collections.Generic.IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1) 實作。 

## <a name="equality-and-sort-example"></a>相等和排序範例

下列程式碼示範簡單商務物件上的 [IEquatable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IEquatable-1) 和 [IComparable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IComparable-1) 實作。 此外，當物件儲存在清單中且經過排序時，您會發現呼叫 `Sort()` 方法時，會為 'Part' 類型使用預設比較子，並使用匿名方法實作 `Sort(Comparison<T>)` 方法。

C#

```csharp
using System;
using System.Collections.Generic;
// Simple business object. A PartId is used to identify the type of part 
// but the part name can change. 
public class Part : IEquatable<Part> , IComparable<Part>
{
    public string PartName { get; set; }

    public int PartId { get; set; }

    public override string ToString()
    {
        return "ID: " + PartId + "   Name: " + PartName;
    }
    public override bool Equals(object obj)
    {
        if (obj == null) return false;
        Part objAsPart = obj as Part;
        if (objAsPart == null) return false;
        else return Equals(objAsPart);
    }
    public int SortByNameAscending(string name1, string name2)
    {

        return name1.CompareTo(name2);
    }

    // Default comparer for Part type.
    public int CompareTo(Part comparePart)
    {
          // A null value means that this object is greater.
        if (comparePart == null)
            return 1;

        else
            return this.PartId.CompareTo(comparePart.PartId);
    }
    public override int GetHashCode()
    {
        return PartId;
    }
    public bool Equals(Part other)
    {
        if (other == null) return false;
        return (this.PartId.Equals(other.PartId));
    }
    // Should also override == and != operators.

}
public class Example
{
    public static void Main()
    {
        // Create a list of parts.
        List<Part> parts = new List<Part>();

        // Add parts to the list.
        parts.Add(new Part() { PartName = "regular seat", PartId = 1434 });
        parts.Add(new Part() { PartName= "crank arm", PartId = 1234 });
        parts.Add(new Part() { PartName = "shift lever", PartId = 1634 }); ;
        // Name intentionally left null.
        parts.Add(new Part() {  PartId = 1334 });
        parts.Add(new Part() { PartName = "banana seat", PartId = 1444 });
        parts.Add(new Part() { PartName = "cassette", PartId = 1534 });


        // Write out the parts in the list. This will call the overridden 
        // ToString method in the Part class.
        Console.WriteLine("\nBefore sort:");
        foreach (Part aPart in parts)
        {
            Console.WriteLine(aPart);
        }


        // Call Sort on the list. This will use the 
        // default comparer, which is the Compare method 
        // implemented on Part.
        parts.Sort();


        Console.WriteLine("\nAfter sort by part number:");
        foreach (Part aPart in parts)
        {
            Console.WriteLine(aPart);
        }

        // This shows calling the Sort(Comparison(T) overload using 
        // an anonymous method for the Comparison delegate. 
        // This method treats null as the lesser of two values.
        parts.Sort(delegate(Part x, Part y)
        {
            if (x.PartName == null && y.PartName == null) return 0;
            else if (x.PartName == null) return -1;
            else if (y.PartName == null) return 1;
            else return x.PartName.CompareTo(y.PartName);
        });

        Console.WriteLine("\nAfter sort by name:");
        foreach (Part aPart in parts)
        {
            Console.WriteLine(aPart);
        }

        /*

            Before sort:
        ID: 1434   Name: regular seat
        ID: 1234   Name: crank arm
        ID: 1634   Name: shift lever
        ID: 1334   Name:
        ID: 1444   Name: banana seat
        ID: 1534   Name: cassette

        After sort by part number:
        ID: 1234   Name: crank arm
        ID: 1334   Name:
        ID: 1434   Name: regular seat
        ID: 1444   Name: banana seat
        ID: 1534   Name: cassette
        ID: 1634   Name: shift lever

        After sort by name:
        ID: 1334   Name:
        ID: 1444   Name: banana seat
        ID: 1534   Name: cassette
        ID: 1234   Name: crank arm
        ID: 1434   Name: regular seat
        ID: 1634   Name: shift lever

         */

    }
}
```

## <a name="see-also"></a>另請參閱

[IComparer](https://docs.microsoft.com/dotnet/core/api/System.Collections.IComparer)

[IEquatable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IEquatable-1)

[IComparer&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.Collections.Generic.IComparer-1)

[IComparable](https://docs.microsoft.com/dotnet/core/api/System.IComparable)

[IComparable&lt;T&gt;](https://docs.microsoft.com/dotnet/core/api/System.IComparable-1)



<!--HONumber=Nov16_HO1-->


