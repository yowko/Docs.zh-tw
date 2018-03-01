---
title: "使用列舉類別，而非列舉類型"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | 使用列舉類別，而非列舉類型"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4b190ee9dde5628bf16fe9c483d3636539c29361
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="using-enumeration-classes-instead-of-enum-types"></a>使用列舉類別，而非列舉類型

[列舉](../../../../docs/csharp/language-reference/keywords/enum.md) (簡稱「列舉類型」) 是整數型別的精簡語言包裝函式。 您可能會想要將其用途限制在儲存一組封閉值中的一個值時。 根據性別 (例如男性、女性、不明) 或大小 (小、中、大) 的分類就是很好的例子。 使用列舉來控制流程或更強固的抽象概念可能會導致[程式碼異味](http://deviq.com/code-smells/) (Code Smell)。 這種使用方式會導致程式碼因為有許多查看列舉值的控制流程陳述式而變得很脆弱。

相反地，您可以建立列舉類別，以便利用物件導向語言的所有豐富功能。

不過，這個主題並不重要，而且在許多情況下，為了方便作業，您仍然可以使用標準[列舉類型](../../../../docs/csharp/language-reference/keywords/enum.md) (如果偏好這樣做)。

## <a name="implementing-an-enumeration-base-class"></a>實作列舉基底類別

eShopOnContainers 中的訂購微服務提供範例列舉基底類別實作，如下列範例所示：

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

-   **Enum’s are evil—update (列舉是有害的 - 更新版)**
    [*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)

-   **Daniel Hardman：How Enums Spread Disease — And How To Cure It (列舉如何散播疾病 - 又該如何對症下藥)**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)

-   **Jimmy Bogard：Enumeration classes (列舉類別)**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)

-   **Steve Smith：Enum Alternatives in C# (C# 中列舉的替代方案)**
    [*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)

-   **Enumeration.cs：** Base Enumeration class in eShopOnContainers (eShopOnContainers 中的基底列舉類別)[*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)

-   **CardType.cs**： eShopOnContainers 中的範例列舉類別
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
[上一個] (implement-value-objects.md) [下一個] (domain-model-layer-validations.md)
