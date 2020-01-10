---
title: 類型設計方針
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: 3e2fe7168bd0029d8f0e8f69a136c9089032973f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709019"
---
# <a name="type-design-guidelines"></a><span data-ttu-id="4da9d-102">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="4da9d-102">Type Design Guidelines</span></span>
<span data-ttu-id="4da9d-103">從 CLR 的觀點來看，只有兩種類別的類型（參考型別和實數值型別），但針對架構設計的討論，我們會將類型分成更多的邏輯群組，每個都有自己的特定設計規則。</span><span class="sxs-lookup"><span data-stu-id="4da9d-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>  
  
 <span data-ttu-id="4da9d-104">類別是參考型別的一般案例。</span><span class="sxs-lookup"><span data-stu-id="4da9d-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="4da9d-105">它們會構成大部分架構中的大量類型。</span><span class="sxs-lookup"><span data-stu-id="4da9d-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="4da9d-106">類別對於其支援的一組豐富物件導向功能，以及其一般適用性，都欠其最熱門。</span><span class="sxs-lookup"><span data-stu-id="4da9d-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="4da9d-107">基類和抽象類別是與擴充性相關的特殊邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="4da9d-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>  
  
 <span data-ttu-id="4da9d-108">介面是可同時由參考型別和實數值型別來執行的類型。</span><span class="sxs-lookup"><span data-stu-id="4da9d-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="4da9d-109">因此，它們可以當做參考型別和實數值型別之多型階層的根。</span><span class="sxs-lookup"><span data-stu-id="4da9d-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="4da9d-110">此外，介面可以用來模擬多重繼承，CLR 原本並不支援。</span><span class="sxs-lookup"><span data-stu-id="4da9d-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>  
  
 <span data-ttu-id="4da9d-111">結構是實值型別的一般案例，應保留給小型的簡單型別，類似于語言基本類型。</span><span class="sxs-lookup"><span data-stu-id="4da9d-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>  
  
 <span data-ttu-id="4da9d-112">列舉是實數值型別的特殊案例，用來定義一組簡短的值，例如一周中的天數、主控台色彩等等。</span><span class="sxs-lookup"><span data-stu-id="4da9d-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>  
  
 <span data-ttu-id="4da9d-113">靜態類別是要作為靜態成員容器的類型。</span><span class="sxs-lookup"><span data-stu-id="4da9d-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="4da9d-114">它們通常用來提供其他作業的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="4da9d-114">They are commonly used to provide shortcuts to other operations.</span></span>  
  
 <span data-ttu-id="4da9d-115">委派、例外狀況、屬性、陣列和集合都是適用于特定用途之參考型別的特殊案例，而在本書的其他地方會討論其設計和使用方式的指導方針。</span><span class="sxs-lookup"><span data-stu-id="4da9d-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>  
  
 <span data-ttu-id="4da9d-116">**✓確實**確保每一種類型都是一組定義完善的相關成員，而不只是隨機收集不相關的功能。</span><span class="sxs-lookup"><span data-stu-id="4da9d-116">**✓ DO** ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4da9d-117">本章節內容</span><span class="sxs-lookup"><span data-stu-id="4da9d-117">In This Section</span></span>  
 [<span data-ttu-id="4da9d-118">在類別和結構之間選擇</span><span class="sxs-lookup"><span data-stu-id="4da9d-118">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [<span data-ttu-id="4da9d-119">抽象類別設計</span><span class="sxs-lookup"><span data-stu-id="4da9d-119">Abstract Class Design</span></span>](../../../docs/standard/design-guidelines/abstract-class.md)  
 [<span data-ttu-id="4da9d-120">靜態類別設計</span><span class="sxs-lookup"><span data-stu-id="4da9d-120">Static Class Design</span></span>](../../../docs/standard/design-guidelines/static-class.md)  
 [<span data-ttu-id="4da9d-121">介面設計</span><span class="sxs-lookup"><span data-stu-id="4da9d-121">Interface Design</span></span>](../../../docs/standard/design-guidelines/interface.md)  
 [<span data-ttu-id="4da9d-122">結構設計</span><span class="sxs-lookup"><span data-stu-id="4da9d-122">Struct Design</span></span>](../../../docs/standard/design-guidelines/struct.md)  
 [<span data-ttu-id="4da9d-123">列舉設計</span><span class="sxs-lookup"><span data-stu-id="4da9d-123">Enum Design</span></span>](../../../docs/standard/design-guidelines/enum.md)  
 [<span data-ttu-id="4da9d-124">巢狀型別</span><span class="sxs-lookup"><span data-stu-id="4da9d-124">Nested Types</span></span>](../../../docs/standard/design-guidelines/nested-types.md)  
 <span data-ttu-id="4da9d-125">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="4da9d-125">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="4da9d-126">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="4da9d-126">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4da9d-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="4da9d-127">See also</span></span>

- [<span data-ttu-id="4da9d-128">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="4da9d-128">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
