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
author: KrzysztofCwalina
ms.openlocfilehash: 1982c7c97802dedd1d49c770be5a7ac00944cbfc
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130870"
---
# <a name="abstract-class-design"></a><span data-ttu-id="c1efa-102">抽象類別設計</span><span class="sxs-lookup"><span data-stu-id="c1efa-102">Abstract Class Design</span></span>
<span data-ttu-id="c1efa-103">**X DO NOT** 抽象型別中定義公用或受保護的內部建構函式。</span><span class="sxs-lookup"><span data-stu-id="c1efa-103">**X DO NOT** define public or protected internal constructors in abstract types.</span></span>  
  
 <span data-ttu-id="c1efa-104">建構函式應該是公用，只有當使用者將需要建立型別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="c1efa-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="c1efa-105">因為您無法建立抽象類型的執行個體，具有公用建構函式的抽象類型是不正確設計，且可能造成誤導使用者。</span><span class="sxs-lookup"><span data-stu-id="c1efa-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>  
  
 <span data-ttu-id="c1efa-106">**✓ DO** 抽象類別中定義受保護或內部的建構函式。</span><span class="sxs-lookup"><span data-stu-id="c1efa-106">**✓ DO** define a protected or an internal constructor in abstract classes.</span></span>  
  
 <span data-ttu-id="c1efa-107">受保護的建構函式是更常見的並只允許基底類別，以建立子型別時進行自己的初始化。</span><span class="sxs-lookup"><span data-stu-id="c1efa-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>  
  
 <span data-ttu-id="c1efa-108">內部的建構函式可用來限制要定義類別的組件的抽象類別的具象實作。</span><span class="sxs-lookup"><span data-stu-id="c1efa-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>  
  
 <span data-ttu-id="c1efa-109">**✓ DO** 提供至少一個繼承自每個您寄送的抽象類別的具象型別。</span><span class="sxs-lookup"><span data-stu-id="c1efa-109">**✓ DO** provide at least one concrete type that inherits from each abstract class that you ship.</span></span>  
  
 <span data-ttu-id="c1efa-110">此舉有助於驗證抽象類別的設計。</span><span class="sxs-lookup"><span data-stu-id="c1efa-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="c1efa-111">例如，<xref:System.IO.FileStream?displayProperty=nameWithType>是實作<xref:System.IO.Stream?displayProperty=nameWithType>抽象類別。</span><span class="sxs-lookup"><span data-stu-id="c1efa-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>  
  
 <span data-ttu-id="c1efa-112">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="c1efa-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="c1efa-113">*皮耳森教育，inc.的權限所印製[Framework 設計方針：慣例、 慣用句和可重複使用的.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 和 Brad Abrams，2008 年 10 月 22 日由 Addison-wesley Professional 的 Microsoft Windows 開發系列的一部分發行。*</span><span class="sxs-lookup"><span data-stu-id="c1efa-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1efa-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1efa-114">See also</span></span>

- [<span data-ttu-id="c1efa-115">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="c1efa-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
- [<span data-ttu-id="c1efa-116">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="c1efa-116">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
