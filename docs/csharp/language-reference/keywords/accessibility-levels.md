---
title: "存取範圍層級 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 77124554d7a0b38414e154e024aceddbfffcfbd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="2386b-102">存取範圍層級 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="2386b-102">Accessibility Levels (C# Reference)</span></span>
<span data-ttu-id="2386b-103">使用存取修飾詞 [public](../../../csharp/language-reference/keywords/public.md)、[protected](../../../csharp/language-reference/keywords/protected.md)、[internal](../../../csharp/language-reference/keywords/internal.md) 或 [private](../../../csharp/language-reference/keywords/private.md) 來指定成員的下列其中一個已宣告存取範圍層級。</span><span class="sxs-lookup"><span data-stu-id="2386b-103">Use the access modifiers, [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md), to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="2386b-104">已宣告存取範圍</span><span class="sxs-lookup"><span data-stu-id="2386b-104">Declared accessibility</span></span>|<span data-ttu-id="2386b-105">意義</span><span class="sxs-lookup"><span data-stu-id="2386b-105">Meaning</span></span>|  
|----------------------------|-------------|  
|`public`|<span data-ttu-id="2386b-106">未限制存取。</span><span class="sxs-lookup"><span data-stu-id="2386b-106">Access is not restricted.</span></span>|  
|`protected`|<span data-ttu-id="2386b-107">存取限於包含類別或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="2386b-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|`internal`|<span data-ttu-id="2386b-108">存取限於目前組件。</span><span class="sxs-lookup"><span data-stu-id="2386b-108">Access is limited to the current assembly.</span></span>|  
|`protected internal`|<span data-ttu-id="2386b-109">存取限於目前組件或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="2386b-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|`private`|<span data-ttu-id="2386b-110">存取限於包含類型。</span><span class="sxs-lookup"><span data-stu-id="2386b-110">Access is limited to the containing type.</span></span>|  
|`private protected`|<span data-ttu-id="2386b-111">存取限於包含的類別或衍生自包含目前組件內類別的類型。</span><span class="sxs-lookup"><span data-stu-id="2386b-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>|  
  
 <span data-ttu-id="2386b-112">只有一個存取修飾詞的成員或型別，除了當您使用`protected internal`或`private protected`組合。</span><span class="sxs-lookup"><span data-stu-id="2386b-112">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="2386b-113">命名空間上不允許存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="2386b-113">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="2386b-114">命名空間沒有存取限制。</span><span class="sxs-lookup"><span data-stu-id="2386b-114">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="2386b-115">根據發生成員宣告的內容，僅允許某些已宣告存取範圍。</span><span class="sxs-lookup"><span data-stu-id="2386b-115">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="2386b-116">如果未在成員宣告中指定任何存取修飾詞，則會使用預設存取範圍。</span><span class="sxs-lookup"><span data-stu-id="2386b-116">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="2386b-117">未巢狀於其他類型中的最上層類型，只能有 `internal` 或 `public` 存取範圍。</span><span class="sxs-lookup"><span data-stu-id="2386b-117">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="2386b-118">這些類型的預設存取範圍是 `internal`。</span><span class="sxs-lookup"><span data-stu-id="2386b-118">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="2386b-119">巢狀型別 (即其他類型的成員) 可以有下表中所指出的已宣告存取範圍。</span><span class="sxs-lookup"><span data-stu-id="2386b-119">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="2386b-120">成員</span><span class="sxs-lookup"><span data-stu-id="2386b-120">Members of</span></span>|<span data-ttu-id="2386b-121">預設成員存取範圍</span><span class="sxs-lookup"><span data-stu-id="2386b-121">Default member accessibility</span></span>|<span data-ttu-id="2386b-122">允許的成員已宣告存取範圍</span><span class="sxs-lookup"><span data-stu-id="2386b-122">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="2386b-123">無</span><span class="sxs-lookup"><span data-stu-id="2386b-123">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="2386b-124">無</span><span class="sxs-lookup"><span data-stu-id="2386b-124">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="2386b-125">巢狀型別的存取範圍取決於其[存取範圍定義域](../../../csharp/language-reference/keywords/accessibility-domain.md)，這是由成員的已宣告存取範圍和立即包含類型的存取範圍定義域所決定。</span><span class="sxs-lookup"><span data-stu-id="2386b-125">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="2386b-126">但是，巢狀型別的存取範圍領域不能超過包含型別 (Containing Type) 的存取範圍領域。</span><span class="sxs-lookup"><span data-stu-id="2386b-126">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="2386b-127">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="2386b-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2386b-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2386b-128">See Also</span></span>  
 [<span data-ttu-id="2386b-129">C# 參考</span><span class="sxs-lookup"><span data-stu-id="2386b-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2386b-130">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2386b-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2386b-131">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="2386b-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="2386b-132">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="2386b-132">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="2386b-133">存取範圍定義域</span><span class="sxs-lookup"><span data-stu-id="2386b-133">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [<span data-ttu-id="2386b-134">使用存取範圍層級的限制</span><span class="sxs-lookup"><span data-stu-id="2386b-134">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [<span data-ttu-id="2386b-135">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="2386b-135">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="2386b-136">public</span><span class="sxs-lookup"><span data-stu-id="2386b-136">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="2386b-137">private</span><span class="sxs-lookup"><span data-stu-id="2386b-137">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="2386b-138">protected</span><span class="sxs-lookup"><span data-stu-id="2386b-138">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="2386b-139">internal</span><span class="sxs-lookup"><span data-stu-id="2386b-139">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
