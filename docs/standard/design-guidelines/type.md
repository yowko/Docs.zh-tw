---
title: 類型設計方針
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
ms.openlocfilehash: a20744f76433ff12456967e4d41d9a13b6f5d46c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677527"
---
# <a name="type-design-guidelines"></a><span data-ttu-id="86ea5-102">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="86ea5-102">Type Design Guidelines</span></span>

<span data-ttu-id="86ea5-103">從 CLR 的觀點來看，只有兩種類別的型別（參考型別和實值型別），但為了討論架構設計，我們將類型分成更多邏輯群組，每個都有自己的特定設計規則。</span><span class="sxs-lookup"><span data-stu-id="86ea5-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>

 <span data-ttu-id="86ea5-104">類別是參考型別的一般案例。</span><span class="sxs-lookup"><span data-stu-id="86ea5-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="86ea5-105">它們會構成大部分架構中的大量類型。</span><span class="sxs-lookup"><span data-stu-id="86ea5-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="86ea5-106">類別會對其支援的一組豐富的物件導向功能，以及其一般適用性，提供其最普及的程度。</span><span class="sxs-lookup"><span data-stu-id="86ea5-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="86ea5-107">基類和抽象類別是與擴充性相關的特殊邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="86ea5-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>

 <span data-ttu-id="86ea5-108">介面是可由參考型別和實值型別實作為的型別。</span><span class="sxs-lookup"><span data-stu-id="86ea5-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="86ea5-109">因此，它們可以作為參考型別和實數值型別之多型階層的根。</span><span class="sxs-lookup"><span data-stu-id="86ea5-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="86ea5-110">此外，介面可以用來模擬多個繼承，CLR 本身並不支援。</span><span class="sxs-lookup"><span data-stu-id="86ea5-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>

 <span data-ttu-id="86ea5-111">結構是實值型別的一般案例，應該保留給小型的簡單型別，類似于語言基本類型。</span><span class="sxs-lookup"><span data-stu-id="86ea5-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>

 <span data-ttu-id="86ea5-112">列舉是實數值型別的特殊案例，用來定義簡短的值集，例如星期幾、主控台色彩等等。</span><span class="sxs-lookup"><span data-stu-id="86ea5-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>

 <span data-ttu-id="86ea5-113">靜態類別是要作為靜態成員容器的類型。</span><span class="sxs-lookup"><span data-stu-id="86ea5-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="86ea5-114">它們通常用來提供其他作業的快捷方式。</span><span class="sxs-lookup"><span data-stu-id="86ea5-114">They are commonly used to provide shortcuts to other operations.</span></span>

 <span data-ttu-id="86ea5-115">委派、例外狀況、屬性、陣列和集合都是適用于特定用途之參考型別的特殊案例，而其設計和使用方式的指導方針會在本書的其他地方討論。</span><span class="sxs-lookup"><span data-stu-id="86ea5-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>

 <span data-ttu-id="86ea5-116">✔️確定每個類型都是一組定義完善的相關成員，而不只是隨機的不相關功能集合。</span><span class="sxs-lookup"><span data-stu-id="86ea5-116">✔️ DO ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="86ea5-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="86ea5-117">In This Section</span></span>

 <span data-ttu-id="86ea5-118">[在類別和結構](choosing-between-class-and-struct.md)[抽象類別](abstract-class.md)之間進行選擇設計 [靜態類別設計](static-class.md)[介面設計](interface.md)[結構設計結構](struct.md)設計 [列舉設計](enum.md)[巢狀型別](nested-types.md)*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="86ea5-118">[Choosing Between Class and Struct](choosing-between-class-and-struct.md) [Abstract Class Design](abstract-class.md) [Static Class Design](static-class.md) [Interface Design](interface.md) [Struct Design](struct.md) [Enum Design](enum.md) [Nested Types](nested-types.md) *Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="86ea5-119">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="86ea5-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="86ea5-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="86ea5-120">See also</span></span>

- [<span data-ttu-id="86ea5-121">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="86ea5-121">Framework Design Guidelines</span></span>](index.md)
