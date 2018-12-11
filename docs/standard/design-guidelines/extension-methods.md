---
title: 擴充方法
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
author: KrzysztofCwalina
ms.openlocfilehash: 6fedd41e901035290995d7ece1b5aa23e76f345e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148286"
---
# <a name="extension-methods"></a><span data-ttu-id="755b2-102">擴充方法</span><span class="sxs-lookup"><span data-stu-id="755b2-102">Extension Methods</span></span>
<span data-ttu-id="755b2-103">擴充方法是允許使用執行個體方法呼叫語法來呼叫靜態方法的語言功能。</span><span class="sxs-lookup"><span data-stu-id="755b2-103">Extension methods are a language feature that allows static methods to be called using instance method call syntax.</span></span> <span data-ttu-id="755b2-104">這些方法必須接受至少一個參數，表示要對方法的執行個體。</span><span class="sxs-lookup"><span data-stu-id="755b2-104">These methods must take at least one parameter, which represents the instance the method is to operate on.</span></span>  
  
 <span data-ttu-id="755b2-105">定義這類的擴充方法的類別稱為 「 贊助商 」 類別，它必須宣告為靜態。</span><span class="sxs-lookup"><span data-stu-id="755b2-105">The class that defines such extension methods is referred to as the "sponsor" class, and it must be declared as static.</span></span> <span data-ttu-id="755b2-106">若要使用擴充方法，其中必須匯入定義 「 贊助商 」 類別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="755b2-106">To use extension methods, one must import the namespace defining the sponsor class.</span></span>  
  
 <span data-ttu-id="755b2-107">**X AVOID** frivolously 特別是在不屬於您的型別上定義擴充方法。</span><span class="sxs-lookup"><span data-stu-id="755b2-107">**X AVOID** frivolously defining extension methods, especially on types you don’t own.</span></span>  
  
 <span data-ttu-id="755b2-108">如果您擁有類型的原始程式碼，請考慮改為使用一般的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="755b2-108">If you do own source code of a type, consider using regular instance methods instead.</span></span> <span data-ttu-id="755b2-109">如果不屬於您，而且您想要新增的方法，要非常小心。</span><span class="sxs-lookup"><span data-stu-id="755b2-109">If you don’t own, and you want to add a method, be very careful.</span></span> <span data-ttu-id="755b2-110">自由使用擴充方法有可能會想堆 Api，都不會有這些方法的類型。</span><span class="sxs-lookup"><span data-stu-id="755b2-110">Liberal use of extension methods has the potential of cluttering APIs of types that were not designed to have these methods.</span></span>  
  
 <span data-ttu-id="755b2-111">**✓ CONSIDER** 任何下列案例中使用擴充方法：</span><span class="sxs-lookup"><span data-stu-id="755b2-111">**✓ CONSIDER** using extension methods in any of the following scenarios:</span></span>  
  
-   <span data-ttu-id="755b2-112">若要提供協助程式功能如果說功能相關的介面，每個實作都可以撰寫方面的核心介面。</span><span class="sxs-lookup"><span data-stu-id="755b2-112">To provide helper functionality relevant to every implementation of an interface, if said functionality can be written in terms of the core interface.</span></span> <span data-ttu-id="755b2-113">這是因為具象實作否則無法指派給介面。</span><span class="sxs-lookup"><span data-stu-id="755b2-113">This is because concrete implementations cannot otherwise be assigned to interfaces.</span></span> <span data-ttu-id="755b2-114">例如，`LINQ to Objects`運算子時，會實作為擴充方法上，所有<xref:System.Collections.Generic.IEnumerable%601>型別。</span><span class="sxs-lookup"><span data-stu-id="755b2-114">For example, the `LINQ to Objects` operators are implemented as extension methods for all <xref:System.Collections.Generic.IEnumerable%601> types.</span></span> <span data-ttu-id="755b2-115">因此，任何`IEnumerable<>`實作是自動啟用 LINQ。</span><span class="sxs-lookup"><span data-stu-id="755b2-115">Thus, any `IEnumerable<>` implementation is automatically LINQ-enabled.</span></span>  
  
-   <span data-ttu-id="755b2-116">當執行個體方法會產生某種類型的相依性，但這類相依性會中斷相依性管理規則。</span><span class="sxs-lookup"><span data-stu-id="755b2-116">When an instance method would introduce a dependency on some type, but such a dependency would break dependency management rules.</span></span> <span data-ttu-id="755b2-117">比方說，從相依性<xref:System.String>要<xref:System.Uri?displayProperty=nameWithType>不可能需要這樣做，，因此`String.ToUri()`傳回的執行個體方法`System.Uri`會從相依性管理的觀點而言錯誤的設計。</span><span class="sxs-lookup"><span data-stu-id="755b2-117">For example, a dependency from <xref:System.String> to <xref:System.Uri?displayProperty=nameWithType> is probably not desirable, and so `String.ToUri()` instance method returning `System.Uri` would be the wrong design from a dependency management perspective.</span></span> <span data-ttu-id="755b2-118">靜態擴充方法`Uri.ToUri(this string str)`傳回`System.Uri`會是更好的設計。</span><span class="sxs-lookup"><span data-stu-id="755b2-118">A static extension method `Uri.ToUri(this string str)` returning `System.Uri` would be a much better design.</span></span>  
  
 <span data-ttu-id="755b2-119">**X AVOID** 上定義的擴充方法 <xref:System.Object?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="755b2-119">**X AVOID** defining extension methods on <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="755b2-120">VB 使用者將無法使用擴充方法語法的物件參考上呼叫這類方法。</span><span class="sxs-lookup"><span data-stu-id="755b2-120">VB users will not be able to call such methods on object references using the extension method syntax.</span></span> <span data-ttu-id="755b2-121">VB 不支援呼叫這類方法，因為，在 VB 中，宣告為參考，為物件會強制所有的方法引動過程上才會晚期繫結 （名為的實際成員在執行階段決定），而繫結到擴充方法在編譯時間 （早期決定繫結）。</span><span class="sxs-lookup"><span data-stu-id="755b2-121">VB does not support calling such methods because, in VB, declaring a reference as Object forces all method invocations on it to be late bound (actual member called is determined at runtime), while bindings to extension methods are determined at compile-time (early bound).</span></span>  
  
 <span data-ttu-id="755b2-122">請注意指導方針適用於相同的繫結行為所在的其他語言，或不支援的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="755b2-122">Note that the guideline applies to other languages where the same binding behavior is present, or where extension methods are not supported.</span></span>  
  
 <span data-ttu-id="755b2-123">**X DO NOT** 擴充方法放在相同的命名空間擴充的型別，除非它是用於將方法加入至介面或相依性管理。</span><span class="sxs-lookup"><span data-stu-id="755b2-123">**X DO NOT** put extension methods in the same namespace as the extended type unless it is for adding methods to interfaces or for dependency management.</span></span>  
  
 <span data-ttu-id="755b2-124">**X AVOID** 定義兩個或多個使用相同的簽章的擴充方法，即使它們是不同的命名空間中。</span><span class="sxs-lookup"><span data-stu-id="755b2-124">**X AVOID** defining two or more extension methods with the same signature, even if they reside in different namespaces.</span></span>  
  
 <span data-ttu-id="755b2-125">**✓ CONSIDER** 如果類型是介面，並擴充方法的用意是要用於大部分或所有的情況下，擴充的型別相同的命名空間中定義的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="755b2-125">**✓ CONSIDER** defining extension methods in the same namespace as the extended type if the type is an interface and if the extension methods are meant to be used in most or all cases.</span></span>  
  
 <span data-ttu-id="755b2-126">**X DO NOT** 定義實作一項功能通常會與其他功能相關聯的命名空間中的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="755b2-126">**X DO NOT** define extension methods implementing a feature in namespaces normally associated with other features.</span></span> <span data-ttu-id="755b2-127">相反地，在其所屬的功能與相關聯的命名空間中定義它們。</span><span class="sxs-lookup"><span data-stu-id="755b2-127">Instead, define them in the namespace associated with the feature they belong to.</span></span>  
  
 <span data-ttu-id="755b2-128">**X AVOID** 泛型命名的命名空間專門用來擴充方法 (例如，"Extensions")。</span><span class="sxs-lookup"><span data-stu-id="755b2-128">**X AVOID** generic naming of namespaces dedicated to extension methods (e.g., "Extensions").</span></span> <span data-ttu-id="755b2-129">使用描述性名稱 （例如，「 路由 」） 改為。</span><span class="sxs-lookup"><span data-stu-id="755b2-129">Use a descriptive name (e.g., "Routing") instead.</span></span>  
  
 <span data-ttu-id="755b2-130">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="755b2-130">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="755b2-131">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="755b2-131">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="755b2-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="755b2-132">See also</span></span>

- [<span data-ttu-id="755b2-133">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="755b2-133">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
- [<span data-ttu-id="755b2-134">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="755b2-134">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
