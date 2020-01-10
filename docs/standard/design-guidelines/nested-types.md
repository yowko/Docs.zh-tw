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
ms.openlocfilehash: 3467851aa767efcd0557e8a412cd36316a48b9b0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709149"
---
# <a name="nested-types"></a><span data-ttu-id="4f5aa-102">巢狀類型</span><span class="sxs-lookup"><span data-stu-id="4f5aa-102">Nested Types</span></span>
<span data-ttu-id="4f5aa-103">巢狀型別是在另一個類型的範圍內定義的類型，稱為封入類型。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-103">A nested type is a type defined within the scope of another type, which is called the enclosing type.</span></span> <span data-ttu-id="4f5aa-104">巢狀型別可以存取其封入類型的所有成員。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-104">A nested type has access to all members of its enclosing type.</span></span> <span data-ttu-id="4f5aa-105">例如，它可以存取在封入類型中定義的私用欄位，以及包含在封入類型的所有祖先中所定義的受保護欄位。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-105">For example, it has access to private fields defined in the enclosing type and to protected fields defined in all ascendants of the enclosing type.</span></span>  
  
 <span data-ttu-id="4f5aa-106">一般而言，應該謹慎使用巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-106">In general, nested types should be used sparingly.</span></span> <span data-ttu-id="4f5aa-107">這有幾個原因。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-107">There are several reasons for this.</span></span> <span data-ttu-id="4f5aa-108">有些開發人員並不完全熟悉此概念。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-108">Some developers are not fully familiar with the concept.</span></span> <span data-ttu-id="4f5aa-109">例如，這些開發人員可能會遇到宣告巢狀型別變數的語法問題。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-109">These developers might, for example, have problems with the syntax of declaring variables of nested types.</span></span> <span data-ttu-id="4f5aa-110">巢狀型別也非常緊密結合其封入類型，因此不適合做為一般用途的類型。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-110">Nested types are also very tightly coupled with their enclosing types, and as such are not suited to be general-purpose types.</span></span>  
  
 <span data-ttu-id="4f5aa-111">巢狀型別最適合用來建立其封入類型的模型化執行詳細資料。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-111">Nested types are best suited for modeling implementation details of their enclosing types.</span></span> <span data-ttu-id="4f5aa-112">使用者應該不需要宣告巢狀型別的變數，而且幾乎不應該有明確具現化巢狀型別的情況。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-112">The end user should rarely have to declare variables of a nested type and almost never should have to explicitly instantiate nested types.</span></span> <span data-ttu-id="4f5aa-113">例如，集合的列舉值可以是該集合的巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-113">For example, the enumerator of a collection can be a nested type of that collection.</span></span> <span data-ttu-id="4f5aa-114">列舉值通常是由其封入類型具現化，而且因為許多語言都支援 foreach 語句，所以一般使用者不需要宣告枚舉器變數。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-114">Enumerators are usually instantiated by their enclosing type, and because many languages support the foreach statement, enumerator variables rarely have to be declared by the end user.</span></span>  
  
 <span data-ttu-id="4f5aa-115">當嵌套型別與其外部型別之間的關聯性時， **✓的確**會使用巢狀型別，因此需要成員協助工具的語法。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-115">**✓ DO** use nested types when the relationship between the nested type and its outer type is such that member-accessibility semantics are desirable.</span></span>  
  
 <span data-ttu-id="4f5aa-116">**X 不會**使用公用的巢狀型別做為邏輯群組結構;針對此使用命名空間。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-116">**X DO NOT** use public nested types as a logical grouping construct; use namespaces for this.</span></span>  
  
 <span data-ttu-id="4f5aa-117">**X 避免**公開公開的巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-117">**X AVOID** publicly exposed nested types.</span></span> <span data-ttu-id="4f5aa-118">唯一的例外是，如果嵌套型別的變數只需要在罕見案例（例如子類別化或其他 advanced 自訂案例）中宣告。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-118">The only exception to this is if variables of the nested type need to be declared only in rare scenarios such as subclassing or other advanced customization scenarios.</span></span>  
  
 <span data-ttu-id="4f5aa-119">如果類型可能會在包含類型之外參考，則**X**不會使用巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-119">**X DO NOT** use nested types if the type is likely to be referenced outside of the containing type.</span></span>  
  
 <span data-ttu-id="4f5aa-120">例如，傳遞至在類別上定義之方法的列舉，不應定義為類別中的巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-120">For example, an enum passed to a method defined on a class should not be defined as a nested type in the class.</span></span>  
  
 <span data-ttu-id="4f5aa-121">如果需要由用戶端程式代碼具現化， **X 就不會**使用巢狀型別。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-121">**X DO NOT** use nested types if they need to be instantiated by client code.</span></span>  <span data-ttu-id="4f5aa-122">如果類型具有公用的函式，則可能不會進行嵌套。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-122">If a type has a public constructor, it should probably not be nested.</span></span>  
  
 <span data-ttu-id="4f5aa-123">如果類型可以具現化，似乎表示類型本身在架構中有一個位置（您可以建立它、使用它，並在不使用外部類型的情況下摧毀它），因此不應該進行嵌套。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-123">If a type can be instantiated, that seems to indicate the type has a place in the framework on its own (you can create it, work with it, and destroy it without ever using the outer type), and thus should not be nested.</span></span> <span data-ttu-id="4f5aa-124">內部類型不應廣泛地在外部類型之外重複使用，而不需要與外部類型有任何關聯性。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-124">Inner types should not be widely reused outside of the outer type without any relationship whatsoever to the outer type.</span></span>  
  
 <span data-ttu-id="4f5aa-125">**X 不會**將嵌套型別定義為介面的成員。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-125">**X DO NOT** define a nested type as a member of an interface.</span></span> <span data-ttu-id="4f5aa-126">許多語言都不支援這種結構。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-126">Many languages do not support such a construct.</span></span>  
  
 <span data-ttu-id="4f5aa-127">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="4f5aa-127">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4f5aa-128">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="4f5aa-128">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f5aa-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="4f5aa-129">See also</span></span>

- [<span data-ttu-id="4f5aa-130">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="4f5aa-130">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="4f5aa-131">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="4f5aa-131">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
