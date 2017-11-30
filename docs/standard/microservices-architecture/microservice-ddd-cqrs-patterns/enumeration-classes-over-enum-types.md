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
# <a name="using-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="d8b07-104">使用而不列舉類型的列舉型別類別</span><span class="sxs-lookup"><span data-stu-id="d8b07-104">Using Enumeration classes instead of enum types</span></span>

<span data-ttu-id="d8b07-105">[列舉型別](https://msdn.microsoft.com/en-us/library/sbbt4032.aspx)(*列舉*縮寫) 是整數類型的精簡型語言包裝函式。</span><span class="sxs-lookup"><span data-stu-id="d8b07-105">[Enumerations](https://msdn.microsoft.com/en-us/library/sbbt4032.aspx) (*enums* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="d8b07-106">您可能想要其使用限制為當您要儲存一個值從一組已關閉的值。</span><span class="sxs-lookup"><span data-stu-id="d8b07-106">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="d8b07-107">性別 （例如，男性，女性，未知） 或大小 (S、 M、 L，XL) 為基礎的分類是良好範例。</span><span class="sxs-lookup"><span data-stu-id="d8b07-107">Classification based on gender (for example, male, female, unknown), or sizes (S, M, L, XL) are good examples.</span></span> <span data-ttu-id="d8b07-108">使用控制流程或更強固的抽象概念列舉可能十分[程式碼氣味](http://deviq.com/code-smells/)。</span><span class="sxs-lookup"><span data-stu-id="d8b07-108">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="d8b07-109">易損壞的程式碼會導致這種類型的使用方式有許多的控制流程陳述式，檢查列舉的值。</span><span class="sxs-lookup"><span data-stu-id="d8b07-109">This type of usage will lead to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="d8b07-110">相反地，您可以建立列舉類別，可啟用的物件導向語言中的所有豐富功能。</span><span class="sxs-lookup"><span data-stu-id="d8b07-110">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span> <span data-ttu-id="d8b07-111">不過，這不嚴重的問題，而且在許多情況下，為了簡單起見，您仍然可以使用一般的列舉，為您的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="d8b07-111">However, this is not a critical issue and in many cases, for simplicity, you can still use regular enums if that is your preference.</span></span>

## <a name="implementing-enumeration-classes"></a><span data-ttu-id="d8b07-112">實作列舉型別類別</span><span class="sxs-lookup"><span data-stu-id="d8b07-112">Implementing Enumeration classes</span></span>

<span data-ttu-id="d8b07-113">EShopOnContainers 中順序的微服務提供的範例列舉基底類別實作，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d8b07-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

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

<span data-ttu-id="d8b07-114">您可以使用這個類別中任何實體或值的物件，與下列 CardType 列舉類別的型別。</span><span class="sxs-lookup"><span data-stu-id="d8b07-114">You can use this class as a type in any entity or value object, as for the following CardType Enumeration class.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="d8b07-115">其他資源</span><span class="sxs-lookup"><span data-stu-id="d8b07-115">Additional resources</span></span>

-   <span data-ttu-id="d8b07-116">**列舉的是惡意 — 更新**
    [*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span><span class="sxs-lookup"><span data-stu-id="d8b07-116">**Enum’s are evil—update**
[*http://www.planetgeek.ch/2009/07/01/enums-are-evil/*](http://www.planetgeek.ch/2009/07/01/enums-are-evil/)</span></span>

-   <span data-ttu-id="d8b07-117">**奧 Hardman。列舉傳播疾病的方式，以及如何更正它**
    [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span><span class="sxs-lookup"><span data-stu-id="d8b07-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It**
[*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)</span></span>

-   <span data-ttu-id="d8b07-118">**Jimmy Bogard：列舉類別**
    [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span><span class="sxs-lookup"><span data-stu-id="d8b07-118">**Jimmy Bogard. Enumeration classes**
[*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)</span></span>

-   <span data-ttu-id="d8b07-119">**Steve Smith。在 C# 中的替代項目列舉**
    [*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)</span><span class="sxs-lookup"><span data-stu-id="d8b07-119">**Steve Smith. Enum Alternatives in C#**
[*http://ardalis.com/enum-alternatives-in-c*](http://ardalis.com/enum-alternatives-in-c)</span></span>

-   <span data-ttu-id="d8b07-120">**Enumeration.cs。**</span><span class="sxs-lookup"><span data-stu-id="d8b07-120">**Enumeration.cs.**</span></span> <span data-ttu-id="d8b07-121">基底列舉類別中 eShopOnContainers [ *https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span><span class="sxs-lookup"><span data-stu-id="d8b07-121">Base Enumeration class in eShopOnContainers [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)</span></span>

-   <span data-ttu-id="d8b07-122">**CardType.cs**。</span><span class="sxs-lookup"><span data-stu-id="d8b07-122">**CardType.cs**.</span></span> <span data-ttu-id="d8b07-123">範例中 eShopOnContainers 列舉類別。</span><span class="sxs-lookup"><span data-stu-id="d8b07-123">Sample Enumeration class in eShopOnContainers.</span></span>
    [<span data-ttu-id="d8b07-124">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*</span><span class="sxs-lookup"><span data-stu-id="d8b07-124">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)


>[!div class="step-by-step"]
<span data-ttu-id="d8b07-125">[上一個](實作的值-objects.md) [下一步] (網域-模式-圖層-validations.md)</span><span class="sxs-lookup"><span data-stu-id="d8b07-125">[Previous] (implement-value-objects.md) [Next] (domain-model-layer-validations.md)</span></span>
