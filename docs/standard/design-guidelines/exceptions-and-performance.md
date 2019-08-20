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
author: KrzysztofCwalina
ms.openlocfilehash: 967692092186b81802a7ab635ea8fe4dbacd49ed
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69611512"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="c8b9e-102">例外狀況和效能</span><span class="sxs-lookup"><span data-stu-id="c8b9e-102">Exceptions and Performance</span></span>
<span data-ttu-id="c8b9e-103">例外狀況的其中一個常見問題是, 如果例外狀況是用於經常失敗的程式碼, 則無法接受執行的效能。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="c8b9e-104">這是有效的考慮。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-104">This is a valid concern.</span></span> <span data-ttu-id="c8b9e-105">當成員擲回例外狀況時, 其效能可能是速度較慢的順序。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="c8b9e-106">不過, 您可以達成良好的效能, 同時嚴格遵守不允許使用錯誤碼的例外狀況指導方針。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="c8b9e-107">本節所述的兩種模式會建議執行這項操作的方式。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-107">Two patterns described in this section suggest ways to do this.</span></span>

 <span data-ttu-id="c8b9e-108">**X DO NOT** 使用錯誤碼，例外狀況可能會造成負面影響效能的考量。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-108">**X DO NOT** use error codes because of concerns that exceptions might affect performance negatively.</span></span>

 <span data-ttu-id="c8b9e-109">若要改善效能, 您可以使用惡人之手模式或 Try-Parse 模式, 如下兩節所述。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>

## <a name="tester-doer-pattern"></a><span data-ttu-id="c8b9e-110">測試人員-惡人之手模式</span><span class="sxs-lookup"><span data-stu-id="c8b9e-110">Tester-Doer Pattern</span></span>
 <span data-ttu-id="c8b9e-111">有時候, 例外狀況擲回成員的效能可以藉由將成員分成兩個來改善。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="c8b9e-112">讓我們看看<xref:System.Collections.Generic.ICollection%601.Add%2A> <xref:System.Collections.Generic.ICollection%601>介面的方法。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>

```csharp
ICollection<int> numbers = ...
numbers.Add(1);
```

 <span data-ttu-id="c8b9e-113">如果集合`Add`是唯讀的, 方法會擲回。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="c8b9e-114">這可能會在方法呼叫預期經常失敗的情況下, 發生效能問題。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="c8b9e-115">解決此問題的其中一個方法, 就是先測試集合是否為可寫入, 再嘗試加入值。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>

```csharp
ICollection<int> numbers = ...
...
if (!numbers.IsReadOnly)
{
    numbers.Add(1);
}
```

 <span data-ttu-id="c8b9e-116">用來測試條件的成員 (在我們的範例中為屬性`IsReadOnly`) 稱為「測試者」。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="c8b9e-117">用來執行可能擲回作業的成員 (在`Add`我們的範例中為方法) 稱為惡人之手。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>

 <span data-ttu-id="c8b9e-118">**✓ CONSIDER** Tester-doer 模式，可能會擲回例外狀況的成員在一般案例，以避免發生效能問題相關的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-118">**✓ CONSIDER** the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

## <a name="try-parse-pattern"></a><span data-ttu-id="c8b9e-119">Try-剖析模式</span><span class="sxs-lookup"><span data-stu-id="c8b9e-119">Try-Parse Pattern</span></span>
 <span data-ttu-id="c8b9e-120">對於非常效能敏感的 Api, 應使用比上一節中所述的測試人員惡人之手模式更快的模式。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="c8b9e-121">模式會呼叫來調整成員名稱, 讓定義完善的測試案例成為成員語義的一部分。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="c8b9e-122">例如, <xref:System.DateTime>會<xref:System.DateTime.Parse%2A>定義方法, 如果字串剖析失敗, 則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="c8b9e-123">它也會定義嘗試<xref:System.DateTime.TryParse%2A>剖析的對應方法, 但如果剖析不成功, 則會傳回 false, 並`out`使用參數傳回成功剖析的結果。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>

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

 <span data-ttu-id="c8b9e-124">使用此模式時, 請務必以嚴格的條款定義 try 功能。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="c8b9e-125">如果成員因為任何不是妥善定義的嘗試而失敗, 則成員仍然必須擲回對應的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>

 <span data-ttu-id="c8b9e-126">**✓ CONSIDER** 再試一次剖析模式，可能會擲回例外狀況的成員在一般案例，以避免發生效能問題相關的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-126">**✓ CONSIDER** the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>

 <span data-ttu-id="c8b9e-127">**✓ DO** 方法實作這個模式使用的前置詞"Try"和布林值傳回型別。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-127">**✓ DO** use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>

 <span data-ttu-id="c8b9e-128">**✓ DO** 擲回例外狀況的成員提供使用 Try 剖析模式，每個成員。</span><span class="sxs-lookup"><span data-stu-id="c8b9e-128">**✓ DO** provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>

 <span data-ttu-id="c8b9e-129">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="c8b9e-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="c8b9e-130">*從[架構設計方針轉載已獲得皮耳森教育, inc. 的許可權:Krzysztof Cwalina 和 Brad Abrams 可重複使用的 .net 程式庫第](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 2 版的慣例、慣用語和模式, 已于2008年10月22日發行, 屬於 Microsoft Windows 開發系列的 Addison-Wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="c8b9e-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="c8b9e-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8b9e-131">See also</span></span>

- [<span data-ttu-id="c8b9e-132">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="c8b9e-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="c8b9e-133">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="c8b9e-133">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
