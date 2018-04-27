---
title: 結構設計
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- deallocating structures
- allocating structures
- value types, structures
- structure design
- type design guidelines, structures
- structures [.NET Framework], design guidelines
ms.assetid: 1f48b2d8-608c-4be6-9ba4-d8f203ed9f9f
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dfa32112a2eb85a93cdd1e7a72d4411a3b197a1a
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="struct-design"></a><span data-ttu-id="bfd27-102">結構設計</span><span class="sxs-lookup"><span data-stu-id="bfd27-102">Struct Design</span></span>
<span data-ttu-id="bfd27-103">一般用途的實值類型通常稱為結構，其 C# 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bfd27-103">The general-purpose value type is most often referred to as a struct, its C# keyword.</span></span> <span data-ttu-id="bfd27-104">本節提供一般結構設計指導方針。</span><span class="sxs-lookup"><span data-stu-id="bfd27-104">This section provides guidelines for general struct design.</span></span>  
  
 <span data-ttu-id="bfd27-105">**X 不**結構提供的預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="bfd27-105">**X DO NOT** provide a default constructor for a struct.</span></span>  
  
 <span data-ttu-id="bfd27-106">遵循這個指導方針可讓結構來建立，而不需要在陣列的每個項目上執行建構函式的陣列。</span><span class="sxs-lookup"><span data-stu-id="bfd27-106">Following this guideline allows arrays of structs to be created without having to run the constructor on each item of the array.</span></span> <span data-ttu-id="bfd27-107">請注意，C# 不允許有預設建構函式的結構。</span><span class="sxs-lookup"><span data-stu-id="bfd27-107">Notice that C# does not allow structs to have default constructors.</span></span>  
  
 <span data-ttu-id="bfd27-108">**X 不**定義可變動的值型別。</span><span class="sxs-lookup"><span data-stu-id="bfd27-108">**X DO NOT** define mutable value types.</span></span>  
  
 <span data-ttu-id="bfd27-109">可變動的值型別有幾個問題。</span><span class="sxs-lookup"><span data-stu-id="bfd27-109">Mutable value types have several problems.</span></span> <span data-ttu-id="bfd27-110">例如，當屬性 getter 傳回實值類型時，呼叫端接收複本。</span><span class="sxs-lookup"><span data-stu-id="bfd27-110">For example, when a property getter returns a value type, the caller receives a copy.</span></span> <span data-ttu-id="bfd27-111">因為隱含地建立複本時，開發人員可能不會察覺複製，而非原始的值會變更。</span><span class="sxs-lookup"><span data-stu-id="bfd27-111">Because the copy is created implicitly, developers might not be aware that they are mutating the copy, and not the original value.</span></span> <span data-ttu-id="bfd27-112">此外，某些語言 （特別是，動態語言） 具有區域變數，即使是取值時，會導致複本可供使用，因為可變動的實值類型的問題。</span><span class="sxs-lookup"><span data-stu-id="bfd27-112">Also, some languages (dynamic languages, in particular) have problems using mutable value types because even local variables, when dereferenced, cause a copy to be made.</span></span>  
  
 <span data-ttu-id="bfd27-113">**✓ 不要**確保所有執行個體資料的狀態設為零，false 或 null （視情況） 無效。</span><span class="sxs-lookup"><span data-stu-id="bfd27-113">**✓ DO** ensure that a state where all instance data is set to zero, false, or null (as appropriate) is valid.</span></span>  
  
 <span data-ttu-id="bfd27-114">建立結構的陣列時，這可防止意外建立無效的執行個體。</span><span class="sxs-lookup"><span data-stu-id="bfd27-114">This prevents accidental creation of invalid instances when an array of the structs is created.</span></span>  
  
 <span data-ttu-id="bfd27-115">**✓ 不要**實作<xref:System.IEquatable%601>實值型別。</span><span class="sxs-lookup"><span data-stu-id="bfd27-115">**✓ DO** implement <xref:System.IEquatable%601> on value types.</span></span>  
  
 <span data-ttu-id="bfd27-116"><xref:System.Object.Equals%2A?displayProperty=nameWithType>實值類型上的方法會導致 boxing，和其預設實作不是非常有效率，因為它會使用反映。</span><span class="sxs-lookup"><span data-stu-id="bfd27-116">The <xref:System.Object.Equals%2A?displayProperty=nameWithType> method on value types causes boxing, and its default implementation is not very efficient, because it uses reflection.</span></span> <span data-ttu-id="bfd27-117"><xref:System.IEquatable%601.Equals%2A> 可能會較佳的效能，而且可以實作，使它不會造成 boxing。</span><span class="sxs-lookup"><span data-stu-id="bfd27-117"><xref:System.IEquatable%601.Equals%2A> can have much better performance and can be implemented so that it will not cause boxing.</span></span>  
  
 <span data-ttu-id="bfd27-118">**X 不**明確地延長<xref:System.ValueType>。</span><span class="sxs-lookup"><span data-stu-id="bfd27-118">**X DO NOT** explicitly extend <xref:System.ValueType>.</span></span> <span data-ttu-id="bfd27-119">事實上，大部分語言防止這。</span><span class="sxs-lookup"><span data-stu-id="bfd27-119">In fact, most languages prevent this.</span></span>  
  
 <span data-ttu-id="bfd27-120">一般情況下，結構就非常有用，但僅用於小型、 單一、 不可變會不會進行 boxed 處理經常的值。</span><span class="sxs-lookup"><span data-stu-id="bfd27-120">In general, structs can be very useful but should only be used for small, single, immutable values that will not be boxed frequently.</span></span>  
  
 <span data-ttu-id="bfd27-121">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="bfd27-121">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="bfd27-122">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="bfd27-122">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfd27-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfd27-123">See Also</span></span>  
 [<span data-ttu-id="bfd27-124">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="bfd27-124">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="bfd27-125">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="bfd27-125">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="bfd27-126">在類別和結構之間選擇</span><span class="sxs-lookup"><span data-stu-id="bfd27-126">Choosing Between Class and Struct</span></span>](../../../docs/standard/design-guidelines/choosing-between-class-and-struct.md)
