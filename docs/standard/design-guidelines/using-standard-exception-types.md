---
title: 使用標準例外狀況類型
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
ms.openlocfilehash: 3caa94d9a39966614161e4b19201dcf6065776a2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743548"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="54662-102">使用標準例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="54662-102">Using Standard Exception Types</span></span>
<span data-ttu-id="54662-103">本節說明架構所提供的標準例外狀況，以及其使用方式的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="54662-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="54662-104">清單完全不是完整的。</span><span class="sxs-lookup"><span data-stu-id="54662-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="54662-105">如需其他架構例外狀況類型的使用方式，請參閱 .NET Framework 參考檔。</span><span class="sxs-lookup"><span data-stu-id="54662-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>

## <a name="exception-and-systemexception"></a><span data-ttu-id="54662-106">Exception 和 SystemException</span><span class="sxs-lookup"><span data-stu-id="54662-106">Exception and SystemException</span></span>
 <span data-ttu-id="54662-107">❌ 不會擲回 <xref:System.Exception?displayProperty=nameWithType> 或 <xref:System.SystemException?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="54662-107">❌ DO NOT throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="54662-108">除非您想要重新擲回，否則 ❌ 不會在 framework 程式碼中攔截 `System.Exception` 或 `System.SystemException`。</span><span class="sxs-lookup"><span data-stu-id="54662-108">❌ DO NOT catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>

 <span data-ttu-id="54662-109">❌ 避免攔截 `System.Exception` 或 `System.SystemException`，但最上層的例外狀況處理常式除外。</span><span class="sxs-lookup"><span data-stu-id="54662-109">❌ AVOID catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>

## <a name="applicationexception"></a><span data-ttu-id="54662-110">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="54662-110">ApplicationException</span></span>
 <span data-ttu-id="54662-111">❌ 不會擲回或衍生自 <xref:System.ApplicationException>。</span><span class="sxs-lookup"><span data-stu-id="54662-111">❌ DO NOT throw or derive from <xref:System.ApplicationException>.</span></span>

## <a name="invalidoperationexception"></a><span data-ttu-id="54662-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="54662-112">InvalidOperationException</span></span>
 <span data-ttu-id="54662-113">如果物件處於不適當的狀態，✔️會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="54662-113">✔️ DO throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>

## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="54662-114">ArgumentException、System.argumentnullexception 和 ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="54662-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>
 <span data-ttu-id="54662-115">如果將不正確的引數傳遞給成員，✔️會擲回 <xref:System.ArgumentException> 或其中一個子類型。</span><span class="sxs-lookup"><span data-stu-id="54662-115">✔️ DO throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="54662-116">偏好最常衍生的例外狀況類型（如果適用的話）。</span><span class="sxs-lookup"><span data-stu-id="54662-116">Prefer the most derived exception type, if applicable.</span></span>

 <span data-ttu-id="54662-117">✔️在擲回 `ArgumentException`的其中一個子類別時，請設定 `ParamName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="54662-117">✔️ DO set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>

 <span data-ttu-id="54662-118">這個屬性代表導致擲回例外狀況的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="54662-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="54662-119">請注意，您可以使用其中一個函式多載來設定屬性。</span><span class="sxs-lookup"><span data-stu-id="54662-119">Note that the property can be set using one of the constructor overloads.</span></span>

 <span data-ttu-id="54662-120">✔️請將 `value` 用於屬性 setter 的隱含值參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="54662-120">✔️ DO use `value` for the name of the implicit value parameter of property setters.</span></span>

## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="54662-121">NullReferenceException、IndexOutOfRangeException 和 AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="54662-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>
 <span data-ttu-id="54662-122">❌ 不允許可公開呼叫的 Api 明確或隱含地擲回 <xref:System.NullReferenceException>、<xref:System.AccessViolationException>或 <xref:System.IndexOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="54662-122">❌ DO NOT allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="54662-123">這些例外狀況是由執行引擎保留和擲回，而在大部分情況下則表示 bug。</span><span class="sxs-lookup"><span data-stu-id="54662-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>

 <span data-ttu-id="54662-124">執行引數檢查以避免擲回這些例外狀況。</span><span class="sxs-lookup"><span data-stu-id="54662-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="54662-125">擲回這些例外狀況會公開可能隨著時間變更之方法的執行詳細資料。</span><span class="sxs-lookup"><span data-stu-id="54662-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>

## <a name="stackoverflowexception"></a><span data-ttu-id="54662-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="54662-126">StackOverflowException</span></span>
 <span data-ttu-id="54662-127">❌ 不會明確擲回 <xref:System.StackOverflowException>。</span><span class="sxs-lookup"><span data-stu-id="54662-127">❌ DO NOT explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="54662-128">例外狀況應該僅由 CLR 明確擲回。</span><span class="sxs-lookup"><span data-stu-id="54662-128">The exception should be explicitly thrown only by the CLR.</span></span>

 <span data-ttu-id="54662-129">❌ 不會攔截 `StackOverflowException`。</span><span class="sxs-lookup"><span data-stu-id="54662-129">❌ DO NOT catch `StackOverflowException`.</span></span>

 <span data-ttu-id="54662-130">在出現任意堆疊溢位的情況中，幾乎不可能撰寫會保持一致的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="54662-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="54662-131">CLR 的非受控元件會使用探查將堆疊溢位移到妥善定義的位置，而不是從任意堆疊溢位進行備份，以保持一致。</span><span class="sxs-lookup"><span data-stu-id="54662-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>

## <a name="outofmemoryexception"></a><span data-ttu-id="54662-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="54662-132">OutOfMemoryException</span></span>
 <span data-ttu-id="54662-133">❌ 不會明確擲回 <xref:System.OutOfMemoryException>。</span><span class="sxs-lookup"><span data-stu-id="54662-133">❌ DO NOT explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="54662-134">這個例外狀況只會由 CLR 基礎結構擲回。</span><span class="sxs-lookup"><span data-stu-id="54662-134">This exception is to be thrown only by the CLR infrastructure.</span></span>

## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="54662-135">ComException、SEHException 和 ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="54662-135">ComException, SEHException, and ExecutionEngineException</span></span>
 <span data-ttu-id="54662-136">❌ 不會明確擲回 <xref:System.Runtime.InteropServices.COMException>、<xref:System.ExecutionEngineException>和 <xref:System.Runtime.InteropServices.SEHException>。</span><span class="sxs-lookup"><span data-stu-id="54662-136">❌ DO NOT explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="54662-137">這些例外狀況只會由 CLR 基礎結構擲回。</span><span class="sxs-lookup"><span data-stu-id="54662-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>

 <span data-ttu-id="54662-138">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="54662-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="54662-139">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 *Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition[ 節錄。](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)*</span><span class="sxs-lookup"><span data-stu-id="54662-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="54662-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54662-140">See also</span></span>

- [<span data-ttu-id="54662-141">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="54662-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="54662-142">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="54662-142">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
