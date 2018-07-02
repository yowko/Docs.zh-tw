---
title: 使用列舉類別，而非列舉類型
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 使用列舉類別，而非列舉類型
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 1b2569caa7e7a6a899a6765d2e39d0fff8e37e2f
ms.sourcegitcommit: 6c480773ae896f45af4671fb3e26611a50e4dd81
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251190"
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a>使用列舉類別，而非列舉類型

[列舉](../../../../docs/csharp/language-reference/keywords/enum.md) (簡稱「列舉類型」) 是整數型別的精簡語言包裝函式。 您可能會想要將其用途限制在儲存一組封閉值中的一個值時。 依大小 (小、中、大) 分類是不錯的範例。 使用列舉來控制流程或更強固的抽象概念可能會導致[程式碼異味](http://deviq.com/code-smells/) (Code Smell)。 這種使用方式會導致程式碼因為有許多查看列舉值的控制流程陳述式而變得很脆弱。

相反地，您可以建立列舉類別，以便利用物件導向語言的所有豐富功能。

不過，這個主題並不重要，而且在許多情況下，為了方便作業，您仍然可以使用標準[列舉類型](../../../../docs/csharp/language-reference/keywords/enum.md) (如果偏好這樣做)。

## <a name="implementing-an-enumeration-base-class"></a>實作列舉基底類別

eShopOnContainers 中的訂購微服務提供範例列舉基底類別實作，如下列範例所示：

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; }
    public int Id { get; }

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

您可以使用此類別作為任何實體或值物件中的類型，如下列 CardType 列舉類別所示：

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

-   **Enum’s are evil—update**
    [*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/) (列舉很邪惡—更新)

-   **Daniel Hardman：How Enums Spread Disease — And How To Cure It**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/) (列舉傳播疾病的方式 — 以及如何治癒它)

-   **Jimmy Bogard：Enumeration classes**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/) (列舉類別)

-   **Steve Smith.Enum Alternatives in C#**
    [*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c) (C# 中的列舉替代項目)

-   **Enumeration.cs：** Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs) (eShopOnContainers 中的基底列舉類別)

-   **CardType.cs**： eShopOnContainers 中的範例列舉類別
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
[上一頁] (implement-value-objects.md) [下一頁] (domain-model-layer-validations.md)
