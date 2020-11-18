---
title: 例外狀況和效能
ms.date: 10/22/2008
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
ms.openlocfilehash: 1d9e4ff3cfb02b1db358c19786322622621329fe
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821199"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="1ec04-102">例外狀況和效能</span><span class="sxs-lookup"><span data-stu-id="1ec04-102">Exceptions and Performance</span></span>
<span data-ttu-id="1ec04-103">與例外狀況相關的其中一個常見考慮是，如果例外狀況是用於經常失敗的程式碼，就無法接受執行的效能。</span><span class="sxs-lookup"><span data-stu-id="1ec04-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="1ec04-104">此顧慮是有效的。</span><span class="sxs-lookup"><span data-stu-id="1ec04-104">This is a valid concern.</span></span> <span data-ttu-id="1ec04-105">當成員擲回例外狀況時，其效能可能會以較慢的順序排列。</span><span class="sxs-lookup"><span data-stu-id="1ec04-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="1ec04-106">不過，您可以達到良好的效能，同時嚴格遵守不允許使用錯誤碼的例外狀況指導方針。</span><span class="sxs-lookup"><span data-stu-id="1ec04-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="1ec04-107">本章節所述的兩種模式會建議您這樣做。</span><span class="sxs-lookup"><span data-stu-id="1ec04-107">Two patterns described in this section suggest ways to do this.</span></span>

 <span data-ttu-id="1ec04-108">❌ 由於例外狀況可能會對效能造成負面影響，因此請勿使用錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="1ec04-108">❌ DO NOT use error codes because of concerns that exceptions might affect performance negatively.</span></span>

 <span data-ttu-id="1ec04-109">若要改善效能，您可以使用 Tester-Doer 模式或 Try-Parse 模式，如接下來的兩節所述。</span><span class="sxs-lookup"><span data-stu-id="1ec04-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>

## <a name="tester-doer-pattern"></a><span data-ttu-id="1ec04-110">Tester-Doer 模式</span><span class="sxs-lookup"><span data-stu-id="1ec04-110">Tester-Doer Pattern</span></span>
 <span data-ttu-id="1ec04-111">有時候例外狀況擲回成員的效能，可以藉由將成員分成兩個來改善。</span><span class="sxs-lookup"><span data-stu-id="1ec04-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="1ec04-112">讓我們看看 <xref:System.Collections.Generic.ICollection%601.Add%2A> 介面的方法 <xref:System.Collections.Generic.ICollection%601> 。</span><span class="sxs-lookup"><span data-stu-id="1ec04-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 <span data-ttu-id="1ec04-113">`Add`如果集合是唯讀的，方法會擲回。</span><span class="sxs-lookup"><span data-stu-id="1ec04-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="1ec04-114">如果預期方法呼叫通常會失敗，這可能會造成效能問題。</span><span class="sxs-lookup"><span data-stu-id="1ec04-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="1ec04-115">解決問題的其中一種方法，是在嘗試加入值之前測試是否可寫入集合。</span><span class="sxs-lookup"><span data-stu-id="1ec04-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 <span data-ttu-id="1ec04-116">用來測試條件的成員（在我們的範例中為屬性）稱為「測試人員」（test） `IsReadOnly` 。</span><span class="sxs-lookup"><span data-stu-id="1ec04-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="1ec04-117">用來執行可能擲回作業的成員（ `Add` 在我們的範例中為方法）稱為惡人之手。</span><span class="sxs-lookup"><span data-stu-id="1ec04-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>

 <span data-ttu-id="1ec04-118">✔️針對可能會在常見案例中擲回例外狀況的成員考慮 Tester-Doer 模式，以避免與例外狀況相關的效能問題。</span><span class="sxs-lookup"><span data-stu-id="1ec04-118">✔️ CONSIDER the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

## <a name="try-parse-pattern"></a><span data-ttu-id="1ec04-119">Try-Parse 模式</span><span class="sxs-lookup"><span data-stu-id="1ec04-119">Try-Parse Pattern</span></span>
 <span data-ttu-id="1ec04-120">針對極具效能效益的 Api，您應該使用比上一節所述的 Tester-Doer 模式更快的模式。</span><span class="sxs-lookup"><span data-stu-id="1ec04-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="1ec04-121">模式會呼叫以調整成員名稱，使定義完善的測試案例成為成員語義的一部分。</span><span class="sxs-lookup"><span data-stu-id="1ec04-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="1ec04-122">例如， <xref:System.DateTime> 定義 <xref:System.DateTime.Parse%2A> 當字串剖析失敗時擲回例外狀況的方法。</span><span class="sxs-lookup"><span data-stu-id="1ec04-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="1ec04-123">它也會定義 <xref:System.DateTime.TryParse%2A> 嘗試剖析的對應方法，但如果剖析失敗，則會傳回 false，並傳回使用參數成功剖析的結果 `out` 。</span><span class="sxs-lookup"><span data-stu-id="1ec04-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>

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

 <span data-ttu-id="1ec04-124">使用此模式時，請務必以嚴格的條款來定義 try 功能。</span><span class="sxs-lookup"><span data-stu-id="1ec04-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="1ec04-125">如果成員因為明確定義的 try 以外的任何原因而失敗，則成員仍然必須擲回對應的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="1ec04-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>

 <span data-ttu-id="1ec04-126">✔️針對可能會在常見案例中擲回例外狀況的成員考慮 Try-Parse 模式，以避免與例外狀況相關的效能問題。</span><span class="sxs-lookup"><span data-stu-id="1ec04-126">✔️ CONSIDER the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

 <span data-ttu-id="1ec04-127">✔️針對實作為此模式的方法，請使用前置詞 "Try" 和布林傳回型別。</span><span class="sxs-lookup"><span data-stu-id="1ec04-127">✔️ DO use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>

 <span data-ttu-id="1ec04-128">✔️使用 Try-Parse 模式，為每個成員提供例外狀況擲回成員。</span><span class="sxs-lookup"><span data-stu-id="1ec04-128">✔️ DO provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>

 <span data-ttu-id="1ec04-129">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="1ec04-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="1ec04-130">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="1ec04-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="1ec04-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="1ec04-131">See also</span></span>

- [<span data-ttu-id="1ec04-132">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="1ec04-132">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="1ec04-133">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="1ec04-133">Design Guidelines for Exceptions</span></span>](exceptions.md)
