---
title: "擴充方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b7edc3420eabe4de20a2fe39f38ae5eee53b593c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="extension-methods"></a><span data-ttu-id="2512b-102">擴充方法</span><span class="sxs-lookup"><span data-stu-id="2512b-102">Extension Methods</span></span>
<span data-ttu-id="2512b-103">擴充方法是讓靜態方法，以使用執行個體方法的呼叫語法來呼叫的語言功能。</span><span class="sxs-lookup"><span data-stu-id="2512b-103">Extension methods are a language feature that allows static methods to be called using instance method call syntax.</span></span> <span data-ttu-id="2512b-104">這些方法必須使用至少一個參數，表示要對方法的執行個體。</span><span class="sxs-lookup"><span data-stu-id="2512b-104">These methods must take at least one parameter, which represents the instance the method is to operate on.</span></span>  
  
 <span data-ttu-id="2512b-105">定義這類的擴充方法的類別稱為 「 贊助者 」 類別，它必須宣告為靜態。</span><span class="sxs-lookup"><span data-stu-id="2512b-105">The class that defines such extension methods is referred to as the "sponsor" class, and it must be declared as static.</span></span> <span data-ttu-id="2512b-106">若要使用的擴充方法，一個必須匯入定義贊助者類別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="2512b-106">To use extension methods, one must import the namespace defining the sponsor class.</span></span>  
  
 <span data-ttu-id="2512b-107">**請避免 x** frivolously 特別是在不屬於您的型別上定義擴充方法。</span><span class="sxs-lookup"><span data-stu-id="2512b-107">**X AVOID** frivolously defining extension methods, especially on types you don’t own.</span></span>  
  
 <span data-ttu-id="2512b-108">如果您擁有類型的原始程式碼，請考慮改為使用一般的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="2512b-108">If you do own source code of a type, consider using regular instance methods instead.</span></span> <span data-ttu-id="2512b-109">如果您並不擁有，而且您想要加入的方法，要非常小心。</span><span class="sxs-lookup"><span data-stu-id="2512b-109">If you don’t own, and you want to add a method, be very careful.</span></span> <span data-ttu-id="2512b-110">盡量使用的擴充方法都有可能會想堆過去並非設計來將這些方法之型別的 Api。</span><span class="sxs-lookup"><span data-stu-id="2512b-110">Liberal use of extension methods has the potential of cluttering APIs of types that were not designed to have these methods.</span></span>  
  
 <span data-ttu-id="2512b-111">**✓ 考慮**任何下列案例中使用擴充方法：</span><span class="sxs-lookup"><span data-stu-id="2512b-111">**✓ CONSIDER** using extension methods in any of the following scenarios:</span></span>  
  
-   <span data-ttu-id="2512b-112">若要提供 helper 可以核心介面來撰寫功能適用於每個實作的介面時，如果說功能。</span><span class="sxs-lookup"><span data-stu-id="2512b-112">To provide helper functionality relevant to every implementation of an interface, if said functionality can be written in terms of the core interface.</span></span> <span data-ttu-id="2512b-113">這是因為介面否則無法指定具象實作。</span><span class="sxs-lookup"><span data-stu-id="2512b-113">This is because concrete implementations cannot otherwise be assigned to interfaces.</span></span> <span data-ttu-id="2512b-114">例如，`LINQ to Objects`運算子當做擴充方法實作所有<xref:System.Collections.Generic.IEnumerable%601>型別。</span><span class="sxs-lookup"><span data-stu-id="2512b-114">For example, the `LINQ to Objects` operators are implemented as extension methods for all <xref:System.Collections.Generic.IEnumerable%601> types.</span></span> <span data-ttu-id="2512b-115">因此，任何`IEnumerable<>`實作是自動具備 LINQ 功能。</span><span class="sxs-lookup"><span data-stu-id="2512b-115">Thus, any `IEnumerable<>` implementation is automatically LINQ-enabled.</span></span>  
  
-   <span data-ttu-id="2512b-116">當執行個體方法會導致相依於某些型別，但是這類相依性會中斷相依性管理規則。</span><span class="sxs-lookup"><span data-stu-id="2512b-116">When an instance method would introduce a dependency on some type, but such a dependency would break dependency management rules.</span></span> <span data-ttu-id="2512b-117">相依性，例如，在從<xref:System.String>至<xref:System.Uri?displayProperty=nameWithType>可能不是恰當的，因此`String.ToUri()`傳回的執行個體方法`System.Uri`就是相依性管理的觀點設計錯誤。</span><span class="sxs-lookup"><span data-stu-id="2512b-117">For example, a dependency from <xref:System.String> to <xref:System.Uri?displayProperty=nameWithType> is probably not desirable, and so `String.ToUri()` instance method returning `System.Uri` would be the wrong design from a dependency management perspective.</span></span> <span data-ttu-id="2512b-118">靜態之所以`Uri.ToUri(this string str)`傳回`System.Uri`更好的設計。</span><span class="sxs-lookup"><span data-stu-id="2512b-118">A static extension method `Uri.ToUri(this string str)` returning `System.Uri` would be a much better design.</span></span>  
  
 <span data-ttu-id="2512b-119">**請避免 x**上定義的擴充方法<xref:System.Object?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="2512b-119">**X AVOID** defining extension methods on <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="2512b-120">VB 使用者將無法使用擴充方法語法的物件參考上呼叫這類方法。</span><span class="sxs-lookup"><span data-stu-id="2512b-120">VB users will not be able to call such methods on object references using the extension method syntax.</span></span> <span data-ttu-id="2512b-121">VB 不支援呼叫這類方法，因為在 VB 中，宣告參考，因為物件會強制所有的方法引動過程上是晚期繫結 （名為實際的成員在執行階段決定），而繫結至擴充方法在編譯時期 （及早決定繫結）。</span><span class="sxs-lookup"><span data-stu-id="2512b-121">VB does not support calling such methods because, in VB, declaring a reference as Object forces all method invocations on it to be late bound (actual member called is determined at runtime), while bindings to extension methods are determined at compile-time (early bound).</span></span>  
  
 <span data-ttu-id="2512b-122">請注意在相同的繫結行為是存在，或是不支援擴充方法，指導方針適用於其他語言。</span><span class="sxs-lookup"><span data-stu-id="2512b-122">Note that the guideline applies to other languages where the same binding behavior is present, or where extension methods are not supported.</span></span>  
  
 <span data-ttu-id="2512b-123">**X 不**擴充方法放在相同的命名空間擴充的型別，除非它是用於將方法加入至介面或相依性管理。</span><span class="sxs-lookup"><span data-stu-id="2512b-123">**X DO NOT** put extension methods in the same namespace as the extended type unless it is for adding methods to interfaces or for dependency management.</span></span>  
  
 <span data-ttu-id="2512b-124">**請避免 x**定義兩個或多個使用相同的簽章的擴充方法，即使它們是不同的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="2512b-124">**X AVOID** defining two or more extension methods with the same signature, even if they reside in different namespaces.</span></span>  
  
 <span data-ttu-id="2512b-125">**✓ 考慮**如果類型是介面，並擴充方法的用意是要用於大部分或所有的情況下，擴充的型別相同的命名空間中定義的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="2512b-125">**✓ CONSIDER** defining extension methods in the same namespace as the extended type if the type is an interface and if the extension methods are meant to be used in most or all cases.</span></span>  
  
 <span data-ttu-id="2512b-126">**X 不**定義實作一項功能通常會與其他功能相關聯的命名空間中的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="2512b-126">**X DO NOT** define extension methods implementing a feature in namespaces normally associated with other features.</span></span> <span data-ttu-id="2512b-127">相反地，在其所屬的功能與相關聯的命名空間中進行定義。</span><span class="sxs-lookup"><span data-stu-id="2512b-127">Instead, define them in the namespace associated with the feature they belong to.</span></span>  
  
 <span data-ttu-id="2512b-128">**請避免 x**泛型命名的命名空間專門用來擴充方法 (例如，"Extensions")。</span><span class="sxs-lookup"><span data-stu-id="2512b-128">**X AVOID** generic naming of namespaces dedicated to extension methods (e.g., "Extensions").</span></span> <span data-ttu-id="2512b-129">使用描述性名稱 （例如，「 路由 」） 改為。</span><span class="sxs-lookup"><span data-stu-id="2512b-129">Use a descriptive name (e.g., "Routing") instead.</span></span>  
  
 <span data-ttu-id="2512b-130">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="2512b-130">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="2512b-131">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="2512b-131">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2512b-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2512b-132">See Also</span></span>  
 [<span data-ttu-id="2512b-133">成員設計指導方針</span><span class="sxs-lookup"><span data-stu-id="2512b-133">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="2512b-134">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="2512b-134">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
