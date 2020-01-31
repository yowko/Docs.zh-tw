---
title: 例外狀況和效能
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
ms.openlocfilehash: afa4e748599781a5979823320d8913ff5357d415
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741652"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="9fc82-102">例外狀況和效能</span><span class="sxs-lookup"><span data-stu-id="9fc82-102">Exceptions and Performance</span></span>
<span data-ttu-id="9fc82-103">例外狀況的其中一個常見問題是，如果例外狀況是用於經常失敗的程式碼，則無法接受執行的效能。</span><span class="sxs-lookup"><span data-stu-id="9fc82-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="9fc82-104">這是有效的考慮。</span><span class="sxs-lookup"><span data-stu-id="9fc82-104">This is a valid concern.</span></span> <span data-ttu-id="9fc82-105">當成員擲回例外狀況時，其效能可能是速度較慢的順序。</span><span class="sxs-lookup"><span data-stu-id="9fc82-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="9fc82-106">不過，您可以達成良好的效能，同時嚴格遵守不允許使用錯誤碼的例外狀況指導方針。</span><span class="sxs-lookup"><span data-stu-id="9fc82-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="9fc82-107">本節所述的兩種模式會建議執行這項操作的方式。</span><span class="sxs-lookup"><span data-stu-id="9fc82-107">Two patterns described in this section suggest ways to do this.</span></span>

 <span data-ttu-id="9fc82-108">❌ 不使用錯誤碼，因為例外狀況可能會對效能造成負面影響。</span><span class="sxs-lookup"><span data-stu-id="9fc82-108">❌ DO NOT use error codes because of concerns that exceptions might affect performance negatively.</span></span>

 <span data-ttu-id="9fc82-109">若要改善效能，您可以使用惡人之手模式或 Try-Parse 模式，如下兩節所述。</span><span class="sxs-lookup"><span data-stu-id="9fc82-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>

## <a name="tester-doer-pattern"></a><span data-ttu-id="9fc82-110">測試人員-惡人之手模式</span><span class="sxs-lookup"><span data-stu-id="9fc82-110">Tester-Doer Pattern</span></span>
 <span data-ttu-id="9fc82-111">有時候，例外狀況擲回成員的效能可以藉由將成員分成兩個來改善。</span><span class="sxs-lookup"><span data-stu-id="9fc82-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="9fc82-112">讓我們看看 <xref:System.Collections.Generic.ICollection%601> 介面的 <xref:System.Collections.Generic.ICollection%601.Add%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9fc82-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 <span data-ttu-id="9fc82-113">如果集合是唯讀的，則方法 `Add` 擲回。</span><span class="sxs-lookup"><span data-stu-id="9fc82-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="9fc82-114">這可能會在方法呼叫預期經常失敗的情況下，發生效能問題。</span><span class="sxs-lookup"><span data-stu-id="9fc82-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="9fc82-115">解決此問題的其中一個方法，就是先測試集合是否為可寫入，再嘗試加入值。</span><span class="sxs-lookup"><span data-stu-id="9fc82-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 <span data-ttu-id="9fc82-116">用來測試條件的成員（在我們的範例中是 `IsReadOnly`的屬性，稱為「測試者」）。</span><span class="sxs-lookup"><span data-stu-id="9fc82-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="9fc82-117">用來執行可能擲回作業的成員（在我們的範例中為 `Add` 方法）稱為惡人之手。</span><span class="sxs-lookup"><span data-stu-id="9fc82-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>

 <span data-ttu-id="9fc82-118">✔️針對可能會在常見案例中擲回例外狀況的成員，請考慮測試人員惡人之手模式，以避免與例外狀況相關的效能問題。</span><span class="sxs-lookup"><span data-stu-id="9fc82-118">✔️ CONSIDER the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

## <a name="try-parse-pattern"></a><span data-ttu-id="9fc82-119">Try-剖析模式</span><span class="sxs-lookup"><span data-stu-id="9fc82-119">Try-Parse Pattern</span></span>
 <span data-ttu-id="9fc82-120">對於非常效能敏感的 Api，應使用比上一節中所述的測試人員惡人之手模式更快的模式。</span><span class="sxs-lookup"><span data-stu-id="9fc82-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="9fc82-121">模式會呼叫來調整成員名稱，讓定義完善的測試案例成為成員語義的一部分。</span><span class="sxs-lookup"><span data-stu-id="9fc82-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="9fc82-122">例如，如果字串的剖析失敗，<xref:System.DateTime> 會定義會擲回例外狀況的 <xref:System.DateTime.Parse%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="9fc82-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="9fc82-123">它也會定義嘗試剖析的對應 <xref:System.DateTime.TryParse%2A> 方法，但如果剖析不成功，則會傳回 false，並使用 `out` 參數傳回成功剖析的結果。</span><span class="sxs-lookup"><span data-stu-id="9fc82-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>

```csharp
public struct DateTime
{
    public static DateTime Parse(string dateTime)
    {
        ...
    }
    public static bool TryParse(string dateTime, out DateTime result)
    {
        ...
    }
}
```

 <span data-ttu-id="9fc82-124">使用此模式時，請務必以嚴格的條款定義 try 功能。</span><span class="sxs-lookup"><span data-stu-id="9fc82-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="9fc82-125">如果成員因為任何不是妥善定義的嘗試而失敗，則成員仍然必須擲回對應的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="9fc82-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>

 <span data-ttu-id="9fc82-126">✔️考慮可能會在常見案例中擲回例外狀況的成員的 Try 剖析模式，以避免與例外狀況相關的效能問題。</span><span class="sxs-lookup"><span data-stu-id="9fc82-126">✔️ CONSIDER the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

 <span data-ttu-id="9fc82-127">✔️對於實作為此模式的方法，請使用前置詞「Try」和布林傳回型別。</span><span class="sxs-lookup"><span data-stu-id="9fc82-127">✔️ DO use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>

 <span data-ttu-id="9fc82-128">✔️確實使用 Try-catch 模式，為每個成員提供例外狀況擲回的成員。</span><span class="sxs-lookup"><span data-stu-id="9fc82-128">✔️ DO provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>

 <span data-ttu-id="9fc82-129">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="9fc82-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="9fc82-130">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="9fc82-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="9fc82-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="9fc82-131">See also</span></span>

- [<span data-ttu-id="9fc82-132">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="9fc82-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="9fc82-133">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="9fc82-133">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
