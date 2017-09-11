---
title: "where (泛型類型條件約束) (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: 10
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
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 3f6960787fb1e9d2c2b8607d5d6852ecc9df17aa
ms.contentlocale: zh-tw
ms.lasthandoff: 05/26/2017

---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="cbe24-102">where (泛型類型條件約束) (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="cbe24-102">where (generic type constraint) (C# Reference)</span></span>
<span data-ttu-id="cbe24-103">在泛型類型定義中，`where` 子句是用來指定類型的條件約束，而這些類型可以用作泛型宣告中所定義類型參數的引數。</span><span class="sxs-lookup"><span data-stu-id="cbe24-103">In a generic type definition, the `where` clause is used to specify constraints on the types that can be used as arguments for a type parameter defined in a generic declaration.</span></span> <span data-ttu-id="cbe24-104">例如，您可以宣告泛型類別 `MyGenericClass`，讓類型參數 `T` 實作 <xref:System.IComparable%601> 介面：</span><span class="sxs-lookup"><span data-stu-id="cbe24-104">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>  
  
```csharp  
public class MyGenericClass<T> where T:IComparable { }  
```  
  
> [!NOTE]
>  <span data-ttu-id="cbe24-105">如需查詢運算式中 where 子句的詳細資訊，請參閱 [where 子句](../../../csharp/language-reference/keywords/where-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="cbe24-105">For more information on the where clause in a query expression, see [where clause](../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
 <span data-ttu-id="cbe24-106">除了介面條件約束之外，`where` 子句可以包含基底類別條件約束，說明類型必須將指定的類別作為基底類別 (或該類別本身)，才能用作該泛型類型的類型引數。</span><span class="sxs-lookup"><span data-stu-id="cbe24-106">In addition to interface constraints, a `where` clause can include a base class constraint, which states that a type must have the specified class as a base class (or be that class itself) in order to be used as a type argument for that generic type.</span></span> <span data-ttu-id="cbe24-107">如果使用這類條件約束，則它必須出現在該類型參數的任何其他條件約束之前。</span><span class="sxs-lookup"><span data-stu-id="cbe24-107">If such a constraint is used, it must appear before any other constraints on that type parameter.</span></span>  
  
 <span data-ttu-id="cbe24-108">[!code-cs[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="cbe24-108">[!code-cs[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]</span></span>  
  
 <span data-ttu-id="cbe24-109">`where` 子句也可能包含建構函式條件約束。</span><span class="sxs-lookup"><span data-stu-id="cbe24-109">The `where` clause may also include a constructor constraint.</span></span> <span data-ttu-id="cbe24-110">您可以建立使用新運算子的類型參數執行個體，但若要這樣做，類型參數必須受限於建構函式條件約束 `new()`。</span><span class="sxs-lookup"><span data-stu-id="cbe24-110">It is possible to create an instance of a type parameter using the new operator; however, in order to do so the type parameter must be constrained by the constructor constraint, `new()`.</span></span> <span data-ttu-id="cbe24-111">[new() 條件約束](../../../csharp/language-reference/keywords/new-constraint.md)可讓編譯器知道提供的任何類型引數都必須有可存取的無參數或預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="cbe24-111">The [new() Constraint](../../../csharp/language-reference/keywords/new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="cbe24-112">例如: </span><span class="sxs-lookup"><span data-stu-id="cbe24-112">For example:</span></span>  
  
 <span data-ttu-id="cbe24-113">[!code-cs[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="cbe24-113">[!code-cs[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]</span></span>  
  
 <span data-ttu-id="cbe24-114">`new()` 條件約束會出現在 `where` 子句中的最後。</span><span class="sxs-lookup"><span data-stu-id="cbe24-114">The `new()` constraint appears last in the `where` clause.</span></span>  
  
 <span data-ttu-id="cbe24-115">若有多個類型參數，請對每個類型參數使用一個 `where` 子句，例如：</span><span class="sxs-lookup"><span data-stu-id="cbe24-115">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>  
  
 <span data-ttu-id="cbe24-116">[!code-cs[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="cbe24-116">[!code-cs[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]</span></span>  
  
 <span data-ttu-id="cbe24-117">您也可以將條件約束附加至泛型方法的類型參數，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="cbe24-117">You can also attach constraints to type parameters of generic methods, like this:</span></span>  
  
```csharp  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 <span data-ttu-id="cbe24-118">請注意，描述委派類型參數條件約束的語法與方法的語法相同︰</span><span class="sxs-lookup"><span data-stu-id="cbe24-118">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>  
  
```csharp  
delegate T MyDelegate<T>() where T : new()  
```  
  
 <span data-ttu-id="cbe24-119">如需泛型委派的資訊，請參閱[泛型委派](../../../csharp/programming-guide/generics/generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="cbe24-119">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>  
  
 <span data-ttu-id="cbe24-120">如需條件約束語法和用法的詳細資料，請參閱[類型參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="cbe24-120">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="cbe24-121">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="cbe24-121">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cbe24-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbe24-122">See Also</span></span>  
 <span data-ttu-id="cbe24-123">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="cbe24-123">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
<span data-ttu-id="cbe24-124"> [C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="cbe24-124"> [C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
<span data-ttu-id="cbe24-125"> [泛型簡介](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span><span class="sxs-lookup"><span data-stu-id="cbe24-125"> [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md) </span></span>  
<span data-ttu-id="cbe24-126"> [new 條件約束](../../../csharp/language-reference/keywords/new-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="cbe24-126"> [new Constraint](../../../csharp/language-reference/keywords/new-constraint.md) </span></span>  
<span data-ttu-id="cbe24-127"> [型別參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)</span><span class="sxs-lookup"><span data-stu-id="cbe24-127"> [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)</span></span>
