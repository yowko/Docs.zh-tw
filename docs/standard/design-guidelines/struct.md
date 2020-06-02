---
title: 結構設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
ms.openlocfilehash: c6ac53014e048da3a90dd7b8e961176f61e90355
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290807"
---
# <a name="struct-design"></a><span data-ttu-id="f5827-102">結構設計</span><span class="sxs-lookup"><span data-stu-id="f5827-102">Struct Design</span></span>
<span data-ttu-id="f5827-103">一般用途的實數值型別通常稱為結構，也就是其 c # 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="f5827-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="f5827-104">本節提供一般結構設計的指導方針。</span><span class="sxs-lookup"><span data-stu-id="f5827-104">This section provides guidelines for general struct design.</span></span>

 <span data-ttu-id="f5827-105">❌請勿為結構提供無參數的函式。</span><span class="sxs-lookup"><span data-stu-id="f5827-105">❌ DO NOT provide a parameterless constructor for a struct.</span></span>

 <span data-ttu-id="f5827-106">遵循此指導方針，可讓您建立結構陣列，而不需要在陣列的每個專案上執行此函式。</span><span class="sxs-lookup"><span data-stu-id="f5827-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="f5827-107">請注意，c # 不允許結構具有無參數的構造函式。</span><span class="sxs-lookup"><span data-stu-id="f5827-107">Notice that C# does not allow structs to have parameterless constructors.</span></span>

 <span data-ttu-id="f5827-108">❌不要定義可變的實值型別。</span><span class="sxs-lookup"><span data-stu-id="f5827-108">❌ DO NOT define mutable value types.</span></span>

 <span data-ttu-id="f5827-109">可變的實值型別有幾個問題。</span><span class="sxs-lookup"><span data-stu-id="f5827-109">Mutable value types have several problems.</span></span> <span data-ttu-id="f5827-110">例如，當屬性 getter 傳回實數值型別時，呼叫端會收到複本。</span><span class="sxs-lookup"><span data-stu-id="f5827-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="f5827-111">因為複本是以隱含方式建立的，所以開發人員可能不知道它們會改變複本，而不是原始值。</span><span class="sxs-lookup"><span data-stu-id="f5827-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="f5827-112">此外，某些語言（尤其是動態語言）在使用可變值型別時遇到問題，因為在取值時，即使是區域變數，也會造成複製的執行。</span><span class="sxs-lookup"><span data-stu-id="f5827-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>

 <span data-ttu-id="f5827-113">✔️確實確定所有實例資料設定為零、false 或 null （適當）的狀態都是有效的。</span><span class="sxs-lookup"><span data-stu-id="f5827-113">✔️ DO ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>

 <span data-ttu-id="f5827-114">這可避免在建立結構的陣列時，意外建立不正確實例。</span><span class="sxs-lookup"><span data-stu-id="f5827-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>

 <span data-ttu-id="f5827-115">✔️在實 <xref:System.IEquatable%601> 數值型別上執行。</span><span class="sxs-lookup"><span data-stu-id="f5827-115">✔️ DO implement <xref:System.IEquatable%601> on value types.</span></span>

 <span data-ttu-id="f5827-116"><xref:System.Object.Equals%2A?displayProperty=nameWithType>實值型別上的方法會造成「裝箱」，而且它的預設執行不會非常有效率，因為它會使用反映。</span><span class="sxs-lookup"><span data-stu-id="f5827-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="f5827-117"><xref:System.IEquatable%601.Equals%2A>可以有更好的效能，而且可以實作為不會造成裝箱的問題。</span><span class="sxs-lookup"><span data-stu-id="f5827-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>

 <span data-ttu-id="f5827-118">❌請勿明確擴充 <xref:System.ValueType> 。</span><span class="sxs-lookup"><span data-stu-id="f5827-118">❌ DO NOT explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="f5827-119">事實上，大部分的語言都會阻止這種情況。</span><span class="sxs-lookup"><span data-stu-id="f5827-119">In fact, most languages prevent this.</span></span>

 <span data-ttu-id="f5827-120">一般來說，結構可能非常有用，但僅適用于不會頻繁地裝箱的小型、單一、不可變的值。</span><span class="sxs-lookup"><span data-stu-id="f5827-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>

 <span data-ttu-id="f5827-121">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="f5827-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="f5827-122">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="f5827-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="f5827-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5827-123">See also</span></span>

- [<span data-ttu-id="f5827-124">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="f5827-124">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="f5827-125">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="f5827-125">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="f5827-126">在類別和結構之間選擇</span><span class="sxs-lookup"><span data-stu-id="f5827-126">Choosing Between Class and Struct</span></span>](choosing-between-class-and-struct.md)
