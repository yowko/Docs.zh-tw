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
# <a name="using-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="ed6c2-103">使用列舉類別，而非列舉類型</span><span class="sxs-lookup"><span data-stu-id="ed6c2-103">Using enumeration classes instead of enum types</span></span>

<span data-ttu-id="ed6c2-104">[列舉](../../../../docs/csharp/language-reference/keywords/enum.md) (簡稱「列舉類型」) 是整數型別的精簡語言包裝函式。</span><span class="sxs-lookup"><span data-stu-id="ed6c2-104">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="ed6c2-105">您可能會想要將其用途限制在儲存一組封閉值中的一個值時。</span><span class="sxs-lookup"><span data-stu-id="ed6c2-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="ed6c2-106">依大小 (小、中、大) 分類是不錯的範例。</span><span class="sxs-lookup"><span data-stu-id="ed6c2-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="ed6c2-107">使用列舉來控制流程或更強固的抽象概念可能會導致[程式碼異味](http://deviq.com/code-smells/) (Code Smell)。</span><span class="sxs-lookup"><span data-stu-id="ed6c2-107">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="ed6c2-108">這種使用方式會導致程式碼因為有許多查看列舉值的控制流程陳述式而變得很脆弱。</span><span class="sxs-lookup"><span data-stu-id="ed6c2-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="ed6c2-109">相反地，您可以建立列舉類別，以便利用物件導向語言的所有豐富功能。</span><span class="sxs-lookup"><span data-stu-id="ed6c2-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="ed6c2-110">不過，這個主題並不重要，而且在許多情況下，為了方便作業，您仍然可以使用標準[列舉類型](../../../../docs/csharp/language-reference/keywords/enum.md) (如果偏好這樣做)。</span><span class="sxs-lookup"><span data-stu-id="ed6c2-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../../docs/csharp/language-reference/keywords/enum.md) if that's your preference.</span></span>

## <a name="implementing-an-enumeration-base-class"></a><span data-ttu-id="ed6c2-111">實作列舉基底類別</span><span class="sxs-lookup"><span data-stu-id="ed6c2-111">Implementing an Enumeration base class</span></span>

<span data-ttu-id="ed6c2-112">eShopOnContainers 中的訂購微服務提供範例列舉基底類別實作，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ed6c2-112">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="ed6c2-113">您可以使用此類別作為任何實體或值物件中的類型，如下列 CardType 列舉類別所示：</span><span class="sxs-lookup"><span data-stu-id="ed6c2-113">You can use this class as a type in any entity or value object, as for the following CardType Enumeration class:</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="ed6c2-114">其他資源</span><span class="sxs-lookup"><span data-stu-id="ed6c2-114">Additional resources</span></span>

-   <span data-ttu-id="ed6c2-115">**Enum’s are evil—update**
    [*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/) (列舉很邪惡—更新)</span><span class="sxs-lookup"><span data-stu-id="ed6c2-115">**Enum’s are evil—update**
[*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span></span>

-   <span data-ttu-id="ed6c2-116">**Daniel Hardman：How Enums Spread Disease — And How To Cure It**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/) (列舉傳播疾病的方式 — 以及如何治癒它)</span><span class="sxs-lookup"><span data-stu-id="ed6c2-116">**Daniel Hardman. How Enums Spread Disease — And How To Cure It**
[*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span></span>

-   <span data-ttu-id="ed6c2-117">**Jimmy Bogard：Enumeration classes**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/) (列舉類別)</span><span class="sxs-lookup"><span data-stu-id="ed6c2-117">**Jimmy Bogard. Enumeration classes**
[*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span></span>

-   <span data-ttu-id="ed6c2-118">**Steve Smith.Enum Alternatives in C#**
    [*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c) (C# 中的列舉替代項目)</span><span class="sxs-lookup"><span data-stu-id="ed6c2-118">**Steve Smith. Enum Alternatives in C#**
[*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)</span></span>

-   <span data-ttu-id="ed6c2-119">**Enumeration.cs：**</span><span class="sxs-lookup"><span data-stu-id="ed6c2-119">**Enumeration.cs.**</span></span> <span data-ttu-id="ed6c2-120">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs) (eShopOnContainers 中的基底列舉類別)</span><span class="sxs-lookup"><span data-stu-id="ed6c2-120">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span></span>

-   <span data-ttu-id="ed6c2-121">**CardType.cs**：</span><span class="sxs-lookup"><span data-stu-id="ed6c2-121">**CardType.cs**.</span></span> <span data-ttu-id="ed6c2-122">eShopOnContainers 中的範例列舉類別</span><span class="sxs-lookup"><span data-stu-id="ed6c2-122">Sample Enumeration class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
<span data-ttu-id="ed6c2-123">[上一頁] (implement-value-objects.md) [下一頁] (domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="ed6c2-123">[Previous] (implement-value-objects.md) [Next] (domain-model-layer-validations.md)</span></span>
