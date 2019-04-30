---
title: 等號比較運算子
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
author: KrzysztofCwalina
ms.openlocfilehash: ef1a0aff1ac59434d9d9a6f0371bf236f637050e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61960327"
---
# <a name="equality-operators"></a><span data-ttu-id="a4518-102">等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="a4518-102">Equality Operators</span></span>
<span data-ttu-id="a4518-103">本節討論多載等號比較運算子，而是指`operator==`和`operator!=`為等號比較運算子。</span><span class="sxs-lookup"><span data-stu-id="a4518-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>  
  
 <span data-ttu-id="a4518-104">**X DO NOT** 的等號比較運算子，但是其中一個多載。</span><span class="sxs-lookup"><span data-stu-id="a4518-104">**X DO NOT** overload one of the equality operators and not the other.</span></span>  
  
 <span data-ttu-id="a4518-105">**✓ DO** 確定 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 和等號比較運算子有完全相同的語意和類似的效能特性。</span><span class="sxs-lookup"><span data-stu-id="a4518-105">**✓ DO** ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>  
  
 <span data-ttu-id="a4518-106">這通常表示`Object.Equals`必須覆寫等號比較運算子多載。</span><span class="sxs-lookup"><span data-stu-id="a4518-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>  
  
 <span data-ttu-id="a4518-107">**X AVOID** 擲回例外狀況，從等號比較運算子。</span><span class="sxs-lookup"><span data-stu-id="a4518-107">**X AVOID** throwing exceptions from equality operators.</span></span>  
  
 <span data-ttu-id="a4518-108">例如，如果傳回 false 其中一個引數為 null 而非擲回`NullReferenceException`。</span><span class="sxs-lookup"><span data-stu-id="a4518-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>  
  
## <a name="equality-operators-on-value-types"></a><span data-ttu-id="a4518-109">實值型別上的等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="a4518-109">Equality Operators on Value Types</span></span>  
 <span data-ttu-id="a4518-110">**✓ DO** 多載等號比較運算子實值型別，如果是有意義的等號比較。</span><span class="sxs-lookup"><span data-stu-id="a4518-110">**✓ DO** overload the equality operators on value types, if equality is meaningful.</span></span>  
  
 <span data-ttu-id="a4518-111">在大部分的程式設計語言，不會有預設實作的`operator==`實值型別。</span><span class="sxs-lookup"><span data-stu-id="a4518-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>  
  
## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="a4518-112">參考型別上的等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="a4518-112">Equality Operators on Reference Types</span></span>  
 <span data-ttu-id="a4518-113">**X AVOID** 多載可變動參考類型的等號比較運算子。</span><span class="sxs-lookup"><span data-stu-id="a4518-113">**X AVOID** overloading equality operators on mutable reference types.</span></span>  
  
 <span data-ttu-id="a4518-114">許多語言有參考類型的內建的等號比較運算子。</span><span class="sxs-lookup"><span data-stu-id="a4518-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="a4518-115">內建運算子通常會實作參考相等，並預設行為變更為實值相等時，許多開發人員都會很驚訝。</span><span class="sxs-lookup"><span data-stu-id="a4518-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>  
  
 <span data-ttu-id="a4518-116">不可變的參考型別降低這個問題，因為不變性讓更難發現參考相等與實值相等之間的差異。</span><span class="sxs-lookup"><span data-stu-id="a4518-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>  
  
 <span data-ttu-id="a4518-117">**X AVOID** 如果實作可能會大幅低於參考相等的多載參考類型的等號比較運算子。</span><span class="sxs-lookup"><span data-stu-id="a4518-117">**X AVOID** overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>  
  
 <span data-ttu-id="a4518-118">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="a4518-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="a4518-119">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="a4518-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4518-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4518-120">See also</span></span>

- [<span data-ttu-id="a4518-121">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="a4518-121">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
- [<span data-ttu-id="a4518-122">用法方針</span><span class="sxs-lookup"><span data-stu-id="a4518-122">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
