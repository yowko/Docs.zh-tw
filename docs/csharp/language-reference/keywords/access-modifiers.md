---
title: 存取修飾詞 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 5568d79c4a13b7b0db5a46bb4ebb2168ea66a2c9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606089"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="d0c31-102">存取修飾詞 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d0c31-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="d0c31-103">存取修飾詞是用來指定成員或類型的宣告存取範圍的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="d0c31-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="d0c31-104">本節將介紹四種存取修飾詞：</span><span class="sxs-lookup"><span data-stu-id="d0c31-104">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="d0c31-105">您可以使用存取修飾詞，指定下列六個存取層級：</span><span class="sxs-lookup"><span data-stu-id="d0c31-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="d0c31-106">[`public`](public.md)：未限制存取。</span><span class="sxs-lookup"><span data-stu-id="d0c31-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="d0c31-107">[`protected`](protected.md)：存取限於包含類別或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="d0c31-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="d0c31-108">[`internal`](internal.md)：存取限於目前組件。</span><span class="sxs-lookup"><span data-stu-id="d0c31-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="d0c31-109">[`protected internal`](protected-internal.md)：存取限於目前組件或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="d0c31-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="d0c31-110">[`private`](private.md)：存取限於包含類型。</span><span class="sxs-lookup"><span data-stu-id="d0c31-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="d0c31-111">[`private protected`](private-protected.md)：存取限於目前組件內包含類別或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="d0c31-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="d0c31-112">本節也會介紹下列項目：</span><span class="sxs-lookup"><span data-stu-id="d0c31-112">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="d0c31-113">[存取範圍層級](./accessibility-levels.md)：使用四種存取修飾詞來宣告六個存取範圍層級。</span><span class="sxs-lookup"><span data-stu-id="d0c31-113">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="d0c31-114">[存取範圍定義域](./accessibility-domain.md)：指定可以參考成員的程式區段。</span><span class="sxs-lookup"><span data-stu-id="d0c31-114">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="d0c31-115">[使用存取範圍層級的限制](./restrictions-on-using-accessibility-levels.md)：使用已宣告存取範圍層級的限制摘要。</span><span class="sxs-lookup"><span data-stu-id="d0c31-115">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0c31-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0c31-116">See also</span></span>

- [<span data-ttu-id="d0c31-117">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d0c31-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d0c31-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d0c31-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d0c31-119">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="d0c31-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="d0c31-120">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="d0c31-120">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="d0c31-121">Access 關鍵字</span><span class="sxs-lookup"><span data-stu-id="d0c31-121">Access Keywords</span></span>](./access-keywords.md)
- [<span data-ttu-id="d0c31-122">修飾詞</span><span class="sxs-lookup"><span data-stu-id="d0c31-122">Modifiers</span></span>](./modifiers.md)
