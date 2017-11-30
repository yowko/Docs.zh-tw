---
title: "存取修飾詞 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 23f99d0925aefde7ef43888d16e888a0943dfc21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="e5056-102">存取修飾詞 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e5056-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="e5056-103">存取修飾詞是用來指定成員或類型的宣告存取範圍的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="e5056-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="e5056-104">本節將介紹四種存取修飾詞：</span><span class="sxs-lookup"><span data-stu-id="e5056-104">This section introduces the four access modifiers:</span></span>  
  
-   [<span data-ttu-id="e5056-105">public</span><span class="sxs-lookup"><span data-stu-id="e5056-105">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
  
-   [<span data-ttu-id="e5056-106">protected</span><span class="sxs-lookup"><span data-stu-id="e5056-106">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
  
-   [<span data-ttu-id="e5056-107">internal</span><span class="sxs-lookup"><span data-stu-id="e5056-107">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
  
-   [<span data-ttu-id="e5056-108">private</span><span class="sxs-lookup"><span data-stu-id="e5056-108">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
  
 <span data-ttu-id="e5056-109">您可以使用存取修飾詞，指定下列六個存取層級：</span><span class="sxs-lookup"><span data-stu-id="e5056-109">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
 <span data-ttu-id="e5056-110">`public`：未限制存取。</span><span class="sxs-lookup"><span data-stu-id="e5056-110">`public`: Access is not restricted.</span></span>  
  
 <span data-ttu-id="e5056-111">`protected`：存取限於包含類別或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="e5056-111">`protected`: Access is limited to the containing class or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="e5056-112">`internal`：存取限於目前組件。</span><span class="sxs-lookup"><span data-stu-id="e5056-112">`internal`: Access is limited to the current assembly.</span></span>  
  
 <span data-ttu-id="e5056-113">[`protected internal`](../../../csharp/language-reference/keywords/protected-internal.md)： 存取限於目前的組件或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="e5056-113">[`protected internal`](../../../csharp/language-reference/keywords/protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="e5056-114">`private`：存取限於包含類型。</span><span class="sxs-lookup"><span data-stu-id="e5056-114">`private`: Access is limited to the containing type.</span></span>  

 <span data-ttu-id="e5056-115">[`private protected`](../../../csharp/language-reference/keywords/private-protected.md)： 存取限於包含的類別或衍生自包含目前組件內類別的類型。</span><span class="sxs-lookup"><span data-stu-id="e5056-115">[`private protected`](../../../csharp/language-reference/keywords/private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="e5056-116">本節也會介紹下列項目：</span><span class="sxs-lookup"><span data-stu-id="e5056-116">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="e5056-117">[存取層級](../../../csharp/language-reference/keywords/accessibility-levels.md)： 使用四種存取修飾詞來宣告存取範圍的六個層級。</span><span class="sxs-lookup"><span data-stu-id="e5056-117">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="e5056-118">[存取範圍定義域](../../../csharp/language-reference/keywords/accessibility-domain.md)：指定可以參考成員的程式區段。</span><span class="sxs-lookup"><span data-stu-id="e5056-118">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="e5056-119">[使用存取層級的限制](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)：使用已宣告存取層級的限制摘要。</span><span class="sxs-lookup"><span data-stu-id="e5056-119">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5056-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5056-120">See Also</span></span>  
 [<span data-ttu-id="e5056-121">C# 參考</span><span class="sxs-lookup"><span data-stu-id="e5056-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e5056-122">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e5056-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e5056-123">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="e5056-123">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e5056-124">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="e5056-124">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="e5056-125">Access 關鍵字</span><span class="sxs-lookup"><span data-stu-id="e5056-125">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
 [<span data-ttu-id="e5056-126">修飾詞</span><span class="sxs-lookup"><span data-stu-id="e5056-126">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
