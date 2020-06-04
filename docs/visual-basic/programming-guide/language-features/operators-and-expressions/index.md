---
title: 運算子和運算式
ms.date: 07/20/2015
helpviewer_keywords:
- operators [Visual Basic], operands
- operators [Visual Basic]
- operands [Visual Basic], definition
- Visual Basic code, operators
- Visual Basic code, expressions
- operands
- expressions [Visual Basic]
ms.assetid: b86f3131-94ee-448f-96cd-79611e028b26
ms.openlocfilehash: dcf52c6200193f81070f323c8037ad82d747942d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403430"
---
# <a name="operators-and-expressions-in-visual-basic"></a><span data-ttu-id="219f0-102">Visual Basic 中的運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="219f0-102">Operators and Expressions in Visual Basic</span></span>
<span data-ttu-id="219f0-103">「運算子」\*\* 是一種程式碼項目，可對保留值的一或多個程式碼項目執行運算。</span><span class="sxs-lookup"><span data-stu-id="219f0-103">An *operator* is a code element that performs an operation on one or more code elements that hold values.</span></span> <span data-ttu-id="219f0-104">值項目包含 `Function` 與 `Operator` 程序和運算式的變數、常數、常值、屬性、傳回值。</span><span class="sxs-lookup"><span data-stu-id="219f0-104">Value elements include variables, constants, literals, properties, returns from `Function` and `Operator` procedures, and expressions.</span></span>  
  
 <span data-ttu-id="219f0-105">「運算式」\*\* 是一系列與運算子合併的值項目，可產生新的值。</span><span class="sxs-lookup"><span data-stu-id="219f0-105">An *expression* is a series of value elements combined with operators, which yields a new value.</span></span> <span data-ttu-id="219f0-106">運算子透過執行計算、比較或其他作業來當成值項目。</span><span class="sxs-lookup"><span data-stu-id="219f0-106">The operators act on the value elements by performing calculations, comparisons, or other operations.</span></span>  
  
## <a name="types-of-operators"></a><span data-ttu-id="219f0-107">運算子類型</span><span class="sxs-lookup"><span data-stu-id="219f0-107">Types of Operators</span></span>  
 <span data-ttu-id="219f0-108">Visual Basic 提供下列類型的運算子：</span><span class="sxs-lookup"><span data-stu-id="219f0-108">Visual Basic provides the following types of operators:</span></span>  
  
- <span data-ttu-id="219f0-109">[算術運算子](arithmetic-operators.md)可對數值執行類似的計算，包括移位其位元模式。</span><span class="sxs-lookup"><span data-stu-id="219f0-109">[Arithmetic Operators](arithmetic-operators.md) perform familiar calculations on numeric values, including shifting their bit patterns.</span></span>  
  
- <span data-ttu-id="219f0-110">[比較運算子](comparison-operators.md)可比較兩個運算式，並傳回代表比較結果的 `Boolean` 值。</span><span class="sxs-lookup"><span data-stu-id="219f0-110">[Comparison Operators](comparison-operators.md) compare two expressions and return a `Boolean` value representing the result of the comparison.</span></span>  
  
- <span data-ttu-id="219f0-111">[串連運算子](concatenation-operators.md)會將多個字串聯結成單一字串。</span><span class="sxs-lookup"><span data-stu-id="219f0-111">[Concatenation Operators](concatenation-operators.md) join multiple strings into a single string.</span></span>  
  
- <span data-ttu-id="219f0-112">[Visual Basic 中的邏輯運算子和位元運算子](logical-and-bitwise-operators.md)可合併 `Boolean` 或數值，並傳回與值相同之資料類型的結果。</span><span class="sxs-lookup"><span data-stu-id="219f0-112">[Logical and Bitwise Operators in Visual Basic](logical-and-bitwise-operators.md) combine `Boolean` or numeric values and return a result of the same data type as the values.</span></span>  
  
 <span data-ttu-id="219f0-113">與運算子合併使用的值項目稱為該運算子的「運算元」\*\*。</span><span class="sxs-lookup"><span data-stu-id="219f0-113">The value elements that are combined with an operator are called *operands* of that operator.</span></span> <span data-ttu-id="219f0-114">與值項目合併使用的運算子可形成運算式，但不含可形成「陳述式」\*\* 的指派運算子。</span><span class="sxs-lookup"><span data-stu-id="219f0-114">Operators combined with value elements form expressions, except for the assignment operator, which forms a *statement*.</span></span> <span data-ttu-id="219f0-115">如需詳細資訊，請參閱[陳述式](../statements.md)。</span><span class="sxs-lookup"><span data-stu-id="219f0-115">For more information, see [Statements](../statements.md).</span></span>  
  
## <a name="evaluation-of-expressions"></a><span data-ttu-id="219f0-116">運算式評估</span><span class="sxs-lookup"><span data-stu-id="219f0-116">Evaluation of Expressions</span></span>  
 <span data-ttu-id="219f0-117">運算式的最終結果代表值，通常是熟悉的資料類型，例如 `Boolean`、`String` 或數值類型。</span><span class="sxs-lookup"><span data-stu-id="219f0-117">The end result of an expression represents a value, which is typically of a familiar data type such as `Boolean`, `String`, or a numeric type.</span></span>  
  
 <span data-ttu-id="219f0-118">下列是運算式範例。</span><span class="sxs-lookup"><span data-stu-id="219f0-118">The following are examples of expressions.</span></span>  
  
 `5 + 4`  
  
 `' The preceding expression evaluates to 9.`  
  
 `15 * System.Math.Sqrt(9) + x`  
  
 `' The preceding expression evaluates to 45 plus the value of x.`  
  
 `"Concat" & "ena" & "tion"`  
  
 `' The preceding expression evaluates to "Concatenation".`  
  
 `763 < 23`  
  
 `' The preceding expression evaluates to False.`  
  
 <span data-ttu-id="219f0-119">數個運算子可以在單一運算式或陳述式中執行動作，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="219f0-119">Several operators can perform actions in a single expression or statement, as the following example illustrates.</span></span>  
  
 [!code-vb[VbVbalrOperators#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#56)]  
  
 <span data-ttu-id="219f0-120">在上述範例中，Visual Basic 會在指派運算子（）的右邊執行運算式中的作業 `=` ，然後將產生的值指派給左邊的變數 `x` 。</span><span class="sxs-lookup"><span data-stu-id="219f0-120">In the preceding example, Visual Basic performs the operations in the expression on the right side of the assignment operator (`=`), then assigns the resulting value to the variable `x` on the left.</span></span> <span data-ttu-id="219f0-121">可合併到運算式的運算子數目沒有實際限制，但需要了解 [Visual Basic 中的運算子優先順序](../../../language-reference/operators/operator-precedence.md)，才能確保您取得所要的結果。</span><span class="sxs-lookup"><span data-stu-id="219f0-121">There is no practical limit to the number of operators that can be combined into an expression, but an understanding of [Operator Precedence in Visual Basic](../../../language-reference/operators/operator-precedence.md) is necessary to ensure that you get the results you expect.</span></span>  

## <a name="see-also"></a><span data-ttu-id="219f0-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="219f0-122">See also</span></span>

- [<span data-ttu-id="219f0-123">運算子</span><span class="sxs-lookup"><span data-stu-id="219f0-123">Operators</span></span>](../../../language-reference/operators/index.md)
- [<span data-ttu-id="219f0-124">有效的運算子組合</span><span class="sxs-lookup"><span data-stu-id="219f0-124">Efficient Combination of Operators</span></span>](efficient-combination-of-operators.md)
- [<span data-ttu-id="219f0-125">陳述式</span><span class="sxs-lookup"><span data-stu-id="219f0-125">Statements</span></span>](../../../language-reference/statements/index.md)
