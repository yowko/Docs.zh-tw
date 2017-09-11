---
title: "如何：定義類型的實值相等 (C# 程式設計手冊) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#] , overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 33b2ab2252fac8442caa7b2f3e9b5b311cc0f9b6
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a><span data-ttu-id="7c340-102">如何：定義類型的實值相等 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="7c340-102">How to: Define Value Equality for a Type (C# Programming Guide)</span></span>
<span data-ttu-id="7c340-103">當您定義類別或結構時，需判斷是否有必要為類型建立實值相等 (或等價) 的自訂定義。</span><span class="sxs-lookup"><span data-stu-id="7c340-103">When you define a class or struct, you decide whether it makes sense to create a custom definition of value equality (or equivalence) for the type.</span></span> <span data-ttu-id="7c340-104">通常，當該類型的物件必須新增至某種集合，或物件的主要目的是為了儲存一組欄位或屬性時，就會實作實值相等。</span><span class="sxs-lookup"><span data-stu-id="7c340-104">Typically, you implement value equality when objects of the type are expected to be added to a collection of some sort, or when their primary purpose is to store a set of fields or properties.</span></span> <span data-ttu-id="7c340-105">您可以根據對該類型中所有欄位和屬性的比較來定義實值相等，也可以根據子集來進行定義。</span><span class="sxs-lookup"><span data-stu-id="7c340-105">You can base your definition of value equality on a comparison of all the fields and properties in the type, or you can base the definition on a subset.</span></span> <span data-ttu-id="7c340-106">不論使用哪種方法，在類別和結構中，您的實作都必須遵循下列五項等價保證：</span><span class="sxs-lookup"><span data-stu-id="7c340-106">But in either case, and in both classes and structs, your implementation should follow the five guarantees of equivalence:</span></span>  
  
1.  <span data-ttu-id="7c340-107">x.`Equals`(x) 會傳回 `true.`這稱為自反屬性。</span><span class="sxs-lookup"><span data-stu-id="7c340-107">x.`Equals`(x) returns `true.` This is called the reflexive property.</span></span>  
  
2.  <span data-ttu-id="7c340-108">x.`Equals`(y) 會傳回與 y.`Equals`(x) 相同的值。</span><span class="sxs-lookup"><span data-stu-id="7c340-108">x.`Equals`(y) returns the same value as y.`Equals`(x).</span></span> <span data-ttu-id="7c340-109">這稱為對稱屬性。</span><span class="sxs-lookup"><span data-stu-id="7c340-109">This is called the symmetric property.</span></span>  
  
3.  <span data-ttu-id="7c340-110">如果 (x.`Equals`(y) && y.`Equals`(z)) 傳回 `true`，則 x.`Equals`(z) 會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="7c340-110">if (x.`Equals`(y) && y.`Equals`(z)) returns `true`, then x.`Equals`(z) returns `true`.</span></span> <span data-ttu-id="7c340-111">這稱為可轉移屬性。</span><span class="sxs-lookup"><span data-stu-id="7c340-111">This is called the transitive property.</span></span>  
  
4.  <span data-ttu-id="7c340-112">只要 x 和 y 所參考的物件沒有經過修改，後續叫用 x.`Equals`(y) 就會傳回相同的值。</span><span class="sxs-lookup"><span data-stu-id="7c340-112">Successive invocations of x.`Equals`(y) return the same value as long as the objects referenced by x and y are not modified.</span></span>  
  
5.  <span data-ttu-id="7c340-113">x.`Equals`(null) 會傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="7c340-113">x.`Equals`(null) returns `false`.</span></span> <span data-ttu-id="7c340-114">不過，null.Equals(null) 會擲回例外狀況，而不會遵守上述第二項規則。</span><span class="sxs-lookup"><span data-stu-id="7c340-114">However, null.Equals(null) throws an exception; it does not obey rule number two above.</span></span>  
  
 <span data-ttu-id="7c340-115">您定義的任何結構已有實值相等的預設實作，這是從 <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> 方法的 <xref:System.ValueType?displayProperty=fullName> 覆寫繼承而來。</span><span class="sxs-lookup"><span data-stu-id="7c340-115">Any struct that you define already has a default implementation of value equality that it inherits from the <xref:System.ValueType?displayProperty=fullName> override of the <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> method.</span></span> <span data-ttu-id="7c340-116">此實作使用反映來檢查類型中的所有欄位和屬性。</span><span class="sxs-lookup"><span data-stu-id="7c340-116">This implementation uses reflection to examine all the fields and properties in the type.</span></span> <span data-ttu-id="7c340-117">雖然此實作會產生正確的結果，但相較於您針對該類型特別撰寫的自訂實作卻慢得多。</span><span class="sxs-lookup"><span data-stu-id="7c340-117">Although this implementation produces correct results, it is relatively slow compared to a custom implementation that you write specifically for the type.</span></span>  
  
 <span data-ttu-id="7c340-118">對類別和結構而言，實值相等的實作細節並不同。</span><span class="sxs-lookup"><span data-stu-id="7c340-118">The implementation details for value equality are different for classes and structs.</span></span> <span data-ttu-id="7c340-119">不過，類別和結構都需要相同的基本步驟來實作相等：</span><span class="sxs-lookup"><span data-stu-id="7c340-119">However, both classes and structs require the same basic steps for implementing equality:</span></span>  
  
1.  <span data-ttu-id="7c340-120">覆寫[虛擬](../../../csharp/language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> 方法。</span><span class="sxs-lookup"><span data-stu-id="7c340-120">Override the [virtual](../../../csharp/language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> method.</span></span> <span data-ttu-id="7c340-121">在大部分情況下，實作 `bool Equals( object obj )` 應該只會呼叫特定類型的 `Equals` 方法，這是 <xref:System.IEquatable%601?displayProperty=fullName> 介面的實作</span><span class="sxs-lookup"><span data-stu-id="7c340-121">In most cases, your implementation of `bool Equals( object obj )` should just call into the type-specific `Equals` method that is the implementation of the <xref:System.IEquatable%601?displayProperty=fullName> interface.</span></span> <span data-ttu-id="7c340-122">(請參閱步驟 2)。</span><span class="sxs-lookup"><span data-stu-id="7c340-122">(See step 2.)</span></span>  
  
2.  <span data-ttu-id="7c340-123">提供特定類型的 `Equals` 方法，以便實作 <xref:System.IEquatable%601?displayProperty=fullName> 介面。</span><span class="sxs-lookup"><span data-stu-id="7c340-123">Implement the <xref:System.IEquatable%601?displayProperty=fullName> interface by providing a type-specific `Equals` method.</span></span> <span data-ttu-id="7c340-124">實際的等價比較是在這裡執行。</span><span class="sxs-lookup"><span data-stu-id="7c340-124">This is where the actual equivalence comparison is performed.</span></span> <span data-ttu-id="7c340-125">例如，您可能決定只比較類型中的一個或兩個欄位，以定義相等。</span><span class="sxs-lookup"><span data-stu-id="7c340-125">For example, you might decide to define equality by comparing only one or two fields in your type.</span></span> <span data-ttu-id="7c340-126">不會從 `Equals` 擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7c340-126">Do not throw exceptions from `Equals`.</span></span> <span data-ttu-id="7c340-127">僅適用於類別：此方法只會檢查在類別中宣告的欄位。</span><span class="sxs-lookup"><span data-stu-id="7c340-127">For classes only: This method should examine only fields that are declared in the class.</span></span> <span data-ttu-id="7c340-128">它應該呼叫 `base.Equals` 以檢查基底類別中的欄位</span><span class="sxs-lookup"><span data-stu-id="7c340-128">It should call `base.Equals` to examine fields that are in the base class.</span></span> <span data-ttu-id="7c340-129">(如果類型直接繼承自 <xref:System.Object>，則請勿這樣做，因為 <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> 的 <xref:System.Object> 實作會執行參考相等檢查)。</span><span class="sxs-lookup"><span data-stu-id="7c340-129">(Do not do this if the type inherits directly from <xref:System.Object>, because the <xref:System.Object> implementation of <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> performs a reference equality check.)</span></span>  
  
3.  <span data-ttu-id="7c340-130">選用但為建議動作︰多載 [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) 和 [!=](../../../csharp/language-reference/operators/not-equal-operator.md) 運算子。</span><span class="sxs-lookup"><span data-stu-id="7c340-130">Optional but recommended: Overload the [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) and [!=](../../../csharp/language-reference/operators/not-equal-operator.md) operators.</span></span>  
  
4.  <span data-ttu-id="7c340-131">覆寫 <xref:System.Object.GetHashCode%2A?displayProperty=fullName>，讓具有實值相等的兩個物件可以產生相同的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="7c340-131">Override <xref:System.Object.GetHashCode%2A?displayProperty=fullName> so that two objects that have value equality produce the same hash code.</span></span>  
  
5.  <span data-ttu-id="7c340-132">選用︰若要支援「大於」或「小於」的定義，請為類型實作 <xref:System.IComparable%601> 介面，並同時多載 [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) 和 [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) 運算子。</span><span class="sxs-lookup"><span data-stu-id="7c340-132">Optional: To support definitions for "greater than" or "less than," implement the <xref:System.IComparable%601> interface for your type, and also overload the [<=](../../../csharp/language-reference/operators/less-than-equal-operator.md) and [>=](../../../csharp/language-reference/operators/greater-than-equal-operator.md) operators.</span></span>  
  
 <span data-ttu-id="7c340-133">接下來的第一個範例示範類別實作。</span><span class="sxs-lookup"><span data-stu-id="7c340-133">The first example that follows shows a class implementation.</span></span> <span data-ttu-id="7c340-134">第二個範例示範結構實作。</span><span class="sxs-lookup"><span data-stu-id="7c340-134">The second example shows a struct implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c340-135">範例</span><span class="sxs-lookup"><span data-stu-id="7c340-135">Example</span></span>  
 <span data-ttu-id="7c340-136">下列範例示範如何在類別 (參考型別) 中實作實值相等。</span><span class="sxs-lookup"><span data-stu-id="7c340-136">The following example shows how to implement value equality in a class (reference type).</span></span>  
  
 <span data-ttu-id="7c340-137">[!code-cs[csProgGuideStatements#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="7c340-137">[!code-cs[csProgGuideStatements#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_1.cs)]</span></span>  
  
 <span data-ttu-id="7c340-138">在類別 (參考型別) 上，<xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> 方法的預設實作都是執行參考相等比較，而不是實值相等檢查。</span><span class="sxs-lookup"><span data-stu-id="7c340-138">On classes (reference types), the default implementation of both <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> methods performs a reference equality comparison, not a value equality check.</span></span> <span data-ttu-id="7c340-139">當實作器覆寫虛擬方法時，其目的是為了提供實值相等語意。</span><span class="sxs-lookup"><span data-stu-id="7c340-139">When an implementer overrides the virtual method, the purpose is to give it value equality semantics.</span></span>  
  
 <span data-ttu-id="7c340-140">`==` 和 `!=` 運算子可以和類別搭配使用，即使類別未多載這些運算子也一樣。</span><span class="sxs-lookup"><span data-stu-id="7c340-140">The `==` and `!=` operators can be used with classes even if the class does not overload them.</span></span> <span data-ttu-id="7c340-141">不過，預設行為是執行參考相等檢查。</span><span class="sxs-lookup"><span data-stu-id="7c340-141">However, the default behavior is to perform a reference equality check.</span></span> <span data-ttu-id="7c340-142">在類別中，如果您多載 `Equals` 方法，您應該多載 `==` 和 `!=` 運算子，但這並非必要。</span><span class="sxs-lookup"><span data-stu-id="7c340-142">In a class, if you overload the `Equals` method, you should overload the `==` and `!=` operators, but it is not required.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c340-143">範例</span><span class="sxs-lookup"><span data-stu-id="7c340-143">Example</span></span>  
 <span data-ttu-id="7c340-144">下列範例示範如何在結構 (實值型別) 中實作實值相等：</span><span class="sxs-lookup"><span data-stu-id="7c340-144">The following example shows how to implement value equality in a struct (value type):</span></span>  
  
 <span data-ttu-id="7c340-145">[!code-cs[csProgGuideStatements#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="7c340-145">[!code-cs[csProgGuideStatements#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_2.cs)]</span></span>  
  
 <span data-ttu-id="7c340-146">對於結構，<xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> 的預設實作 (這是 <xref:System.ValueType?displayProperty=fullName> 中的覆寫版本) 會使用反映來比較類型中每個欄位的值，以便執行實值相等檢查。</span><span class="sxs-lookup"><span data-stu-id="7c340-146">For structs, the default implementation of <xref:System.Object.Equals%28System.Object%29?displayProperty=fullName> (which is the overridden version in <xref:System.ValueType?displayProperty=fullName>) performs a value equality check by using reflection to compare the values of every field in the type.</span></span> <span data-ttu-id="7c340-147">當實作器覆寫結構中的虛擬 `Equals` 方法時，其目的是為了提供更有效率的方法來執行實值相等檢查，以及選擇性地根據結構的一部分欄位或屬性進行比較。</span><span class="sxs-lookup"><span data-stu-id="7c340-147">When an implementer overrides the virtual `Equals` method in a struct, the purpose is to provide a more efficient means of performing the value equality check and optionally to base the comparison on some subset of the struct's field or properties.</span></span>  
  
 <span data-ttu-id="7c340-148">除非結構明確多載 [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) 和 [!=](../../../csharp/language-reference/operators/not-equal-operator.md) 運算子，否則這些運算子無法用於結構。</span><span class="sxs-lookup"><span data-stu-id="7c340-148">The [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) and [!=](../../../csharp/language-reference/operators/not-equal-operator.md) operators cannot operate on a struct unless the struct explicitly overloads them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c340-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c340-149">See Also</span></span>  
 <span data-ttu-id="7c340-150">[相等比較](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md) </span><span class="sxs-lookup"><span data-stu-id="7c340-150">[Equality Comparisons](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md) </span></span>  
<span data-ttu-id="7c340-151"> [C# 程式設計指南](../../../csharp/programming-guide/index.md)</span><span class="sxs-lookup"><span data-stu-id="7c340-151"> [C# Programming Guide](../../../csharp/programming-guide/index.md)</span></span>

