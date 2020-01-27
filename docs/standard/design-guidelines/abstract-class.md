---
title: 抽象類別設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
ms.openlocfilehash: 018dd353024e75e9819f5a97008f2f422ecad291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739064"
---
# <a name="abstract-class-design"></a><span data-ttu-id="0014e-102">抽象類別設計</span><span class="sxs-lookup"><span data-stu-id="0014e-102">Abstract Class Design</span></span>

<span data-ttu-id="0014e-103">❌ 不會定義抽象類別型中的公用或受保護的內部處理函式。</span><span class="sxs-lookup"><span data-stu-id="0014e-103">❌ DO NOT define public or protected internal constructors in abstract types.</span></span>

 <span data-ttu-id="0014e-104">只有當使用者需要建立類型的實例時，才應該公開公用函式。</span><span class="sxs-lookup"><span data-stu-id="0014e-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="0014e-105">因為您無法建立抽象類別型的實例，所以具有公用函式的抽象類別型設計不正確，而且會誤導使用者。</span><span class="sxs-lookup"><span data-stu-id="0014e-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>

 <span data-ttu-id="0014e-106">✔️確實在抽象類別中定義受保護或內部的函式。</span><span class="sxs-lookup"><span data-stu-id="0014e-106">✔️ DO define a protected or an internal constructor in abstract classes.</span></span>

 <span data-ttu-id="0014e-107">受保護的函式較常見，只允許基類在建立子類型時執行自己的初始化。</span><span class="sxs-lookup"><span data-stu-id="0014e-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>

 <span data-ttu-id="0014e-108">內部的函式可以用來將抽象類別的具體執行限制為定義類別的元件。</span><span class="sxs-lookup"><span data-stu-id="0014e-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>

 <span data-ttu-id="0014e-109">✔️確實提供了一個從您出貨之每個抽象類別繼承的具體型別。</span><span class="sxs-lookup"><span data-stu-id="0014e-109">✔️ DO provide at least one concrete type that inherits from each abstract class that you ship.</span></span>

 <span data-ttu-id="0014e-110">這麼做有助於驗證抽象類別的設計。</span><span class="sxs-lookup"><span data-stu-id="0014e-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="0014e-111">例如，<xref:System.IO.FileStream?displayProperty=nameWithType> 是 <xref:System.IO.Stream?displayProperty=nameWithType> 抽象類別的執行。</span><span class="sxs-lookup"><span data-stu-id="0014e-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>

 <span data-ttu-id="0014e-112">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="0014e-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="0014e-113">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="0014e-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="0014e-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="0014e-114">See also</span></span>

- [<span data-ttu-id="0014e-115">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="0014e-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="0014e-116">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="0014e-116">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
