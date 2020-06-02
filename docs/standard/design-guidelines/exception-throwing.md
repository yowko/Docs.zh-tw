---
title: 擲回例外狀況
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- exceptions, throwing
- explicitly throwing exceptions
- throwing exceptions, design guidelines
ms.assetid: 5388e02b-52f5-460e-a2b5-eeafe60eeebe
ms.openlocfilehash: 6bbc6e8fa11759afbd3a1fb2d785f476a6c178ad
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289807"
---
# <a name="exception-throwing"></a><span data-ttu-id="d6562-102">擲回例外狀況</span><span class="sxs-lookup"><span data-stu-id="d6562-102">Exception Throwing</span></span>
<span data-ttu-id="d6562-103">這一節中所述的例外狀況擲回指導方針，需要有良好的執行失敗意義定義。</span><span class="sxs-lookup"><span data-stu-id="d6562-103">Exception-throwing guidelines described in this section require a good definition of the meaning of execution failure.</span></span> <span data-ttu-id="d6562-104">當成員無法執行其設計所要執行的作業時（成員名稱會隱含），就會發生執行失敗。</span><span class="sxs-lookup"><span data-stu-id="d6562-104">Execution failure occurs whenever a member cannot do what it was designed to do (what the member name implies).</span></span> <span data-ttu-id="d6562-105">例如，如果 `OpenFile` 方法無法將開啟的檔案控制代碼傳回給呼叫端，則會將它視為執行失敗。</span><span class="sxs-lookup"><span data-stu-id="d6562-105">For example, if the `OpenFile` method cannot return an opened file handle to the caller, it would be considered an execution failure.</span></span>

 <span data-ttu-id="d6562-106">大部分的開發人員都已熟悉使用例外狀況來處理使用錯誤，例如零除或 null 參考。</span><span class="sxs-lookup"><span data-stu-id="d6562-106">Most developers have become comfortable with using exceptions for usage errors such as division by zero or null references.</span></span> <span data-ttu-id="d6562-107">在架構中，例外狀況會用於所有的錯誤情況，包括執行錯誤。</span><span class="sxs-lookup"><span data-stu-id="d6562-107">In the Framework, exceptions are used for all error conditions, including execution errors.</span></span>

 <span data-ttu-id="d6562-108">❌不要傳回錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="d6562-108">❌ DO NOT return error codes.</span></span>

 <span data-ttu-id="d6562-109">例外狀況是在架構中報告錯誤的主要方法。</span><span class="sxs-lookup"><span data-stu-id="d6562-109">Exceptions are the primary means of reporting errors in frameworks.</span></span>

 <span data-ttu-id="d6562-110">✔️會擲回例外狀況來報告執行失敗。</span><span class="sxs-lookup"><span data-stu-id="d6562-110">✔️ DO report execution failures by throwing exceptions.</span></span>

 <span data-ttu-id="d6562-111">✔️考慮藉由呼叫 `System.Environment.FailFast` （.NET Framework 2.0 功能）來終止進程，而不是在程式碼遇到不安全的情況下擲回例外狀況，以供進一步執行。</span><span class="sxs-lookup"><span data-stu-id="d6562-111">✔️ CONSIDER terminating the process by calling `System.Environment.FailFast` (.NET Framework 2.0 feature) instead of throwing an exception if your code encounters a situation where it is unsafe for further execution.</span></span>

 <span data-ttu-id="d6562-112">❌如果可能，請不要使用一般控制流程的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d6562-112">❌ DO NOT use exceptions for the normal flow of control, if possible.</span></span>

 <span data-ttu-id="d6562-113">除了系統失敗和具有潛在競爭情況的作業以外，架構設計人員應該設計 Api，讓使用者可以撰寫不會擲回例外狀況的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d6562-113">Except for system failures and operations with potential race conditions, framework designers should design APIs so users can write code that does not throw exceptions.</span></span> <span data-ttu-id="d6562-114">例如，您可以提供方法來檢查前置條件，然後再呼叫成員，讓使用者可以撰寫不會擲回例外狀況的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d6562-114">For example, you can provide a way to check preconditions before calling a member so users can write code that does not throw exceptions.</span></span>

 <span data-ttu-id="d6562-115">用來檢查另一個成員之前置條件的成員通常稱為「測試者」，而實際執行工作的成員稱為「惡人之手」。</span><span class="sxs-lookup"><span data-stu-id="d6562-115">The member used to check preconditions of another member is often referred to as a tester, and the member that actually does the work is called a doer.</span></span>

 <span data-ttu-id="d6562-116">在某些情況下，測試人員惡人之手模式可能會造成無法接受的效能負擔。</span><span class="sxs-lookup"><span data-stu-id="d6562-116">There are cases when the Tester-Doer Pattern can have an unacceptable performance overhead.</span></span> <span data-ttu-id="d6562-117">在這種情況下，應該考慮所謂的嘗試剖析模式（如需詳細資訊，請參閱[例外狀況和效能](exceptions-and-performance.md)）。</span><span class="sxs-lookup"><span data-stu-id="d6562-117">In such cases, the so-called Try-Parse Pattern should be considered (see [Exceptions and Performance](exceptions-and-performance.md) for more information).</span></span>

 <span data-ttu-id="d6562-118">✔️考慮擲回例外狀況的效能影響。</span><span class="sxs-lookup"><span data-stu-id="d6562-118">✔️ CONSIDER the performance implications of throwing exceptions.</span></span> <span data-ttu-id="d6562-119">每秒100以上的擲回率可能會明顯影響大部分應用程式的效能。</span><span class="sxs-lookup"><span data-stu-id="d6562-119">Throw rates above 100 per second are likely to noticeably impact the performance of most applications.</span></span>

 <span data-ttu-id="d6562-120">✔️確實記載由公開可呼叫成員擲回的所有例外狀況，因為違反了成員合約（而不是系統失敗），並將它們視為合約的一部分。</span><span class="sxs-lookup"><span data-stu-id="d6562-120">✔️ DO document all exceptions thrown by publicly callable members because of a violation of the member contract (rather than a system failure) and treat them as part of your contract.</span></span>

 <span data-ttu-id="d6562-121">屬於合約一部分的例外狀況不應該從某個版本變更為下一個版本（亦即，例外狀況類型不應變更，也不應該加入新的例外狀況）。</span><span class="sxs-lookup"><span data-stu-id="d6562-121">Exceptions that are a part of the contract should not change from one version to the next (i.e., exception type should not change, and new exceptions should not be added).</span></span>

 <span data-ttu-id="d6562-122">❌沒有可以擲回或不是根據某個選項的公用成員。</span><span class="sxs-lookup"><span data-stu-id="d6562-122">❌ DO NOT have public members that can either throw or not based on some option.</span></span>

 <span data-ttu-id="d6562-123">❌沒有會傳回例外狀況的公用成員做為傳回值或 `out` 參數。</span><span class="sxs-lookup"><span data-stu-id="d6562-123">❌ DO NOT have public members that return exceptions as the return value or an `out` parameter.</span></span>

 <span data-ttu-id="d6562-124">從公用 Api 傳回例外狀況，而不是擲回它們，會使例外狀況錯誤報表的許多優點。</span><span class="sxs-lookup"><span data-stu-id="d6562-124">Returning exceptions from public APIs instead of throwing them defeats many of the benefits of exception-based error reporting.</span></span>

 <span data-ttu-id="d6562-125">✔️考慮使用例外狀況產生器方法。</span><span class="sxs-lookup"><span data-stu-id="d6562-125">✔️ CONSIDER using exception builder methods.</span></span>

 <span data-ttu-id="d6562-126">通常會從不同的位置擲回相同的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d6562-126">It is common to throw the same exception from different places.</span></span> <span data-ttu-id="d6562-127">若要避免程式碼膨脹，請使用建立例外狀況的 helper 方法，並初始化其屬性。</span><span class="sxs-lookup"><span data-stu-id="d6562-127">To avoid code bloat, use helper methods that create exceptions and initialize their properties.</span></span>

 <span data-ttu-id="d6562-128">此外，擲回例外狀況的成員不會內嵌。</span><span class="sxs-lookup"><span data-stu-id="d6562-128">Also, members that throw exceptions are not getting inlined.</span></span> <span data-ttu-id="d6562-129">在產生器內移動 throw 語句可能會允許內嵌該成員。</span><span class="sxs-lookup"><span data-stu-id="d6562-129">Moving the throw statement inside the builder might allow the member to be inlined.</span></span>

 <span data-ttu-id="d6562-130">❌不要從例外狀況篩選區塊擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d6562-130">❌ DO NOT throw exceptions from exception filter blocks.</span></span>

 <span data-ttu-id="d6562-131">例外狀況篩選準則引發例外狀況時，CLR 會攔截例外狀況，而篩選準則會傳回 false。</span><span class="sxs-lookup"><span data-stu-id="d6562-131">When an exception filter raises an exception, the exception is caught by the CLR, and the filter returns false.</span></span> <span data-ttu-id="d6562-132">這種行為與執行和明確傳回 false 的篩選器不區分，因此很難進行偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="d6562-132">This behavior is indistinguishable from the filter executing and returning false explicitly and is therefore very difficult to debug.</span></span>

 <span data-ttu-id="d6562-133">❌避免從 finally 區塊明確擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="d6562-133">❌ AVOID explicitly throwing exceptions from finally blocks.</span></span> <span data-ttu-id="d6562-134">隱含擲回的例外狀況是由呼叫可接受的方法所產生。</span><span class="sxs-lookup"><span data-stu-id="d6562-134">Implicitly thrown exceptions resulting from calling methods that throw are acceptable.</span></span>

 <span data-ttu-id="d6562-135">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="d6562-135">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="d6562-136">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="d6562-136">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="d6562-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d6562-137">See also</span></span>

- [<span data-ttu-id="d6562-138">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="d6562-138">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="d6562-139">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="d6562-139">Design Guidelines for Exceptions</span></span>](exceptions.md)
