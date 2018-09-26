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
ms.openlocfilehash: c3a0a51fc6055190f9a0189de2e17d98f88036ea
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47192728"
---
# <a name="static-class-design"></a><span data-ttu-id="d4bb0-102">靜態類別設計</span><span class="sxs-lookup"><span data-stu-id="d4bb0-102">Static Class Design</span></span>
<span data-ttu-id="d4bb0-103">靜態類別會定義為只包含靜態成員的類別 (當然除了繼承自的執行個體成員<xref:System.Object?displayProperty=nameWithType>和可能的私用的建構函式)。</span><span class="sxs-lookup"><span data-stu-id="d4bb0-103">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="d4bb0-104">某些語言中提供靜態類別的內建的支援。</span><span class="sxs-lookup"><span data-stu-id="d4bb0-104">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="d4bb0-105">在 C# 2.0 和更新版本中，當類別宣告為靜態，它是密封的抽象，而且可以覆寫或宣告任何執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="d4bb0-105">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>  
  
 <span data-ttu-id="d4bb0-106">靜態類別都是單純的物件導向設計和簡易性之間取得折衷。</span><span class="sxs-lookup"><span data-stu-id="d4bb0-106">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="d4bb0-107">它們通常用來提供其他作業的捷徑 (例如<xref:System.IO.File?displayProperty=nameWithType>)，擴充方法，或功能的完整物件導向包裝函式的非預期的持有者 (例如<xref:System.Environment?displayProperty=nameWithType>)。</span><span class="sxs-lookup"><span data-stu-id="d4bb0-107">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>  
  
 <span data-ttu-id="d4bb0-108">**✓ DO** 謹慎使用靜態類別。</span><span class="sxs-lookup"><span data-stu-id="d4bb0-108">**✓ DO** use static classes sparingly.</span></span>  
  
 <span data-ttu-id="d4bb0-109">靜態類別應該僅被用作為支援物件導向的核心架構的類別。</span><span class="sxs-lookup"><span data-stu-id="d4bb0-109">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>  
  
 <span data-ttu-id="d4bb0-110">**X DO NOT** 視為其他的值區的靜態類別。</span><span class="sxs-lookup"><span data-stu-id="d4bb0-110">**X DO NOT** treat static classes as a miscellaneous bucket.</span></span>  
  
 <span data-ttu-id="d4bb0-111">**X DO NOT** 宣告或覆寫在靜態類別中的執行個體成員。</span><span class="sxs-lookup"><span data-stu-id="d4bb0-111">**X DO NOT** declare or override instance members in static classes.</span></span>  
  
 <span data-ttu-id="d4bb0-112">**✓ DO** 宣告為密封，抽象的並加入私用執行個體建構函式，如果您的程式語言並沒有內建支援靜態類別。</span><span class="sxs-lookup"><span data-stu-id="d4bb0-112">**✓ DO** declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>  
  
 <span data-ttu-id="d4bb0-113">*Portions © 2005, 2009 Microsoft Corporation.All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="d4bb0-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="d4bb0-114">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="d4bb0-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4bb0-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4bb0-115">See also</span></span>

- [<span data-ttu-id="d4bb0-116">類型設計方針</span><span class="sxs-lookup"><span data-stu-id="d4bb0-116">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
- [<span data-ttu-id="d4bb0-117">Framework 設計方針</span><span class="sxs-lookup"><span data-stu-id="d4bb0-117">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
