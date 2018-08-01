---
title: 介面設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- interfaces [.NET Framework], design guidelines
- type design guidelines, interfaces
- class library design guidelines [.NET Framework], interfaces
ms.assetid: a016bd18-6710-4358-9438-9f190a295392
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dea5877f952869d5c84d6019617fcdc52d8ee0a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33573035"
---
# <a name="interface-design"></a><span data-ttu-id="3a742-102">介面設計</span><span class="sxs-lookup"><span data-stu-id="3a742-102">Interface Design</span></span>
<span data-ttu-id="3a742-103">雖然大部分的應用程式開發介面最能模擬使用類別和結構，但是有些的狀況介面比較適合或是唯一的選項。</span><span class="sxs-lookup"><span data-stu-id="3a742-103">Although most APIs are best modeled using classes and structs, there are cases in which interfaces are more appropriate or are the only option.</span></span>  
  
 <span data-ttu-id="3a742-104">CLR 不支援多重繼承 （亦即，CLR 類別不可以繼承自多個基底類別），但它不允許實作除了繼承自基底類別的一個或多個介面的型別。</span><span class="sxs-lookup"><span data-stu-id="3a742-104">The CLR does not support multiple inheritance (i.e., CLR classes cannot inherit from more than one base class), but it does allow types to implement one or more interfaces in addition to inheriting from a base class.</span></span> <span data-ttu-id="3a742-105">因此，介面常用來達成的多重繼承的效果。</span><span class="sxs-lookup"><span data-stu-id="3a742-105">Therefore, interfaces are often used to achieve the effect of multiple inheritance.</span></span> <span data-ttu-id="3a742-106">例如，<xref:System.IDisposable>是一種介面，允許以支援 disposability 它們要加入任何其他繼承階層架構的獨立類型。</span><span class="sxs-lookup"><span data-stu-id="3a742-106">For example, <xref:System.IDisposable> is an interface that allows types to support disposability independent of any other inheritance hierarchy in which they want to participate.</span></span>  
  
 <span data-ttu-id="3a742-107">中定義的介面是適當的情況下會建立數種類型，包括一些實值類型必須支援的通用介面。</span><span class="sxs-lookup"><span data-stu-id="3a742-107">The other situation in which defining an interface is appropriate is in creating a common interface that can be supported by several types, including some value types.</span></span> <span data-ttu-id="3a742-108">實值類型無法繼承類型以外<xref:System.ValueType>，但它們可以實作介面，因此使用的介面是唯一的選項，以便提供通用基底型別。</span><span class="sxs-lookup"><span data-stu-id="3a742-108">Value types cannot inherit from types other than <xref:System.ValueType>, but they can implement interfaces, so using an interface is the only option in order to provide a common base type.</span></span>  
  
 <span data-ttu-id="3a742-109">**✓ DO**定義介面，如果您需要一組型別，其中包含實值類型必須支援某些一般的 API。</span><span class="sxs-lookup"><span data-stu-id="3a742-109">**✓ DO** define an interface if you need some common API to be supported by a set of types that includes value types.</span></span>  
  
 <span data-ttu-id="3a742-110">**✓ CONSIDER**定義介面，如果您需要在已經繼承自其他類型的型別上支援其功能。</span><span class="sxs-lookup"><span data-stu-id="3a742-110">**✓ CONSIDER** defining an interface if you need to support its functionality on types that already inherit from some other type.</span></span>  
  
 <span data-ttu-id="3a742-111">**X AVOID**使用標記介面 （不含成員的介面）。</span><span class="sxs-lookup"><span data-stu-id="3a742-111">**X AVOID** using marker interfaces (interfaces with no members).</span></span>  
  
 <span data-ttu-id="3a742-112">如果您要將類別標示為具有特定特性 （標記），請在一般情況下，使用自訂屬性，而不是介面。</span><span class="sxs-lookup"><span data-stu-id="3a742-112">If you need to mark a class as having a specific characteristic (marker), in general, use a custom attribute rather than an interface.</span></span>  
  
 <span data-ttu-id="3a742-113">**✓ DO**提供至少一個型別是介面的實作。</span><span class="sxs-lookup"><span data-stu-id="3a742-113">**✓ DO** provide at least one type that is an implementation of an interface.</span></span>  
  
 <span data-ttu-id="3a742-114">此舉有助於驗證介面的設計。</span><span class="sxs-lookup"><span data-stu-id="3a742-114">Doing this helps to validate the design of the interface.</span></span> <span data-ttu-id="3a742-115">例如，<xref:System.Collections.Generic.List%601>是實作<xref:System.Collections.Generic.IList%601>介面。</span><span class="sxs-lookup"><span data-stu-id="3a742-115">For example, <xref:System.Collections.Generic.List%601> is an implementation of the <xref:System.Collections.Generic.IList%601> interface.</span></span>  
  
 <span data-ttu-id="3a742-116">**✓ DO**提供至少一個應用程式開發介面使用您定義每個介面 （做為參數或屬性取得介面的方法型別為介面）。</span><span class="sxs-lookup"><span data-stu-id="3a742-116">**✓ DO** provide at least one API that consumes each interface you define (a method taking the interface as a parameter or a property typed as the interface).</span></span>  
  
 <span data-ttu-id="3a742-117">此舉有助於驗證介面設計。</span><span class="sxs-lookup"><span data-stu-id="3a742-117">Doing this helps to validate the interface design.</span></span> <span data-ttu-id="3a742-118">例如，<xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>取用<xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType>介面。</span><span class="sxs-lookup"><span data-stu-id="3a742-118">For example, <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> consumes the <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> interface.</span></span>  
  
 <span data-ttu-id="3a742-119">**X DO NOT**將成員加入至先前已發佈的介面。</span><span class="sxs-lookup"><span data-stu-id="3a742-119">**X DO NOT** add members to an interface that has previously shipped.</span></span>  
  
 <span data-ttu-id="3a742-120">這樣會中斷介面的實作。</span><span class="sxs-lookup"><span data-stu-id="3a742-120">Doing so would break implementations of the interface.</span></span> <span data-ttu-id="3a742-121">您應該建立新的介面，以避免版本控制問題。</span><span class="sxs-lookup"><span data-stu-id="3a742-121">You should create a new interface in order to avoid versioning problems.</span></span>  
  
 <span data-ttu-id="3a742-122">除了這些指導方針所述的情況下，您在一般情況下，應該設計 managed 程式碼可重複使用程式庫選擇類別，而不是介面。</span><span class="sxs-lookup"><span data-stu-id="3a742-122">Except for the situations described in these guidelines, you should, in general, choose classes rather than interfaces in designing managed code reusable libraries.</span></span>  
  
 <span data-ttu-id="3a742-123">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="3a742-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="3a742-124">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="3a742-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a742-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3a742-125">See Also</span></span>  
 [<span data-ttu-id="3a742-126">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="3a742-126">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="3a742-127">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="3a742-127">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
