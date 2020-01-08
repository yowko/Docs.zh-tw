---
title: 擴充方法
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 5de945cb-88f4-49d7-b0e6-f098300cf357
author: KrzysztofCwalina
ms.openlocfilehash: ad78bae2dc7a3000b67224da6f1a8c578053087f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347024"
---
# <a name="extension-methods"></a><span data-ttu-id="d60c3-102">擴充方法</span><span class="sxs-lookup"><span data-stu-id="d60c3-102">Extension Methods</span></span>
<span data-ttu-id="d60c3-103">擴充方法是一種語言功能，可使用實例方法呼叫語法來呼叫靜態方法。</span><span class="sxs-lookup"><span data-stu-id="d60c3-103">Extension methods are a language feature that allows static methods to be called using instance method call syntax.</span></span> <span data-ttu-id="d60c3-104">這些方法必須採用至少一個參數，其代表方法要運作的實例。</span><span class="sxs-lookup"><span data-stu-id="d60c3-104">These methods must take at least one parameter, which represents the instance the method is to operate on.</span></span>  
  
 <span data-ttu-id="d60c3-105">定義這類擴充方法的類別稱為「贊助商」類別，而且必須宣告為靜態。</span><span class="sxs-lookup"><span data-stu-id="d60c3-105">The class that defines such extension methods is referred to as the "sponsor" class, and it must be declared as static.</span></span> <span data-ttu-id="d60c3-106">若要使用擴充方法，其中一個必須匯入定義贊助者類別的命名空間。</span><span class="sxs-lookup"><span data-stu-id="d60c3-106">To use extension methods, one must import the namespace defining the sponsor class.</span></span>  
  
 <span data-ttu-id="d60c3-107">**X 避免**frivolously 定義擴充方法，特別是在您不擁有的類型上。</span><span class="sxs-lookup"><span data-stu-id="d60c3-107">**X AVOID** frivolously defining extension methods, especially on types you don’t own.</span></span>  
  
 <span data-ttu-id="d60c3-108">如果您擁有類型的原始程式碼，請考慮改為使用一般實例方法。</span><span class="sxs-lookup"><span data-stu-id="d60c3-108">If you do own source code of a type, consider using regular instance methods instead.</span></span> <span data-ttu-id="d60c3-109">如果您不擁有，而且想要新增方法，請務必小心。</span><span class="sxs-lookup"><span data-stu-id="d60c3-109">If you don’t own, and you want to add a method, be very careful.</span></span> <span data-ttu-id="d60c3-110">使用擴充方法時，可能會有雜亂的型別 Api，而這些型別並未設計成具有這些方法。</span><span class="sxs-lookup"><span data-stu-id="d60c3-110">Liberal use of extension methods has the potential of cluttering APIs of types that were not designed to have these methods.</span></span>  
  
 <span data-ttu-id="d60c3-111">**✓請考慮**在下列任何案例中使用擴充方法：</span><span class="sxs-lookup"><span data-stu-id="d60c3-111">**✓ CONSIDER** using extension methods in any of the following scenarios:</span></span>  
  
- <span data-ttu-id="d60c3-112">若要提供與每個介面執行相關的協助程式功能，也可以根據核心介面來撰寫功能。</span><span class="sxs-lookup"><span data-stu-id="d60c3-112">To provide helper functionality relevant to every implementation of an interface, if said functionality can be written in terms of the core interface.</span></span> <span data-ttu-id="d60c3-113">這是因為實體的執行無法以其他方式指派給介面。</span><span class="sxs-lookup"><span data-stu-id="d60c3-113">This is because concrete implementations cannot otherwise be assigned to interfaces.</span></span> <span data-ttu-id="d60c3-114">例如，`LINQ to Objects` 運算子會實作為所有 <xref:System.Collections.Generic.IEnumerable%601> 類型的擴充方法。</span><span class="sxs-lookup"><span data-stu-id="d60c3-114">For example, the `LINQ to Objects` operators are implemented as extension methods for all <xref:System.Collections.Generic.IEnumerable%601> types.</span></span> <span data-ttu-id="d60c3-115">因此，任何 `IEnumerable<>` 的執行都會自動啟用 LINQ。</span><span class="sxs-lookup"><span data-stu-id="d60c3-115">Thus, any `IEnumerable<>` implementation is automatically LINQ-enabled.</span></span>  
  
- <span data-ttu-id="d60c3-116">當實例方法會引進某種類型的相依性，但這類相依性會中斷相依性管理規則。</span><span class="sxs-lookup"><span data-stu-id="d60c3-116">When an instance method would introduce a dependency on some type, but such a dependency would break dependency management rules.</span></span> <span data-ttu-id="d60c3-117">例如，從 <xref:System.String> 到 <xref:System.Uri?displayProperty=nameWithType> 的相依性可能並不理想，因此從相依性管理的觀點來看，傳回 `System.Uri` 的 `String.ToUri()` 實例方法會是錯誤的設計。</span><span class="sxs-lookup"><span data-stu-id="d60c3-117">For example, a dependency from <xref:System.String> to <xref:System.Uri?displayProperty=nameWithType> is probably not desirable, and so `String.ToUri()` instance method returning `System.Uri` would be the wrong design from a dependency management perspective.</span></span> <span data-ttu-id="d60c3-118">靜態擴充方法 `Uri.ToUri(this string str)` 傳回 `System.Uri` 會是更好的設計。</span><span class="sxs-lookup"><span data-stu-id="d60c3-118">A static extension method `Uri.ToUri(this string str)` returning `System.Uri` would be a much better design.</span></span>  
  
 <span data-ttu-id="d60c3-119">**X 避免**在 <xref:System.Object?displayProperty=nameWithType>上定義擴充方法。</span><span class="sxs-lookup"><span data-stu-id="d60c3-119">**X AVOID** defining extension methods on <xref:System.Object?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="d60c3-120">Visual Basic 使用者將無法在使用擴充方法語法的物件參考上呼叫這類方法。</span><span class="sxs-lookup"><span data-stu-id="d60c3-120">Visual Basic users will not be able to call such methods on object references using the extension method syntax.</span></span> <span data-ttu-id="d60c3-121">Visual Basic 不支援呼叫這類方法，因為在 Visual Basic 中，將參考宣告為物件會強制將其上的所有方法調用都設為晚期繫結（呼叫的實際成員是在執行時間決定），而擴充方法的系結則是由編譯時期（早期繫結）。</span><span class="sxs-lookup"><span data-stu-id="d60c3-121">Visual Basic does not support calling such methods because, in Visual Basic, declaring a reference as Object forces all method invocations on it to be late bound (actual member called is determined at runtime), while bindings to extension methods are determined at compile-time (early bound).</span></span>  
  
 <span data-ttu-id="d60c3-122">請注意，本指導方針適用于具有相同系結行為的其他語言，或不支援擴充方法的位置。</span><span class="sxs-lookup"><span data-stu-id="d60c3-122">Note that the guideline applies to other languages where the same binding behavior is present, or where extension methods are not supported.</span></span>  
  
 <span data-ttu-id="d60c3-123">**X**不會將擴充方法放在與延伸類型相同的命名空間中，除非它是用來將方法加入介面或用於相依性管理。</span><span class="sxs-lookup"><span data-stu-id="d60c3-123">**X DO NOT** put extension methods in the same namespace as the extended type unless it is for adding methods to interfaces or for dependency management.</span></span>  
  
 <span data-ttu-id="d60c3-124">**X 避免**定義兩個或多個具有相同簽章的擴充方法，即使它們位於不同的命名空間也一樣。</span><span class="sxs-lookup"><span data-stu-id="d60c3-124">**X AVOID** defining two or more extension methods with the same signature, even if they reside in different namespaces.</span></span>  
  
 <span data-ttu-id="d60c3-125">如果類型為介面，而且如果擴充方法要用於大部分或所有案例， **✓請考慮**在與延伸類型相同的命名空間中定義擴充方法。</span><span class="sxs-lookup"><span data-stu-id="d60c3-125">**✓ CONSIDER** defining extension methods in the same namespace as the extended type if the type is an interface and if the extension methods are meant to be used in most or all cases.</span></span>  
  
 <span data-ttu-id="d60c3-126">**X 不會**定義在命名空間中執行功能的擴充方法，通常與其他功能相關聯。</span><span class="sxs-lookup"><span data-stu-id="d60c3-126">**X DO NOT** define extension methods implementing a feature in namespaces normally associated with other features.</span></span> <span data-ttu-id="d60c3-127">相反地，請在與它們所屬的功能相關聯的命名空間中定義它們。</span><span class="sxs-lookup"><span data-stu-id="d60c3-127">Instead, define them in the namespace associated with the feature they belong to.</span></span>  
  
 <span data-ttu-id="d60c3-128">**X 避免**針對擴充方法（例如「延伸模組」）專用的命名空間進行一般命名。</span><span class="sxs-lookup"><span data-stu-id="d60c3-128">**X AVOID** generic naming of namespaces dedicated to extension methods (e.g., "Extensions").</span></span> <span data-ttu-id="d60c3-129">請改用描述性名稱（例如「路由」）。</span><span class="sxs-lookup"><span data-stu-id="d60c3-129">Use a descriptive name (e.g., "Routing") instead.</span></span>  
  
 <span data-ttu-id="d60c3-130">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="d60c3-130">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d60c3-131">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="d60c3-131">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d60c3-132">請參閱</span><span class="sxs-lookup"><span data-stu-id="d60c3-132">See also</span></span>

- [<span data-ttu-id="d60c3-133">成員設計方針</span><span class="sxs-lookup"><span data-stu-id="d60c3-133">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="d60c3-134">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="d60c3-134">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
