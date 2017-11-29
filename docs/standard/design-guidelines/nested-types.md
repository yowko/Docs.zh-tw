---
title: "巢狀類型"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0ae09df49b97cc2fe84285c3a37e1562da185f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="nested-types"></a><span data-ttu-id="44af8-102">巢狀類型</span><span class="sxs-lookup"><span data-stu-id="44af8-102">Nested Types</span></span>
<span data-ttu-id="44af8-103">巢狀型別是另一個類型，稱為封入類型的範圍內定義的類型。</span><span class="sxs-lookup"><span data-stu-id="44af8-103">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="44af8-104">巢狀型別可以存取其封入類型的所有成員。</span><span class="sxs-lookup"><span data-stu-id="44af8-104">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="44af8-105">例如，具有存取權給定義在封入類型，以及受保護的定義中封入類型的所有上階欄位的私用欄位。</span><span class="sxs-lookup"><span data-stu-id="44af8-105">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>  
  
 <span data-ttu-id="44af8-106">一般情況下，就應該謹慎巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="44af8-106">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="44af8-107">這有幾個原因。</span><span class="sxs-lookup"><span data-stu-id="44af8-107">There are several reasons for this.</span></span> <span data-ttu-id="44af8-108">有些開發人員並不完全熟悉概念。</span><span class="sxs-lookup"><span data-stu-id="44af8-108">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="44af8-109">這些開發人員可能會比方說，有巢狀類型的變數的宣告語法問題。</span><span class="sxs-lookup"><span data-stu-id="44af8-109">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="44af8-110">巢狀型別也非常緊密結合其封入類型，並在這種情況不適合一般用途的型別。</span><span class="sxs-lookup"><span data-stu-id="44af8-110">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>  
  
 <span data-ttu-id="44af8-111">巢狀型別是最適合用來建立模型及其封入類型的實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="44af8-111">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="44af8-112">終端使用者應該很少需要宣告巢狀類型的變數，而幾乎永遠都不應該需要明確具現化巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="44af8-112">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="44af8-113">例如，集合的列舉值可以是該集合的巢狀的類型。</span><span class="sxs-lookup"><span data-stu-id="44af8-113">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="44af8-114">通常會依其封入類型具現化列舉值，因為許多語言都支援 foreach 陳述式，列舉值的變數很少需要使用者宣告。</span><span class="sxs-lookup"><span data-stu-id="44af8-114">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>  
  
 <span data-ttu-id="44af8-115">**✓ 不要**時的巢狀的類型和其外部型別之間的關聯性，這類成員存取範圍語法是想要使用巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="44af8-115">**✓ DO** use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>  
  
 <span data-ttu-id="44af8-116">**X 不**使用公用巢狀型別做為邏輯群組建構，則使用這個命名空間。</span><span class="sxs-lookup"><span data-stu-id="44af8-116">**X DO NOT** use public nested types as a logical grouping construct; use namespaces for this.</span></span>  
  
 <span data-ttu-id="44af8-117">**請避免 x**公開巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="44af8-117">**X AVOID** publicly exposed nested types.</span></span> <span data-ttu-id="44af8-118">唯一的例外是如果需要宣告只有在極少數的情況下，例如 subclassing 或其他進階的自訂案例的巢狀類型的變數。</span><span class="sxs-lookup"><span data-stu-id="44af8-118">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>  
  
 <span data-ttu-id="44af8-119">**X 不**可能外部包含型別中參考該類型時，使用巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="44af8-119">**X DO NOT** use nested types if the type is likely to be referenced outside of the containing type.</span></span>  
  
 <span data-ttu-id="44af8-120">例如，傳遞至方法，在類別定義列舉不應定義為類別中的巢狀類型。</span><span class="sxs-lookup"><span data-stu-id="44af8-120">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>  
  
 <span data-ttu-id="44af8-121">**X 不**使用巢狀型別，如果它們必須具現化用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="44af8-121">**X DO NOT** use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="44af8-122">如果類型具有公用建構函式，它應該可能不是巢狀。</span><span class="sxs-lookup"><span data-stu-id="44af8-122">If a type has a public constructor, it should probably not be nested.</span></span>  
  
 <span data-ttu-id="44af8-123">如果型別可以具現化，這好像來表示型別具有自己的架構中的位置 （您可以建立、 使用它，和摧毀不需使用外部型別），因此應該不巢狀。</span><span class="sxs-lookup"><span data-stu-id="44af8-123">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="44af8-124">內部的類型應該不能廣泛地重複使用外部型別，如果沒有任何關聯性外部擔保外部型別。</span><span class="sxs-lookup"><span data-stu-id="44af8-124">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>  
  
 <span data-ttu-id="44af8-125">**X 不**定義巢狀型別為介面的成員。</span><span class="sxs-lookup"><span data-stu-id="44af8-125">**X DO NOT** define a nested type as a member of an interface.</span></span> <span data-ttu-id="44af8-126">許多語言不支援這類建構。</span><span class="sxs-lookup"><span data-stu-id="44af8-126">Many languages do not support such a construct.</span></span>  
  
 <span data-ttu-id="44af8-127">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="44af8-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="44af8-128">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="44af8-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44af8-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44af8-129">See Also</span></span>  
 [<span data-ttu-id="44af8-130">型別設計指導方針</span><span class="sxs-lookup"><span data-stu-id="44af8-130">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="44af8-131">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="44af8-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
