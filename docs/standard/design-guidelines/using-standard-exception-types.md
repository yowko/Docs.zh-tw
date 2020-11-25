---
title: 使用標準例外狀況類型
description: 瞭解 .NET 中的標準例外狀況類型。 瞭解 SystemException、ApplicationException、ArgumentException、ComException 等等。
ms.date: 10/22/2008
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: ef420d47e6204aef5e3d9bc12ace31fbf5521ee7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734357"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="ce645-104">使用標準例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="ce645-104">Using Standard Exception Types</span></span>

<span data-ttu-id="ce645-105">本節說明架構所提供的標準例外狀況，以及其使用方式的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ce645-105">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="ce645-106">這份清單並不完整。</span><span class="sxs-lookup"><span data-stu-id="ce645-106">The list is by no means exhaustive.</span></span> <span data-ttu-id="ce645-107">請參閱 .NET Framework 參考檔，以取得其他架構例外狀況類型的使用方式。</span><span class="sxs-lookup"><span data-stu-id="ce645-107">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>

## <a name="exception-and-systemexception"></a><span data-ttu-id="ce645-108">例外狀況和 SystemException</span><span class="sxs-lookup"><span data-stu-id="ce645-108">Exception and SystemException</span></span>

 <span data-ttu-id="ce645-109">❌ 請勿擲回 <xref:System.Exception?displayProperty=nameWithType> 或 <xref:System.SystemException?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="ce645-109">❌ DO NOT throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="ce645-110">❌ 除非您想要重新擲回，否則請勿攔截 `System.Exception` 或 `System.SystemException` 在架構程式碼中。</span><span class="sxs-lookup"><span data-stu-id="ce645-110">❌ DO NOT catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>

 <span data-ttu-id="ce645-111">❌ 避免攔截 `System.Exception` 或 `System.SystemException` （除了最上層例外狀況處理常式之外）。</span><span class="sxs-lookup"><span data-stu-id="ce645-111">❌ AVOID catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>

## <a name="applicationexception"></a><span data-ttu-id="ce645-112">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="ce645-112">ApplicationException</span></span>

 <span data-ttu-id="ce645-113">❌ 請勿擲回或衍生自 <xref:System.ApplicationException> 。</span><span class="sxs-lookup"><span data-stu-id="ce645-113">❌ DO NOT throw or derive from <xref:System.ApplicationException>.</span></span>

## <a name="invalidoperationexception"></a><span data-ttu-id="ce645-114">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="ce645-114">InvalidOperationException</span></span>

 <span data-ttu-id="ce645-115"><xref:System.InvalidOperationException>如果物件處於不適當的狀態，✔️就會擲回。</span><span class="sxs-lookup"><span data-stu-id="ce645-115">✔️ DO throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="ce645-116">ArgumentException、System.argumentnullexception 和 ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="ce645-116">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>

 <span data-ttu-id="ce645-117"><xref:System.ArgumentException>如果將不正確的引數傳遞給成員，✔️會擲回或其中一個子類型。</span><span class="sxs-lookup"><span data-stu-id="ce645-117">✔️ DO throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="ce645-118">偏好最常衍生的例外狀況類型（如果適用）。</span><span class="sxs-lookup"><span data-stu-id="ce645-118">Prefer the most derived exception type, if applicable.</span></span>

 <span data-ttu-id="ce645-119">✔️當擲回 `ParamName` 的其中一個子類別時，請設定屬性 `ArgumentException` 。</span><span class="sxs-lookup"><span data-stu-id="ce645-119">✔️ DO set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>

 <span data-ttu-id="ce645-120">此屬性代表導致擲回例外狀況的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="ce645-120">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="ce645-121">請注意，您可以使用其中一個函數多載來設定屬性。</span><span class="sxs-lookup"><span data-stu-id="ce645-121">Note that the property can be set using one of the constructor overloads.</span></span>

 <span data-ttu-id="ce645-122">✔️請將 `value` 用於屬性 setter 的隱含值參數名稱。</span><span class="sxs-lookup"><span data-stu-id="ce645-122">✔️ DO use `value` for the name of the implicit value parameter of property setters.</span></span>

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="ce645-123">NullReferenceException、IndexOutOfRangeException 和了 [accessviolationexception</span><span class="sxs-lookup"><span data-stu-id="ce645-123">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>

 <span data-ttu-id="ce645-124">❌ 不允許可公開呼叫的 Api 明確或隱含地擲回 <xref:System.NullReferenceException> 、 <xref:System.AccessViolationException> 或 <xref:System.IndexOutOfRangeException> 。</span><span class="sxs-lookup"><span data-stu-id="ce645-124">❌ DO NOT allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="ce645-125">這些例外狀況會由執行引擎保留並擲回，而在大部分情況下，則表示有錯誤。</span><span class="sxs-lookup"><span data-stu-id="ce645-125">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>

 <span data-ttu-id="ce645-126">請檢查引數，以避免擲回這些例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ce645-126">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="ce645-127">擲回這些例外狀況會公開可能隨著時間變更之方法的執行詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ce645-127">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>

## <a name="stackoverflowexception"></a><span data-ttu-id="ce645-128">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="ce645-128">StackOverflowException</span></span>

 <span data-ttu-id="ce645-129">❌ 不要明確擲回 <xref:System.StackOverflowException> 。</span><span class="sxs-lookup"><span data-stu-id="ce645-129">❌ DO NOT explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="ce645-130">例外狀況只能由 CLR 明確擲回。</span><span class="sxs-lookup"><span data-stu-id="ce645-130">The exception should be explicitly thrown only by the CLR.</span></span>

 <span data-ttu-id="ce645-131">❌ 請勿攔截 `StackOverflowException` 。</span><span class="sxs-lookup"><span data-stu-id="ce645-131">❌ DO NOT catch `StackOverflowException`.</span></span>

 <span data-ttu-id="ce645-132">撰寫 managed 程式碼時，幾乎不可能發生任意堆疊溢位的情況。</span><span class="sxs-lookup"><span data-stu-id="ce645-132">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="ce645-133">CLR 未受管理的部分保持一致，方法是使用探查將堆疊溢位移至妥善定義的位置，而不是從任意堆疊溢位進行備份。</span><span class="sxs-lookup"><span data-stu-id="ce645-133">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>

## <a name="outofmemoryexception"></a><span data-ttu-id="ce645-134">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="ce645-134">OutOfMemoryException</span></span>

 <span data-ttu-id="ce645-135">❌ 不要明確擲回 <xref:System.OutOfMemoryException> 。</span><span class="sxs-lookup"><span data-stu-id="ce645-135">❌ DO NOT explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="ce645-136">只有 CLR 基礎結構才會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ce645-136">This exception is to be thrown only by the CLR infrastructure.</span></span>

## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="ce645-137">ComException、SEHException 和 ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="ce645-137">ComException, SEHException, and ExecutionEngineException</span></span>

 <span data-ttu-id="ce645-138">❌ 請勿明確擲回 <xref:System.Runtime.InteropServices.COMException> 、  <xref:System.ExecutionEngineException> 和 <xref:System.Runtime.InteropServices.SEHException> 。</span><span class="sxs-lookup"><span data-stu-id="ce645-138">❌ DO NOT explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="ce645-139">這些例外狀況只能由 CLR 基礎結構擲回。</span><span class="sxs-lookup"><span data-stu-id="ce645-139">These exceptions are to be thrown only by the CLR infrastructure.</span></span>

 <span data-ttu-id="ce645-140">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="ce645-140">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="ce645-141">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="ce645-141">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ce645-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ce645-142">See also</span></span>

- [<span data-ttu-id="ce645-143">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="ce645-143">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="ce645-144">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="ce645-144">Design Guidelines for Exceptions</span></span>](exceptions.md)
