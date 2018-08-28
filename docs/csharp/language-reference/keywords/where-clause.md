---
title: where 子句 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- whereclause_CSharpKeyword
helpviewer_keywords:
- where keyword [C#]
- where clause [C#]
ms.assetid: 7f9bf952-7744-4f91-b676-cddb55d107c3
ms.openlocfilehash: 8607c79a8b1e9a9fd999e4f5b77ecfac786161b3
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2018
ms.locfileid: "43003147"
---
# <a name="where-clause-c-reference"></a><span data-ttu-id="02423-102">where 子句 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="02423-102">where clause (C# Reference)</span></span>
<span data-ttu-id="02423-103">`where` 子句用於查詢運算式中，以指定將在查詢運算式中傳回資料來源中的項目。</span><span class="sxs-lookup"><span data-stu-id="02423-103">The `where` clause is used in a query expression to specify which elements from the data source will be returned in the query expression.</span></span> <span data-ttu-id="02423-104">它會將布林值條件 (*predicate*) 套用到每個來源項目 (透過範圍變數所參考)，並傳回所指定條件為 true 的項目。</span><span class="sxs-lookup"><span data-stu-id="02423-104">It applies a Boolean condition (*predicate*) to each source element (referenced by the range variable) and returns those for which the specified condition is true.</span></span> <span data-ttu-id="02423-105">單一查詢運算式可能會包含多個 `where` 子句，而單一子句可能會包含多個述詞子運算式。</span><span class="sxs-lookup"><span data-stu-id="02423-105">A single query expression may contain multiple `where` clauses and a single clause may contain multiple predicate subexpressions.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02423-106">範例</span><span class="sxs-lookup"><span data-stu-id="02423-106">Example</span></span>  
 <span data-ttu-id="02423-107">在下列範例中，`where` 子句會篩選掉不小於五的所有數字。</span><span class="sxs-lookup"><span data-stu-id="02423-107">In the following example, the `where` clause filters out all numbers except those that are less than five.</span></span> <span data-ttu-id="02423-108">如果您移除 `where` 子句，則會傳回資料來源中的所有數字。</span><span class="sxs-lookup"><span data-stu-id="02423-108">If you remove the `where` clause, all numbers from the data source would be returned.</span></span> <span data-ttu-id="02423-109">`num < 5` 運算式是套用至每個項目的述詞。</span><span class="sxs-lookup"><span data-stu-id="02423-109">The expression `num < 5` is the predicate that is applied to each element.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="02423-110">範例</span><span class="sxs-lookup"><span data-stu-id="02423-110">Example</span></span>  
 <span data-ttu-id="02423-111">在單一 `where` 子句內，您可以使用 [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) 和 [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) 運算子來指定所需數目的述詞。</span><span class="sxs-lookup"><span data-stu-id="02423-111">Within a single `where` clause, you can specify as many predicates as necessary by using the [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) operators.</span></span> <span data-ttu-id="02423-112">在下列範例中，查詢會指定兩個述詞，只選取小於五的偶數。</span><span class="sxs-lookup"><span data-stu-id="02423-112">In the following example, the query specifies two predicates in order to select only the even numbers that are less than five.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="02423-113">範例</span><span class="sxs-lookup"><span data-stu-id="02423-113">Example</span></span>  
 <span data-ttu-id="02423-114">`where` 子句可能包含一個或多個傳回布林值的方法。</span><span class="sxs-lookup"><span data-stu-id="02423-114">A `where` clause may contain one or more methods that return Boolean values.</span></span> <span data-ttu-id="02423-115">在下列範例中，`where` 子句使用方法來判斷範圍變數的目前值是偶數還是奇數。</span><span class="sxs-lookup"><span data-stu-id="02423-115">In the following example, the `where` clause uses a method to determine whether the current value of the range variable is even or odd.</span></span>  
  
 [!code-csharp[cscsrefQueryKeywords#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/where-clause_3.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="02423-116">備註</span><span class="sxs-lookup"><span data-stu-id="02423-116">Remarks</span></span>  
 <span data-ttu-id="02423-117">`where` 子句是篩選機制。</span><span class="sxs-lookup"><span data-stu-id="02423-117">The `where` clause is a filtering mechanism.</span></span> <span data-ttu-id="02423-118">它幾乎可以放在查詢運算式中的任何位置，但不能是第一個或最後一個子句。</span><span class="sxs-lookup"><span data-stu-id="02423-118">It can be positioned almost anywhere in a query expression, except it cannot be the first or last clause.</span></span> <span data-ttu-id="02423-119">`where` 子句可能出現在 [group](../../../csharp/language-reference/keywords/group-clause.md) 子句之前或之後，取決於必須在分組來源項目之前還是之後進行篩選。</span><span class="sxs-lookup"><span data-stu-id="02423-119">A `where` clause may appear either before or after a [group](../../../csharp/language-reference/keywords/group-clause.md) clause depending on whether you have to filter the source elements before or after they are grouped.</span></span>  
  
 <span data-ttu-id="02423-120">如果指定的述詞不適用於資料來源中的項目，則會產生編譯時期錯誤。</span><span class="sxs-lookup"><span data-stu-id="02423-120">If a specified predicate is not valid for the elements in the data source, a compile-time error will result.</span></span> <span data-ttu-id="02423-121">這是 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 所提供的強類型檢查的其中一個優點。</span><span class="sxs-lookup"><span data-stu-id="02423-121">This is one benefit of the strong type-checking provided by [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)].</span></span>  
  
 <span data-ttu-id="02423-122">在編譯時間，`where` 關鍵字會轉換為 <xref:System.Linq.Enumerable.Where%2A> 標準查詢運算子方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="02423-122">At compile time the `where` keyword is converted into a call to the <xref:System.Linq.Enumerable.Where%2A> Standard Query Operator method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02423-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="02423-123">See Also</span></span>

- [<span data-ttu-id="02423-124">查詢關鍵字 (LINQ)</span><span class="sxs-lookup"><span data-stu-id="02423-124">Query Keywords (LINQ)</span></span>](../../../csharp/language-reference/keywords/query-keywords.md)  
- [<span data-ttu-id="02423-125">from 子句</span><span class="sxs-lookup"><span data-stu-id="02423-125">from clause</span></span>](../../../csharp/language-reference/keywords/from-clause.md)  
- [<span data-ttu-id="02423-126">select 子句</span><span class="sxs-lookup"><span data-stu-id="02423-126">select clause</span></span>](../../../csharp/language-reference/keywords/select-clause.md)  
- [<span data-ttu-id="02423-127">篩選資料</span><span class="sxs-lookup"><span data-stu-id="02423-127">Filtering Data</span></span>](../../programming-guide/concepts/linq/filtering-data.md)  
- [<span data-ttu-id="02423-128">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="02423-128">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)  
- [<span data-ttu-id="02423-129">開始使用 C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="02423-129">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
