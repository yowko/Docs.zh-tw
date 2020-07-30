---
title: 相等比較 - C# 程式設計指南
description: 瞭解相等比較。 請參閱「實值相等」和「參考相等」的描述，並查看其他資源。
ms.date: 07/20/2015
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
ms.openlocfilehash: d10d1851978ef25b7b02503f196cd2a436aab608
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381680"
---
# <a name="equality-comparisons-c-programming-guide"></a><span data-ttu-id="ad954-104">相等比較 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="ad954-104">Equality comparisons (C# Programming Guide)</span></span>

<span data-ttu-id="ad954-105">有時候需要比較兩個值是否相等。</span><span class="sxs-lookup"><span data-stu-id="ad954-105">It is sometimes necessary to compare two values for equality.</span></span> <span data-ttu-id="ad954-106">在某些情況下，您要測試「值是否相等」\*\* (也稱為「等價」\*\*，表示兩個變數所含的值相等。</span><span class="sxs-lookup"><span data-stu-id="ad954-106">In some cases, you are testing for *value equality*, also known as *equivalence*, which means that the values that are contained by the two variables are equal.</span></span> <span data-ttu-id="ad954-107">在其他情況下，您必須判斷兩個變數是否參照記憶體中的相同基礎物件。</span><span class="sxs-lookup"><span data-stu-id="ad954-107">In other cases, you have to determine whether two variables refer to the same underlying object in memory.</span></span> <span data-ttu-id="ad954-108">這類型的相等稱為「參考相等」\*\* 或「識別」\*\*。</span><span class="sxs-lookup"><span data-stu-id="ad954-108">This type of equality is called *reference equality*, or *identity*.</span></span> <span data-ttu-id="ad954-109">本主題描述這兩種相等，並提供其他主題的連結以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="ad954-109">This topic describes these two kinds of equality and provides links to other topics for more information.</span></span>  
  
## <a name="reference-equality"></a><span data-ttu-id="ad954-110">參考相等</span><span class="sxs-lookup"><span data-stu-id="ad954-110">Reference equality</span></span>

 <span data-ttu-id="ad954-111">參考相等表示兩個物件參考都指向相同的基礎物件。</span><span class="sxs-lookup"><span data-stu-id="ad954-111">Reference equality means that two object references refer to the same underlying object.</span></span> <span data-ttu-id="ad954-112">這可能是透過簡單指派所發生，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ad954-112">This can occur through simple assignment, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideStatements#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#18)]  
  
 <span data-ttu-id="ad954-113">在這個程式碼中，建立兩個物件，但在指派陳述式之後，這兩個參考都指向相同的物件。</span><span class="sxs-lookup"><span data-stu-id="ad954-113">In this code, two objects are created, but after the assignment statement, both references refer to the same object.</span></span> <span data-ttu-id="ad954-114">因此，它們具有參考相等。</span><span class="sxs-lookup"><span data-stu-id="ad954-114">Therefore they have reference equality.</span></span> <span data-ttu-id="ad954-115">使用 <xref:System.Object.ReferenceEquals%2A> 方法，以判斷兩個參考是否指向相同的物件。</span><span class="sxs-lookup"><span data-stu-id="ad954-115">Use the <xref:System.Object.ReferenceEquals%2A> method to determine whether two references refer to the same object.</span></span>  
  
<span data-ttu-id="ad954-116">參考相等的概念只適用於參考類型。</span><span class="sxs-lookup"><span data-stu-id="ad954-116">The concept of reference equality applies only to reference types.</span></span> <span data-ttu-id="ad954-117">因為將實值型別的執行個體指派給變數時會建立實值的複本，所以實值型別物件不能具有參考相等。</span><span class="sxs-lookup"><span data-stu-id="ad954-117">Value type objects cannot have reference equality because when an instance of a value type is assigned to a variable, a copy of the value is made.</span></span> <span data-ttu-id="ad954-118">因此，您絕不會有兩個參照記憶體中相同位置的 Unboxed 結構。</span><span class="sxs-lookup"><span data-stu-id="ad954-118">Therefore you can never have two unboxed structs that refer to the same location in memory.</span></span> <span data-ttu-id="ad954-119">此外，如果您使用 <xref:System.Object.ReferenceEquals%2A> 來比較兩個實值型別，則結果一律為 `false`，即使物件中所包含的值完全相同也是一樣。</span><span class="sxs-lookup"><span data-stu-id="ad954-119">Furthermore, if you use <xref:System.Object.ReferenceEquals%2A> to compare two value types, the result will always be `false`, even if the values that are contained in the objects are all identical.</span></span> <span data-ttu-id="ad954-120">這是因為每個變數都會對個別物件執行個體進行 Boxed 處理。</span><span class="sxs-lookup"><span data-stu-id="ad954-120">This is because each variable is boxed into a separate object instance.</span></span> <span data-ttu-id="ad954-121">如需詳細資訊，請參閱[如何測試參考是否相等（身分識別）](./how-to-test-for-reference-equality-identity.md)。</span><span class="sxs-lookup"><span data-stu-id="ad954-121">For more information, see [How to test for reference equality (Identity)](./how-to-test-for-reference-equality-identity.md).</span></span>

## <a name="value-equality"></a><span data-ttu-id="ad954-122">實值相等</span><span class="sxs-lookup"><span data-stu-id="ad954-122">Value equality</span></span>

 <span data-ttu-id="ad954-123">實值相等表示兩個物件包含相同的值。</span><span class="sxs-lookup"><span data-stu-id="ad954-123">Value equality means that two objects contain the same value or values.</span></span> <span data-ttu-id="ad954-124">對於 [int](../../language-reference/builtin-types/integral-numeric-types.md) 或 [bool](../../language-reference/builtin-types/bool.md) 這類基本實值型別，測試實值相等十分簡單。</span><span class="sxs-lookup"><span data-stu-id="ad954-124">For primitive value types such as [int](../../language-reference/builtin-types/integral-numeric-types.md) or [bool](../../language-reference/builtin-types/bool.md), tests for value equality are straightforward.</span></span> <span data-ttu-id="ad954-125">您可以使用 [==](../../language-reference/operators/equality-operators.md#equality-operator-) 運算子，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="ad954-125">You can use the [==](../../language-reference/operators/equality-operators.md#equality-operator-) operator, as shown in the following example.</span></span>  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.
if (b == a)
{  
    // The two integers are equal.  
}  
```  
  
 <span data-ttu-id="ad954-126">對於大部分其他類型，測試實值相等較為複雜，因為您需要了解類型如何定義它。</span><span class="sxs-lookup"><span data-stu-id="ad954-126">For most other types, testing for value equality is more complex because it requires that you understand how the type defines it.</span></span> <span data-ttu-id="ad954-127">對於具有多個欄位或屬性的類別和結構，通常會定義實值相等，表示所有欄位或屬性具有相同的值。</span><span class="sxs-lookup"><span data-stu-id="ad954-127">For classes and structs that have multiple fields or properties, value equality is often defined to mean that all fields or properties have the same value.</span></span> <span data-ttu-id="ad954-128">例如，如果 pointA.X 等於 pointB.X 而且 pointA.Y 等於 pointB.Y，則兩個 `Point` 物件可能定義為相等。</span><span class="sxs-lookup"><span data-stu-id="ad954-128">For example, two `Point` objects might be defined to be equivalent if pointA.X is equal to pointB.X and pointA.Y is equal to pointB.Y.</span></span>  
  
<span data-ttu-id="ad954-129">不過，相等性不需要根據類型中的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="ad954-129">However, there is no requirement that equivalence be based on all the fields in a type.</span></span> <span data-ttu-id="ad954-130">而是根據子集。</span><span class="sxs-lookup"><span data-stu-id="ad954-130">It can be based on a subset.</span></span> <span data-ttu-id="ad954-131">當您比較不屬於您的類型時，務必特別了解如何定義該類型的相等性。</span><span class="sxs-lookup"><span data-stu-id="ad954-131">When you compare types that you do not own, you should make sure to understand specifically how equivalence is defined for that type.</span></span> <span data-ttu-id="ad954-132">如需如何在您自己的類別和結構中定義實值相等的詳細資訊，請參閱[如何定義類型的實值相等](./how-to-define-value-equality-for-a-type.md)。</span><span class="sxs-lookup"><span data-stu-id="ad954-132">For more information about how to define value equality in your own classes and structs, see [How to define value equality for a type](./how-to-define-value-equality-for-a-type.md).</span></span>
  
### <a name="value-equality-for-floating-point-values"></a><span data-ttu-id="ad954-133">浮點值的實值相等</span><span class="sxs-lookup"><span data-stu-id="ad954-133">Value equality for floating-point values</span></span>

 <span data-ttu-id="ad954-134">浮點值的相等比較 ([double](../../language-reference/builtin-types/floating-point-numeric-types.md) 和 [float](../../language-reference/builtin-types/floating-point-numeric-types.md)) 有問題，因為二進位電腦上的浮點算術不精確。</span><span class="sxs-lookup"><span data-stu-id="ad954-134">Equality comparisons of floating-point values ([double](../../language-reference/builtin-types/floating-point-numeric-types.md) and [float](../../language-reference/builtin-types/floating-point-numeric-types.md)) are problematic because of the imprecision of floating-point arithmetic on binary computers.</span></span> <span data-ttu-id="ad954-135">如需詳細資訊，請參閱 <xref:System.Double?displayProperty=nameWithType> 主題中的備註。</span><span class="sxs-lookup"><span data-stu-id="ad954-135">For more information, see the remarks in the topic <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="ad954-136">相關主題</span><span class="sxs-lookup"><span data-stu-id="ad954-136">Related topics</span></span>  
  
|<span data-ttu-id="ad954-137">標題</span><span class="sxs-lookup"><span data-stu-id="ad954-137">Title</span></span>|<span data-ttu-id="ad954-138">描述</span><span class="sxs-lookup"><span data-stu-id="ad954-138">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="ad954-139">如何測試參考是否相等（識別）</span><span class="sxs-lookup"><span data-stu-id="ad954-139">How to test for reference equality (Identity)</span></span>](./how-to-test-for-reference-equality-identity.md)|<span data-ttu-id="ad954-140">描述如何判斷兩個變數是否具有參考相等。</span><span class="sxs-lookup"><span data-stu-id="ad954-140">Describes how to determine whether two variables have reference equality.</span></span>|  
|[<span data-ttu-id="ad954-141">如何定義類型的實值相等性</span><span class="sxs-lookup"><span data-stu-id="ad954-141">How to define value equality for a type</span></span>](./how-to-define-value-equality-for-a-type.md)|<span data-ttu-id="ad954-142">描述如何提供類型實值相等的自訂定義。</span><span class="sxs-lookup"><span data-stu-id="ad954-142">Describes how to provide a custom definition of value equality for a type.</span></span>|  
|[<span data-ttu-id="ad954-143">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ad954-143">C# Programming Guide</span></span>](../index.md)|<span data-ttu-id="ad954-144">提供有關 c # 透過 .NET 提供之重要 c # 語言功能和功能的詳細資訊連結。</span><span class="sxs-lookup"><span data-stu-id="ad954-144">Provides links to detailed information about important C# language features and features that are available to C# through .NET.</span></span>|  
|[<span data-ttu-id="ad954-145">類型</span><span class="sxs-lookup"><span data-stu-id="ad954-145">Types</span></span>](../types/index.md)|<span data-ttu-id="ad954-146">提供 C# 類型系統的相關資訊以及其他資訊的連結。</span><span class="sxs-lookup"><span data-stu-id="ad954-146">Provides information about the C# type system and links to additional information.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ad954-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ad954-147">See also</span></span>

- [<span data-ttu-id="ad954-148">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ad954-148">C# Programming Guide</span></span>](../index.md)
