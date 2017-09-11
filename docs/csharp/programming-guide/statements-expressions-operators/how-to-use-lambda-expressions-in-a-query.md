---
title: "如何：在查詢中使用 Lambda 運算式 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- lambda expressions [C#], in LINQ
ms.assetid: 3cac4d25-d11f-4abd-9e7c-0f02e97ae06d
caps.latest.revision: 16
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5ad819a0e4d441f6ea092480544195b89e0796ca
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-use-lambda-expressions-in-a-query-c-programming-guide"></a><span data-ttu-id="69e40-102">如何：在查詢中使用 Lambda 運算式 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="69e40-102">How to: Use Lambda Expressions in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="69e40-103">您不會在查詢語法中直接使用 Lambda 運算式，而是在方法呼叫中使用它們，因此查詢運算式可以包含方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="69e40-103">You do not use lambda expressions directly in query syntax, but you do use them in method calls, and query expressions can contain method calls.</span></span> <span data-ttu-id="69e40-104">事實上，某些查詢作業只能以方法語法來表示。</span><span class="sxs-lookup"><span data-stu-id="69e40-104">In fact, some query operations can only be expressed in method syntax.</span></span> <span data-ttu-id="69e40-105">如需查詢語法與方法語法之間差異的詳細資訊，請參閱 [LINQ 中的查詢語法及方法語法](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)。</span><span class="sxs-lookup"><span data-stu-id="69e40-105">For more information about the difference between query syntax and method syntax, see [Query Syntax and Method Syntax in LINQ](../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69e40-106">範例</span><span class="sxs-lookup"><span data-stu-id="69e40-106">Example</span></span>  
 <span data-ttu-id="69e40-107">下列範例示範如何透過 <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> 標準查詢運算子，在以方法為基礎的查詢中使用 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="69e40-107">The following example demonstrates how to use a lambda expression in a method-based query by using the <xref:System.Linq.Enumerable.Where%2A?displayProperty=fullName> standard query operator.</span></span> <span data-ttu-id="69e40-108">請注意，此範例中的 <xref:System.Linq.Enumerable.Where%2A> 方法具有委派類型 <xref:System.Func%601> 的輸入參數，而且該委派會接受整數作為輸入並傳回布林值。</span><span class="sxs-lookup"><span data-stu-id="69e40-108">Note that the <xref:System.Linq.Enumerable.Where%2A> method in this example has an input parameter of the delegate type <xref:System.Func%601> and that delegate takes an integer as input and returns a Boolean.</span></span> <span data-ttu-id="69e40-109">Lambda 運算式可轉換成該委派。</span><span class="sxs-lookup"><span data-stu-id="69e40-109">The lambda expression can be converted to that delegate.</span></span> <span data-ttu-id="69e40-110">如果這是使用 <xref:System.Linq.Queryable.Where%2A?displayProperty=fullName> 方法的 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 查詢，參數類型就會是 `Expression<Func\<int,bool>>`，但 Lambda 運算式看起來會完全相同。</span><span class="sxs-lookup"><span data-stu-id="69e40-110">If this were a [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] query that used the <xref:System.Linq.Queryable.Where%2A?displayProperty=fullName> method, the parameter type would be an `Expression<Func\<int,bool>>` but the lambda expression would look exactly the same.</span></span> <span data-ttu-id="69e40-111">如需運算式類型的詳細資訊，請參閱 <xref:System.Linq.Expressions.Expression?displayProperty=fullName>。</span><span class="sxs-lookup"><span data-stu-id="69e40-111">For more information on the Expression type, see <xref:System.Linq.Expressions.Expression?displayProperty=fullName>.</span></span>  
  
 <span data-ttu-id="69e40-112">[!code-cs[csProgGuideLINQ#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="69e40-112">[!code-cs[csProgGuideLINQ#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="69e40-113">範例</span><span class="sxs-lookup"><span data-stu-id="69e40-113">Example</span></span>  
 <span data-ttu-id="69e40-114">下列範例示範如何在查詢運算式的方法呼叫中使用 Lambda 運算式。</span><span class="sxs-lookup"><span data-stu-id="69e40-114">The following example demonstrates how to use a lambda expression in a method call of a query expression.</span></span> <span data-ttu-id="69e40-115">因為無法使用查詢語法來叫用 <xref:System.Linq.Enumerable.Sum%2A> 標準查詢運算子，所以需要此 Lambda。</span><span class="sxs-lookup"><span data-stu-id="69e40-115">The lambda is necessary because the <xref:System.Linq.Enumerable.Sum%2A> standard query operator cannot be invoked by using query syntax.</span></span>  
  
 <span data-ttu-id="69e40-116">此查詢會先根據學生的年級 (已定義於 `GradeLevel` 列舉) 來進行分組。</span><span class="sxs-lookup"><span data-stu-id="69e40-116">The query first groups the students according to their grade level, as defined in the `GradeLevel` enum.</span></span> <span data-ttu-id="69e40-117">接著會針對每一組加總計算每個學生的總分數。</span><span class="sxs-lookup"><span data-stu-id="69e40-117">Then for each group it adds the total scores for each student.</span></span> <span data-ttu-id="69e40-118">這需要兩個 `Sum` 運算。</span><span class="sxs-lookup"><span data-stu-id="69e40-118">This requires two `Sum` operations.</span></span> <span data-ttu-id="69e40-119">內部的 `Sum` 會計算每個學生的總分數，而外部的 `Sum` 會不斷執行，以加總該群組中所有學生的總分數。</span><span class="sxs-lookup"><span data-stu-id="69e40-119">The inner `Sum` calculates the total score for each student, and the outer `Sum` keeps a running, combined total for all students in the group.</span></span>  
  
 <span data-ttu-id="69e40-120">[!code-cs[csProgGuideLINQ#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="69e40-120">[!code-cs[csProgGuideLINQ#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-lambda-expressions-in-a-query_2.cs)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="69e40-121">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="69e40-121">Compiling the Code</span></span>  
 <span data-ttu-id="69e40-122">若要執行此程式碼，請將該方法複製並貼到[如何︰查詢物件集合](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md)中所提供的 `StudentClass`，然後從 `Main` 方法進行呼叫。</span><span class="sxs-lookup"><span data-stu-id="69e40-122">To run this code, copy and paste the method into the `StudentClass` that is provided in [How to: Query a Collection of Objects](../../../csharp/programming-guide/linq-query-expressions/how-to-query-a-collection-of-objects.md) and call it from the `Main` method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69e40-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69e40-123">See Also</span></span>  
 <span data-ttu-id="69e40-124">[Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="69e40-124">[Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) </span></span>  
 [<span data-ttu-id="69e40-125">運算式樹狀結構</span><span class="sxs-lookup"><span data-stu-id="69e40-125">Expression Trees</span></span>](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b)

