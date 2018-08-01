---
title: 靜態類別設計
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92152600d317c04e3fef26400b11e94a549fde4c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571055"
---
# <a name="static-class-design"></a><span data-ttu-id="522ff-102">靜態類別設計</span><span class="sxs-lookup"><span data-stu-id="522ff-102">Static Class Design</span></span>
<span data-ttu-id="522ff-103">靜態類別會定義為只包含靜態成員的類別 (當然除了繼承自執行個體成員<xref:System.Object?displayProperty=nameWithType>和可能的私用的建構函式)。</span><span class="sxs-lookup"><span data-stu-id="522ff-103">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="522ff-104">某些語言提供靜態類別內建支援。</span><span class="sxs-lookup"><span data-stu-id="522ff-104">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="522ff-105">C# 2.0 版及更新版本中，類別會宣告為靜態，當它是密封、 抽象的而且可以覆寫或宣告沒有任何執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="522ff-105">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>  
  
 <span data-ttu-id="522ff-106">靜態類別是單純的物件導向設計和簡單性之間的洩露。</span><span class="sxs-lookup"><span data-stu-id="522ff-106">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="522ff-107">它們通常用來提供其他作業的快速鍵 (例如<xref:System.IO.File?displayProperty=nameWithType>)，擴充方法或功能的完整物件導向包裝函式為未經授權的持有者 (例如<xref:System.Environment?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="522ff-107">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="522ff-108">**✓ DO**謹慎使用靜態類別。</span><span class="sxs-lookup"><span data-stu-id="522ff-108">**✓ DO** use static classes sparingly.</span></span>  
  
 <span data-ttu-id="522ff-109">靜態類別應作為只支援物件導向的核心架構的類別。</span><span class="sxs-lookup"><span data-stu-id="522ff-109">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>  
  
 <span data-ttu-id="522ff-110">**X DO NOT**視為其他的值區的靜態類別。</span><span class="sxs-lookup"><span data-stu-id="522ff-110">**X DO NOT** treat static classes as a miscellaneous bucket.</span></span>  
  
 <span data-ttu-id="522ff-111">**X DO NOT**宣告或覆寫在靜態類別中的執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="522ff-111">**X DO NOT** declare or override instance members in static classes.</span></span>  
  
 <span data-ttu-id="522ff-112">**✓ DO**宣告為密封，抽象的並加入私用執行個體建構函式，如果您的程式語言並沒有內建支援靜態類別。</span><span class="sxs-lookup"><span data-stu-id="522ff-112">**✓ DO** declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>  
  
 <span data-ttu-id="522ff-113">*部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="522ff-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="522ff-114">*皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*</span><span class="sxs-lookup"><span data-stu-id="522ff-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="522ff-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="522ff-115">See Also</span></span>  
 [<span data-ttu-id="522ff-116">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="522ff-116">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="522ff-117">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="522ff-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
