---
title: where (泛型類型條件約束) (C# 參考)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- whereconstraint
- whereconstraint_CSharpKeyword
helpviewer_keywords:
- where (generic type constraint) [C#]
ms.assetid: d7aa871b-0714-416a-bab2-96f87ada4310
caps.latest.revision: 10
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f2b7b159689aa771d3f9d59e3b1dd340c85b1d79
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="where-generic-type-constraint-c-reference"></a><span data-ttu-id="996fd-102">where (泛型類型條件約束) (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="996fd-102">where (generic type constraint) (C# Reference)</span></span>
<span data-ttu-id="996fd-103">在泛型類型定義中，`where` 子句是用來指定類型的條件約束，而這些類型可以用作泛型宣告中所定義類型參數的引數。</span><span class="sxs-lookup"><span data-stu-id="996fd-103">In a generic type definition, the `where` clause is used to specify constraints on the types that can be used as arguments for a type parameter defined in a generic declaration.</span></span> <span data-ttu-id="996fd-104">例如，您可以宣告泛型類別 `MyGenericClass`，讓型別參數 `T` 實作 <xref:System.IComparable%601> 介面：</span><span class="sxs-lookup"><span data-stu-id="996fd-104">For example, you can declare a generic class, `MyGenericClass`, such that the type parameter `T` implements the <xref:System.IComparable%601> interface:</span></span>  
  
```csharp  
public class MyGenericClass<T> where T:IComparable { }  
```  
  
> [!NOTE]
>  <span data-ttu-id="996fd-105">如需查詢運算式中 where 子句的詳細資訊，請參閱 [where 子句](../../../csharp/language-reference/keywords/where-clause.md)。</span><span class="sxs-lookup"><span data-stu-id="996fd-105">For more information on the where clause in a query expression, see [where clause](../../../csharp/language-reference/keywords/where-clause.md).</span></span>  
  
 <span data-ttu-id="996fd-106">除了介面條件約束之外，`where` 子句可以包含基底類別條件約束，說明類型必須將指定的類別作為基底類別 (或該類別本身)，才能用作該泛型類型的類型引數。</span><span class="sxs-lookup"><span data-stu-id="996fd-106">In addition to interface constraints, a `where` clause can include a base class constraint, which states that a type must have the specified class as a base class (or be that class itself) in order to be used as a type argument for that generic type.</span></span> <span data-ttu-id="996fd-107">如果使用這類條件約束，則它必須出現在該類型參數的任何其他條件約束之前。</span><span class="sxs-lookup"><span data-stu-id="996fd-107">If such a constraint is used, it must appear before any other constraints on that type parameter.</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_1.cs)]  
  
 <span data-ttu-id="996fd-108">`where` 子句也可能包含建構函式條件約束。</span><span class="sxs-lookup"><span data-stu-id="996fd-108">The `where` clause may also include a constructor constraint.</span></span> <span data-ttu-id="996fd-109">您可以建立使用新運算子的類型參數執行個體，但若要這樣做，類型參數必須受限於建構函式條件約束 `new()`。</span><span class="sxs-lookup"><span data-stu-id="996fd-109">It is possible to create an instance of a type parameter using the new operator; however, in order to do so the type parameter must be constrained by the constructor constraint, `new()`.</span></span> <span data-ttu-id="996fd-110">[new() 條件約束](../../../csharp/language-reference/keywords/new-constraint.md)可讓編譯器知道提供的任何類型引數都必須有可存取的無參數或預設建構函式。</span><span class="sxs-lookup"><span data-stu-id="996fd-110">The [new() Constraint](../../../csharp/language-reference/keywords/new-constraint.md) lets the compiler know that any type argument supplied must have an accessible parameterless--or default-- constructor.</span></span> <span data-ttu-id="996fd-111">例如: </span><span class="sxs-lookup"><span data-stu-id="996fd-111">For example:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_2.cs)]  
  
 <span data-ttu-id="996fd-112">`new()` 條件約束會出現在 `where` 子句中的最後。</span><span class="sxs-lookup"><span data-stu-id="996fd-112">The `new()` constraint appears last in the `where` clause.</span></span>  
  
 <span data-ttu-id="996fd-113">若有多個類型參數，請對每個類型參數使用一個 `where` 子句，例如：</span><span class="sxs-lookup"><span data-stu-id="996fd-113">With multiple type parameters, use one `where` clause for each type parameter, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-generic-type-constraint_3.cs)]  
  
 <span data-ttu-id="996fd-114">您也可以將條件約束附加至泛型方法的類型參數，如下所示︰</span><span class="sxs-lookup"><span data-stu-id="996fd-114">You can also attach constraints to type parameters of generic methods, like this:</span></span>  
  
```csharp  
public bool MyMethod<T>(T t) where T : IMyInterface { }  
```  
  
 <span data-ttu-id="996fd-115">請注意，描述委派類型參數條件約束的語法與方法的語法相同︰</span><span class="sxs-lookup"><span data-stu-id="996fd-115">Notice that the syntax to describe type parameter constraints on delegates is the same as that of methods:</span></span>  
  
```csharp  
delegate T MyDelegate<T>() where T : new()  
```  
  
 <span data-ttu-id="996fd-116">如需泛型委派的資訊，請參閱[泛型委派](../../../csharp/programming-guide/generics/generic-delegates.md)。</span><span class="sxs-lookup"><span data-stu-id="996fd-116">For information on generic delegates, see [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>  
  
 <span data-ttu-id="996fd-117">如需條件約束語法和用法的詳細資料，請參閱[類型參數的條件約束](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="996fd-117">For details on the syntax and use of constraints, see [Constraints on Type Parameters](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="996fd-118">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="996fd-118">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="996fd-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="996fd-119">See Also</span></span>  
 [<span data-ttu-id="996fd-120">C# 參考</span><span class="sxs-lookup"><span data-stu-id="996fd-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="996fd-121">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="996fd-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="996fd-122">泛型簡介</span><span class="sxs-lookup"><span data-stu-id="996fd-122">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="996fd-123">new 條件約束</span><span class="sxs-lookup"><span data-stu-id="996fd-123">new Constraint</span></span>](../../../csharp/language-reference/keywords/new-constraint.md)  
 [<span data-ttu-id="996fd-124">型別參數的條件約束</span><span class="sxs-lookup"><span data-stu-id="996fd-124">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)
