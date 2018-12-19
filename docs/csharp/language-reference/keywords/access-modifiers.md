---
title: 存取修飾詞 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 0fb435a35b928cb78511d8969f1dfce9f94869eb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242018"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="bf620-102">存取修飾詞 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="bf620-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="bf620-103">存取修飾詞是用來指定成員或類型的宣告存取範圍的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="bf620-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="bf620-104">本節將介紹四種存取修飾詞：</span><span class="sxs-lookup"><span data-stu-id="bf620-104">This section introduces the four access modifiers:</span></span>  
  
-   `public`
-   `protected`
-   `internal`
-   `private`
  
 <span data-ttu-id="bf620-105">您可以使用存取修飾詞，指定下列六個存取層級：</span><span class="sxs-lookup"><span data-stu-id="bf620-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="bf620-106">[`public`](public.md)：未限制存取。</span><span class="sxs-lookup"><span data-stu-id="bf620-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="bf620-107">[`protected`](protected.md)：存取限於包含類別或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="bf620-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="bf620-108">[`internal`](internal.md)：存取限於目前組件。</span><span class="sxs-lookup"><span data-stu-id="bf620-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="bf620-109">[`protected internal`](protected-internal.md)：存取限於目前組件或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="bf620-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="bf620-110">[`private`](private.md)：存取限於包含類型。</span><span class="sxs-lookup"><span data-stu-id="bf620-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="bf620-111">[`private protected`](private-protected.md)：存取限於目前組件內包含類別或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="bf620-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="bf620-112">本節也會介紹下列項目：</span><span class="sxs-lookup"><span data-stu-id="bf620-112">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="bf620-113">[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)：使用四種存取修飾詞來宣告六個存取範圍層級。</span><span class="sxs-lookup"><span data-stu-id="bf620-113">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="bf620-114">[存取範圍定義域](../../../csharp/language-reference/keywords/accessibility-domain.md)：指定可以參考成員的程式區段。</span><span class="sxs-lookup"><span data-stu-id="bf620-114">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="bf620-115">[使用存取範圍層級的限制](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)：使用已宣告存取範圍層級的限制摘要。</span><span class="sxs-lookup"><span data-stu-id="bf620-115">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf620-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="bf620-116">See Also</span></span>  
- [<span data-ttu-id="bf620-117">C# 參考</span><span class="sxs-lookup"><span data-stu-id="bf620-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="bf620-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bf620-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="bf620-119">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="bf620-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="bf620-120">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="bf620-120">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [<span data-ttu-id="bf620-121">Access 關鍵字</span><span class="sxs-lookup"><span data-stu-id="bf620-121">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
- [<span data-ttu-id="bf620-122">修飾詞</span><span class="sxs-lookup"><span data-stu-id="bf620-122">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
