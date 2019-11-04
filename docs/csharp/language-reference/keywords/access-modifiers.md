---
title: 存取修飾詞 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 7dfbc103b3fd0ebf8c349bd36dc54915782eb807
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422930"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="50d1e-102">存取修飾詞 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="50d1e-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="50d1e-103">存取修飾詞是用來指定成員或類型的宣告存取範圍的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="50d1e-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="50d1e-104">本節將介紹四種存取修飾詞：</span><span class="sxs-lookup"><span data-stu-id="50d1e-104">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="50d1e-105">您可以使用存取修飾詞，指定下列六個存取層級：</span><span class="sxs-lookup"><span data-stu-id="50d1e-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="50d1e-106">[`public`](public.md)：未限制存取。</span><span class="sxs-lookup"><span data-stu-id="50d1e-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="50d1e-107">[`protected`](protected.md)：存取限於包含類別或衍生自包含類別的型別。</span><span class="sxs-lookup"><span data-stu-id="50d1e-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="50d1e-108">[`internal`](internal.md)：存取限於目前組件。</span><span class="sxs-lookup"><span data-stu-id="50d1e-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="50d1e-109">[`protected internal`](protected-internal.md)：存取限於目前組件或衍生自包含類別的型別。</span><span class="sxs-lookup"><span data-stu-id="50d1e-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="50d1e-110">[`private`](private.md)：存取限於包含型別。</span><span class="sxs-lookup"><span data-stu-id="50d1e-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="50d1e-111">[`private protected`](private-protected.md)：存取限於目前組件內包含類別或衍生自包含類別的型別。</span><span class="sxs-lookup"><span data-stu-id="50d1e-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="50d1e-112">本節也會介紹下列項目：</span><span class="sxs-lookup"><span data-stu-id="50d1e-112">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="50d1e-113">[存取層級](./accessibility-levels.md)：使用四種存取修飾詞來宣告六個存取層級。</span><span class="sxs-lookup"><span data-stu-id="50d1e-113">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="50d1e-114">[存取範圍定義域](./accessibility-domain.md)：指定可以參考成員的程式區段。</span><span class="sxs-lookup"><span data-stu-id="50d1e-114">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="50d1e-115">[使用存取層級的限制](./restrictions-on-using-accessibility-levels.md)：使用已宣告存取層級的限制摘要。</span><span class="sxs-lookup"><span data-stu-id="50d1e-115">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50d1e-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="50d1e-116">See also</span></span>

- [<span data-ttu-id="50d1e-117">C# 參考</span><span class="sxs-lookup"><span data-stu-id="50d1e-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="50d1e-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="50d1e-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="50d1e-119">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="50d1e-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="50d1e-120">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="50d1e-120">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="50d1e-121">Access 關鍵字</span><span class="sxs-lookup"><span data-stu-id="50d1e-121">Access Keywords</span></span>](base.md)
- [<span data-ttu-id="50d1e-122">修飾詞</span><span class="sxs-lookup"><span data-stu-id="50d1e-122">Modifiers</span></span>](index.md)
