---
title: 相等運算子
ms.date: 10/22/2008
helpviewer_keywords:
- class library design guidelines [.NET Framework], Equals method
- class library design guidelines [.NET Framework], equality operator
- equality operator (==) [.NET Framework]
- Equals method
- == operator (equality) [.NET Framework]
ms.assetid: bc496a91-fefb-4ce0-ab4c-61f09964119a
ms.openlocfilehash: 2331a852adb4dd254af85060a5077f454bcfe0eb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734422"
---
# <a name="equality-operators"></a><span data-ttu-id="66601-102">相等運算子</span><span class="sxs-lookup"><span data-stu-id="66601-102">Equality Operators</span></span>

<span data-ttu-id="66601-103">本節討論多載等號比較運算子，並參考 `operator==` 和 `operator!=` 做為等號比較運算子。</span><span class="sxs-lookup"><span data-stu-id="66601-103">This section discusses overloading equality operators and refers to `operator==` and `operator!=` as equality operators.</span></span>

 <span data-ttu-id="66601-104">❌ 請勿多載其中一個等號比較運算子，而不是另一個相等運算子。</span><span class="sxs-lookup"><span data-stu-id="66601-104">❌ DO NOT overload one of the equality operators and not the other.</span></span>

 <span data-ttu-id="66601-105">✔️確定 <xref:System.Object.Equals%2A?displayProperty=nameWithType> 和等號比較運算子具有完全相同的語義和類似的效能特性。</span><span class="sxs-lookup"><span data-stu-id="66601-105">✔️ DO ensure that <xref:System.Object.Equals%2A?displayProperty=nameWithType> and the equality operators have exactly the same semantics and similar performance characteristics.</span></span>

 <span data-ttu-id="66601-106">這通常表示 `Object.Equals` 當相等運算子超載時，需要覆寫。</span><span class="sxs-lookup"><span data-stu-id="66601-106">This often means that `Object.Equals` needs to be overridden when the equality operators are overloaded.</span></span>

 <span data-ttu-id="66601-107">❌ 避免從相等運算子擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="66601-107">❌ AVOID throwing exceptions from equality operators.</span></span>

 <span data-ttu-id="66601-108">例如，如果其中一個引數為 null，而不是擲回，則傳回 false `NullReferenceException` 。</span><span class="sxs-lookup"><span data-stu-id="66601-108">For example, return false if one of the arguments is null instead of throwing `NullReferenceException`.</span></span>

## <a name="equality-operators-on-value-types"></a><span data-ttu-id="66601-109">實數值型別上的等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="66601-109">Equality Operators on Value Types</span></span>

 <span data-ttu-id="66601-110">如果等號比較有意義，✔️會在實數值型別上多載等號比較運算子。</span><span class="sxs-lookup"><span data-stu-id="66601-110">✔️ DO overload the equality operators on value types, if equality is meaningful.</span></span>

 <span data-ttu-id="66601-111">在大部分的程式設計語言中，實數值型別沒有的預設實 `operator==` 值。</span><span class="sxs-lookup"><span data-stu-id="66601-111">In most programming languages, there is no default implementation of `operator==` for value types.</span></span>

## <a name="equality-operators-on-reference-types"></a><span data-ttu-id="66601-112">參考型別上的等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="66601-112">Equality Operators on Reference Types</span></span>

 <span data-ttu-id="66601-113">❌ 避免可變參考型別上的多載等號比較運算子。</span><span class="sxs-lookup"><span data-stu-id="66601-113">❌ AVOID overloading equality operators on mutable reference types.</span></span>

 <span data-ttu-id="66601-114">許多語言都有參考型別的內建等號比較運算子。</span><span class="sxs-lookup"><span data-stu-id="66601-114">Many languages have built-in equality operators for reference types.</span></span> <span data-ttu-id="66601-115">內建運算子通常會實作為參考相等，而許多開發人員會在預設行為變更為值相等時感到驚訝。</span><span class="sxs-lookup"><span data-stu-id="66601-115">The built-in operators usually implement the reference equality, and many developers are surprised when the default behavior is changed to the value equality.</span></span>

 <span data-ttu-id="66601-116">因為不變的參考型別會讓不變的參考型別變得更容易，所以不需要注意參考相等和值相等之間的差異。</span><span class="sxs-lookup"><span data-stu-id="66601-116">This problem is mitigated for immutable reference types because immutability makes it much harder to notice the difference between reference equality and value equality.</span></span>

 <span data-ttu-id="66601-117">❌ 如果實作為參考型別的多載等號比較運算子，請避免在參考型別上多載相等運算子。</span><span class="sxs-lookup"><span data-stu-id="66601-117">❌ AVOID overloading equality operators on reference types if the implementation would be significantly slower than that of reference equality.</span></span>

 <span data-ttu-id="66601-118">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="66601-118">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="66601-119">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="66601-119">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="66601-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66601-120">See also</span></span>

- [<span data-ttu-id="66601-121">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="66601-121">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="66601-122">使用指導方針</span><span class="sxs-lookup"><span data-stu-id="66601-122">Usage Guidelines</span></span>](usage-guidelines.md)
