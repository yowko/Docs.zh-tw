---
title: 擲回例外狀況
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a493e6591d90ce05a652e48807f63fa90764a91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573717"
---
# <a name="exception-throwing"></a><span data-ttu-id="60616-102">擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="60616-102">Exception Throwing</span></span>
<span data-ttu-id="60616-103">擲回例外狀況這一節所述的指導方針需要良好定義的執行失敗的意義。</span><span class="sxs-lookup"><span data-stu-id="60616-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="60616-104">每當成員無法執行的動作前，就會發生執行失敗執行 （其成員名稱一樣）。</span><span class="sxs-lookup"><span data-stu-id="60616-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="60616-105">例如，如果`OpenFile`方法不能將開啟的檔案控制代碼傳回給呼叫者，它會被視為新的執行失敗。</span><span class="sxs-lookup"><span data-stu-id="60616-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>  
  
 <span data-ttu-id="60616-106">大部分的開發人員已成為想要使用使用量錯誤，例如除法的例外狀況，由零或 null 參考。</span><span class="sxs-lookup"><span data-stu-id="60616-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="60616-107">在架構中，例外狀況會用於所有的錯誤狀況，包括執行錯誤。</span><span class="sxs-lookup"><span data-stu-id="60616-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>  
  
 <span data-ttu-id="60616-108">**X 不**傳回的錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="60616-108">**X DO NOT** return error codes.</span></span>  
  
 <span data-ttu-id="60616-109">例外狀況是報告錯誤架構中的主要方法。</span><span class="sxs-lookup"><span data-stu-id="60616-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>  
  
 <span data-ttu-id="60616-110">**✓ 不要**報表執行失敗數目，所擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="60616-110">**✓ DO** report execution failures by throwing exceptions.</span></span>  
  
 <span data-ttu-id="60616-111">**✓ 考慮**藉由呼叫終止處理序`System.Environment.FailFast`（.NET Framework 2.0 功能） 而不是擲回例外狀況，如果您的程式碼遇到的情況下，它是不安全的進一步執行。</span><span class="sxs-lookup"><span data-stu-id="60616-111">**✓ CONSIDER** terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>  
  
 <span data-ttu-id="60616-112">**X 不**盡可能使用控制項的正常流程例外狀況。</span><span class="sxs-lookup"><span data-stu-id="60616-112">**X DO NOT** use exceptions for the normal flow of control, if possible.</span></span>  
  
 <span data-ttu-id="60616-113">除了系統失敗和作業可能的競爭情形，架構設計人員應該設計應用程式開發介面，讓使用者都可以寫入不擲回例外狀況的程式碼。</span><span class="sxs-lookup"><span data-stu-id="60616-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="60616-114">例如，您可以提供檢查先決條件之前呼叫成員，因此使用者可以撰寫程式碼不會擲回例外狀況的方法。</span><span class="sxs-lookup"><span data-stu-id="60616-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>  
  
 <span data-ttu-id="60616-115">用來檢查先決條件的另一個成員的成員通常稱為測試人員，並呼叫 doer 實際運作成員。</span><span class="sxs-lookup"><span data-stu-id="60616-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>  
  
 <span data-ttu-id="60616-116">有些情況是當 Tester-doer 模式可能是無法接受的效能負擔。</span><span class="sxs-lookup"><span data-stu-id="60616-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="60616-117">在這種情況下，應該考量所謂再試一次剖析模式 (請參閱[例外狀況和效能](../../../docs/standard/design-guidelines/exceptions-and-performance.md)如需詳細資訊)。</span><span class="sxs-lookup"><span data-stu-id="60616-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](../../../docs/standard/design-guidelines/exceptions-and-performance.md) for more information).</span></span>  
  
 <span data-ttu-id="60616-118">**✓ 考慮**擲回例外狀況的效能含意。</span><span class="sxs-lookup"><span data-stu-id="60616-118">**✓ CONSIDER** the performance implications of throwing exceptions.</span></span> <span data-ttu-id="60616-119">每秒 100 以上的擲回率是有可能會大幅影響大部分的應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="60616-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>  
  
 <span data-ttu-id="60616-120">**✓ 不要**文件，因為成員的違規的緣故，公開呼叫成員所擲回的所有例外狀況合約 （而不是系統失敗），並視為程式合約的一部分。</span><span class="sxs-lookup"><span data-stu-id="60616-120">**✓ DO** document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>  
  
 <span data-ttu-id="60616-121">例外狀況合約的一部分，不應該從一個版本變更至下一個 （亦即，不應該變更例外狀況類型，和不應該加入新的例外狀況）。</span><span class="sxs-lookup"><span data-stu-id="60616-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>  
  
 <span data-ttu-id="60616-122">**X 不**或不可以是擲回的公用成員取決於一些選項。</span><span class="sxs-lookup"><span data-stu-id="60616-122">**X DO NOT** have public members that can either throw or not based on some option.</span></span>  
  
 <span data-ttu-id="60616-123">**X 不**擁有傳回例外狀況當做傳回值的公用成員或`out`參數。</span><span class="sxs-lookup"><span data-stu-id="60616-123">**X DO NOT** have public members that return exceptions as the return value or an `out` parameter.</span></span>  
  
 <span data-ttu-id="60616-124">傳回從公用 Api，而不是擲回的例外狀況，就失去了許多例外狀況架構錯誤報告的優點。</span><span class="sxs-lookup"><span data-stu-id="60616-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>  
  
 <span data-ttu-id="60616-125">**✓ 考慮**使用例外狀況產生器方法。</span><span class="sxs-lookup"><span data-stu-id="60616-125">**✓ CONSIDER** using exception builder methods.</span></span>  
  
 <span data-ttu-id="60616-126">通常會從不同的地方擲回相同的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="60616-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="60616-127">若要避免程式碼，請使用 helper 方法，建立例外狀況，並初始化其屬性。</span><span class="sxs-lookup"><span data-stu-id="60616-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>  
  
 <span data-ttu-id="60616-128">此外，擲回例外狀況的成員不會進行內嵌。</span><span class="sxs-lookup"><span data-stu-id="60616-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="60616-129">移動產生器將 throw 陳述式可能會允許內嵌的成員。</span><span class="sxs-lookup"><span data-stu-id="60616-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>  
  
 <span data-ttu-id="60616-130">**X 不**擲回例外狀況的例外狀況篩選條件區塊。</span><span class="sxs-lookup"><span data-stu-id="60616-130">**X DO NOT** throw exceptions from exception filter blocks.</span></span>  
  
 <span data-ttu-id="60616-131">當例外狀況篩選條件會引發例外狀況時，由 CLR 攔截例外狀況和篩選條件傳回 false。</span><span class="sxs-lookup"><span data-stu-id="60616-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="60616-132">此行為是區別執行篩選條件並明確傳回 false，因此很難偵錯。</span><span class="sxs-lookup"><span data-stu-id="60616-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>  
  
 <span data-ttu-id="60616-133">**請避免 x**明確擲回例外狀況的 finally 區塊。</span><span class="sxs-lookup"><span data-stu-id="60616-133">**X AVOID** explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="60616-134">可接受的隱含擲回造成呼叫方法會擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="60616-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>  
  
 <span data-ttu-id="60616-135">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="60616-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="60616-136">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="60616-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60616-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60616-137">See Also</span></span>  
 [<span data-ttu-id="60616-138">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="60616-138">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="60616-139">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="60616-139">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
