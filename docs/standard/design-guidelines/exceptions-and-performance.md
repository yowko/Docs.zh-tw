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
ms.openlocfilehash: ab125117836545b9a2436347375ed0e08c591c7b
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153744"
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="74d49-102">例外狀況和效能</span><span class="sxs-lookup"><span data-stu-id="74d49-102">Exceptions and Performance</span></span>
<span data-ttu-id="74d49-103">其中一個例外狀況的相關的一般考量，如果例外狀況會用於經常失敗的程式碼，實作的效能就是無法接受。</span><span class="sxs-lookup"><span data-stu-id="74d49-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="74d49-104">這是有效的考量。</span><span class="sxs-lookup"><span data-stu-id="74d49-104">This is a valid concern.</span></span> <span data-ttu-id="74d49-105">當成員擲回例外狀況時，其效能可以呈數量級速度較慢。</span><span class="sxs-lookup"><span data-stu-id="74d49-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="74d49-106">不過，就可以達到良好的效能，同時完全符合不允許使用錯誤碼的例外狀況指導方針。</span><span class="sxs-lookup"><span data-stu-id="74d49-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="74d49-107">這一節所述的兩種模式提供建議這樣做。</span><span class="sxs-lookup"><span data-stu-id="74d49-107">Two patterns described in this section suggest ways to do this.</span></span>  
  
 <span data-ttu-id="74d49-108">**X DO NOT** 使用錯誤碼，例外狀況可能會造成負面影響效能的考量。</span><span class="sxs-lookup"><span data-stu-id="74d49-108">**X DO NOT** use error codes because of concerns that exceptions might affect performance negatively.</span></span>  
  
 <span data-ttu-id="74d49-109">若要改善效能，就可以使用 Tester-doer 模式或嘗試剖析模式中，接下來兩節中所述。</span><span class="sxs-lookup"><span data-stu-id="74d49-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>  
  
## <a name="tester-doer-pattern"></a><span data-ttu-id="74d49-110">Tester-doer 模式</span><span class="sxs-lookup"><span data-stu-id="74d49-110">Tester-Doer Pattern</span></span>  
 <span data-ttu-id="74d49-111">有時可以被提升效能例外狀況擲回成員的成員分成兩個。</span><span class="sxs-lookup"><span data-stu-id="74d49-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="74d49-112">讓我們看看<xref:System.Collections.Generic.ICollection%601.Add%2A>方法的<xref:System.Collections.Generic.ICollection%601>介面。</span><span class="sxs-lookup"><span data-stu-id="74d49-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 <span data-ttu-id="74d49-113">此方法`Add`如果集合是唯讀模式則會擲回。</span><span class="sxs-lookup"><span data-stu-id="74d49-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="74d49-114">這可以是在方法呼叫應該在其中經常失敗的情況下的效能問題。</span><span class="sxs-lookup"><span data-stu-id="74d49-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="74d49-115">其中一種方式，來緩和這個問題是測試集合是否為可寫入之前嘗試加入的值。</span><span class="sxs-lookup"><span data-stu-id="74d49-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 <span data-ttu-id="74d49-116">用來測試條件，這在我們的範例是屬性的成員`IsReadOnly`，稱為 「 測試人員。</span><span class="sxs-lookup"><span data-stu-id="74d49-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="74d49-117">用來執行可能擲回的作業，該成員`Add`在我們的範例，方法指 doer。</span><span class="sxs-lookup"><span data-stu-id="74d49-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>  
  
 <span data-ttu-id="74d49-118">**✓ CONSIDER** Tester-doer 模式，可能會擲回例外狀況的成員在一般案例，以避免發生效能問題相關的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="74d49-118">**✓ CONSIDER** the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
## <a name="try-parse-pattern"></a><span data-ttu-id="74d49-119">嘗試剖析模式</span><span class="sxs-lookup"><span data-stu-id="74d49-119">Try-Parse Pattern</span></span>  
 <span data-ttu-id="74d49-120">對於極為重視效能的 Api，應該使用與上一節中所述的 Tester-doer 模式甚至更快的模式。</span><span class="sxs-lookup"><span data-stu-id="74d49-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="74d49-121">此模式需要調整要定義完善的測試案例的一部分成員語意的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="74d49-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="74d49-122">例如，<xref:System.DateTime>定義<xref:System.DateTime.Parse%2A>字串的剖析失敗時，擲回例外狀況的方法。</span><span class="sxs-lookup"><span data-stu-id="74d49-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="74d49-123">它也會定義相對應<xref:System.DateTime.TryParse%2A>嘗試剖析，但如果方法會傳回 false 剖析失敗，並傳回成功剖析使用結果`out`參數。</span><span class="sxs-lookup"><span data-stu-id="74d49-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>  
  
```  
public struct DateTime {  
    public static DateTime Parse(string dateTime){   
        ...   
    }  
    public static bool TryParse(string dateTime, out DateTime result){  
        ...  
    }  
}  
```  
  
 <span data-ttu-id="74d49-124">使用此模式時，務必在嚴格的詞彙定義試功能。</span><span class="sxs-lookup"><span data-stu-id="74d49-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="74d49-125">如果成員因為任何原因以外定義完善的嘗試失敗，成員必須仍會擲回對應的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="74d49-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>  
  
 <span data-ttu-id="74d49-126">**✓ CONSIDER** 再試一次剖析模式，可能會擲回例外狀況的成員在一般案例，以避免發生效能問題相關的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="74d49-126">**✓ CONSIDER** the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
 <span data-ttu-id="74d49-127">**✓ DO** 方法實作這個模式使用的前置詞"Try"和布林值傳回型別。</span><span class="sxs-lookup"><span data-stu-id="74d49-127">**✓ DO** use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>  
  
 <span data-ttu-id="74d49-128">**✓ DO** 擲回例外狀況的成員提供使用 Try 剖析模式，每個成員。</span><span class="sxs-lookup"><span data-stu-id="74d49-128">**✓ DO** provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>  
  
 <span data-ttu-id="74d49-129">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="74d49-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="74d49-130">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="74d49-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74d49-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74d49-131">See also</span></span>

- [<span data-ttu-id="74d49-132">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="74d49-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="74d49-133">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="74d49-133">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
