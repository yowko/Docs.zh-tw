---
title: "使用而不列舉類型的列舉型別類別"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |使用而不列舉類型的列舉型別類別"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1745198720fd12a9d26aab2d2afb2c5dd6b6b49d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a>使用而不列舉類型的列舉型別類別

[列舉型別](https://msdn.microsoft.com/en-us/library/sbbt4032.aspx)(*列舉*縮寫) 是整數類型的精簡型語言包裝函式。 您可能想要其使用限制為當您要儲存一個值從一組已關閉的值。 性別 （例如，男性，女性，未知） 或大小 (S、 M、 L，XL) 為基礎的分類是良好範例。 使用控制流程或更強固的抽象概念列舉可能十分[程式碼氣味](http://deviq.com/code-smells/)。 易損壞的程式碼會導致這種類型的使用方式有許多的控制流程陳述式，檢查列舉的值。

相反地，您可以建立列舉類別，可啟用的物件導向語言中的所有豐富功能。 不過，這不嚴重的問題，而且在許多情況下，為了簡單起見，您仍然可以使用一般的列舉，為您的喜好設定。

## <a name="implementing-enumeration-classes"></a>實作列舉型別類別

EShopOnContainers 中順序的微服務提供的範例列舉基底類別實作，如下列範例所示：

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }
    public int Id { get; private set; }

    protected Enumeration()
    {
    }

    protected Enumeration(int id, string name)
    {
        Id = id;
        Name = name;
    }

    public override string ToString()
    {
        return Name;
    }

    public static IEnumerable<T> GetAll<T>() where T : Enumeration, new()
    {
        var type = typeof(T);
        var fields = type.GetTypeInfo().GetFields(BindingFlags.Public |
            BindingFlags.Static |
            BindingFlags.DeclaredOnly);
        foreach (var info in fields)
        {
            var instance = new T();
            var locatedValue = info.GetValue(instance) as T;
            if (locatedValue != null)
            {
                yield return locatedValue;
            }
        }
    }

    public override bool Equals(object obj)
    {
        var otherValue = obj as Enumeration;
        if (otherValue == null)
        {
            return false;
        }
        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);
        return typeMatches && valueMatches;
    }

    public int CompareTo(object other)
    {
        return Id.CompareTo(((Enumeration)other).Id);
    }

    // Other utility methods ...
}
```

您可以使用這個類別中任何實體或值的物件，與下列 CardType 列舉類別的型別。

```csharp
public class CardType : Enumeration
{
    public static CardType Amex = new CardType(1, "Amex");
    public static CardType Visa = new CardType(2, "Visa");
    public static CardType MasterCard = new CardType(3, "MasterCard");

    protected CardType() { }

    public CardType(int id, string name)
        : base(id, name)
    {
    }


    public static IEnumerable<CardType> List()
    {
        return new[] { Amex, Visa, MasterCard };
    }
    // Other util methods
}
```

## <a name="additional-resources"></a>其他資源

-   **列舉的是惡意 — 更新**
    [*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)

-   **奧 Hardman。列舉傳播疾病的方式，以及如何更正它**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)

-   **Jimmy Bogard：列舉類別**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)

-   **Steve Smith。在 C# 中的替代項目列舉**
    [*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)

-   **Enumeration.cs。** 基底列舉類別中 eShopOnContainers [ *https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)

-   **CardType.cs**。 範例中 eShopOnContainers 列舉類別。
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
[上一個](實作的值-objects.md) [下一步] (網域-模式-圖層-validations.md)
