---
title: 存取範圍層級 - C# 參考
ms.custom: seodec18
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: ca7bef8bf68b80015128619336db9fc6a8f5c237
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661815"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="0fe3f-102">存取範圍層級 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="0fe3f-102">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="0fe3f-103">使用存取修飾詞 `public`、`protected`、`internal` 或 `private` 來指定成員的下列其中一個已宣告存取範圍層級。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-103">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="0fe3f-104">已宣告存取範圍</span><span class="sxs-lookup"><span data-stu-id="0fe3f-104">Declared accessibility</span></span>|<span data-ttu-id="0fe3f-105">意義</span><span class="sxs-lookup"><span data-stu-id="0fe3f-105">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="0fe3f-106">未限制存取。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-106">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="0fe3f-107">存取限於包含類別或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="0fe3f-108">存取限於目前組件。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-108">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="0fe3f-109">存取限於目前組件或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="0fe3f-110">存取限於包含類型。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-110">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="0fe3f-111">存取限於目前組件內包含類別或衍生自包含類別的類型。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="0fe3f-112">自 C# 7.2 起可用。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-112">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="0fe3f-113">一個成員或類型只允許一個存取修飾詞，但合併使用 `protected internal` 或 `private protected` 時除外。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-113">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="0fe3f-114">命名空間上不允許存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-114">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="0fe3f-115">命名空間沒有存取限制。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-115">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="0fe3f-116">根據發生成員宣告的內容，僅允許某些已宣告存取範圍。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-116">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="0fe3f-117">如果未在成員宣告中指定任何存取修飾詞，則會使用預設存取範圍。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-117">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="0fe3f-118">未巢狀於其他類型中的最上層類型，只能有 `internal` 或 `public` 存取範圍。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-118">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="0fe3f-119">這些類型的預設存取範圍是 `internal`。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-119">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="0fe3f-120">巢狀型別 (即其他類型的成員) 可以有下表中所指出的已宣告存取範圍。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-120">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="0fe3f-121">成員</span><span class="sxs-lookup"><span data-stu-id="0fe3f-121">Members of</span></span>|<span data-ttu-id="0fe3f-122">預設成員存取範圍</span><span class="sxs-lookup"><span data-stu-id="0fe3f-122">Default member accessibility</span></span>|<span data-ttu-id="0fe3f-123">允許的成員已宣告存取範圍</span><span class="sxs-lookup"><span data-stu-id="0fe3f-123">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="0fe3f-124">無</span><span class="sxs-lookup"><span data-stu-id="0fe3f-124">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="0fe3f-125">無</span><span class="sxs-lookup"><span data-stu-id="0fe3f-125">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="0fe3f-126">巢狀型別的存取範圍取決於其[存取範圍定義域](../../../csharp/language-reference/keywords/accessibility-domain.md)，這是由成員的已宣告存取範圍和立即包含類型的存取範圍定義域所決定。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-126">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="0fe3f-127">但是，巢狀型別的存取範圍領域不能超過包含型別 (Containing Type) 的存取範圍領域。</span><span class="sxs-lookup"><span data-stu-id="0fe3f-127">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="0fe3f-128">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="0fe3f-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0fe3f-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fe3f-129">See also</span></span>
- [<span data-ttu-id="0fe3f-130">C# 參考</span><span class="sxs-lookup"><span data-stu-id="0fe3f-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="0fe3f-131">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="0fe3f-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0fe3f-132">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="0fe3f-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="0fe3f-133">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="0fe3f-133">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)
- [<span data-ttu-id="0fe3f-134">存取範圍定義域</span><span class="sxs-lookup"><span data-stu-id="0fe3f-134">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)
- [<span data-ttu-id="0fe3f-135">使用存取範圍層級的限制</span><span class="sxs-lookup"><span data-stu-id="0fe3f-135">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="0fe3f-136">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="0fe3f-136">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="0fe3f-137">public</span><span class="sxs-lookup"><span data-stu-id="0fe3f-137">public</span></span>](../../../csharp/language-reference/keywords/public.md)
- [<span data-ttu-id="0fe3f-138">private</span><span class="sxs-lookup"><span data-stu-id="0fe3f-138">private</span></span>](../../../csharp/language-reference/keywords/private.md)
- [<span data-ttu-id="0fe3f-139">protected</span><span class="sxs-lookup"><span data-stu-id="0fe3f-139">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
- [<span data-ttu-id="0fe3f-140">internal</span><span class="sxs-lookup"><span data-stu-id="0fe3f-140">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
