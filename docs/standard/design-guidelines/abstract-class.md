---
title: 抽象類別設計
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- type design guidelines, abstract classes
- abstract classes, design guidelines
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], abstract
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d3646e6d-5c1f-4922-8fb0-ec5effb30d60
caps.latest.revision: 13
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: a98c40ccc8005789a3a991bfc93deb11786b8943
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="abstract-class-design"></a><span data-ttu-id="b9c5a-102">抽象類別設計</span><span class="sxs-lookup"><span data-stu-id="b9c5a-102">Abstract Class Design</span></span>
<span data-ttu-id="b9c5a-103">**X 不**抽象型別中定義公用或受保護的內部建構函式。</span><span class="sxs-lookup"><span data-stu-id="b9c5a-103">**X DO NOT** define public or protected internal constructors in abstract types.</span></span>  
  
 <span data-ttu-id="b9c5a-104">應該只有當使用者將需要建立類型的執行個體的公用建構函式。</span><span class="sxs-lookup"><span data-stu-id="b9c5a-104">Constructors should be public only if users will need to create instances of the type.</span></span> <span data-ttu-id="b9c5a-105">因為您無法建立抽象類型的執行個體，具有公用建構函式的抽象類型是不正確地設計與誤導使用者。</span><span class="sxs-lookup"><span data-stu-id="b9c5a-105">Because you cannot create instances of an abstract type, an abstract type with a public constructor is incorrectly designed and misleading to the users.</span></span>  
  
 <span data-ttu-id="b9c5a-106">**✓ 不要**抽象類別中定義受保護或內部的建構函式。</span><span class="sxs-lookup"><span data-stu-id="b9c5a-106">**✓ DO** define a protected or an internal constructor in abstract classes.</span></span>  
  
 <span data-ttu-id="b9c5a-107">受保護的建構函式更常見，並只允許基底類別建立子型別時執行它自己的初始化。</span><span class="sxs-lookup"><span data-stu-id="b9c5a-107">A protected constructor is more common and simply allows the base class to do its own initialization when subtypes are created.</span></span>  
  
 <span data-ttu-id="b9c5a-108">內部的建構函式可以用來限制要定義類別的組件的抽象類別的具象實作。</span><span class="sxs-lookup"><span data-stu-id="b9c5a-108">An internal constructor can be used to limit concrete implementations of the abstract class to the assembly defining the class.</span></span>  
  
 <span data-ttu-id="b9c5a-109">**✓ 不要**提供至少一個繼承自每個您寄送的抽象類別的具象型別。</span><span class="sxs-lookup"><span data-stu-id="b9c5a-109">**✓ DO** provide at least one concrete type that inherits from each abstract class that you ship.</span></span>  
  
 <span data-ttu-id="b9c5a-110">此舉有助於驗證抽象類別的設計。</span><span class="sxs-lookup"><span data-stu-id="b9c5a-110">Doing this helps to validate the design of the abstract class.</span></span> <span data-ttu-id="b9c5a-111">例如，<xref:System.IO.FileStream?displayProperty=nameWithType>是實作<xref:System.IO.Stream?displayProperty=nameWithType>抽象類別。</span><span class="sxs-lookup"><span data-stu-id="b9c5a-111">For example,  <xref:System.IO.FileStream?displayProperty=nameWithType> is an implementation of the <xref:System.IO.Stream?displayProperty=nameWithType> abstract class.</span></span>  
  
 <span data-ttu-id="b9c5a-112">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="b9c5a-112">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="b9c5a-113">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="b9c5a-113">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9c5a-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9c5a-114">See Also</span></span>  
 [<span data-ttu-id="b9c5a-115">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="b9c5a-115">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="b9c5a-116">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="b9c5a-116">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
