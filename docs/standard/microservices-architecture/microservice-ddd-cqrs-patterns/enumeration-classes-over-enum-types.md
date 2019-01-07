---
title: 使用列舉類別，而非列舉類型
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 了解如何使用列舉類別 (而非列舉) 來解決後者的一些限制。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 72a3e7ef8043e0016cefb45a4182b5c2e3061753
ms.sourcegitcommit: 3b9b7ae6771712337d40374d2fef6b25b0d53df6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/04/2019
ms.locfileid: "54029706"
---
# <a name="use-enumeration-classes-instead-of-enum-types"></a><span data-ttu-id="52f3b-103">使用列舉類別，而非列舉類型</span><span class="sxs-lookup"><span data-stu-id="52f3b-103">Use enumeration classes instead of enum types</span></span>

<span data-ttu-id="52f3b-104">[列舉](../../../../docs/csharp/language-reference/keywords/enum.md) (簡稱「列舉類型」) 是整數型別的精簡語言包裝函式。</span><span class="sxs-lookup"><span data-stu-id="52f3b-104">[Enumerations](../../../../docs/csharp/language-reference/keywords/enum.md) (or *enum types* for short) are a thin language wrapper around an integral type.</span></span> <span data-ttu-id="52f3b-105">您可能會想要將其用途限制在儲存一組封閉值中的一個值時。</span><span class="sxs-lookup"><span data-stu-id="52f3b-105">You might want to limit their use to when you are storing one value from a closed set of values.</span></span> <span data-ttu-id="52f3b-106">依大小 (小、中、大) 分類是不錯的範例。</span><span class="sxs-lookup"><span data-stu-id="52f3b-106">Classification based on sizes (small, medium, large) is a good example.</span></span> <span data-ttu-id="52f3b-107">使用列舉來控制流程或更強固的抽象概念可能會導致[程式碼異味](http://deviq.com/code-smells/) (Code Smell)。</span><span class="sxs-lookup"><span data-stu-id="52f3b-107">Using enums for control flow or more robust abstractions can be a [code smell](http://deviq.com/code-smells/).</span></span> <span data-ttu-id="52f3b-108">這種使用方式會導致程式碼因為有許多查看列舉值的控制流程陳述式而變得很脆弱。</span><span class="sxs-lookup"><span data-stu-id="52f3b-108">This type of usage leads to fragile code with many control flow statements checking values of the enum.</span></span>

<span data-ttu-id="52f3b-109">相反地，您可以建立列舉類別，以便利用物件導向語言的所有豐富功能。</span><span class="sxs-lookup"><span data-stu-id="52f3b-109">Instead, you can create Enumeration classes that enable all the rich features of an object-oriented language.</span></span>

<span data-ttu-id="52f3b-110">不過，這個主題並不重要，而且在許多情況下，為了方便作業，您仍然可以使用標準[列舉類型](../../../csharp/language-reference/keywords/enum.md) (如果偏好這樣做)。</span><span class="sxs-lookup"><span data-stu-id="52f3b-110">However, this isn't a critical topic and in many cases, for simplicity, you can still use regular [enum types](../../../csharp/language-reference/keywords/enum.md) if that's your preference.</span></span> <span data-ttu-id="52f3b-111">無論如何，使用列舉類別與商務相關概念比較有關。</span><span class="sxs-lookup"><span data-stu-id="52f3b-111">Anyway, the use of enumeration classes is more related to business-related concepts.</span></span>

## <a name="implement-an-enumeration-base-class"></a><span data-ttu-id="52f3b-112">實作列舉基底類別</span><span class="sxs-lookup"><span data-stu-id="52f3b-112">Implement an Enumeration base class</span></span>

<span data-ttu-id="52f3b-113">eShopOnContainers 中的訂購微服務提供範例列舉基底類別實作，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="52f3b-113">The ordering microservice in eShopOnContainers provides a sample Enumeration base class implementation, as shown in the following example:</span></span>

```csharp
public abstract class Enumeration : IComparable
{
    public string Name { get; private set; }

    public int Id { get; private set; }

    protected Enumeration()
    { }

    protected Enumeration(int id, string name) 
    {
        Id = id; 
        Name = name; 
    }

    public override string ToString() => Name;

    public static IEnumerable<T> GetAll<T>() where T : Enumeration
    {
        var fields = typeof(T).GetFields(BindingFlags.Public | 
                                         BindingFlags.Static | 
                                         BindingFlags.DeclaredOnly); 

        return fields.Select(f => f.GetValue(null)).Cast<T>();
    }

    public override bool Equals(object obj) 
    {
        var otherValue = obj as Enumeration; 

        if (otherValue == null) 
            return false;

        var typeMatches = GetType().Equals(obj.GetType());
        var valueMatches = Id.Equals(otherValue.Id);

        return typeMatches && valueMatches;
    }

    public int CompareTo(object other) => Id.CompareTo(((Enumeration)other).Id); 

    // Other utility methods ... 
}
```

<span data-ttu-id="52f3b-114">您可以使用此類別作為任何實體或值物件中的類型，如下列 `CardType` : `Enumeration` 類別所示：</span><span class="sxs-lookup"><span data-stu-id="52f3b-114">You can use this class as a type in any entity or value object, as for the following `CardType` : `Enumeration` class:</span></span>

```csharp
public abstract class CardType : Enumeration
{
    public static CardType Amex = new AmexCardType();
    public static CardType Visa = new VisaCardType();
    public static CardType MasterCard = new MasterCardType();

    protected CardType(int id, string name)
        : base(id, name)
    { }

    private class AmexCardType : CardType
    {
        public AmexCardType(): base(1, "Amex")
        { }
    }
    
    private class VisaCardType : CardType
    {
        public VisaCardType(): base(2, "Visa")
        { }
    }
    
    private class MasterCardType : CardType
    {
        public MasterCardType(): base(3, "MasterCard")
        { }
    }
}
```

## <a name="additional-resources"></a><span data-ttu-id="52f3b-115">其他資源</span><span class="sxs-lookup"><span data-stu-id="52f3b-115">Additional resources</span></span>

- <span data-ttu-id="52f3b-116">**Enum’s are evil—update (列舉很邪惡—更新)** \\</span><span class="sxs-lookup"><span data-stu-id="52f3b-116">**Enum’s are evil—update** \\</span></span>
  [*https://www.planetgeek.ch/2009/07/01/enums-are-evil/*](https://www.planetgeek.ch/2009/07/01/enums-are-evil/)

- <span data-ttu-id="52f3b-117">**Daniel Hardman：How Enums Spread Disease — And How To Cure It (列舉傳播疾病的方式 — 以及如何治癒它)** \\</span><span class="sxs-lookup"><span data-stu-id="52f3b-117">**Daniel Hardman. How Enums Spread Disease — And How To Cure It** \\</span></span>
  [*https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/*](https://codecraft.co/2012/10/29/how-enums-spread-disease-and-how-to-cure-it/)

- <span data-ttu-id="52f3b-118">**Jimmy Bogard：Enumeration classes (列舉類別)** \\</span><span class="sxs-lookup"><span data-stu-id="52f3b-118">**Jimmy Bogard. Enumeration classes** \\</span></span>
  [*https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/*](https://lostechies.com/jimmybogard/2008/08/12/enumeration-classes/)

- <span data-ttu-id="52f3b-119">**Steve Smith.Enum Alternatives in C# (C# 中的列舉替代項目)** \\</span><span class="sxs-lookup"><span data-stu-id="52f3b-119">**Steve Smith. Enum Alternatives in C#** \\</span></span>
  [*https://ardalis.com/enum-alternatives-in-c*](https://ardalis.com/enum-alternatives-in-c)

- <span data-ttu-id="52f3b-120">**Enumeration.cs：**</span><span class="sxs-lookup"><span data-stu-id="52f3b-120">**Enumeration.cs.**</span></span> <span data-ttu-id="52f3b-121">eShopOnContainers 中的基底列舉類別 \\</span><span class="sxs-lookup"><span data-stu-id="52f3b-121">Base Enumeration class in eShopOnContainers \\</span></span>
  [*https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs*](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/Enumeration.cs)

- <span data-ttu-id="52f3b-122">**CardType.cs**：</span><span class="sxs-lookup"><span data-stu-id="52f3b-122">**CardType.cs**.</span></span> <span data-ttu-id="52f3b-123">eShopOnContainers 中的範例列舉類別</span><span class="sxs-lookup"><span data-stu-id="52f3b-123">Sample Enumeration class in eShopOnContainers.</span></span> \
  [*https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs*](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/BuyerAggregate/CardType.cs)
    
- <span data-ttu-id="52f3b-124">**SmartEnum**：</span><span class="sxs-lookup"><span data-stu-id="52f3b-124">**SmartEnum**.</span></span> <span data-ttu-id="52f3b-125">Ardalis - 可協助在 .NET 中產生強型別且更聰明的列舉。</span><span class="sxs-lookup"><span data-stu-id="52f3b-125">Ardalis - Classes to help produce strongly typed smarter enums in .NET.</span></span> \
  [*https://www.nuget.org/packages/Ardalis.SmartEnum/*](https://www.nuget.org/packages/Ardalis.SmartEnum/)

>[!div class="step-by-step"]
><span data-ttu-id="52f3b-126">[上一頁](implement-value-objects.md)
>[下一頁](domain-model-layer-validations.md)</span><span class="sxs-lookup"><span data-stu-id="52f3b-126">[Previous](implement-value-objects.md)
[Next](domain-model-layer-validations.md)</span></span>