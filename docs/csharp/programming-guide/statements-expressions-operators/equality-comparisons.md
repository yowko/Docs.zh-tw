---
title: 相等比較 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- object equality [C#]
ms.assetid: 10b865ea-4e7b-4127-9242-c9b8f57d9f04
ms.openlocfilehash: 7cbd1a2c1a9968ae8ed4f96d503d472bbe9b32c4
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545451"
---
# <a name="equality-comparisons-c-programming-guide"></a><span data-ttu-id="81227-102">相等比較 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="81227-102">Equality comparisons (C# Programming Guide)</span></span>

<span data-ttu-id="81227-103">有時候需要比較兩個值是否相等。</span><span class="sxs-lookup"><span data-stu-id="81227-103">It is sometimes necessary to compare two values for equality.</span></span> <span data-ttu-id="81227-104">在某些情況下，您要測試「值是否相等」 (也稱為「等價」，表示兩個變數所含的值相等。</span><span class="sxs-lookup"><span data-stu-id="81227-104">In some cases, you are testing for *value equality*, also known as *equivalence*, which means that the values that are contained by the two variables are equal.</span></span> <span data-ttu-id="81227-105">在其他情況下，您必須判斷兩個變數是否參照記憶體中的相同基礎物件。</span><span class="sxs-lookup"><span data-stu-id="81227-105">In other cases, you have to determine whether two variables refer to the same underlying object in memory.</span></span> <span data-ttu-id="81227-106">這類型的相等稱為「參考相等」或「識別」。</span><span class="sxs-lookup"><span data-stu-id="81227-106">This type of equality is called *reference equality*, or *identity*.</span></span> <span data-ttu-id="81227-107">本主題描述這兩種相等，並提供其他主題的連結以取得詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="81227-107">This topic describes these two kinds of equality and provides links to other topics for more information.</span></span>  
  
## <a name="reference-equality"></a><span data-ttu-id="81227-108">參考相等</span><span class="sxs-lookup"><span data-stu-id="81227-108">Reference equality</span></span>

 <span data-ttu-id="81227-109">參考相等表示兩個物件參考都指向相同的基礎物件。</span><span class="sxs-lookup"><span data-stu-id="81227-109">Reference equality means that two object references refer to the same underlying object.</span></span> <span data-ttu-id="81227-110">這可能是透過簡單指派所發生，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="81227-110">This can occur through simple assignment, as shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideStatements#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#18)]  
  
 <span data-ttu-id="81227-111">在這個程式碼中，建立兩個物件，但在指派陳述式之後，這兩個參考都指向相同的物件。</span><span class="sxs-lookup"><span data-stu-id="81227-111">In this code, two objects are created, but after the assignment statement, both references refer to the same object.</span></span> <span data-ttu-id="81227-112">因此，它們具有參考相等。</span><span class="sxs-lookup"><span data-stu-id="81227-112">Therefore they have reference equality.</span></span> <span data-ttu-id="81227-113">使用 <xref:System.Object.ReferenceEquals%2A> 方法，以判斷兩個參考是否指向相同的物件。</span><span class="sxs-lookup"><span data-stu-id="81227-113">Use the <xref:System.Object.ReferenceEquals%2A> method to determine whether two references refer to the same object.</span></span>  
  
 <span data-ttu-id="81227-114">參考相等的概念只適用於參考類型。</span><span class="sxs-lookup"><span data-stu-id="81227-114">The concept of reference equality applies only to reference types.</span></span> <span data-ttu-id="81227-115">因為將實值型別的執行個體指派給變數時會建立實值的複本，所以實值型別物件不能具有參考相等。</span><span class="sxs-lookup"><span data-stu-id="81227-115">Value type objects cannot have reference equality because when an instance of a value type is assigned to a variable, a copy of the value is made.</span></span> <span data-ttu-id="81227-116">因此，您絕不會有兩個參照記憶體中相同位置的 Unboxed 結構。</span><span class="sxs-lookup"><span data-stu-id="81227-116">Therefore you can never have two unboxed structs that refer to the same location in memory.</span></span> <span data-ttu-id="81227-117">此外，如果您使用 <xref:System.Object.ReferenceEquals%2A> 來比較兩個實值型別，則結果一律為 `false`，即使物件中所包含的值完全相同也是一樣。</span><span class="sxs-lookup"><span data-stu-id="81227-117">Furthermore, if you use <xref:System.Object.ReferenceEquals%2A> to compare two value types, the result will always be `false`, even if the values that are contained in the objects are all identical.</span></span> <span data-ttu-id="81227-118">這是因為每個變數都會對個別物件執行個體進行 Boxed 處理。</span><span class="sxs-lookup"><span data-stu-id="81227-118">This is because each variable is boxed into a separate object instance.</span></span> <span data-ttu-id="81227-119">如需詳細資訊，請參閱[如何：參考相等 (識別) 的測試](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)。</span><span class="sxs-lookup"><span data-stu-id="81227-119">For more information, see [How to: Test for Reference Equality (Identity)](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md).</span></span>  

## <a name="value-equality"></a><span data-ttu-id="81227-120">實值相等</span><span class="sxs-lookup"><span data-stu-id="81227-120">Value equality</span></span>

 <span data-ttu-id="81227-121">實值相等表示兩個物件包含相同的值。</span><span class="sxs-lookup"><span data-stu-id="81227-121">Value equality means that two objects contain the same value or values.</span></span> <span data-ttu-id="81227-122">對於 [int](../../../csharp/language-reference/keywords/int.md) 或 [bool](../../../csharp/language-reference/keywords/bool.md) 這類基本實值型別，測試實值相等十分簡單。</span><span class="sxs-lookup"><span data-stu-id="81227-122">For primitive value types such as [int](../../../csharp/language-reference/keywords/int.md) or [bool](../../../csharp/language-reference/keywords/bool.md), tests for value equality are straightforward.</span></span> <span data-ttu-id="81227-123">您可以使用 [==](../../../csharp/language-reference/operators/equality-operators.md#equality-operator-) 運算子，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="81227-123">You can use the [==](../../../csharp/language-reference/operators/equality-operators.md#equality-operator-) operator, as shown in the following example.</span></span>  
  
```csharp  
int a = GetOriginalValue();  
int b = GetCurrentValue();  
  
// Test for value equality.   
if( b == a)   
{  
    // The two integers are equal.  
}  
```  
  
 <span data-ttu-id="81227-124">對於大部分其他類型，測試實值相等較為複雜，因為您需要了解類型如何定義它。</span><span class="sxs-lookup"><span data-stu-id="81227-124">For most other types, testing for value equality is more complex because it requires that you understand how the type defines it.</span></span> <span data-ttu-id="81227-125">對於具有多個欄位或屬性的類別和結構，通常會定義實值相等，表示所有欄位或屬性具有相同的值。</span><span class="sxs-lookup"><span data-stu-id="81227-125">For classes and structs that have multiple fields or properties, value equality is often defined to mean that all fields or properties have the same value.</span></span> <span data-ttu-id="81227-126">例如，如果 pointA.X 等於 pointB.X 而且 pointA.Y 等於 pointB.Y，則兩個 `Point` 物件可能定義為相等。</span><span class="sxs-lookup"><span data-stu-id="81227-126">For example, two `Point` objects might be defined to be equivalent if pointA.X is equal to pointB.X and pointA.Y is equal to pointB.Y.</span></span>  
  
 <span data-ttu-id="81227-127">不過，相等性不需要根據類型中的所有欄位。</span><span class="sxs-lookup"><span data-stu-id="81227-127">However, there is no requirement that equivalence be based on all the fields in a type.</span></span> <span data-ttu-id="81227-128">而是根據子集。</span><span class="sxs-lookup"><span data-stu-id="81227-128">It can be based on a subset.</span></span> <span data-ttu-id="81227-129">當您比較不屬於您的類型時，務必特別了解如何定義該類型的相等性。</span><span class="sxs-lookup"><span data-stu-id="81227-129">When you compare types that you do not own, you should make sure to understand specifically how equivalence is defined for that type.</span></span> <span data-ttu-id="81227-130">如需如何在您自己的類別和結構中定義實值相等的詳細資訊，請參閱[如何：定義類型的實值相等](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)。</span><span class="sxs-lookup"><span data-stu-id="81227-130">For more information about how to define value equality in your own classes and structs, see [How to: Define Value Equality for a Type](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md).</span></span>  
  
### <a name="value-equality-for-floating-point-values"></a><span data-ttu-id="81227-131">浮點值的實值相等</span><span class="sxs-lookup"><span data-stu-id="81227-131">Value equality for floating-point values</span></span>

 <span data-ttu-id="81227-132">浮點值的相等比較 ([double](../../../csharp/language-reference/keywords/double.md) 和 [float](../../../csharp/language-reference/keywords/float.md)) 有問題，因為二進位電腦上的浮點算術不精確。</span><span class="sxs-lookup"><span data-stu-id="81227-132">Equality comparisons of floating-point values ([double](../../../csharp/language-reference/keywords/double.md) and [float](../../../csharp/language-reference/keywords/float.md)) are problematic because of the imprecision of floating-point arithmetic on binary computers.</span></span> <span data-ttu-id="81227-133">如需詳細資訊，請參閱 <xref:System.Double?displayProperty=nameWithType> 主題中的備註。</span><span class="sxs-lookup"><span data-stu-id="81227-133">For more information, see the remarks in the topic <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="81227-134">相關主題</span><span class="sxs-lookup"><span data-stu-id="81227-134">Related topics</span></span>  
  
|<span data-ttu-id="81227-135">標題</span><span class="sxs-lookup"><span data-stu-id="81227-135">Title</span></span>|<span data-ttu-id="81227-136">說明</span><span class="sxs-lookup"><span data-stu-id="81227-136">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="81227-137">如何：參考相等 (識別) 的測試</span><span class="sxs-lookup"><span data-stu-id="81227-137">How to: Test for Reference Equality (Identity)</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-test-for-reference-equality-identity.md)|<span data-ttu-id="81227-138">描述如何判斷兩個變數是否具有參考相等。</span><span class="sxs-lookup"><span data-stu-id="81227-138">Describes how to determine whether two variables have reference equality.</span></span>|  
|[<span data-ttu-id="81227-139">如何：定義類型的實值相等</span><span class="sxs-lookup"><span data-stu-id="81227-139">How to: Define Value Equality for a Type</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-define-value-equality-for-a-type.md)|<span data-ttu-id="81227-140">描述如何提供類型實值相等的自訂定義。</span><span class="sxs-lookup"><span data-stu-id="81227-140">Describes how to provide a custom definition of value equality for a type.</span></span>|  
|[<span data-ttu-id="81227-141">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="81227-141">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)|<span data-ttu-id="81227-142">提供重要 C# 語言功能以及可透過 .NET Framework 以 C# 取得之功能的詳細資訊連結。</span><span class="sxs-lookup"><span data-stu-id="81227-142">Provides links to detailed information about important C# language features and features that are available to C# through the .NET Framework.</span></span>|  
|[<span data-ttu-id="81227-143">型別</span><span class="sxs-lookup"><span data-stu-id="81227-143">Types</span></span>](../../../csharp/programming-guide/types/index.md)|<span data-ttu-id="81227-144">提供 C# 類型系統的相關資訊以及其他資訊的連結。</span><span class="sxs-lookup"><span data-stu-id="81227-144">Provides information about the C# type system and links to additional information.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81227-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81227-145">See also</span></span>

- [<span data-ttu-id="81227-146">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="81227-146">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
