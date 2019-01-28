---
title: HOW TO：在查詢運算式中使用隱含類型區域變數和陣列 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: 6217b741a4dfabb67fc182a58543187ac37987ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695669"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a><span data-ttu-id="6f165-102">HOW TO：在查詢運算式中使用隱含類型區域變數和陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="6f165-102">How to: Use Implicitly Typed Local Variables and Arrays in a Query Expression (C# Programming Guide)</span></span>
<span data-ttu-id="6f165-103">每次您希望編譯器判斷區域變數的類型時，可以使用隱含型別區域變數。</span><span class="sxs-lookup"><span data-stu-id="6f165-103">You can use implicitly typed local variables whenever you want the compiler to determine the type of a local variable.</span></span> <span data-ttu-id="6f165-104">您必須使用隱含型別區域變數來儲存查詢運算式中常用的匿名型別。</span><span class="sxs-lookup"><span data-stu-id="6f165-104">You must use implicitly typed local variables to store anonymous types, which are often used in query expressions.</span></span> <span data-ttu-id="6f165-105">下列範例說明在查詢中選擇性使用和必須使用隱含型別區域變數的情況。</span><span class="sxs-lookup"><span data-stu-id="6f165-105">The following examples illustrate both optional and required uses of implicitly typed local variables in queries.</span></span>  
  
 <span data-ttu-id="6f165-106">隱含型別區域變數是透過 [var](../../../csharp/language-reference/keywords/var.md) 內容關鍵字宣告。</span><span class="sxs-lookup"><span data-stu-id="6f165-106">Implicitly typed local variables are declared by using the [var](../../../csharp/language-reference/keywords/var.md) contextual keyword.</span></span> <span data-ttu-id="6f165-107">如需詳細資訊，請參閱[隱含型別區域變數](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)和[隱含型別陣列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="6f165-107">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f165-108">範例</span><span class="sxs-lookup"><span data-stu-id="6f165-108">Example</span></span>  
 <span data-ttu-id="6f165-109">下列範例顯示需要 `var` 關鍵字的常見案例：產生一系列匿名型別的查詢運算式。</span><span class="sxs-lookup"><span data-stu-id="6f165-109">The following example shows a common scenario in which the `var` keyword is required: a query expression that produces a sequence of anonymous types.</span></span> <span data-ttu-id="6f165-110">在此案例中，`foreach` 陳述式中的查詢變數和反覆運算變數都必須使用 `var` 來隱含輸入，因為您無法存取匿名型別的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="6f165-110">In this scenario, both the query variable and the iteration variable in the `foreach` statement must be implicitly typed by using `var` because you do not have access to a type name for the anonymous type.</span></span> <span data-ttu-id="6f165-111">如需匿名型別的詳細資訊，請參閱[匿名型別](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。</span><span class="sxs-lookup"><span data-stu-id="6f165-111">For more information about anonymous types, see [Anonymous Types](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
 [!code-csharp[csProgGuideLINQ#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="6f165-112">範例</span><span class="sxs-lookup"><span data-stu-id="6f165-112">Example</span></span>  
 <span data-ttu-id="6f165-113">下列範例會在類似情況下使用 `var` 關鍵字，但可選擇是否使用 `var`。</span><span class="sxs-lookup"><span data-stu-id="6f165-113">The following example uses the `var` keyword in a situation that is similar, but in which the use of `var` is optional.</span></span> <span data-ttu-id="6f165-114">因為 `student.LastName` 是字串，所以執行查詢會傳回一系列的字串。</span><span class="sxs-lookup"><span data-stu-id="6f165-114">Because `student.LastName` is a string, execution of the query returns a sequence of strings.</span></span> <span data-ttu-id="6f165-115">因此，`queryID` 的類型會宣告為 `System.Collections.Generic.IEnumerable<string>`，而不是 `var`。</span><span class="sxs-lookup"><span data-stu-id="6f165-115">Therefore, the type of `queryID` could be declared as `System.Collections.Generic.IEnumerable<string>` instead of `var`.</span></span> <span data-ttu-id="6f165-116">關鍵字 `var` 是為了方便起見。</span><span class="sxs-lookup"><span data-stu-id="6f165-116">Keyword `var` is used for convenience.</span></span> <span data-ttu-id="6f165-117">在範例中，`foreach` 陳述式中的反覆運算變數明確輸入為字串，但它可以改為使用 `var` 來宣告。</span><span class="sxs-lookup"><span data-stu-id="6f165-117">In the example, the iteration variable in the `foreach` statement is explicitly typed as a string, but it could instead be declared by using `var`.</span></span> <span data-ttu-id="6f165-118">因為反覆運算變數的類型不是匿名型別，所以使用 `var` 是選項而非需求。</span><span class="sxs-lookup"><span data-stu-id="6f165-118">Because the type of the iteration variable is not an anonymous type, the use of `var` is an option, not a requirement.</span></span> <span data-ttu-id="6f165-119">請記住，`var` 本身不是類型，而是編譯器用來推斷和指派類型的指令。</span><span class="sxs-lookup"><span data-stu-id="6f165-119">Remember, `var` itself is not a type, but an instruction to the compiler to infer and assign the type.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6f165-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f165-120">See also</span></span>

- [<span data-ttu-id="6f165-121">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6f165-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="6f165-122">擴充方法</span><span class="sxs-lookup"><span data-stu-id="6f165-122">Extension Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [<span data-ttu-id="6f165-123">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="6f165-123">LINQ (Language-Integrated Query)</span></span>](../../../csharp/linq/index.md)
- [<span data-ttu-id="6f165-124">var</span><span class="sxs-lookup"><span data-stu-id="6f165-124">var</span></span>](../../../csharp/language-reference/keywords/var.md)
- [<span data-ttu-id="6f165-125">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="6f165-125">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
