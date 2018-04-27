---
title: 例外狀況和效能
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tester-doer pattern
- TryParse pattern
- exceptions, throwing
- exceptions, performance
- throwing exceptions, performance
ms.assetid: 3ad6aad9-08e6-4232-b336-0e301f2493e6
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7972cf7d63ee22e791d46046f30c9be467cc758e
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="exceptions-and-performance"></a><span data-ttu-id="62939-102">例外狀況和效能</span><span class="sxs-lookup"><span data-stu-id="62939-102">Exceptions and Performance</span></span>
<span data-ttu-id="62939-103">一個常見的問題相關的例外狀況是針對經常失敗的程式碼使用例外狀況，如果實作的效能將會無法接受。</span><span class="sxs-lookup"><span data-stu-id="62939-103">One common concern related to exceptions is that if exceptions are used for code that routinely fails, the performance of the implementation will be unacceptable.</span></span> <span data-ttu-id="62939-104">這是有效的問題。</span><span class="sxs-lookup"><span data-stu-id="62939-104">This is a valid concern.</span></span> <span data-ttu-id="62939-105">當成員擲回例外狀況時，其效能可能會大幅度速度較慢。</span><span class="sxs-lookup"><span data-stu-id="62939-105">When a member throws an exception, its performance can be orders of magnitude slower.</span></span> <span data-ttu-id="62939-106">不過，它是達成目標時不允許使用錯誤碼的例外狀況指導方針嚴格遵守良好的效能。</span><span class="sxs-lookup"><span data-stu-id="62939-106">However, it is possible to achieve good performance while strictly adhering to the exception guidelines that disallow using error codes.</span></span> <span data-ttu-id="62939-107">本節中所述的兩種模式提供的建議執行這項操作。</span><span class="sxs-lookup"><span data-stu-id="62939-107">Two patterns described in this section suggest ways to do this.</span></span>  
  
 <span data-ttu-id="62939-108">**X 不**使用錯誤碼，例外狀況可能會造成負面影響效能的考量。</span><span class="sxs-lookup"><span data-stu-id="62939-108">**X DO NOT** use error codes because of concerns that exceptions might affect performance negatively.</span></span>  
  
 <span data-ttu-id="62939-109">若要改善效能，便可使用 Tester-doer 模式或再試一次剖析模式，在下兩節中所述。</span><span class="sxs-lookup"><span data-stu-id="62939-109">To improve performance, it is possible to use either the Tester-Doer Pattern or the Try-Parse Pattern, described in the next two sections.</span></span>  
  
## <a name="tester-doer-pattern"></a><span data-ttu-id="62939-110">Tester-doer 模式</span><span class="sxs-lookup"><span data-stu-id="62939-110">Tester-Doer Pattern</span></span>  
 <span data-ttu-id="62939-111">有時例外狀況擲回成員的可改善效能的分成兩個成員。</span><span class="sxs-lookup"><span data-stu-id="62939-111">Sometimes performance of an exception-throwing member can be improved by breaking the member into two.</span></span> <span data-ttu-id="62939-112">讓我們看看<xref:System.Collections.Generic.ICollection%601.Add%2A>方法<xref:System.Collections.Generic.ICollection%601>介面。</span><span class="sxs-lookup"><span data-stu-id="62939-112">Let’s look at the <xref:System.Collections.Generic.ICollection%601.Add%2A> method of the <xref:System.Collections.Generic.ICollection%601> interface.</span></span>  
  
```  
ICollection<int> numbers = ...   
numbers.Add(1);  
```  
  
 <span data-ttu-id="62939-113">此方法`Add`會擲回，如果集合是唯讀狀態。</span><span class="sxs-lookup"><span data-stu-id="62939-113">The method `Add` throws if the collection is read-only.</span></span> <span data-ttu-id="62939-114">這可以是在方法呼叫失敗通常預期有效能問題。</span><span class="sxs-lookup"><span data-stu-id="62939-114">This can be a performance problem in scenarios where the method call is expected to fail often.</span></span> <span data-ttu-id="62939-115">其中一種方式來緩和這個問題是測試集合是否為可寫入之前嘗試加入的值。</span><span class="sxs-lookup"><span data-stu-id="62939-115">One of the ways to mitigate the problem is to test whether the collection is writable before trying to add a value.</span></span>  
  
```  
ICollection<int> numbers = ...   
...  
if(!numbers.IsReadOnly){  
    numbers.Add(1);  
}  
```  
  
 <span data-ttu-id="62939-116">用來測試條件，這在我們的範例是屬性之成員`IsReadOnly`，指軟體測試人員。</span><span class="sxs-lookup"><span data-stu-id="62939-116">The member used to test a condition, which in our example is the property `IsReadOnly`, is referred to as the tester.</span></span> <span data-ttu-id="62939-117">用於執行可能會擲回的作業，該成員`Add`在本例中，方法指 doer。</span><span class="sxs-lookup"><span data-stu-id="62939-117">The member used to perform a potentially throwing operation, the `Add` method in our example, is referred to as the doer.</span></span>  
  
 <span data-ttu-id="62939-118">**✓ 考慮**Tester-doer 模式，可能會擲回例外狀況的成員在一般案例，以避免發生效能問題相關的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="62939-118">**✓ CONSIDER** the Tester-Doer Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
## <a name="try-parse-pattern"></a><span data-ttu-id="62939-119">嘗試剖析模式</span><span class="sxs-lookup"><span data-stu-id="62939-119">Try-Parse Pattern</span></span>  
 <span data-ttu-id="62939-120">適用於極重視效能的 Api，應該使用更快的模式比上一節中所述的 Tester-doer 模式。</span><span class="sxs-lookup"><span data-stu-id="62939-120">For extremely performance-sensitive APIs, an even faster pattern than the Tester-Doer Pattern described in the previous section should be used.</span></span> <span data-ttu-id="62939-121">此模式需要調整的成員名稱來讓妥善定義的測試大小寫的成員語意的一部分。</span><span class="sxs-lookup"><span data-stu-id="62939-121">The pattern calls for adjusting the member name to make a well-defined test case a part of the member semantics.</span></span> <span data-ttu-id="62939-122">例如，<xref:System.DateTime>定義<xref:System.DateTime.Parse%2A>剖析字串的失敗時，擲回例外狀況的方法。</span><span class="sxs-lookup"><span data-stu-id="62939-122">For example, <xref:System.DateTime> defines a <xref:System.DateTime.Parse%2A> method that throws an exception if parsing of a string fails.</span></span> <span data-ttu-id="62939-123">它也會定義對應<xref:System.DateTime.TryParse%2A>嘗試剖析，但如果方法傳回 false 剖析器失敗，並傳回成功剖析使用的結果`out`參數。</span><span class="sxs-lookup"><span data-stu-id="62939-123">It also defines a corresponding <xref:System.DateTime.TryParse%2A> method that attempts to parse, but returns false if parsing is unsuccessful and returns the result of a successful parsing using an `out` parameter.</span></span>  
  
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
  
 <span data-ttu-id="62939-124">當使用此模式時，務必在嚴格的詞彙定義再試一次功能。</span><span class="sxs-lookup"><span data-stu-id="62939-124">When using this pattern, it is important to define the try functionality in strict terms.</span></span> <span data-ttu-id="62939-125">如果成員失敗，因為任何原因以外完善再試一次，成員必須仍會擲回對應的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="62939-125">If the member fails for any reason other than the well-defined try, the member must still throw a corresponding exception.</span></span>  
  
 <span data-ttu-id="62939-126">**✓ 考慮**再試一次剖析模式，可能會擲回例外狀況的成員在一般案例，以避免發生效能問題相關的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="62939-126">**✓ CONSIDER** the Try-Parse Pattern for members that might throw exceptions in common scenarios to avoid performance problems related to exceptions.</span></span>  
  
 <span data-ttu-id="62939-127">**✓ 不要**方法實作這個模式使用的前置詞"Try"和布林值傳回型別。</span><span class="sxs-lookup"><span data-stu-id="62939-127">**✓ DO** use the prefix "Try" and Boolean return type for methods implementing this pattern.</span></span>  
  
 <span data-ttu-id="62939-128">**✓ 不要**擲回例外狀況的成員提供使用 Try 剖析模式，每個成員。</span><span class="sxs-lookup"><span data-stu-id="62939-128">**✓ DO** provide an exception-throwing member for each member using the Try-Parse Pattern.</span></span>  
  
 <span data-ttu-id="62939-129">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="62939-129">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="62939-130">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="62939-130">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62939-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62939-131">See Also</span></span>  
 [<span data-ttu-id="62939-132">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="62939-132">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="62939-133">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="62939-133">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
