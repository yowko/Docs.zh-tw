---
title: 相等運算子
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: bd36b98af25db2921c164ac359188997d379a270
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280046"
---
# <a name="equality-operators"></a><span data-ttu-id="a7810-102">相等運算子</span><span class="sxs-lookup"><span data-stu-id="a7810-102">Equality Operators</span></span>
<span data-ttu-id="a7810-103">本節討論多載等號比較運算子，並將 `operator==` 和 `operator!=` 視為等號比較運算子。</span><span class="sxs-lookup"><span data-stu-id="a7810-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>

 <span data-ttu-id="a7810-104">❌請勿多載其中一個等號比較運算子，而不是另一個。</span><span class="sxs-lookup"><span data-stu-id="a7810-104">❌ DO NOT overload one of the equality operators and not the other.</span></span>

 <span data-ttu-id="a7810-105">✔️確實確保 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 和等號比較運算子具有完全相同的語義和類似的效能特性。</span><span class="sxs-lookup"><span data-stu-id="a7810-105">✔️ DO ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>

 <span data-ttu-id="a7810-106">這通常表示 `Object.Equals` 當等號比較運算子多載時，必須覆寫。</span><span class="sxs-lookup"><span data-stu-id="a7810-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>

 <span data-ttu-id="a7810-107">❌避免從等號比較運算子擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="a7810-107">❌ AVOID throwing exceptions from equality operators.</span></span>

 <span data-ttu-id="a7810-108">例如，如果其中一個引數是 null，而不是擲回，則會傳回 false `NullReferenceException` 。</span><span class="sxs-lookup"><span data-stu-id="a7810-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>

## <a name="equality-operators-on-value-types"></a><span data-ttu-id="a7810-109">實數值型別的等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="a7810-109">Equality Operators on Value Types</span></span>
 <span data-ttu-id="a7810-110">✔️在實數值型別上多載等號比較運算子（如果相等）是否有意義。</span><span class="sxs-lookup"><span data-stu-id="a7810-110">✔️ DO overload the equality operators on value types, if equality is meaningful.</span></span>

 <span data-ttu-id="a7810-111">在大部分的程式設計語言中，實數值型別沒有的預設執行 `operator==` 。</span><span class="sxs-lookup"><span data-stu-id="a7810-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>

## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="a7810-112">參考型別上的等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="a7810-112">Equality Operators on Reference Types</span></span>
 <span data-ttu-id="a7810-113">❌避免可變參考型別的多載等號比較運算子。</span><span class="sxs-lookup"><span data-stu-id="a7810-113">❌ AVOID overloading equality operators on mutable reference types.</span></span>

 <span data-ttu-id="a7810-114">許多語言都有參考型別的內建等號比較運算子。</span><span class="sxs-lookup"><span data-stu-id="a7810-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="a7810-115">內建運算子通常會實作為參考相等，而當預設行為變更為值相等時，許多開發人員會感到驚訝。</span><span class="sxs-lookup"><span data-stu-id="a7810-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>

 <span data-ttu-id="a7810-116">不變的參考型別會降低這個問題，因為不可變性會讓您更難注意參考相等和值相等之間的差異。</span><span class="sxs-lookup"><span data-stu-id="a7810-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>

 <span data-ttu-id="a7810-117">❌避免在參考型別上多載等號比較運算子，但如果執行速度明顯比參考相等</span><span class="sxs-lookup"><span data-stu-id="a7810-117">❌ AVOID overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>

 <span data-ttu-id="a7810-118">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="a7810-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="a7810-119">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。\*\*</span><span class="sxs-lookup"><span data-stu-id="a7810-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="a7810-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7810-120">See also</span></span>

- [<span data-ttu-id="a7810-121">架構設計方針</span><span class="sxs-lookup"><span data-stu-id="a7810-121">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="a7810-122">使用指導方針</span><span class="sxs-lookup"><span data-stu-id="a7810-122">Usage Guidelines</span></span>](usage-guidelines.md)
