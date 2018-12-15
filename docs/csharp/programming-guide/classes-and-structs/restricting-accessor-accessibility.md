---
title: 限制存取子的存取範圍 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accesibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: 1dd0f81a454475d6d668324198eb498cdfe20310
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149539"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="982f5-102">限制存取子的存取範圍 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="982f5-102">Restricting Accessor Accessibility (C# Programming Guide)</span></span>
<span data-ttu-id="982f5-103">屬性或索引子的 [get](../../../csharp/language-reference/keywords/get.md) 和 [set](../../../csharp/language-reference/keywords/set.md) 部分稱為「存取子」。</span><span class="sxs-lookup"><span data-stu-id="982f5-103">The [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="982f5-104">根據預設，這些存取子具有其所屬屬性或索引子的相同可見度或存取層級。</span><span class="sxs-lookup"><span data-stu-id="982f5-104">By default these accessors have the same visibility or access level of the property or indexer to which they belong.</span></span> <span data-ttu-id="982f5-105">如需詳細資訊，請參閱[存取範圍層級](../../../csharp/language-reference/keywords/accessibility-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="982f5-105">For more information, see [accessibility levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="982f5-106">不過，限制其中一個存取子的存取權時，這有時十分有用。</span><span class="sxs-lookup"><span data-stu-id="982f5-106">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="982f5-107">一般而言，這包含限制 `set` 存取子的存取範圍，同時保留可公開存取的 `get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="982f5-107">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="982f5-108">例如：</span><span class="sxs-lookup"><span data-stu-id="982f5-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_1.cs)]  
  
 <span data-ttu-id="982f5-109">在此範例中，稱為 `Name` 的屬性定義 `get` 和 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="982f5-109">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="982f5-110">`get` 存取子會接收屬性本身的存取範圍階層 (在此情況下為 `public`)，同時將 [protected](../../../csharp/language-reference/keywords/protected.md) 存取修飾詞套用至存取子本身以明確限制 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="982f5-110">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../../csharp/language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="982f5-111">存取子的存取修飾詞限制</span><span class="sxs-lookup"><span data-stu-id="982f5-111">Restrictions on Access Modifiers on Accessors</span></span>  
 <span data-ttu-id="982f5-112">在屬性或索引子上使用存取子修飾詞受限於這些條件：</span><span class="sxs-lookup"><span data-stu-id="982f5-112">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
-   <span data-ttu-id="982f5-113">您無法在介面或明確[介面](../../../csharp/language-reference/keywords/interface.md)成員實作上使用存取子修飾詞。</span><span class="sxs-lookup"><span data-stu-id="982f5-113">You cannot use accessor modifiers on an interface or an explicit [interface](../../../csharp/language-reference/keywords/interface.md) member implementation.</span></span>  
  
-   <span data-ttu-id="982f5-114">只有在屬性或索引子同時具有 `set` 和 `get` 存取子時，才能使用存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="982f5-114">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="982f5-115">在此情況下，允許只在兩個存取子之一上使用修飾詞。</span><span class="sxs-lookup"><span data-stu-id="982f5-115">In this case, the modifier is permitted on one only of the two accessors.</span></span>  
  
-   <span data-ttu-id="982f5-116">如果屬性或索引子具有 [override](../../../csharp/language-reference/keywords/override.md) 修飾詞，則存取子修飾詞必須符合已覆寫存取子的存取子 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="982f5-116">If the property or indexer has an [override](../../../csharp/language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
-   <span data-ttu-id="982f5-117">存取子上的存取範圍層級必須比屬性或索引子本身上的存取範圍層級更為嚴格。</span><span class="sxs-lookup"><span data-stu-id="982f5-117">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="982f5-118">覆寫存取子上的存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="982f5-118">Access Modifiers on Overriding Accessors</span></span>  
 <span data-ttu-id="982f5-119">當您覆寫屬性或索引子時，覆寫端程式碼必須可以存取覆寫的存取子。</span><span class="sxs-lookup"><span data-stu-id="982f5-119">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="982f5-120">此外，屬性/索引子及其存取子的存取範圍必須符合已覆寫的對應屬性/索引子及其存取子。</span><span class="sxs-lookup"><span data-stu-id="982f5-120">Also, the accessibility of both the property/indexer and its accessors must match the corresponding overridden property/indexer and its accessors.</span></span> <span data-ttu-id="982f5-121">例如：</span><span class="sxs-lookup"><span data-stu-id="982f5-121">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_2.cs)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="982f5-122">實作介面</span><span class="sxs-lookup"><span data-stu-id="982f5-122">Implementing Interfaces</span></span>  
 <span data-ttu-id="982f5-123">當您使用存取子實作介面時，存取子不能有存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="982f5-123">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="982f5-124">不過，如果您使用一個存取子 (例如 `get`) 實作介面，其他存取子可以有存取修飾詞，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="982f5-124">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_3.cs)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="982f5-125">存取子存取範圍定義域</span><span class="sxs-lookup"><span data-stu-id="982f5-125">Accessor Accessibility Domain</span></span>  
 <span data-ttu-id="982f5-126">如果您在存取子上使用存取修飾詞，這個修飾詞會判斷存取子的[存取範圍定義域](../../../csharp/language-reference/keywords/accessibility-domain.md)。</span><span class="sxs-lookup"><span data-stu-id="982f5-126">If you use an access modifier on the accessor, the [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="982f5-127">如果您未在存取子上使用存取修飾詞，屬性或索引子的存取範圍層級會判斷存取子的存取範圍定義域。</span><span class="sxs-lookup"><span data-stu-id="982f5-127">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="982f5-128">範例</span><span class="sxs-lookup"><span data-stu-id="982f5-128">Example</span></span>  
 <span data-ttu-id="982f5-129">下列範例包含三個類別：`BaseClass`、`DerivedClass` 和 `MainClass`。</span><span class="sxs-lookup"><span data-stu-id="982f5-129">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="982f5-130">這兩個類別的 `BaseClass`、`Name` 和 `Id` 上有兩個屬性。</span><span class="sxs-lookup"><span data-stu-id="982f5-130">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="982f5-131">此範例示範當您使用 [protected](../../../csharp/language-reference/keywords/protected.md) 或 [private](../../../csharp/language-reference/keywords/private.md) 這類限制存取修飾詞時，`BaseClass` 上的 `Id` 屬性可以隱藏 `DerivedClass` 上的 `Id` 屬性。</span><span class="sxs-lookup"><span data-stu-id="982f5-131">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../../csharp/language-reference/keywords/protected.md) or [private](../../../csharp/language-reference/keywords/private.md).</span></span> <span data-ttu-id="982f5-132">因此，當您將值指派給這個屬性時，會改為呼叫 `BaseClass` 類別上的屬性。</span><span class="sxs-lookup"><span data-stu-id="982f5-132">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="982f5-133">將存取修飾詞取代為 [public](../../../csharp/language-reference/keywords/public.md) 會將屬性設為可存取。</span><span class="sxs-lookup"><span data-stu-id="982f5-133">Replacing the access modifier by [public](../../../csharp/language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="982f5-134">此範例也會示範 `DerivedClass` 中 `Name` 屬性之 `set` 存取子上的 `private` 或 `protected` 這類限制性存取修飾詞防止存取存取子，並在您指派給它時產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="982f5-134">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_4.cs)]  
  
## <a name="comments"></a><span data-ttu-id="982f5-135">註解</span><span class="sxs-lookup"><span data-stu-id="982f5-135">Comments</span></span>  
 <span data-ttu-id="982f5-136">請注意，如果您將宣告 `new private string Id` 取代為 `new public string Id`，則會取得輸出：</span><span class="sxs-lookup"><span data-stu-id="982f5-136">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="982f5-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="982f5-137">See Also</span></span>

- [<span data-ttu-id="982f5-138">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="982f5-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="982f5-139">屬性</span><span class="sxs-lookup"><span data-stu-id="982f5-139">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [<span data-ttu-id="982f5-140">索引子</span><span class="sxs-lookup"><span data-stu-id="982f5-140">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
- [<span data-ttu-id="982f5-141">存取修飾詞</span><span class="sxs-lookup"><span data-stu-id="982f5-141">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
