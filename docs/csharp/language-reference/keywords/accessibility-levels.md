---
description: 存取範圍層級 - C# 參考
title: 存取範圍層級 - C# 參考
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 6e1a5bddc0d40b0b62c7b07dbc6b4134a3447a95
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168786"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="6b0ae-103">存取範圍層級 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="6b0ae-103">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="6b0ae-104">使用存取修飾詞 `public`、`protected`、`internal` 或 `private` 來指定成員的下列其中一個已宣告存取範圍層級。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-104">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="6b0ae-105">已宣告存取範圍</span><span class="sxs-lookup"><span data-stu-id="6b0ae-105">Declared accessibility</span></span>|<span data-ttu-id="6b0ae-106">意義</span><span class="sxs-lookup"><span data-stu-id="6b0ae-106">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="6b0ae-107">未限制存取。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-107">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="6b0ae-108">存取限於包含類別或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-108">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="6b0ae-109">存取限於目前組件。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-109">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="6b0ae-110">存取限於目前組件或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-110">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="6b0ae-111">存取限於包含類型。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-111">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="6b0ae-112">存取限於目前組件內包含類別或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-112">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="6b0ae-113">自 C# 7.2 起可用。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-113">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="6b0ae-114">一個成員或類型只允許一個存取修飾詞，但合併使用 `protected internal` 或 `private protected` 時除外。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-114">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="6b0ae-115">命名空間上不允許存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-115">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="6b0ae-116">命名空間沒有存取限制。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-116">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="6b0ae-117">根據發生成員宣告的內容，僅允許某些已宣告存取範圍。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-117">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="6b0ae-118">如果未在成員宣告中指定任何存取修飾詞，則會使用預設存取範圍。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-118">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="6b0ae-119">未巢狀於其他類型中的最上層類型，只能有 `internal` 或 `public` 存取範圍。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-119">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="6b0ae-120">這些類型的預設存取範圍是 `internal`。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-120">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="6b0ae-121">巢狀型別 (即其他類型的成員) 可以有下表中所指出的已宣告存取範圍。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-121">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="6b0ae-122">成員</span><span class="sxs-lookup"><span data-stu-id="6b0ae-122">Members of</span></span>|<span data-ttu-id="6b0ae-123">預設成員存取範圍</span><span class="sxs-lookup"><span data-stu-id="6b0ae-123">Default member accessibility</span></span>|<span data-ttu-id="6b0ae-124">允許的成員已宣告存取範圍</span><span class="sxs-lookup"><span data-stu-id="6b0ae-124">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="6b0ae-125">無</span><span class="sxs-lookup"><span data-stu-id="6b0ae-125">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="6b0ae-126">無</span><span class="sxs-lookup"><span data-stu-id="6b0ae-126">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="6b0ae-127">巢狀型別的存取範圍取決於其 [存取範圍網域](./accessibility-domain.md)，這取決於成員的宣告存取範圍和立即包含類型的存取範圍定義域。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-127">The accessibility of a nested type depends on its [accessibility domain](./accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="6b0ae-128">但是，巢狀型別的存取範圍領域不能超過包含型別 (Containing Type) 的存取範圍領域。</span><span class="sxs-lookup"><span data-stu-id="6b0ae-128">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6b0ae-129">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="6b0ae-129">C# Language Specification</span></span>  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6b0ae-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b0ae-130">See also</span></span>

- [<span data-ttu-id="6b0ae-131">C # 參考</span><span class="sxs-lookup"><span data-stu-id="6b0ae-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6b0ae-132">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6b0ae-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6b0ae-133">C # 關鍵字</span><span class="sxs-lookup"><span data-stu-id="6b0ae-133">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="6b0ae-134">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="6b0ae-134">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="6b0ae-135">協助工具定義域</span><span class="sxs-lookup"><span data-stu-id="6b0ae-135">Accessibility Domain</span></span>](./accessibility-domain.md)
- [<span data-ttu-id="6b0ae-136">使用協助工具層級的限制</span><span class="sxs-lookup"><span data-stu-id="6b0ae-136">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="6b0ae-137">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="6b0ae-137">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="6b0ae-138">public</span><span class="sxs-lookup"><span data-stu-id="6b0ae-138">public</span></span>](./public.md)
- [<span data-ttu-id="6b0ae-139">private</span><span class="sxs-lookup"><span data-stu-id="6b0ae-139">private</span></span>](./private.md)
- [<span data-ttu-id="6b0ae-140">protected</span><span class="sxs-lookup"><span data-stu-id="6b0ae-140">protected</span></span>](./protected.md)
- [<span data-ttu-id="6b0ae-141">internal</span><span class="sxs-lookup"><span data-stu-id="6b0ae-141">internal</span></span>](./internal.md)
