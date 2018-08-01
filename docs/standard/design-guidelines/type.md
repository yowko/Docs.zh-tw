---
title: 類型設計方針
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines
- type design guidelines, about type design guidelines
- class library design guidelines [.NET Framework], type design guidelines
- types [.NET Framework], design guidelines
ms.assetid: 6b49314e-8bba-43ea-97ca-4e0255812f95
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af7511f4159fdbfe2d3f972dc927e9ee11fd586f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572885"
---
# <a name="type-design-guidelines"></a><span data-ttu-id="43fc8-102">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="43fc8-102">Type Design Guidelines</span></span>
<span data-ttu-id="43fc8-103">CLR 觀點中，有類型只有兩個類別，參考類型和實值類型 — 但架構設計的相關討論，為了分割類型分成多個邏輯群組，每個都有它自己的特定設計規則。</span><span class="sxs-lookup"><span data-stu-id="43fc8-103">From the CLR perspective, there are only two categories of types—reference types and value types—but for the purpose of a discussion about framework design, we divide types into more logical groups, each with its own specific design rules.</span></span>  
  
 <span data-ttu-id="43fc8-104">類別是參考類型的一般情況。</span><span class="sxs-lookup"><span data-stu-id="43fc8-104">Classes are the general case of reference types.</span></span> <span data-ttu-id="43fc8-105">它們會構成大量大部分的架構中的型別。</span><span class="sxs-lookup"><span data-stu-id="43fc8-105">They make up the bulk of types in the majority of frameworks.</span></span> <span data-ttu-id="43fc8-106">類別在其支援的物件導向的功能集的豐富和一般適用性年末其受歡迎情況看出。</span><span class="sxs-lookup"><span data-stu-id="43fc8-106">Classes owe their popularity to the rich set of object-oriented features they support and to their general applicability.</span></span> <span data-ttu-id="43fc8-107">基底類別和抽象類別是特殊的邏輯群組與擴充性。</span><span class="sxs-lookup"><span data-stu-id="43fc8-107">Base classes and abstract classes are special logical groups related to extensibility.</span></span>  
  
 <span data-ttu-id="43fc8-108">介面是由參考類型和實值類型可以實作的類型。</span><span class="sxs-lookup"><span data-stu-id="43fc8-108">Interfaces are types that can be implemented by both reference types and value types.</span></span> <span data-ttu-id="43fc8-109">它們可因此做為參考類型和實值型別多型階層的根目錄。</span><span class="sxs-lookup"><span data-stu-id="43fc8-109">They can thus serve as roots of polymorphic hierarchies of reference types and value types.</span></span> <span data-ttu-id="43fc8-110">此外，介面可以用來模擬原生不支援由 CLR 中的多重繼承。</span><span class="sxs-lookup"><span data-stu-id="43fc8-110">In addition, interfaces can be used to simulate multiple inheritance, which is not natively supported by the CLR.</span></span>  
  
 <span data-ttu-id="43fc8-111">結構是實值類型的一般情況下，以及應該保留小型、 簡單類型，類似於語言基本類型。</span><span class="sxs-lookup"><span data-stu-id="43fc8-111">Structs are the general case of value types and should be reserved for small, simple types, similar to language primitives.</span></span>  
  
 <span data-ttu-id="43fc8-112">列舉是用來定義簡短組值，例如週、 的主控台色彩等等的天的實值類型的特殊案例。</span><span class="sxs-lookup"><span data-stu-id="43fc8-112">Enums are a special case of value types used to define short sets of values, such as days of the week, console colors, and so on.</span></span>  
  
 <span data-ttu-id="43fc8-113">靜態類別是要作為容器使用的靜態成員的型別。</span><span class="sxs-lookup"><span data-stu-id="43fc8-113">Static classes are types intended to be containers for static members.</span></span> <span data-ttu-id="43fc8-114">它們通常用於提供其他作業的捷徑。</span><span class="sxs-lookup"><span data-stu-id="43fc8-114">They are commonly used to provide shortcuts to other operations.</span></span>  
  
 <span data-ttu-id="43fc8-115">委派、 例外狀況、 屬性、 陣列和集合的參考型別適用於特定用途，所有的特殊情況下，而且這個活頁簿中已於他處討論設計和使用方式的指導方針。</span><span class="sxs-lookup"><span data-stu-id="43fc8-115">Delegates, exceptions, attributes, arrays, and collections are all special cases of reference types intended for specific uses, and guidelines for their design and usage are discussed elsewhere in this book.</span></span>  
  
 <span data-ttu-id="43fc8-116">**✓ DO**確保每個類型的一組妥善定義之相關成員，不只是隨機的不相關的功能集合。</span><span class="sxs-lookup"><span data-stu-id="43fc8-116">**✓ DO** ensure that each type is a well-defined set of related members, not just a random collection of unrelated functionality.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="43fc8-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="43fc8-117">In This Section</span></span>  
 [<span data-ttu-id="43fc8-118">在類別和結構之間選擇</span><span class="sxs-lookup"><span data-stu-id="43fc8-118">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)  
 [<span data-ttu-id="43fc8-119">抽象類別設計</span><span class="sxs-lookup"><span data-stu-id="43fc8-119">Abstract Class Design</span></span>](../../../docs/standard/design-guidelines/abstract-class.md)  
 [<span data-ttu-id="43fc8-120">靜態類別設計</span><span class="sxs-lookup"><span data-stu-id="43fc8-120">Static Class Design</span></span>](../../../docs/standard/design-guidelines/static-class.md)  
 [<span data-ttu-id="43fc8-121">介面設計</span><span class="sxs-lookup"><span data-stu-id="43fc8-121">Interface Design</span></span>](../../../docs/standard/design-guidelines/interface.md)  
 [<span data-ttu-id="43fc8-122">結構設計</span><span class="sxs-lookup"><span data-stu-id="43fc8-122">Struct Design</span></span>](../../../docs/standard/design-guidelines/struct.md)  
 [<span data-ttu-id="43fc8-123">列舉設計</span><span class="sxs-lookup"><span data-stu-id="43fc8-123">Enum Design</span></span>](../../../docs/standard/design-guidelines/enum.md)  
 [<span data-ttu-id="43fc8-124">巢狀型別</span><span class="sxs-lookup"><span data-stu-id="43fc8-124">Nested Types</span></span>](../../../docs/standard/design-guidelines/nested-types.md)  
 <span data-ttu-id="43fc8-125">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="43fc8-125">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="43fc8-126">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="43fc8-126">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43fc8-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43fc8-127">See Also</span></span>  
 [<span data-ttu-id="43fc8-128">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="43fc8-128">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
