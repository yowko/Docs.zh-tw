---
title: 靜態類別設計
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: 104fa204a95ef31d34e224348068e3a6505aded5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743590"
---
# <a name="static-class-design"></a><span data-ttu-id="e1089-102">靜態類別設計</span><span class="sxs-lookup"><span data-stu-id="e1089-102">Static Class Design</span></span>
<span data-ttu-id="e1089-103">靜態類別定義為僅包含靜態成員的類別（當然，除了繼承自 <xref:System.Object?displayProperty=nameWithType> 的實例成員之外，可能也會是私用的函數）。</span><span class="sxs-lookup"><span data-stu-id="e1089-103">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="e1089-104">某些語言會提供靜態類別的內建支援。</span><span class="sxs-lookup"><span data-stu-id="e1089-104">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="e1089-105">在C# 2.0 和更新版本中，將類別宣告為靜態時，它是密封的、抽象的，而且不能覆寫或宣告任何實例成員。</span><span class="sxs-lookup"><span data-stu-id="e1089-105">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>

 <span data-ttu-id="e1089-106">靜態類別是單純的物件導向設計與簡單的取捨。</span><span class="sxs-lookup"><span data-stu-id="e1089-106">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="e1089-107">它們通常用來提供其他作業的快捷方式（例如 <xref:System.IO.File?displayProperty=nameWithType>）、擴充方法的持有者，或預期完整物件導向包裝函式的功能（例如 <xref:System.Environment?displayProperty=nameWithType>）。</span><span class="sxs-lookup"><span data-stu-id="e1089-107">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="e1089-108">✔️不謹慎地使用靜態類別。</span><span class="sxs-lookup"><span data-stu-id="e1089-108">✔️ DO use static classes sparingly.</span></span>

 <span data-ttu-id="e1089-109">靜態類別只能當做架構物件導向核心的支援類別使用。</span><span class="sxs-lookup"><span data-stu-id="e1089-109">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>

 <span data-ttu-id="e1089-110">❌ 不會將靜態類別視為其他值區。</span><span class="sxs-lookup"><span data-stu-id="e1089-110">❌ DO NOT treat static classes as a miscellaneous bucket.</span></span>

 <span data-ttu-id="e1089-111">❌ 不會在靜態類別中宣告或覆寫實例成員。</span><span class="sxs-lookup"><span data-stu-id="e1089-111">❌ DO NOT declare or override instance members in static classes.</span></span>

 <span data-ttu-id="e1089-112">如果您的程式設計語言沒有靜態類別的內建支援，✔️會將靜態類別宣告為密封、抽象，並加入私用實例的函式。</span><span class="sxs-lookup"><span data-stu-id="e1089-112">✔️ DO declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>

 <span data-ttu-id="e1089-113">*部分©2005、2009 Microsoft Corporation。已保留擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="e1089-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="e1089-114">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="e1089-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="e1089-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="e1089-115">See also</span></span>

- [<span data-ttu-id="e1089-116">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="e1089-116">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="e1089-117">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="e1089-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
