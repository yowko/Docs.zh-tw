---
description: 存取修飾詞 - C# 參考
title: 存取修飾詞 - C# 參考
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 2ea7a65c23b6a1edee572f6f6ff6c52d14358408
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89127148"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="a7810-103">存取修飾詞 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="a7810-103">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="a7810-104">存取修飾詞是用來指定成員或類型的宣告存取範圍的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="a7810-104">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="a7810-105">本節將介紹四種存取修飾詞：</span><span class="sxs-lookup"><span data-stu-id="a7810-105">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="a7810-106">您可以使用存取修飾詞，指定下列六個存取層級：</span><span class="sxs-lookup"><span data-stu-id="a7810-106">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="a7810-107">[`public`](public.md)：存取不受限制。</span><span class="sxs-lookup"><span data-stu-id="a7810-107">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="a7810-108">[`protected`](protected.md)：存取限於包含類別或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="a7810-108">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="a7810-109">[`internal`](internal.md)：存取限於目前元件。</span><span class="sxs-lookup"><span data-stu-id="a7810-109">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="a7810-110">[`protected internal`](protected-internal.md)：存取限於目前元件或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="a7810-110">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="a7810-111">[`private`](private.md)：存取限於包含類型。</span><span class="sxs-lookup"><span data-stu-id="a7810-111">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="a7810-112">[`private protected`](private-protected.md)：存取限於包含類別或衍生自目前元件內包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="a7810-112">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="a7810-113">本節也會介紹下列項目：</span><span class="sxs-lookup"><span data-stu-id="a7810-113">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="a7810-114">[存取層級](./accessibility-levels.md)：使用四種存取修飾詞來宣告六個存取層級。</span><span class="sxs-lookup"><span data-stu-id="a7810-114">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="a7810-115">[存取範圍定義域](./accessibility-domain.md)：指定可以參考成員的程式區段。</span><span class="sxs-lookup"><span data-stu-id="a7810-115">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="a7810-116">[使用存取層級的限制](./restrictions-on-using-accessibility-levels.md)：使用已宣告存取層級的限制摘要。</span><span class="sxs-lookup"><span data-stu-id="a7810-116">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7810-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7810-117">See also</span></span>

- [<span data-ttu-id="a7810-118">C # 參考</span><span class="sxs-lookup"><span data-stu-id="a7810-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a7810-119">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a7810-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a7810-120">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="a7810-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="a7810-121">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="a7810-121">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="a7810-122">存取關鍵字</span><span class="sxs-lookup"><span data-stu-id="a7810-122">Access Keywords</span></span>](base.md)
- [<span data-ttu-id="a7810-123">修飾詞</span><span class="sxs-lookup"><span data-stu-id="a7810-123">Modifiers</span></span>](index.md)
