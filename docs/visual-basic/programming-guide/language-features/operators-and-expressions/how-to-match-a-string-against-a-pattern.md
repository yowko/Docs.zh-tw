---
title: HOW TO：比對的字串和模式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: ca6537d81f080120fcbea0cf083f450dce4e9f62
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58826011"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a><span data-ttu-id="344bd-102">HOW TO：比對的字串和模式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="344bd-102">How to: Match a String against a Pattern (Visual Basic)</span></span>
<span data-ttu-id="344bd-103">如果您想要找出是否有運算式[字串資料類型](../../../../visual-basic/language-reference/data-types/string-data-type.md)滿足模式，則您可以使用[Like 運算子](../../../../visual-basic/language-reference/operators/like-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="344bd-103">If you want to find out if an expression of the [String Data Type](../../../../visual-basic/language-reference/data-types/string-data-type.md) satisfies a pattern, then you can use the [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
 <span data-ttu-id="344bd-104">`Like` 會使用兩個運算元。</span><span class="sxs-lookup"><span data-stu-id="344bd-104">`Like` takes two operands.</span></span> <span data-ttu-id="344bd-105">左的運算元是一個字串運算式，和右運算元是字串，包含要用來比對的模式。</span><span class="sxs-lookup"><span data-stu-id="344bd-105">The left operand is a string expression, and the right operand is a string containing the pattern to be used for matching.</span></span> <span data-ttu-id="344bd-106">`Like` 傳回`Boolean`值，指出字串運算式是否符合模式。</span><span class="sxs-lookup"><span data-stu-id="344bd-106">`Like` returns a `Boolean` value indicating whether the string expression satisfies the pattern.</span></span>  
  
 <span data-ttu-id="344bd-107">您可以比對的字串運算式，針對特定的字元、 萬用字元、 字元清單中或字元範圍中每個字元。</span><span class="sxs-lookup"><span data-stu-id="344bd-107">You can match each character in the string expression against a specific character, a wildcard character, a character list, or a character range.</span></span> <span data-ttu-id="344bd-108">要比對字串運算式中的字元位置的對應，模式字串中的規格位置。</span><span class="sxs-lookup"><span data-stu-id="344bd-108">The positions of the specifications in the pattern string correspond to the positions of the characters to be matched in the string expression.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a><span data-ttu-id="344bd-109">若要符合的特定字元的字串運算式中的字元</span><span class="sxs-lookup"><span data-stu-id="344bd-109">To match a character in the string expression against a specific character</span></span>  
  
-   <span data-ttu-id="344bd-110">將特定的字元放在模式比對字串中直接。</span><span class="sxs-lookup"><span data-stu-id="344bd-110">Put the specific character directly in the pattern string.</span></span> <span data-ttu-id="344bd-111">某些特殊字元必須加上方括號 (`[ ]`)。</span><span class="sxs-lookup"><span data-stu-id="344bd-111">Certain special characters must be enclosed in brackets (`[ ]`).</span></span> <span data-ttu-id="344bd-112">如需詳細資訊，請參閱 < [Like 運算子](../../../../visual-basic/language-reference/operators/like-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="344bd-112">For more information, see [Like Operator](../../../../visual-basic/language-reference/operators/like-operator.md).</span></span>  
  
     <span data-ttu-id="344bd-113">下列範例會測試是否`myString`只包含單一字元`H`。</span><span class="sxs-lookup"><span data-stu-id="344bd-113">The following example tests whether `myString` consists exactly of the single character `H`.</span></span>  
  
     [!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a><span data-ttu-id="344bd-114">若要符合萬用字元的字串運算式中的字元</span><span class="sxs-lookup"><span data-stu-id="344bd-114">To match a character in the string expression against a wildcard character</span></span>  
  
-   <span data-ttu-id="344bd-115">將問號 (`?`)，模式字串中。</span><span class="sxs-lookup"><span data-stu-id="344bd-115">Put a question mark (`?`) in the pattern string.</span></span> <span data-ttu-id="344bd-116">在這個位置中的任何有效字元會比對成功。</span><span class="sxs-lookup"><span data-stu-id="344bd-116">Any valid character in this position makes a successful match.</span></span>  
  
     <span data-ttu-id="344bd-117">下列範例會測試是否`myString`組成的單一字元`W`後面兩個字元的任何值。</span><span class="sxs-lookup"><span data-stu-id="344bd-117">The following example tests whether `myString` consists of the single character `W` followed by exactly two characters of any values.</span></span>  
  
     [!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a><span data-ttu-id="344bd-118">若要符合的字元清單的字串運算式中的字元</span><span class="sxs-lookup"><span data-stu-id="344bd-118">To match a character in the string expression against a list of characters</span></span>  
  
-   <span data-ttu-id="344bd-119">將方括號 (`[ ]`) 在模式字串中，並將清單的字元放在方括號內。</span><span class="sxs-lookup"><span data-stu-id="344bd-119">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the list of characters.</span></span> <span data-ttu-id="344bd-120">不需以逗號或任何其他分隔符號分隔保留字元。</span><span class="sxs-lookup"><span data-stu-id="344bd-120">Do not separate the characters with commas or any other separator.</span></span> <span data-ttu-id="344bd-121">在清單中的任何單一字元會比對成功。</span><span class="sxs-lookup"><span data-stu-id="344bd-121">Any single character in the list makes a successful match.</span></span>  
  
     <span data-ttu-id="344bd-122">下列範例會測試是否`myString`後面接著一個字元的任何有效的字元所組成`A`， `C`，或`E`。</span><span class="sxs-lookup"><span data-stu-id="344bd-122">The following example tests whether `myString` consists of any valid character followed by exactly one of the characters `A`, `C`, or `E`.</span></span>  
  
     [!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]  
  
     <span data-ttu-id="344bd-123">請注意此項比對會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="344bd-123">Note that this match is case-sensitive.</span></span>  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a><span data-ttu-id="344bd-124">若要符合的字元範圍的字串運算式中的字元</span><span class="sxs-lookup"><span data-stu-id="344bd-124">To match a character in the string expression against a range of characters</span></span>  
  
-   <span data-ttu-id="344bd-125">將方括號 (`[ ]`) 以連字號分隔的模式字串中，括號的最低和最高的字元放在範圍內 (`–`)。</span><span class="sxs-lookup"><span data-stu-id="344bd-125">Put brackets (`[ ]`) in the pattern string, and inside the brackets put the lowest and highest characters in the range, separated by a hyphen (`–`).</span></span> <span data-ttu-id="344bd-126">在範圍內的任何單一字元會比對成功。</span><span class="sxs-lookup"><span data-stu-id="344bd-126">Any single character within the range makes a successful match.</span></span>  
  
     <span data-ttu-id="344bd-127">下列範例會測試是否`myString`字元所組成`num`只有其中一個字元後面接著`i`， `j`， `k`， `l`， `m`，或`n`。</span><span class="sxs-lookup"><span data-stu-id="344bd-127">The following example tests whether `myString` consists of the characters `num` followed by exactly one of the characters `i`, `j`, `k`, `l`, `m`, or `n`.</span></span>  
  
     [!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]  
  
     <span data-ttu-id="344bd-128">請注意此項比對會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="344bd-128">Note that this match is case-sensitive.</span></span>  
  
## <a name="matching-empty-strings"></a><span data-ttu-id="344bd-129">比對空字串</span><span class="sxs-lookup"><span data-stu-id="344bd-129">Matching Empty Strings</span></span>  
 <span data-ttu-id="344bd-130">`Like` 會將順序`[]`為零長度字串 (`""`)。</span><span class="sxs-lookup"><span data-stu-id="344bd-130">`Like` treats the sequence `[]` as a zero-length string (`""`).</span></span> <span data-ttu-id="344bd-131">您可以使用`[]`來測試是否將整個字串運算式是空的但您無法使用它來測試是否是空的字串運算式中的特定位置。</span><span class="sxs-lookup"><span data-stu-id="344bd-131">You can use `[]` to test whether the entire string expression is empty, but you cannot use it to test if a particular position in the string expression is empty.</span></span> <span data-ttu-id="344bd-132">空的位置是其中一個選項，如果您要測試其是否可以使用`Like`一次以上。</span><span class="sxs-lookup"><span data-stu-id="344bd-132">If an empty position is one of the options you need to test for, you can use `Like` more than once.</span></span>  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a><span data-ttu-id="344bd-133">若要符合的字元或字元清單的字串運算式中的字元</span><span class="sxs-lookup"><span data-stu-id="344bd-133">To match a character in the string expression against a list of characters or no character</span></span>  
  
1.  <span data-ttu-id="344bd-134">呼叫`Like`運算子兩次相同的字串運算式，並連接兩個呼叫使用[或運算子](../../../../visual-basic/language-reference/operators/or-operator.md)或[OrElse 運算子](../../../../visual-basic/language-reference/operators/orelse-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="344bd-134">Call the `Like` operator twice on the same string expression, and connect the two calls with either the [Or Operator](../../../../visual-basic/language-reference/operators/or-operator.md) or the [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).</span></span>  
  
2.  <span data-ttu-id="344bd-135">在模式比對字串的前`Like`子句中，包含字元清單中，以括弧括住 (`[ ]`)。</span><span class="sxs-lookup"><span data-stu-id="344bd-135">In the pattern string for the first `Like` clause, include the character list, enclosed in brackets (`[ ]`).</span></span>  
  
3.  <span data-ttu-id="344bd-136">在第二個模式比對字串`Like`子句，請不要將任何字元的位置有問題。</span><span class="sxs-lookup"><span data-stu-id="344bd-136">In the pattern string for the second `Like` clause, do not put any character at the position in question.</span></span>  
  
     <span data-ttu-id="344bd-137">下列範例會測試的七位數電話號碼`phoneNum`剛好三個數值的數字，後面接著一個空格、 連字號 (`–`)、 句號 (`.`)，或任何字元，後面接著剛好四位數字。</span><span class="sxs-lookup"><span data-stu-id="344bd-137">The following example tests the seven-digit telephone number `phoneNum` for exactly three numeric digits, followed by a space, a hyphen (`–`), a period (`.`), or no character at all, followed by exactly four numeric digits.</span></span>  
  
     [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]  
  
## <a name="see-also"></a><span data-ttu-id="344bd-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="344bd-138">See also</span></span>

- [<span data-ttu-id="344bd-139">比較運算子</span><span class="sxs-lookup"><span data-stu-id="344bd-139">Comparison Operators</span></span>](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [<span data-ttu-id="344bd-140">運算子和運算式</span><span class="sxs-lookup"><span data-stu-id="344bd-140">Operators and Expressions</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [<span data-ttu-id="344bd-141">Like 運算子</span><span class="sxs-lookup"><span data-stu-id="344bd-141">Like Operator</span></span>](../../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="344bd-142">String 資料類型</span><span class="sxs-lookup"><span data-stu-id="344bd-142">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
