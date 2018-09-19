---
title: 結構設計
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3879dc3f0270a56132b44882a74c50d05914ff89
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46324616"
---
# <a name="struct-design"></a><span data-ttu-id="e6677-102">結構設計</span><span class="sxs-lookup"><span data-stu-id="e6677-102">Struct Design</span></span>
<span data-ttu-id="e6677-103">一般用途的實值型別最常稱為結構時，它的 C# 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e6677-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="e6677-104">本節提供一般的結構設計指導方針。</span><span class="sxs-lookup"><span data-stu-id="e6677-104">This section provides guidelines for general struct design.</span></span>  
  
 <span data-ttu-id="e6677-105">**X DO NOT** 結構提供的預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="e6677-105">**X DO NOT** provide a default constructor for a struct.</span></span>  
  
 <span data-ttu-id="e6677-106">遵循此指導方針，可讓建立而不需陣列的每個項目上執行建構函式的結構陣列。</span><span class="sxs-lookup"><span data-stu-id="e6677-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="e6677-107">請注意，C# 不允許有預設建構函式的結構。</span><span class="sxs-lookup"><span data-stu-id="e6677-107">Notice that C# does not allow structs to have default constructors.</span></span>  
  
 <span data-ttu-id="e6677-108">**X DO NOT** 定義可變動的值型別。</span><span class="sxs-lookup"><span data-stu-id="e6677-108">**X DO NOT** define mutable value types.</span></span>  
  
 <span data-ttu-id="e6677-109">可變動的實值型別有幾個問題。</span><span class="sxs-lookup"><span data-stu-id="e6677-109">Mutable value types have several problems.</span></span> <span data-ttu-id="e6677-110">例如，當屬性 getter 傳回實值型別時，呼叫端會收到複本。</span><span class="sxs-lookup"><span data-stu-id="e6677-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="e6677-111">因為隱含地建立複本時，可能不知道複本，而不是原始的值會變更開發人員。</span><span class="sxs-lookup"><span data-stu-id="e6677-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="e6677-112">此外，某些語言 （特別是，動態語言） 有取值時，甚至是本機變數，會造成複本設為使用可變動的實值型別，因為的問題。</span><span class="sxs-lookup"><span data-stu-id="e6677-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>  
  
 <span data-ttu-id="e6677-113">**✓ DO** 確保所有執行個體資料的狀態設為零，false 或 null （視情況） 無效。</span><span class="sxs-lookup"><span data-stu-id="e6677-113">**✓ DO** ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>  
  
 <span data-ttu-id="e6677-114">建立結構的陣列時，這會防止意外建立無效的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e6677-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>  
  
 <span data-ttu-id="e6677-115">**✓ DO** 實作 <xref:System.IEquatable%601> 實值型別。</span><span class="sxs-lookup"><span data-stu-id="e6677-115">**✓ DO** implement <xref:System.IEquatable%601> on value types.</span></span>  
  
 <span data-ttu-id="e6677-116"><xref:System.Object.Equals%2A?displayProperty=nameWithType>實值型別上的方法會導致 boxing，和其預設實作不是非常有效率，因為它會使用反映。</span><span class="sxs-lookup"><span data-stu-id="e6677-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="e6677-117"><xref:System.IEquatable%601.Equals%2A> 可以有更好的效能，並使它不會造成 boxing 可以實作。</span><span class="sxs-lookup"><span data-stu-id="e6677-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>  
  
 <span data-ttu-id="e6677-118">**X DO NOT** 明確地延長 <xref:System.ValueType>。</span><span class="sxs-lookup"><span data-stu-id="e6677-118">**X DO NOT** explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="e6677-119">事實上，大部分語言避免這個問題。</span><span class="sxs-lookup"><span data-stu-id="e6677-119">In fact, most languages prevent this.</span></span>  
  
 <span data-ttu-id="e6677-120">一般情況下，結構可以很有幫助，但僅用於小型、 單一、 不可變的值，將不會進行 boxed 處理常見問題。</span><span class="sxs-lookup"><span data-stu-id="e6677-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>  
  
 <span data-ttu-id="e6677-121">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="e6677-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="e6677-122">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="e6677-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6677-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6677-123">See also</span></span>

- [<span data-ttu-id="e6677-124">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="e6677-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
- [<span data-ttu-id="e6677-125">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="e6677-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
- [<span data-ttu-id="e6677-126">在類別和結構之間選擇</span><span class="sxs-lookup"><span data-stu-id="e6677-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
