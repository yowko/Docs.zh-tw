---
title: 靜態類別設計
ms.date: 10/22/2008
helpviewer_keywords:
- type design guidelines, static classes
- class library design guidelines [.NET Framework], classes
- classes [.NET Framework], static
- static classes [.NET Framework]
- classes [.NET Framework], design guidelines
- type design guidelines, classes
ms.assetid: d67c14d8-c4dd-443f-affb-4ccae677c9b6
ms.openlocfilehash: efa5ca6e7b5e7b7d03cbe1d55471a388f3faab37
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94828656"
---
# <a name="static-class-design"></a><span data-ttu-id="a14b1-102">靜態類別設計</span><span class="sxs-lookup"><span data-stu-id="a14b1-102">Static Class Design</span></span>
<span data-ttu-id="a14b1-103">靜態類別定義為只包含靜態成員的類別 (當然，除了繼承自的實例成員 <xref:System.Object?displayProperty=nameWithType> ，以及可能) 私用的函式。</span><span class="sxs-lookup"><span data-stu-id="a14b1-103">A static class is defined as a class that contains only static members (of course besides the instance members inherited from <xref:System.Object?displayProperty=nameWithType> and possibly a private constructor).</span></span> <span data-ttu-id="a14b1-104">某些語言提供靜態類別的內建支援。</span><span class="sxs-lookup"><span data-stu-id="a14b1-104">Some languages provide built-in support for static classes.</span></span> <span data-ttu-id="a14b1-105">在 c # 2.0 和更新版本中，當類別宣告為靜態時，它會是密封的、抽象的，且不能覆寫或宣告任何實例成員。</span><span class="sxs-lookup"><span data-stu-id="a14b1-105">In C# 2.0 and later, when a class is declared to be static, it is sealed, abstract, and no instance members can be overridden or declared.</span></span>

 <span data-ttu-id="a14b1-106">靜態類別是純物件導向設計和簡單性之間的折衷。</span><span class="sxs-lookup"><span data-stu-id="a14b1-106">Static classes are a compromise between pure object-oriented design and simplicity.</span></span> <span data-ttu-id="a14b1-107">它們通常用來提供其他作業的快捷方式 (例如 <xref:System.IO.File?displayProperty=nameWithType>) 、擴充方法的持有者，或完整物件導向包裝函式所預期的功能 (例如 <xref:System.Environment?displayProperty=nameWithType>) 。</span><span class="sxs-lookup"><span data-stu-id="a14b1-107">They are commonly used to provide shortcuts to other operations (such as <xref:System.IO.File?displayProperty=nameWithType>), holders of extension methods, or functionality for which a full object-oriented wrapper is unwarranted (such as <xref:System.Environment?displayProperty=nameWithType>).</span></span>

 <span data-ttu-id="a14b1-108">✔️請謹慎使用靜態類別。</span><span class="sxs-lookup"><span data-stu-id="a14b1-108">✔️ DO use static classes sparingly.</span></span>

 <span data-ttu-id="a14b1-109">靜態類別只能做為架構之物件導向核心的支援類別使用。</span><span class="sxs-lookup"><span data-stu-id="a14b1-109">Static classes should be used only as supporting classes for the object-oriented core of the framework.</span></span>

 <span data-ttu-id="a14b1-110">❌ 請勿將靜態類別視為其他值區。</span><span class="sxs-lookup"><span data-stu-id="a14b1-110">❌ DO NOT treat static classes as a miscellaneous bucket.</span></span>

 <span data-ttu-id="a14b1-111">❌ 請勿在靜態類別中宣告或覆寫實例成員。</span><span class="sxs-lookup"><span data-stu-id="a14b1-111">❌ DO NOT declare or override instance members in static classes.</span></span>

 <span data-ttu-id="a14b1-112">如果您的程式設計語言沒有靜態類別的內建支援，則✔️會將靜態類別宣告為 sealed、abstract，然後新增私用實例的函式。</span><span class="sxs-lookup"><span data-stu-id="a14b1-112">✔️ DO declare static classes as sealed, abstract, and add a private instance constructor if your programming language does not have built-in support for static classes.</span></span>

 <span data-ttu-id="a14b1-113">*部分©2005、2009 Microsoft Corporation。保留的擁有權限。*</span><span class="sxs-lookup"><span data-stu-id="a14b1-113">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="a14b1-114">獲 Pearson Education, Inc. 的授權再版，從 Krzysztof Cwalina 和 Brad Abrams 撰寫，並在 2008 年 10 月 22 日由 Addison-Wesley Professional 出版，作為 Microsoft Windows Development Series 一部份的 [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) 節錄。</span><span class="sxs-lookup"><span data-stu-id="a14b1-114">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="a14b1-115">請參閱</span><span class="sxs-lookup"><span data-stu-id="a14b1-115">See also</span></span>

- [<span data-ttu-id="a14b1-116">型別設計方針</span><span class="sxs-lookup"><span data-stu-id="a14b1-116">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="a14b1-117">架構設計指導方針</span><span class="sxs-lookup"><span data-stu-id="a14b1-117">Framework Design Guidelines</span></span>](index.md)
