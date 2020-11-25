---
title: 結構設計
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: 7bb7e63004df2eb7541ba8d4f1118ea2272db126
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730899"
---
# <a name="struct-design"></a><span data-ttu-id="8911a-102">結構設計</span><span class="sxs-lookup"><span data-stu-id="8911a-102">Struct Design</span></span>

<span data-ttu-id="8911a-103">一般用途的實值型別通常稱為結構，也就是它的 c # 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="8911a-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="8911a-104">本節提供一般結構設計的指導方針。</span><span class="sxs-lookup"><span data-stu-id="8911a-104">This section provides guidelines for general struct design.</span></span>

 <span data-ttu-id="8911a-105">❌ 請勿為結構提供無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="8911a-105">❌ DO NOT provide a parameterless constructor for a struct.</span></span>

 <span data-ttu-id="8911a-106">遵循此指導方針可建立結構陣列，而不需要在陣列的每個專案上執行此函式。</span><span class="sxs-lookup"><span data-stu-id="8911a-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="8911a-107">請注意，c # 不允許結構具有無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="8911a-107">Notice that C# does not allow structs to have parameterless constructors.</span></span>

 <span data-ttu-id="8911a-108">❌ 請勿定義可變實數值型別。</span><span class="sxs-lookup"><span data-stu-id="8911a-108">❌ DO NOT define mutable value types.</span></span>

 <span data-ttu-id="8911a-109">可變實值型別有幾個問題。</span><span class="sxs-lookup"><span data-stu-id="8911a-109">Mutable value types have several problems.</span></span> <span data-ttu-id="8911a-110">例如，當屬性 getter 傳回實值型別時，呼叫端會收到一份複本。</span><span class="sxs-lookup"><span data-stu-id="8911a-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="8911a-111">由於複本是以隱含方式建立的，因此開發人員可能不知道它們會改變複本，而不是原始值。</span><span class="sxs-lookup"><span data-stu-id="8911a-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="8911a-112">此外，某些語言 (動態語言，特別是) 在使用可變實值型別時遇到問題，因為即使是本機變數，當取值時，也會產生複製。</span><span class="sxs-lookup"><span data-stu-id="8911a-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>

 <span data-ttu-id="8911a-113">✔️確定所有實例資料都設定為零、false 或 null (適當的) 有效的狀態。</span><span class="sxs-lookup"><span data-stu-id="8911a-113">✔️ DO ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>

 <span data-ttu-id="8911a-114">這可防止在建立結構陣列時，意外建立不正確實例。</span><span class="sxs-lookup"><span data-stu-id="8911a-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>

 <span data-ttu-id="8911a-115">✔️在實 <xref:System.IEquatable%601> 值型別上執行。</span><span class="sxs-lookup"><span data-stu-id="8911a-115">✔️ DO implement <xref:System.IEquatable%601> on value types.</span></span>

 <span data-ttu-id="8911a-116"><xref:System.Object.Equals%2A?displayProperty=nameWithType>實值型別上的方法會造成裝箱，而其預設實並不太有效率，因為它會使用反映。</span><span class="sxs-lookup"><span data-stu-id="8911a-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="8911a-117"><xref:System.IEquatable%601.Equals%2A> 可以有更好的效能，並可進行實作為，使其不會導致裝箱。</span><span class="sxs-lookup"><span data-stu-id="8911a-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>

 <span data-ttu-id="8911a-118">❌ 請勿明確擴充 <xref:System.ValueType> 。</span><span class="sxs-lookup"><span data-stu-id="8911a-118">❌ DO NOT explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="8911a-119">事實上，大部分的語言都能防止這種情況。</span><span class="sxs-lookup"><span data-stu-id="8911a-119">In fact, most languages prevent this.</span></span>

 <span data-ttu-id="8911a-120">一般而言，結構可能很有用，但僅適用于不會經常被裝箱的小型、單一且不可變的值。</span><span class="sxs-lookup"><span data-stu-id="8911a-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>

 <span data-ttu-id="8911a-121">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="8911a-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="8911a-122">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="8911a-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="8911a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8911a-123">See also</span></span>

- [<span data-ttu-id="8911a-124">型別設計方針</span><span class="sxs-lookup"><span data-stu-id="8911a-124">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="8911a-125">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="8911a-125">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="8911a-126">在類別和結構之間選擇</span><span class="sxs-lookup"><span data-stu-id="8911a-126">Choosing Between Class and Struct</span></span>](choosing-between-class-and-struct.md)
