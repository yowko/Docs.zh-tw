---
title: 巢狀類型
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- types, nested
- public nested types
- type design guidelines, nested types
- nested types
- members [.NET Framework], type
- class library design guidelines [.NET Framework], nested types
ms.assetid: 12feb7f0-b793-4d96-b090-42d6473bab8c
author: KrzysztofCwalina
ms.openlocfilehash: 22c14d05105154ff642cb8a44eda8e7c5d0575e4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559537"
---
# <a name="nested-types"></a><span data-ttu-id="abc88-102">巢狀類型</span><span class="sxs-lookup"><span data-stu-id="abc88-102">Nested Types</span></span>
<span data-ttu-id="abc88-103">巢狀型別是另一個類型，稱為封入類型的範圍內定義的類型。</span><span class="sxs-lookup"><span data-stu-id="abc88-103">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="abc88-104">巢狀型別可以存取其封入類型的所有成員。</span><span class="sxs-lookup"><span data-stu-id="abc88-104">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="abc88-105">比方說，它必須定義在封入類型，以及受保護的欄位定義中的封入類型的所有上階的私用欄位的存取。</span><span class="sxs-lookup"><span data-stu-id="abc88-105">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>  
  
 <span data-ttu-id="abc88-106">一般情況下，應該謹慎使用巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="abc88-106">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="abc88-107">這有幾個原因。</span><span class="sxs-lookup"><span data-stu-id="abc88-107">There are several reasons for this.</span></span> <span data-ttu-id="abc88-108">有些開發人員並不完全熟悉的概念。</span><span class="sxs-lookup"><span data-stu-id="abc88-108">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="abc88-109">這些開發人員，比方說，可能無法使用巢狀型別的變數的宣告語法。</span><span class="sxs-lookup"><span data-stu-id="abc88-109">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="abc88-110">巢狀型別以及其封入類型，也非常緊密結合，並因此不適用於一般用途的型別。</span><span class="sxs-lookup"><span data-stu-id="abc88-110">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>  
  
 <span data-ttu-id="abc88-111">巢狀型別是最適合用於模型化其封入類型的實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="abc88-111">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="abc88-112">終端使用者應該幾乎不需要宣告巢狀類型的變數，而且幾乎不應該明確具現化巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="abc88-112">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="abc88-113">例如，集合的列舉值可以是該集合的巢狀的類型。</span><span class="sxs-lookup"><span data-stu-id="abc88-113">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="abc88-114">列舉值通常是具現化依其封入類型，因為許多語言支援 foreach 陳述式，列舉值的變數很少需要使用者宣告。</span><span class="sxs-lookup"><span data-stu-id="abc88-114">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>  
  
 <span data-ttu-id="abc88-115">**✓ DO** 時的巢狀的類型和其外部型別之間的關聯性，這類成員存取範圍語法是想要使用巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="abc88-115">**✓ DO** use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>  
  
 <span data-ttu-id="abc88-116">**X DO NOT** 使用公用巢狀型別做為邏輯群組建構，則使用這個命名空間。</span><span class="sxs-lookup"><span data-stu-id="abc88-116">**X DO NOT** use public nested types as a logical grouping construct; use namespaces for this.</span></span>  
  
 <span data-ttu-id="abc88-117">**X AVOID** 公開巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="abc88-117">**X AVOID** publicly exposed nested types.</span></span> <span data-ttu-id="abc88-118">唯一的例外是如果需要宣告只有在罕見的情況下，例如 subclassing 或其他進階的自訂案例的巢狀類型的變數。</span><span class="sxs-lookup"><span data-stu-id="abc88-118">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>  
  
 <span data-ttu-id="abc88-119">**X DO NOT** 可能外部包含型別中參考該類型時，使用巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="abc88-119">**X DO NOT** use nested types if the type is likely to be referenced outside of the containing type.</span></span>  
  
 <span data-ttu-id="abc88-120">例如，傳遞至方法，類別中定義的列舉不應該定義為類別中的巢狀類型。</span><span class="sxs-lookup"><span data-stu-id="abc88-120">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>  
  
 <span data-ttu-id="abc88-121">**X DO NOT** 使用巢狀型別，如果它們必須具現化用戶端程式碼。</span><span class="sxs-lookup"><span data-stu-id="abc88-121">**X DO NOT** use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="abc88-122">如果類型具有公用建構函式，它應該可能不是巢狀。</span><span class="sxs-lookup"><span data-stu-id="abc88-122">If a type has a public constructor, it should probably not be nested.</span></span>  
  
 <span data-ttu-id="abc88-123">如果類型可以具現化，這就好像是指出該類型具有本身的架構中的位置 （您可以建立、 使用，並終結不需使用外部型別），因此應該不是巢狀。</span><span class="sxs-lookup"><span data-stu-id="abc88-123">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="abc88-124">內部的類型應該不能廣泛地重複使用之外沒有任何關聯性的外部型別也為外部型別。</span><span class="sxs-lookup"><span data-stu-id="abc88-124">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>  
  
 <span data-ttu-id="abc88-125">**X DO NOT** 定義巢狀型別為介面的成員。</span><span class="sxs-lookup"><span data-stu-id="abc88-125">**X DO NOT** define a nested type as a member of an interface.</span></span> <span data-ttu-id="abc88-126">許多語言不支援這類建構。</span><span class="sxs-lookup"><span data-stu-id="abc88-126">Many languages do not support such a construct.</span></span>  
  
 <span data-ttu-id="abc88-127">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="abc88-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="abc88-128">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="abc88-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abc88-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="abc88-129">See also</span></span>

- [<span data-ttu-id="abc88-130">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="abc88-130">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="abc88-131">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="abc88-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
