---
title: 使用標準例外狀況類型
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- throwing exceptions, standard types
- catching exceptions
- exceptions, catching
- exceptions, throwing
ms.assetid: ab22ce03-78f9-4dca-8824-c7ed3bdccc27
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81e4047c171e3a58f335821d64390432524b25df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574591"
---
# <a name="using-standard-exception-types"></a><span data-ttu-id="7ed08-102">使用標準例外狀況類型</span><span class="sxs-lookup"><span data-stu-id="7ed08-102">Using Standard Exception Types</span></span>
<span data-ttu-id="7ed08-103">本章節描述架構和其使用方式的詳細資料所提供的標準例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7ed08-103">This section describes the standard exceptions provided by the Framework and the details of their usage.</span></span> <span data-ttu-id="7ed08-104">清單是不是完整詳盡。</span><span class="sxs-lookup"><span data-stu-id="7ed08-104">The list is by no means exhaustive.</span></span> <span data-ttu-id="7ed08-105">請參閱.NET Framework 參考文件的使用方式的其他架構例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="7ed08-105">Please refer to the .NET Framework reference documentation for usage of other Framework exception types.</span></span>  
  
## <a name="exception-and-systemexception"></a><span data-ttu-id="7ed08-106">例外狀況和 SystemException</span><span class="sxs-lookup"><span data-stu-id="7ed08-106">Exception and SystemException</span></span>  
 <span data-ttu-id="7ed08-107">**X 不**擲回<xref:System.Exception?displayProperty=nameWithType>或<xref:System.SystemException?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="7ed08-107">**X DO NOT** throw <xref:System.Exception?displayProperty=nameWithType> or <xref:System.SystemException?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="7ed08-108">**X 不**攔截`System.Exception`或`System.SystemException`framework 程式碼中，除非您想要重新擲回。</span><span class="sxs-lookup"><span data-stu-id="7ed08-108">**X DO NOT** catch `System.Exception` or `System.SystemException` in framework code, unless you intend to rethrow.</span></span>  
  
 <span data-ttu-id="7ed08-109">**請避免 x**攔截`System.Exception`或`System.SystemException`，除非在最上層例外狀況處理常式。</span><span class="sxs-lookup"><span data-stu-id="7ed08-109">**X AVOID** catching `System.Exception` or `System.SystemException`, except in top-level exception handlers.</span></span>  
  
## <a name="applicationexception"></a><span data-ttu-id="7ed08-110">ApplicationException</span><span class="sxs-lookup"><span data-stu-id="7ed08-110">ApplicationException</span></span>  
 <span data-ttu-id="7ed08-111">**X 不**擲回或衍生自<xref:System.ApplicationException>。</span><span class="sxs-lookup"><span data-stu-id="7ed08-111">**X DO NOT** throw or derive from <xref:System.ApplicationException>.</span></span>  
  
## <a name="invalidoperationexception"></a><span data-ttu-id="7ed08-112">InvalidOperationException</span><span class="sxs-lookup"><span data-stu-id="7ed08-112">InvalidOperationException</span></span>  
 <span data-ttu-id="7ed08-113">**✓ 不要**擲回<xref:System.InvalidOperationException>的物件是否不適當的狀態。</span><span class="sxs-lookup"><span data-stu-id="7ed08-113">**✓ DO** throw an <xref:System.InvalidOperationException> if the object is in an inappropriate state.</span></span>  
  
## <a name="argumentexception-argumentnullexception-and-argumentoutofrangeexception"></a><span data-ttu-id="7ed08-114">ArgumentException、 ArgumentNullException 和 ArgumentOutOfRangeException</span><span class="sxs-lookup"><span data-stu-id="7ed08-114">ArgumentException, ArgumentNullException, and ArgumentOutOfRangeException</span></span>  
 <span data-ttu-id="7ed08-115">**✓ 不要**擲回<xref:System.ArgumentException>或如果不正確的引數會傳遞給成員及其子型別之一。</span><span class="sxs-lookup"><span data-stu-id="7ed08-115">**✓ DO** throw <xref:System.ArgumentException> or one of its subtypes if bad arguments are passed to a member.</span></span> <span data-ttu-id="7ed08-116">如果適用，偏好最常衍生的例外狀況類型。</span><span class="sxs-lookup"><span data-stu-id="7ed08-116">Prefer the most derived exception type, if applicable.</span></span>  
  
 <span data-ttu-id="7ed08-117">**✓ 不要**設定`ParamName`屬性時擲回的子類別的其中一個`ArgumentException`。</span><span class="sxs-lookup"><span data-stu-id="7ed08-117">**✓ DO** set the `ParamName` property when throwing one of the subclasses of `ArgumentException`.</span></span>  
  
 <span data-ttu-id="7ed08-118">這個屬性表示造成擲回的例外狀況的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="7ed08-118">This property represents the name of the parameter that caused the exception to be thrown.</span></span> <span data-ttu-id="7ed08-119">請注意，這個屬性可以使用其中一個建構函式多載設定。</span><span class="sxs-lookup"><span data-stu-id="7ed08-119">Note that the property can be set using one of the constructor overloads.</span></span>  
  
 <span data-ttu-id="7ed08-120">**✓ 不要**使用`value`屬性 setter 的隱含值參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="7ed08-120">**✓ DO** use `value` for the name of the implicit value parameter of property setters.</span></span>  
  
## <a name="nullreferenceexception-indexoutofrangeexception-and-accessviolationexception"></a><span data-ttu-id="7ed08-121">NullReferenceException、 IndexOutOfRangeException 和了 AccessViolationException</span><span class="sxs-lookup"><span data-stu-id="7ed08-121">NullReferenceException, IndexOutOfRangeException, and AccessViolationException</span></span>  
 <span data-ttu-id="7ed08-122">**X 不**允許公開呼叫 Api，明確或隱含地擲回<xref:System.NullReferenceException>， <xref:System.AccessViolationException>，或<xref:System.IndexOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="7ed08-122">**X DO NOT** allow publicly callable APIs to explicitly or implicitly throw <xref:System.NullReferenceException>, <xref:System.AccessViolationException>, or <xref:System.IndexOutOfRangeException>.</span></span> <span data-ttu-id="7ed08-123">這些例外狀況會保留並擲回的執行引擎在大部分情況下表示 bug。</span><span class="sxs-lookup"><span data-stu-id="7ed08-123">These exceptions are reserved and thrown by the execution engine and in most cases indicate a bug.</span></span>  
  
 <span data-ttu-id="7ed08-124">執行檢查，以避免擲回這些例外狀況的引數。</span><span class="sxs-lookup"><span data-stu-id="7ed08-124">Do argument checking to avoid throwing these exceptions.</span></span> <span data-ttu-id="7ed08-125">擲回這些例外狀況會公開實作詳細資料，您可能會隨著時間變更的方法。</span><span class="sxs-lookup"><span data-stu-id="7ed08-125">Throwing these exceptions exposes implementation details of your method that might change over time.</span></span>  
  
## <a name="stackoverflowexception"></a><span data-ttu-id="7ed08-126">StackOverflowException</span><span class="sxs-lookup"><span data-stu-id="7ed08-126">StackOverflowException</span></span>  
 <span data-ttu-id="7ed08-127">**X 不**明確擲回<xref:System.StackOverflowException>。</span><span class="sxs-lookup"><span data-stu-id="7ed08-127">**X DO NOT** explicitly throw <xref:System.StackOverflowException>.</span></span> <span data-ttu-id="7ed08-128">應該在只能由 CLR 明確擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7ed08-128">The exception should be explicitly thrown only by the CLR.</span></span>  
  
 <span data-ttu-id="7ed08-129">**X 不**攔截`StackOverflowException`。</span><span class="sxs-lookup"><span data-stu-id="7ed08-129">**X DO NOT** catch `StackOverflowException`.</span></span>  
  
 <span data-ttu-id="7ed08-130">它是幾乎不可能撰寫仍然維持一致且任意堆疊溢位的 managed 程式碼。</span><span class="sxs-lookup"><span data-stu-id="7ed08-130">It is almost impossible to write managed code that remains consistent in the presence of arbitrary stack overflows.</span></span> <span data-ttu-id="7ed08-131">使用探查移動堆疊溢位到妥善定義的位置而非從任意的堆疊溢位退出，unmanaged 的 CLR 組件保持一致。</span><span class="sxs-lookup"><span data-stu-id="7ed08-131">The unmanaged parts of the CLR remain consistent by using probes to move stack overflows to well-defined places rather than by backing out from arbitrary stack overflows.</span></span>  
  
## <a name="outofmemoryexception"></a><span data-ttu-id="7ed08-132">OutOfMemoryException</span><span class="sxs-lookup"><span data-stu-id="7ed08-132">OutOfMemoryException</span></span>  
 <span data-ttu-id="7ed08-133">**X 不**明確擲回<xref:System.OutOfMemoryException>。</span><span class="sxs-lookup"><span data-stu-id="7ed08-133">**X DO NOT** explicitly throw <xref:System.OutOfMemoryException>.</span></span> <span data-ttu-id="7ed08-134">是僅供 CLR 基礎結構會擲回這個例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7ed08-134">This exception is to be thrown only by the CLR infrastructure.</span></span>  
  
## <a name="comexception-sehexception-and-executionengineexception"></a><span data-ttu-id="7ed08-135">ComException、 SEHException 和 ExecutionEngineException</span><span class="sxs-lookup"><span data-stu-id="7ed08-135">ComException, SEHException, and ExecutionEngineException</span></span>  
 <span data-ttu-id="7ed08-136">**X 不**明確擲回<xref:System.Runtime.InteropServices.COMException>， <xref:System.ExecutionEngineException>，和<xref:System.Runtime.InteropServices.SEHException>。</span><span class="sxs-lookup"><span data-stu-id="7ed08-136">**X DO NOT** explicitly throw <xref:System.Runtime.InteropServices.COMException>,  <xref:System.ExecutionEngineException>, and <xref:System.Runtime.InteropServices.SEHException>.</span></span> <span data-ttu-id="7ed08-137">這些例外狀況會擲回僅供 CLR 基礎結構。</span><span class="sxs-lookup"><span data-stu-id="7ed08-137">These exceptions are to be thrown only by the CLR infrastructure.</span></span>  
  
 <span data-ttu-id="7ed08-138">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="7ed08-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="7ed08-139">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="7ed08-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ed08-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ed08-140">See Also</span></span>  
 [<span data-ttu-id="7ed08-141">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="7ed08-141">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="7ed08-142">例外狀況的設計方針</span><span class="sxs-lookup"><span data-stu-id="7ed08-142">Design Guidelines for Exceptions</span></span>](../../../docs/standard/design-guidelines/exceptions.md)
